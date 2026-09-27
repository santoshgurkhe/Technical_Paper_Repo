## 1. What is `on_delete=models.CASCADE`?

- `on_delete` defines what happens to related records when a referenced object is deleted.
- `CASCADE` means deleting the parent also deletes its related child records.

Example:

```python
class Choice(models.Model):
    question = models.ForeignKey(
        Question,
        on_delete=models.CASCADE
    )
```
If a Question is deleted, its related Choice objects are also deleted.

## 2. What are Django Model Fields?

- Fields define the **type of data** stored in a database table.
- Each model field usually represents a database column.

### Common Fields

- `CharField` - Short text
- `TextField` - Long text
- `IntegerField` - Integer numbers
- `FloatField` - Decimal numbers
- `BooleanField` - True or False
- `DateField` - Date
- `DateTimeField` - Date and time
- `ForeignKey` - Relationship between models
- `EmailField` - Email address

Example:

```python
class Product(models.Model):
    name = models.CharField(max_length=100)
    price = models.IntegerField()
    available = models.BooleanField(default=True)
```

## Important Field Options
- null=True → Allows NULL in the database.
- blank=True → Allows the field to be empty during validation.
- default → Gives the field a default value.
- unique=True → Does not allow duplicate values.
- primary_key=True → Makes the field the primary key.
- choices → Allows only predefined choices.
- max_length → Sets the maximum length for text.

## 3. What are Django Validators?

- Validators are used to check whether a value is valid.
- They are used with model fields.

### Common Validators

- `MinValueValidator` → Minimum number
- `MaxValueValidator` → Maximum number
- `MinLengthValidator` → Minimum length
- `MaxLengthValidator` → Maximum length
- `RegexValidator` → Checks a pattern
- `EmailValidator` → Checks email format
- `URLValidator` → Checks URL format

### Example

```python
from django.core.validators import MinValueValidator

age = models.IntegerField(
    validators=[MinValueValidator(18)]
)
```


## 12. Module vs Class in Django

- Module is a Python file like `models.py` or `views.py`.
- Class is written inside a module and is used to create objects.

Example:

```python
# models.py

class Question(models.Model):
    pass
```

- models.py → Module
- Question → Class
```
Module = Python file
Class = Code written inside the file
```

