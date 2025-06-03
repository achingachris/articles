---
title: "Creating A Weather Search App in Vanilla JavaScript"
datePublished: Thu Sep 22 2022 20:42:36 GMT+0000 (Coordinated Universal Time)
cuid: cl8dit46e03bowpnv8unxh9ri
slug: creating-a-weather-search-app-in-vanilla-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/TKlxhlRdj9A/upload/v1662704839483/FenhyLAWU.jpeg
tags: javascript

---

This post covers creating a simple weather search application using plain JavaScript, HTML, and CSS.

## Demo and Source Code

The project demo is live on [codesandbox](https://codesandbox.io/s/weather-robot-phase-1-lzt9z9), and the source code is available on [GitHub](https://github.com/achingachris/weather-robot).

%[https://codesandbox.io/embed/weather-robot-phase-1-lzt9z9?fontsize=14&hidenavigation=1&theme=dark]

## Prerequisites

1. [Openweathermap](https://openweathermap.org/) API Keys
2. JavaScript Fetch API and DOM Manipulation
3. Basic HTML and CSS

## Creating the HTML and CSS Files

Create a new file (index.html) and add the following:

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Weather Robot</title>
    <link rel="stylesheet" href="./weatherRobot.css" />
  </head>
  <body>
    <section class="section-head">
      <div class="container">
        <h1 class="heading">Weather Robot</h1>
        <form>
          <input type="text" placeholder="Search for a city" autofocus />
          <button type="submit">GET WEATHER</button>
          <span class="msg"></span>
        </form>
      </div>
    </section>
    <section class="city-array">
      <div class="container">
        <ul class="cities"></ul>
      </div>
    </section>
    <script src="./weatherRobot.js"></script>
  </body>
</html>
```


Create separate files for the styles and JavaScript. Inside the CSS file, add the following:

%[https://gist.github.com/achingachris/fffc4c92672843c1d5688f5c2004f9a1]

Open the file on your browser to view the web page

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663869626651/gtK21BXA4.png align="left")

Now let's add some functionality to search and get weather information!

### Getting OpenWeatherMap API Keys:

After signing in to your account, navigate to https://home.openweathermap.org/api_keys to get your API Keys:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663870023461/QK6J75zs0.png align="left")

Inside the js file, add the following at the top:

```js
const form = document.querySelector('.section-head form'),
  input = document.querySelector('.section-head input'),
  msg = document.querySelector('.section-head .msg'),
  list = document.querySelector('.city-array .cities'),
  apiKey = 'API_KEY'
```

Replace the API_KEY with your API Key from [OpenWeatherMap]( https://home.openweathermap.org/api_keys).

In the snippets above, we grab the input to capture the city name entered by a user, `document.querySelector('.section-head input'),` and return the results in a list `list = document.querySelector('.city-array .cities'),`

We then create an event listener to listen for user inputs and query the API to get the weather of the entered city:

```js
form.addEventListener('submit', (e) => {

}
```

Copy the following code inside the event listener function:

%[https://gist.github.com/achingachris/935d15948a95aac09150cd7dc7e99469]

Run the file to view the changes. For every valid city searched, it's added on the card list:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663879328533/e51LVw9KU.png align="left")




