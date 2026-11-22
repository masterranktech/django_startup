# Django Notes

A complete guide to learning Django from beginner to advanced.

---

# Table of Contents

- 1. Virtual Environment
- 2. Django Project
- 3. Django Application
- 4. Running the Server
- 5. Database & Migrations
- 6. Django Admin
- 7. Django ORM (CRUD)

---

# 1. Virtual Environment

A virtual environment creates an isolated Python environment for each project.

## Create a Virtual Environment

```bash
python -m venv venv
```

Creates a virtual environment named **venv**.

## Activate the Virtual Environment (Windows)

```bash
venv\Scripts\activate
```

When activated, your terminal should look similar to:

```text
(venv) C:\Projects\MyProject>
```

> **Note**
>
> Always activate the virtual environment before installing packages or running the project.

---

# 2. Django Project

## Install Django

```bash
pip install django
```

Installs Django inside the active virtual environment.

You can verify the installation using:

```bash
django-admin --version
```

---

## Create a Django Project

```bash
django-admin startproject ProjectName
```

Example:

```bash
django-admin startproject config
```

Project structure:

```text
ProjectName/
│
├── manage.py
├── ProjectName/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   ├── wsgi.py
│   └── __init__.py
```

---

# 3. Django Application

## Create a New App

```bash
python manage.py startapp core
```

This command creates a new Django application.

### Register the App

Open **settings.py** and add the app inside **INSTALLED_APPS**.

```python
INSTALLED_APPS = [
    ...
    'core',
]
```

> **Important**
>
> If the app is not registered, Django will ignore its models, templates, and other components.

---

# 4. Running the Development Server

Run the project using:

```bash
python manage.py runserver
```

Default Address:

```text
http://127.0.0.1:8000/
```

Run on a custom port:

```bash
python manage.py runserver 8001
```

---

# 5. Database & Migrations

## Create Migration Files

```bash
python manage.py makemigrations
```

Creates migration files based on changes in your models.

---

## Apply Migrations

```bash
python manage.py migrate
```

Applies all pending migrations to the database.

> **Migration Flow**
>
> 1. Edit Models
> 2. Run `makemigrations`
> 3. Run `migrate`

---

# 6. Django Admin

## Create a Superuser

```bash
python manage.py createsuperuser
```

After creating the account, access the admin panel:

```text
http://127.0.0.1:8000/admin/
```

---

# 7. Django ORM (CRUD)

Django ORM allows you to communicate with the database using Python instead of SQL.

---

## Read All Objects

```python
ObjectName.objects.all()
```

Returns every record.

---

## Get a Single Object

```python
ObjectName.objects.get(id=1)
```

or

```python
ObjectName.objects.get(pk=1)
```

Both return a single object.

> **Tip**
>
> `pk` stands for **Primary Key**.

---

## Filter Objects

```python
ObjectName.objects.filter(is_enable=True)
```

Returns all objects matching the condition.

---

## Access Object Fields

```python
post = ObjectName.objects.get(id=1)

post.title
post.text
```

Access the object's fields.

---

## Update an Object

```python
post = ObjectName.objects.get(id=1)

post.title = "New Title"
post.save()
```

The `save()` method stores the updated values in the database.

---

## Create a New Object

```python
ObjectName.objects.create(
    title="Your Title",
    text="Your Text"
)
```

Creates and saves a new object.

---

## Delete an Object

```python
post = ObjectName.objects.get(id=1)
post.delete()
```

Deletes the object from the database.

---

# Summary

| Command | Description |
|---------|-------------|
| `python -m venv venv` | Create Virtual Environment |
| `venv\Scripts\activate` | Activate Virtual Environment |
| `pip install django` | Install Django |
| `django-admin startproject` | Create Project |
| `python manage.py startapp` | Create App |
| `python manage.py runserver` | Run Server |
| `python manage.py makemigrations` | Create Migration Files |
| `python manage.py migrate` | Apply Migrations |
| `python manage.py createsuperuser` | Create Admin User |
