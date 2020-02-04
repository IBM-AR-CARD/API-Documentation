# History API

## Get history

### `POST` - /history/get

Use this request to return the list of user history.

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
    _id: string
}
```

| Key   | Type     | Description                                                   | Constraints | Default | Required |
| ----- | -------- | ------------------------------------------------------------- | ----------- | ------- | -------- |
| `_id` | `string` | MongoDb ObjectID of the request sender. Sent from the client. | N/A         | N/A     | No       |
