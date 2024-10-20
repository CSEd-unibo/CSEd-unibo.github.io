## Possible Solution
These examples are certainly "non-obvious," and some may not be suitable for students who are just beginning to program.

### Simple Linear Scan
```python
def map_function(f, S):
    """Given a function f and a mutable sequence S, applies f to each element of S."""
    for i in range(len(S)):
        S[i] = f(S[i])

def double(e):
    return e * 2

S = [1, 2, 3]
map_function(double, S)
print(S)
S = ['a', 'b', 'c']
map_function(double, S)
print(S)
```

### Linear Scan with Accumulation
```python
'''Check if randint(0,1) is balanced'''
throws = 10**6
heads = 0
i = 0
from random import randint
while i < throws:
    heads += randint(0,1)
    i += 1
print(heads, throws//2)
```

### Certain Linear Search
```python
# Search for the next leap year!

from calendar import isleap
from datetime import datetime

year = datetime.today().year + 1 # next year

while not isleap(year):
    year += 1
print(year)
```

### Uncertain Linear Search
```python
def is_numeric_sequence(S):
    """True if and only if S is a sequence of all numbers (int, float, complex)."""
    for e in S:
        if type(e) not in (int, float, complex):
            return False
    return True
```

### Linear Scan (Simple or with Accumulation) Until a Sentinel is Reached
```python
"""How many tries does it take to extract 42?"""
from random import randint
r = randint(0, 100)
i = 1
while r != 42:
    r = randint(0, 100)
    i += 1
print("It took", i, "tries to get 42")
```

### Input Reading Until the Desired Value is Received
```python
from ast import literal_eval
# Safer than eval

tuple_input = literal_eval(input("Enter a numeric tuple, separated by commas: "))
while not is_numeric_sequence(tuple_input):
    print("The tuple must be a numeric sequence")
    tuple_input = literal_eval(input("Enter a numeric tuple, separated by commas: "))
print(tuple_input)
```
