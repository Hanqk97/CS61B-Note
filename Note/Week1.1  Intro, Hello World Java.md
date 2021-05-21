# Slide
## **Course Structure**

Phase 1: Programming Intensive Introduction to Java. 

- Weeks 1-4.
- One browser-based programming HW (this HW0 is optional).
- Three labs to introduce you to various tools (starting this week).
- Two projects (proj0 and proj1).

Phase 2: Advanced Programming

- Weeks 5-7. 
- One small HW (HW1).
- One large project, due ~3/5. New: You design your own explorable world (within some constraints).
- Labs to support large project.

Phase 3: Data Structures and Algorithms

- Weeks 8-14
- Incredibly important and foundational material: Expect an CS job interview to lean heavily on this part of the course.
- Labs: Implement a data structure or algorithm. Each lab ends with a TA led discussion of best implementation.
- Six HWs: Apply a data structure or algorithm toward a real world problem. Two released during RRR week. Can be used to makeup missed homeworks earlier, or for practice.
- One very challenging data structure/algorithms project (but not as big as project 2).

## **Java and Object Orientation** 

Java is an object oriented language with strict requirements:

1. Every Java file must contain a class declaration*.*
2. ***All code** lives inside a class*, even helper functions, global constants, etc.
3. To run a Java program, you typically define a main method using`public static void main(String[] args)`

## **Reflections on Static Typing**

The Good:

1. Debugging is a lot easier, type errors are avoided.
2. Produciton code has no type errors, so that means people’s phones won’t crash because of type errors.
3. Programs run more efficiently in time and memory.
4. Self-documenting: YOU KNOW WHAT YOU’VE GOT.

The Bad:

1. Code is more verbose.
2. Code is less general.

# Reading

## Compiler

The most common way to execute a Java program is to run it through a sequence of two programs. The first is the Java compiler, or `javac`. The second is the Java interpreter, or `java`.

![compilationflow](https://joshhug.gitbooks.io/hug61b/content/assets/compilation_figure.svg)

For example, to run `HelloWorld.java`, we'd type the command `javac HelloWorld.java` into the terminal, followed by the command `java HelloWorld`. The result would look something like this:

```bash
$ javac HelloWorld.java
$ java HelloWorld
Hello World! 
$ cat HelloWorld.java/class 显示文件内部代码
```

##  Static Typing

One of the most important features of Java is that all variables and expressions have a so-called `static type`. Java variables can contain values of that type, and only that type. Furthermore, the type of a variable can never change.

`static typing` has the following advantages:

- The compiler ensures that all types are compatible, making it easier for the programmer to debug their code.
- Since the code is guaranteed to be free of type errors, users of your compiled programs will never run into type errors. For example, Android Applications are written in Java, and are typically distributed only as .class files, i.e. in a compiled format. As a result, such applications should never crash due to a type error since they have already been checked by the compiler.
- Every variable, parameter, and function has a declared type, making it easier for a programmer to understand and reason about code.

## Defining Functions in Java

 All Java code is part of a class, we must define functions so that they belong to some class. Functions that are part of a class are commonly called "methods".

## Code Style, Comments, Java doc

Some of the most important features of good coding style are:

- Consistent style (spacing, variable naming, brace style, etc)
- Size (lines that are not too wide, source files that are not too long)
- Descriptive naming (variables, functions, classes), e.g. variables or functions with names like `year` or `getUserName` instead of `x` or `f`.
- Avoidance of repetitive code: You should almost never have two significant blocks of code that are nearly identical except for a few changes.
- Comments where appropriate. Line comments in Java use the `//` delimiter. Block (a.k.a. multi-line comments) comments use `/*` and `*/`.

**Style**:

-  basic indentation step is 4 spaces.

- Place a “}” brace on the same line as a following “else”, “finally”, or “catch”, as in.

- Methods should have Java doc comments explaining the behavior, parameters (using `@param` tags or otherwise), and return type.

- Methods that return non-void values must describe them in their Java doc comment either with a “@return” tag or in a phrase in running text that contains the word “return”, “returning”, or “returns”.

- Each Java doc comment must start with a properly formed sentence(大写字母), starting with a capital letter and ending with a period(句号).

- ### Names

  1. Names of static final constants must be in all capitals (e.g., RED, DEFAULT_NAME).
  
  2. Names of parameters, local variables, and methods must start with a lower-case letter, or consist of a single, upper-case letter.
  
  3. Names of types (classes), including type parameters, must start with a capital letter.
  
  4. Names of packages must start with a lower-case letter.
  
  5. Names of instance variables and non-final class (static) variables must start with either a lower-case letter or “_”.
  
- Do not try to catch the exceptions `Exception`, `RuntimeError`, or `Error`.

- Write “b” rather than “b == true” and “!b” rather than “b == false”.

- ### Limits

  1. No file may be longer than 2000 lines.
  2. No line may be longer than 100 characters.
  3. No method may be longer than 80 lines.
  4. No method may have more than 8 parameters.
  5. Every file must contain exactly one outer class (nested classes are OK).

