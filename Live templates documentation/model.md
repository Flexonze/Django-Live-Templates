# model

### Description
Create basic Django model

### Template text
```python
from django.db import models
from django_extensions.db.models import TimeStampedModel

from core.models import UUIDModel


class $MODEL_NAME$(UUIDModel, TimeStampedModel):
    $END$

    def __str__(self):
        return self.pk

```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| MODEL_NAME | capitalize(camelCase(fileNameWithoutExtension())) |  | - [ ] |

### Applicable contexts
- Python: top-level

### Example result
```python
from django.db import models
from django_extensions.db.models import TimeStampedModel

from core.models import UUIDModel


class Project(UUIDModel, TimeStampedModel):
    
    
    def __str__(self):
        return self.pk

```

### Additional notes
 - This template assumes that `core.models.UUIDModel` (which inherits from `django.db.models.Model`) exists in your project.