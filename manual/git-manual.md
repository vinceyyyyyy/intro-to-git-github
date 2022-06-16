# Intro to Git/GitHub

## About

This manual is for everyone to follow along to practice Git/GitHub. It is strongly recommanded to do after finishing the presentation or practicing in the workshop.

The manual will cover each step in three methods: CLI, GUI, and IDE Integration.

## Prerequisites

-   A GitHub account
-   A Terminal
    -   for windows, use [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-us&gl=US) (recommanded) or PowerShell (PowerShell is installed in every Windows 10 computer, you can find it by searching in your start menu)
    -   for macOS, use [iTerm2](https://iterm2.com/) (recommanded) or native Terminal (you can find it by searching in Spotlight)
    -   for Linux, use your terminal of choice.

## Find the demo repo

Demo repo is at [GitHub Repo](https://github.com/vinceyyyyyy/intro-to-git-github). The repo itself is a monorepo, meaning it contains multiple (in engineering sense) saperated things. For the purpose of this manual, please find the [Manual](https://github.com/vinceyyyyyy/intro-to-git-github/manual) folder in it.

Because content in other folders are possible to change at the same time while you following along this manual, It is also a good chance to think about why it is recommanded to use separated repos for multiple projects, and when do you want to use monorepo approach.

## Install Git on your local machine

### CLI

Git is developed as a CLI (Command Line Interface) tool, meaning you interact with it in terminal. To install it as its original form, head to [Git official website](https://git-scm.com/downloads) and download the version for your operating system. **This is required for using GUI and IDE Integration as well**.

After installation, open your terminal and type `git --version`. You should see the version of your installation printed out.

### GUI

If you are not comfortable with CLI, [GitHub Desktop](https://desktop.github.com/) is a good alternative. **However git CLI is still required before you can use GitHub Desktop**. Please refer to the **CLI** section to install it.

After installing git, simply download and install GitHub Desktop, then you can run it like any GUI application.

It also prompts you for configuration during the installation. You can skip the **Config Git** section if you do it here.

### IDE Integration

IDEs, such as VSCode or JetBrain Pycharm, usually come with git integration as the form of version control or source control. However it also **requires Git CLI been installed in your machine**. Please refer to the **CLI** section to install it.

For VSCode, there are two amazing extensions to improve your git workflow: [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) and [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

## Config Git

At a minimum, Git requires **username** and **email** to identify unique authors, which is the first step we need to do.

### CLI

In your terminal, type:

-   `git config --global user.name "FIRST_NAME LAST_NAME"` to set your username. This name is used as your author name for every commit.
-   `git config --global user.email "MY_NAME@example.com"` to set your email.

You can use `git config --global -l` to verify if configuration is done correctly.

### GUI

GitHub Desktop picks up local git config by default, so you can refer to **CLI** section to config.

Or, in GitHub Desktop, open **File - Options... - Git** and fill in your name and email, then hit **Save**.

### IDE Integration

Refer to **CLI** section to config.

## Connect to GitHub and pull

### CLI

Git does not know the existence of GitHub, GitHub is just another remote machine to your local git. However, your computer must be authenticated to connect to GitHub.

The easist way to do so it by setting up SSH keys with GitHub:

1. In terminal, type `ssh-keygen -t rsa -b 4096 -o -a 100` and press `enter`. You can just press **enter** for the following promts. This step generates a [SSH key pair](https://www.ssh.com/academy/ssh/public-key-authentication) on your computer, which contains one private key and one public key.

2. Find the public key generated and get its content. Usually you can get it by getting the file location from the first step (file path ends with `/.ssh/id_rsa`), and the same path but with `/.ssh/id_rsa.pub` is your public key. You can get the content of the public key by `cd` to its path then `cat id_rsa.pub`, or just open it with a text editor.

3. open [GitHub.com](https://github.com), click your avatar at top right corner, and select **Settings** from the drop down menu.

4. Find **SSH and GPG keys** under **Access** section. Click `New SSH key` at the rop right corner.

5. Give this key a title such as "blend360-laptop". It is possible (and likely) to have multiple keys stored on Github, so it is important to have a descriptive titile to let you know which machine is authencated by this key.

6. Copy and paste the content of your public key into the `Key` box below.

7. Click `Add SSH key` button and you are good to go.

### GUI

Refer to **CLI** section to config if needed.

### IDE Integration

Refer to **CLI** section to config.

## Branching

## Modify content and commit

## Merge locally

## Push and Pull Request (Merge on GitHub)
