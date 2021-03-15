## React & Bootstrap Starter Template


%[https://chrisachinga.github.io/react-bootstrap-starter]


I love using Bootstrap because it saves time when trying to make a site responsive. After learning to use react, I started working on using [bootstrap](https://getbootstrap.com/) with [react](https://reactjs.org/). It was tough at first, and after I got a hang of it, I quickly made a template that I'd reuse every time I want to use react and bootstrap altogether.

# Here is brief documentation and description of the template:

The Template is live [here](https://chrisachinga.github.io/react-bootstrap-starter), hosted on [GitHub Pages](https://pages.github.com/).

## Usage:

Start using the template in these few simple steps:

### go to the repository

Go to https://github.com/ChrisAchinga/react-bootstrap-starter, and click the `use template` button on the right side, or use this [Link](https://github.com/ChrisAchinga/react-bootstrap-starter/generate)

The repo will be recreated on your account.

Clone the repo on your local environment.

Install the dependencies:

```shell
npm install
```

Start the development server

```shell
npm start
```

## Descrtiption: Language & Frameworks

### create-react-app

I created the app using [create-react-app](https://create-react-app.dev/) tool, which generates starter code-files for React without you worrying about the development environment.

To start using it, simply run the command:

```shell
npx create-react-app [project-name]
```

It will take a couple of minutes to get install everything.

The project structure will be as shown below:

```shell
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```

Read more about getting started with [create-react-app here](https://create-react-app.dev/docs/getting-started)

### react-bootstrap

[React-bootstrap](https://react-bootstrap.github.io/) is a front-end framework that rebuilds bootstrap to make it compatible with React.

To start using it in your project, you install it using:

```shell
npm install react-bootstrap bootstrap
```

which installs both react-bootstrap and bootstrap.

You have to import bootstrap CSS as a module in your index.js file:

```js
import 'bootstrap/dist/css/bootstrap.css'
```

Here is a practical example of using react-bootstrap:

```js
import { Container } from 'react-bootstrap'

const Header = (props) => {
  return (
    <Container>
      <div className='starter-template text-center mt-5'>
        <h1>{props.pageTitle} Page</h1>
        <p className='lead'>{props.pageDescription}</p>
      </div>
    </Container>
  )
}

export default Header
```

You first import the bootstrap component, in this case, the Container, then use it as a JSX element to wrap the contents.

Read more on using [react-bootstrap here](https://react-bootstrap.github.io/getting-started/introduction).

### react-router-dom

I used [react-router-dom](https://www.npmjs.com/package/react-router-dom) to create navigations and pagination of the app.

It makes it easier to create multiple pages within the react app.

To use it, simply install using:

```shell
npm i react-router-dom
```

This is how I used it in App.js file

Imported it:

```js
import { BrowserRouter as Router, Route } from 'react-router-dom'
```

Using it:

```js
const App = () => {
  return (
    <Router>
      <Menu />
      <main>
        <Container>
          <Route path='/react-bootstrap-starter' component={HomePage} exact />
          <Route path='/react-bootstrap-starter/about' component={AboutPage} />
        </Container>
      </main>
    </Router>
  )
}
```

I wrapped everything in the BrowserRouter component and specified what components to display based on the current route.

### react-helmet

[react-helmet docs](https://github.com/nfl/react-helmet)

It enables you to create different <HTML> meta and title stages on different pages on your react application.

To install, simply run:

```shell
npm install --save react-helmet
```

Here's how I used it:

Home Page:

`src/pages/HomePage.js`

```js
import { Helmet } from 'react-helmet'
import Header from '../components/Header'

const HomePage = () => {
  return (
    <div>
      <Helmet>
        <title>Home Page</title>
        <meta name='description' content='Helmet application' />
      </Helmet>
      <Header pageTitle='Landing' pageDescription='This is the Landing Page' />
    </div>
  )
}

export default HomePage
```

About Page:

`src/pages/AboutPage.js`

```js
import { Helmet } from 'react-helmet'
import Header from '../components/Header'

const AboutPage = () => {
  return (
    <>
      <Helmet>
        <title>About Page</title>
        <meta name='description' content='Helmet application' />
      </Helmet>
      <Header pageTitle='About' pageDescription='About Page' />
    </>
  )
}

export default AboutPage
```

### gh-pages

The template is hosted on GitHub pages.

I simply used an article I wrote as a guide to deploy the template:

%[https://chrisdev.hashnode.dev/deploy-a-react-app-on-github-pages]

#### The End!
The repo is open to suggestions and free to use:
[GitHub](https://github.com/ChrisAchinga/react-bootstrap-starter)

Written with ❤️ by [Chris achinga](https://linktr.ee/chrisdev)
