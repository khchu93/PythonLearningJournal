# PythonLearningJournal
Personal repository to track what I’ve learned about Python from exercises, work, and experiments.

### Knowledge map
- Class <br>
- - Instance/Object <br>
  - Dunder/magic method
  - Member of a class/object <br>
  - - Methods <br>
    - Attributes

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
class Circle:                          #class name should start with an uppercase
  def __init__(self, radius):          #object initializer, radius = parameter/argument
    self.radius = radius               #instance variable (attribute)
  def calculate_area(self):            #method name should start with lowercase and contains a verb (except for dunder method)
    area = math.pi * self.radius ** 2  #class variable
    return area
```        

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
Definition: different behaviors that objects will show

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
``
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
