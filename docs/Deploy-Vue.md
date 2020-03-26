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

## Install Vue CLI by Npm

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