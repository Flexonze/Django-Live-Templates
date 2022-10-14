# admintests

### Description
Create basic tests for a ModelAdmin

### Template text
```python
from django.contrib import admin
from django.contrib.admin import ModelAdmin
from django.test import TestCase
from django.urls import reverse
from accounts.tests.factories import UserFactory
from $APP_NAME$.models import $MODEL_NAME$
from $APP_NAME$.tests.factories import $MODEL_NAME$Factory
from $APP_NAME$.admin import $MODEL_NAME$Admin


class Test$MODEL_NAME$Admin(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.user = UserFactory(super_user=True)
        cls.$MODEL_NAME_SNAKE_CASE$s = $MODEL_NAME$Factory.create_batch($NUMBER_OF_OBJECTS$)

    def setUp(self):
        self.client.force_login(self.user)

    def test_config(self):
        self.assertTrue(issubclass($MODEL_NAME$Admin, ModelAdmin))
        self.assertTrue(admin.site.is_registered($MODEL_NAME$))

    def test_changelist(self):
        url = reverse("admin:$APP_NAME$_$MODEL_NAME_LOWER_CASE$_changelist")

        with self.assertNumQueries($NUMBER_OF_QUERIES$):
            response = self.client.get(url)

        self.assertEqual(200, response.status_code)

    def test_add(self):
        url = reverse("admin:$APP_NAME$_$MODEL_NAME_LOWER_CASE$_add")

        with self.assertNumQueries($NUMBER_OF_QUERIES$):
            response = self.client.get(url)

        self.assertEqual(200, response.status_code)

    def test_change(self):
        url = reverse("admin:$APP_NAME$_$MODEL_NAME_LOWER_CASE$_change", kwargs={"object_id": self.$MODEL_NAME_SNAKE_CASE$s[0].id})

        with self.assertNumQueries($NUMBER_OF_QUERIES$):
            response = self.client.get(url)

        self.assertEqual(200, response.status_code)
$END$
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath())|               | - [x]           |
| MODEL_NAME | capitalize(camelCase(MODEL_NAME_SNAKE_CASE)) |  | - [X] |
| MODEL_NAME_SNAKE_CASE | groovyScript("return _1.split('_')[1..-2].join('_');", fileName()), | | - [X] |
| NUMBER_OF_OBJECTS | 3 | 3 | - [ ] |
| MODEL_NAME_LOWER_CASE | groovyScript("return _1.replace('_', '')", MODEL_NAME_SNAKE_CASE) |               | - [X] |
| NUMBER_OF_QUERIES | 2 | 2 | - [ ] |

### Applicable contexts
- Python: top-level.

### Example result
```python
from django.contrib import admin
from django.contrib.admin import ModelAdmin
from django.test import TestCase
from django.urls import reverse
from accounts.tests.factories import UserFactory
from myapp.models import Project
from myapp.tests.factories import ProjectFactory
from myapp.admin import ProjectAdmin


class TestProjectAdmin(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.user = UserFactory(super_user=True)
        cls.projects = ProjectFactory.create_batch(2)

    def setUp(self):
        self.client.force_login(self.user)

    def test_config(self):
        self.assertTrue(issubclass(ProjectAdmin, ModelAdmin))
        self.assertTrue(admin.site.is_registered(Project))

    def test_changelist(self):
        url = reverse("admin:myapp_project_changelist")

        with self.assertNumQueries(5):
            response = self.client.get(url)

        self.assertEqual(200, response.status_code)

    def test_add(self):
        url = reverse("admin:myapp_project_add")

        with self.assertNumQueries(5):
            response = self.client.get(url)

        self.assertEqual(200, response.status_code)

    def test_change(self):
        url = reverse("admin:myapp_project_change", kwargs={"object_id": self.projects[0].id})

        with self.assertNumQueries(5):
            response = self.client.get(url)

        self.assertEqual(200, response.status_code)

```

### Additional notes
- Must be in its own file called ` test_model_name_admin.py` (where `model_name` is the name of your model in snake_case)
