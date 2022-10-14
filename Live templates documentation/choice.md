# Template Name

### Description
Template description

### Template text
```python
$CHOICE$ = "$CHOICE_VALUE$", _("$CHOICE_VERBOSE$")
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| CHOICE |            |               | - [ ]           |
| CHOICE_VALUE | snakeCase(CHOICE) | | - [ ] |
| CHOICE_VERBOSE | spaceSeparated(lowercaseAndDash(CHOICE)) | | - [ ] |

### Applicable contexts
- Python: class, top-level.


### Example result
```python
MALE = "male", _("Male")
```

### Additional notes
 - Requires `ugettext_lazy` to be imported as `_`. See `gettextlazy.md`