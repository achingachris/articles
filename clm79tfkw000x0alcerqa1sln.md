---
title: "Setting Up a Django Project"
datePublished: Wed Sep 06 2023 05:00:10 GMT+0000 (Coordinated Universal Time)
cuid: clm79tfkw000x0alcerqa1sln
slug: setting-up-a-django-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693949335779/fb32561b-ee13-4a25-98d2-a56d52c1343a.png
tags: python, django, backend

---

[Django](https://djangoproject.com/)(Python Django) is a high-level web development framework. It provides and flexible project structure and makes it easier to start new projects, In addition to that it follows the Model-View-Controller(MVC) architectural pattern, commonly referred to as Model-View-Template(MVT) in Django.

In this piece, we will document the procedural steps to setting up and installing a Django project.

***While there are a number of ways to get started, feel free to explore available options on the internet and go for whatever makes you comfortable.***

### Prerequisites

Before we get started, here is a checklist:

1. [Python](https://www.python.org/) installed
    
2. [Virtual](https://www.google.com/search?q=python+virtual+environment&oq=python+virt&gs_lcrp=EgZjaHJvbWUqBwgBEAAYgAQyBggAEEUYOTIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIGCAcQRRhB0gEINDM0OGowajeoAgCwAgA&sourceid=chrome&ie=UTF-8) Environment (Recommended to have one): *I will be using virtualenv*
    

### Creating a Virtual Environment(with `virtualenv`)

To get started, we will create a virtual environment to install and run Django. Using `virtualenv` makes it way easier to do so(I think ... 🤔 💭).

Open a terminal (CMD), and go to a working directory or a location where your project files will be. To create an environment, run the following:

```bash
virtualenv <project_name>
```

Replace the &lt;project\_name&gt; with the name of the project, i.e. My project will be: django-starter

```bash
virtualenv django-starter
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693939644618/6338e59a-d28d-4f00-9c35-172ebca41a15.png align="center")

Once that is done, you need to activate the environment. Before you do that, ensure that your terminal is in the project directory, "django-starter".

To activate the environment, run the following:

```bash
source bin/activate
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693939975377/95bbb585-cac3-41f3-9922-9f82e914f609.png align="center")

Once the environment is activated, you will notice the environment will be enclosed by brackets on your terminal path:

`(django-starter) chris@Chriss-MacBook-Pro django-starter %`

To install django, run the following on the terminal/CMD:

```bash
pip install django
```

To confirm a successful installation, you can use `pip freeze` to check for installed packages inside the environment:

```bash
pip freeze
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693946923860/1052b124-6839-4909-97e2-21e96032dcc0.png align="center")

## Creating a Django project

Django has the simplest project structure, you simply create a single django project, where you can have a number of applications inside it. We will start by creating a Django project, and then proceed to creating applications inside it.

To create a project, run the following:

```bash
django-admin startproject <project_name>
```

Replace the `<project_name>` with the project name.

Here's how I prefer to do it since I'm in the root folder of my environment, I'd love all my project configurations to be there, I will therefore run the following to create a django project:

```bash
django-admin startproject config .
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693947640601/1b3ec8cd-bb31-4cde-beef-7d4ffa7faa82.png align="center")

This will create the core files to run and configure your project: `manage.py` and a `config` directory where it will have main settings and URLs for the project.

Note that you won’t be editing the `manage.py` file. Inside the config directory, you will find a `settings.py` file that defines the database, middleware, and more configurations for a Django project.

(Optional Step)

Before we run the server, open the settings.py and go to the TIME\_ZONE variable. Set the timezone to your local time zone (Really helps with real-time logging and debugging)

```python
TIME_ZONE = 'UTC'
```

I will update my timezone to

```python
TIME_ZONE = 'Africa/Nairobi'
```

To test for a successful setup, start the server by running the following:

```python
python manage.py runserver
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693948152964/fca9da85-b8dd-4135-8e23-f260246044f3.png align="center")

Django locally runs on port 8000:

[http://localhost:8000/](http://localhost:8000/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693948561074/0f3ad228-5002-4ce4-8f7d-525de0752f80.png align="center")

This confirms a successful setup.

### Conclusion

This masterpiece has broken down the process of creating a Django project:

1. Setting Up an Environment
    
2. Activating an Environment
    
3. Installing Django
    
4. Creating a Django Project
    

***Note: To deactivate the environment, run the following:***

```bash
deactivate
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693948794408/29789f32-f36b-481f-9a84-7fc986cf87dd.png align="center")

### What Next?

The next article will cover the following:

1. How to create applications in a django project
    
2. How to set Templates and Static files (CSS and JS)
    
3. Writing simple views and URLs