## Deploying NextJS on Netlify - Starter Template

# Deploying NextJS to production

By default, [NextJS](https://nextjs.org/) applications are easily deployable on [Vercel](https://vercel.com/) with zero configurations. That doesn't mean you shouldn't explore what other platforms have to offer.

To deploy a NextJS application, simply follow the steps below. 
If you want to start straight up without the hustle, use the button below:

[![Deploy on Netlfiy](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/achingachris/next-netlify-starter)

## Create a Netlify Account

On your browser, go to https://app.netlify.com/signup to create your Netlify account.


![Creating a Netlify Account](https://cdn.hashnode.com/res/hashnode/image/upload/v1644080613728/s27NP3fJY.png)

Choose a method that works best with you(I would use GitHub)

## Set Your Next project Ready

Install `@netlify/plugin-nextjs` dependency on your project:

```shell
npm i @netlify/plugin-nextjs
```

On the root of your NextJS project, create a `netlify.toml` file and the following code in the file:

```toml
[build]
  command = "npm run build"
  publish = ".next"

[[plugins]]
  package = "@netlify/plugin-nextjs"

```

>Ensure to update and commit changes on GitHub

##  Deploy on Netlify

To deploy, head over to your Netlify dashboard, https://app.netlify.com/ and create on the `Add New Site` button in the `Site` tab.

![addnew](https://cdn.hashnode.com/res/hashnode/image/upload/v1644082441537/hYhIpMP6B.png)

From the dropdown, select `Import an Existing Project`.

![create-dropdown.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644082852674/JQrAOg-uD.png)

You'll be taken to a new page and asked to pick a Git provider, I will use GitHub.

![pick-git.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644083397211/PSMnVT4zF.png)

Choose the repository with your project in it and proceed to deploy the site. Do not change anything under the `Basic build settings`. 

![build.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644083552224/rtND2bWdb.png)

Click on the `Deploy Site` button and wait for it to complete.

Once the deployment is successful, you are ready to go!

>Netlify offers automatic deploys once you push a commit, and provides a preview link for the build! That is very useful!

View The demo site: https://nextnetlifystarter.netlify.app/

View The Source: https://github.com/achingachris/next-netlify-starter


![next-on-netlify.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644087308025/otfRPzknj.png)

### You Got This



