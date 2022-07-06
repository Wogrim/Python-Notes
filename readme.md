# Data Types and Variables

- variables are not explicitly declared (just assign stuff to them)
- (can make it harder to spot typos because no "undeclared" error)
- 

## primitives

### ints


### floats

### booleans

AND
`if i < 5 and i > 0:`

OR
`if i < 5 or i > 10:`

NOT
`if not i < 5:`

### strings

strings are immutable

you can access characters from a string with an index like a list  
also strings can be sliced like a list

## composites

there are sequence functions mentioned later which apply to all of these, plus strings

### lists

square brackets makes a list:  
`stuff = ["red", "yellow", "green", "blue"]`

- zero-indexed
- heterogenous (can have a mix of data types)
- allows negative index (-1 is last)

get and assign with common bracket notation
`stuff[0] = 5`

concatenate lists  
`combined = stuff1 + stuff2`

make a list that repeats 5 times
`stuff = ["A","B","C"] * 5`

slicing: get a part of the list  
from start until (not including) index 5
`stuff[:5]`  
from index 2 until the end  
`stuff[2:]`
from index 2 until (not including) last index
`stuff[2:-1]`
slicing with step value (in this case every second index)
`stuff[1::2]`

unpack a list as comma-separated arguments to a function  
`print(*stuff,sep=", ")`

also see list-specific functions

### tuples

similar to a list, but
- immutable
- use parentheses instead of square brackets when creating tuples
- (parentheses technically not required)

### dictionaries

map keys to values (hash table)  
it is uncommon to use anything other than a string for the key
```
scores = {
    "best": "Smith",
    "Bob": 5,
    "Joe": 10,
    "Jeff": 15,
    "Smith": [5,10,15,20]
}
print(scores["Joe"])
```
KeyError if you try to reference a key not in the dictionary

can check if a key is in the dictionary with
```
if "Joe" not in scores:
    print("Joe has no score")
```
(or without "not")

pop a dictionary value out of the dictionary
`val = scores.pop("Bob")`

delete a dictionary entry without doing anything with the value
`del scores["Joe"]`

clear the whole dictionary
`scores.clear()`

get a value, with a default returned value (instead of error) if it's not in the dictionary
`scores.get("James",default=0)`

`.keys()` for a list of keys  
`.values()` for a list of values
`.items()` for a list of (key, value) tuples  
`for name, score in scores.items():`

# synatax

- control flow of Python based on colons, new lines and indentation (not brackets)
- no semicolon at the end of each line
- `pass` = empty statement (required for empty loop)

## functions

defaults for paramters can be specified; can call function without them  
also, can target specific parameters ("named arguments") and the rest will use defaults  
parameters without defaults must be used in order
```
def doSomething(word="cool", story=1):
    print(word)
    return "cool"

doSomething("nice")
doSomething()
doSomething(story=5)
```

## loops

loop through i from 0 through 19  
`for i in range(20):
    print(i)`

for 1-20  
`range(1,21)`

for 4-20 by 2
`range(4,21,2)`

loop through a list of stuff
`stuff = ["red", "yellow", "green", "blue"]
for i in range(len(stuff)):
    print(stuff[i])`

foreach version (on lists, strings, tuples)
`for thing in things:
    print(thing)`

foreach on a dictionary
`for key in dict:
    print(f"{key}: {dict[key]})`

while loop
```
i = 0
while i < 20:
    print(i)
    i += 1
```

while else to run the else code once when the condition fails (not called if you break or return to exit the loop)
```
while cond:
    stuff.pop()
else:
    print("cond failed")
```

break and continue
```
while cond:
    if cond2:
        break
    if cond3:
        continue
    dostuff()
```

## if, elif, else

```
if len(stuff) < 10:
    print("A")
elif len(stuff) > 10:
    print("C")
else:
    print("B")
```

# Common Functions

print something
`print("hi")`
print multiple things (default separator = space)
`print("hi", "bye")`
print multiple things with a different separator
`print("hi", "bye", sep=",")`

## sequence functions

these work on lists, tuples, strings, and maybe dictionaries?

get the number of elements in the sequence  
`len(stuff)`

get the biggest value in the sequence  
`max(stuff)`

get the minimum value in the sequence
`min(stuff)`

get a sorted copy of the sequence  
`sorted(stuff)`

## list-specific functions

add 5 to the end of the list
`stuff.append(5)`

remove the last element in the list and store it
`last = stuff.pop()`

remove first element and store it
`another = stuff.pop(0)`

reverse the order of the list
`stuff.reverse()`

get the index of a certain value in the list
`print("index of Bob is", stuff.index("Bob"))`

sort the list (numbers or strings?)
`stuff.sort()`

empty the list
`stuff.clear()`