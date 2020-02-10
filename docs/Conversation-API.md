# User Chat Conversation API

This endpoint handles the conversation and natural language processing from the front-end, Watson Assitant is used here to understand and classify the question user ask. The raw question acquired from front-end speech to text would be passed into Watson, Watson would then return the response type or response text back after processing, the backend would then process the information from Watson again to add user profile and finally send back to the client.

## Get question response

### `POST` - /chat

Use this request to send a question and get the response.



**Query Parameter(s)**: none


**Request Body**: 

```typescript
{ 
    "userid": String,
	"content": String,
	"senderUsername": String
}
```

| Key              | Type     | Description                                                                            | Constraints           | Default | Required |
| ---------------- | -------- | -------------------------------------------------------------------------------------- | --------------------- | ------- | -------- |
| `userid`         | `string` | MongoDb ObjectID of the profile the user is chatting (asking question) to              | MongoDb ObjectID Type | N/A     | Yes      |
| `content`        | `string` | The question content                                                                   | N/A                   | N/A     | Yes      |
| `senderUsername` | `string` | The username of the sender, for record purposes. Leave `null` if no user is logged in. | N/A                   | N/A     | Yes      |


---

!!! success
    The history can be added.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "type": "<`text`, `audio`, `image` or `url`>",
        "content": "<String of content type>"
    }
    ```

    | Key       | Type     | Description                              |
    | --------- | -------- | ---------------------------------------- |
    | `type`    | `string` | One of `text`, `audio`, `image` or `url` |
    | `content` | `string` | String of content type                   |



!!! failure "Bad Request"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "<Error message>"
    }
    ```
