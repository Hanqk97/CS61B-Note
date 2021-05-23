# Static vs. Non-Static Methods

## Static Methods

A class that uses another class is sometimes called a "client" of that class. Neither of the two techniques is better: Adding a main method to `Dog` may be better in some situations, and creating a client class like `DogLauncher` may be better in others.

## Instance Variables and Object Instantiation

```java
public class Dog {
    public int weightInPounds;

    public void makeNoise() {
        if (weightInPounds < 10) {
            System.out.println("yipyipyip!");
        } else if (weightInPounds < 30) {
            System.out.println("bark. bark.");
        } else {
            System.out.println("woof!");
        }
    }    
}
```
- An `Object` in Java is an instance of any class.
- The `Dog` class has its own variables, also known as *instance variables* or *non-static variables*. These must be declared inside the class, unlike languages like Python, where new variables can be added at runtime.
- The method that we created in the `Dog` class did not have the `static` keyword. We call such methods *instance methods* or *non-static methods*.
- To call the `makeNoise` method, we had to first *instantiate* a `Dog` using the `new` keyword, and then make a specific `Dog` bark. In other words, we called `d.makeNoise()` instead of `Dog.makeNoise()`.
- Once an object has been instantiated, it can be *assigned* to a *declared* variable of the appropriate type, e.g. `d = new Dog();`
- Variables and methods of a class are also called *members* of a class.
- Members of a class are accessed using *dot notation*.

## Constructors in Java

```java
public class DogLauncher {
    public static void main(String[] args) {
        Dog d = new Dog(20);
        d.makeNoise();
    }
}
```
-  the instantiation is parameterized, saving us the time and messiness of manually typing out potentially many instance variable assignments. To enable such syntax, we need only add a "constructor" to our Dog class, as shown below:
```java
public class Dog {
    public int weightInPounds;

    public Dog(int w) {
        weightInPounds = w;
    }

    public void makeNoise() {
        if (weightInPounds < 10) {
            System.out.println("yipyipyip!");
        } else if (weightInPounds < 30) {
            System.out.println("bark. bark.");
        } else {
            System.out.println("woof!");
        }    
    }
}
```

The constructor with signature `public Dog(int w)` will be invoked anytime that we try to create a `Dog` using the `new` keyword and a single integer parameter. 

## Terminology Summary

```java
public class Dog {
public int weightInPounds;//Instance variable. Can have as many of these as you want.

public Dog(int startingWeight) {//Constructor (similar to a method, but not a method). Determines how to 	instantiate the class.
weightInPounds = startingWeight;
}

/**
Non-static method, a.k.a. Instance Method. Idea: If the method is going to be invoked by an instance of the class (as in the next slide), then it should be non-static.

Roughly speaking: If the method needs to use “my instance variables”, the method must be non-static.
*/
public void makeNoise() {
if (weightInPounds < 10) {
System.out.println("yipyipyip!");
   		} else if (weightInPounds < 30) {
      	System.out.println("bark. bark.");
   	} else {
      	System.out.println("woof!");
   	}
   }
}
```

## **Instantiating a Class and Terminology**

```java
public class DogLauncher {
	public static void main(String[] args) {
		Dog smallDog;//Declaration of a Dog variable.
		new Dog(20);//Instantiation of the Dog class as a Dog Object.
   		smallDog = new Dog(5);//Instantiation and Assignment.
   		Dog hugeDog = new Dog(150);//Declaration, Instantiation and Assignment.
   		smallDog.makeNoise();
   		hugeDog.makeNoise();//Invocation of the 150 lb Dog’s makeNoise method.
        					//The dot notation means that we want to use a method or variable belonging to 								  hugeDog, or more succinctly, a member of hugeDog.	
	}
}
```

## **Arrays of Objects**

To create an array of objects:

- First use the new keyword to create the array.
- Then use new again for each object that you want to put in the array.

```java
Dog[] dogs = new Dog[2];//Creates an array of Dogs of size 2.
dogs[0] = new Dog(8);
dogs[1] = new Dog(20);
dogs[0].makeNoise();
```

# Class Methods vs. Instance Methods

Java allows us to define two types of methods:

- Class methods, example: static methods.
- Instance methods, example:non-static methods.

