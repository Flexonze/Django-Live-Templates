# foreignkey

### Description
Create a ForeignKey field

### Template text
```python
$FOREIGN_KEY$ = models.ForeignKey(
    $FOREIGN_KEY_MODEL$, 
    on_delete=models.$FOREIGN_KEY_ON_DELETE$,
    null=$FOREIGN_KEY_NULL$, 
    blank=$FOREIGN_KEY_BLANK$,
)
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| FOREIGN_KEY | capitalize(camelCase(FOREIGN_KEY)) |  | - [ ] |
| FOREIGN_KEY_MODEL | enum("CASCADE", "PROTECT", "RESTRICT", "SET", "SET_NULL", "SET_DEFAULT", "DO_NOTHING") | "CASCADE" | - [ ] |
| FOREIGN_KEY_ON_DELETE | enum("False", "True") |  | - [ ] |
| FOREIGN_KEY_NULL | enum("False", "True") |  | - [ ] |
| FOREIGN_KEY_BLANK |  |  | - [ ] |

### Applicable contexts
- Python: class.

### Example result
```python
team = models.ForeignKey(
    Team,
    on_delete=models.CASCADE,
    null=False,
    blank=False,
)
```
