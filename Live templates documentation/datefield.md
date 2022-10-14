# datefield

### Description
Create a date field

### Template text
```python
$FIELD$ = models.DateField(
    null=$FIELD_NULL$, 
    blank=$FIELD_BLANK$,
    default=$FIELD_DEFAULT$,
)
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| FIELD |  |  | - [ ] |
| FIELD_NULL | enum("False", "True") |  | - [ ] |
| FIELD_BLANK | enum("False", "True") |  | - [ ] |
| FIELD_DEFAULT |  | "\"\"" | - [ ] |

### Applicable contexts
- Python: class.

### Example result
```python
birthday = models.DateField(
    null=True,
    blank=True,
    default=date.today,
)
```