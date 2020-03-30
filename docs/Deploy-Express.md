# Deploy Express

## Install Node.js

If you already install Node.js please jump to [Clone from Github](#clone-from-github)

### Download Node and Npm

Download your prefer version of [Node.js](https://nodejs.org/en/)

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

## Run the application

Make sure you current directory is the backend working directory. Run

```bash
node server.js
```

to start the server, once the server has started you will see similar output:

```bash
App listening on port ${port}!
```

