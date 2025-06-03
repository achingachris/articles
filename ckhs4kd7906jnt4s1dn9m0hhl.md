---
title: "The GitHub CLI (gh repo clone)"
datePublished: Sun Nov 01 2020 20:06:03 GMT+0000 (Coordinated Universal Time)
cuid: ckhs4kd7906jnt4s1dn9m0hhl
slug: the-github-cli-gh-repo-clone
canonical: https://medium.com/devcnairobi/the-github-cli-gh-repo-clone-c0595e5672de
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1605989260858/_URl3DV_h.png
tags: github

---

<span class="s"></span>

# The GitHub CLI (gh repo clone)


<noscript><img alt="Image for post" class="t u v gv aj" src="https://miro.medium.com/max/1436/1*_t6Uv_WHkdAqBj7GO0a8_g.png" width="718" height="436" srcSet="https://miro.medium.com/max/552/1*_t6Uv_WHkdAqBj7GO0a8_g.png 276w, https://miro.medium.com/max/1104/1*_t6Uv_WHkdAqBj7GO0a8_g.png 552w, https://miro.medium.com/max/1280/1*_t6Uv_WHkdAqBj7GO0a8_g.png 640w, https://miro.medium.com/max/1400/1*_t6Uv_WHkdAqBj7GO0a8_g.png 700w" sizes="700px"/></noscript>

[GitHub CLI](https://cli.github.com/) beta version was released a while ago, and it comes with really cool features. I have been using and interacting with GitHub without necessarily visiting the website, that’s fun right.

An alternative to using GitHub CLI is [HUB](https://hub.github.com/), which was there before GitHub cli was introduced.

GitHub CLI is an open-source project, here on [GitHub](https://github.com/cli/cli/).

I had an article before on [using GitHub CLI and its commands](https://dev.to/chrisachinga/using-github-s-cli-on-ubuntu-commands-3a89), so this is kind of like an update because the cli is up on version 1.x.x right now, better to stay on the know/updated. To get the latest releases of the cli [https://github.com/cli/cli/releases](https://github.com/cli/cli/releases)

![Image for post](https://miro.medium.com/max/60/1*pn3P9h9Yv3dNcO5ZkgXBSg.png?q=20)

<noscript><img alt="Image for post" class="t u v gv aj" src="https://miro.medium.com/max/2732/1*pn3P9h9Yv3dNcO5ZkgXBSg.png" width="1366" height="768" srcSet="https://miro.medium.com/max/552/1*pn3P9h9Yv3dNcO5ZkgXBSg.png 276w, https://miro.medium.com/max/1104/1*pn3P9h9Yv3dNcO5ZkgXBSg.png 552w, https://miro.medium.com/max/1280/1*pn3P9h9Yv3dNcO5ZkgXBSg.png 640w, https://miro.medium.com/max/1400/1*pn3P9h9Yv3dNcO5ZkgXBSg.png 700w" sizes="700px"/></noscript>

Everything you need to know about the cli is on their site, [https://cli.github.com/](https://cli.github.com/)

# Installation

[GitHub CLI](https://cli.github.com/) has to be installed on your device for you to use it.

View installation procedures based on your operating system:

[Installing GitHub CLI](https://github.com/cli/cli#installation)

# Usage

With the cli, you can create repositories, pull requests, issues, clone repos, and much more.

If I were to write on every usage gh cli has to offer, this would have been one of the longest and probably most boring technical articles, so I’ll break them down and make a mini-article-series if that makes sense.

# `gh repo clone`

This is one of the commands GitHub cli comes with. The gh clone works in a similar way as the popular git command, git clone.

Note that git and GitHub cli are two different things, but the gh clone and git clone perform a similar function altogether and have a similar syntax.

to use the command, browse into your favorite GitHub project, and clone it using GitHub cli, easy and fun.

For me, I’ll go to one of my repos, [https://github.com/ChrisAchinga/javascript.](https://github.com/ChrisAchinga/javascript.) Click on the green button code, a dropdown appears, click on the Github CLI tab and copy the command; `gh repo clone ChrisAchinga/javascript`

![Image for post](https://miro.medium.com/max/60/1*U0WvFiMOwWgYcTzAegxiFA.png?q=20)

<noscript><img alt="Image for post" class="t u v gv aj" src="https://miro.medium.com/max/2732/1*U0WvFiMOwWgYcTzAegxiFA.png" width="1366" height="768" srcSet="https://miro.medium.com/max/552/1*U0WvFiMOwWgYcTzAegxiFA.png 276w, https://miro.medium.com/max/1104/1*U0WvFiMOwWgYcTzAegxiFA.png 552w, https://miro.medium.com/max/1280/1*U0WvFiMOwWgYcTzAegxiFA.png 640w, https://miro.medium.com/max/1400/1*U0WvFiMOwWgYcTzAegxiFA.png 700w" sizes="700px"/></noscript>

Simple as that and you are done.

A simple start to becoming a GitHub cli master!