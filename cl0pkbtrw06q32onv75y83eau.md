## Using Postman Like a Pro!

---
title: Using Postman Like a Pro!
published: true
date: 2021-06-04 11:02:06 UTC
tags: 2Articles1Week,APIs,Testing
---
![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193211388/2AE6poQJJ.png)


![Postman logo](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193214115/2Q_gALPj0.png)

[Postman](https://www.postman.com/) is an API testing platform. You can use postman [web platform](https://web.postman.co/build):

![postman web](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193215823/vjfgFi7TN.png)

or the [desktop application](https://www.postman.com/downloads/) for testing your APIs.

![desktopostman.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193217594/SrqRkpclm.png)

Postman can be used to test all API requests: `get/put/create/delete`

If you are new to postman, I'd suggest you go through their Bootcamp: [https://web.postman.co/bootcamp](https://web.postman.co/bootcamp)

> I will be using the desktop application for the demos, they're no big differences from using the web version of postman.

# What this article covers:

1. Creating collections
2. Adding requests
3. Creating environments and Variables

## Creating Collections:

In Postman, collections are folders where you put all APIs with similar descriptions or projects together. It is a pretty neat way to organize your APIs for testing.

[https://www.postman.com/collection/](https://www.postman.com/collection/)

Follow the few steps to create an API collection:

1. Ensure that you are on the `collections` tab by clicking on the `Collections` with a folder icon on the top left side menu.

![Postman Collections](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193219693/pS8P5_6zP.png)

On the right of the `Collections` notice the "+" icon and on hovering it, a pop up with the message: "Create new Collection" appears.

![Create new collection - postman](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193221091/0ZJkRIxph.png)

1. Click the "+" icon to create a new collection. Notice a new folder is created `New Collection` and a new tab opened simultaneously.

![created collection](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193222661/JUE8kYy1P.png)

Right-click on the folder and select `rename` to give the collection a name of your choosing or double click on the `new collection` name on the tab to rename.

![double-click.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193224197/Itp56eTIw.png)

![right-click.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193225906/vjAcmyYeH.png)

PSST! I will rename mine to `Demo`

## Adding requests to a Collection:

On hovering over the collection name on the left panel. notice the 3-horizontal-dots, click on it to open a quick menu.

![Add a new request](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193227495/vJqeoJNoa.png)

Select `Add request` and notice a new tab opens:

![new-request.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193228894/MV7R77vO5.png)

Let's add an API endpoint and make a request:

```
https://jsonplaceholder.typicode.com/users

```

Paste the URL in the input label with a placeholder text "Enter request URL", ensure the method on the left is set to "GET" and hit 'Send' to make a request.

![Making a request](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193230463/6qUVhLq21a.png)

The response:

![response.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193233379/GL4S_Rqra.png)

## Creating environments and Variables

An environment in postman is just a collection of variables to be used in a request or a collection

[https://learning.postman.com/docs/sending-requests/managing-environments/](https://learning.postman.com/docs/sending-requests/managing-environments/)

The selected environment status is at the top-right of Postman, the default is "_No environment_".

Here is how we create a new environment and add our variables:

On the left side of the postman web/app, click on the `Environment`.

Click on the "+" icon to create a new environment, then give it a name.

![new-env.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193234973/La6h6r9Q5.png)

To create a variable, manually fill the details on the environment tab:

I will create a variable for the base URL of the API endpoint: `https://jsonplaceholder.typicode.com/`

```
VARIABLE: url
INITIAL VALUE: https://jsonplaceholder.typicode.com/
CURRENT VALUE: https://jsonplaceholder.typicode.com/

```

![variable](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193236887/I7lGHgEcB.png)

To use the variable, go to the request tab and replace the `https://jsonplaceholder.typicode.com/` with `{{url}}`

Then on the top-right, select an environment (select the one you just created from the Dropdown).

After that, make the request to see if everything went well:

![env-var.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193238511/IvKtKMYeH.png)

That is it, to view the demo use:

[![Run in Postman](https://cdn.hashnode.com/res/hashnode/image/upload/v1647193240908/5cRdzz_kJ.svg+xml)](https://app.getpostman.com/run-collection/9711024-0af1bf1e-8e28-43f1-9e96-d7aa7c17d895?action=collection%2Ffork&collection-url=entityId%3D9711024-0af1bf1e-8e28-43f1-9e96-d7aa7c17d895%26entityType%3Dcollection%26workspaceId%3D26c4f6b7-8da3-4522-98d6-b7066cd76325#?env%5BDemo%5D=W3sia2V5IjoidXJsIiwidmFsdWUiOiJodHRwczovL2pzb25wbGFjZWhvbGRlci50eXBpY29kZS5jb20vIiwiZW5hYmxlZCI6dHJ1ZX1d)

## NOTE

There are many ways to create a variable, environment or collections in Postman, I just highlighted the common ones. Feel free to hover on the postman docs to learn and practice more:

https://learning.postman.com/docs/getting-started/introduction/

[MY BIO](https://linktr.ee/chrisdev)