---
title: Setup Dotnet, ASP.NET app with VS Code on Ubuntu / Linux
date: 2023-01-29 16:00
categories: [Linux, DotNet]
tags: [dotnet, linux, ubuntu]
render_with_liquid: false
---

This article will help you to setup Dotnet/.NET 7, ASP.NET 7 app with VS Code on Ubuntu / Linux
- ASP.NET 7 webapi source code can be found at: <https://github.com/abhishek-pradhan/dotnet7-webapi-hello-world> 

## Setup Dotnet / .NET 7

> Note: Microsoft offers 2 ways to install dotnet: Scripted and Manual. I will follow the Manual way, so as to have control over installation and since this approach lets you install different versions into separate locations and choose explicitly which one to use by which application
{: .prompt-info }

### Install Dotnet SDK

- Install Dotnet SDK binaries from <https://dotnet.microsoft.com/en-us/download/dotnet/7.0> &amp; Download Linux tar file

  - Check your architecture version by running:

    ```bash
    lscpu
    ```

    > If Architecture: x86_64, this means you are on x64
    {: .prompt-tip }

- dotnet-sdk-7.0.102-linux-x64.tar.gz file gets downloaded to default ~/Downloads dir.

- Now go to Downloads dir &amp; create a new dir called .dotnet (we are creating .dotnet dir, since if you directly unzip .tar.gz, it will unzip all its contents to Downloads dir, which we don't want) 

  ```bash
  cd ~/Downloads
  mkdir .dotnet
  chmod +x .dotnet
  tar zxvf dotnet-sdk-7.0.102-linux-x64.tar.gz -C .dotnet
  ```

- Set DOTNET_ROOT &amp; PATH variables in ~/.bashrc: (vim ~/.bashrc) 

   ```bash
  # dotnet 7 sdk
  export DOTNET_ROOT=/home/abhi/Downloads/.dotnet
  export PATH=${PATH}:${DOTNET_ROOT}:${DOTNET_ROOT}/tools
  ```
  {: file='.bashrc'}

    > Note: I am not sure why we need /tools dir in PATH, as it doesn't exist! However, this is what Microsoft recommends.

- Append these variables to .bashrc file, save and now reboot terminal &amp; run either of dotnet commands (dotnet --version or dotnet --info) to test setup:

  ```bash
  dotnet --version
  ```
  > successfull output: 
    ```terminal
    7.0.102
    ```

### Setup dotnet auto completion

- *Optional* Setup dotnet auto-completion: Add following to ~/.bashrc and reboot terminal:

  ```bash
    # dotnet auto-completion 
    # bash parameter completion for the dotnet CLI 
    function _dotnet_bash_complete() 
    { 
      local cur="${COMP_WORDS[COMP_CWORD]}" IFS=$'\n' 

      local candidates

      read -d '' -ra candidates < <(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)

      read -d '' -ra COMPREPLY < <(compgen -W "${candidates[*]:-}" -- "$cur")
    }

    complete -f -F _dotnet_bash_complete dotnet
  ```
  {: file='.bashrc'}

- Test auto-completion:

  ```terminal
  dotnet n (tab-out) -> dotnet new
  dotnet new l (tab-out) -> dotnet new list
  ```

## Create ASP.NET WebApi project

- Create dir and goto that dir:

  ```bash
  mkdir dotnet7-webapi-hello-world
  cd dotnet7-webapi-hello-world
  ```

  > Check what all project types we can create using dotnet cli:
  ```bash
  dotnet new list
  ```
  {: .prompt-tip }

- Create new dotnet webapi project using dotnet cli:

  ```bash
  dotnet new webapi
  ```

- At this point, we can use VS Code to open up code and run the project. For now lets continue using dotnet cli. Later in this article, we will install VS Code and open up this app.

  ```bash
  dotnet build
  ```

- Run the application:

  ```bash
  dotnet run
  ```

> Checking url / port number mentioned in the terminal, as output of above dotnet run cmd

- Now open up new terminal or check in browser <http://localhost:5166/WeatherForecast>:

  ```bash
  curl http://localhost:5166/WeatherForecast
  ```

> To stop the application, press Ctrl+C in the terminal


## Setup VS Code

- Download VS Code (free) from <https://code.visualstudio.com/>

- In your default ~/Downloads folder, you will see code_1.74.3-1673284829_amd64.deb

- Double click to open in Software Install and go ahead and install VS Code

- Open up VS code either from menu or from terminal by navigating to your above project dir:

  ```bash
  code . 
  ```

### Install C# extension

- Install C# extension from 'Extensions' panel (Ctrl+Shift+X) on left hand side

### Enable C# debugging

- Enable C# debugging by opening up any .cs file and then you will get a Notification from C# extension: Required assets to build and debug are missing from 'project-name'. Add them? OR

- Enable C# debugging 'Run and Debug' panel (Ctrl+Shift+X) on left hand side:
  ![enable vscode debugging 1](/assets/img/posts/2023-01-29-setup-dotnet-with-vscode/enable-vscode-debugging-1.png)

  - This will generate .vscode folder with 2 files, which allows C# extension to provide debugger in VS Code:
   ![enable vscode debugging 2](/assets/img/posts/2023-01-29-setup-dotnet-with-vscode/enable-vscode-debugging-2.png)

  - Open up a .cs file, add a Breakpoint and Start Debugging from Run menu or press F5:
   ![vscode debugging breakpoint](/assets/img/posts/2023-01-29-setup-dotnet-with-vscode/vscode-debugging-breakpoint.png)

   - To stop debugging press Shift+F5 or from debug options bar, click on red stop button.

> Note: dotnet/VS Code IDE versions may vary in future or you might be using a different distro of Linux, but this guide should still be valid.
{: .prompt-info }