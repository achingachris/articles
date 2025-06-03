---
title: "How to add Cloudinary to Strapi CMS for Image/Video uploads"
datePublished: Sun Jun 12 2022 17:46:18 GMT+0000 (Coordinated Universal Time)
cuid: cl4bllhrf09w6q2nv0twudd5t
slug: how-to-add-cloudinary-to-strapi-cms-for-imagevideo-uploads
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1655055933238/A6XQtW5Ku.png
tags: cloudinary, headless-cms, strapi

---

[Strapi](https://strapi.io/) is an open-source Headless CMS. 

> TL;DR:

The demo source code to this article can be found on [GitHub](https://github.com/achingachris/cloudinary-on-strapi).

To get started, you need to have the following on your computer:

- [NodeJS](https://nodejs.org/en/) v14 +
- [Cloudinary](https://cloudinary.com/) Account

## Creating a Strapi Project

To create a new strapi project, run the following:

```shell
npx create-strapi-app@latest my-project --quickstart
```

After a successful installation, Strapi will automatically open a new browser for you to create a local account:

![terminal commands](https://cdn.hashnode.com/res/hashnode/image/upload/v1654894857515/pBMlVt5ix.png align="left")

On the browser: http://localhost:1337/admin/auth/register-admin

![strapi headless cms](https://cdn.hashnode.com/res/hashnode/image/upload/v1654894963453/7HN4j8iX1.png align="left")

## Installing Cloudinary Upload Plugin

To be able to integrate Cloudinary inside your Strapi project, you'll need to install the `provider-upload-cloudinary`:

https://www.npmjs.com/package/@strapi/provider-upload-cloudinary

To install, run the following inside the root of your project:

```shell
npm install @strapi/provider-upload-cloudinary
```

Inside the `./config` folder, create a new file: `plugins.js` and paste the following:

```js
module.exports = ({ env }) => ({
  upload: {
    config: {
      provider: "cloudinary",
      providerOptions: {
        cloud_name: env("CLOUDINARY_NAME"),
        api_key: env("CLOUDINARY_KEY"),
        api_secret: env("CLOUDINARY_SECRET"),
      },
      actionOptions: {
        upload: {},
        uploadStream: {},
        delete: {},
      },
    },
  },
});
```

## Configuring environment variables

At the root of the project folder, locate the `.env` folder, and add the following:

```env
CLOUDINARY_NAME=
CLOUDINARY_KEY=
CLOUDINARY_SECRET=
```
To find the credentials, log into your Cloudinary account and head over to the [account console/dashboard](https://cloudinary.com/console).

![Screenshot from 2022-06-11 01-06-34.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1654899013532/7QriWmi4f.jpg align="left")

You will find your API key and secret on the dashboard, and paste them to your `.env` file. Save and restart the development server:

```shell
npm run develop
```

On the admin dashboard, navigate to **Media Library** to test out the integration. Click on the `+ Add new assets` to upload image/images:


![Screenshot from 2022-06-11 01-31-20.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654900432510/QCGCcTE9P.png align="left")

Upon a successful upload, the status code on your terminal will be 200, or if you check your Cloudinary dashboard, you'll see the image uploaded via Strapi.

![Screenshot from 2022-06-11 01-39-03.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654900871211/8vIY_CFVs.png align="left")

## Conclusion
The post covers the steps to link [Cloudinary](https://cloudinary.com/) with [Strapi](https://strapi.io/) Headless CMS project.