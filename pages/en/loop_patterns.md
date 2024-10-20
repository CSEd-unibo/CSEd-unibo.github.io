# Basic Patterns for Scanning Sequences or Collections

A _pattern_ can be defined as _"a general design solution to a recurring problem"_ [3].

An _elementary pattern_ is a pattern suitable for novices to help them learn fundamental programming concepts [4].

Students, by reading, tracing, completing, or solving various instances of different and diverse problems sharing a common resolution pattern, can learn these patterns and apply them in new contexts that can be solved with the same solution schema.

It's not about teaching the pattern in the abstract, but rather observing it (and naming it) explicitly in concrete instances of its application.

## Linear Scans

These are scans where we process *all* the elements of a collection, knowing in advance (possibly in constant time) how many elements there are or when we have reached the end.

Thus, they can be used on iterable collections (e.g., `for e in s: print(e)`) or on indexable collections (e.g., `for i in range(len(s)): print(s[i])`).

### Simple Linear Scan
These are scans where each iteration contributes parts of the result.

With an iterator:
```
for each e in c:
   process e
```

With indices:
```
for i ranging between the extreme values of the indices of c: # (e.g., between 0 and len(c))
   process c[i]
   increment or decrement i
```

With indices and while:
```
i = one of the extreme values of c
while i is less than one of the extreme values of the indices of c: # (e.g., between 0 and len(c))
   process c[i]
   increment or decrement i
```

_Example._ Write a function that _prints_ all the elements of a collection on separate lines.

```python
# with iterator
def print_it(c):
  for e in c:
    print(e)

l = [1, 3, 5]
print_it(l)
t = ('M', 'F', 'X')
print_it(t)
d = {'Michael', 'Stefano', 'Simone', 'Elisa'}
print_it(d) # note that sets are unordered but can be enumerated and iterated

# with index
def print_in(c):
  for i in range(len(c)):
    print(c[i])

print_in(l)
print_in(t)
# print_in(d) # sets are unordered and non-indexable
```

_Example._ Write a function that _prints_ the **letters** of a string passed as a parameter in reverse order.

```python
def reverse(s):
  for i in range(len(s), 0, -1): # i ranges between len(s) (included) and 0 (excluded): [len(s), 0[
    print(s[i-1]) # while the vector's indices range from ]len(s), 0], which is why we need i-1

reverse('hello')
```

_Example._ Write a Python function that *prints* **the vowels** of a string passed as a parameter.

```python
def print_vowels(s):
  vowels = 'aeiouAEIOU'
  for l in s:
    if l in vowels:
      print(l)

print_vowels('hello')
```

Python allows iterating over the elements of a string with the `for` construct (`for c in s`).
Alternatively, we can access each character by its index.

```python
def print_vowels(s):
  vowels = 'aeiouAEIOU'
  for i in range(len(s)): # range(len(s)) indicates [0, len(s)[
    if s[i] in vowels:
      print(s[i])

print_vowels('hello')
```

### Linear Scan with Accumulation
This is a scan where iterating helps to build successive approximations of the result.

```
accumulator = neutral element #(e.g., 0 if sum, 1 if product, empty collection if collection, empty string, True or False...)
for each e in c:
   if e satisfies a condition: #(this might not even be necessary)
      accumulator += value to accumulate
output accumulator
```

(It is straightforward to construct the version with indices, working on ``c[i]`` instead of ``e``).

_Example._ Write a function that **returns the length of a sequence** without using Python's built-in `len()` method.

```python
def length(seq):
  accumulator = 0
  for e in seq:
    accumulator += 1
  return accumulator

print(length('hello'))
```

_Example._ Write a function that _prints_ **the number of vowels** in a string passed as a parameter.

```python
def print_num_vowels(s):
  vowels = 'aeiouAEIOU' # you might want to consider accented vowels as well
  num_vowels = 0
  for l in s:
    if l in vowels:
      num_vowels += 1
  print('There are ' + str(num_vowels) + ' vowels in the string ' + s)

print_num_vowels('hello')
```

_Example._ Write a Python function that *returns* **a string containing the vowels** of a string passed as a parameter.

```python
def get_vowels(s):
  vowels = 'aeiouAEIOU'
  vowels_in_s = ''
  for letter in s:
    if letter in vowels:
      vowels_in_s += letter
  return vowels_in_s

print(get_vowels('hello'))
```

## Linear Search

### Certain Linear Search

We search for an element ``e`` (for example, in a sequence of numbers, or in a sequence or collection ``c``) that satisfies a certain condition. We stop when we find it.

With an iterator:
```
for each e in c:
   if e satisfies the condition:
      action upon finding
      exit the loop
```

With indices:
```
for i between the extreme indices of c:
  if c[i] satisfies the condition:
     action upon finding
     exit the loop
  increment i
```

With while:
```
i = 0
while i < length(c):
   if c[i] satisfies the condition:
     action upon finding
     exit the loop
   increment i
```

With while, combining conditions:
```
i = 0
while i < length(c) and c[i] does not satisfy the condition:
   increment i
action upon finding
```

For the latter case, we assume that the programming language uses lazy evaluation ("short-circuit evaluation") of boolean expressions: e.g., if the first operand of an AND is false, the second one is not evaluated (and False is returned); similarly, if the first operand of an OR is true, the second one is not evaluated (and True is returned).
Without this assumption, if ``i == length(c)``, continuing to evaluate the expression in the "while" condition would attempt to access ``c[i]``, which would be out of range for the collection (where the indices range from ``0`` to ``length(c)-1``).

