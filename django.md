# Django web framework

Django is a Python-based free and open-source web framework that follows the **model-template-views (MTV)** architectural pattern.
It is maintained by the **Django Software Foundation (DSF)**, an American independent organization.

## Quick guide

### Install django

Being a Python web framework, Django requires Python.
Python includes a lightweight database called SQLite so you won’t need to set up a database just yet.

Install an official release by using pip, django 2.2.8 for example, enter the command:

```bash
pip install django==2.2.8
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

### Use MSSQl Server as database backend

Django don't support MSSQl Server as database backend officially, so Microsoft ODBC Driver is essential.
This method runs like:

```
MSSQL Server -> MSSQL Server ODBC Driver -> django-pyodbc-azure -> django frontend 
```

**Notes**: This article explains how to install the Microsoft ODBC Driver for SQL Server on Linux.
For more information, visit Microsoft's documentation: https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-ver15#redhat17.

Install the Microsoft ODBC Driver on Red Hat Enterprise Server and Oracle Linux:

```bash
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Red Hat Enterprise Server 6
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo

#Red Hat Enterprise Server 7 and Oracle Linux 7
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo

#Red Hat Enterprise Server 8 and Oracle Linux 8
curl https://packages.microsoft.com/config/rhel/8/prod.repo > /etc/yum.repos.d/mssql-release.repo

exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install -y msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install -y mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install -y unixODBC-devel
```

`django-pyodbc-azure` is a modern fork of django-pyodbc, a Django Microsoft SQL Server external DB backend that uses ODBC by employing the pyodbc library. It supports Microsoft SQL Server and Azure SQL Database.
Install this package by enter the command:

```bash
pip install django-pyodbc-azure-2019
```

Open the file `settings.py` on your project directory, and configure the SQL Server database access:

```python
DATABASES = {
    'default': {
        'ENGINE': 'sql_server.pyodbc',
        'NAME': 'database_name',
        'USER': 'your_username',
        'PASSWORD': 'your_password',
        'HOST': 'database_host',
        'PORT': '1433',
        'OPTIONS': {
            'driver': 'ODBC Driver 17 for SQL Server',
            'MARS_Connection': True,
        },
    },
}
```

### Create a project

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

### Create a app

Each application you write in Django consists of a Python package that follows a certain convention.
Django comes with a utility that automatically generates the basic directory structure of an app, so you can focus on writing code rather than creating directories.

To create your app, make sure you’re in the same directory as `manage.py` and enter the command:

```bash
python manage.py startapp example_app
```

That’ll create a directory example_app, which is laid out like this:

```
example_app/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

make django know your data models has been changed

```
python manage.py makemigrations example_app
```

rebuild table structure

```
python manage.py migrate
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
For example, if you want to run script `example_script.py`, enter the command:

```bash
python manage.py runscript example_script
```

## HTTP technology

### HTTP response status codes

HTTP response status codes indicate whether a specific HTTP request has been successfully completed.
Responses are grouped in five classes:

- Informational responses (100–199)
- Successful responses (200–299)
- Redirects (300–399)
- Client errors (400–499)
- Server errors (500–599)

**Response 100: Continue.**
This interim response indicates that everything so far is OK and that the client should continue the request, or ignore the response if the request is already finished.

**Response 102: Processing (WebDAV).**
This code indicates that the server has received and is processing the request, but no response is available yet.

**Response 200: OK.**
The request has succeeded. The meaning of the success depends on the HTTP method:

- `GET`: The resource has been fetched and is transmitted in the message body.
- `PUT` or `POST`: The resource describing the result of the action is transmitted in the message body.
- `HEAD`: The entity headers are in the message body.
- `TRACE`: The message body contains the request message as received by the server.

**Response 201: Created.**
The request has succeeded and a new resource has been created as a result.
This is typically the response sent after `POST` requests, or some `PUT` requests.

**Response 400: Bad Request.**
The server could not understand the request due to invalid syntax.

**Response 401: Unauthorized**
Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated". That is, the client must authenticate itself to get the requested response.

**Response 403: Forbidden.**
The client does not have access rights to the content; that is, it is unauthorized, so the server is refusing to give the requested resource.
Unlike 401, the client's identity is known to the server.

**Response 404: Not Found.**
The server can not find the requested resource.
In the browser, this means the URL is not recognized.
In an API, this can also mean that the endpoint is valid but the resource itself does not exist.
Servers may also send this response instead of 403 to hide the existence of a resource from an unauthorized client.
This response code is probably the most famous one due to its frequent occurrence on the web.
