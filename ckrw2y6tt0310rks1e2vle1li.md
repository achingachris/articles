---
title: "How to Create A Simple API: ExpressJS"
datePublished: Tue Aug 03 2021 13:11:16 GMT+0000 (Coordinated Universal Time)
cuid: ckrw2y6tt0310rks1e2vle1li
slug: how-to-create-a-simple-api-expressjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1627996204957/ipANKv0St.png
tags: express, javascript, server, apis, expressjs-cilb5apda0066e053g7td7q24

---

Express JS is a backend framework that runs on Node JS.

It really comes in handy when creating backend microservices for our applications. 

I will take you through simple steps in creating a simple API with Express.

## Installing dependencies

This should be the simplest of all:

On the project root, open up your terminal/CMD and install express using the following command:

```shell
npm install express
```

## Create a server file

While still on the root of your project, create a JavaScript file; `app.js`

## Creating A server:

On the newly created file (app.js), let's create a simple server:

```js
// importing express
const express = require('express')

// creating a instance of express
const app = express();
```

After bringing express into the app, let's create a simple server:

```js
app.listen(5000, console.log('App Running On Port 5000!'))
```
 [The  .listen() method binds and listens for connections on the specified host and port.](http://expressjs.com/en/5x/api.html#app.listen) 

Your file should now have the following code:

```js
// importing express
const express = require('express')

// creating a instance of express
const app = express();

app.listen(5000, console.log('App Running On Port 5000!'))
```

On your terminal, run the server using:

```shell
node app.js
```

![run1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627993632364/uETsDecIQ.png)

When you see the message: 'App Running On Port 5000!' on your terminal, well! you are good to GO.

## Getting the API

Well normally, your backend application will be sending data to a client site, let's create a simple server.

On the same folder, create a new file "data.js" with the following data:

```JS
const colors = [
  {
    color: 'red',
    value: '#f00',
  },
  {
    color: 'green',
    value: '#0f0',
  },
  {
    color: 'blue',
    value: '#00f',
  },
  {
    color: 'cyan',
    value: '#0ff',
  },
  {
    color: 'magenta',
    value: '#f0f',
  },
  {
    color: 'yellow',
    value: '#ff0',
  },
  {
    color: 'black',
    value: '#000',
  },
]

module.exports = colors
```

let's write the code to server the data from the file from our server:

```js
// getting the data file
const color = require('./data')

// serving data
app.get('/api/colors', (req, res) => {
    res.send(color)
})
```

First, we bring in the data file and create the route for getting the data.

```js
// importing express
const express = require('express')

// getting the data file
const color = require('./data')

// creating a instance of express
const app = express();

// serving data
app.get('/api/colors', (req, res) => {
    res.send(color)
})

app.listen(5000, console.log('App Running On Port 5000!'))
```

Run the server and go to http://localhost:5000/api/colors on your browser.

![results.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627995834660/69ZwbpgZY.png)

Wasn't that simple!

