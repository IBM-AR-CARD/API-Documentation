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

    | Key        | Type      | Description                       |
    | ---------- | --------- | --------------------------------- |
    | `_id`      | `string`  | MongoDB ObjectID                  |
    | `dummyid`  | `string`  | Exists if the user is dummy data. |
    | `username` | `string`  | Unique identifier                 |
    | `profile`  | `string`  | Profile picture image Url         |
    | `gender`   | `integer` | 0 - Unset, 1 - Female, 2 - Male   |

!!! failure "User not found"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    ```json
    {
        "error": "not-found"
    }
    ```

