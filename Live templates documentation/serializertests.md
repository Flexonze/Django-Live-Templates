# serializertests

### Description
Create basic tests for a ModelSerializer

### Template text
```python
from django.test import TestCase

from $APP_NAME$.serializers.$SERIALIZER_NAME_SNAKE_CASE$ import $SERIALIZER_NAME$
from $APP_NAME$.tests.factories import $MODEL_NAME$Factory


class Test$SERIALIZER_NAME$(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.serializer = $SERIALIZER_NAME$
        cls.$MODEL_NAME_SNAKE_CASE$ = $MODEL_NAME$Factory()
        cls.data = cls.serializer(cls.$MODEL_NAME_SNAKE_CASE$).data

    def test_contains_expected_fields(self):
        expected_keys = {
            "id",
            "$EXPECTED_FIELD_1$",
            $END$
        }
        self.assertSetEqual(set(self.data.keys()), expected_keys)

    def test_returns_the_expected_values(self):
        self.assertEqual(self.data["id"], str(self.$MODEL_NAME_SNAKE_CASE$.id))
        self.assertEqual(self.data["$EXPECTED_FIELD_1$"], self.user.$EXPECTED_FIELD_1$)

```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x] |
| SERIALIZER_NAME |  |  | - [ ] |
| SERIALIZER_NAME_SNAKE_CASE | snakeCase(SERIALIZER_NAME) |  | - [x] |
| MODEL_NAME | capitalize(camelCase(groovyScript("return _1.replace('test_','').replace('_serializer.py','')", fileName()))) |  | - [ ] |
| MODEL_NAME_SNAKE_CASE | snakeCase(MODEL_NAME) |  | - [x] |
| EXPECTED_FIELD_1 |  |  | - [ ] |

### Applicable contexts
- Python: top-level.

### Example result
```python
from django.test import TestCase

from accounts.serializers.user_serializer import UserSerializer
from accounts.tests.factories import UserFactory


class TestUserSerializer(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.serializer = UserSerializer
        cls.user = UserFactory()
        cls.data = cls.serializer(cls.user).data

    def test_contains_expected_fields(self):
        expected_keys = {
            "id",
            "first_name",
        }
        self.assertSetEqual(set(self.data.keys()), expected_keys)

    def test_returns_the_expected_values(self):
        self.assertEqual(self.data["id"], str(self.user.id))
        self.assertEqual(self.data["first_name"], self.user.first_name)

```

### Additional notes
- Must be in its own file called `test_model_name_serializer.py` (where `model_name` is the name of your model in snake_case)
- You must continue to add fields to `expected_keys` dict.
- You must continue to add assertions to `test_returns_the_expected_values`