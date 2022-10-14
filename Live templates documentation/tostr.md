# tostr

### Description
Create a simple  __str__ method

### Template text
```python
def __str__(self):
    return f"{self.$FIRST_ATTRIBUTE$} - {self.$SECOND_ATTRIBUTE$}"
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| FIRST_ATTRIBUTE |  |  | - [ ] |
| SECOND_ATTRIBUTE |  |  | - [ ] |

### Applicable contexts
- Python: class.

### Example result
```python
def __str__(self):
    return f"{self.name} - {self.short_description$}"
```
