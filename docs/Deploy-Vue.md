# Install Node.js

## Download Node and Npm

Download your prefer version of [Node.js](https://nodejs.org/en/)

## Check that you have node and npm installed

To check if you have Node.js installed, run this command in your terminal:

```bash
node -v
```

To confirm that you have npm installed you can run this command in your terminal:

```bash
npm -v
```

## Install Yarn

follow the instruction to install latest version of yarn:

<https://classic.yarnpkg.com/en/docs/install>

Test that Yarn is installed by running:

```bash
yarn --version
```

## Install Vue CLI

To install the new package, use one of the following commands. You need administrator privileges to execute these unless npm was installed on your system through a Node.js version manager (e.g. n or nvm).

```bash
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

After installation, you will have access to the vue binary in your command line. You can verify that it is properly installed by simply running vue, which should present you with a help message listing all available commands.

You can check you have the right version with this command:

```bash
vue --version
```

Run the following command to install required npm packages:

```bash
npm install
npm install --save vue-router

```

## Build Web Application

To setup project run:

```bash
yarn install
```

This will install required package automatically.

### Run it with hot reload

Run the following command if you want the application run it in local with hot reload feature when you modify the code:

```bash
yarn serve
```

This will serve the website in localhost

### Build for production

Run the following command to compile your virtual DOM to real DOM:

```bash
yarn build
```

under current directory /dist you will see the compiled files which is ready to put into server.
