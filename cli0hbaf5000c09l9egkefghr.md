---
title: "Deploying A Django Project on PythonAnywhere"
datePublished: Tue May 23 2023 16:16:48 GMT+0000 (Coordinated Universal Time)
cuid: cli0hbaf5000c09l9egkefghr
slug: deploying-a-django-project-on-pythonanywhere
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684858572125/fc43fd62-e06e-4b91-81e9-ee5c4f7c794d.png
tags: python, deployment, django, django-rest-framework

---

Deploying a Django project on [PythonAnywhere](https://pythonanywhere.com/) lets you make your web application accessible online. With PythonAnywhere, you can create a web app, configure it with a WSGI file, and host your Django project seamlessly.

This article provides a comprehensive, step-by-step guide to help you deploy your existing Django project on PythonAnywhere successfully.

## Prerequisites:

* [Pythonanywhere](http://pythonanywhere.com) Account
    
* An existing Django project is ready for deployment.
    
* GitHub (Code Repo)
    
* Basic Familiarity with Django and the command line interface
    

For demo purposes, please refer to the following project: It’s a voting app from the official [Django Tutorial](https://docs.djangoproject.com/en/4.2/intro/tutorial01/)

%[https://github.com/achingachris/Django-Polls-Tutorials] 

## Uploading Your Code to pythonanywhere

Open a console(terminal) on your pythonanywhere dashboard:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684829498793_image.png align="left")

Just click on the blue bash button to open a terminal-like page:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684829640577_image.png align="left")

If your Django project is hosted on a code-sharing platform like GitHub or Bitbucket, you can clone it directly onto PythonAnywhere using a Bash console. Here's an example command:

```bash
git clone https://github.com/achingachris/Django-Polls-Tutorials.git
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684829792342_image.png align="left")

Alternatively, as mentioned in the [documentation](https://help.pythonanywhere.com/pages/FileBrowser/), you can explore other methods of uploading and downloading files on PythonAnywhere.

## Set Up a Virtual Environment and Install Dependencies

Create a virtual environment in the Bash console on PythonAnywhere and install Django and any other project dependencies.

To do so, use the command:

```bash
 mkvirtualenv --python=/usr/bin/python3.10 <environment name>
```

Replace `<environment name>` with any name, you want to give to your virtual environment.

So for the demo, I will use:

```bash
mkvirtualenv --python=/usr/bin/python3.10 polls
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684830849405_image.png align="left")

To install the dependencies, change the active directive on your console to the folder cloned from GitHub(or uploaded):

```bash
cd projectname
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684830986580_image.png align="left")

Ensure you have the `requirements.txt` file

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684831011630_image.png align="left")

To install the dependencies, run:

```bash
pip install -r requirements.txt
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684833355188_image.png align="left")

## Configure the Web App and WSGI File

To set up your Django project on PythonAnywhere, follow these steps:

**Create a Web app with Manual Configuration:**

Navigate to the "Web Apps" tab on PythonAnywhere and create a new web app.

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684833813223_image.png align="left")

Select the default domain for free accounts

Choose the "Manual Configuration" option and select the appropriate Python version matching your virtual environment.

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684833863638_image.png align="left")

Choose a Python version: (preferably v3.10)

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684833898978_image.png align="left")

You will get notified that you have to set up the configuration manually:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684833949439_image.png align="left")

**Specify the Virtual Environment:**

Scroll down to the "virtualenv" section of the web app configuration, and enter the name of your virtual environment (e.g., polls).

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684834346841_image.png align="left")

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684834404220_image.png align="left")

**Edit the WSGI File:**

Scroll down to the “Code” section of the web app configuration.

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684834948790_image.png align="left")

Click the link and make the necessary changes to the WSGI file. You will be redirected to an in-browser text editor view:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684835028478_image.png align="left")

Delete everything except the Django section and then uncomment that section. Your WSGI file should look something like this:

```python
# +++++++++++ DJANGO +++++++++++
    # To use your own Django app use code like this:
    import os
    import sys
    
    # assuming your Django settings file is at '/home/myusername/mysite/mysite/settings.py'
    path = '/home/myusername/mysite'
    if path not in sys.path:
        sys.path.insert(0, path)
    
    os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'
    
    ## Uncomment the lines below depending on your Django version
    ###### then, for Django >=1.5:
    from django.core.wsgi import get_wsgi_application
    application = get_wsgi_application()
    ###### or, for older Django <=1.4
    #import django.core.handlers.wsgi
    #application = django.core.handlers.wsgi.WSGIHandler()
```

Edit the code to configure your Django application. For the demo, the project name is `polls` , and my username is `chrisachinga`:

```python

import os
import sys
    

path = '/home/chrisachinga/polls'
   if path not in sys.path:
      sys.path.insert(0, path)
    
os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684835430356_image.png align="left")

Remember to save after editing the file.

**Database Setup**

We will use the simple SQLite database for this demo, so no extra configuration is needed.

Go to the **Consoles tab**, start a bash console, and use `cd` to navigate to the directory where your Django projects [`manage.py`](http://manage.py) lives, then run:

```bash
 ./manage.py migrate
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684835727344_image.png align="left")

(ignore the warnings 🤣🤣)

You can now check if everything is okay. Click the link on the web tab to view the deployed version: *“*[*chrisachinga.pythonanywhere.com*](http://chrisachinga.pythonanywhere.com)*”*

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684835867965_image.png align="left")

On loading the site, it’s most likely to get this error: `DisallowedHost`:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684836176767_image.png align="left")

Here's how you can solve it:

Open the Django settings file (`settings.py`) in your project. Locate the `**ALLOWED_HOSTS**` variable. It should be a list or tuple.

Add `'`[`chrisachinga.pythonanywhere.com`](http://chrisachinga.pythonanywhere.com)`'` to the list of allowed hosts. Example:

```python
ALLOWED_HOSTS = ['localhost', '127.0.0.1', 'chrisachinga.pythonanywhere.com']
```

I edited mine on GitHub:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684836432033_image.png align="left")

Note: Include any other domains or IP addresses you want to allow access to your site.

To update the code on pythonanywhere, you can pull the code from the terminal:

```bash
git fetch
git pull
```

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684836548875_image.png align="left")

After that, head back to the web application tab and reload the site:

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684836588392_image.png align="left")

And now, when I load the site on: IT WORKS!

[https://chrisachinga.pythonanywhere.com/polls/](https://chrisachinga.pythonanywhere.com/polls/)

![](https://paper-attachments.dropboxusercontent.com/s_4B15B70D4A39164626C86C6661B2784280421D19B08714EB934B2D139F4C323D_1684836631588_image.png align="left")

**Next Steps:**

You can interact with the Django shell and API on the console to create a superuser, migrate databases, and more. Just ensure the virtualenv is turned on.

## **Conclusion:**

Following this step-by-step guide, you can successfully deploy your Django project on PythonAnywhere. Remember to adapt the instructions to match your project's specific configuration and requirements. PythonAnywhere offers a convenient platform for hosting your Django application, allowing you to share your web app with users across the internet. Enjoy the benefits of a live Django site hosted on PythonAnywhere and provide an exceptional user experience.