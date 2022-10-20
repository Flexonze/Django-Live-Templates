# get_related_model_count

### Description
method that returns the count as a link that automatically filters related model in your ModelAdmin

### Template text
```python
def get_$RELATED_MODEL_SNAKE_CASE$_count(self, obj):
    count = obj.$RELATED_MODEL_SNAKE_CASE$s.count()

    if count == 0:
        return "-"

    base_url = reverse("admin:$APP_NAME$_$RELATED_MODEL_LOWER$_changelist")
    url = base_url + f"?$MODEL_NAME_LOWER$__id__exact={obj.id}"
    return mark_safe('<a href="{}">{}</a>'.format(url, f"{count} (see)"))
        
get_$RELATED_MODEL_SNAKE_CASE$_count.short_description = "$RELATED_MODEL_STR$s"
$END$
```

### Template variables
| Name          | Expression | Default value | Skip if defined |
|---------------|------------|---------------|-----------------|
| APP_NAME | groovyScript("return _1.split('/').take(1);", fileRelativePath()) |  | - [x] |
| RELATED_MODEL_SNAKE_CASE |  |  | - [ ] |
| RELATED_MODEL_LOWER | groovyScript("return _1.replace('_', '')", RELATED_MODEL_SNAKE_CASE) |  | - [x] |
| MODEL_NAME_LOWER | groovyScript("return _1.replace('_admin.py', '').replace('_', '')", fileName()) |  | - [x] |
| RELATED_MODEL_STR | capitalize(underscoresToSpaces(RELATED_MODEL_SNAKE_CASE)) |  | - [x] |

### Applicable contexts
- Python: class.

### Example result
```python
def get_project_count(self, obj):
    count = obj.projects.count()

    if count == 0:
        return "-"

    base_url = reverse("admin:myapp_project_changelist")
    url = base_url + f"?team__id__exact={obj.id}"
    return mark_safe('<a href="{}">{}</a>'.format(url, f"{count} (see)"))

get_project_count.short_description = "Projects"
```

### Additional notes
 - Will need to import `reverse` and `mark_safe`.
 ```python
from django.urls import reverse
from django.utils.safestring import mark_safe
 ```

 - Add the method name to `list_display`. Examples:
 ```python
 list_display = ["name", "get_project_count"]
 ```