Factory method is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.

![[factory-method-en.png]]
Imagine that you're creating a logistics management application. The first version of your app can only handle transportation by trucks, so the buck of your code lives inside the `Truck` class.

After a while, your app becomes pretty popular. Each day you receive dozens of requests from sea transportation companies to incorporate sea logistics into your page.

![[problem1-en.png]]

Great news, right? But how about the code? At present, most of your code is coupled to the `Truck` class. Adding `Ships` into your app would require making changes to the entire codebase. Moreover, if later you decide to add another type of transportation to the app, you will probably need to make all of these changes again.

As a result, you will end up with pretty nasty code, riddled with conditionals that switch the app's behaviour depending on the class of transportation objects.

The Factory Method pattern suggests that you replace direct object construction calls (using the new operator) with calls to a special *factory* method. Objects returned by a factory method are often referred to as *products*.

![[solution1.png]]

At first glance, this change may look pointless: we just moved the constructor call from one part of the program to another. However, consider this: now you can override the factory method in a subclass and change the class of products being created by the method.

There's a slight limitation though: subclasses may return different types of products only if these products have a common base class or interface. Also, the factory method in the base class should have its return type declared as this interface.

![[solution2-en.png]]

For example, both `Truck` and `Ship` classes should implement the `Transport` interface, which declares a method called `deliver`. Each class implements this method differently: trucks deliver cargo by land, ships deliver cargo by sea. The factory method in the `RoadLogistics` class returns truck objects, where as the factory method in the `SeaLogistics` returns ships.

![[solution3-en.png]]

The code that uses the factory method (often called the *client code*) doesn't see a difference between the actual products returned by various subclasses. The client treats all the products as abstract `Transport`. The client knows that all transport objects are supposed to have the `deliver` method, but exactly how it works isn't important to the client.

### Structure:
![[structure.png]]

1. The **Product** declares the interface, which is common to all objects that can be produced by the creator and its subclasses.
2. **Concrete Products** are different implementations of the product interface.
3. The **Creator** class declares the factory method that returns new product objects. It's important that the return type of this method matches the product interface. You can declare the factory method as `abstract` to force all subclasses to implement their own versions of the method. As an alternative, the base factory method can return some default product type.
4. **Concrete Creators** override the base factory method so it returns a different type of product.

