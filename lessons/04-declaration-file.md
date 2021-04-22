A Type Declaration or Type Definition file is a TypeScript file but with .d.ts filename extension. So what so special about these Type Declaration files and how they are different from normal TypeScript files with .ts filename extensions?
A Type Declaration file, as the name suggests, only contains the type declarations and not the actual source code (business logic). These files are meant to only provide aid to the development process and not become part of the compilation itself.
A type declaration is just a declaration of a type such as an interface, a function or a class. You can declare a type and entity such as a variable, function, or an n object (that uses this type) at the same place (in the same file) or separate these in different files. We already went through the mechanisms to import these declarations in the previous lessons but here is the summary.
In the Module System lesson, we learned how to share type declaration between modules using import/export statements. You can import a type declaration from an ECMAScript or a CommonJS module just like a value.
In the Namespaces lesson, we learned how namespaces can help us achieve some modularity in a project without having to use fancy module systems such as ECMAScript or CommonJS. We can also share type declarations between different source files through interfaces using the triple-slash directives (explained in the namespaces lesson).
In the Compilation lesson, we learned about the lib compiler-option that controls the standard libraries included in the compilation process. These libraries are nothing but the declaration files provided by the TypeScript. We can also explicitly include type declarations in the compilation process using typeRoots and types compiler-options.
We can write our own TypeScript Declaration files or have them produced from the compilation of TypeScript files (.ts) by setting declaration compiler-option to true in the tsconfig.json file (or using--declaration flag with the tsc command).
In this lesson, we are going to learn the structure of the Type Declaration files and their use cases. Type Declaration in itself is a huge topic since the whole TypeScript ecosystem revolves around the Erased Type System (types), so we will keep this lesson as concise as possible. For more info on this topic, please visit the official TypeScript documentation website.

## Global Type Declarations
A global type declaration is available everywhere all the time. For example, when you write new Promise but do not provide any arguments, the TypeScript compiler won’t compile the program since one function argument is required in the Promise constructor. So where this Promise class type is defined and how does the TypeScript compiler know about it?
![image](https://user-images.githubusercontent.com/12141921/115661602-e2fb2180-a367-11eb-941f-068975d064a2.png)

As you can see from the above example, your IDE displays the error message and the location of the Type Declaration file that contains Promise type when you hover over the error. Such type declaration files are called global type declarations since they are exposed to every TypeScript program (included in the compilation) without having to explicitly import them.
The Promise type is written in one of the type declaration files provided by the TypeScript (lib.es2015.promise.d.ts to be precise, click on the blue link to open the file). They are collectively called the standard library.

>💡 You can control which standard libraries are imported implicitly using the lib compiler-option. You can explicitly disable all standard libraries by setting noLib compiler-option to true. These options are explained in the Compilation lesson.
>
The standard library (global type declaration) files are imported implicitly by the TypeScript compiler by looking at the lib compiler-option (or target when lib is not provided).
To load some global type declaration files manually, we need to instruct the TypeScript compiler where to find them. These are done using typeRoots and types compiler-options. These are explained in detail in the Compilation lesson so I am just going to go straight to the example.
Let’s say in our project, we need to have a few common types that will be available to all the source files. The typeRoots option specifies the list of directories from where the types should be imported. When the value of this option is not specified in the tsconfig.json, the TypeScript compiler imports declarations from all the node_modules/@types directories using the Node’s module resolution algorithm.
The node_modules/@types is a default type-root directory. A type-root directory contains normal Node modules but designed only to provides only type declarations. This declaration module should have a index.d.ts in its parent directory which would be imported by TypeScript as an entry declaration file of the module and this file can later import other declaration files. Or this module should have the package.json that indicates the location of the entry declaration file inside the module.

``` /project/sample/
├── program.ts
├── tsconfig.json
└── types/
   └── common/
      ├── main.d.ts
      └── package.json
```
At the moment, my project structure looks like this. I have a tsconfig.json file in the root directory of the project and a types/ directory which will be my custom type-root directory. The common declaration module contains the main.d.ts declaration file and a standard package.json.
Since the common declaration module doesn’t contain index.d.ts, we need to indicate the path of the main.d.ts (which is our entry declaration file) using the types or typings field of the package.json as shown below.
```
// types/common/package.json
{
  "name": "common",
  "version": "1.0.0",
  "typings": "main.d.ts"
}
```
Though we have a type declaration module, TypeScript has no idea that it exists since we haven’t configured the typeRoots compiler-option.
```
// tsconfig.json
{
  "files": [
    "./program.ts"
  ],
  "compilerOptions": {
    "typeRoots": [
      "./types"
    ]
  }
}
```
