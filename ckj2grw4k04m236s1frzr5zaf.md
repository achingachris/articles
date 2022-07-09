## State Management in React

A state is the current data passed in React components. State management in React enables you to dynamically update data in Components. 

This post will take you through creating an initial state and an event to trigger a state update in Reactjs.

## Prerequisites:
- NodeJS Installed
- Knowledge of React

## Source Code and Demo

[GitHub Repo Link](https://github.com/achingachris/state-management-react-demo)


**Creating A New React App**:

```shell
# create a new react app
npx create-react-app state-management-demo
# move into the new app's directory
cd  state management-demo
# start the app to see if everything is okay
npm start
```

For the Demo, clean the `App.js` to have the following:

```js
const App = () => {
  return <div>My React Application</div>
}

export default App
```

We will create a simple counter button to demonstrate state management.

At the top of the `App.js` file, import `useState`:

```js
import { useState } from 'react'
```

Inside the `App()` function, we will set our default state, `0`. Then once a user clicks a button, the number increases by `1` per click. 

```js
const [count, setCount] = useState(0)
```

We will add a function, that will fire up when the button is clicked:

```js
  const handleClick = () => {
    setCount((count) => {
      return count + 1
    })
  }
```

Update the return function to the following:

```js
  return (
    <div className='container'>
      <h1>Counter</h1>
      <p>{count}</p>
      <button className='btn btn-outline-secondary' onClick={handleClick}>Click Me!</button>
    </div>
  )
```
Run the development server and open the browser on port 3000: `http://localhost:3000/`

![Screenshot from 2022-07-09 22-06-26.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657393644309/wXhPSpoTF.png align="left")

The full code:

%[https://gist.github.com/achingachris/e3e85f714b5f0921450f0ce480322140]

Here is a demo:

%[https://codesandbox.io/embed/tender-lewin-yiw2pz?fontsize=14&hidenavigation=1&theme=dark]

## Conclusion:

We created a component and added a button that shows the number of times it's been clicked, using the `useState` hook. Cool isn't it?

## References:
- [React Hooks and State](https://reactjs.org/docs/hooks-state.html)
