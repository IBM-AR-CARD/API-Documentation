# User Authentication

## Overview

We uses [JWT (Json Web Token)](https://jwt.io/) for user login and autehtications. 

A JWT token will be assigned to the 
client after the login request, the token is persistent unless the user log out manually. The token will be stored in 
the database, up to 2 tokens can be generated, thus it means the user can sign in to 2 different devices (e.g. web and 
mobile) at the same time. If additional device is logged in, the oldest token will be automatically invalidated, thus 
the first device would be automatically logged out.

Every user specific requests (e.g. log out, update profile, access favourites) would requrie the JWT Token be passed as 
autorization in the request header. With key `Authorization` and value `Bearer <JWT-Token>`, example below.

!!! example "`Authorization` Header Example"
    ```
    Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTM0ODQ2YzllMjcxNTEwMmQyNDZiOWMiLCJpYXQiOjE1ODA1MjIzMzR9.2kafsTdABIemwiQN-sDfmHbdkOmPkz8fj_n_qGpxYKg
    ```

The user can access `logout-all` endpoint to invalidate all tokens at once.

## User Registration

### `POST` - /user/register

Use this request to register a new user.


**Request Body**:

```typescript
{
    "username": String, // min length 3, max length 25
    "email": String,
    "password": String // min length 5, max length 25
}
```

| Key        | Type     | Description                                  | Constraints                 | Default | Required |
| ---------- | -------- | -------------------------------------------- | --------------------------- | ------- | -------- |
| `username` | `string` | Unique username.                             | min length 3, max length 25 | N/A     | Yes      |
| `email`    | `string` | Unique E-mail. Different from contact e-mail | Email format                | N/A     | Yes      |
| `password` | `string` | Plain text password                          | min length 5, max length 25 | N/A     | Yes      |

---

!!! success
    The user can be registered.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "Successfully regisered, you can now log in."
    }
    ```

    | Key       | Type     | Description     |
    | --------- | -------- | --------------- |
    | `success` | `string` | Success message |


!!! failure "Invalid credentials"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "<Error message>"
    }
    ```





## User Login

### `POST` - /user/login

Use this request to login an existing user.


**Request Body**:

```typescript
{
    "email": String, 
    "password": String
}
```

| Key        | Type     | Description                                  | Constraints                 | Default | Required |
| ---------- | -------- | -------------------------------------------- | --------------------------- | ------- | -------- |
| `email`    | `string` | Unique E-mail. Different from contact e-mail | Email format                | N/A     | Yes      |
| `password` | `string` | Plain text password                          | min length 5, max length 25 | N/A     | Yes      |




---

!!! success
    The user can be logged in.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "Successfully logged in.",
        "token": "<JWT Token>"
    }
    ```

    | Key       | Type     | Description     |
    | --------- | -------- | --------------- |
    | `success` | `string` | Success message |
    | `token`   | `string` | JWT Token of the user, this token is persistent |


!!! failure "Invalid credentials"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "<Error message>"
    }
    ```






## User Logout

### `POST` - /user/logout

Use this request to logout an existing user. This will invalidate the JWT token passed.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Request Body**: None


---

!!! success
    The user can be logged out.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "You are logged out"
    }
    ```

    | Key       | Type     | Description                                     |
    | --------- | -------- | ----------------------------------------------- |
    | `success` | `string` | Success message                                 |


!!! failure "Unauthorized"
    **Status Code**: `401 Unauthorized`

    **Response Body**:

    ```json
    {
        "error": "You are not authorized to access this resource"
    }
    ```



### `POST` - /user/logout-all

Use this request to logout all devices of an existing user. This will invalidate ALL JWT tokens stored in the server.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Request Body**: None


---

!!! success
    The user can be logged out.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "You are logged out of all devices"
    }
    ```

    | Key       | Type     | Description                                     |
    | --------- | -------- | ----------------------------------------------- |
    | `success` | `string` | Success message                                 |


!!! failure "Unauthorized"
    **Status Code**: `401 Unauthorized`

    **Response Body**:

    ```json
    {
        "error": "You are not authorized to access this resource"
    }
    ```





## JWT Test

### `POST` - /user/test-token

Test if a token is valid.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Request Body**: None


---

!!! success
    The token is valid.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "token valid"
    }
    ```

    | Key       | Type     | Description                                     |
    | --------- | -------- | ----------------------------------------------- |
    | `success` | `string` | Success message                                 |


!!! failure "Unauthorized"
    **Status Code**: `401 Unauthorized`

    **Response Body**:

    ```json
    {
        "error": "You are not authorized to access this resource"
    }
    ```