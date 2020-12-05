## Make You Forms Function With Netlify Forms

It's normal to have a back-end on your website for your forms to be functional. Say no More!.  

 [Netlify](https://www.netlify.com/)  offers hosting to static websites and serverless technologies, and it comes with super great feature including form handling, yes without a back-end.

Let's build a form with Netlify:

What you will need:

- Netlify account
- GitHub account

First off let's start with a simple html form:

Create a new html file and paste in the form below:


```html
      <form method="post" name="Friends">
        <p>
          <label for="friend-name">Name:</label>
          <input type="text" name="name" id="name" />
        </p>
        <p>
          <label for="Country">Country Of Residence:</label>
          <input type="text" name="country" id="country" />
        </p>
        <p>
          <label for="stack">Your Tech Stack:</label>
          <select id="stack" name="stack">
            <option value="front-end">Front-End</option>
            <option value="back-end">Back-End</option>
            <option value="mobile-developer">Mobile-Developer</option>
            <option value="full-stack">Full-Stack</option>
          </select>
        </p>
        <p>
          <input type="submit" />
        </p>
      </form>
``` 
[The Complete Html File](https://gist.github.com/sryderdev/01cdd80f79bc9f7c9bbfc6f8f9d8226c)

We have a simple forms that takes in few inputs from a user. Now that we have that, let's deploy the site from Netlify. (Add the file to your new GitHub Repository and deploy form netlify by linking the repo)

## Netlify Forms

To start using forms, you only need to a few attributes to your <form> tag.
You can either use `netlify` or `data-netlify="true"`

```html
<form method="post" name="Friends" netlify>
``` 

```html
<form method="post" name="Friends" data-netlify="true">
``` 

Use any attribute that makes you feel comfortable. Just like that, you have a functional form on your static site, for real!

To test your form, go the url provided by netlify and submit and entry


![form-submitted.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607168091527/PHIFtnmcI.png)

To view your submissions, head over to Netlify dashboard under the Forms tab.


![dash.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607168264276/a-wl1WVyI.png)

Click on the name of the form to view the submission. Just like you are done.

## Adding a Customized response page

Create a new html form, `success.html` and copy the code below, or add your own success message code:


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <title>Success</title>
    <link
      rel="stylesheet"
      href="https://bootswatch.com/4/slate/bootstrap.min.css"
    />
    <!-- Custom styles for this template -->
    <link href="cover.css" rel="stylesheet" />
  </head>
  <body class="text-center">
    <div class="cover-container d-flex w-100 h-100 p-3 mx-auto flex-column">
      <main role="main" class="inner cover">
        <p class="lead">
          <a href="#" class="btn btn-lg btn-secondary"
            >Thank You, I have Recieved Your Details Buddy</a
          >
        </p>
      </main>
    </div>
  </body>
</html>
``` 

After that add an action attribute to you opening <form> tag:

```html
<form method="post" name="Friends" action="/success.html" netlify>
``` 

After that, update the GitHub repository and refresh your page and try out the new changes, see what happens after submitting another form.

The new customized response page.

![success.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607169351364/3xpAA50Vp.png)

The End!! Watch out for more interesting articles by subscribing to my newsletter on my  [my blog](https://chrisdev.hashnode.dev/)

[My Profile](http://chrisachinga.me)
