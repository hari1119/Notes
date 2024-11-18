## Django ORM Guide: Exploring All Model Methods and Operations

### 1. Creating a New Record
```python3
new_user = User.objects.create(email="newuser@example.com", first_name="New", last_name="User", is_active=True, is_staff=False)
```

### 2.Retrieving a Single Record
```python3
user = User.objects.get(id=1)
```

### 3.Retrieving All Records
```python3
users = User.objects.all()
```

### 4.Filtering Records by Condition
```python3
active_users = User.objects.filter(is_active=True)
```

### 5. Excluding Records by Condition
```python3
non_active_users = User.objects.exclude(is_active=True)
```

### 6. Updating a Record
```python3
user = User.objects.get(id=1)
user.first_name = "Jonathan"
user.save()
```

### 7. Bulk Updating Multiple Records

```python3
User.objects.filter(is_active=True).update(is_staff=True)
```

### 8.Deleting a Record

```python3
user = User.objects.get(id=3)
user.delete()
```
### 9. Soft Deleting a Record

```python3
category = Category.objects.get(id=3)
category.deleted = True
category.save()
```

### 10. Aggregating Data

```python3
from django.db.models import Sum
total_expenses = Expense.objects.aggregate(total=Sum('amount'))
```

### 11. Counting Records

```python3
total_users = User.objects.count()
```

### 12. Ordering Records

```python3
expenses = Expense.objects.order_by('-amount')
```

### 13. Limiting Query Results

```python3
limited_expenses = Expense.objects.all()[:2]
```

### 14. Using ```Q``` Objects for Complex Filtering

```python3
from django.db.models import Q
filtered_users = User.objects.filter(Q(is_active=True) | Q(is_staff=True))
```

### 15. Select Related for Optimizing Foreign Key Lookups

```python3
expenses = Expense.objects.select_related('user').all()
```

### 16. Prefetch Related for Optimizing Many-to-Many Lookups

```python3
categories = Category.objects.prefetch_related('expenses').all()
```

### 17. Getting Distinct Values

```python3
distinct_emails = User.objects.values('email').distinct()
```

### 18. Updating or Creating a Record (```update_or_create```)

```python3
user, created = User.objects.update_or_create(
    email="user1@example.com",
    defaults={"first_name": "Johnny"}
)
```

### 19. Deleting Multiple Records

```python3
User.objects.filter(is_staff=True).delete()
```

### 20. Annotating Data with Calculated Fields

```python3
from django.db.models import Count
categories = Category.objects.annotate(num_expenses=Count('expense'))
```

### 21. Raw SQL Queries

```python3
users = User.objects.raw("SELECT * FROM app_user WHERE is_active = true")
```

### 22. Transactions for Atomic Operations

```python3
from django.db import transaction

@transaction.atomic
def transfer_balance(user_id, amount):
    user = User.objects.select_for_update().get(id=user_id)
    user.balance.remaining_balance -= amount
    user.balance.save()
```

### 23. Batch Creating Records

```python3
Expense.objects.bulk_create([
    Expense(user_id=1, category_id=1, amount=20.00, description="Snack", date="2024-01-07"),
    Expense(user_id=2, category_id=2, amount=30.00, description="Internet", date="2024-01-07")
])
```









