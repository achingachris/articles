## How To Create A Layout Component: React

When creating a react application/website, most of the pages would be sharing the same content all over. For example the navigation bar and page footer. Instead of importing each component in every page to be rendered, it is much easier and faster to just create a layout component.

This post will cover how to create a react app using Layout Components.

Live demo: https://hjpx0v.csb.app/

Source Code to the demo: https://github.com/achingachris/react-layout-demo

Here is how to do it:

## Creating a React App using `create-react-app`

To start a new React application, run the following on the CLI of your developer environment:

```shell
npx create-react-app react-layout-demo
cd react-layout-demo
npm start
```

If the installation is successful, open the browser and go to http://localhost:3000/:


![Default react landing page](https://cdn.hashnode.com/res/hashnode/image/upload/v1653830941522/-ysRy_4y_.png align="center")

## Creating the Layout Component

Inside the `src` directory, create a new folder: `components/` and inside the new folder, add a new file: `Layout.js`

Inside the new file, create a new component.

>You can choose either class component or functional component that works best for you 😄

```jsx

const Layout = () => {
  return (
    <div>Layout</div>
  )
}

export default Layout
```

## Making the Component a `Layout Component`

To make the component, a `layout component`, we will use [React inheritance](https://reactjs.org/docs/composition-vs-inheritance.html), which allows the contents of the component used anywhere the `Layout` component will be imported. To do that, we will use the `children` props:

```jsx
const Layout = ({ children }) => {
  return <div>{children}</div>
}

export default Layout
```

## Adding Navigation and Footer to the Layout.

Inside the `src/components` directory, add two new files: `Navigation.js` and `Footer.js` and update the content as follows:

`Navigation.js`

%[https://gist.github.com/achingachris/63975779e8c8c4757e59485c5cef57ac]

`Footer.js`

%[https://gist.github.com/achingachris/55584bf64f3e219f2efccfad694cf3a0]

To add the Navigation and Footer on the Layout component, update the `Layout.js` to:

```jsx
import Navigation from './Navigation'
import Footer from './Footer'

const Layout = ({ children }) => {
  return (
    <>
      <Navigation />
      <main>{children}</main>
      <Footer />
    </>
  )
}

export default Layout
```


```JavaScript

import NavigationBar from '../components/NavigationBar'
import Footer from '../components/Footer'

const Layout = ({children}) => {
 return (
  <div>
    <NavigationBar />
    <Footer />
  </div>
 )
}

```

## Using the Layout Component

Import the component into the pages needed i.e

```JavaScript
import Layout from '../layout/Layout'

const AboutPage = () => {

return (
  <Layout>
    //page content
  </Layout>
)

}

```

Ensure that all the contents in the component are wrapped inside the `<Layout></Layout>`

## Conclusion

The post has covered the steps to create a Layout component in React.

## Codesandbox

%[https://codesandbox.io/embed/gifted-orla-hjpx0v?fontsize=14&hidenavigation=1&theme=dark]

