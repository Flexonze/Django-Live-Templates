# simplelistfilter

### Description
Create a basic SimpleListFilter

### Template text
```python
from django.contrib.admin import SimpleListFilter
from django.utils.translation import gettext as _


class $FILTER_NAME_CAMEL_CASE$Filter(SimpleListFilter):
    title = _("$FILTER_NAME$")
    parameter_name = "$FILTER_NAME_SNAKE_CASE$"

    def lookups(self, request, model_admin):
        return (
            ("$LOOKUP_VALUE$", _("$LOOKUP_VALUE_CAPITALIZED$")),$END$
        )

    def queryset(self, request, queryset):
        if self.value() == "$LOOKUP_VALUE$":
            return queryset.filter($FILTER_NAME_SNAKE_CASE_EDITABLE$=True)
        else:
            return queryset

```

### Template variables
| Name                   | Expression | Default value | Skip if defined |
|------------------------|-----------|---------------|-----------------|
| FILTER_NAME_CAMEL_CASE | capitalize(camelCase(FILTER_NAME)) | | - [x]           |
| FILTER_NAME            | groovyScript("return _1.replace('_filter.py', '')", fileName()) | | - [x]           |
| FILTER_NAME_SNAKE_CASE | snakeCase(FILTER_NAME) | | - [x]           |
| LOOKUP_VALUE | | | - [ ] |
| LOOKUP_VALUE_CAPITALIZED | capitalize(spaceSeparated(LOOKUP_VALUE)) | | - [x] |
| FILTER_NAME_SNAKE_CASE_EDITABLE | FILTER_NAME_SNAKE_CASE | | - [ ] |


### Applicable contexts
- Python: top-level.


### Example result
```python
from django.contrib.admin import SimpleListFilter
from django.utils.translation import gettext as _


class CategoryFilter(SimpleListFilter):
    title = _("category")
    parameter_name = "category"

    def lookups(self, request, model_admin):
        return (
            ("some_category", _("Some category")),
            ("other_categories", _("Other")),
        )

    def queryset(self, request, queryset):
        if self.value() == "some_category":
            return queryset.filter(category='some_category')
        elif self.value() == "some_other_category":
            return queryset.exclude(category='some_category')
        else:
            return queryset

```

### Additional notes
 - Must be in its own file called `some_name_filter.py` (where `some_name` is the name of your filter in snake_case)