
# Variable Roles Solutions

## Fixed Value
A variable takes the role of a "fixed value" if its value is not modified at runtime, **after initialization**.

```python
pi = 3.14
r = float(input("Enter the radius:"))
vol = (4/3)*pi*(r**3)
print("The volume of the sphere is", vol)
```

Both the variables ```pi``` and ```r``` are **fixed values**.
The variable ```vol``` is  [a temporary variable]
What does the program do? [It returns the volume of a sphere with the input radius]

## Stepper or Index

The stepper/index is used to iterate through a sequence of values systematically. It can also be used to count or as an index of an array/list.

```python
n = int(input("Which multiplication table do you want?:"))
factor = 0
while factor < 11:
    print(n,"x",factor,"=",n*factor)
    factor += 1
```
The variable ```factor``` is a stepper/index.
The variable ```n``` is  [a fixed value]
What does the program do? [Prints the multiplication table of n from nx0 to nx10]

## Most Recent Holder

A variable is a **most recent holder** if it contains the most recent value I have of a certain sequence or input.

```python
grade = float(input("Enter a grade (from 1 to 10): "))
while (grade < 1 or grade > 10):
    print("The grade must be between 1 and 10")
    grade = float(input("Enter a grade (from 1 to 10): "))
print(grade)
```

The variable ```grade``` is a **most recent holder**.
What does the program do? [It takes an input grade until the user provides a legal value (i.e., grade >= 1 and <= 10)]

## Most Wanted Holder

This is the "best" value I have found up to this point.

```python
L = [3, 1, 4, 10, 2, 7]
max_value = L[0]
for e in L[1:]:
    if e > max_value:
        max_value = e
print("Max value: ", max_value)
```

The variable ```max_value``` is a **most wanted holder**.
The variable ```L``` is  [a fixed value]
The variable ```e``` is  [a walker]
What does the program do? [Finds and prints the maximum value in L]


## Gatherer
A gatherer collects all the values I have found up to this point. Typically, it is initialized with the neutral element of the accumulation operation (e.g., 0 if summing, 1 if multiplying, empty collection if collecting, empty string, True or False, etc.).

```python
s = 0
n = 0
i = int(input("Rainfall: "))
while i != 99999:
    if i >= 0:
        s += i
        n += 1
    i = int(input("Rainfall: "))

if n > 0:
    print("Average rainfall:", s/n)
else:
    print("No data")
```

The variable ```s``` is a **gatherer**.
The variable ```n``` is  [a counter or a gatherer]
The variable ```i``` is  [a most recent holder]


## Follower
A variable is a *follower* if it contains the value of another variable at the moment when the latter assumes a new value (thus remembering the previous value of the latter).

```python
#From an idea by Dario Malchiodi
prev_fibo = 0
fibo = 1
count = 2
while fibo < 4000000:
   c = prev_fibo + fibo
   prev_fibo = fibo
   fibo = c
   count += 1
print(count)
```
The variable ```prev_fibo``` is a **follower** of the variable ```fibo```
The variable ```count``` is [a counter]
The variable ```c``` is [a temporary variable (or less evidently, a gatherer)]
What does the program do? [Counts how many Fibonacci numbers are < 4000000]

## One-Way Flag

A one-way flag is a boolean that can be changed only once, after which it cannot be reverted to its original value (it is "write once").

```python
s = "Michael Lodi"
space_found = False
vowel_count = 0
for c in s:
    if c in "aeiouAEIOU":
        vowel_count += 1
    elif c == " ":
        space_found = True
print("The string", s, "contains", vowel_count, "vowels.")
if space_found:
    print("The string", s, "contains at least one space")
```

The variable ```space_found``` is a **one-way flag**
The variable ```vowel_count``` is  [a counter]
The variable ```c``` is  [a walker]
The variable ```s``` is  [a fixed value]
What does the program do? [Prints the number of vowels in the string s, and a message if s contains at least one space]

## Temporary

A variable is temporary if its value is used only for a brief period of time [and only for intermediate calculations], such as in variable swapping. It is also used for efficiency reasons (storing a value that would otherwise be recalculated multiple times) or to make a program more readable.

```python
M = [[1,2,3],[4,5,6]]
MT = []
rows = len(M)
if rows != 0:
    cols = len(M[0])
    for i in range(cols):
        col = []
        for j in range(rows):
            col.append(M[j][i])
        MT.append(col)
print(MT)
```
The variables ```rows``` and  ```cols``` are **temporary** variables.
The variables ```rows``` and  ```cols``` are also [fixed values]
The variables ```MT``` and ```col``` are [gatherers]
The variable ```col``` is also [temporary]
The variables ```i``` and ```j``` are [steppers]
What does the program do? [Prints the transpose of matrix M]




## Walker

A walker is used to traverse the elements of a data structure (for example in a "foreach" loop).

```python
class Node:
    def __init__(self, value=None, next_node=None):
        self.value = value
        self.next_node = next_node
    def __str__(self):
        return str(self.value)

LL = Node(1, Node(2, Node(3)))

p = LL
while p is not None:
    print(p, end = " ")
    p = p.next_node
print()
```

The variable ```p``` is a **walker**
The variable ```LL``` is  [a fixed value]
What does the program do? [Traverses and prints all the values of the Linked List LL]