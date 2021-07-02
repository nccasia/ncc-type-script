In this section, we will learn about generics in TypeScript.

When writing programs, one of the most important aspects is to build reusable components. This ensures that the program is flexible as well as scalable in the long-term.

Generics offer a way to create reusable components. Generics provide a way to make components work with any data type and not restrict to one data type. So, components can be called or used with a variety of data types. Generics in TypeScript is almost similar to C# generics.

Let's see why we need Generics using the following example.
```
function getArray(items : any[] ) : any[] {
    return new Array().concat(items);
}
let myNumArr = getArray([100, 200, 300]);
let myStrArr = getArray(["Hello", "World"]);

myNumArr.push(400); // OK
myStrArr.push("Hello TypeScript"); // OK

myNumArr.push("Hi"); // OK
myStrArr.push(500); // OK

console.log(myNumArr); // [100, 200, 300, 400, "Hi"]
console.log(myStrArr); // ["Hello", "World", "Hello TypeScript", 500]
```
In the above example, the getArray() function accepts an array of type any. It creates a new array of type any, concats items to it and returns the new array. Since we have used type any for our arguments, we can pass any type of array to the function. However, this may not be the desired behavior. We may want to add the numbers to number array or the strings to the string array but not numbers to the string array or vice-versa.

To solve this, TypeScript introduced generics. Generics uses the type variable <T>, a special kind of variable that denotes types. The type variable remembers the type that the user provides and works with that particular type only. This is called preserving the type information.

The above function can be rewritten as a generic function as below.

Example: Generic Function Copy
```
function getArray<T>(items : T[] ) : T[] {
    return new Array<T>().concat(items);
}

let myNumArr = getArray<number>([100, 200, 300]);
let myStrArr = getArray<string>(["Hello", "World"]);

myNumArr.push(400); // OK
myStrArr.push("Hello TypeScript"); // OK

myNumArr.push("Hi"); // Compiler Error
myStrArr.push(500); // Compiler Error
```
In the above example, the type variable T is specified with the function in the angle brackets getArray<T>. The type variable T is also used to specify the type of the arguments and the return value. This means that the data type which will be specified at the time of a function call, will also be the data type of the arguments and of the return value.

We call generic function getArray() and pass the numbers array and the strings array. For example, calling the function as getArray<number>([100, 200, 300]) will replace T with the number and so, the type of the arguments and the return value will be number array. In the same way, for getArray<string>(["Hello", "World"]), the type of arguments and the return value will be string array. So now, the compiler will show an error if you try to add a string in myNumArr or a number in myStrArr array. Thus, you get the type checking advantage.

It is not recommended but we can also call a generic function without specifying the type variable. The compiler will use type inference to set the value of T on the function based on the data type of argument values.

Example: Calling Generic Function without Specifying the Type Copy
```
let myNumArr = getArray([100, 200, 300]); // OK
let myStrArr = getArray(["Hello", "World"]); // OK
```
Generics can be applied to the function's argument, a function's return type, and a class fields or methods.

