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
