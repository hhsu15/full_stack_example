# full_stack_example
- `$django-admin startproject full_stack`
- cd into the full_stack
- `$create-react-app react-query-builder', 'build')`
- run `npm start` just to test it works
- run `npm run build` to create the build folder (which contains all the compiled codes)
- go back to the django directory and go to `settings.py` under full_stack
- under TEMPLATES, DIRS, add this to the list:
```python
os.path.join(BASE_DIR, 'react-query-builder', 'build')
```
- and then add this to the bottom of the same file
```python
STATICFILES_DIRS = [
  os.path.join(BASE_DIR, 'react-query-builder', 'build', 'static')
```
- finally, go to the urls.py and add something like this:
```python
from django.contrib import admin
from django.urls import path, re_path
from django.views.generic import TemplateView
urlpatterns = [
    path('admin/', admin.site.urls),
    re_path('.*', TemplateView.as_view(template_name='index.html')),
]
```

