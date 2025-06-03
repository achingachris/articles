---
title: "Syncing A forked Repo with the Parent Repo on GitHub"
datePublished: Fri Jan 01 2021 19:14:24 GMT+0000 (Coordinated Universal Time)
cuid: ckjenovaf004lh4s1128b810a
slug: syncing-a-forked-repo-with-the-parent-repo-on-github
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1609528441549/y5PNL9od2.png
tags: repository, github, opensource, git, christmashackathon

---


A short guide and a practical reference to [GitHub Documentation on syncing a repo.](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

> 
It's kind of an 'open-source' hacks

For the guide, I'll be using a  [repo](https://github.com/ChrisAchinga/FbDevcCommunityContent)  I forked from [FbDevcCommunityContent](https://github.com/fbdevelopercircles/FbDevcCommunityContent).

From the terminal, I will change my directory to where the project files are:


![terminal.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609526934002/J5GB-3Oaz.png)

The first step will be to fetch branches and their commits from the upstream, or the parent repository:

```shell
git fetch upstream
```


![terminal1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609527142520/U-XFSLp7m.png)

After that, ensure that you are at the default repository on your remote repo. In my case, the default branch is `master`, and so is the upstream.

To confirm your current branch you are on:

```shell
git status
```

![terminal2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609527421779/UqluZLgvi.png)

All set so go ahead and merge with the upstream's master branch:

```shell
git merge upstream/master
```

If you haven't made any changes or commits on your master branch, git will automatically merge the repos and it'll be up to date


![terminal3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609527664051/ThwaF-YqQ.png)

Once that is done, update your remote files to GitHub:

```shell
git add .
git commit -m 'synced repo with upstream'
git push
```


![push.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609527975330/6g9XRasXY.png)

Well, that's pretty much it.
Find the original documentation here:

[https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

https://linktr.ee/chrisdev