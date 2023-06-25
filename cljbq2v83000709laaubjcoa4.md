---
title: "Into PWA: Creating an installable Next.Js Application"
datePublished: Sun Jun 25 2023 17:47:22 GMT+0000 (Coordinated Universal Time)
cuid: cljbq2v83000709laaubjcoa4
slug: into-pwa-creating-an-installable-nextjs-application
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687713531821/81b2d862-c780-4af4-9d7a-8b754f42b9bf.png
tags: pwa, nextjs

---

Progressive Web Applications (PWAs) have gained significant popularity in recent years due to their ability to deliver a native-like experience to users across multiple devices. One of the frameworks that has emerged as a powerful tool for building PWAs is Next.js.

Next.js, a React framework for server-side rendering, provides a solid foundation for creating fast and efficient web applications. In this article, we will explore the process of creating an installable Next.js application, taking advantage of the PWA features offered by modern browsers.

## What is a Progressive Web Application (PWA)?

A Progressive Web Application is a web application that utilizes modern web capabilities to deliver an app-like experience to users. PWAs are built with web technologies such as HTML, CSS, and JavaScript and can be accessed through a browser without installing an app store. PWAs offer several advantages, including offline functionality, push notifications, and the ability to be added to the user's home screen for quick access.

%[https://youtu.be/Z8MjdQGyjfA] 

## Building a PWA with Next.Js

Before diving into the process of creating an installable Next.js application, let's quickly set up a basic Next.js project. Ensure you have Node.js and npm (Node Package Manager) installed on your system. Then, follow these steps:

1. Clone the Next.Js starter template (or create a new Next.Js application):
    
    ```bash
    git clone https://github.com/achingachris/nextjs-starter.git
    ```
    
2. Install the dependencies:
    
    ```bash
    npm install
    ```
    
3. Once the installation completes, you can run the development server:
    
    ```bash
    npm run dev
    ```
    

This will start the Next.js development server, and your application will be accessible at [http://localhost:3000](http://localhost:3000)

![Next.Js starter template](https://paper-attachments.dropboxusercontent.com/s_FE8567DF8AC654F148D6F0E50CBBE7D40B8151A655A46C565AE4CFB90B129154_1687600771803_image.png align="left")

## Adding PWA Functionality: Installability

For this demo, we will use an npm package, [`next-pwa`](https://www.npmjs.com/package/next-pwa), to install it, run the following at the root of the project:

```bash
npm i next-pwa
```

Once the installation is complete, update the `next.config.js` file to have the following:

```javascript
const withPWA = require('next-pwa')({
      dest: 'public',
      register: true,
      skipWaiting: true,
      disable: process.env.NODE_ENV === 'development'
    })
    
    /** @type {import('next').NextConfig} */
    const path = require('path')
    
    const nextConfig = {
      reactStrictMode: true,
      sassOptions: {
        includePaths: [path.join(__dirname, 'styles')],
      },
    }
    
    module.exports = nextConfig
```

In the code above, we added the `next-pwa` configurations:

```javascript
    const withPWA = require('next-pwa')({
      dest: 'public',
      register: true,
      skipWaiting: true,
      disable: process.env.NODE_ENV === 'development'
    })
```

The `withPWA` function wraps the configuration options provided and returns a modified Next.js configuration object that includes the PWA settings. This modified configuration can be used in the `next.config.js` file to enable the PWA features in your Next.js application. Using this code snippet, you can easily configure the `next-pwa` package to add PWA functionality to your Next.js application, including service worker registration, caching, and offline support.

## Creating the `manifest.json`

Next, create a new file in the root of your project called `public/manifest.json`.

The `manifest.json` file is a key component of a Progressive Web Application (PWA). It provides metadata and configuration information about the application, allowing browsers and devices to understand and present the PWA appropriately. Here are the main functions of the `manifest.json` file:

1. App Metadata: The `manifest.json` file contains information about the PWA, such as its name, short name, description, and icons. This metadata is used by browsers and devices when displaying the PWA, including on the home screen, app switcher, or other relevant user interfaces.
    
2. Launch Behavior: The `manifest.json` file defines the launch behavior of the PWA. For example, you can specify the start URL, which is the page the PWA opens when launched. You can also define the display mode, such as "fullscreen," "standalone," or "minimal-ui," which determines how the PWA appears to the user.
    
3. Icons: The `manifest.json` file allows you to specify icons of different sizes and formats for the PWA. Browsers and devices use these icons to represent the application visually. Providing icons in multiple sizes is important to ensure the PWA looks good on various devices and platforms.
    
4. Theme Color: The `manifest.json` file includes a theme color property that defines the color scheme for the PWA's user interface. Browsers can use this color to customize the appearance of the browser's UI elements when the PWA is active.
    
5. Additional Configuration: The `manifest.json` file can include other configuration options based on the specific requirements of the PWA. For example, you can define the orientation, background color, language preferences, and more.
    

Providing these details in the manifest.json file enables browsers and devices to handle the PWA appropriately, ensuring users' consistent and native-like experience. Additionally, the `manifest.json` file is used when users choose to install the PWA, as it provides the necessary information for creating an app-like shortcut on the home screen and launching the PWA in its standalone mode.

Here is a sample `manifest.json`:

```json
{
        "name": "Next.js PWA Demo",
        "short_name": "pwaedemo",
        "description": "A Progressive Web App built with Next.js",
        "start_url": "/",
        "display": "standalone",
        "background_color": "#ffffff",
        "theme_color": "#000000",
        "icons": [
            {
                "src": "/icon-192x192.png",
                "sizes": "192x192",
                "type": "image/png"
            },
            {
                "src": "/icon-256x256.png",
                "sizes": "256x256",
                "type": "image/png"
            },
            {
                "src": "/icon-384x384.png",
                "sizes": "384x384",
                "type": "image/png"
            },
            {
                "src": "/icon-512x512.png",
                "sizes": "512x512",
                "type": "image/png"
            }
        ]
    }

```

You can find icons on the site [https://www.iconarchive.com/](https://www.iconarchive.com/), and customize the icons to various sizes on the site: [https://www.simicart.com/manifest-generator.html/](https://www.simicart.com/manifest-generator.html/)

## Updating `_document.js`

Finally, update the `_document.js` file: `src/pages/_document.js`:

```xml
    <link rel="manifest" href="/manifest.json" />
    <link rel="apple-touch-icon" href="/icon-512x512.png"></link>
    <meta name="theme-color" content="#000" />
```

Complete file:

```javascript

    import { Html, Head, Main, NextScript } from 'next/document'
    
    export default function Document() {
      return (
        <Html lang="en">
          <Head>
            <link rel="manifest" href="/manifest.json" />
            <link rel="apple-touch-icon" href="/icon-512x512.png"></link>
            <meta name="theme-color" content="#000" />
          </Head>
          <body>
            <Main />
            <NextScript />
          </body>
        </Html>
      )
    }
```

## Testing the Installable Next.js PWATesting the Installable Next.js PWA

With the above configurations, you can now test your installable Next.js PWA. Run the following command in your project directory to build the optimized production version of your application:

`npm run build`

After the build process completes, start the production server by running:

`npm start`

%[https://www.youtube.com/watch?v=MO4uAp087eY&] 

After installing the application, you can search for it on the app launcher:

![](https://paper-attachments.dropboxusercontent.com/s_FE8567DF8AC654F148D6F0E50CBBE7D40B8151A655A46C565AE4CFB90B129154_1687712728640_image.png align="left")

## Conclusion

In this article, we explored transforming a Next.js application into an installable Progressive Web Application (PWA). By leveraging the power of Next.js and the PWA capabilities provided by modern browsers, we can create fast, efficient, and app-like experiences for our users. Test your PWA on multiple devices and browsers to ensure broad compatibility and an optimal user experience. With the steps outlined in this article, you now have the knowledge to start building your own installable Next.js PWAs. Happy coding!