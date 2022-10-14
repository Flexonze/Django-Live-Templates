# choicefield

### Description
Create a CharField with choices

### Template text
```python
$FIELD$ = models.CharField(
    max_length=$FIELD_LENGTH$, 
    null=$FIELD_NULL$, 
    blank=$FIELD_BLANK$,
    choices=$FIELD_CHOICES$.choices,
    default=$FIELD_CHOICES$.$FIELD_DEFAULT$,
)
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| FIELD |  |  | - [ ] |
| FIELD_LENGTH |  | "25" | - [ ] |
| FIELD_NULL | enum("False", "True") |  | - [ ] |
| FIELD_BLANK | enum("False", "True") |  | - [ ] |
| FIELD_CHOICES | capitalize(camelCase(FIELD)) |  | - [ ] |
| FIELD_DEFAULT |  |  | - [ ] |

### Applicable contexts
- Python: class.

### Example result
```python
gender = models.CharField(
    max_length=25,
    null=False,
    blank=False,
    choices=Genders.choices,
    default=Genders.MALE,
)
```