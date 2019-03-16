# Object and classes
Let us look at the syntax of how we do OOP in python

## Creating a class
First and foremost, pythons syntax is very clean, there is little boilerplate code needed since there are behind the scenes sensible default values.

```python
class MyFirstClass:
    pass
```
This is just a short example of a class without any attributes or behaviours. Notice the class name, it has capitalized the first letter of each word, standard variable name rules apply, only letters, underscore or numbers are allowed. 

```python
>>> a = MyFirstClass()
>>> b = MyFirstClass()
>>> print(a)
<__main__.MyFirstClass object at 0x10764eda0>
>>> print(b)
<__main__.MyFirstClass object at 0x10764fb0>
>>>
```
This code instantiates two objects, `a` and `b`, this is done by typing the name of the class followed by a pair of parentheses. It looks like how you call a function but python knows that in this case it should create an instance of an object. This is one of the many ways python helps you along the way. When printed it shows you the memory location of the object, this is something that is seldom used in python, but here it just shows that the two objects are distinct from each other.

## Adding attributes and behaviours
With our basic class (that does nothing), lets change that and make some attributes.

eivl:
> Python is a language for consenting adults

By this we mean that you can change and add code everywhere or anywhere, we just have to all agree that this is the case.

Lets add some attributes to a `Point` class without coding it into the object.
```python
class Point:
    pass

p1 = Point()
p2 = Point()

p1.x = 23
p1.y = 13

p2.x = 3
p2.y = 9

print(p1.x, p1.y)
print(p2.x, p2.y)
```
Here we add the x and y attributes to the object instance after it is created and instantiated.
```python
>>> 23 13
>>> 3 9
```

You might ask, how do you get the object to do something?
Great question, since the point of OOP is to make objects with interaction between objects. How do we make actions that changes attributes? 
We start by modelling some actions on our `Point` class, we will make a *method* (it's like a function but it has a link to the object, or it has a link to `itself`) called `reset`. Like functions you define it with the `def` keyword.

```python
class Point:
    def reset(self):
        self.x = 0
        self.y = 0

p = Point()
p.reset()
print(p.x, p.y)
```
```python
0 0
```
Notice the use of the word `self`, it is nothing special with the name, it could be anything, but it is a already agreed upon convention to call it `self`. Next is that the `method` is called with the dot-notation `.` between the object instance and the method name, and lastly to call/run the method you use a pair of parentheses(just like functions do).

## What about self?
Syntactically there is only one difference between a method and a function, methods have one required argument. This argument is conventionally named `self`, there is nothing magical about the name, you can call it `this` or `eivl`.
The `self` argument to a method is a reference to the object that the method is being invoked on. We can access attributes and methods of that object as if it were any other object. This is what is done above in the `reset` method, there x and y attributes are set of the `self` object.

Notice above, in usage of `p.reset()` we do not have to pass the `self` argument, this is done automatically by python. It already know you are calling a method on the object `p`.
Since a method is just like a function, we do not have to use the method on the object, we can invoke the function on the class, explicitly passing our object as the `self` argument.

```python
p = Ponit()
Point.reset(p)
print(p.x, p.y)
```

Internally this is the same process as using a method on the object