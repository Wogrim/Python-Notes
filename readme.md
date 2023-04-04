# Getting Started

download Python from [python.org](https://www.python.org/downloads/)

during install, make sure to add to PATH so the command can be used in the terminal from anywhere

you can access the python interpreter in the terminal with `python` or `py` (maybe different on different versions)

or write some code in a **hello_world.py** file
```
#hello_world.py

print("hello world!")
```
and run the code from the terminal with
```
py hello_world.py
```

**pip** should be installed (and put in PATH) by default with Python installation
- pip is a terminal command for installing packages from [pypi.org](https://pypi.org/)

one-time installation of **pipenv** on your computer for putting your projects in virtual environments for dependency management
```
pip install pipenv
```

for a project, install packages it needs with pipenv, which will be tracked in *Pipfile*
```
pipenv install Flask
```
(this installs the Flask package for the virtual environment for the current folder)

in your code, use what you need from the package
```
#server.py
from flask import Flask

app = Flask(__name__)

if __name__ == "__main__"":
    app.run(debug = True)
```

or if you copy your project to another computer, to install the dependencies from the Pipfile
```
pipenv install
```

run the virtual environment and your code with
```
pipenv shell
py server.py
```

- stop your code with **Ctrl + C**
- leave the virtual environment with `exit`

# Funky Features of Python

- newlines and indentation determine control flow
- list comprehensions: fancy way to build a list (which is an array)
- list and string slicing and lots of built-in methods make common operations very easy
- integers can be as big as you have memory to hold them

# Data Types and Variables

- variables are not explicitly declared (just assign stuff to them)
  - can make it harder to spot typos because no "undeclared" error

## primitives

### numbers: int, float, complex

integer division and remainder and float division
```
x = 5//3
x = 5%3
x = 5/3
```

power
```
twentyfive = 5**2
```

### booleans

can be `True` or `False`

AND
```
if i < 5 and i > 0:
```

OR
```
if i < 5 or i > 10:
```

NOT (unary)
```
if not i < 5:
```

### strings

- you can read specific characters from a string with an index like a list
- strings are immutable
- also strings can be sliced like a list (see below)

use single or double quotes for strings
```
string1 = "help"
string2 = 'help'
```

get the length
```
length = len("abcdef")
```

f-strings: make a string with inserted values
```
print(f"Hello {name}")
```

string concatenation, need to explicitly convert numbers to strings
```
print("Hello " + name)
print("I am " + str(age) + " years old")
```

string split (default separator space) into a list of strings, join with hyphens
```
wordlist = "I like cookies".split()
hyphenated = "-".join(wordlist)
```

## composites

there are sequence functions mentioned later which apply to all of these, plus strings

### lists

square brackets makes a list:
```
stuff = ["red", "yellow", "green", "blue"]
```

- zero-indexed
- heterogenous (can have a mix of data types)
- allows negative index (-1 is last)

get and assign with common bracket notation
```
stuff[0] = 5
```

concatenate lists  
```
combined = stuff1 + stuff2
```

make a list that repeats 5 times
```
stuff = ["A","B","C"] * 5
```

slicing: get a part of the list  
from start until (not including) index 5
```
stuff[:5]
```  
from index 2 until the end  
```
stuff[2:]
```
from index 2 until (not including) last index
```
stuff[2:-1]
```
slicing with step value (in this case every second index)
```
stuff[1::2]
```

unpack a list as comma-separated arguments to a function (printing with a ', ' between them)
```
print(*stuff,sep=", ")
```

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

pop a dictionary value out of the dictionary, default value if it is not in the dictionary
```
val = scores.pop("Bob")
val = scores.pop("Bob", default=0)
```

delete a dictionary entry without doing anything with the value
```
del scores["Joe"]
```

clear the whole dictionary
```
scores.clear()
```

get a value, with a default returned value (instead of error) if it's not in the dictionary
```
scores.get("James",default=0)
```

`.keys()` for a list of keys  
`.values()` for a list of values
`.items()` for a list of (key, value) tuples  
```
for name, score in scores.items():
```

# synatax

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

to make a function with variable number of arguments, use splat operator (*)  
any arguments past the regular ones are packed in a tuple in the splatted parameter
```
def printextraarguments(num, name, *extras):
    for extra in extras:
        print(extra)
```

## loops

loop through i from 0 through 19  
```
for i in range(20):
    print(i)
```

for 1-20  
```
range(1,21)
```

for 4-20 by 2
```
range(4,21,2)
```

loop through a list of stuff
```
stuff = ["red", "yellow", "green", "blue"]
for i in range(len(stuff)):
    print(stuff[i])
```

foreach version (on lists, strings, tuples)
```
for thing in things:
    print(thing)
```

foreach on a dictionary
```
for key in dict:
    print(f"{key}: {dict[key]})
```

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

## classes

class definition (convention: first letter uppercase)  
methods always take self as first parameter
```
class User:
    # constructor
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def namechange(self, newname):
        self.name = newname
    
    def older(self):
        self.age += 1
```

create an instance of the class  
access attributes with dot notation (not brackets like dictionaries)  
method calls implicitly pass self
```
john = User("John", 42)
print(john.age)
john.older()
```

class attributes, class methods, static methods are all called from the class, not an instance (no self) 
class methods take **cls** as an implicit argument and thus can reference class attributes
static methods do not have an implicit argument
```
class User:
    population = 0 #class attribute

    # constructor
    def __init__(self, name, age):
        self.name = name
        self.age = age
        User.population += 1 #change the class attribute
    
    @classmethod
    def how_many(cls):
        print(f"{cls.population} users")
    
    @staticmethod
    def about():
        print("The User class represents a user")

users = [User("John",42), User("James",32), User("Jim", 27)]

print(User.population)
User.how_many()
User.about()
```

inheritance: Gigachad inherits from User  
overwrites older()
```
class Gigachad(User):
    #constructor
    def __init__(self):
        #call parent constructor
        super().__init__("Billy Badass", 23)
        #attribute the parent class doesn't have
        self.muscles = True
    #overwrite has no special syntax
    def older(self)
        print("Gigachads don't get older")
```

can make a function virtual by making the parent class version throw an error
```
    def taunt(self):
        raise NotImplementedError
```

## exceptions

*TODO*

# Common Functions

## input and output

print something
```
print("hi")
```
print multiple things (default separator = space)
```
print("hi", "bye")
```
print multiple things with a different separator
```
print("hi", "bye", sep=",")
```

to receive user input, always gives a string
```
input()
```
to first display a prompt so the user knows what to type
```
input("Enter age: ")
```

## sequence functions

these work on lists, tuples, strings, and maybe dictionaries?

get the number of elements in the sequence  
```
len(stuff)
```

get the biggest value in the sequence  
```
max(stuff)
```

get the minimum value in the sequence
```
min(stuff)
```

get a sorted copy of the sequence  
```
sorted(stuff)
```

## list-specific functions

add 5 to the end of the list
```
stuff.append(5)
```

remove the last element in the list and store it
```
last = stuff.pop()
```

remove first element and store it
```
another = stuff.pop(0)
```

reverse the order of the list
```
stuff.reverse()
```

get the index of a certain value in the list
```
print("index of Bob is", stuff.index("Bob"))
```

sort the list (numbers or strings?)
```
stuff.sort()
```

empty the list
```
stuff.clear()
```

# Modules

modules are just python libraries; they are python files with a bunch of functions  
modules are imported as *modulename*, runs the code in the file once  
you can make your own modules just by having functions in a separate *modulename*.py file  
the functions are called as *modulename.functionname* such as
```
import random
print(random.randint(1,10))
```

## packages

packages are folders with modules in them; to import a module in a package,
```
import packagename.modulename
```
OR
```
from packagename import modulename
```
