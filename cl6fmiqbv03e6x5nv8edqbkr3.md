## Adding Forms To Static Websites Using FabForm

Static websites are known for a minimum to zero functionalities. Initially, one has to write a lot of code to be able to collect data from users through forms. This post will guide you on how to add forms to a static website without creating a server-side application for your website.

You will be using [FabForm](https://fabform.io/). FabForm allows you to add form functionalities to a static website with a simple setup procedure.

## Prerequisites

- FabForm Account - Create a free account [here](https://app.fabform.io/signup)
- A static Webpage 

## Demo

You can find the live demo on Codesandbox:

%[https://codesandbox.io/embed/pedantic-euler-rkqk4g?fontsize=14&hidenavigation=1&theme=dark]

Source code available on [GitHub](https://github.com/achingachris/staticpages-form)

## Creating a Static site

You can skip this step if you already have a static site. You will set up a simple NextJS site that asks for the user's best programming language and JavaScript framework.

To create a NextJS project, run the following command on your terminal:

```shell
npm create-next-app best-language
```

You will style the page using [Bootstrap](https://getbootstrap.com/). Install it by running:

```shell
npm install bootstrap@5.2.0
```

Once the installation is complete, open the `index.js` file and paste the code below:

%[https://gist.github.com/achingachris/8a1ccc1a10ff39bffdd70427bb30272e]

Run the local server to view the changes made:

```shell
npm run dev
```

Open your browser and go to `http://localhost:3000/`:

![simple form](https://cdn.hashnode.com/res/hashnode/image/upload/v1659648912229/IwlBP048b.png align="left")

After setting up the dummy form, head over to https://fabform.io/ to create an account and follow the steps below to make the form collect data.

## Using FabForm

After creating a free account, head to https://app.fabform.io/forms to create an endpoint for your form.

![Creating an endpoint](https://cdn.hashnode.com/res/hashnode/image/upload/v1659649268035/b6CSrGWhD.png align="left")

Once the endpoint is created, you will be redirected to https://app.fabform.io/forms, where all your endpoints are listed:

![FabForm Endpoints](https://cdn.hashnode.com/res/hashnode/image/upload/v1659649372632/2wckSUFHc.png align="left")

To edit your endpoint, click on it, and click on the settings icon on the right side of the page:

![endpoint settings](https://cdn.hashnode.com/res/hashnode/image/upload/v1659649497570/wWUWYoezf.png align="left")

Enter a targeted email where you will be notified for every response. You can add the sheet ID on the endpoint settings if you need to have the responses in a Google Sheet. 

> Note: Add `fabform@fabform.iam.gserviceaccount.com` as an editor to the google sheet document linked.

Click save after adding all the details needed.

![Screenshot from 2022-08-05 00-49-23.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659649775718/OTnJaS3mH.png align="left")

The last step is to add an action attribute to your form:

```
<form
  id='contactForm'
  action='https://fabform.io/f/{form_id}'
  method='post'
>
</form>
```

Replace the `{form_id}` with your endpoint ID. 

For the demo, I will showcase and use my endpoint id in the form:

%[https://gist.github.com/achingachris/f3476d135cd019724bf2a59c3a78f7a3]

Run the development server to test the form now. After submitting, check the Google Sheet document for any changes:

![Screenshot from 2022-08-05 01-23-15.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659651813843/sF27e1wHi.png align="left")

The response updates on your Google Sheet as shown:

![Screenshot from 2022-08-05 01-24-03.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659651881616/ZJuaG1Pbl.png align="left")

## Conclusion

The post demonstrates how to add functionality to a form on a static web application with fewer configurations using FabForm.