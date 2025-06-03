---
title: "5 JavaScript Console Methods you should Know"
seoTitle: "JavaScript Console Methods"
datePublished: Thu Apr 29 2021 11:48:15 GMT+0000 (Coordinated Universal Time)
cuid: cko2tpn4r01aeels1a26k9fwo
slug: 5-javascript-console-methods-you-should-know
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1619522015595/SZqq8TSto.png
tags: javascript, debugging, 2articles1week

---

All web developers are probably familiar with using the web console as their debugging tool. The most common way is using the famous `console.log` tool that JavaScript provides.

The `console` has more than just the `.log()` method that could be helpful. Check out some of the methods you could use:

## 1. `console.log()`

>This is the most used method of all

It outputs messages to the web console. The message may be of any data type.
can also pass in variables and functions as parameters.

Examples:

```javascript
console.log('A message to the console')

console.log(451999)
```

![console-log.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619522610442/3AWlG_1_p.png)

There are a lot of things you could do with the `.log()`:

### Showing a variable content:

```javascript
let name = 'hashnode blog'

// displaying contents stored in name variable to the console
console.log(name)
```

### Calling a function

```javascript
const Hello = str => {
 return `Hello ${str}`
}

console.log(Hello('World'))
```

## 2.` console.error()`

This is used to output error messages on the web console. 

Errors shown are in red text and have a light red background color.

![error.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619527317584/Z6hCMbLqr.png)

## 3. `console.warn()`

It's used to output warning messages on the web console.

Warning texts will be in yellow over a light-yellow background on the console.

![warning.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619527561456/5l9S2iDL0.png)

## 4. `console.table()`

The method is used to display groups of data in a tabular layout on the web console.
helps visualize complex data in form of arrays and objects in a tabular form.
takes in two arguments, the data and the columns to be displayed.

### Displaying Arrays

```javascript
// an array of strings
console.table(["apples", "oranges", "bananas"]);
```

![tablearray.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619528089006/lxecU9L5k.png)

### Objects

```javascript
// an array of objects

function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

var john = new Person("John", "Smith");
var jane = new Person("Jane", "Doe");
var emily = new Person("Emily", "Jones");

console.table([john, jane, emily]);
```

![table-array.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619528575418/_MjUJpBGp.png)

## 5. `console.clear()`

This one clears everything from your console.

## Conclusion 

Visit  [MDN DOCS](https://developer.mozilla.org/en-US/docs/Web/API/Console) to learn more about the console API and its methods
