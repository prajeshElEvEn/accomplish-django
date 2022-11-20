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

- Create a model in `todo/models.py` by adding the following code.

```python

```
