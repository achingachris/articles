---
title: "Git and GitHub SSH Configuration"
seoTitle: "Git and GitHub SSH Configuration"
seoDescription: "Configure SSH to your GitHub using git for better experiences with GitHub and git"
datePublished: Tue May 11 2021 18:54:58 GMT+0000 (Coordinated Universal Time)
cuid: cki8us9y9003dgos14zhp8xdr
slug: git-and-github-ssh-configuration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1620759009258/7NZXO3nHW.png
tags: github, git, ssh, 2articles1week

---

## Installing git

[Install git from here](https://git-scm.com/downloads) Choose a selection based on your operating system. For Linux and Ubuntu OS, you may use this alternative: Open your terminal and paste the command below:

```bash
sudo apt-get install git
```

Ensure you have a GitHub account. If not, create one here [Join GitHub](https://github.com/join).

First of all, we’ll configure your details to git. “Assuming your GitHub username is DevAcc, and the email used on GitHub is devacc@mail.com” On your terminal, use the following commands:

```bash
$ git config --global user.name "devAcc"
$ git config --global user.email “devacc@mail.com”
```

To confirm the details, use `git config --list` With that set, you should be ready to start working efficiently with your local repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671370441892/zue5ZtE_6.png align="center")

## Generating a git ssh key

This prevents git from requesting your username and password every time you push into GitHub. *(it’s annoying)* So this is how we do it:

Open your terminal and use the commands below:

```bash
ssh-keygen -t rsa -b 4096 -C "devacc@mail.com"
```

This will prompt you to enter a location to save the key and create a password to access that.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671370609773/O-Os-J24u.png align="center")

## Connecting to Your GitHub Account

After this, you’ll need to copy the key to the clipboard. Use the command below to view the ssh key in a human-readable format:

```bash
cat < ~/.ssh/id_rsa.pub
```

![key.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620758991329/Q3VOjCzPb.png align="left")

**Note:**

If you are using Windows PowerShell, use the command:

```bash
Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
```

Copy the key displayed to your clipboard:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671370695216/gav79cUGz.png align="center")

Go to your GitHub profile and navigate to settings, or better still use the link [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new). On the left side, panel, click on SSH and GPG keys, then click on the top green button “New SSH” and paste the key there.

Voila! You are good to go