---
title: "Building a Weather and Time Telegram Bot using Node.js"
datePublished: Mon May 15 2023 08:59:57 GMT+0000 (Coordinated Universal Time)
cuid: clhom6ow0000l09l63iv9dk9o
slug: building-a-weather-and-time-telegram-bot-using-nodejs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684140444193/8c2fd6ad-50b2-43c8-b6be-5a6ab1a43189.png
tags: bot, nodejs, telegram, 2articles1week

---

[Telegram](https://telegram.org/) bots are automated applications that run inside Telegram. Users can interact with bots by sending messages, commands, and inline requests. Today, we'll walk you through how to build a simple Telegram bot using Node.js that provides weather and time information for any city.

## **Prerequisites**

Before we start, make sure you have the following:

* Node.js and npm are installed on your machine.
    
* A Telegram account to create and manage bots.
    
* An API key from OpenWeatherMap.
    

## **Setting Up Your Project**

Firstly, install the required Node.js packages: `dotenv`, `node-telegram-bot-api`, `axios`, and `moment-timezone`.

`npm install dotenv node-telegram-bot-api axios moment-timezone`

* `dotenv`: To handle environment variables.
    
* `node-telegram-bot-api`: To interact with the Telegram Bot API.
    
* `axios`: To make HTTP requests to the OpenWeatherMap API.
    
* `moment-timezone`: To handle time and time zones.
    

## **Creating the Bot**

You'll need a bot token from Telegram. Use the [BotFather](https://t.me/BotFather) to create a new bot and get the token. Save the token and your [OpenWeatherMap](https://home.openweathermap.org/api_keys) API key in a `**.env**` file:

```plaintext
TELEGRAM_BOT_TOKEN=your_telegram_bot_token OPENWEATHERMAP_API_KEY=your_openweathermap_api_key
```

![](https://paper-attachments.dropboxusercontent.com/s_62AE45369E0CC4290E70D12C6A4561E35C0E74490B9B9B0824AFE428A244885D_1684138152939_image.png align="left")

In your main JavaScript`(app.js)` file, initialize your bot and the storage object:

```javascript
require('dotenv').config()

const TelegramBot = require('node-telegram-bot-api') const axios = require('axios') const moment = require('moment-timezone')

const TELEGRAM_BOT_TOKEN = process.env.TELEGRAM_BOT_TOKEN const OPENWEATHERMAP_API_KEY = process.env.OPENWEATHERMAP_API_KEY

const bot = new TelegramBot(TELEGRAM_BOT_TOKEN, { polling: true }) const storage = {}
```

The `storage` object will keep track of the state of the conversation with each user.

## **Handling Commands and Callback Queries**

Next, handle the `/start` command and present the user with two options: getting the weather or the time. We use an inline keyboard for this:

```javascript

bot.onText(/\/start/, (msg) => {
  const chatId = msg.chat.id
  bot.sendMessage(
    chatId,
    'Hello! This bot can show you the weather and time for any city. To use it, please choose an option below:',
    {
      reply_markup: {
        inline_keyboard: [
          [{ text: 'Get Weather', callback_data: 'get_weather' }],
          [{ text: 'Get Time', callback_data: 'get_time' }],
        ],
      },
    }
  )
})
```

The bot then listens for button presses and asks the user to enter the name of a city:

```javascript

bot.on('callback_query', async (callbackQuery) => {
  const chatId = callbackQuery.message.chat.id
  const data = callbackQuery.data

  switch (data) {
    case 'get_weather':
      const userDataWeather = getUserData(chatId)
      userDataWeather.waitingForCity = true
      userDataWeather.waitingForWeather = true
      bot.sendMessage(chatId, 'Please enter the name of the city or send /stop to cancel:')
      break
    case 'get_time':
      const userDataTime = getUserData(chatId)
      userDataTime.waitingForCity = true
      userDataTime.waitingForTime = true
      bot.sendMessage(chatId, 'Please enter the name of the city or send /stop to cancel:')
      break
    default:
      break
  }
})
```

## **Handling User Responses**

The `**getUserData**` function initializes or retrieves the user's state from the `**storage**` object:

```javascript
function getUserData(chatId) {
  let userData = storage[chatId]
  if (!userData) {
    userData = {
      waitingForCity: false,
      waitingForWeather: false,
      waitingForTime: false,
    }
    storage[chatId] = userData
  }
  return userData
}
```

Then, the bot listens for a message from the user, which should be the city's name:

```javascript

bot.on('message', async (msg) => {
  const chatId = msg.chat.id
  const text = msg.text

  const userData = getUserData(chatId)
  if (userData && userData.waitingForCity) {
    const city = text
    let messageText = ''
    if (userData.waitingForWeather) {
      messageText = await getWeatherData(city)
    } else if (userData.waitingForTime) {
      messageText = await getTimeData(city)
    }
    bot.sendMessage(chatId, messageText)
    resetUserData(chatId)
  }
})
```

We reset the user data after sending the response so the bot is ready for the next command. The `resetUserData` function looks like this:

```javascript

function resetUserData(chatId) {
  const userData = getUserData(chatId)
  userData.waitingForCity = false
  userData.waitingForWeather = false
  userData.waitingForTime = false
}
```

## **Fetching the Weather and Time Data**

The `getWeatherData` function fetches weather data from the OpenWeatherMap API:

```javascript

async function getWeatherData(city) {
  const response = await axios.get(
    `http://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${OPENWEATHERMAP_API_KEY}`
  )
  const weatherData = response.data
  const weatherDescription = weatherData.weather[0].description
  const temperature = Math.round(weatherData.main.temp - 273.15)
  const messageText = `The weather in ${city} is currently ${weatherDescription} with a temperature of ${temperature}°C.`
  return messageText
}
```

The `getTimeData` function gets the current time in the city's local timezone using moment-timezone:

```javascript

async function getTimeData(city) {
  const response = await axios.get(
    `http://api.geonames.org/timezoneJSON?formatted=true&lat=${city.lat}&lng=${city.lon}&username=demo&style=full`
  )
  const data = response.data
  const localTime = data.time
  const messageText = `The current time in ${city} is ${localTime}.`
  return messageText
}
```

## Running The Bot

Update your `package.json` file to run the bot:

```javascript

 "scripts": {
    "start": "node app.js"
  },
```

Run the command on a terminal:

`npm start`

Open your Bot on the Telegram app to test it:

%[https://www.youtube.com/shorts/XwnkYmZfJiU] 

## **Wrapping Up**

This simple bot is a fun way to explore the capabilities of Telegram bots and Node.js. The bot could be expanded in numerous ways, such as supporting more commands, integrating more APIs, or adding a more sophisticated conversation state.

Remember to secure your API keys and tokens properly. Never expose them in your code or version control system. Instead, use environment variables or some form of secure secret management.

%[https://github.com/achingachris/telegram-helper] 

Happy coding!