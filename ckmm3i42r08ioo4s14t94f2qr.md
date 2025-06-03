---
title: "How I  made my first website using an API 😎"
datePublished: Tue Mar 23 2021 14:10:33 GMT+0000 (Coordinated Universal Time)
cuid: ckmm3i42r08ioo4s14t94f2qr
slug: how-i-made-my-first-website-using-an-api
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1616507200759/754hkQbO6.png
tags: apis, project-management, 2articles1week

---


![Screenshot from 2021-03-23 14-38-30.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616509550608/pizpKvBm1.png)

A year ago, I was struggling with using APIs to creating a simple website. After some tutorials online I made a simple website that displays the statistics for covid-19. It is not a fancy or unique site, but it did its purpose, TEACH.

## Which API did I use?

I used [`coronavirus-monitor`](https://rapidapi.com/astsiatsko/api/coronavirus-monitor) from [Rapid API platform](https://rapidapi.com/). The API returns an array of countries with average statistics on the number of total infections, deaths, number of people in critical conditions, and number of people recovered. (and many more)

## How I Used The API ...

I used vanilla JS in the application. So to get the data from API, I used `FETCH` in JS.  Here are a few links to getting to know what Fetch is and how to use it:

https://www.digitalocean.com/community/tutorials/how-to-use-the-javascript-fetch-api-to-get-data

https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

So I used two endpoints, one to get the general summary statistics and the other one to get all countries and their details.

#### Summary

```js
//  fetching data starts here ...
fetch('https://coronavirus-monitor.p.rapidapi.com/coronavirus/worldstat.php', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'coronavirus-monitor.p.rapidapi.com',
    'x-rapidapi-key': 'api_key',
  },
})
  .then((response) =>
    response.json().then((data) => {
      console.log(data);
    })
  )
  .catch((err) => {
    console.log(err)
  })
```

The code snippet above fetched data from the URL provided:

```txt
https://coronavirus-monitor.p.rapidapi.com/coronavirus/worldstat.php
```
The Headers interface of the Fetch API allows you to perform various actions on HTTP request and response headers.

#### Country Data

```js
//Fetching The Case by Country Data
fetch(
  'https://coronavirus-monitor.p.rapidapi.com/coronavirus/cases_by_country.php',
  {
    method: 'GET',
    headers: {
      'x-rapidapi-host': 'coronavirus-monitor.p.rapidapi.com',
      'x-rapidapi-key': 'api_key',
    },
  }
)
  .then((response) =>
    response.json().then((data) => {
      // console.log(data)
      let countries_stat = data.countries_stat
      //Getting all the country statistic using a loop
      for (let i = 0; i < countries_stat.length; i++) {
        console.log(countries_stat[i]);
      }
    })
  )
  .catch((err) => {
    console.log(err)
  })
````

Data is fetched from the URL:

```txt
https://coronavirus-monitor.p.rapidapi.com/coronavirus/cases_by_country.php
```

## Displaying Data:

To show data, all I did was play around with the DOM.

At the top of my javascript file, notice how I grabbed various parts of the DOM that I later used. 

```js
let new_cases = document.getElementById('new_case')
let new_death = document.getElementById('new_death')
let total_death = document.getElementById('total_death')
let total_recovered = document.getElementById('total_recovered')
let total_cases = document.getElementById('total_cases')
let table = document.getElementById('countries_stat')
```

An example of parsing the total number of cases reported into the HTML, you don't hard code the numbers in it, you let js do it for you. 😜

```html
<p class="card-text" id="total_cases"></p>
```

## Searching for a Single Country ..?

Since we getting details for all the countries, imagine looking for a single country in the table with more than 100 rows ... 😫😫😫

I actually used w3schools for this feature, so I created a search functionality that begins filtering data immediately a user starts keying characters.

The search input:
```html
<div class="container m-3">
            <input
              class="form-control"
              type="text"
              id="myInput"
              onkeyup="filterTable()"
              placeholder="Search for a Country.."
              title="Type in a name"
            />
          </div>
```

The function:

```js

const filterTable = () => {
  let i, txtValue
  const input = document.getElementById('myInput')
  const filter = input.value.toUpperCase()
  const table = document.getElementById('countries_stat')
  const tr = table.getElementsByTagName('tr')

  for (i = 0; i < tr.length; i++) {
    let td = tr[i].getElementsByTagName('td')[0]
    if (td) {
      txtValue = td.textContent || td.innerText
      if (txtValue.toUpperCase().indexOf(filter) > -1) {
        tr[i].style.display = ''
      } else {
        tr[i].style.display = 'none'
      }
    }
  }
}
```

That's it, that is how I built my first website using an API, it was almost a year ago. 👻

[Source Code](https://github.com/ChrisAchinga/covid19-stats)

[Live Preview](https://rona19stats.netlify.app/)

## NB:

####  COVID-19 affects different people in different ways. Most infected people will develop mild to moderate illness and recover without hospitalization.

Most common symptoms:

- fever
- dry cough
- tiredness

Less common symptoms:
- aches and pains
- sore throat
- diarrhea
- conjunctivitis
- headache
- loss of taste or smell
- a rash on the skin, or discoloration of fingers or toes

[more on covid](https://www.who.int/news-room/q-a-detail/q-a-coronaviruses#:~:text=symptoms)


![Blue 7 Step Prevention Coronavirus Awareness Poster.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616508152667/At00CxAPV.png)

Written with 💜 by [Chris Achinga](https://chrisdev.netlify.app/)

#2Articles1Week




