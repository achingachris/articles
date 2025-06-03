---
title: "Using JavaScript in JupyterLab"
datePublished: Sat Aug 20 2022 17:04:44 GMT+0000 (Coordinated Universal Time)
cuid: cl725hthh03s0p0nv2rhagodp
slug: using-javascript-in-jupyterlab
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1661009097663/b51wR6_VP.png
tags: javascript, jupyter, 2articles1week

---

> **TL;DR**
> This post will take you through installing JupyterLabs and how to add a NodeJS kernel to it in Ubuntu.

## Installing JupyterLabs

For a better experience, you should install Jupyter Lab inside a virtual environment. 

```shell
sudo  apt install python3-venv
```

After the installation is complete, create a new environment:

```
python3 -m venv jlab
```

> *Note that you can replace the `jlab` with any name of your choice.*

Now activate the environment:

```
. jlab/bin/activate
```

![Activating a virtual environment](https://cdn.hashnode.com/res/hashnode/image/upload/v1661010372178/3i2YxqlrG.png align="center")

Now install Jupyter Lab in Ubuntu:

```
pip install jupyterlab
``` 

Once the installation is complete, you can start Jupyter lab by running:

```shell
jupyter lab
```

Jupyter Labs runs locally on port 8888: http://localhost:8888/

## Installing Javascript Kernel

Inside the activated virtual environment, install the javascript kernel by running:

```
npm install -g ijavascript
```

To activate the kernel, run:

```
ijsinstall
```

Re-start Jupyter lab:

```shell
jupyter lab
```

![Javascript in jupyter lab](https://cdn.hashnode.com/res/hashnode/image/upload/v1661014401573/qPeHpGSzM.png align="center")

To test it out, click on the `NodeJS` logo to start a Javascript lab:

![Srunning javascript on jupyter lab](https://cdn.hashnode.com/res/hashnode/image/upload/v1661014803723/WNqhjI01M.png align="center")

## Conclusion

The article demonstrates how to install Jupyter labs in a virtual environment and add a JavaScript kernel.

## Resources

%[https://www.youtube.com/watch?v=gkeh9phGgYo&list=PL1ROSNerT41L9l0-es4HFXyEyEmKwSya4&index=20&t=81s]
