# factory

### Description
Create a basic model factory

### Template text
```python
import factory

from $APP_NAME$.models import $MODEL_NAME$


class $MODEL_NAME$Factory(factory.django.DjangoModelFactory):
    $END$

    class Meta:
        model = $MODEL_NAME$

```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x] |
| MODEL_NAME | capitalize(camelCase(groovyScript("return _1.replace('_factory.py', '')", fileName()))) |  | - [x] |

### Applicable contexts
- Python: top-level.

### Example result
```python
import factory

from myapp.models import Project


class ProjectFactory(factory.django.DjangoModelFactory):
    title = factory.Faker("sentence", nb_words=2)

    class Meta:
        model = Project

```

### Additional notes
- Must be in its own file called `model_name_factory.py` (where `model_name` is the name of your model in snake_case)
- You must define the attributes yourself