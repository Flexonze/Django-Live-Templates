# modeltests

### Description
Create basic tests for a Model

### Template text
```python
from django.test import TestCase
from $APP_NAME$.models import $MODEL_NAME$


class Test$MODEL_NAME$(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.$MODEL_NAME_SNAKE_CASE$ = $MODEL_NAME$(
            $ATTRIBUTES$
        )

    def test_can_create_a_$MODEL_NAME_SNAKE_CASE$(self):
        self.$MODEL_NAME_SNAKE_CASE$.full_clean()
        self.$MODEL_NAME_SNAKE_CASE$.save()

    def test_can_print_a_$MODEL_NAME_SNAKE_CASE$(self):
        expected_str = "$EXPECTED_STR$"
        self.assertEqual(str(self.$MODEL_NAME_SNAKE_CASE$), expected_str)
$END$
```

### Template variables
| Name | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x]         |
| MODEL_NAME | capitalize(camelCase(MODEL_NAME_SNAKE_CASE)) |  | - [x] |
| MODEL_NAME_SNAKE_CASE | groovyScript("return _1.replace('test_', '').replace('.py', '');", fileName()), |  | - [x] |
| ATTRIBUTES |  |  | - [ ] |
| EXPECTED_STR | "" |  | - [ ] |

### Applicable contexts
- Python: top-level.

### Example result
```python
from django.test import TestCase
from myapp.models import Project


class TestProject(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.project = Project(
            title="My title",
        )

    def test_can_create_a_project(self):
        self.project.full_clean()
        self.project.save()

    def test_can_print_a_project(self):
        expected_str = self.project.title
        self.assertEqual(str(self.project), expected_str)

```

### Additional notes
- Must be in its own file called `test_model_name.py` (where `model_name` is the name of your model in snake_case)
