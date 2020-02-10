# History Cards API

## Get history

### `GET` - /history/get

Use this request to return a history list of cards the user have scanned.

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
        "userid": "<User ID of the history owner>",
        "list": [
            {
                "_id": "<History item id, with time info>",
                "name": "<History user name>",
                "userid": "<Current item user id>",
                "profile": "<Profile avatar url>",
                "username": "<Current item user name>",
            },
            ...
        ]
    }
    ```

    | Key      | Type     | Description           |
    | -------- | -------- | --------------------- |
    | `userid` | `string` | User ID               |
    | `list`   | `List`   | List of history items |


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









## Add to history

### `POST` - /history/add

Use this request to add a single item into the user's history list. Any existing history of this particular
 id will be overwritten (i.e. only one history entry per each user, only newest entry is kept).

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: 

```typescript
{
    userid: string
}
```

| Key      | Type     | Description                                                  | Constraints           | Default | Required |
| -------- | -------- | ------------------------------------------------------------ | --------------------- | ------- | -------- |
| `userid` | `string` | MongoDb ObjectID of the history item (an viewed user) to add | MongoDb ObjectID Type | N/A     | Yes      |


---

!!! success
    The history can be added.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "history updated"
    }
    ```

    | Key       | Type     | Description     |
    | --------- | -------- | --------------- |
    | `success` | `string` | success message |



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






## Remove from history

### `POST` - /history/remove

Use this request to remove a single entry from the history.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: 

```typescript
{
    userid: string
}
```

| Key      | Type     | Description                                                     | Constraints           | Default | Required |
| -------- | -------- | --------------------------------------------------------------- | --------------------- | ------- | -------- |
| `userid` | `string` | MongoDb ObjectID of the history item (an viewed user) to remove | MongoDb ObjectID Type | N/A     | Yes      |


---

!!! success
    The history is removed if the userid provided is correct.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "history might be removed"
    }
    ```

    | Key       | Type     | Description     |
    | --------- | -------- | --------------- |
    | `success` | `string` | success message |



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




### `POST` - /history/remove-all

Use this request to remove all entries from the history list.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: none

---

!!! success
    The history is cleared.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "history is cleared"
    }
    ```

    | Key       | Type     | Description     |
    | --------- | -------- | --------------- |
    | `success` | `string` | success message |



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