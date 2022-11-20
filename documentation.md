# Accomplish Django Documentation

- Create a new folder `todo` and enter into it.

```bash
mkdir todo
cd todo
```

- Create a new virtual environment and activate it.

```bash
virtualenv venv
source venv/bin/activate
```

- Install django and create a new project.

```python
pip install django
django-admin startproject accomplish
```

- Create a new app `todo`.

```python
cd accomplish
python3 manage.py startapp todo
```

- Add `todo` to `INSTALLED_APPS` in `accomplish/settings.py`.

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'todo',
]
```

- Create a model in `todo/models.py` file by adding the following code.

```python
from django.db import models

class Todo(models.Model):
    title = models.CharField(max_length=255)
    description = models.TextField(blank=True, null=True)
    is_done = models.BooleanField(default=False)
    data_added = models.DateTimeField(auto_now_add=True)
```

- Run the command to make migrations of the model

```bash
python3 manage.py makemigrations
```

- Initialize the model by running the command

```bash
python3 manage.py migrate
```

- Run the server

```bash
python3 manage.py runserver 127.0.0.1:8000
```
