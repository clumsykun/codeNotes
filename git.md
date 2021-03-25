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
