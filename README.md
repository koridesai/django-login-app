# django-login-app
Basic Django app with login functionality
Create a django login app using postgresql
let's go over creating a basic django login app with postgresql.
Firstly you need to install python, you can install it from the official python site. 
The link i used to download python

**https://www.python.org/ftp/python/3.12.0/python-3.12.0-macos11.pkg**

Then we need to install some basic packages such as pip, django, postgresql. you can use the following codes to install the respective packages

To install pip & to check the current pip version installed

**python3 -m pip install --user --upgrade pip
python3 -m pip --version**

different projects have different versions of softwares required. so to avoid conflicts between software versions, it is best recommended for us to use virtual environments
Virtual environments can be created using the following code

**python3 -m venv env**

#here "env" is the name of the virtual environment
To activate the virtual environment, you can use

**source env/bin/activate**

#env is the environment name
#use the following command to check the version of python in the current virtual environment
You can deactivate the virual environment anytime using the following command

**deactivate**

Use the following command to install django

**pip3 install django**

#This installs the latest version of django, you can even install a specific version of django by using 
#example: pip3 install django==3.2.5
use the following command to check the version of django installed

**django-admin version**

To create a new project, we can start by using 

**django-admin startproject login_project**

#This creates a login_project folder with basic pre-installed dependencies for django

**cd login_project
brew install postgresql@15
brew services start postgresql@15**

#you can use any version you want

**pip3 install psycopg2
pip3 install psycopg2-binary**

**brew services list
createuser -s admin
createdb logindb**

#Create a Super user

(env) (base) saikoride@Sais-MacBook-Pro login_project % python3 manage.py createsuperuser
Username (leave blank to use 'username'): **admin**
Email address: 
Password: 
Password (again): 
This password is too short. It must contain at least 8 characters.
This password is entirely numeric.
Bypass password validation and create user anyway? [y/N]: **y**
Superuser created successfully.

Change the DATABASES code in settings.py file, to change the default database in django from sqllite to postgresql

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'logindb',
        'USER': 'admin',  # Replace with the correct PostgreSQL user
        'PASSWORD': '12345',
        'HOST': 'localhost',  # You can change this if your PostgreSQL server is on a different host
        'PORT': '',  # You can specify a port if necessary
    }
}

Use the following code to execute the migration of the app to the postgres database
python3 manage.py migrate
Create a new folder named "templates" (used as default for the django to search the index)

Create folder templates, create a subfolder registration in the templates directory, in the registrations directory create login.html file (view the file from the repo)

The "home.html" page has to be the home page, this is made as the default home page by adding this in the urls.py path

create new files base.html and home.html in the templates directory
base.html

The base.html page has the basic header and footer elements which can be extended in all other pages directly, instead of repeating the code in all the pages.
home.html
(view the files from the repo)

This page is considered to be the home page, this is made as the default home page by adding this in the urls.py
Add this in the settings.py file, to redirect to this page on successful login

**LOGIN_REDIRECT_URL = "home"
LOGOUT_REDIRECT_URL = "home"**

To run the server, use the command

**python3 manage.py runserver**

Open the link and view the results
