# Django web framework

Django is a Python-based free and open-source web framework that follows the **model-template-views (MTV)** architectural pattern.
It is maintained by the **Django Software Foundation (DSF)**, an American independent organization.

## Quick install guide

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
For example, if you want to run script `simple_scripts.py`, enter the command:

```bash
python manage.py runscript simple_scripts
```


