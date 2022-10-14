# Template Name

### Description
Create a CharField

### Template text
```python
$FIELD$ = models.CharField(
    max_length=$FIELD_LENGHT$, 
    null=$FIELD_NULL$, 
    blank=$FIELD_BLANK$,
    default=$FIELD_DEFAULT$,
)
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| FIELD | | | - [ ] |
| FIELD_LENGTH| | "254" | - [ ] |
| FIELD_NULL | enum("False", "True") | | - [ ] |
| FIELD_BLANK | enum("False", "True") | | - [ ] |
| FIELD_DEFAULT | | "\"\"" | - [ ] |


### Applicable contexts
- Python: class.


### Example result
```python
description = models.CharField(
    max_length=254,
    null=False,
    blank=False,
    default="A project description",
)
```
