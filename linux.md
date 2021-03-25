# Linux operating systems
Linux is a family of open-source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by **Linus Torvalds**.
Linux is typically packaged in a Linux distribution.

**Red Hat Enterprise Linux** (often abbreviated to **RHEL**) is a Linux distribution developed by Red Hat for the commercial market.
Red Hat Enterprise Linux is released in server versions for x86-64, Power ISA, ARM64, and IBM Z and a desktop version for x86-64.
All of Red Hat's official support and training, together with the Red Hat Certification Program, focuses on the Red Hat Enterprise Linux platform.

**CentOS** is a Linux distribution that provides a free, community-supported computing platform functionally compatible with its upstream source, Red Hat Enterprise Linux.
In January 2014, CentOS announced the official joining with Red Hat while staying independent from RHEL, under a new CentOS governing board.

## Linux frequently used knowledge

### File management

Command `touch`: create a file without any content.

```bash
touch file1_name file2_name file3_name 
```

This command can be used to create a single file at a time: `touch file_name`.
It also can be used to create the multiple numbers of files at the same time:

### User management

Command `useradd`: create a new user or update default new user information.

```bash
useradd [options] LOGIN
useradd -D
useradd -D [options]
```

Only *root* or users with *sudo privileges* can use the useradd command to create new user accounts.
When invoked without the `-D` option, the useradd command creates a new user account using the values specified on the command line plus the default values from the system file, which is `/etc/default/useradd`.

Command `passwd`: change user's password.

```bash
passwd [options] [LOGIN]
```

The passwd command changes passwords for user accounts. A normal user may only change the password for their own account, while the superuser may change the password for any account.

### Privilege management

The easiest way to **grant sudo privileges** to a user on CentOS is to add the user to the “wheel” group.
Members of this group are able to run all commands via `sudo` and prompted to authenticate themselves with their password when using `sudo`.

```bash
usermod -aG wheel LOGIN
```

### Shell Builtin Commands

Command `source`: Read and execute commands from filename in the current shell environment and return the exit status of the last command executed from filename.

```bash
source filename [arguments]
```

If filename does not contain a slash, file names in PATH are used to find the directory containing filename.
The file searched for in PATH need not be executable.
