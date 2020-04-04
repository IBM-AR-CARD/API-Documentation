# Deploy Node.js and Express Server

## Install Node.js

If you already install Node.js please jump to [Clone from Github](#clone-from-github)

### Download Node and Npm

Download your prefer version of [Node.js](https://nodejs.org/en/){target=_blank}

### Check that you have node and npm installed

To check if you have Node.js installed, run this command in your terminal:

```bash
node -v
```

To confirm that you have npm installed you can run this command in your terminal:

```bash
npm -v
```

## Clone from Github

clone the repository by runnning:

```bash
git clone https://github.com/IBM-AR-CARD/Backend-API.git
```

now navigate to the project

```bash
cd Backend-API
```

## Config your backend server

Make a copy of the default environment file `.env.default` then rename the file to `.env`.

Open the `.env` you just created, complete the config the save it.

!!! warning
    Please correctly config the Watson Assistant, and paste the correct `WATSON_KEY` and `WATSON_ASSISTANT_ID` into the `.env` file. We have attached our Watson Config Key and ID into the submission.

    Please also note that `UPLOAD_FOLDER` should be publically accessible.

    `SERVER_ADDRESS` should be the root URL of the server, `JWT_KEY` can be any arbitrary key for encryption.

## Run the application

Make sure:

- Your current directory is the backend working directory.
- MongoDB is correctly installed.
- You have ran `npm install` to install all the dependencies.
- Your `.env` is correctly configured.

Run:

```bash
node server.js
```

to start the server, once the server has started you will see similar output:

```bash
App listening on port ${port}!
```

You can also use a process manager such as `pm2` to run the server persistantly.

If you have pm2 installed, you can also use our launch script: 


```bash
./launch.sh 
```
