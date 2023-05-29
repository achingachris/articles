---
title: "How to Fetch Data from an API in Angular"
datePublished: Mon May 29 2023 08:46:11 GMT+0000 (Coordinated Universal Time)
cuid: cli8luwoz000809l03uhneypa
slug: how-to-fetch-data-from-an-api-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685348611602/e923643f-095a-46e1-969c-4ee8d88fdf11.png
tags: angularjs, apis, typescript

---

*The Dad Jokes App: Spreading Laughter One Click at a Time*

This article will demonstrate how to get data from external APIs in an Angular project.

> Humor has a unique way of brightening up our day and creating moments of joy. In the digital age, countless apps cater to various interests, and one app that stands out is the Dad Jokes App. This lighthearted application brings a collection of witty and groan-inducing dad jokes to your fingertips, ensuring laughter is just a click away. In this article, we'll explore the features and development of the Dad Jokes App and its impact on users' daily lives.

## Prerequisites

* NodeJs Installed
    
* [Basic Angular Knowledge](https://angular.io/start)
    
* Angular CLI installed
    

*NOTE:* *The demo is using Tailwind CSS to get started with the starter, clone the repository:*

%[https://github.com/achingachris/dad-jokes-angular/tree/tailwindconfig] 

## Creating an Angular Project

[To create an Angular project](https://angular.io/start), be sure to have installed the Angular CLI on your local environment:

```bash
    npm install -g @angular/cli
```

You can learn more about the Angular CLI here:

[https://angular.io/cli](https://angular.io/cli)

To start a new Angular project, run the following script on a terminal (CMD):

```bash
    ng new dad-jokes
```

You will be prompted to select some choices for configurations. You can go with the defaults for this article.

![image](https://paper-attachments.dropboxusercontent.com/s_1CECAC8753046AB8EC9C674C2B7E5173AED9DC682FB51D4CFF7EE651B0C370CF_1685303162823_image.png align="left")

## Running Angular Locally

Navigate to the project's root directory:

```bash
    cd dad-jokes
```

Run the following command to start the Angular development server:

```bash
    ng serve
```

![image](https://paper-attachments.dropboxusercontent.com/s_1CECAC8753046AB8EC9C674C2B7E5173AED9DC682FB51D4CFF7EE651B0C370CF_1685303734553_image.png align="left")

Open your browser and visit [`http://localhost:4200`](http://localhost:4200**). You should see the default Angular app running successfully.

![image](https://paper-attachments.dropboxusercontent.com/s_1CECAC8753046AB8EC9C674C2B7E5173AED9DC682FB51D4CFF7EE651B0C370CF_1685303774742_image.png align="left")

## Creating a Service:

An Angular service class provides reusable functionality to your Angular application. Services typically handle data access, business logic, and other tasks not specific to a particular component. Services are defined using the `@Injectable()` decorator, which tells Angular that the class can be injected into other classes as a dependency. This allows you to easily share code and data between different parts of your application.

This article will use an Angular service to get data from an API.

To create a new service, run the following:

```bash
    ng generate service jokes
```

A new file will be created, `src/app/jokes.service.ts`. Here, we will define the service to get data from an API.

```typescript
    import { Injectable } from '@angular/core';
    @Injectable({
      providedIn: 'root'
    })
    export class JokesService {
      constructor() { }
    }
```

Update the code to request an HTTP API request and retrieve the jokes.  
We will use the API: [`https://icanhazdadjoke.com`](https://icanhazdadjoke.com) to fetch random “dad” jokes

Here's an example implementation:

```typescript
    import { Injectable } from '@angular/core';
    import { HttpClient } from '@angular/common/http';
    import { Observable } from 'rxjs';
    @Injectable({
      providedIn: 'root',
    })
    export class JokesService {
      url = 'https://icanhazdadjoke.com';
      constructor(private http: HttpClient) {}
      getJoke(): Observable<any> {
        return this.http.get(this.url, { headers: { Accept: 'application/json' } });
      }
    }
```

This service is used to get jokes from the [`icanhazdadjoke.com`](http://icanhazdadjoke.com) API. The `JokesService` class is decorated with the `@Injectable()` decorator, which tells Angular that the class can be injected into other classes as a dependency. This allows you to easily share code and data between different parts of your application.

The `JokesService` class has a single property, URL, and URL of the [`icanhazdadjoke.com`](http://icanhazdadjoke.com) API. The class also has a constructor that takes an instance of the `HttpClient` service as a dependency. The `HttpClient` service is used to make HTTP requests to the [`icanhazdadjoke.com`](http://icanhazdadjoke.com) API.

The `JokesService` class has a single method, `getJoke()`, which returns an `Observable` of type `any`. The `getJoke()` method requests an HTTP to the [`icanhazdadjoke.com`](http://icanhazdadjoke.com) API and returns an `Observable` of the response data. The `Observable` can be subscribed to in order to get the joke data.

## Rendering Data:

Now, let's render the fetched joke in our app's component. Open the `src/app.component.ts` file.

Start by importing the JokesService:

```typescript
    import { JokesService } from './jokes.service';
```

We then update the `AppComponent()` class:

```typescript
    export class AppComponent {
      joke: string = '';
      title = 'Dad jokes';
      constructor(private jokeService: JokesService) { }  
      fetchJoke(): void {
        this.jokeService.getJoke().subscribe((data: any) => {
          this.joke = data.joke;
        });
      }
    }
```

Code explanations:

* The `joke` property is a string that will hold the joke that is fetched from the API.
    
* The `constructor` method takes an instance of the `JokesService` class as a dependency. The `JokesService` class is used to fetch jokes from an API.
    
* The `fetchJoke()` method calls the `getJoke()` method on the `JokesService` class and subscribes to the returned Observable.
    

The `fetchJoke()` method is called when the application is loaded. The method calls the `getJoke()` method on the `JokesService` class. The `getJoke()` method returns an `Observable` of type `any`. The `Observable` emits an object that contains the joke data. The callback function passed to the `subscribe()` method is called when the `Observable` emits a value. The callback function sets the `joke` property to the `joke` property of the object that was emitted by the `Observable`.

The complete `src/app.component.ts` file:

```typescript
    import { Component } from '@angular/core';
    import { JokesService } from './jokes.service';
    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {
      joke: string = '';
      title = 'Dad jokes';
      constructor(private jokeService: JokesService) { }  
      fetchJoke(): void {
        this.jokeService.getJoke().subscribe((data: any) => {
          this.joke = data.joke;
        });
      }
    }
```

Next, we update our web view by opening the `**app.component.html**` file. Update the file:

```typescript
    <nav class="bg-blue-500 p-4">
      <div class="container mx-auto flex items-center justify-between">
        <a href="#" class="text-xl font-bold text-white">Dad Jokes</a>
      </div>
    </nav>
    <div class="container mx-auto text-center">
      <h3 class="mb-4 text-3xl font-bold">Don't Laugh Challenge</h3>
      <div id="joke" class="mb-4 rounded-lg bg-gray-200 p-4">{{ joke }}</div>
      <button
        id="jokeBtn"
        class="rounded-lg bg-blue-500 px-4 py-2 text-white"
        (click)="fetchJoke()"
      >
        Get Another Joke
      </button>
    </div>
```

Reload your browser to view the changes:

![image](https://paper-attachments.dropboxusercontent.com/s_1CECAC8753046AB8EC9C674C2B7E5173AED9DC682FB51D4CFF7EE651B0C370CF_1685306172159_image.png align="left")

NOTE: The demo above used Tailwind CSS to get started with the starter, clone the repository:

%[https://github.com/achingachris/dad-jokes-angular/tree/tailwindconfig] 

The complete source code is available on GitHub:

%[https://github.com/achingachris/dad-jokes-angular] 

## Conclusion:

In this article, we explored how to fetch data from an API using Angular. We covered the prerequisites, setting up an Angular project, fetching jokes from an API using a service, rendering the data in the app's component, and deploying the app on Vercel. With the app up and running, users can now enjoy a delightful collection of dad jokes, spreading laughter one click at a time.

A live demo of the app can be view here:

[https://dad-jokes-angular.vercel.app/](https://dad-jokes-angular.vercel.app/)