# User Profile API

## Get User Profile

### `POST` - /profile/get

Use this request to return of the user's full profile in JSON. The URL of this endpoint is embedded in the QR code on the business card.

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


---

!!! success
    The user can be found using the query and have a full profile.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
      _id: "xxxxxxxxxx",
      dummyid: "dummy1",
      username: "jonmcnamara",
      profile:
        "https://media-exp2.licdn.com/dms/image/C5603AQFA_oQhi6-2Cg/profile-displayphoto-shrink_800_800/0?e=1584576000&v=beta&t=QfVEJg5DU7IHXBiUlaZ2nRjI5gHTqok20eL17iHHa8Y",
      firstname: "John",
      lastname: "McNamara",
      description:
        "John is a Senior Inventor, Research Fellow, Impact Fellow and currently provides technical leadership for the IBM Hursley Innovation Centre. John has a diverse background that includes consultancy, performance, service & product delivery, all underpinned by a passion for innovation. Most recently his work leading the Innovation Centre technologist team has allowed him to combine these interests in order to maximise the potential of new technology while solving real problems. John has overseen the delivery of many cognitive cloud-based solutions and understands how to combine technologies to quickly provide value for customers. John is an active inventor with an invention portfolio spanning mobile, A.I, messaging, integration and predictive analytics.",
      experience:
        "Senior Inventor at IBM and Hursley Innovation Labs Technologist Lead",
      education:
        "I have studied at University of Humberside, on Field Of StudyInformation Systems. And received a 2:1 Grade",
      gender: 2,
      isFav: true
    }
    ```

    | Key        | Type      | Description                                             |
    | ---------- | --------- | ------------------------------------------------------- |
    | `_id`      | `string`  | MongoDB ObjectID                                        |
    | `dummyid`  | `string`  | Exists if the user is dummy data.                       |
    | `username` | `string`  | Unique identifier                                       |
    | `profile`  | `string`  | Profile picture image Url                               |
    | `gender`   | `integer` | 0 - Unset, 1 - Female, 2 - Male                         |
    | `isFav`    | `boolean` | Whether the profile is in current user's favourite list |

!!! failure "User not found"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "not-found"
    }
    ```

### `GET` - /profile/get

This request should not be used by the client, as the endpoint is prepared when the user scans the QR code using other app such as the camera app. 
In such case the URL would be opend in a browser. A html page which invites the user to download our app would be returned.

**Query Parameter(s)**:

Same as the `POST` request above.

!!! success
    HTML page which invites the user to download the app.







## Update User Profile

### `POST` - /profile/update


**Request Body**:

```typescript
{
      _id: "xxxxxxxxxx",
      dummyid: "dummy1",
      username: "jonmcnamara",
      profile:
        "https://media-exp2.licdn.com/dms/image/C5603AQFA_oQhi6-2Cg/profile-displayphoto-shrink_800_800/0?e=1584576000&v=beta&t=QfVEJg5DU7IHXBiUlaZ2nRjI5gHTqok20eL17iHHa8Y",
      firstname: "John",
      lastname: "McNamara",
      description:
        "John is a Senior Inventor, Research Fellow, Impact Fellow and currently provides technical leadership for the IBM Hursley Innovation Centre. John has a diverse background that includes consultancy, performance, service & product delivery, all underpinned by a passion for innovation. Most recently his work leading the Innovation Centre technologist team has allowed him to combine these interests in order to maximise the potential of new technology while solving real problems. John has overseen the delivery of many cognitive cloud-based solutions and understands how to combine technologies to quickly provide value for customers. John is an active inventor with an invention portfolio spanning mobile, A.I, messaging, integration and predictive analytics.",
      experience:
        "Senior Inventor at IBM and Hursley Innovation Labs Technologist Lead",
      education:
        "I have studied at University of Humberside, on Field Of StudyInformation Systems. And received a 2:1 Grade",
      gender: 2
    }
```

| Key          | Type     | Description                               | Constraints           | Default | Required |
| ------------ | -------- | ----------------------------------------- | --------------------- | ------- | -------- |
| `_id`        | `string` | User's MongoDb id                         | MongoDb ObjectID Type | N/A     | Yes      |
| Other fields | N/A      | Any other changed fields, or full profile | N/A                   | N/A     | No       |

---

!!! success
    The user can be found using the query and can be updated.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
        "status":"success"
    }
    ```


!!! failure "User not found or cannot be updated"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "<Error Message>"
    }
    ```







## Create dummy profile data

### `GET` - /profile/generate

Use this request to generate 3 predefined user profiles (with `username`: `jonmcnamara`, `amy-pajak`, `ben-jones` respectively).

!!! note "Note"
    To use the dummy profile queried by the usernames above, you must generate it using this request first


**Query Parameter(s)**: None



---

!!! success
    Profile generated.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
      "status":"success"
    }
    ```
