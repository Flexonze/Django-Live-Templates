# manager

### Description
Create a Manager class

### Template text
```python
from django.db.models import Manager


class $MODEL_NAME$Manager(Manager):
    def get_queryset(self):
        queryset = super().get_queryset()
        return queryset$END$

```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| MODEL_NAME | capitalize(camelCase(groovyScript("return _1.replace('_manager.py', '')", fileName()))) |  | - [x] |

### Applicable contexts
- Python: top-level.

### Example result
```python
from django.db.models import Manager


class ProjectManager(Manager):
    def get_queryset(self):
        queryset = super().get_queryset()
        return queryset

```

### Additional notes
- Must be in its own file called ` model_name_manager.py` (where `model_name` is the name of your model in snake_case)
