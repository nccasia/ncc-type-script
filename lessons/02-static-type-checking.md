Java is dynamically typed language where the interpreter assigns variables a type at runtime based on the variable's value at the time.
Read more at the below link to understand what is defferent between static type vs dynamically typed
https://thecodeboss.dev/2015/11/programming-concepts-static-vs-dynamic-type-checking/
https://medium.com/android-news/magic-lies-here-statically-typed-vs-dynamically-typed-languages-d151c7f95e2b

## Type Checking
The process of verifying and enforcing the constraints of types . Type Checking may occur either at compile-time (a static check) or at run-time (dynamic check).
If a language specification requires its typing rules strongly (i.e., more or less allowing only those automatic type conversions that do not lose information), one can refer to the process as Strongly typed, if not, as Weakly typed.
Type checking is all about ensuring that the program is type-safe, minimizing the possibility of type errors. For eg — type error could be a situation where an operation is performed on a data of type integer with the intent that it is a float, or even something such as adding a string and an integer together
```javascript
a = “5” + 2;
```
Despite of the fact that in many languages both strings and integers can make use of the + operator, this would often result in a type error because this expression is usually not meant to handle multiple data types.
When a program is considered not to be type-safe, there is no single standard course of action that happens upon encountering a type error. Many Programming languages throw type errors which halts the run-time or compilation of the program, depending on the language type — static or dynamically typed.

Now since we have a basic understanding of what types are and how type checking works, we can start with the two primary methods of type checking: statically and dynamically typed languages.

## Static typed languages
A language is statically-typed if the type of a variable is known at compile-time instead of at run-time. Common examples of statically-typed languages include Java, C, C++, FORTRAN, Pascal and Scala.
In Statically typed languages, once a variable has been declared with a type, it cannot ever be assigned to some other variable of different type and doing so will raise a type error at compile-time(some IDE’s generally shows a Red Cross mark denoting the error).

declaration-constraints: https://miro.medium.com/max/386/1*75q760EAOyR9egJCEODu1w.png)
Type declaration constraints

## Example
Statically-typed languages require you to declare the data types of your variables before you use them
```javascript
int data;
data = 50;
```
data = “Hello World!”; // causes an compilation error
Note: the statement above (which binds an integer value, and then binds a string value to the same variable name data) is illegal. But in a dynamically-typed language this sequence of statements is perfectly fine.
### Advantages:
A large class of errors are caught in the early stage of development process.
Static typing usually results in compiled code that executes more quickly because when the compiler knows the exact data types that are in use, it can produce optimized machine code (i.e. faster and/or using less memory).
For a list of languages with static type checking, see the category for statically typed languages.

## Dynamically typed languages
A language is dynamically-typed if the type of a variable is checked during run-time. Common examples of dynamically-typed languages includes JavaScript, Objective-C, PHP, Python, Ruby, Lisp, and Tcl.
In Dynamically typed languages, variables are bound to objects at run-time by means of assignment statements, and it is possible to bind the same variables to objects of different types during the execution of the program.

## Type declaration constraints
Dynamic type checking typically results in less optimized code than static type checking. It also includes the possibility of run time type errors and forces run time checks to occur for every execution of the program (instead of just at compile-time).
Python Example
Dynamically-typed languages do not require you to declare the data types of your variables before you use them
```Python
data = 10;
data = “Hello World!”; // no error caused
```
The above statement assigns a new value to the same variable data of different data type than the one assigned earlier. The program will execute successfully without any error. This is characteristic to dynamic-typed programming languages.
### Advantages:
Implementations of dynamically type-checked languages generally associate each run time object with a type tag (i.e., a reference to a type) containing its type information. This run-time type information (RTTI) can also be used to implement dynamic dispatch, late binding, down-casting, reflection, and similar features.
The absence of a separate compilation step means that you don’t have to wait for the compiler to finish before you can test your code changes. This makes the debug cycle much shorter and less cumbersome.
For a list of such languages, see the category for dynamically typed programming languages.


Compare typescript vs javascript vs flow

https://soshace.com/typescript-vs-javascript-vs-flow/
