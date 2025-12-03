# General comments

## Classes

- Package class

  - Most common features when working with classes
  - It has three members, defines a constructor and a method

- Every object is an instance of a class
- All classes except Null descend from Object
- It has a mixin-based inheritance, meaning that althought every classe, except for the otp class, has exactly one superclass, a class body can be reused in multiple class hierachies.
- Extension methods are a way to add functionality to a class without changing the class or creating a subclass
- Class modifier allow to control how libraries can subtype a class
- When you define a class, you should consider overriding `toString`to return a string describind an instance of that class.
- You might aldo need to define `hashCode` and `operator ==`
  - `hashCode` -> int
  - `runtimeType` -> Type
- Methods
  - `noSuchMethod(Invocation)` -> dynamic
    -Invoked when a nonexistent method or property is accessed
  - `toString()` -> String

### Using class members

- Object have members
  - Consists of cuntions and data (methods, and instance variables).
  - When you call a method, you invoke it on a object (the method has acces to that object functions and data)
- Use a dot `.` to refer to an instance variable or method
- You can use `?` to avoid an exception when the leftmost operand is null

### Constructors

- You can create an object using a constructor
- Constructor names can be either Classanem or ClassName.identifier
  ex: `Point(), Point.fromJson(), new Point()`
- Constanct constructors (const)
  - Create a compile-time constant using `const` keyword before the constructor name
  - With a constant context, you can omit the const before a constructor or literal, establishing the constant context.
- If you try to invoke a contructor with one constant object, and a non-constant (declared outside of a constant context), it creates in total a non-constant opject.

### Getting an object's type

- To get an object's type at runtime, you can use `Object` property `runtimeType`, which returns a Type object.
- It is preferable to use a type test operator rather than runtimeType, beecause it returns as `object is Type` other than `object.runtimeType == Type`

### Type test operator

    - `as` -> Typecast
    - `is` -> True if object has specified type
    - `is!` -> Contrary of is

### Instance variables

- `example? y;` -> Initially null
- `example z = 1` -> Initially 0
- All instance variables generate an implicit `getter method`
- Non-final instance variables and `late final` instance variables without initializers also generate an implicit `setter method`
  - For `getter method` you can use syntax `get` such as in example you get an instance variable -`exampleOne get instanceVarOne => propertyOne + propertyTwo;`
  - For `setter method`, access the object variable and define a new value using `.` and `=` operator.
- Using `this.` can access this in a late initializer, but not on a non-late initializer
- Using `final` keyword, the non-final instance variable must be set exactly once
- Be careful using `late final` since without an initializer adds a setter to the API
- Private fields can't be used as named initializing formals.
  -All variables introduced from initializing formal parameters are both final and only in scope of the initialized variables.
- To perform logic that you can't express in the initializer list, create a factory constructor or static method with that logic. You can then pass the computed values to a normal constructor.

#### Use an initializer list

- Before the constructor body runs, you can initialize instance variables. Separate initializers with commas.

### Implicit interfaces

- Every class implicitly defines an interface containing all the instance members of the class and of any interfaces it implements
- Ex: if you want to create a class A that supports class B's API without inheriting B's implementation, class A should implement the B interface

### Class variables and methods

#### Static Keyword

- Use `static` keyword to implement class-wide variables and methods (not only class variables)
- Static variables are useful for class-wide state and constants, such as:
  - `static const exampleOne = "example";`
- Static variables aren't initialized until they're declared (not called per se, such as late keyword)
  - Static keyword belongs to the class itself, rather than to any specific instance of the class
    - That means that there is only one copy of a `static` variable, shared by all instances of the class -`static` members can be accessed directly using the class name (ex: ClassName.staticVariable), without needing an instance of the class
- It can be mutable or immutable

#### Static Methods

- Doesn't operate on an instance, meaning that don't have access to `this`.
- They access static variables
- Consider using top-level functions, instead of static methods, for common or widely used utilites and functionality

### Redirecting constructors

- A constructor might redirect to another constructor in the same class
- The syntax is: `ExampleClass.alongXAxis(variable X) : this(X, 0);`

### Factory Constructors

- Usage examples of a `factory` keyword:
  - The constructor doesn't always create a new instance of its class
  - As checking arguments or doing any other processing that can't be handled in the initializer list
- It can't access this
- It can't return `null`
- It might return:
  - Existing instance from a cache instead of creating a new one
  - A new instance of a subtype

#### Redirecting factory constructors

- It specifies a call to a constructor of another class to use whenever someone calls to the redirecting constructor
  - Ex: `factory Listenable.merge(List<Listenable> listenables) = _MergingListenable`
- The advantages of redirecting factory constructors are:
  - An abstract class might provide a constant constructor that uses the constant constructor of another class
  - A redirecting factory constructor avoids the need for forwardes to repeat the formal parameters and their default values

### Constructor tear-offs

- A tear-off takes out the need to use the parentheses, serving as a closure that invokes the constructor with the same parameters
- If the tear-off is a constructor with the same signature and return type as the method accepts, you can use the tear-off as a parameter or variable
- Tear-off differ from lambdas or anonymous functios, since a tear-off is the constructor
- Ex: `var strings = charCodes.map(String.fromCharCode);`

#### Late Keyword

- Using `late` keyword meand that it's initialization is deffered until the first time the variable is accessed (lazy initialization)
- It can be mutable if doens't go with `final` keyword

### Constructor inheritance

- `Subclasses`, or child classes, don't inherit constructors from their superclass, or immediate parent class. If a class doesn't declare a constructor, it can only use the default contructor.
- A class can inherit the `parameters` of a superclass, these are classed `super parameters`

#### Non-default superclass constructors

- Dart executes constructors in the following order:
  - initializer list
  - superclass's unnamed, no-arg constructor
  - main class's no-arg constructor
- If the superclass lacks an unnamed, no-argument constructor, `call one of the constructors in the superclass`. Before the constructor body (if any), specify the `superclass constructor` after a colon `(:)`.

#### Super parameters

## Type safety

- Dart language is type safe

  - Uses static type checking to ensure that a variable's value always matches the static type

  - ## sound null safety

## Entrypoint

- Main entrypoint in a starter Flutter app is in lib/main.dart
  - the main method is as:
    `void main() {
runApp(const MyApp());
}`
