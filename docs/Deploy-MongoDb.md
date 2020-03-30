# Deploy mongoDB

Select the operating system on which you are installing MongoDB:

+ [Linux](#linux)
+ macOS
+ Windows

## Linux

This instruction is for Ubuntu only if your are other than Ubuntu, please follow the instruction from [official website](https://docs.mongodb.com/manual/administration/install-on-linux/)

### Install MongoDB Community Edition

Follow these steps to install MongoDB Community Edition using the apt package manager.

#### 1. **Import the public key used by the package management system.**

From a terminal, issue the following command to import the MongoDB public GPG Key from <https://www.mongodb.org/static/pgp/server-4.2.asc>:

```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```

The operation should respond with an OK.

However, if you receive an error indicating that gnupg is not installed, you can:

1. Install gnupg and its required libraries using the following command:

    ```bash
    sudo apt-get install gnupg
    ```

2. Once installed, retry importing the key:

    ```bash
    wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
    ```

#### 2. **Create a list file for MongoDB.**

Create the list file /etc/apt/sources.list.d/mongodb-org-4.2.list for your version of Ubuntu.

Choose the appropriate option for your version of Ubuntu. If you are unsure of what Ubuntu version the host is running, open a terminal or shell on the host and execute lsb_release -dc.

+ Ubuntu 18.04 (Bionic)  
  Create the /etc/apt/sources.list.d/mongodb-org-4.2.list file for Ubuntu 18.04 (Bionic):

  ```bash
  echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
  ```

+ Create the /etc/apt/sources.list.d/mongodb-org-4.2.list file for Ubuntu 16.04 (Xenial):  

  ```bash
  echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
  ```

#### 3. **Reload local package database.**

Issue the following command to reload the local package database:

```bash
sudo apt-get update
```

#### 3. **Install the MongoDB packages.**

To install the latest stable version, issue the following:

```bash
sudo apt-get install -y mongodb-org
```

Optional. Although you can specify any available version of MongoDB, apt-get will upgrade the packages when a newer version becomes available. To prevent unintended upgrades, you can pin the package at the currently installed version:

```bash
echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```

### **Run MongoDB Community Edition**

#### 1. Start MongoDB.

You can start the mongod process by issuing the following command:

```bash
sudo systemctl start mongod
```

If you receive an error similar to the following when starting mongod:

>Failed to start mongod.service: Unit mongod.service not found.

Run the following command first:

```bash
sudo systemctl daemon-reload
```

Then run the start command above again.

#### 2. **Verify that MongoDB has started successfully.**

```bash
sudo systemctl status mongod
```

You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:

```bash
sudo systemctl enable mongod
```

#### 3. **Stop MongoDB**

As needed, you can stop the mongod process by issuing the following command:

```bash
sudo systemctl stop mongod
```

### 4. **Restart MongoDB.**

You can restart the mongod process by issuing the following command:

```bash
sudo systemctl restart mongod
```

You can follow the state of the process for errors or important messages by watching the output in the /var/log/mongodb/mongod.log file.

*Instruction reference from <https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#create-a-list-file-for-mongodb>*

## macOS

### Install MongoDB Community Edition

#### Prerequisites

If you have the Homebrew brew package installed on your OSX host and you have previously tapped the official [MongoDB Homebrew Tap](https://github.com/mongodb/homebrew-brew), skip the prerequisites and go to the [Procedure](#procedure) step.

#### Install XCode

Apple’s XCode includes command-line tools that are required by brew, and is available for free on the App Store. Make sure you are running the latest version.

#### Install Homebrew

OSX does not include the Homebrew brew package by default. Install brew using the [official instructions](https://brew.sh/#install).

#### Tap the MongoDB Homebrew Tap

Issue the following from the terminal to tap the official [MongoDB Homebrew Tap](https://github.com/mongodb/homebrew-brew):

```bash
brew tap mongodb/brew
```

#### Procedure

Follow these steps to install MongoDB Community Edition using the third-party brew package manager.

From a terminal, issue the following:

```bash
brew install mongodb-community@4.2
```

### Run MongoDB Community Edition

Follow these steps to run MongoDB Community Edition. These instructions assume that you are using the default settings.

You can run MongoDB as a macOS service using brew, or you can run MongoDB manually as a background process. It is recommended to run MongoDB as a macOS service, as doing so sets the correct system ulimit values automatically (see [ulimit settings](https://docs.mongodb.com/manual/reference/ulimit/#ulimit-settings) for more information).

+ To run MongoDB (i.e. the mongod process) as a macOS service, issue the following:

  ```bash
  brew services start mongodb-community@4.2
  ```

+ To run MongoDB manually as a background process, issue the following:

  ```bash
  mongod --config /usr/local/etc/mongod.conf --fork
  ```

Both methods use the /usr/local/etc/mongod.conf file created during the install. You can add your own [MongoDB configuration](https://docs.mongodb.com/manual/reference/configuration-options/) options to this file as well.

To verify that MongoDB is running, search for mongod in your running processes:

```bash
ps aux | grep -v grep | grep mongod
```

You can also view the log file to see the current status of your mongod process: /usr/local/var/log/mongodb/mongo.log.

### Connect and Use MongoDB

To begin using MongoDB, connect a mongo shell to the running instance. From a new terminal, issue the following:

```bash
mongo
```

## Windows

