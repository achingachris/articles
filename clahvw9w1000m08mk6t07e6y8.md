---
title: "How to configure Bootstrap SCSS and JS into a NextJS Project"
datePublished: Tue Nov 15 2022 07:19:28 GMT+0000 (Coordinated Universal Time)
cuid: clahvw9w1000m08mk6t07e6y8
slug: how-to-configure-bootstrap-scss-and-js-into-a-nextjs-project
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/TkZYCXmrKK4/upload/v1667509619493/tU9VFsbwgf.jpeg
tags: bootstrap, reactjs, nextjs

---

Bootstrap is one of the simplest and most used CSS libraries. This article will guide you on configuring a NextJs project with Bootstrap SCSS and JS files.

Codesandbox Demo

%[https://codesandbox.io/p/github/achingachris/next-bootstrap-template/draft/zealous-archimedes]


GitHub:

%[https://github.com/achingachris/next-bootstrap-template/tree/config-bootstrap-scss-and-js
]

## Creating a Next.js Project

If you already have a NextJS project, skip to the next step.

On a terminal, run the following script to set up a NextJs project:

```bash
 npx create-next-app@latest
```

After installation, run:

```bash
    npm run dev
```

A successful setup will run on localhost:3000.


## Installing Bootstrap

To install bootstrap, run the following script on the root of the project:


    npm i bootstrap

If you want to use bootstrap styles as they are, without any customization, import the styles to the file: `pages/_app.js`


    import 'bootstrap/dist/css/bootstrap.min.css'

The updated file:


    import 'bootstrap/dist/css/bootstrap.min.css'
    import '../styles/globals.css'
    
    function MyApp({ Component, pageProps }) {
      return <Component {...pageProps} />
    }
    export default MyApp

To test for a successful setup, edit `pages/app.js` to the following:


    import Head from 'next/head'
    export default function Home() {
      return (
        <>
          <Head>
            <title>NextJS</title>
            <meta name='description' content='Generated by create next app' />
            <link rel='icon' href='/favicon.ico' />
          </Head>
          <main className='container'>
            <h1 className='text-center'>NextJS Application</h1>
          </main>
        </>
      )
    }

Run the development server to view the changes:


    npm run dev

NextJs runs on localhost:3000


![](https://paper-attachments.dropboxusercontent.com/s_6E51278DFDF4307306192D0EAEAF220C26A723178B0E26A756E3222DBFAAB050_1667330256502_image.png)


If the text is centered, the setup was a success! Kudos 


## Configuring Bootstrap with SCSS

In most cases, you would love to customize most of Bootstrap’s styles. Bootstrap allows you to do that by using its SCSS files.

Install `sass` by running:


    npm install sass

After that, you need to add the path to where the `.scss` files are. Add the following to the `next.config.js` file:


      sassOptions: {
        includePaths: [path.join(__dirname, 'styles')],
      },

The updated `next.config.js` file:


    module.exports = {
      reactStrictMode: true,
      sassOptions: {
        includePaths: [path.join(__dirname, 'styles')],
      },
    }

Next, inside the styles directory, create a new scss file: `customBootstrap.scss,` and add the following:


    $theme-colors: (
      'primary': #093ea8,
      'secondary': #3bd7ec,
      'success': #22e11c,
      'info': #d9ff50,
      'warning': #ffbe0b,
      'danger': #ff0000,
      'light': #c0ccda,
      'dark': #000103,
    );
    @import '/node_modules/bootstrap/scss/bootstrap.scss';

By using `$theme-colors` you override bootstrap default values. 

To render the new changes, you update the import statement in `pages/app.js`:


    import '../styles/customBootstrap.scss'
    import '../styles/globals.css'
    function MyApp({ Component, pageProps }) {
      return <Component {...pageProps} />
    }
    export default MyApp

Add buttons with different colors to notice the difference from bootstrap’s default colors. You can do that by updating the `pages/index.js` file into:


    import Head from 'next/head'
    export default function Home() {
      return (
        <>
          <Head>
            <title>NextJS</title>
            <meta name='description' content='Generated by create next app' />
            <link rel='icon' href='/favicon.ico' />
          </Head>
          <main className='container'>
            <h1 className='text-center'>NextJS Application</h1>
            <button className='btn btn-primary m-2'>Button</button>
            <button className='btn btn-secondary m-2'>Button</button>
            <button className='btn btn-danger m-2'>Button</button>
          </main>
        </>
      )
    }


![](https://paper-attachments.dropboxusercontent.com/s_6E51278DFDF4307306192D0EAEAF220C26A723178B0E26A756E3222DBFAAB050_1667332058247_image.png)


Congratulations! You did it.
One more thing…


## Using Bootstrap JS

There are a number of ways to add Bootstrap JS scripts to a NextJS application. For this article, you will use the simplest and most effective way, using the `useEffect` hook. 

To do that, you will edit the `pages``/``**_app.js**` file to:


    import { useEffect } from 'react'
    import '../styles/customBootstrap.scss'
    import '../styles/globals.css'
    function MyApp({ Component, pageProps }) {
      useEffect(() => {
        import('bootstrap/dist/js/bootstrap')
      }, [])
      
      return <Component {...pageProps} />
    }
    export default MyApp

To test a successful configuration, add the following snippet inside the `index.js` file:


              {/* Button trigger modal */}
              <button
                type='button'
                className='btn btn-primary'
                data-bs-toggle='modal'
                data-bs-target='#exampleModal'
              >
                Launch demo modal
              </button>
              {/* Modal */}
              <div
                className='modal fade'
                id='exampleModal'
                tabIndex={-1}
                aria-labelledby='exampleModalLabel'
                aria-hidden='true'
              >
                <div className='modal-dialog'>
                  <div className='modal-content'>
                    <div className='modal-header'>
                      <h1 className='modal-title fs-5' id='exampleModalLabel'>
                        Modal title
                      </h1>
                      <button
                        type='button'
                        className='btn-close'
                        data-bs-dismiss='modal'
                        aria-label='Close'
                      />
                    </div>
                    <div className='modal-body'>...</div>
                    <div className='modal-footer'>
                      <button
                        type='button'
                        className='btn btn-secondary'
                        data-bs-dismiss='modal'
                      >
                        Close
                      </button>
                      <button type='button' className='btn btn-primary'>
                        Save changes
                      </button>
                    </div>
                  </div>
                </div>
              </div>

Run the local server and on the Launch Modal button and observe what happens

[NextJS - 3 November 2022 - Watch Video](https://www.loom.com/share/72691116ea254efb98a3f45eea7bc71c)

![](https://cdn.loom.com/sessions/thumbnails/72691116ea254efb98a3f45eea7bc71c-with-play.gif)



![](https://paper-attachments.dropboxusercontent.com/s_6E51278DFDF4307306192D0EAEAF220C26A723178B0E26A756E3222DBFAAB050_1667502618720_image.png)

![](https://paper-attachments.dropboxusercontent.com/s_6E51278DFDF4307306192D0EAEAF220C26A723178B0E26A756E3222DBFAAB050_1667502628356_image.png)


If a modal box pops up! Congratulations, you did it.


