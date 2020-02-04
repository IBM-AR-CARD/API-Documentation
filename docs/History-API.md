# History API

## Get history

### `GET` - /history/get

Use this request to return the list of user history.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: none


---

!!! success
    The history can be returned.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "_id": "<History Storage ID, not usable>",
        "userid": "<User ID>",
        "history": [
            {
                "name": "<History user name>",
                "description": "<History user description>",
                "avatar": "<History user profile URL>",
            },
            ...
        ]
    }
    ```

    | Key       | Type     | Description           |
    | --------- | -------- | --------------------- |
    | `userid`  | `string` | User ID               |
    | `history` | `List`   | List of history items |


!!! failure "Bad Request"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "<Error message>"
    }
    ```

!!! failure "Unauthorized"
    **Status Code**: `401 Unauthorized`

    **Response Body**:

    ```json
    {
        "error": "You are not authorized to access this resource"
    }
    ```