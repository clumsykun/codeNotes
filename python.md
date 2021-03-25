# Python programming language

Python is an *interpreted*, *high-level* and *general-purpose* programming language.
Python's design philosophy emphasizes code readability with its notable use of significant indentation.
Its *language constructs* and *object-oriented approach* aim to help programmers write clear, logical code for small and large-scale projects.

**Anaconda** is a distribution of the Python and R programming languages for *scientific computing* (data science, machine learning applications, large-scale data processing, predictive analytics, etc.), that aims to simplify package management and deployment.
The distribution includes data-science packages suitable for Windows, Linux, and macOS.

## Configure and customize Anaconda

We do not recommend adding Anaconda to the PATH manually.
During installation, you will be asked “Do you wish the installer to initialize Anaconda3 by running conda init?”
We recommend “yes”.
If you enter “no”, then conda will not modify your shell scripts at all.
In order to initialize after the installation process is done, enter the code:

```bash
source <path to conda>/bin/activate
conda init
```

## Configure and customize pip

**pip** is a *package-management system* written in Python used to install and manage software packages. It connects to an online repository of public and paid-for private packages, called the **Python Package Index**.

By default, when you `pip install`, it pulls from the *public pypi repository* http://pypi.python.org/simple/. 
You can change the default repository by specifying the custom file, `~/.pip/pip.conf` on Linux or `HOMEPATH/pip/pip.ini` on Windows:

```
[global]
timeout = 60
index = http://mirrors.aliyun.com/pypi/simple/
index-url = http://mirrors.aliyun.com/pypi/simple/
trusted-host=mirrors.aliyun.com
```

Keep in mind that `--index-url` is used by `pip install`, and `--index` is used by `pip search`.
You can also use other repository in China, here is the list:

```
http://mirrors.aliyun.com/pypi/simple/ 
https://pypi.mirrors.ustc.edu.cn/simple/ 
http://pypi.douban.com/simple/ 
https://pypi.tuna.tsinghua.edu.cn/simple/ 
http://pypi.mirrors.ustc.edu.cn/simple/
```


