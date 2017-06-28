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
