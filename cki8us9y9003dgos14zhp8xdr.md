## Git and GitHub SSH Configuration

## Installing git

[Install git from here](https://git-scm.com/downloads)
Choose a selection based on your operating system.
For Linux and Ubuntu OS, you may use this alternative:
Open your terminal and paste the command below:

```shell
sudo apt install git-all
```

## Configure git with your GitHub Account
Ensure you have a GitHub account. If not, create one here [Join GitHub](https://github.com/join).

First of all, we’ll configure your details to git.
“Assuming your GitHub username is DevAcc and the email used on GitHub is devacc@mail.com”
On your terminal, use the following commands:

```shell
$ git config --global user.name "devAcc"
$ git config --global user.email “devacc@mail.com”
```

To confirm the details use  ``` git config --list ```
With that set, you should be ready to start working efficiently with your local repository.

## Generating a git ssh key
This prevents git from requesting your username and password every time you push into GitHub. (it’s annoying)
So this is how we do it:

Open your terminal and use the commands below:
```shell
ssh-keygen -t rsa -b 4096 -C "devacc@mail.com"
```
This will prompt you to enter a location to save the key and also create a password like a key to access that.

## Connecting to Your GitHub Account

After this, you’ll need to copy the key to the clipboard.
Use the command below to view the ssh key in a human-readable format:

```shell
cat < ~/.ssh/id_rsa.pub
```

![key.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620758991329/Q3VOjCzPb.png)

Copy the key displayed to your clipboard.

Go to your GitHub profile and navigate to settings: https://github.com/settings/profile
On the left side, panel click on SSH and GPG keys, then click on the top green button “New SSH” and paste the key there.
Voila! You are good to go

[My Profile](https://chrisdev.netlify.app/)
