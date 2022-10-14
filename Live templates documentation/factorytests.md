# factorytests

### Description
Create basic tests for a DjangoModelFactory

### Template text
```python
from django.test import TestCase
from $APP_NAME$.models import $MODEL_NAME$
from $APP_NAME$.tests.factories import $MODEL_NAME$Factory


class Test$MODEL_NAME$Factory(TestCase):
    def test_can_create_$MODEL_NAME_SNAKE_CASE$_factory(self):
        initial_$MODEL_NAME_SNAKE_CASE$_count = $MODEL_NAME$.objects.count()

        factory = $MODEL_NAME$Factory()
        factory.full_clean()

        $MODEL_NAME_SNAKE_CASE$_count = $MODEL_NAME$.objects.count()

        self.assertEqual($MODEL_NAME_SNAKE_CASE$_count, initial_$MODEL_NAME_SNAKE_CASE$_count + 1)
$END$
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x] |
| MODEL_NAME_SNAKE_CASE | groovyScript("return _1.split('_')[1..-2].join('_');", fileName()) |  | - [x] |
| MODEL_NAME | capitalize(camelCase(MODEL_NAME_SNAKE_CASE))  |  | - [x] |

### Applicable contexts
- Python: top-level

### Example result
```python
from django.test import TestCase
from myapp.models import Project
from myapp.tests.factories import ProjectFactory


class TestProjectFactory(TestCase):
    def test_can_create_project_factory(self):
        initial_project_count = Project.objects.count()

        factory = ProjectFactory()
        factory.full_clean()

        project_count = Project.objects.count()

        self.assertEqual(project_count, initial_project_count + 1)
```

### Additional notes
- Must be in its own file called ` test_model_name_factory.py` (where `model_name` is the name of your model in snake_case)