_Example._ Define a Python function that **returns ``True`` if an element** (provided as a parameter) **is found in a collection** (provided as a parameter). Use a loop to process the elements of the collection, providing a strategy to exit the loop early if the target element is found before reaching the end of the scan.

```python
def linear_search(elem, seq):
  for e in seq:
    if e == elem:
      return True
```

### Uncertain Linear Search

We search for an element ``e`` (for example, in a sequence of numbers, or in a sequence or collection ``c``) that satisfies a certain condition. We must handle the special case where the element is not present.

With an iterator:
```
for each e in c:
   if e satisfies the condition:
      action upon finding
      exit the loop
action upon *not* finding
```

With indices:
```
for i between the extreme indices of c:
  if c[i] satisfies the condition:
     action upon finding
     exit the loop
  increment i
action upon *not* finding
```

With while:
```
i = 0
while i < length(c):
   if c[i] satisfies the condition:
     action upon finding
     exit the loop
   increment i
action upon *not* finding
```

With while, combining conditions:
```
i = 0
while i < length(c) and c[i] does not satisfy the condition:
   increment i
if i != length(c):
   action upon finding
else:
   action upon *not* finding
```

NB: We assume lazy evaluation...

_Example._ Modify the previous solution to handle the case where the target of the search **is not found** in the collection, treating it as a special case.

```python
def linear_search(elem, seq):
  for e in seq:
    if e == elem:
      return True
  return False
```

Similarly, a solution using the `while` construct can be defined as follows:

```python
def linear_search_while(elem, seq):
  i = 0
  while i < len(seq):
    if seq[i] == elem:
      return True
    i += 1
  return False
```

Or, more compactly:

```python
def linear_search_while(elem, seq):
  i = 0
  while i < len(seq) and seq[i] != elem:
    i += 1
  return i != len(seq)
```

_Example._ Write a function that returns ``True`` if the number ``n`` passed as a parameter is **prime**, and ``False`` otherwise.
This is

 the "obvious" algorithm, corresponding to searching for a divisor of ``n`` among the numbers smaller than ``n``.

```python
def is_prime(n): # assuming n > 1
  for i in range(2, n): # actually, you only need to check up to sqrt(n)
    if n % i == 0: # n is divisible by i
      return False # found a divisor other than 1 and itself
  return True # no divisors found
```

## "Interactive" Scans and Searches

In these cases, the length of the collection is not known in advance, and the user provides the elements one by one.

### Linear Scan (Simple or with Accumulation) Until a Sentinel is Reached

We want to read and process all the values entered one at a time by the user until a specific value, called the _sentinel_, is entered.

```
read value
while value != sentinel:
  process value
  read value
```

_Example._ Write a program that prompts for student grades (from 1 to 10), prints them (simple scan), sums them (accumulation scan), and ends when the user enters the number 0.

```python
sum_grades = 0
grade = int(input("Enter a grade (integer, from 1 to 10): "))
while grade != 0:
  print(grade)
  sum_grades += grade
  grade = int(input("Enter a grade (integer, from 1 to 10): "))
```

### Input Reading Until the Desired Value is Obtained

We ask the user for a value with specific constraints and keep asking until we get a "valid" value.

```
read value
while value is not valid:
  print "Invalid"
  read value
```

_Example._ Write a program that prompts the user for a grade. The program checks that it is between 1 and 10 (inclusive): if not, it asks again and continues until a "valid" grade is entered.

```python
  grade = float(input("Enter a grade (from 1 to 10): "))
  while (grade < 1 or grade > 10):
    print("The grade must be between 1 and 10")
    grade = float(input("Enter a grade (from 1 to 10): "))
```

#### Alternatives
If you want to avoid duplicating the input code, instead of the first read (the one outside the while), you can assign ``value`` a value that is surely invalid (e.g., ``grade = 0`` in the last example; this can also be adapted to the previous one), so that the ``while`` loop is guaranteed to execute at least once.
In languages that allow it (not Python), you can alternatively use the ``do... while`` construct.

Another option is to use exceptions.

_Example._ Write a program that prompts the user to enter an integer and keeps asking until an integer is provided.

```python
x = None
while x is None:
    try:
        x = int(input('Give me an integer: '))
    except ValueError:
        print('I wanted an integer, and you didn’t give me one.')
print("Thanks for giving me the integer", x)
```

# Exercise
* For each pattern, identify an example (different from the ones already presented and possibly not too obvious) of an application of the pattern, and write the corresponding Python code. [Example solution](pattern_solutions.md)

# References
1. [Owen Astrachan & Eugene Wallingford - Loop Patterns](http://www.cs.uni.edu/~wallingf/patterns/loops.html)
2. [Philip Guo - Python Tutor](http://pythontutor.com/visualize.html)
3. [Wikipedia - Design pattern](https://en.wikipedia.org/wiki/Design_pattern)
4. [Michael J. Clancy and Marcia C. Linn. 1999. Patterns and pedagogy. SIGCSE Bull. 31, 1](https://doi.org/10.1145/384266.299673)

*Thanks to Simone Martini and Stefano Pio Zingaro for their contributions to the improvement of this page*
