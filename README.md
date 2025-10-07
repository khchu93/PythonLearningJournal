# PythonLearningJournal
Personal repository to track what I’ve learned about Python from exercises, work, and experiments.

### Knowledge map
- Class <br>
- - Instance/Object <br>
  - Dunder/magic method
  - - \_\_init\_\_
  - Member of a class/object <br>
  - - Methods/Functions <br>
    - - Instance methods
      - Class methods
      - - Data class
      - Static methods
    - Attributes
    - - Class attributes
      - Instance attributes
      - Local variables

- OOP
- - Encapsulation
  - - Public
    - Protected
    - Private


### What is:

**!** (ex. !pip install python) <br>
Definition: Run this command in the underlying shell (bash) instead of Python. <br>
Use case: <br>
```
!pip, !scp, etc
```
if **not** [variable]: <br>
Definition: This code checks for falsy values (e.g., boolean False, int 0, empty ([], '', ""), special constant None)

[element] = [list].**pop([int])** <br>
Definition: pop the int variable of the list (e.g., 0 = first, -1 = last)

**id**([variable]) <br>
Definition: return the id of the variable. It can be used to check if you're working on a reference of the same variable or a new variable.

**Class** <br>
Definition: a blueprint that specifies the data and behavior of an object/instance that it can instantiate from
Use case: <br>
```
class Circle:                          #class, name should start with an uppercase
  num_instances = 0                    #class attributes (/variable)
  def __init__(self, radius):          #object initializer, radius = parameter/argument
    type(self).num_instances += 1      #type(self) is used to modify it without creating a new instance attribute, friendly to subclasses
    self.radius = radius               #instance attribute (/variable)
  def calculate_area(self):            #method, name should start with lowercase and contains a verb (except for dunder method)
    area = math.pi * self.radius ** 2  #local variable
    return area
```        

**Class attributes**(/variables)<br>
Definition: a variable that you define in the class body directly, belongs to its containing class, all instances initially reference the same value/object in memory, **changing the class attribute via the class propagates to all instances that haven’t overridden it** (for those that have overridden it, it will remain to the overridden value)

**Instance attributes**(/variables)<br>
Definition: a variable that you define inside an **instance method** using the self argument, its data is only available to that instance and defines its state

**Local variable**<br>
Definition: a temporal variable exists only while the method is running

**Object/Instance** <br>
Definition: an actual thing built from that blueprint, with its own specific data, created when you instantiate it
Use case: <br>
```
circle_1 = Circle(42)
```

**Members of a class/object** <br>
Definition: Attributes + Methods

**Attributes/Instance variables** <br>
Definition: variables defined inside a class to store all the required data for the class to work
Use case: <br>
```
circle_1.radius
```

**Class variables** <br>
Definition: variables defined directly in the class body (outside of methods). They belong to the class itself and are shared across all instances.
Use case: <br>
```
area
```

**Methods** <br>
Definition: different behaviors that objects will show, inside a class
Use case: <br>
```
class Circle:
  def calculate_area(self):
```

**Functions** <br>
Definition: same as method, but outside a class
Use case: <br>
```
def calculate_area(self):
```

**Instance Methods** <br>
Definition: methods that use **self** to access **instance attributes** and **class attributes** (to store or modify), needs data from a specific object/instance
Use case: <br>
```
class Example:
    def instance_method(self):
        return f"I'm tied to the instance: {self}"

obj = Example()
print(obj.instance_method())
```

**Class Methods** <br>
Definition: methods that use **cls** to access **class attributes**, works with the class itself
Use case: <br>
```
class Example:
    count = 0

    def __init__(self):
        Example.count += 1

    @classmethod                                      # identify the following method as class method
    def how_many(cls):                                # cls refers to Example (class name) itself
        return f"There are {cls.count} instances."    # class attribute can still be accessed by calling the class name directly: Example.count

a = Example()
b = Example()
print(Example.how_many())  # "There are 2 instances."
```

**Data class** (TBD)<br> 
Definition:
Use case: <br>

**Module** (TBD)<br> 
Definition:
Use case: <br>

**Package** (TBD)<br> 
Definition:
Use case: <br>

**Static Methods** <br>
Definition: behaves just like a normal function, but is grouped inside the class, doesn't have access to instance attributes (can still access class attributes with the class name directly), a helper function bundled with the class
Use case: <br>
```
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

print(MathUtils.add(3, 5))  # 8
```

**__init__** <br>
Definition: a **dunder method** that is also known as the **object initializer** that defines and sets the initial values for the object's attributes

**Public** attributes
Definition: refers to members that can be used inside and outside their defining class, uses the normal naming pattern
Use case: <br>
```
circle_1.calculate_area()
```

**Protected** attributes
Definition: members that shouldn't be used outside their defining class (but they're still accessible), create a public method to access those non-public instance variables or methods, include a leading underscore in names
Use case: <br>
```
self._radius, _calculate_area()
```

**Private** attributes
Definition: same as protected, but with two leading underscores in names, more difficult to access (**Name Mangling**)
Use case: <br>
```
self.__radius      #circle_1._Circle__radius, instead of circle_1.__radius to access the instance variable
```

**Name Mangling**
```
class Dog:
    def __init__(self, name):
        self.__secret = "likes bacon"   # private

dog = Dog("Buddy")
print(dog.__secret)         # ❌ AttributeError
print(dog._Dog__secret)     # ✅ works, but hacky
```

**map(function, iterable)**
Definition: applies a function to every item in an iterable (like a list, tuple, or string)
Use case: <br>
```
numbers = ["1", "2", "3", "4"]
result = map(int, numbers)
print(list(result))  # [1, 2, 3, 4]
```

**type(variable)**
Definition: return the type of variable

**with** function **as** variable
Definition: use to manage resources safely and automatically, to open and close the objects automatically, it works with any objects that have __enter__() and __exit__()
Use case:<br>
```
with open("file.txt", "r") as f:
  data = f.read()
```
This replaces the following:
```
f = open("file.txt", "r")     # calls __enter__()
try:
    data = f.read()
finally:
    f.close()                 # calls __exit__() automatically
```
