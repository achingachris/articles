## Deploy A React app on GitHub pages

GitHub offers more than just a host for your code. In this short tutorial, I will walk you through deploying a static react app/project on  [GitHub Pages](https://pages.github.com/).

I will be deploying a project I did today (Nov, 28 - 2020). To follow along, feel free to clone or fork the repo. 

Link to the repo:  [GitHub/myRepo](https://github.com/ChrisAchinga/myRepos/tree/174080e27061235d153ff10e51ac0ad3f5661222) 


>A programmer's learning tool is by practicing     --I said that.

Let's Get Started:

## Step 1: Install the Dependencies:

I use npm for my projects, so after cloning the repo, open the project on your terminal or cmd (windows) and execute:

```shell
npm install
```

### Install the *gh-pages* package as a dev-dependency of the app

```shell
npm install gh-pages --save-dev
```

## Step 2: Define Homepage in package.json

In the `package.json` file in your react app and add homepage property using the given syntax:

```shell
http://{username}.github.io/{repo-name}
```

where {username} is your GitHub username, and {repo-name} is the name of the GitHub repository. Below is an example for my project:

```json
"homepage": "http://ChrisAchinga.github.io/myRepos",
```

![screenshotpng](https://cdn.hashnode.com/res/hashnode/image/upload/v1606575051396/lUBJUjw-F.png)

## Step 3: Deploy script in `package.json` file

Now we can add the deploy script in the package.json file. In the existing scripts property, add a predeploy property and a deploy property, each having the values shown below:

```json
"scripts": {
  // some code before
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build"
}
```

So your "scripts" should look like this:

![Screenshot from 2020-11-28 17-56-54.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606575468680/qe4IOKIDk.png)

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


Kudos your React app is ready for view... on https://chrisachinga.github.io/myRepos/

Get The Complete Source Code:

%[https://github.com/ChrisAchinga/myRepos]

