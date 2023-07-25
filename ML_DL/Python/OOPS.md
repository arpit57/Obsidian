## Basics

->Methtod vs Function:
A function defined inside a class is a method.

->'self' parameter of a method:
When instancing, the instance is automatically passed as a self parameter.
in our exanple, these are Item_1 and Item_2.
It's a convention to call this parameter as 'self', although a user can choose to define it as any other param

->Atrribute
An attribute in Python is a named value or object property, associated with an object.
It is accessed using dot (.) notation, for example "object.attribute".

->Arguments vs parameters:
An argument is a value passed to a function when the function is called. 
A parameter is a variable in the function definition that receives the argument. 
Simply put, arguments are the values passed to a function, and parameters are the variables in the function that receive those values.

```python
class Item:
    def totalPrice(self, x, y):
        return x * y

Item_1 = Item() #Creating instance of a class
Item_1.name = "Mobile phone" #Assigning attribute to an instance of a class
Item_1.price = 20000
Item_1.quantity = 5
print(type(Item_1))
print(type(Item_1.name))

Item_2 = Item()
Item_2.name = "Laptop"
Item_2.price = 60000
Item_2.quantity = 2

print(Item_1.totalPrice(Item_1.price, Item_1.quantity))
print(Item_2.totalPrice(Item_2.price, Item_2.quantity))

```

## Constructor and more

->constructor:
__ init __ is one of the magic methods availbale in python
whenever an instance is created, this method is called

->Assertion:
assertion is a statement that checks if the given condition is true, 
and raises an error (AssertionError) if the condition is false.

```python
class Item:
    payRate = 0.9 # A class attribute
    all = [] #a list to store created instances
    def __init__(self, name: str, price: float, quantity=1): # setting default quantity as '1'
        print(f"Constructor call on instance creation with name {name}")
        
        assert price >=0, f'Price must not be -ve'
        assert quantity >=0, f'quantity must not be -ve'
        
        # defining 3 instance attribute
        self.name = name 
        self.price = price
        self.quantity = quantity
        
        Item.all.append(self)
    def totalPrice(self):
        return self.price * self.quantity
    
    def applyDiscount(self):
        return self.price * self.payRate
    
item_1 = Item("Phone", 20000, 2)
item_2 = Item("laptop", 60000) # not passing quantity, hence the default value '1' will be assigned
item_3 = Item("Smart watch", 10000, 3)

item_2.hasNumpad = True #we can still declare an attribute outside the constructor

print(Item.totalPrice(item_1))
print(item_2.totalPrice()) # Another way of calling a class method
print(item_3.totalPrice())
print(f"laptop has numpad {item_2.hasNumpad}\n")

print(Item.__dict__) #All class level attributes
print(Item.payRate)
print(item_1.__dict__)#All instance level attributes
print(item_1.payRate, "\n")  # accessing a class attribute using instance even though it's not at same level
item_2.payRate = 0.5
print(item_1.applyDiscount()) #for a default 10% discount
print(item_2.applyDiscount(), "\n") #for a 50% discount

for x in Item.all:
    print(x.name) #printing name of each instance

```

## Inheritence

let's consider a simple example. Suppose we have a generic `Animal` class and we want to create a specific `Dog` class. In Python, we could use inheritance to create the `Dog` class from the `Animal` class.

Here's how we might do that:

```python
class Animal:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def speak(self):
        return "I don't know what sound I make!"

class Dog(Animal):  # Dog inherits from Animal
    def __init__(self, name, color, breed):
        super().__init__(name, color)  # Call the initializer of the parent class (Animal)
        self.breed = breed

    def speak(self):  # Override the speak method for a dog
        return "Woof!"

# Now let's create some instances
generic_animal = Animal("Generic animal", "Grey")
print(generic_animal.speak())  # prints: I don't know what sound I make!

my_dog = Dog("Fido", "Brown", "Labrador")
print(my_dog.speak())  # prints: Woof!
```

In this example, `Dog` is a subclass of `Animal`. By calling `super().__init__(name, color)`, we're using the constructor of `Animal` to set the `name` and `color` properties, and then setting an additional property, `breed`, that is specific to `Dog`.

