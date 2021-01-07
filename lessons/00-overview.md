# Why typescript is beter way to approach FE?
There are a few new reasons I summarized on stackoverflow

## TypeScript's relation to JavaScript

### Support for modern JavaScript features 
- The JavaScript language (not the runtime) is standardized through the ECMAScript standards. Not all browsers and JavaScript runtimes support all features of all ECMAScript standards (see this overview). TypeScript allows for the use of many of the latest ECMAScript features and translates them to older ECMAScript targets of your choosing (see the list of compile targets under the --target compiler option). This means that you can safely use new features, like modules, lambda functions, classes, the spread operator and destructuring, while remaining backwards compatible with older browsers and JavaScript runtimes.

### Advanced type system
- The type support is not part of the ECMAScript standard and will likely never be due to the interpreted nature instead of compiled nature of JavaScript. The type system of TypeScript is incredibly rich and includes: interfaces, enums, hybrid types, generics, union/intersection types, access modifiers and much more. The official website of TypeScript gives an overview of these features. Typescript's type system is on-par with most other typed languages and in some cases arguably more powerful.

### Developer tooling support 
- TypeScript's compiler can run as a background process to support both incremental compilation and IDE integration such that you can more easily navigate, identify problems, inspect possibilities and refactor your codebase.

### Strict null checks
- With strict null checks enabled (--strictNullChecks compiler flag) the TypeScript compiler will not allow undefined to be assigned to a variable unless you explicitly declare it to be of nullable type. For example, let x : number = undefined will result in a compile error. This fits perfectly with type theory since undefined is not a number. One can define x to be a sum type of number and undefined to correct this: let x : number | undefined = undefined.

```javascript
let x: number | undefined;
if (x !== undefined) x += 1; // this line will compile, because x is checked.
x += 1; // this line will fail compilation, because x might be undefined.
```


### JavaScript interoperability

Since TypeScript is so closely related to JavaScript it has great interoperability capabilities, but some extra work is required to work with JavaScript libraries in TypeScript. TypeScript definitions are needed so that the TypeScript compiler understands that function calls like _.groupBy or angular.copy or $.fadeOut are not in fact illegal statements. The definitions for these functions are placed in .d.ts files.

The simplest form a definition can take is to allow an identifier to be used in any way. For example, when using Lodash, a single line definition file declare var _ : any will allow you to call any function you want on _, but then, of course, you are also still able to make mistakes: _.foobar() would be a legal TypeScript call, but is, of course, an illegal call at run-time. If you want proper type support and code completion your definition file needs to to be more exact (see lodash definitions for an example).

Npm modules that come pre-packaged with their own type definitions are automatically understood by the TypeScript compiler (see documentation). For pretty much any other semi-popular JavaScript library that does not include its own definitions somebody out there has already made type definitions available through another npm module. These modules are prefixed with "@types/" and come from a Github repository called DefinitelyTyped.

There is one caveat: the type definitions must match the version of the library you are using at run-time. If they do not, TypeScript might disallow you from calling a function or dereferencing a variable that exists or allow you to call a function or dereference a variable that does not exist, simply because the types do not match the run-time at compile-time. So make sure you load the right version of the type definitions for the right version of the library you are using.

To be honest, there is a slight hassle to this and it may be one of the reasons you do not choose TypeScript, but instead go for something like Babel that does not suffer from having to get type definitions at all. On the other hand, if you know what you are doing you can easily overcome any kind of issues caused by incorrect or missing definition files.

### Debugging TypeScript
Many browsers and IDEs offer direct debugging support through sourcemaps. See this Stack Overflow question for more details: Debugging TypeScript code with Visual Studio.
