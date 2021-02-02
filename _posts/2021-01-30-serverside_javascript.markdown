---
layout: post
title:      "ServerSide JavaScript"
date:       2021-01-30 17:28:55 -0500
permalink:  serverside_javascript
---



This past week I attended a virtual coding meetup, where I learned how to set up a local server using JavaScript!  I have only built servers using Ruby on Rails in the past. So this was different but also familiar because we still used HTTP requests, along with utilizing the Node.js and Express.js packages. I learned a lot from this event, from how to set up my local environment to making get requests and manipulating the responses. If you are interested in trying to set up your own local server with JS, keep reading! 

First, you want to make sure you have the latest versions of NPM (node package manager) and Node.js installed on your system. I will put all relevant links at the bottom of this post so you can complete this step if needed. 

Next, create your app folder and after you cd into the app directory, run `npm init` in your terminal. This will give you several prompts to go through to set up your package.json file. The prompts will look like this : 

```
name: (project-name) project-name
version: (0.0.0) 0.0.1
description: The Project Description
entry point: leave empty
test command: leave empty
git repository: the repositories url
keywords: leave empty
author: your name
license: N/A
```

Once you are finished setting this file up your package.json file will look something like this:

```
{
  "name": "project-name",
  "version": "0.0.1",
  "description": "Project Description",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "the repositories url"
  },
  "author": "your name",
  "license": "N/A"
}
```

Next, we will create our web network by installing Express.js. This will give us the modules, packages, and dependencies that Node depends on to run Express. Now we run `npm install --save express` in the terminal. 

That is the last thing we have to do for our initial setup and we are ready to set up our first request!

In the index.js file we will need to set up an endpoint/portNumber, require the Express.js package, and require the path module that comes with Node.js for our server requests. The path module allows us to work with file and directory paths so we can point to specific files we need our requests to utilize. We can set this all up using variables, like so:

```
const express = require("express");
const portNumber = 4000;
const path = require("path");

const app = express();
```


We also need this bit of code to ensure our app is listening for our requests on an open port:

```
app.listen(portNumber, () => {
  console.log("App running on port:", portNumber);
});
```

Now we are ready to make our first request! We have access to the request and response objects because of our express package. The request object handles the data coming from our client/going to the server and the response object handles all the data coming back from the server/going to the client. 

```
app.get("/", (request, response) => {
  console.log(request);
 response.send("Hello World!");
 });
```

Here we are just console logging our request object and sending a response in the form of “Hello World!” However, if you want to actually send a response back using a file in your directory, the set up would look more like:

```
app.get("/", (request, response) => {

 app.use(express.static("public"));
 response.sendFile(path.join(__dirname, "public/index.html"));
});
```

In the above code, we are telling the server to use the public folder and using the path package name to send our response. So, whatever is in the index.html file (in this case, the text for the home page) will be our response. 

If you want to create a dynamic route, that is also possible! For this example, the challenge was to change the original route slightly so that it will accept a parameter, which will represent a person's name. This is the code we came up with, utilizing the enteredName property on the params object. 

```
app.get("/name/:enteredName", (request, response) => {
  console.log(request.params.enteredName);
  response.send(`Hello ${request.params.enteredName}`);
});
```

That’s all you have to do to get started! I have included some links below that you would need for setup, along with my repo with the code for this blog. I encourage you to try this out for yourself and see what you can do. Happy Coding!

**Resources :**
```
Install NPM - [https://www.npmjs.com/package/npm-install](http://)
Install Node.js - [https://nodejs.org/en/](http://)
Gihub Repo - [ https://github.com/SMakaiTakori/ServerSideJS](http://)
```
