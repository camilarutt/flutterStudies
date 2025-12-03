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
- Constanct constructors
  - Create a compile-time constant using `const` keyword before the constructor name
  - With a constant context, you can omit the const before a constructor or literal, establishing the constant context.
- If you try to invoke a contructor with one constant object, and a non-constant (declared outside of a constant context), it creates in total a non-constant opject.

### Getting an object's type

- To get an object's type at runtime, you can use `Object` property `runtimeType`, which returns a Type object.
- It is preferable to use a type test operator rather than runtimeType, beecause it returns as `object is Type` other than `object.runtimeType == Type`

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
