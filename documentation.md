# Accomplish | Django Documentation

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

- Click on the `url` to open your page [http://localhost:8000/](http://localhost:8000/)

- Create a new folder `templates` for `html` files in `todo` folder

```bash
cd todo
mkdir templates
```

- Create a `base.html` file with the code

```bash
cd templates
touch base.html
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Accomplish</title>
  </head>

  <body>
    <div class="container">{% block content %} {% endblock %}</div>
  </body>
</html>
```

- Create a `todo.html` file with the code

```bash
touch todo.html
```

```html
{% extends 'base.html' %} {% block content %}
<div class="content">
  <div class="title">Accomplish</div>
  <form>
    {% csrf_token %} {{form.as_p}}
    <button type="submit" class="btn">Submit</button>
  </form>
  <div class="list">
    {% for todo in todos %}
    <p>{{todo.title}}</p>
    {% empty %}
    <p>No todos</p>
    {% endfor %}
  </div>
</div>
{% endblock %}
```
