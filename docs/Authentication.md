# User Authentication

## Overview

We uses [JWT (Json Web Token)](https://jwt.io/) for user login and autehtications.

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