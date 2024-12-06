**OOP's in Python by javaTpoint**
https://www.javatpoint.com/python-oops-concepts


**OOP's interview questions**
https://www.javatpoint.com/oops-interview-


**OOP's in java**
https://www.geeksforgeeks.org/object-oriented-programming-oops-concept-in-java/


OOP's in Python
https://www.geeksforgeeks.org/python-oops-concepts/?ref=shm

**OOP's Github repo for revision**
https://github.com/vineethm1627/OOP

---
### Why Object-Oriented Programming (OOP)?

1. **Organization:** OOP helps to organize code by breaking it into smaller, manageable pieces called objects.
2. **Reuse:** You can reuse code easily, which saves time and effort.
3. **Maintenance:** It makes code easier to update and maintain.
4. **Data Protection:** OOP keeps data safe by bundling it with methods that work on the data.
5. **Simplicity:** It hides complex details and shows only what’s necessary.
6. **Flexibility:** You can use one method to work with different objects.

### Importance of Class and Object

- **Class:** A blueprint for creating objects. It defines what attributes and methods the objects will have.
- **Object:** An instance of a class. It represents a real thing with specific details.

### Sample Code in Python

```python
# Defining a class
class Car:
    # Class attribute
    type = "Vehicle"

    # Constructor method to initialize attributes
    def __init__(self, brand, model, year):
        # Instance attributes
        self.brand = brand
        self.model = model
        self.year = year

    # Method to display car details
    def show_details(self):
        print(f"Car: {self.brand} {self.model}, Year: {self.year}")

    # Method to start the car
    def start_engine(self):
        print(f"{self.brand} {self.model}'s engine is now running.")

# Creating objects (instances) of the Car class
car1 = Car("Toyota", "Corolla", 2020)
car2 = Car("Honda", "Civic", 2018)

# Accessing class attributes and methods
print(f"Type of car1: {car1.type}")
print(f"Type of car2: {car2.type}")

car1.show_details()
car2.show_details()

car1.start_engine()
car2.start_engine()
```

### Explanation

- **Class Definition:** The `Car` class is like a blueprint. It defines what a car object will have: brand, model, year, and some methods.
- **Constructor:** The `__init__` method sets up (initializes) the object's details.
- **Creating Objects:** `car1` and `car2` are two cars created using the `Car` class blueprint.
- **Using Methods:** The methods `show_details` and `start_engine` are called on the car objects to show details and start the engine.

OOP helps you create organized, reusable, and easy-to-maintain code by using classes and objects.


## OOP Cheatsheet

### 1. Basic Concepts

- **Class**: A blueprint for creating objects.
  ```python
  class ClassName:
      # class body
      pass
  ```

- **Object**: An instance of a class.
  ```python
  obj = ClassName()
  ```

- **Attributes**: Variables that belong to a class or an instance of a class.
  ```python
  class Dog:
      def __init__(self, name, age):
          self.name = name  # instance attribute
          self.age = age
  ```

- **Methods**: Functions that belong to a class.
  ```python
  class Dog:
      def __init__(self, name, age):
          self.name = name
          self.age = age
      
      def bark(self):
          print(f"{self.name} says woof!")
  ```

### 2. Four Pillars of OOP

#### 1. Encapsulation

- Bundling the data (attributes) and methods that operate on the data into a single unit, a class, and restricting access to some of the object's components.
  ```python
  class Dog:
      def __init__(self, name, age):
          self._name = name  # protected attribute
          self.__age = age   # private attribute
      
      def get_age(self):
          return self.__age
  ```

#### 2. Abstraction

- Hiding the complex implementation details and showing only the necessary features.
  ```python
  from abc import ABC, abstractmethod

  class Animal(ABC):
      @abstractmethod
      def make_sound(self):
          pass

  class Dog(Animal):
      def make_sound(self):
          print("Woof")
  ```

#### 3. Inheritance

- Mechanism of basing a class (child class) on another class (parent class), retaining similar implementation.
  ```python
  class Animal:
      def __init__(self, name):
          self.name = name
      
      def make_sound(self):
          pass

  class Dog(Animal):
      def make_sound(self):
          print("Woof")
  ```

#### 4. Polymorphism

- Ability to present the same interface for different underlying data types.
  ```python
  class Cat(Animal):
      def make_sound(self):
          print("Meow")
      
  animals = [Dog("Fido"), Cat("Whiskers")]

  for animal in animals:
      animal.make_sound()
  ```

### 3. Advanced Concepts

#### 1. Class vs. Instance Variables

- **Class Variable**: Shared across all instances.
- **Instance Variable**: Unique to each instance.
  ```python
  class Dog:
      species = 'Canine'  # class variable

      def __init__(self, name, age):
          self.name = name  # instance variable
          self.age = age
  ```

#### 2. Class Methods and Static Methods

- **Class Method**: A method bound to the class and not the object of the class.
  ```python
  class Dog:
      species = 'Canine'

      @classmethod
      def get_species(cls):
          return cls.species
  ```

- **Static Method**: A method that does not operate on an instance or the class.
  ```python
  class Math:
      @staticmethod
      def add(x, y):
          return x + y
  ```

#### 3. Method Overriding

- Providing a specific implementation in a subclass for a method already defined in its superclass.
  ```python
  class Animal:
      def make_sound(self):
          print("Some generic sound")

  class Dog(Animal):
      def make_sound(self):
          print("Woof")
  ```

#### 4. Multiple Inheritance

- Inheriting from more than one class.
  ```python
  class Parent1:
      pass

  class Parent2:
      pass

  class Child(Parent1, Parent2):
      pass
  ```

#### 5. The `super()` Function

- Calling the superclass method.
  ```python
  class Animal:
      def __init__(self, name):
          self.name = name

  class Dog(Animal):
      def __init__(self, name, age):
          super().__init__(name)
          self.age = age
  ```

### 4. Access Modifiers

- **Public**: Accessible from anywhere.
  ```python
  class MyClass:
      def __init__(self):
          self.my_attribute = "I'm public"
  ```

- **Protected**: Prefix with a single underscore (_). Should not be accessed directly, but still possible.
  ```python
  class MyClass:
      def __init__(self):
          self._my_attribute = "I'm protected"
  ```

- **Private**: Prefix with double underscore (__). Not accessible directly.
  ```python
  class MyClass:
      def __init__(self):
          self.__my_attribute = "I'm private"
  ```

### 5. Special Methods

- **`__init__`**: Constructor method, called when an object is instantiated.
  ```python
  class MyClass:
      def __init__(self, value):
          self.value = value
  ```

- **`__str__`**: Method to define the string representation of an object.
  ```python
  class MyClass:
      def __init__(self, value):
          self.value = value

      def __str__(self):
          return f"MyClass with value {self.value}"
  ```

### 6. Example Code

```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def make_sound(self):
        raise NotImplementedError("Subclass must implement abstract method")

class Dog(Animal):
    def __init__(self, name, age):
        super().__init__(name)
        self.age = age
    
    def make_sound(self):
        return "Woof"

class Cat(Animal):
    def make_sound(self):
        return "Meow"

dog = Dog("Fido", 3)
cat = Cat("Whiskers")

print(dog.make_sound())  # Output: Woof
print(cat.make_sound())  # Output: Meow
```

This expanded cheatsheet provides a comprehensive overview of OOP concepts with Python code examples, including encapsulation, abstraction, inheritance, and polymorphism, as well as advanced concepts like class and instance variables, class methods, static methods, and access modifiers. Use it as a quick reference to understand and implement OOP principles in your projects.