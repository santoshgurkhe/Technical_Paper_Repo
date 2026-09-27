## 1. Using ORM Queries in Django Shell

- Django ORM lets us work with the database using Python instead of SQL.
- We can use it inside the Django shell.

Open shell:

```bash
python manage.py shell
```
```py
from polls.models import Question

Question.objects.all()                 # Get all
Question.objects.get(id=1)             # Get one
Question.objects.filter(id=1)          # Filter
Question.objects.create(...)           # Create
Question.objects.filter(id=1).update(...)  # Update
Question.objects.filter(id=1).delete()     # Delete
```

## 2. What are Aggregations and Annotations?

Both are used to calculate values from database records, but they are used differently.

### Aggregation

Aggregation gives **one final result** from multiple records.

Example:

```python
from django.db.models import Avg

Question.objects.aggregate(Avg("id"))
```
### Annotation

Annotation adds a calculated value to each record.

Example:
```py
from django.db.models import Count

Question.objects.annotate(
    choice_count=Count("choice")
)
```
Now each Question has its own choice_count.

## 3. What is a Migration File in Django?

- A migration file records changes made to Django models.
- It helps apply those changes to the database.

### Commands

```bash
python manage.py makemigrations
```

- Creates migration files based on model changes.
```py
python manage.py migrate
```
Applies the migration changes to the database.


## 4. What are SQL Transactions?

- A transaction is a group of database operations treated as one unit.
- Either all operations succeed, or all operations are cancelled.

### Simple Example

Suppose we transfer ₹500 from Account A to Account B.

1. Remove ₹500 from Account A.
2. Add ₹500 to Account B.

If step 2 fails, step 1 can also be cancelled using a rollback.


## 5. What are Atomic Transactions in Django?

- An atomic transaction makes sure that a group of database operations works as one unit.
- If any operation fails, all changes are rolled back.

In Django, we can use `transaction.atomic()`.

Example:

```python
from django.db import transaction

with transaction.atomic():
    account_a.balance -= 500
    account_a.save()

    account_b.balance += 500
    account_b.save()
```
