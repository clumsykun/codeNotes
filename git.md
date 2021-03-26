# Git guide

Git is software for tracking changes in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development.
Its goals include speed, data integrity, and support for distributed, non-linear workflows (thousands of parallel branches running on different systems).

## Installing Git on CentOS

Use `yum`, CentOS’s native package manager, to search for and install the latest git package available in CentOS’s repositories, enter the command:

```bash
sudo yum install git
```

If the command completes without error, you will have git downloaded and installed. To double-check that it is working correctly, enter the command to check version:

```bash
git --version
```

### Setting Global Git Username and Password

The global git username and password are associated with commits on all repositories on your system that don’t have repository-specific values.
To set your global commit name and email address, enter the command:

```bash
git config --global user.name "your_name"
git config --global user.email "your_email@yourdomain.com"
```

This command saves the values in the global configuration file `~/.gitconfig`.
You can also access it by enter the command:

```bash
git config --list
```

### Generating Your SSH Public Key

Many Git servers authenticate using SSH public keys.
In order to provide a public key, each user in your system must generate one if they don’t already have one.

First, you should check to make sure you don’t already have a key.
By default, a user’s SSH keys are stored in that user’s `~/.ssh` directory. You can easily check to see if you have a key already by going to that directory and listing the contents.

```bash
cd ~/.ssh
ls
```

You’re looking for a pair of files named something like `id_dsa` or `id_rsa` and a matching file with a `.pub` extension.
The `.pub` file is your public key, and the other file is the corresponding private key.

If you don’t have these files (or you don’t even have a `~/.ssh` directory), you can create them by enter the command

```bash
ssh-keygen -o
```
