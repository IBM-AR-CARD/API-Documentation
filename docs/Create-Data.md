# Create Server Dummy Data

## Create Basic User Profile

Replace with your server address and port, run the following URL in your browser or postman:

```
     http://${SERVER_ADDRESS}:${PORT}/generate/profile/
```

You should see `SUCCESS`.

This request will generate 3 predefined user profiles (with `username`: `jonmcnamara`, `amy-pajak`, `ben-jones` respectively).

Their login credentials are:

| Username      | Email            | Password   |
| ------------- | ---------------- | ---------- |
| `jonmcnamara` | `john@ucl.ac.uk` | `password` |
| `amy-pajak`   | `amy@ucl.ac.uk`  | `password` |
| `ben-jones`   | `ben@ucl.ac.uk`  | `password` |


!!! warning "Note"
    To use the demo feature in the app or any dummy profile queried by the usernames above, you must generate it using this request first


## Create History and Favourite Dummy
Replace with your server address and port, and userid of the user to create dummy data with, run the following URL in your browser or postman:

For history:
```
     http://${SERVER_ADDRESS}:${PORT}/generate/history?_id=${USER_ID}
```

For favourites:
```
     http://${SERVER_ADDRESS}:${PORT}/generate/favorite?_id=${USER_ID}
```

You should see `SUCCESS`.

This will create 6 more randomly generated users, and add them all in to the user's history or favourite list.

!!! warning
    This will overwrite the user's history or favourite list, this should only be used for development purposes.



## Remove All Dummy data


Replace with your server address and port, run the following URL in your browser or postman:

```
     http://${SERVER_ADDRESS}:${PORT}/generate/clear-dummy/
```

This will clear all dummy user, dummy history, dummy favorites.