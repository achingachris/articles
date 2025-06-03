---
title: "How To Display JSON data on an HTML page using Vanilla JavaScript"
seoTitle: "Display Data using Vanila JS"
seoDescription: "How To Display JSON data on an HTML page using plain JavaScript"
datePublished: Fri May 28 2021 13:17:58 GMT+0000 (Coordinated Universal Time)
cuid: ckp8copu002uc04s13o8w9cap
slug: how-to-display-json-data-on-an-html-page-using-vanilla-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1622207766329/imoF6DzN-.png
tags: javascript, apis, fetch, 2articles1week

---


This is a hands-on code tutorial on how to fetch data using plain JavaScript and Displaying data on a simple HTML web page.

When creating websites, there is a possibility that you'll be getting data from an API. The data is in JSON, in most cases.

> How do I display the JSON is my HTML page using vanilla JS?

Let's do that in a few steps.

JS has a built-in function called `.fetch()` that is used to 'fetch' data from external files or resources.

Let's work on a simple project:

We'll fetch country names and their abbreviations from a JSON file and list them on an HTML page.

[LIVE DEMO](https://chrisachinga.github.io/fetch-api-demo/)

![country_complete.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622202333384/9BBjBCSHw.png)

Start by creating a simple HTML file: `index.html`

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>JSON-JS</title>
  </head>
  <body>
    <h1>countries: a long list</h1>
    <div id="country"></div>
    <script src="script.js"></script>
  </body>
</html>
```

I added the empty div `<div id='country></div>` because we will use it to pass the list of countries from the JSON file. [countries.json](https://github.com/ChrisAchinga/fetch-api-demo/blob/dev/countries.json)

On line 29, i used `<script src="script.js"></script>` to import the javascript file that we will use to get the data.

On the same folder/directory where you created the `index.html` file, create a new file `script.js`

on the js file, create an empty function and then call it at the end of the file:

```JavaScript
function fetchData() {

}

fetchData()
```

in the fetchData() function, we will add the code that fetches data from the JSON file and then create a list on the HTML.

fetch has a simple syntax:

```JavaScript
fetch().then().then().catch()
```

in simple terms:

The first part: `fetch()`, takes in the URL or path to the resource
the following `.then()` blocks, are promises that return the response in the desired format and the other one to display the result or do anything with the result.
`.catch()` takes in the code that runs when something is wrong.

**Download the [countries JSON file](https://github.com/ChrisAchinga/fetch-api-demo/blob/dev/countries.json) and add it in the same folder as the index and script files.**

Lets, add the path to our data file:

```JavaScript
fetch('countries.json')
```

Your current js file should now contain:

```JavaScript
function fetchData() {
    fetch('countries.json')
}

fetchData()
```

Now let's get our response and make it be in json format:

```JavaScript
.then((res) => res.json())
```

fetch() returns a promise with a response: "res", which we then convert into JSON format

Your current js file should now contain:

```JavaScript
function fetchData() {
    fetch('countries.json').then((res) => res.json())
}

fetchData()
```

We now display our data.
we can test for success using the console,

```JavaScript
function fetchData() {
    fetch('countries.json')
    .then((res) => res.json())
    .then((data) => {
        console.log(data)
    })
}

fetchData()
```

![Console Shots](https://cdn.hashnode.com/res/hashnode/image/upload/v1622204387769/ZKOF4a99U.png)

![console](https://cdn.hashnode.com/res/hashnode/image/upload/v1622204415009/yCgUHcY6n.png)


As you can see on the screenshots, data is shown in an array of data.

Finally, let's add an error handler in the `.catch()`

```JavaScript
function fetchData() {
    fetch('countries.json')
    .then((res) => res.json())
    .then((data) => {
        console.log(data)
    })
    .catch((error) => {
      console.log(`Error Fetching data : ${error}`)
      document.getElementById('country').innerHTML = 'Error Loading Data'
    })
}

fetchData()
```

## Displaying data on the HTML page

We do this from js using the DOM, we access the part of the website: `<div id="country"></div>` .

First update your script file to:

```JavaScript
function fetchData() {
    fetch('countries.json')
    .then((res) => res.json())
    .then((data) => {
        console.log(data)
        let output = '<h2 class="mb-4">Countries</h2>'
        data.forEach(function (item) {
        output += `
        <ul class="list-group mb-3">
          <li class="list-group-item">Country: ${item.Country}</li>
          <li class="list-group-item">CODE: ${item.ISO2}</li>
        </ul>
      `
    })
    .catch((error) => {
      console.log(`Error Fetching data : ${error}`)
      document.getElementById('country').innerHTML = 'Error Loading Data'
    })
}

fetchData()
```

Explanation:

We added

```JavaScript
let output = '<h2">Countries</h2>'
  data.forEach(function (item) {
  output += `
  <ul class="list-group mb-3">
    <li class="list-group-item">Country: ${item.Country}</li>
    <li class="list-group-item">CODE: ${item.ISO2}</li>
  </ul>
  `}
```

First I created the heading and assigned it to the variable 'output'

```JavaScript
let output = '<h2">Countries</h2>'
```

Since the data we get is in an array, we use `forEach()` to loop through the data and display each item.

[forEach() docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

```JavaScript
data.forEach(function (item) {
  // display data here
  }
```

The above code will go through the whole array of data returned.

```JavaScript
output += `
  <ul class="list-group mb-3">
    <li class="list-group-item">Country: ${item.Country}</li>
    <li class="list-group-item">CODE: ${item.ISO2}</li>
  </ul>
  `
```

In the above code, the code takes each item from the array and puts it into a list.

I use the template literals (`string_here`) because it allows the use of variables and also we can add HTML tags to it. we access `${item.Country}` and `${item.ISO2}` which are returned by the data we fetched.

[template literals documentatin](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

Finally we display the data:

```JavaScript
document.getElementById('country').innerHTML = output
```

The above line of code grabs the div with the id of 'country' and using the `.innerHTML` we parse in the variable `output` where we created the list from data fetched.

```JavaScript
function fetchData() {
    fetch('countries.json')
    .then((res) => res.json())
    .then((data) => {
      console.log(data)
      let output = '<h2">Countries</h2>'
      data.forEach(function (item) {
        output += `
        <ul>
          <li>Country: ${item.Country}</li>
          <li>CODE: ${item.ISO2}</li>
        </ul>
      `
      })
      document.getElementById('country').innerHTML = output
    })
    .catch((error) => {
      console.log(`Error Fetching data : ${error}`)
      document.getElementById('country').innerHTML = 'Error Loading Data'
    })
}

fetchData()
```

Now you can view the page with the list of countries:


![country_complete.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622204685031/6fxbNPhGx.png)


### Complete HTML

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>JSON-JS</title>
  </head>
  <body>
    <h1>countries: a long list</h1>
    <div id="country"></div>
    <script src="script.js"></script>
  </body>
</html>
```

### Complete JavaScript

```JavaScript
function fetchData() {
  fetch('countries.json')
    .then((res) => res.json())
    .then((data) => {
      console.log(data)
      let output = '<h2">Countries</h2>'
      data.forEach(function (item) {
        output += `
        <ul>
          <li>Country: ${item.Country}</li>
          <li>CODE: ${item.ISO2}</li>
        </ul>
      `
      })
      document.getElementById('country').innerHTML = output
    })
    .catch((error) => {
      console.log(`Error Fetching data : ${error}`)
      document.getElementById('country').innerHTML = 'Error Loading Data'
    })
}

fetchData()
```

Source code for the demo:

%[https://github.com/ChrisAchinga/fetch-api-demo]

[LIVE DEMO](https://chrisachinga.github.io/fetch-api-demo/)

## Resources:

### Intro to the DOM

https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction

<hr />

### Accessing the dom

https://www.digitalocean.com/community/tutorials/how-to-access-elements-in-the-dom

<hr />

### Intro to fetch (youtube)

https://www.youtube.com/watch?v=Oive66jrwBs&t=1229s
<hr />

### Fetch API

https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

## Intro to fetch

https://developers.google.com/web/updates/2015/03/introduction-to-fetch

https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch