# User Profile API

## Get User Profile

### `POST` - /profile/get

Use this request to return of the user's full profile in JSON.

<!-- !!! warning "Authorization"
    `none` -->


**Query Parameter(s)**:

| Parameter  | Type     | Description                             | Constraints           | Default | Required               |
| ---------- | -------- | --------------------------------------- | --------------------- | ------- | ---------------------- |
| `username` | `string` | Username of the profile being reuqested | N/A                   | N/A     | One of two is required |
| `_id`      | `string` | User's MongoDb id                       | MongoDb ObjectID Type | N/A     | One of two is required |

!!! note "Example"
    `/profile/get?username=jonmcnamara`


**Request Body**:

```typescript
{
    username: string
}
```

| Key        | Type     | Description                                    | Constraints | Default | Required |
| ---------- | -------- | ---------------------------------------------- | ----------- | ------- | -------- |
| `username` | `string` | User name of the sender. Sent from the client. | N/A         | N/A     | No       |


---

!!! success
    The user can be found using the query and have a full profile.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "aaa": "aaa"
    }
    ```

    | Key                 | Type     | Description                      |
    | ------------------- | -------- | -------------------------------- |
    | `uclcssaSessionKey` | `string` | Key representing a user session. |

!!! failure "User not found"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "not-found"
    }
    ```

