# GitLab Basics

## Install and configure Git

> Check if Git is already installed

```shell
git --version

# If Git is installed the output will be similar to:
git version 2.3.8

# If Git is not installed the output will be similar to:
-bash: git: command not found
```

> Add your Git username and set your email

```bash
git config --global user.name "Your Name"
git config --global user.email you@example.com
```

> Verify your configuration information

```bash
git config --global --list

# Result:
user.name=Your Name
user.email=you@example.com
```

To interact with GitLab projects you will need to install the Git command
line utility. This utility allows you to clone projects, push and pull code, and
stay in sync with the central repository.

### Command Line Interface

Use a command line interface (also called a terminal or shell) to run the commands
on the right. Depending on your operating system, find the application of your preference.
Here are some suggestions.

- [Terminal](http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line) on Mac OSX
- [GitBash](https://msysgit.github.io) on Windows
- [Linux Terminal](http://www.howtogeek.com/140679/beginner-geek-how-to-start-using-the-linux-terminal/) on Linux

<aside class="notice">It is important to configure Git with your username and
email address. Git and GitLab use this information to identify your changes.</aside>

## Add an SSH Key Pair

> Check if you already have an SSH key

```bash
cat ~/.ssh/id_rsa.pub

# If you already have a key it will look something like this
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAEAQDVvUplNVHBJLyezQ/hq4yzETyXiwkgHZbet9q8ftp+TcputKd7V1NCOuHGjfIPWF1 you@computer-name

# If you do not have a key you will see an error like this
cat: /Users/you/.ssh/id_rsa.pub: No such file or directory
```

> Generate a new SSH key pair if you received an error above

```bash
ssh-keygen -t rsa -b 4096 -C "you@computer-name"

# You will be prompted for the following information. Press enter to accept the defaults. Defaults appear in parentheses.
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/you/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/you/.ssh/id_rsa.
Your public key has been saved in /Users/you/.ssh/id_rsa.pub.
The key fingerprint is:
39:fc:ce:94:f4:09:13:95:64:9a:65:c1:de:05:4d:01 you@computer-name
```

SSH keys allow you to interact with GitLab using the Git command line
tool. Instead of using your username and password, the SSH key will securely
authenticate you. You will need to complete these steps on each computer
you want to use with GitLab.

### Generate an SSH key pair

Before you can add your public key to your GitLab account you need to check if
you have an SSH key pair. If not, you need to generate one.

<aside class="notice">It is a best practice to use a password for an SSH key, but it is not
required and you can skip creating a password by pressing enter. Note that
the password you choose here can't be altered or retrieved. </aside>

### Add your SSH Key to your GitLab account

> Copy the contents of your SSH public key.

```bash
cat ~/.ssh/id_rsa.pub
```

> Copy everything including the `ssh-rsa` and `you@computer-name` parts.

```bash
# Example public key as output by the previous command
ssh-rsa AAAAB3NzaC1yc2EAAAADAQEL17Ufacg8cDhlQMS5NhV8z3GHZdhCrZbl4gz you@example.com
```

First, copy the contents of your SSH public key. Then, from the GitLab Dashboard
click on "Profile Settings"

![Profile Settings](basicsimages/profile_settings_menu.png)

Click "SSH Keys":

![SSH Keys](basicsimages/ssh_keys_profile_menu.png)

Click on the "Add SSH Key" button

![Add SSH Key](basicsimages/add_ssh_key_button.png)

Paste your SSH public key in the "Key" text area. The title will be added automatically.
Click "Add key" to save your public key.

![Paste SSH Key](basicsimages/add_ssh_key.png)

Now, you'll be able to use Git over SSH.
