# Lab 07 - Exercise

The goal of this lab is to combine everything that you have learned in the
previous labs and put it into practice.

Your goal is to create your own Docker image that contains a "Hello world!"
application in a javascript.

Once you have created it, push it to the Docker Hub and  share it over Slack so
you colleagues can check what you have created.

## Task 1: Export your username

Because the username of your dockerhub account is used in this exercise start
with exporting it into an environment variable like in a previous lab.

        export DOCKER_HUB_USERNAME=<YOUR_DOCKER_HUB_USERNAME>

## Task 2: Create the Node.js app

First start with a new folder on your laptop. We will put everything for the
application in this folder.

You can follow the following steps to create a simple HelloWorld javascript
application. Be free to use your own imagination in creating this application.

Start with a `package.json` file with the following content.
```
{
  "name": "docker_web_app",
  "version": "1.0.0",
  "description": "Node.js on Docker",
  "author": "First Last <first.last@example.com>",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.16.1"
  }
}
```
After you created this `package.json` file run `npm install`.

Now create your `server.js` file with the following content.
```
'use strict';

const express = require('express');

// Constants
const PORT = 8080;
const HOST = '0.0.0.0';

// App
const app = express();
app.get('/', (req, res) => {
  res.send('Hello world\n');
});

app.listen(PORT, HOST);
console.log(`Running on http://${HOST}:${PORT}`);
```
Now that we have an application let's put in in a container!

## Task 3: Node.js application in a self created container

Start with creating a `Dockerfile` in the same folder as where you created the
javascript files. As usual don't give this file an extension.

Let's start with how our `Dockerfile` should be build up. First we will need to
define a docker image where we are going to build on.

        FROM node:8

We will choose the node image and continue from there. We need to create a work
directory inside of the container.

        WORKDIR /usr/src/app

Copy our `package.json` file in the container. We will use a wildcard to be sure
that all the files are copied. (after npm version 5 a `package-lock.json` file is
also created next to the `package.json` file. )

        COPY package*.json ./

You can now use the `npm install` in the `Dockerfile`

        RUN npm install

Now copy all your application source in the container with the following `COPY`.

        COPY . .

Since we are using port `8080` inside of the container, this is explained in lab
[lab-04](../lab-04), we need to expose the port in the `Dockerfile`.

        EXPOSE 8080

The only thing that's left is defining our `ENTRYPOINT` this is the behaviour of
the container when it will start. It needs to be the `npm start` command in this
case.

        ENTRYPOINT [ "npm", "start" ]

It will start the server and serve our service on port `8080` inside the
container. Your entire `Dockerfile` should look something like this.
```
FROM node:8

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 8080

ENTRYPOINT [ "npm", "start" ]
``` 
Let's build this image.

        docker build -t ${DOCKER_HUB_USERNAME}/hello-javascript .

Now that we have our image we will be able to run this with `Docker`. Also seen in [lab-04](../lab-04), you will have to map the `8080` port on the `8080` port on your system. This is done in the `docker run` command.

        docker run -p 8080:8080 ${DOCKER_HUB_USERNAME/hello-javascript}


        > docker_web_app@1.0.0 start /usr/src/app
        > node server.js

        Running on http://0.0.0.0:8080

When you get the output above your server is running on localhost. Verify by
browsing to `localhost:8080`.

Congratulations you created your own Javascript application inside of a docker
container.

## Task 4: clean up

To clean up run the following commands:

        docker system prune
        unset DOCKER_HUB_USERNAME
