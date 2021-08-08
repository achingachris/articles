## Using Bootstrap in NextJS (No packages needed!)

Usually, you'll need to install third-party packages like  [react-bootstrap](https://react-bootstrap.github.io/) or  [reactstrap](https://reactstrap.github.io/) for you to fully get the benefits of  [Bootstrap components](https://getbootstrap.com/docs/5.1/components/accordion/).

The updated  [NextJS](https://nextjs.org/docs)  version has made it possible to use Bootstrap with react without necessarily installing 3rd party packages, which would rather make your app heavy and slow. Here is how to do it:

First of all, you'll need to be using NextJS version 11.

%[https://nextjs.org/conf]

To enjoy all that bootstrap has to offer, you have to use both CSS and JS files from both. On bootstrap's home page, there are the CDN links to bootstrap CSS and JS files.

NextJS has the **Head** and **Script** components that let us use the CDN directly without any configuration.

%[https://nextjs.org/docs/api-reference/next/head]

%[https://nextjs.org/docs/basic-features/script]

On your layout file or page file, import the two components from NextJS;

```js
import Script from 'next/script'
import Head from 'next/head'
```

At the top, we'll use `Head` to get the bootstrap styles;

```js
import Head from 'next/head'

const index = () => {
  return (
   <Head>
      <link
        rel='stylesheet'
        href='https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css'
        referrerPolicy='no-referrer'
      />
    </Head>
  )
}

export default index
```

Note that you can use the `<link>` inside the `<Head></Head>` component in Next, and just like that you'd have brought in bootstrap CSS into your project.

Most of the features need to have Bootstrap's javascript to actually work, to do that we'll use the `<Script>` at the bottom of the file:

```js
import Head from 'next/head'
import Script from 'next/script'

const index = () => {
  return (
   <Head>
      <link
        rel='stylesheet'
        href='https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css'
        referrerPolicy='no-referrer'
      />
    </Head>
  
   // page content
   // some code goes here

<Script
        src='https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/js/bootstrap.bundle.min.js'
        strategy='afterInteractive'
/>
  )
}

export default index
```

The Script component takes in the CDN link as the prop to `src`.

With that included, you can comfortably use Bootstrap classes on your page and get responsive and desired results.

Get the sample code used here:

%[https://gist.github.com/achingachris/d63873c468f47f1f130b35f961f6b54a]
