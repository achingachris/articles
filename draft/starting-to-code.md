# Ready Set, Wait... Go

>Okay funny tittle but we all know how hard it is to giving names, especialy when it comes to variables. 

But it is easy to start programming with little or null knowledge at all. Let's get started.

## Summary

- Pilot
- Getting a Text Editor
- Creating Your First File
- Deploying your Code
- Finding next projects
- Keep Practicing
  
## Pilot

The easiest way to becoming a programmer is by doing what I did. It was a simple html page that printed the obvious "Hello Word!". Sure you could do that in many other languages. But this article will help you make the first step into programming by coding a simple and basic website using HTML, CSS and JavaScript.

## Getting a text editor
A text editor is the software or application where you will create and edit your code. A document of course. There are alot of text editors available, Google comes in handy but here is a list of a few of my favorites:

1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Atom](https://atom.io/)
3. [Sublime Text](https://www.sublimetext.com/)
   
My personal favorite is VSCode, but they all do the same tasks after all.

You may want to install a text editor if you don't have one.

## Creating your first file

First of all, I'll open my editor (VSCode), as shown in the image below:

![vscode window](../static-files/vsc.png)

To create a new file, use the shortcut `ctr + N` or click on `File` on the tool bar on top and select `New File`.

After a new `Untitled file` appears, use the shortcut keys <kbd>ctrl + s</kbd> to save the file.

Create a new folder from the dialog box and name the files as `index.html`. After hitting save, you'll notice a HTML logo appears. That is because the .html extension indicates that the file contains a HTML markup.

I will use emmet extension to create a starting HTML template. To learn more on what Emmet is and how usefull it is, visit [https://code.visualstudio.com/docs/editor/emmet](https://code.visualstudio.com/docs/editor/emmet).

On the empty file, use <kbd>shit + 1</kbd> the tap on <kbd> tab </kbd>. The follwoing code will be populated on your index file.


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

Here is a list of resources where you can learn more on HTML:
- [Freecode Camp](https://www.freecodecamp.org/learn/): (Responsive Web Design Certification)
- [Codecademy](https://www.codecademy.com/learn/paths/web-development)
  
And many more, Just Google it!

Now that's the basic HTML stucture. Let's add something and open our little project a web browser.

Add the code below between the ```<body> </body>``` tags:

```html
    <header>
        <h1>
            Starter Files
        </h1>
    </header>
    <main>
        <section>
            <h2>
                Heading
            </h2>
            <p>
                This is web page sections
            </p>
        </section>
        <section>
            <h2>
                What!
            </h2>
            <p>
                The last Heading
            </p>
        </section>
    </main>
```

Your file should be like the one below:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Starter</title>
</head>
<body>
    <header>
        <h1>
            Starter Files
        </h1>
    </header>
    <main>
        <section>
            <h2>
                Heading
            </h2>
            <p>
                This is web page sections
            </p>
        </section>
        <section>
            <h2>
                What!
            </h2>
            <p>
                The last Heading
            </p>
        </section>
    </main>
</body>
</html>
```

Your file is ready for a page view on a browser.

I use ["Live Server"](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension to run my files, so on my index file, I right click and select `open wuth live server`, 

Well, the page looks, dull, lets add some styles to cheer it up.

To add styles, we use CSS (Cascading Styles Sheet), it makes the page look attractive. CSS files have a .css extension name.

On the current folder where you have the index.html file is, create a new file `style.css`.

We now have to link the new styles file to our index file. Here it's how it's done:

Add this line just below the `<title> </title>` tags:

```html
<link rel="stylesheet" href="style.css">
```
