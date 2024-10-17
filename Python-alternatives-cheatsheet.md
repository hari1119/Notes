## Python Advance / Alternative Concept.

### Use PyProject.toml instead of requirements.txt

- Don’t do it. Stop putting in your README.md “install dependencies with pip install -r requirements.txt”. Can pip do it? Yes. Should you? No. requirements.txt is a accidental standard. Just use pyproject.toml. It makes sense, pip understands it, you can define dev and groups of dependencies in it so you don’t have to start using “dev-requirements.txt” and a slew of cicd pipeline rules.

### Use a python version and project manager like Poetry or UV
- I’m partial to UV, but I like Poetry too. They both will read the pyproject.toml file, handle dependencies, building, running applications in sandboxes, managing version of python and more. It will take you an hour to read about these tools and it will save you head ache.

At a bare minimum, use a virtual environment like ```venv``` to save yourself some global dependency headaches.

Also UV will install dependencies way faster than pip.

### Use Type hints
- Use hints to understand the code.
```python3
def alter_map(data: Map) -> None:
""" Alters data in a 2d map. Alters the object refernced directly
"""
  for x in map:
    for y in map[x]:
      transmute(map[x][y])
```
### Add a Raises section to your function docstrings

```python3
from typing import Dict, Any, optional

def query_db(query: SqlQuery) -> Optional[Dict[str, Any]:
  """Calls the database
  Args:
    ...

  Raises:
    ClientException: you goofed up
    TimeoutException: db took too long
    ConnectionException: something is wrong with your network

  Returns:
    The response from the query, if any.
  """
```

### Use a linter and formatter like Ruff

- Javascript projects have prettier and its a near standard at this point. In Python, use ruff (which copies Black’s formatting standard) and its fast. it also will lint common issues that you might have missed. this linting is not as in depth as a static analysis tool like mypy, but sure does help.

- While you’re add it, add a few of these opt-in rules into your pyproject.toml to make your code base even better:

```toml
[tool.ruff]
target-version = "py12"

[tool.ruff.lint]
extend-select: [
  'D', #pydocstyle
  'E', 'W', # pycodestyle
  'F', #pyflakes
  'I', # sort imports
  'UP', #pyupgrade
  "RUF",  # ruff dev's own rules
  "SIM", # pyflakes simplicity
  "C90", # more complexity rules
]

[tool.ruff.lint.pydocstyle]
convention = "google"

[tool.ruff.lint.isort]
combine-as-imports = true
split-on-trailing-commas = false
```

### Use Pytest over unittest

- Where is makes sense to convert, use pytest over unittest. The pytest fixtures are very helpful and composable.


### Using Dictionaries to avoid “if-elif” hell

 - Instead of ```IF-ElIF``` we can use the python dictionary methods.
 ###### Example
 
 ```python3
from collections.abc import Callable

# Function 1 
def first():
  print("Calling First Function...")


# Function 2
def second():
  print("Calling Second Function...")


# Function 3
def third():
  print("Calling Third Function...")


# Function Default
def default():
  print("Calling Default Function...")

# User Input
options: int = int(input("Enter an option :", ))

# Dictionary to hold options as key and functions as values  
funcs_dict : dict[int, Callable[[], None]] = {1: first, 2: second, 3: third}

# Checking if the key exist and incase it doesn't then deafult function will run
final_result = funcs_dict.get(options, default)
final_result()

```

### Using “Memoization” to Optimize Code

- To check the time complex in the regular code, use the below code to check the time of excution and improve the code quality.

 ###### Example
 
```python3
import time

def memo_fibonacci(num: int, dictionary: dict[int, int]):
    if num in dictionary:
        return dictionary[num]
    else:
        dictionary[num] = memo_fibonacci(num-1, dictionary) + memo_fibonacci(num-2, dictionary)
        return dictionary[num]

# Catching using a Dictionary
dictionary: dict[int, int] = {0: 1, 1: 1}

# Elapsed time
start_time: float = time.time()
# Calling the function
result: int = memo_fibonacci(48, dictionary)
end_time: float = time.time()
# Calculating the elapsed time
elapsed_time: float = end_time - start_time


print(f"Result: {result}") # Result: 7778742049
print(f"Elapsed time: {elapsed_time:.6f} seconds") # Elapsed time: 0.000133 seconds
```

### Using “@decorators” to avoid Repetitiveness

- We can use the @decorators for the avoid the duplication of the code.
###### Example

```python3
import time

def elapsed_time(func):
    def wrapper():
        start_time: float = time.time()
        
        func()
        
        end_time: float = time.time() - start_time
        print(f"{func.__name__}() took {end_time:.6f} seconds")
        
    return wrapper

@elapsed_time
def some_code():
    # Simulating running code..
    time.sleep(0.00002)

# Calling the function
some_code() # some_code() took 0.000009 seconds
```
### Using “all” Operator instead “and” | “any” Operator instead “or”

- we can use this ```all``` and ```any```, to avoid the learge number of line code.

#### ```all```
```python3
# User input from a registration form 
form_data: dict[str, str] = {"name" : "Nikita", 
             "email": "analyticalnikita@gmail.com",
             "phone": "123478911"}

# List of reuired fields
required_fields: list[str] = ["name", "email", "phone"]

# Using all operator
if all(field in form_data for field in required_fields):
    print("All required fields are filled out.")
else:
    print("Some required fields are missing or empty.")
```

#### ```any```

```python3
# List of permissions to the user
user_permission: list[str] = ["read", "execute"]

# Check if user has at least one of the required permissions
required_permissions: list[str] = ["write", "read", "admin"]
    
# Using "all" operator
if any(permission in user_permission for permission in required_permissions):
    print(f"Since you have required permissions. Access is allowed.")
else:
    print("You're a standard user. Not allowed the access.")
```

### Using the Comprehensions for Shorter Syntax
- #### List Comprehensions
  ##### Example

  ```python3
    # Nested-if using List Comprehension
    fruits: list[str] = ["apple", "orange", "avacado", "kiwi", "banana"]
    basket: list[str] = ["apple", "avacado", "apricot", "kiwi"]

    [i for i in fruits if i in basket if i.startswith("a")] # ['apple', 'avacado']
  ```
- #### Tuple Comprehensions
  ##### Example
  
  ```python3
  # Generator expression converted to a tuple
  tuple(i**2 for i in range(10))

  # (0, 1, 4, 9, 16, 25, 36, 49, 64, 81)
  ```

- #### Dictionary Comprehensions
  ##### Example

    ```python3
    # Creating a set with condition
    print({i**2 for i in range(1, 11) if i > 5})
    # {64, 36, 100, 49, 81}
    ```
