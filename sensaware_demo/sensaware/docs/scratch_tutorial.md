# Design Journey of the Sensaware App

1. Start new virtualenv and install basic packages

```bash
git init sensaware_app
cd sensaware_app
virtualenv env
source env/bin/activate
pip install django djangorestframework
```

2. Start a new Django Project

Note that ours is going to be an app that is going to reside in a larger ecosystem of many other apps. So, the name of the overall project would be something different. In our case, we will name it as `sensaware_demo`. The app would reside inside this project for our use case.

```bash
django-admin startproject sensaware_demo
python manage.py startapp sensaware
```

3. Edit the `settings.py` for project specific settings

```python
...
PROJECT_PATH = os.path.abspath(os.path.dirname(__file__))
...
INSTALLED_APPS = [
...
    'sensaware',
    'rest_framework',
    'rest_framework.authtoken'
]
...
TEMPLATES = [
    {
...
    'DIRS': [os.path.join(PROJECT_PATH, "templates")],
}
]
...
#REST FRAMEWORK Configuration
REST_FRAMEWORK = {
   'DEFAULT_PREMISSION_CLASSES': [
        'rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly'
    ]
}
```

The `PROJECT_PATH` is my setting of convenience to address everything with respect to the folder which contains the `settings.py` file.

4. Also, we would like to make API documentation and other relevant notes for online publishing and would like to tackle them as we go rather than doing them totally before, or after the work is done. We will try to follow this regimen of project development - Think, Design Documentation, Code, Code Documentation, Usage Updates, Repeat. This way, I am trying to stick to the practice of documenting the project as it comes along to be able to keep track of design decisions while making room for improvements and also not underpining my enthusiasm to get hands dirty with code ASAP when I get an idea. So, it is basically a Document-Code-Document cycle over shortened spans. So, we will install `mkdocs` for this purpose using `pip install mkdocs`. A quick guide to getting started with it may be found [here](http://www.mkdocs.org/)

```bash
pip install mkdocs
cd sensaware
mkdocs new docs
```

So far, we have created a new project, a new app and its documentation setup. Let us do a quick commit to our project at this point.