We also override the `speak` method in the `Dog` class. So, when we call `speak` on an instance of `Dog`, it prints "Woof!" instead of "I don't know what sound I make!".

## Polymorphism

polymorphism in Python enables us to use a single type entity (method, operator, or object) to represent different types in different scenarios. Here's an example:

```python
class Animal:
    def __init__(self, name):    
        self.name = name

    def speak(self):
        raise NotImplementedError("Subclass needs to implement this method")

class Dog(Animal):
    def speak(self):
        return 'Woof!'

class Cat(Animal):
    def speak(self):
        return 'Meow!'

animals = [Cat('Missy'),
           Cat('Mr. Mistoffelees'),
           Dog('Lassie')]

for animal in animals:
    print(animal.name + ': ' + animal.speak())
```

## Encapsulation

Encapsulation in object-oriented programming is the concept of bundling the data (attributes) and the methods that manipulate this data into a single unit, known as a 'class'. This concept allows the data to be hidden from outside methods and manipulations.

The idea is to make the attributes inaccessible directly and instead provide methods (getters and setters) through which they can be manipulated in a controlled manner. The key benefit of encapsulation is that it allows for data hiding, and protects the data from being modified accidentally.

Here's an example of encapsulation in Python:

```python
class Car:
    def __init__(self, max_speed, mileage):
        self._max_speed = max_speed  # Protected member
        self.__mileage = mileage  # Private member

    # Getter method
    def get_max_speed(self):
        return self._max_speed

    # Setter method
    def set_max_speed(self, speed):
        self._max_speed = speed

    # Getter for mileage
    def get_mileage(self):
        return self.__mileage

    # Setter for mileage
    def set_mileage(self, mileage):
        self.__mileage = mileage

# Creating object
my_car = Car(200, 15)

# Accessing using class methods
print(my_car.get_max_speed())  # Outputs: 200
print(my_car.get_mileage())  # Outputs: 15

# Changing values using class methods
my_car.set_max_speed(220)
my_car.set_mileage(16)
print(my_car.get_max_speed())  # Outputs: 220
print(my_car.get_mileage())  # Outputs: 16
```

In this example, the `_max_speed` and `__mileage` attributes are not accessible directly, and instead we provide `get_max_speed`, `set_max_speed`, `get_mileage`, `set_mileage` methods to access and modify them. This way, we can control what values are allowed, or trigger certain actions whenever the values are accessed or changed, if we wanted to.

Please note, unlike some other languages like Java, Python doesn't provide strict ways to hide attributes completely. The `__mileage` attribute is a private member and conventionally it's not accessed directly, but Python still provides a way to access it if necessary. This is often summarized as "we're all consenting adults here" in the Python community. However, the convention encourages the use of getter and setter methods for accessing such attributes.

## Abstarction

in object-oriented programming, abstraction is a process of hiding the real implementation of an application from the user and providing functionality to the user in an easy-to-understand manner.

Here is an example of using abstract classes in Python.

``` python
from abc import ABC, abstractmethod

class AbstractAnimal(ABC):
    @abstractmethod
    def make_sound(self):
        pass

class Dog(AbstractAnimal):
    def make_sound(self):
        return "Woof!"

class Cat(AbstractAnimal):
    def make_sound(self):
        return "Meow!"

# Create instances of the concrete classes
dog = Dog()
cat = Cat()

# Use the instances
print(dog.make_sound())  # Outputs: "Woof!"
print(cat.make_sound())  # Outputs: "Meow!"
```

In the above example, `AbstractAnimal` is an abstract class that declares an abstract method `make_sound`. This method is later defined in each of the concrete classes `Dog` and `Cat` that inherit from `AbstractAnimal`.

You can't create an instance of an abstract class. Trying to create an instance of `AbstractAnimal` would lead to an error. But you can use it as a base class and create instances of `Dog` and `Cat`.

The abstract `make_sound` method provides a way to ensure that each concrete class that inherits from `AbstractAnimal` will have a `make_sound` method, but the implementation of the method is left up to each concrete class. This is a form of abstraction: the user doesn't need to know how the `make_sound` method is implemented in each concrete class, they just need to know that they can call `make_sound` on any `AbstractAnimal` instance.