Instance methods are actions that can be taken only by a specific instance of a class. Static methods are actions that are taken by the class itself. Both are useful in different circumstances. As an example of a static method, the `Math` class provides a `sqrt` method. Because it is static, we can call it as follows:

```java
x = Math.sqrt(100);
```

If `sqrt` had been an instance method, we would have instead the awkward syntax below. Luckily `sqrt` is a static method so we don't have to do this in real programs.

```java
Math m = new Math();
x = m.sqrt(100);
```

## Static Variables

Static variables should be accessed using the name of the class rather than a specific instance, e.g. you should use `Dog.binomen`, not `d.binomen`.

## public static void main(String[] args)

With what we've learned so far, it's time to demystify the declaration we've been using for the main method. Breaking it into pieces, we have:

- `public`: So far, all of our methods start with this keyword.
- `static`: It is a static method, not associated with any particular instance.
- `void`: It has no return type.
- `main`: This is the name of the method.
- `String[] args`: This is a parameter that is passed to the main method.

## Command Line Arguments

Since main is called by the Java interpreter itself rather than another Java class, it is the interpreter's job to supply these arguments. They refer usually to the command line arguments. For example, consider the program `ArgsDemo` below:

```java
public class ArgsDemo {
    public static void main(String[] args) {
        System.out.println(args[0]);
    }
}
```

This program prints out the 0th command line argument, e.g.

```
$ java ArgsDemo these are command line arguments
these
```

In the example above, `args` will be an array of Strings, where the entries are {"these", "are", "command", "line", "arguments"}.

# Using Libraries

# Overview

**Client Programs and Main Methods.** A Java program without a main method cannot be run using the `java` command. However, methods from one class can be invoked using the `main` method of another class. A java class that uses another class is called a client of that class.

**Class Declaration.** Java classes can contain methods and/or variables. We say that such methods and variables are “members” of the calss. Members can be *instance* members or *static* members. Static members are declared with the `static` keyword. Instance members are any members without the `static` keyword.

**Class Instantiation.** Instantiating a class is almost always done using the new keyword, e.g. `Dog d = new Dog()`. An instance of a class in Java is also called an `Object`.

**Dot Notation.** We access members of a class using dot notation, e.g. `d.bark()`. Class members can be accessed from within the same class or from other classes.

**Constructors.** Constructors tell Java what to do when a program tries to create an instance of a class, e.g. what it should do when it executes `Dog d = new Dog()`.

**Array Instantiation.** Arrays are also instantiated using the `new` keyword. If we have an array of Objects, e.g. `Dog[] dogarray`, then each element of the array must also be instantiated separately.

**Static vs. Instance methods.** The distinction between static and instance methods is incredibly important. Instance methods are actions that can only be taken by an instance of the class (i.e. a specific object), whereas static methods are taken by the class itself. An instance method is invoked using a reference to a specific instance, e.g. `d.bark()`, whereas static methods should be invoked using the class name, e.g. `Math.sqrt()`. Know when to use each.

**Static variables.** Variables can also be static. Static variables should be accessed using the class name, e.g. `Dog.binomen` as opposed to `d.binomen`. Technically Java allows you to access using a specific instance, but we strongly encourage you not to do this to avoid confusion.

**void methods.** A method which does not return anything should be given a void return type.

**The `this` keyword.** Inside a method, we can use the `this` keyword to refer to the current instance.

**public static void main(String[] args).** We now know what each of these things means:

- public: So far, all of our methods start with this keyword.
- static: It is a static method, not associated with any particular instance.
- void: It has no return type.
- main: This is the name of the method.
- String[] args: This is a parameter that is passed to the main method.

**Command Line Arguments.** Arguments can be provided by the operating system to your program as “command line arguments,” and can be accessed using the `args` parameter in `main`. For example if we call our program from the command line like this `java ArgsDemo these are command line arguments`, then the `main` method of `ArgsDemo` will have an array containing the Strings “these”, “are”, “command”, “line”, and “arguments”.

**Using Libraries.** There’s no need in the year 2017 to build everything yourself from scratch. In our course, you are allowed to and highly encouraged to use Java’s built-in libraries, as well as libraries that we provide, e.g. the Princeton standard library.
