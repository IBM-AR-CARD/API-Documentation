# User Favourite Cards API

## Get favorite

### `GET` - /favorite/get

Use this request to return a favorite list of cards the user have scanned.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: none


---

!!! success
    The favorite can be returned.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "_id": "<Favorite Storage ID, not usable>",
        "userid": "<User ID of the favorite owner>",
        "list": [
            {
                "_id": "<Favorite item id, with time info>",
                "name": "<Favorite user name>",
                "userid": "<Current item user id>",
                "profile": "<Profile avatar url>",
                "username": "<Current item user name>",
            },
            ...
        ]
    }
    ```

    | Key      | Type     | Description            |
    | -------- | -------- | ---------------------- |
    | `userid` | `string` | User ID                |
    | `list`   | `List`   | List of favorite items |


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









## Add to favorite

### `POST` - /favorite/add

Use this request to add a single item into the user's favorite list. Any existing favorite of this particular
 id will be overwritten (i.e. only one favorite entry per each user, only newest entry is kept).

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: 

```typescript
{
    userid: string
}
```

| Key      | Type     | Description                                                   | Constraints           | Default | Required |
| -------- | -------- | ------------------------------------------------------------- | --------------------- | ------- | -------- |
| `userid` | `string` | MongoDb ObjectID of the favorite item (an viewed user) to add | MongoDb ObjectID Type | N/A     | Yes      |


---

!!! success
    The favorite can be added.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "favorite updated"
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






## Remove from favorite

### `POST` - /favorite/remove

Use this request to remove a single entry from the favorite.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: 

```typescript
{
    userid: string
}
```

| Key      | Type     | Description                                                      | Constraints           | Default | Required |
| -------- | -------- | ---------------------------------------------------------------- | --------------------- | ------- | -------- |
| `userid` | `string` | MongoDb ObjectID of the favorite item (an viewed user) to remove | MongoDb ObjectID Type | N/A     | Yes      |


---

!!! success
    The favorite is removed if the userid provided is correct.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "favorite might be removed"
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




### `POST` - /favorite/remove-all

Use this request to remove all entries from the favorite list.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`


**Query Parameter(s)**: none


**Request Body**: none

---

!!! success
    The favorite is cleared.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "favorite is cleared"
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