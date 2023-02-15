# filterset

### Description
Create a basic filterset (requires the django-filters package)

### Template text
```python
from django_filters.rest_framework import FilterSet

from $APP_NAME$.models import $MODEL_NAME$


class $MODEL_NAME$Filter(FilterSet):
    class Meta:
        model = $MODEL_NAME$
        fields = [
            "$END$",
        ]
```

### Template variables
| Name       | Expression | Default value | Skip if defined |
|------------|------------|---------------|----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x] |
| MODEL_NAME | capitalize(camelCase(groovyScript("return _1.replace('_filters.py', '')", fileName()))) |  | - [x] |

### Applicable contexts
- Python: top-level.

### Example result
```python
from django_filters.rest_framework import FilterSet

from myapp.models import Project


class ProjectFilter(FilterSet):
    class Meta:
        model = Project
        fields = [
            "",
        ]
```

### Additional notes
 - Requires the [django-filters](https://pypi.org/project/django-filter/) package
 - Must be in its own file called ` model_name_filters.py` (where `model_name` is the name of your model in snake_case)
