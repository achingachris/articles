## How To Install WordPress in Windows

Let's get started.

## What you Need

- Xampp installed 

## Downloading WordPress

[WordPress](https://wordpress.org/is an open-source CMS (Content Management System), it's available for free. To download the installation files, head over to https://wordpress.org/download/. 

Follow the following steps to install and start using WordPress locally:

### 1. Unzip the downloaded folder

Unzip the folder and move to `C:\xampp\htdocs` (`htdocs` inside Xampp directory).

Ensure that the document has the `index.php` file among other `.php` files in the root

![file content](https://cdn.hashnode.com/res/hashnode/image/upload/v1644267299430/XJfndSfpS.png)

![Xampp htdocs](https://cdn.hashnode.com/res/hashnode/image/upload/v1644265979518/yQTkDxfOL.png)

Rename the folder to your project name. I will name mine `hashnode`.

## Start Xampp Server

Open Xampp and start Apache and MySQL services.

![Starting XAMPP](https://cdn.hashnode.com/res/hashnode/image/upload/v1644266202583/5qxghzit6.png)

Test if the server is running by going to `http://localhost/dashboard/`

If a similar page like the image below loads up, everything is good to go:

![Local Host Server](https://cdn.hashnode.com/res/hashnode/image/upload/v1644267039756/10w3VtQ2C.png)

## Create Database

On your browser, go to `http://localhost/phpmyadmin/` to create a new database for the new WordPress site.

![phpMyadmin](https://cdn.hashnode.com/res/hashnode/image/upload/v1644267735809/v1PVZuK5d.png)

On the left panel, click on `New` to create a new database. I'll call mine 'hashnode'. Leave other options as they are and click on 'Create'.

##  Configure WordPress

On your browser, open the newly added WordPress site: `http://localhost/{folderName}`. Since I renamed mine to `hashnode`, I'll go to `http://localhost/hashnode`.

Select your language once the page loads. (English for me)

![Screenshot_7.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644307983119/I7eHB6ENe.png)

A new page load to add database configurations:

![Screenshot_8.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644308866521/JGwJUwOBs.png)

Replace `database_name_here` with the database name created.

Replace `password_here` with an empty space, since we don't have a password to the database.

Replace `username_here` with `root`

Refer to the code snippet below:

%[https://gist.github.com/achingachris/fba7790934cd7a2248b42682a852d1f7]

Alternatively you can add Database configurations to the `wp-config-sample.php` file. Locate where the database configurations are and edit as instructed below:

```php
// ** Database settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', 'database_name_here' );

/** Database username */
define( 'DB_USER', 'username_here' );

/** Database password */
define( 'DB_PASSWORD', 'password_here' );

/** Database hostname */
define( 'DB_HOST', 'localhost' );

/** Database charset to use in creating database tables. */
define( 'DB_CHARSET', 'utf8' );

/** The database collate type. Don't change this if in doubt. */
define( 'DB_COLLATE', '' );
```

Replace `database_name_here` with the database name created.

Replace `password_here` with an empty space, since we don't have a password to the database.

Replace `username_here` with `root`

Once that is done, click on submit. If the configurations are successful, an installation page loads:

![Screenshot_11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644309046796/7wqiZbDiN.png)

Enter your site details as shown on the page (image shown)

![Screenshot_12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644309463752/RO3pNolYp.png)

Once you have entered the site details and your credentials, you'll be redirected to a login page, after that, your site is ready for editing!


![Screenshot_13.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644309598700/P73v7JuRd.png)

### Parting Shot!

I have never used WordPress locally, up until recently, and I had to document it. What do you think about WordPress, does it cater for your needs when creating solutions?