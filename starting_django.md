
##  [Table of contents](#table-of-contents)
  1. [Activate Django Environment](#activate-django-environment)
  2. [Creating Project Folder](#creating-project-folder)
  3. [Creating an App](#creating-an-app)
  4. [Migrate (to use sessions)](#migrate-to-use-sessions)

<br />

### Starting folder structure should looks similar to this
>```
>Python_Stack
>├── django
>│   └── django_intro     
>│
>└── my_environments
>     └── djangoPy3env
>```
>
<br />

## 1. Activate Django Environment
- windows
    ```properties
    call my_environments\djangoPy3env\Scripts\Activate
    ```
- Mac
    ```properties
    source my_environments\djangoPy3env\bin\activate
    ```
    <br>

## 2. Creating Project Folder
```properties
(djangoPy3Env) cd python_stack/django/django_intro
```
<br />

create project in working folder
```properties
(djangoPy3Env) django_intro > django-admin startproject your_project_name_here
```
<br />

navigate into the folder

```properties
(djangoPy3Env) django_intro > cd your_project_name_here
```
<br />

run your server
```properties
(djangoPy3Env) main_project > python manage.py runserver
```
<br />
navigate to ```localhost:8000``` to check the server is running

press ``` ctrl+c ``` to stop the server

<br />




## 3. Creating an App
<br />
<br />
open the project in VScode
<br />

```properties
main_project > code .
```

Create  the app
```properties
(djangoPy3Env) main_project > python manage.py startapp your_app_name_here
```
in settings.py find the variable ```INSTALLED_APPS```:

```python
INSTALLED_APPS = [
       'your_app_name_here', #Your app name here
       'django.contrib.admin',
       'django.contrib.auth',
       'django.contrib.contenttypes',
       'django.contrib.sessions',
       'django.contrib.messages',
       'django.contrib.staticfiles',
   ]
```
in project folder urls.py add the following:
```python
from django.urls import path, include

urlpatterns = [
    path('', include('your_app_name_here.urls')),
]
```

in app folder create ```urls.py``` and add:
```python
from django.urls import path     
from . import views
urlpatterns = [
    path('', views.index),	   
]
```
in views.py add the following:
```python
from django.shortcuts import render, HttpResponse

def index(request):
    return HttpResponse("this is the equivalent of @app.route('/')!")
```

run your server
```properties
(djangoPy3Env) main_project > python manage.py runserver
```
navigate to ```localhost:8000``` to check the server is running

## 4. Migrate (to use sessions)

```properties
(djangoPy3Env) project_name> python manage.py migrate
```
