---
title: "Using MongoDB in a NodeJS Project"
datePublished: Tue Apr 18 2023 21:02:22 GMT+0000 (Coordinated Universal Time)
cuid: clgmr3pui000009ju0y2zgppr
slug: using-mongodb-in-a-nodejs-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681850443497/21c83014-5df9-4306-8eb0-ba0c1d2ef1f1.png
tags: mongodb, nodejs, databases, marketing

---

[MongoDB](https://mongodb.com/) is a popular NoSQL database widely used in web development for its scalability, flexibility, and ease of use. NodeJS, on the other hand, is a popular server-side JavaScript runtime that allows developers to build fast and scalable network applications.

When used together, MongoDB and NodeJS make a powerful combination for building modern web applications that can handle large amounts of data and traffic. This article will cover the basic process of creating and connecting a MongoDB database to a simple NodeJS Application.

## Creating A MongoDB Account

First of all, go to [https://www.mongodb.com/](https://www.mongodb.com/) to create an account (log in if you already have one)

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681652309248_Screenshot+from+2023-04-16+16-32-50.png align="left")

## Creating A Database

After creating an account/login into your account, you create a cluster: If you have not created a database before, the screen below shows:

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681652348673_image.png align="left")

Click the `Build a database` to create a database:

Choose the free option:

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681652475278_image.png align="left")

Give a name to your cluster (any name that makes sense)

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681652498525_image.png align="left")

Create a user for the database:

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681652574476_image.png align="left")

Leave the other options as they are, and click finish and create below.

Once done, the database is created:

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681652672644_image.png align="left")

## Connecting to NodeJS Application:

To follow along, please download a copy of the repo below:

[https://github.com/achingachris/airspacenext-server/tree/mongo-db-connect](https://github.com/achingachris/airspacenext-server/tree/mongo-db-connect)

To link to a NodeJS Application, you will need to get the connection string, by clicking on the connect button:

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681664571708_image.png align="left")

Choose to connect with your application (drivers) and go to option number 3:

![](https://paper-attachments.dropboxusercontent.com/s_145B36EAFE2014CCA10156E55E91165A99E8A7E4C4C86F510F451520C5F607E9_1681664647605_image.png align="left")

Copy the connection string: Replace the `<password>` with the password, you created for your database user.

```plaintext
mongodb+srv://doghot:@chrisprojects.bar17ze.mongodb.net/?retryWrites=true&w=majorit
```

Save the string inside a `.env` file:

```plaintext
MONGO_URI = mongodb+srv://doghot:@chrisprojects.bar17ze.mongodb.net/?retryWrites=true&w=majority
```

**Connecting Mongo to NodeJs Application:**

We will use [Mongoose](https://mongoosejs.com/), an object modelling tool for Node.Js, allowing us to create models and schema in our database.

By using Mongoose, developers can define the structure and validation rules for their data, making it easier to manage and maintain the consistency of the data in a MongoDB database. Mongoose simplifies the interaction with MongoDB and helps organise the codebase, making it more efficient and maintainable.

Installing:

`npm install mongoose`

To connect to MongoDB:

```javascript
import mongoose from "mongoose";

const connectDB = async () => {
    try {
        const conn = await mongoose.connect(process.env.MONGO_URI, {
        useNewUrlParser: true,
        useUnifiedTopology: true,
        });
    
        console.log(`MongoDB connected: ${conn.connection.host}`);
    } catch (error) {
        console.error(`Error: ${error.message}`);
        process.exit(1);
    }
}

export default connectDB;
```

The purpose of the connectDB function is to connect to a MongoDB database using the Mongoose library. Here's a breakdown of the code:

1. `**import mongoose from "mongoose";**`: Import the `**mongoose**` library using ECMAScript Modules (ESM) syntax.
    
2. `**const connectDB = async () => { ... }**`: Declare an asynchronous function named `**connectDB**`. This function will be responsible for establishing the connection to the MongoDB database.
    
3. `**try { ... } catch (error) { ... }**`: Use a try-catch block to handle any errors while connecting to the MongoDB database.
    
4. `**const conn = await mongoose.connect(process.env.MONGO_URI, { ... });**`: Inside the try block, call the `**mongoose.connect()**` method with the connection string stored in the `**MONGO_URI**` environment variable. This is an asynchronous operation, so you use the `**await**` keyword to wait for the connection to be established. The `**connect()**` method returns a connection object, which is stored in the `**conn**` constant.
    
5. `**useNewUrlParser: true, useUnifiedTopology: true,**`: These options are passed to the `**mongoose.connect()**` method to enable the new URL parser and the unified topology in the MongoDB driver. The new URL parser is less strict and more efficient, while the unified topology provides better support for various MongoDB deployment topologies.
    
6. `**console.log(**`**MongoDB connected: ${**[**conn.connection.host**](http://conn.connection.host)**}**`**);**`: If the connection is successful, log a message to the console with the host information.
    
7. `**catch (error) { ... }**`The catch block will be executed if an error occurs during the connection attempt.
    
8. `**console.error(**`**Error: ${error.message}**`**);**`: Log the error message to the console.
    
9. `**process.exit(1);**`: Terminate the Node.js process with an exit code of 1, indicating that an error occurred.
    
10. `**export default connectDB;**`: Export the `**connectDB**` function as the default export of this module. This allows you to import and use the `**connectDB**` function in other parts of your application.
    

To use this module, you'll need to import it and call the `**connectDB()**` function in the main entry point of your application. Also, set the `**MONGO_URI**` environment variable to the appropriate connection string for your MongoDB instance.

Following these simple steps, you can now use MongoDB in your NextJS Project.

**Note To Nerds:**

*This article is a build of my project documentation. I am building a MERN stack E-Commerce to refresh my programming skills and documenting it to refresh my technical writing skills*