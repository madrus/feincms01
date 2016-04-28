# How to Create a New FEINCMS Project

1. create solution directory
2. inside it create virtual environment: `virtualenv env`
3. activate it: `env\scripts\activate`
4. install django: `pip install django`
5. install feincms: `pip install feincms`
6. create django project 'src': `django-admin.py startproject src`
7. `cd src`
8. create application 'main': `python manage.py startapp main`
9. add stuff to `settings.py`
    1. applications to `INSTALLED_APPS`:
        ```python
        INSTALLED_APPS = [
            # feincms apps
            'feincms',
            'feincms.module.page',
            'feincms.module.medialibrary',
            'main',
            'mptt',
            ...
        ]
        ```
    2. `TEMPLATE_DIRS` and `TEMPLATE_CONTEXT_PROCESSORS`:
        ```python
        TEMPLATE_DIRS = [
            # List of template directories.
            # Example:
            os.path.join(BASE_DIR, 'templates'),
        ]

        TEMPLATE_CONTEXT_PROCESSORS = [
            'django.contrib.auth.context_processors.auth',
            'django.contrib.messages.context_processors.messages',
            'django.core.context_processors.i18n',
            'django.core.context_processors.media',
            'django.core.context_processors.request',
            'django.core.context_processors.static',
        ]
        ```
    3. `tinymce` from [tinymce website](https://www.tinymce.com/)
        - option 1:
            - download tinymce and copy tinymce and jquery to /static/feincms folder
            - add FEINCMS_RICHTEXT_INIT_CONTEXT at the end of the file:
                ```python
                FEINCMS_RICHTEXT_INIT_CONTEXT = {
                    'TINYMCE_JS_URL': STATIC_URL + 'feincms/tinymce.min.js',
                }
                ```
        - option 2:
            - maybe it is possible to use the CDN link (?)
                ```html
                <head>
                  <script src="//cdn.tinymce.com/4/tinymce.min.js"></script>
                </head>
                ```
10. add stuff to `models.py`
11. create superuser: `python manage.py createsuperuser`
12. download `sqlite3.exe` from [sqlite3 website](https://sqlite.org/download.html).
    Take the command-line tools bundle. Put the following files in the `Scripts`
    folders your Python installations (like `C:\Python27\Scripts`).
