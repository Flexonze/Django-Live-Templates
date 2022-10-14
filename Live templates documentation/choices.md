# choices

### Description
Create a new TextChoices class

### Template text
```python
class $CLASS$(models.TextChoices):
    $CHOICE$ = "$CHOICE_VALUE$", _("$CHOICE_VERBOSE$")$END$
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| CLASS |  |  | - [ ] |
| CHOICE |  |  | - [ ] |
| CHOICE_VALUE | snakeCase(CHOICE) |  | - [ ] |
| CHOICE_VERBOSE | spaceSeparated(lowercaseAndDash(CHOICE)) |  | - [ ] |

### Applicable contexts
- Python: class, top-level.

### Example result
```python
class Genders(models.TextChoices):
    Male = "male", _("Male")
```
