# File Upload API

## File upload

### `POST` - /upload

Upload image or audio file into the backend server. The file will be stored in the user's respective folder. Please name the filename carefully before upload, as this will be the file name stored on the server, file with the same name uploaded by the same user will be overwritten.

!!! warning "Authorization"
    JWT Token inside request header, with key `Authorization` and value `Bearer <JWT-Token>`

**Request Body**: none

**Request Header**
Please put the raw file into the request header.

| Key             | Type     | Description | Constraints     | Default | Required |
| --------------- | -------- | ----------- | --------------- | ------- | -------- |
| `Authorization` | `string` | JWT Token   | As stated above | N/A     | Yes      |
| `file`          | `File`   | Raw File    | N/A             | N/A     | Yes      |




---

!!! success
    The file can be upload.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "success": "file uploaded",
        "path": "<Uploaded file URL>"
    }
    ```

    | Key       | Type     | Description       |
    | --------- | -------- | ----------------- |
    | `success` | `string` | Success message   |
    | `path`    | `string` | Uploaded file URL |


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




## Standard file names

The following are the example file names of common files shared between the client and the server.

| File name             | Description                                                        | File type |
| --------------------- | ------------------------------------------------------------------ | --------- |
| `profile.png`         | `Image for user's profile picture`                                 | `png`     |
| `education.mp3`       | `User's recording file for their education section`                | `mp3`     |
| `description.mp3`     | `User's recording file for their one sentence description section` | `mp3`     |
| `work-experience.mp3` | `User's recording file for their work experiences section`         | `mp3`     |