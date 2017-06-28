## Introduction
* C# (pronounced "SeeSharp") is a simple, modern, object-oriented,and type-safe programming language
* C# is an object-oriented language, but C# further includes support for component-oriented programming.
Contemporary software design increasingly relies on softwarecomponents in theform of self-contained and selfdescribing
packages of functionality. Key to such components is that they presenta programming model with
properties, methods,and events; they haveattributes that provide declarativeinformation about thecomponent;
and they incorporatetheir own documentation.
* Garbagecollection automatically reclaims memory occupied by unreachable unused objects
* exception handling provides a structured and extensibleapproach to error detection and recovery
* type-safe design of thelanguage makes it impossibleto read from uninitialized variables, to indexarrays beyond their bounds, or to perform unchecked type casts.
* C# has a unified typesystem. All C# types, including primitivetypes such as int and double , inherit from a singleroot object type
* C# sourcefiles typically havethefileextension .cs
*  Namespaces providea hierarchical means of organizing C# programs and libraries. Namespaces contain types and other namespaces

## .NET Framework

### CLR (Common Language Runtime)
* Memory Mgmt
* Operating system and Hardware Independence
* Language Independence

### CLR (Framework Class Library)
* A library to build applications(regex etc)

![1](https://user-images.githubusercontent.com/8856857/27516012-0fb2c078-59f4-11e7-88af-02ce23f9b919.PNG)

.cs - extension to a c# source code
compiles code and transforms it to MSIL (Microsoft Intermediate Language)

### Debugging
* start debugging/F5 and stops at a breakpoint
* autos window which has the arguments that are being looked at
* F10 and F11 Step Into and Step Over
 
## Program Structure
* The key organizational concepts in C# are programs, namespaces, types, members, and assemblies. 
* C# programs consist of one or more source files. Programs declare types, which contain members and can be organized into namespaces.
* Classes and interfaces are examples of types. 
* Fields, methods, properties, and events are examples of members. 
* When C# programs are compiled, they are physically packaged into assemblies. Assemblies typically have the file extension .exe or .dll, depending on whether they implement applications or libraries, respectively.

## Types and variables 
* There are two kinds of types in C#: value types and reference types.
* Variables of value types directly contain their data whereas variables of reference types store references to their data, the latter being known as objects
* C#’s value types are further divided into simple types, enum types, struct types, and nullable value types. C#’s reference types are further divided into class types, interface types, array types, and delegate types.
###The following provides an overview of C#’s type system.
* Value types
   * Simple Types
      * Signed integral: sbyte, short, int, long
      * Unsigned integral: byte, ushort, uint, ulong
      * Unicode characters: char
      * IEEE floating point: float, double
      * High-precision decimal: decimal
      * Boolean: bool
   * Enum types
      * User-defined types of the form enum E {...}
   * Struct types
      * User-defined types of the form struct S {...}
   * Nullable value types
      * Extensions of all other value types with a null value
 * Reference types
    * Class types
       * Ultimate base class of all other types: object
       * Unicode strings: string
       * User-defined types of the form class C {...}
    * Interface types
       * User-defined types of the form interface I {...}
    * Array types
       * Single- and multi-dimensional, for example, int[] and int[,]
    * Delegate types
       * User-defined types of the form delegate int D(...)
### Class Type
A class type defines a data structure that contains data members (fields) and function members (methods, properties, and others). Class types support single inheritance and polymorphism, mechanisms whereby derived classes can extend and specialize base classes.
### Struct Type
A struct type is similar to a class type in that it represents a structure with data members and function members. However, unlike classes, structs are value types and do not typically require heap allocation. Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type object.
### Interface Type
An interface type defines a contract as a named set of public function members. A class or struct that implements an interface must provide implementations of the interface’s function members. An interface may inherit from multiple base interfaces, and a class or struct may implement multiple interfaces.
### Delegate Type
A delegate type represents references to methods with a particular parameter list and return type. Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters. Delegates are analogous to function types provided by functional languages. They are also similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.
