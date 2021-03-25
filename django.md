# Django web framework

Django is a Python-based free and open-source web framework that follows the **model-template-views (MTV)** architectural pattern.
It is maintained by the **Django Software Foundation (DSF)**, an American independent organization.

## Quick guide

### Installing django

Being a Python web framework, Django requires Python.
Python includes a lightweight database called SQLite so you won’t need to set up a database just yet.

Install an official release by using pip, django 2.2.8 for example, enter the command:

```bash
pip install django=2.2.8
```

After installation, enter the command below to check the version.

```bash
python -m django --version
```

Package **django-extensions** is a collection of custom extensions for the Django framework.
These include *management commands*, *additional database fields*, *admin extensions* and much more.
Install Django Extensions by using pip, enter the command:

```bash
pip install django-extensions
```

### Creating a project

If this is your first time using Django, you’ll have to take care of some initial setup.
Namely, you’ll need to auto-generate some code that establishes a Django project – a collection of settings for an instance of Django, including database configuration, Django-specific options and application-specific settings.

From the command line, `cd` into a directory where you’d like to store your code, enter the command:

```code
 django-admin startproject example_proj
```

This command will create a example_proj directory in your current directory, which looks like:

```
example_proj/
    manage.py
    example_proj/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

- `example_proj/`: This outer root directory is a container for your project.The name doesn’t matter to Django, you can rename it to anything you like.

- `example_proj/manage.py`: A command-line utility that lets you interact with this Django project in various ways.

- `example_proj/example_proj/`: This inner directory is the actual Python package for your project. Its name is the Python package name you’ll need to use to import anything inside it (e.g. example_proj.urls).

- `example_proj/example_proj/__init__.py`: An empty file that tells Python that this directory should be considered a Python package.

- `example_proj/example_proj/settings.py`: Settings/configuration for this Django project. 

- `example_proj/example_proj/urls.py`: The URL declarations for this Django project; a “table of contents” of your Django-powered site.

- `example_proj/example_proj/wsgi.py`: An entry-point for WSGI-compatible web servers to serve your project.

## Usage of django-extensions

### Command RunScript

The command `runscript` lets you run an arbitrary set of python commands within the Django context. It offers the same usability and functionality as running a set of commands in shell accessed by:

```bash
python manage.py shell
```

To get started, create a directory `scripts` in your project root.
The `__init__.py` file in this directory is necessary so that the folder is picked up as a python package.

```bash
mkdir scripts
touch scripts/__init__.py
```

- All python scripts must stored in directory `scripts`, which may in your project root `/scripts/`, or app root  `/app_name/scripts/`.
- All python scripts must implement a `run()` function. This is what gets called when you run the script. You can import any models or other parts of your django project to use in these scripts.

Use the command `runscript` with the name of the script that you want to run.
For example, if you want to run script `example_script.py`, enter the command:

```bash
python manage.py runscript example_script
```


