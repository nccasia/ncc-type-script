TypeScript is a superset of JavaScript, so some datatypes are inherited from it. But TS introduces many more helpful data types. Let’s break them down in the following list.

## Boolean: 
is the simplest datatype, it is used to represent a logical value and can have only 2 values: true or false. It is the same as JavaScript boolean primitive type.
    
    ```typescript
    let isBoolean: boolean = true;
    let isLoading: boolean = false;
    ```

## Number:
like in JavaScript, all numbers in TypeScript are floating point values. In addition to hexadecimal and decimal literals, TypeScript also supports binary and octal literals introduced in ECMAScript 2015.
    
    ```typescript
    let decimal: number = 6;
    let hex: number = 0xf00d;
    let binary: number = 0b1010;
    let octal: number = 0o744;
    ```
    
## String:
is a textual datatype, it represents a sequence of characters stored as Unicode UTF-16 code. Just like JavaScript, TypeScript also uses double quotes " or single quotes to surround string data.

    ```typescript
    let str: string = 'this is a string';
    ```
    
In TypeScript is also possible to use template strings, which can span multiple lines and have embedded expressions. These strings are surrounded by the backtick/backquote () character, and embedded expressions are of the form ${expr}.

    ```typescript
    let name: string = 'Riccardo';
    let age: number = 39;
    let sentence: string = 'Hi my name is ${name}.
    I will be age ${age + 1} next year.';
    ```
    
## Array:
like JavaScript, Array types can be written in one of two ways. In the first, you use the type of the elements followed by [] to denote an array of that element type:

    ```typescript
    let arrayOfNumbers: number[] = [1, 2, 3];
    The second way uses a generic array type, Array<elemType>:
    let numbers: Array<number> = [1, 2, 3];
    ```
## Tuple:
this type allow developers to express an array with a fixed number of elements whose types are known, but need not be the same. For example, you may want to represent a value as a pair of a string and a number:

    ```typescript
    let x: [string, number] = ['Hello World', 13];
    ```
    Enum: this is a new feature of TypeScript and a helpful addition to the standard set of datatypes from JavaScript. An enum is a way of giving more friendly names to sets of numeric values.
    ```typescript
    enum Colours { Red, Green, Blue};
    let colour: Colours = Colours.Green;
    ```
    
    By default, enum begins numbering their members starting at 0. But this can be changed by manually setting the value of one of its members or set all the values in the enum:
    ```typescript
    enum Colours { Red = 1, Green = 5, Blue = 20};
    ```
    This means that using the values you can get the name of the colour in the example shown:
    ```typescript
    enum Colours { Red = 1, Green = 5, Blue = 20};
    let colorName: string = Colours[5];
    ```
    
## Any:
    when developers do not know the type of the value returning from an application or a third party library or the value dynamically changes every time a function is called, any is a placeholder to opt-out of type checking and let the values pass through compile-time checks.
    ```typescript
    let notSureAboutType: any = 5;
    notSureAboutType = 'reassigned as a string';
    ```
    
##  Void: 
this is usually the absence of having any type at all. Developers may commonly use this as the return type of functions that do not return a value.
    Null and Undefined: those are subtypes of all other types. That means you can assign null and undefined to something like number.
    Never: never type represents the type of values that never occurs. For instance, never is the return type for a function expression or an arrow function expression that always throws an exception or one that never returns; Variables also acquire the type never when narrowed by any type guards that can never be true.
    The never type is a subtype of, and assignable to, every type; however, no type is a subtype of, or assignable to, never (except never itself). Even any isn’t assignable to never.
    Object: object is a type that represents the non-primitive type, i.e. anything that is not number, string, boolean, bigint, symbol, null, or undefined.
    Type assertion: when there is a situation where developers know more about a value than TypeScript does, Type assertions are a way to tell the compiler to trust the value that is specified. It has no runtime impact, and is used purely by the compiler. TypeScript assumes that the programmers have performed any special checks that they need.
    Type assertions have two forms. One is the “angle-bracket” syntax:
    ```typescript
    let variableName: any = 'Hello World';
    let strLenght: number = (<string>variableName).length;
    And the other is the as syntax:
    let variableName: any = 'Hello World';
    let strLenght: number = (variableName as string).length;
    ```

This article want to be just as informative as possible and for more detailed information the official documentation is a must for everyone.
https://www.typescriptlang.org/docs/handbook/2/basic-types.html
