# Intro to Git/GitHub

## About

This manual is for everyone to follow along to practice Git/GitHub. It is strongly recommanded to do after finishing the presentation or practicing in the workshop.

There are more than one way of using Git/GitHub: CLI, GUI, and IDE Integration. CLI is the default way of doing thing, but using something with GUI may be the most easy way for most people. However, it still requires some interactions with CLI tool beforehand to make most GUI tools up and running.

Please follow this manual step by step if it is your first time using git. Options will be listed under CLI/GUI/IDE Integration sub titles in each section if applicable.

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

Git is developed as a CLI (Command Line Interface) tool, meaning you interact with it in terminal. To install it as its original form, head to [Git official website](https://git-scm.com/downloads) and download the version for your operating system. **This is required for using GUI and IDE Integration as well**.

After installation, open your terminal and type `git --version`. You should see the version of your installation printed out.

### GUI

If you are not comfortable with CLI, [GitHub Desktop](https://desktop.github.com/) is a good alternative. **However git CLI is still required before you can use GitHub Desktop**.

After installing git, simply download and install GitHub Desktop, then you can run it like any GUI application.

It also prompts you for configuration during the installation. You can skip the **Config Git** section if you do it here.

### IDE Integration

IDEs, such as VSCode or JetBrain Pycharm, usually come with git integration as the form of version control or source control. However it also **requires Git CLI been installed in your machine**. Please refer to the **CLI** section to install it.

For VSCode, there are two amazing extensions to improve your git workflow: [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) and [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

## Config Git

At a minimum, Git requires **username** and **email** to identify unique authors, which is the first step we need to do.

In your terminal, type:

-   `git config --global user.name "FIRST_NAME LAST_NAME"` to set your username. This name is used as your author name for every commit.
-   `git config --global user.email "MY_NAME@example.com"` to set your email.

You can use `git config --global -l` to verify if configuration is done correctly.

### GUI

GitHub Desktop picks up local git config by default, so you can refer to **CLI** section to config.

Or, in GitHub Desktop, open **File - Options... - Git** and fill in your name and email, then hit **Save**.

## Connect to GitHub (Authentication)

Git does not know the existence of GitHub, GitHub is just another remote machine to your local git. However, your computer must be authenticated to connect to GitHub.

The easist way to do so it by setting up SSH keys with GitHub:

1. In terminal, type `ssh-keygen -t rsa -b 4096 -o -a 100` and press `enter`. You can just press **enter** for the following promts. This step generates a [SSH key pair](https://www.ssh.com/academy/ssh/public-key-authentication) on your computer, which contains one private key and one public key.

2. Find the public key generated and get its content. Usually you can get it by getting the file location from the first step (file path ends with `/.ssh/id_rsa`), and the same path but with `/.ssh/id_rsa.pub` is your public key. You can get the content of the public key by `cd` to its path then `cat id_rsa.pub`, or just open it with a text editor.

3. open [GitHub.com](https://github.com), click your avatar at top right corner, and select **Settings** from the drop down menu.

4. Find **SSH and GPG keys** under **Access** section. Click `New SSH key` at the rop right corner.

5. Give this key a title such as "blend360-laptop". It is possible (and likely) to have multiple keys stored on Github, so it is important to have a descriptive titile to let you know which machine is authencated by this key.

6. Copy and paste the content of your public key into the `Key` box below.

7. Click `Add SSH key` button and you are good to go.

## Clone the Repo

### CLI

1. Go to [this repo's GitHub page](https://github.com/vinceyyyyyy/intro-to-git-github), click the green `Code` button. The dropdown menu displays `SSH` connection string by default, witch is a text string starting with `git@github.com:`.

2. In your terminal of choice, type `git clone ` followed by that SSH string. `git clone git@github.com:vinceyyyyyy/intro-to-git-github.git` in this case.
   3
3. Press `enter` and it will clone the git repo to your working directory.

### GUI

1. At the top left corner where is usually displays `Current Repository`, click it to open the dropdown menu.

2. Click `Add - Clone Repository...`

3. Switch to `URL` tab and paste in the url of this demo repo, click `Clone` button at the bottom.

## Pull and Branching

### CLI

When you clone the repo, you have the latest content from remote. You can do `git pull` to refresh it again and will likely not run into any trouble.

However, the the files you see in you `File Explore` right now may not be all the content of this repo, because there are files only exists in other branches. For example, type `git checkout another-branch` to switch from `develop` branch to `another-branch` branch, and you will see a `hidden-file` in the root directory.

To create a new branch for you to work on, type `git checkout -b YOUR_BRANCH_NAME`. This command creates a new branch named YOUR_BRANCH_NAME based on your current branch, and switch to that new branch.

### GUI

When you clone the repository in GitHub Desktop, you have pulled that repo to you local machine already. Click `Fetch origin` at the top of the window to refresh what on the remote machine.

Using the dropdown menu from `Current Branch` button, you can see all the branches in this repo, switch to another branch, or create your new branch. Create your own branch and switch to that branch.

## Modify content and commit

Once you are on your own branch, open `README.md` file in the root directory. Add your name and how you feel today to the bottom of the content, as the format of `| YOUR_NAME | YOUR_FEELINGS |`. This is the markdown syntax for table.

For example, `| Vincent Yan | Feeling good today |`

After saving the file, we can start letting Git knows that we are adding changes to the version history, by adding a `commit`.

### CLI

Type `git add README.md` to add the modified file to staging area. This is a temporary area for you to organize this commit.

Then use `git commit -m "YOUR_MESSAGE"` to commit the change with your commit message.

### GUI

Once some changed in the repo, the left side bar displays that change under Changes. This is essentially a visualized staging area, which includes all changes automaticlly.

Type your commit message at the bottom of the side bar, then hit the `commit to` button beneath.

## Push

Your branch only exsits on your local machine at this point, it is not visible for others using Github, and is not backed up on the cloud. Therefore, we need to push (publish) your branch to the remote.

### CLI

Type `git push --set-upstream origin YOUR_BRANCH_NAME_ON_CLOUD` to publish your branch and push the content to remote. You need to assign the name again here, because your branch can have different name for remote and local.

### GUI

Use the `Publish Branch` button to publish it.

## Pull Request (Merge branches on GitHub)

Now, you have a new personal branch with your name and feeling in `README.md` file. However, it does not exist on other branches yet, and people probably will not look at your personal branch. Therefore, we want to merge the changes you made into the `develop` branch as one part of our code base.

Unfortunately, Pull Requst is a GitHub feature, meaning the native Git CLI does not have that. Open the [GitHub Repo](https://github.com/vinceyyyyyy/intro-to-git-github), you will most likely see a message telling you your new branch just get pushed and if you want to `Compare & pull request`.

Click the button, the next page will shows the difference between your branch and the branch you want to merge into at the bottom of the page. You can, and should leave your message here as well to let others know why you did this pull requst. Once all done, create the pull request by clicking that green button.

The repo admin will review your pull request along with what you have changed, and approve it if he/she feels safe to do so. You will get a notification once your PR is passed, or if the admin wants you to modify anything in your PR.

If your PR gets approved, you can finish it by click one more button, and then your name and feeling will appear in the develop branch.

### GUI

You can do pretty much anything from GitHub Desktop, just click the `Create Pull Request` button after pulishing your branch.
