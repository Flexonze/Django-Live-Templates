# modeladmin

### Description
Create an empty ModelAdmin

### Template text
```python
from django.contrib import admin
from django.contrib.admin import ModelAdmin
from $APP_NAME$.models import $MODEL_NAME$


@admin.register($MODEL_NAME$)
class $MODEL_NAME$Admin(ModelAdmin):
    pass
$END$
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x] |
| MODEL_NAME | capitalize(camelCase(groovyScript("return _1.replace('_admin.py', '')", fileName()))) |  | - [x] |

### Applicable contexts
- Python: top-level.

### Example result
```python
from django.contrib import admin
from django.contrib.admin import ModelAdmin
from myapp.models import Project


@admin.register(Project)
class ProjectAdmin(ModelAdmin):
    pass

```

### Additional notes
- Must be in its own file called ` model_name_admin.py` (where `model_name` is the name of your model in snake_case)
