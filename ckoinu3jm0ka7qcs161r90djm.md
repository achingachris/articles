---
title: "Getting Started With strapi"
seoTitle: "Strapi Tutorial"
seoDescription: "Getting started with strapi headless cms"
datePublished: Mon May 10 2021 13:48:04 GMT+0000 (Coordinated Universal Time)
cuid: ckoinu3jm0ka7qcs161r90djm
slug: getting-started-with-strapi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1620651704956/TcjpE_264.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1620654430398/7hLjrx9L7.png
tags: javascript, apis, cms, headless-cms, 2articles1week

---

## Using Strapi 

https://strapi.io/

### What is Strapi 

Strapi is a headless CMS 

A headless content management system, or headless CMS, is a back-end-only content management system that acts primarily as a content repository. A headless CMS makes content accessible via an API for display on any device, without a built-in front-end or presentation layer

A list of headless cms - https://jamstack.org/headless-cms/

## Creating a simple blog CMS with strapi

### Setup strapi project:

#### Requirements

Need to have nodejs(Version 10 and above) and npm. 

To start open your terminal/cmd and run:

```
npx create-strapi-app blog-cms
```

You will be prompted to select an installation type, select `Quickstart`

![selet-instalation-type.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652140835/rhBCViJYm.png)

Installation proceeds

![installing.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652278552/Kp5KiI0t1.png)

Completed Installation:

![completed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652356507/V3N5poMaA.png)

This command will set up the necessary files and folders for your projects. 
You don't have to understand everything at once, we'll go through the basics.

Once the project is set up, it will open a browser tab for the admin panel, where you will be required to create an admin account - http://localhost:1337/admin/auth/register-admin


![admincreate.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652589346/lwfEqSCez.png)

I will use a dummy user to create one for demo purpose:
you will need first and last name, email, and a password.

![admin.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652661252/GV3xpZ8fO.png)

Once you have created the account, you will be redirected to an admin panel. 
Strapi admin has a simple to understand layout.

![dash.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652727796/aC5jxA_Gq.png)

### Creating Content:

Say you are creating a blogging site, you will need something like an entry table on the database, tag/category table too, so in strapi, we create that from the content-type feature on strapi.
We do that by creating a Content-Type in strapi.

Right on the admin dashboard, there is a button to 'create your first content-type

The first step is to create the name, a name could be of anything you think of, let's say a blog entry.

![contentcreate.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620652970494/amcGGmU1o.png)

While giving it a name, strapi will automatically create a uid from the name.
once you are done, click on continue to go on.

A modal box will appear after the click for you to create the fields for your blog entry.

![fieldtypes-box.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653075152/-3f0kZ8Ak.png)

There are a lot of options based on the data type you want an entry to be of:


1. Text
2. Rich Text
3. number 
4. date 
5. boolean
6. relation 
7. email
8. password
9. enumeration (list of choices)
10. media
11. JSON
12. uid

We will create a simple title and body: 

So select the 'text' options.

Give it a name: 'title'

![title.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653257343/Oc72QVKfX.png)

Click `+add another` field

Then select Rich Text for the article body:

Give it a name: 'entry'

![entry.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653339222/gSFzCWNTl.png)

Click finish, that's it.

Click on save after that. the server will reload while saving the current content-type.


![loadaing.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653693936/-6VTADlBA.png)

That's it, you are done.

On the left of the dashboard, under the content-types, you'll see Blog Entries/the name of the content type you created.

Go ahead and add a few entries, one or two (to test of course)

![entry1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653496746/LnPJ-9rWr.png)

After you have added an entry, and saved it, you have to publish it.

**Remember: it's save then publish!**

### Access Your API

You may have a client side site that you'd want to show the blog or the content from your cms, Strapi has a built in api that lets you do that, after all that's the main point, aint it...

By default, strapi runs on port 1337 on your localhost. to acces the api, you use the url: http://localhost:1337/<content-Type-Name> 

In my demo: http://localhost:1337/blog-entries

![api403.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653599638/vU6KIAtq1.png)

By default the api will be forbiden for public urls, to disable that we go settings:

(http://localhost:1337/admin/settings/application-infos)

in settings go to 'USERS & PERMISSIONS PLUGIN  ' and select roles

There are 2 roles, authenticated and public

![roles.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620653664909/CzUa3eHp-.png)

Let's start with the authenticated, scroll down to permissions and select all and save. do the same for the public.

![permisoms.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620654010685/fc2HqD8oZ.png)

After that let's go back to the API URL and refresh the page:

there we go:

![api.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620654056429/2l5uSE5kB.png)

As simple as that, now you can use strapi to manage dynamic content on your site.

## NOTES:

### To run the development server:

```
npm run develop
```

### Source Code
Github: https://github.com/ChrisAchinga/strapi-demo

### Strapi Docs and Tutorials

[Strapi Docs](https://strapi.io/documentation/developer-docs/latest/getting-started/quick-start.html#_1-install-strapi-and-create-a-new-project)

[udemy: strapi and next](https://www.udemy.com/course/nextjs-dev-to-deployment/)



