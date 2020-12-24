## Simple `useState()` in React

[This is a hands-on code tutorial on creating react components and using hooks.](https://reactjs.org/docs/hooks-state.html)

View the final product [here](https://chrisachinga.github.io/usestate-demo/)

Little knowledge of react or just the basics will take you through the tutorial.

Clone my repo to go through the code snippets or simply start by creating a new react app using the [`create-react-app`](https://create-react-app.dev/docs/getting-started/).

**Creating A New React App**:

```shell
# create a new react app
npx create-react-app usestate-react
# move into the new app's directory
cd usestate-react
# start the app to see of everything is okay
npm start
```

**Cloning My Repo**

[GitHub Repo Link](https://github.com/ChrisAchinga/usestate-demo)

Cloning using git:

```shell
git clone git@github.com:ChrisAchinga/usestate-demo.git
```

Cloning using gh:
```shell
gh repo clone ChrisAchinga/usestate-demo
```

## The Counter Component

In the `src/components` create a new file, `Counter.js`.
To see the component in action, we have to import it in the `App.js` file in `src` folder.

At the top of the file (`src/App.js`), add the import statement:

```js
import Counter from './components/Counter'
```

Now update the `App()` function to use the `Counter` component:

```js
const App = () => {
  return (
    <>
      <main>
        <Counter />
      </main>
    </>
  )
}
```

```txt
PS: I love using arrow functions and fragments in react
```

Your final `App.js` file should look like the one below here:

```js
import Counter from './components/Counter'
import './App.css'

const App = () => {
  return (
    <>
      <main>
        <Counter />
      </main>
    </>
  )
}

export default App
```

Let's create our Counter component that will have a button, which when clicked, updates the initial number by 1.

Let's do this line by line: (get it, kind of a joke though)

**First**, we import `useState()` from react:

```js
import { useState } from 'react'
```

Since we will need to update the button every time it is clicked, we will need react hooks to do that.
The `useState()` is simply a react hook

**Secondly**, we create the component function that will display the button:

```js
const Counter = () => {
  return (
    <>
      <button>0</button>
    </>
  )
}
```

Don't forget to export the module at the bottom of the file:

```js
export default Counter
```

Run the app to see if everything is upto set.

There should be a big button with a small zero (LOL - No Styles intended), just like this:


![image0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608791021443/ZxfxFwHh2.png)

**Third** step: let's set up the hook in the `Counter` component:

A useState() hook syntax would be simply:

```js
const [state, setstate] = useState(initialState)
```

It's a simple destructuring syntax.

The `state` will be the initial value set by the parameter in the `useState()`, which in this case a Zero (0). The `setstate` will be a function that will be executed to update the `state`, after an event or a trigger.

So back to our file: `src/components/Counter.js` let's update with the `useState()` hook:

```js
const [initial, updater] = useState(0)
```

We set the `initial` to 0 `(useState(0))` and then we have the function that will be executed when the button is clicked to update the `initial` value to the number of times it has been clicked, the `updater` in this case.

Your Counter.js file should be:

```js
import { useState } from 'react'

const Counter = () => {
  const [initial, updater] = useState(0)
  return (
    <>
      <button>0</button>
    </>
  )
}

export default Counter
```

**Fourth** step is to create the updater fucntion, which is an easy one here:

While still in the `Counter()` function, just above the return keyword, add the following function:

```js
const clickEvent = () => updater(initial + 1)
```

This is same as :

```js
function clickEvent() = {
    updater(initial + 1)
}
```

So the `clickEvent()` function will use the `updater` that we declared in the hook. It simply take the initial value and adds one to it.

Stuck? Don't worry, this is how your file should be like up to now:

```js
import { useState } from 'react'

const Counter = () => {
  const [initial, updater] = useState(0)
  const clickEvent = () => updater(initial + 1)
  return (
    <>
      <button>0</button>
    </>
  )
}

export default Counter
```

**Now** let's update our button to use the hook:

We'll make the button more dynamic by removing the hard coded `0` and make it more static. Here's how:

```js
<>
  <button>{initial}</button>
</>
```

We are replacing the `0` with a variable that will be updated every time we click the button.

Our final step will be adding the `onClick` function, which will be telling the button what to do when it is clicked.

What we want to happen is for the `clickEvent()` function to run every time we click the button.

So here's what we do:

```js
<>
  <button onClick={clickEvent}>{initial}</button>
</>
```

We are telling react to run the `clickEvent()` function every time we click on the button.

Our Counter component is now ready!

```js
import { useState } from 'react'

const Counter = () => {
  const [initial, updater] = useState(0)
  const clickEvent = () => updater(initial + 1)
  return (
    <>
      <button onClick={clickEvent}>{initial}</button>
    </>
  )
}

export default Counter
```

So in a summary:

We created a component, added a button that shows the number of times it's been clicked, using the `useState` hook. Cool isn't it?

#### NOTE:

I set my js environment linting with prettier not to use semi-colon


![react-tools.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608790964085/R_vFeFwSc.png)
