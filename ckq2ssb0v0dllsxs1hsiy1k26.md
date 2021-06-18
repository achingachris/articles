## C#(Dotnet) Setup in Ubuntu with VSCode

C# is a general-purpose, multi-paradigm programming language encompassing static typing, strong typing, lexically scoped, imperative, declarative, functional, generic, object-oriented, and component-oriented programming disciplines.

In this article, I will take you through installing and setting up C#(c-sharp) environment on a Ubuntu OS(Operating System).

Requirements:

-  [Ubuntu](https://ubuntu.com/)  OS (20.0 and above)
- Internet Connection (For Installation)
-  [Command Line Skills](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)  (for the obvious LOL)
-  [Visual Studio Code](https://code.visualstudio.com/) 

>Note that .NET is a C# library

## Installing .NET (Csharp)

Start your terminal on Ubuntu;

`ctr` + `shift` + `T`

![Terminal](https://cdn.hashnode.com/res/hashnode/image/upload/v1624046438527/NHPeFyFrP.png)

First we need to add the Microsoft package signing key to your list of trusted keys and add the package repository. Run the commands in the order as they appear;

```shell
wget https://packages.microsoft.com/config/ubuntu/21.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
```

```shell
sudo dpkg -i packages-microsoft-prod.deb
```

<hr />

Installing .NET SDK

```shell
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

Installing The Runtime

```shell
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

To test the installation, run the command `dotnet` on your terminal;

```shell
dotnet
```

![test.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1624046930043/zzhtV5SXU.png)

yaay! we are done with that.

%[https://docs.microsoft.com/en-us/dotnet/core/install/linux-ubuntu]

%[https://dotnet.microsoft.com/download]

## Visual Studio Code Setup

This is an easy procedure, as we only need to install an extension on VSCode.

The extension is: **C# for Visual Studio Code (powered by OmniSharp)**

%[https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp]

![extension screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1624047760180/DZnQEhotl.png)

How to Install VSCode Extensions:

%[https://youtu.be/SKcZ3cwX8lA]

Once you have the extension added, we can create the famous **Hello World** application in C#.

## Creating Hello World in C#

First you create a new Project folder, say `c-sharp`, and open the empty folder with Visual Studio Code.

Open the integrated terminal in VSCode or use the terminal (ensure you are in the project's folder path).

To start a C# program use the command below;

```shell
dotnet new console
```

`dotnet new` is creating a new dotnet project. `console` is to specify the application type, in this case our program will be running on our terminal (console).

Once you run the command, a couple of files and folders are created.

We are only interested in the `Program.cs` file for now:

```cs
using System;

namespace hello
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

You don't need to change anything for now.

Let's run the program using the command:

```shell
dotnet run
```

![hello.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1624050366155/8fe4Unc_f.png)

And that is how you get to use C# in Ubuntu. 

Demo Files:

%[https://github.com/ChrisAchinga/c-sharp]

>Don't mind my terminal name, my laptop is really slow LOL!

