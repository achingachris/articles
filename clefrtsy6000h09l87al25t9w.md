---
title: "How To Convert HTML templates to NextJS (v13)"
datePublished: Wed Feb 22 2023 14:28:51 GMT+0000 (Coordinated Universal Time)
cuid: clefrtsy6000h09l87al25t9w
slug: how-to-convert-html-templates-to-nextjs-v13
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677073822121/2f2bd464-6087-4b60-97e6-9d7cf17ac807.png
tags: reactjs, html5, template, nextjs

---

Now that Next.JS is an awesome frontend tool. How can we get HTML/CSS/JS Templates to work perfectly in a Next.JS project? This article will take you through the steps.

# Requirements

To fully grasp the content, it’s highly recommended that you have the following tools installed on your development environment:

1. NodeJS
    
2. Text Editor (Maybe VIM?)
    
3. Basic React.js and Next.JS knowledge
    

# Finding a Template

For the demo, we will use one of the open-sourced templates from [Startbootstrap](https://startbootstrap.com/). We will use the Freelancer theme, a perfect template for a personal portfolio website.

%[https://startbootstrap.com/theme/freelancer] 

The template can be downloaded using the [link](https://github.com/startbootstrap/startbootstrap-freelancer/archive/gh-pages.zip) and also cloned from the GitHub repository:

%[https://github.com/startbootstrap/startbootstrap-freelancer] 

*Note: Feel free to use any template.*

# Creating a Next.JS Project

To start a new project, open up a command line application and run the script:

```bash
    npx create-next-app@latest my-portfolio
```

*Note:* `my-portfolio` *can be replaced with the name of the project.*

Note that we get some prompts for Next.JS configuration:

```bash
    ✔ Would you like to use TypeScript with this project? … No / Yes
    ✔ Would you like to use ESLint with this project? … No / Yes
    ✔ Would you like to use src/ directory with this project? … No / Yes
    ✔ Would you like to use experimental app/ directory with this project? … No / Yes
    ✔ What import alias would you like configured? … @/*
```

![](https://paper-attachments.dropboxusercontent.com/s_08227D4A666122755B64787FBF008950CBC2A9BC339FC7FA30152C62932CE380_1676973061436_image.png align="left")

Follow along with the [commit](https://github.com/achingachris/convert-html-to-nextjs/commit/e970109af3b0986081fefde8b179d32be68b0772)

After the installation, run the development server using the command:

```bash
    npm run dev
```

Next.JS development server runs on [localhost:3000](http://localhost:3000)

![](https://paper-attachments.dropboxusercontent.com/s_08227D4A666122755B64787FBF008950CBC2A9BC339FC7FA30152C62932CE380_1676986637946_image.png align="left")

## The HTML Template Structure

The HTML template consists of the basic HTML, CSS, and JS files.

```plaintext
    .
    ├── assets
    │   ├── favicon.ico
    │   └── img
    │       ├── avataaars.svg
    │       └── portfolio
    │           ├── cabin.png
    │           ├── cake.png
    │           ├── circus.png
    │           ├── game.png
    │           ├── safe.png
    │           └── submarine.png
    ├── css
    │   └── styles.css
    ├── index.html
    └── js
        └── scripts.js
    
    5 directories, 11 files
```

To successfully convert the project into Next.JS, follow the steps below:

## Adding CSS and Assets

Inside the template directory, copy the `styles.css` file inside the `css/` folder, and paste it into the Next.JS project: `src/styles`.

![](https://paper-attachments.dropboxusercontent.com/s_08227D4A666122755B64787FBF008950CBC2A9BC339FC7FA30152C62932CE380_1676986890306_image.png align="left")

After that, we import the styles into our project by adding the following line inside the `src/pages/_app.js` file:

Follow along with the [commit](https://github.com/achingachris/convert-html-to-nextjs/commit/6ed07f431e4944b3df4ce3750e2e156e7c1e5f33).

Back to the template folder, copy the `assets` folder into the Next.JS `public` folder.

Follow along with the [commit](https://github.com/achingachris/convert-html-to-nextjs/commit/68b7185d5f4bb9e51c195303b32a8546fd4a67c0).

One final step copying the JS folder from the template directory to Next.JS public folder.

Follow along with the [commit](https://github.com/achingachris/convert-html-to-nextjs/commit/2714794f6e501e73ae27443248da583869c4c7fc).

## Adding Custom JavaScript file to Next.JS

Next.JS has made it easier to use custom script files, using **Custom** `**document**`

[https://nextjs.org/docs/advanced-features/custom-document](https://nextjs.org/docs/advanced-features/custom-document)

The default `_document.js` file has the following content:

```jsx
    import { Html, Head, Main, NextScript } from 'next/document'
    export default function Document() {
      return (
        <Html lang="en">
          <Head />
          <body>
            <Main />
            <NextScript />
          </body>
        </Html>
      )
    }
```

To add the script, we add the following inside the body tag:

```js
    {/* Custom JS files */}
    <script
    async
    src='https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js'
    ></script>
    {/* theme js */}
    <script async src='/js/scripts.js'></script>
    {/* startbootstrap forms */}
    <script
    async
    src='https://cdn.startbootstrap.com/sb-forms-latest.js'
    ></script>
```

The updated file will now contain:

```jsx
    import { Html, Head, Main, NextScript } from 'next/document'
    export default function Document() {
      return (
        <Html lang='en'>
          <Head />
          <body>
            <Main />
            <NextScript />
            {/* Custom JS files */}
            <script
              async
              src='https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js'
            ></script>
            {/* theme js */}
            <script async src='/js/scripts.js'></script>
            {/* startbootstrap forms */}
            <script
              async
              src='https://cdn.startbootstrap.com/sb-forms-latest.js'
            ></script>
          </body>
        </Html>
      )
    }
```

Follow along with the [commit](https://github.com/achingachris/convert-html-to-nextjs/commit/4ad099d45f81d64972405e482ba7f578f152a808)

## Adding Page Content

First, we clean the `src/pages/index.js` file to contain the following:

```js
    import Head from 'next/head'
    import Image from 'next/image'
    
    export default function Home() {
      return (
        <>
          <Head>
            <title>Freelancer Portfolio</title>
            <meta name='description' content='Generated by create next app' />
            <meta name='viewport' content='width=device-width, initial-scale=1' />
            <link rel='icon' href='/favicon.ico' />
          </Head>
        </>
      )
    }
```

The next steps will be adding the page content from the `index.html` file in the template to the `index.js` file in our Next.JS project.

The content includes everything inside the `body` tag, without the `scripts` tag:

%[https://gist.github.com/achingachris/805284613a19305a2ee98fc59bc1098e] 

To add the code, we have to use JSX syntax. To make our work easier, we will use a tool to convert HTML to JSX:

[https://transform.tools/html-to-jsx](https://transform.tools/html-to-jsx)

![](https://paper-attachments.dropboxusercontent.com/s_08227D4A666122755B64787FBF008950CBC2A9BC339FC7FA30152C62932CE380_1677071819130_image.png align="left")

So we’ll paste the HTML into to the site and convert it to JSX. This is the updated file:

%[https://gist.github.com/achingachris/45927f894e06f4c360bb4bcf57801064] 

Follow along with the [commit](https://github.com/achingachris/convert-html-to-nextjs/commit/e15ebbc27a24624054ef1882cfb8baf60f762de7).

## Conclusion

The article gives the most important yet basic procedure to use when converting an HTML template to Next.JS

%[https://github.com/achingachris/convert-html-to-nextjs]