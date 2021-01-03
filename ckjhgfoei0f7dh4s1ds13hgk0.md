## How I started Using ES6 Modules in Node JS

A short guide on how I started using ES6 Modules when using Node.

I love the EcmaScript Module syntax and I use it almost in all my code and practices.

I will use the example from [Express Introduction - MDN](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)

So, create a new folder (node-es6):

```shell
mkdir node-es6
```

Inside the folder, initialize a node application by:

```shell
npm init -y
```

Now open the folder using your favorite text editor.

Create a new file `hello.js` and paste the code:

```javascript
// Load HTTP module
const http = require("http");

const hostname = "127.0.0.1";
const port = 8000;

// Create HTTP server
const server = http.createServer((req, res) => {

   // Set the response HTTP header with HTTP status and Content type
   res.writeHead(200, {'Content-Type': 'text/plain'});

   // Send the response body "Hello World"
   res.end('Hello World\n');
});

// Prints a log once the server starts listening
server.listen(port, hostname, () => {
   console.log(`Server running at http://${hostname}:${port}/`);
})
```

Run the file to ensure that it's okay:

```shell
node hello.js
```

If the message shows on the terminal:

```shell
Server running at http://127.0.0.1:8000/
```

Then it's running.

## Using ES6

It's simple to get started, head over to the `package.json` file, and add the line:

```JSON
"type": "module",
```

Your updated file should be like this:

```JSON
{
  "name": "node-es6",
  "version": "1.0.0",
  "type": "module",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

The last step would be to update our js file to use es6 modules"

```javascript
// Load HTTP module
import http from "http";

const hostname = "127.0.0.1";
const port = 8000;

// Create HTTP server
const server = http.createServer((req, res) => {

   // Set the response HTTP header with HTTP status and Content type
   res.writeHead(200, {'Content-Type': 'text/plain'});

   // Send the response body "Hello World"
   res.end('Hello World\n');
});

// Prints a log once the server starts listening
server.listen(port, hostname, () => {
   console.log(`Server running at http://${hostname}:${port}/`);
})
```

Note that I changed

```javascript
// Load HTTP module
const http = require("http");
```
To

```javascript
// Load HTTP module
import http from "http";
```

Run the file to make sure that everything worked as planned.

That's it, Tschuss!!
