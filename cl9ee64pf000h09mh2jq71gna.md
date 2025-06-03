---
title: "How To Create and Deploy a json-server"
datePublished: Tue Oct 18 2022 16:00:14 GMT+0000 (Coordinated Universal Time)
cuid: cl9ee64pf000h09mh2jq71gna
slug: how-to-create-and-deploy-a-json-server
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/ot5kWZkH97s/upload/v1666103604086/9aL54Mk0o.jpeg
tags: javascript, json, server

---

`json-server` is a tool for creating mock REST API fast! To get started, ensure you have the following requirements:

1. NodeJS (npm)

>Let's get started!

On an empty folder, initiate a nodejs application by running the following on your terminal/CMD:

```shell
npm init -y
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666104260278/mP6C7CN2d.png align="left")

Once that is complete, you install the following packages:

- `json-server`
- `json-serve`
- `cors`
- `nodemon` (as a dev dependency)

```shell
npm install json-server json-serve cors
```

```shell
npm install -D nodemon
```

After the installation, create a new file: `index.js`. This is the entry point for the json-serve. Add the following inside the file:

```js
const jsonServer = require('json-server')
const cors = require('cors')
const path = require('path')

const server = jsonServer.create()
const router = jsonServer.router(path.join(__dirname, 'db.json'))
const middlewares = jsonServer.defaults()

server.use(cors())
server.use(jsonServer.bodyParser)
server.use(middlewares)
server.use(router)

const PORT = 8000

server.listen(PORT, () => {
  console.log(`JSON Server is running on http://localhost:${PORT}`)
})
```

In the code above, a server has been created that will be fetching and updating data from a json file, `db.json`

In the project root, create a new file: `db.json` and add the following:

```JSON
{
    "feedback": [
        {
            "id": 1,
            "rating": 10,
            "user_name": "Tony Stark",
            "text": "You are the ironman of this world"
        },
        {
            "id": 2,
            "rating": 9,
            "user_name": "Bruce Wayne",
            "text": "You are the batman of this world"
        },
        {
            "id": 3,
            "rating": 8,
            "user_name": "Peter Parker",
            "text": "You are the spiderman of this world"
        }
    ]
}
```

The mock server is ready to run, but let's add some scripts in `package.json`:

Update the `"scripts"` to:

```JSON
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  },
```

To run the server, use either of the scripts:

```shell
npm run start
```

The server runs on port 8000:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666106933814/ZcGrHylgC.png align="left")

http://localhost:8000/:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666107072195/FDu1-KBvd.png align="left")

The API endpoint is: `http://localhost:8000/feedback`


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666107202771/xNcnZubfw.png align="left")

The following images show the GET and POST methods:

#### GET

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666107404425/kQSKiaybw.png align="left")

#### POST


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666107433130/h11ahTN0d.png align="left")

After POST.ing new data, the `db.json` files update the latest entry.

## Deploying to cyclic.sh

Create an account at cyclic.sh (link account to your GitHub profile). Then upload the mock server to [GitHub](https://github.com/achingachris/yelpme-json-server).

To deploy on cyclic, click the green deploy button on the dashboard:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666107972211/f1yCbvsh6.png align="left")

Select the `Link Your Own` tab to select from GitHub:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666108043995/iwrmCCa4f.png align="left")

Search for the repo and click connect:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666108156132/vBT-zszlJ.png align="left")

After a successful deployment:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666108746193/H_BbeXEZG.png align="left")

Just like that you have your simple server/API ready for use!




