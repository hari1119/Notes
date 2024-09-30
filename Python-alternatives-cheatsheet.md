## Python Advance / Alternative Consept.

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
