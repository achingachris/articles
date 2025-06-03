---
title: "Deploying A React app on GitHub Pages"
seoTitle: "Deploy a react app using GitHub pages"
seoDescription: "Using GitHub Pages to deploy a static react app for free, straight from your GitHub repo"
datePublished: Tue May 25 2021 14:47:54 GMT+0000 (Coordinated Universal Time)
cuid: cki1u90je01jukus12bpraivl
slug: github-pages-with-react
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1621953722862/AM7JSCoIY.png
tags: github, deployment, reactjs

---

GitHub offers more than just a host for your code. In this short tutorial, I will walk you through deploying a static react app/project on  [GitHub Pages](https://pages.github.com/).

I will be using one of my React projects from GitHub:

%[https://github.com/achingachris/myRepos]

>A programmer's learning tool is by practicing     --I said that...

Let's Get Started:

**This tutorial assumes you already have your react project setup and ready to deploy**

## Step 1: Install the Dependencies (gh-pages):

I use npm for my projects, so while in your project root directory, open the project on your terminal or cmd (windows).

### Install the *gh-pages* package as a dev-dependency of the app

```shell
npm install gh-pages --save-dev
```

## Step 2: Define Homepage in package.json

In the `package.json` file in your react app and add homepage property using the given syntax:

```shell
http://{username}.github.io/{repo-name}
```

Where {username} is your GitHub username, and {repo-name} is the name of the GitHub repository. Below is an example for my project:

```JSON
"homepage": "http://achingachris.github.io/myRepos",
```

```JSON
{
  "name": "myrepos",
  "homepage": "http://achingachris.github.io/myRepos",
  "version": "0.1.0",
  "private": true,
}
```

## Step 3: Deploy script in `package.json` file

Now we can add the deploy script in the package.json file. In the existing scripts property, add a predeploy property and a deploy property, each having the values shown below:

```JSON
"scripts": {
  // some code before
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build"
}
```

So your "scripts" should look like this:

```JSON
{
  "scripts": {
    "start": "react-scripts start",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
}
```

## Step 4: Deploy Your App
Update your GitHub repository using git commands:

```shell
npm run deploy
```

## Step 5: Commit and Push to GitHub

On your project terminal, run the deploy script

```shell
git add .
git commit -m "gh-pages deploy"
git push
```

Kudos your React app is ready for view... on  the URL: 

```txt
https://{github-user-name}.github.io/{repo-name}/
```

https://achingachris.github.io/myRepos/

[Deployment Preview](https://achingachris.github.io/myRepos/)

### Resources For GitHub Pages

- https://pages.github.com/






