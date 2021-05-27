#### What are the differences between a class and an interface?
Following are the notable differences between class and an interface.


|   |**TypeScript Class**   | **TypeScript Interface**  |
| ------------ | ------------ | ------------ |
|  **Introduction** |  Classes are the fundamental entities used to create reusable components. It is a group of objects which have common properties. It can contain properties like fields, methods, constructors, etc | An Interface defines a structure which acts as a contract in our application. It contains only the declaration of the methods and fields, but not the implementation  |
|  **Usage** | It is used for object creation, encapsulation for fields, methods  | It is used to create a structure for an entity  |
|  **Keyword** | We can create a class by using the class keyword.  | We can create an interface by using the interface keyword.  |
|  **Compilation** | A class cannot disappear during the compilation of code  | Interface completely disappeared during the compilation of code  |
|  **Real-Time Usage** |  Design Pattern, Designing project Structure | Implements of defined Architectures  |
|  **Instantiation** | A class can be instantiated to create an object  | An interface cannot be instantiated  |
|  **Methods** | The methods of a class are used to perform a specific action  |  The methods in an interface are purely abstract (the only declaration, not have a body). |
|  **Access Specifier** | The member of a class can be public, protected, or private  | The members of an interface are always public  |
|  **Constructor** | A class can have a constructor  | An interface cannot have a constructor  |
|  **Implement/Extend** | A class can extend only one class and can implement any number of the interface  | An interface can extend more than one interfaces but cannot implement any interface.  |

##### Optional Properties
##### Readonly properties
##### Excess Property Checks
##### Function Types
##### Indexable Types
##### Class Types
###### Difference between the static and instance sides of classes
When working with classes and interfaces, it helps to keep in mind that a class has two types: the type of the static side and the type of the instance side. You may notice that if you create an interface with a construct signature and try to create a class that implements this interface you get an error:


```
interface ClockConstructor {
  new (hour: number, minute: number);
}

class Clock implements ClockConstructor {
```
Class 'Clock' incorrectly implements interface 'ClockConstructor'.
  Type 'Clock' provides no match for the signature 'new (hour: number, minute: number): any'.
```
  currentTime: Date;
  constructor(h: number, m: number) {}
}
```
This is because when a class implements an interface, only the instance side of the class is checked. Since the constructor sits in the static side, it is not included in this check.

Instead, you would need to work with the static side of the class directly. In this example, we define two interfaces, ClockConstructor for the constructor and ClockInterface for the instance methods. Then, for convenience, we define a constructor function createClock that creates instances of the type that is passed to it:

```
interface ClockConstructor {
  new (hour: number, minute: number): ClockInterface;
}

interface ClockInterface {
  tick(): void;
}

function createClock(
  ctor: ClockConstructor,
  hour: number,
  minute: number
): ClockInterface {
  return new ctor(hour, minute);
}

class DigitalClock implements ClockInterface {
  constructor(h: number, m: number) {}
  tick() {
    console.log("beep beep");
  }
}

class AnalogClock implements ClockInterface {
  constructor(h: number, m: number) {}
  tick() {
    console.log("tick tock");
  }
}

let digital = createClock(DigitalClock, 12, 17);
let analog = createClock(AnalogClock, 7, 32);
```
##### Hybrid Types
As we mentioned earlier, interfaces can describe the rich types present in real world JavaScript. Because of JavaScript’s dynamic and flexible nature, you may occasionally encounter an object that works as a combination of some of the types described above.

One such example is an object that acts as both a function and an object, with additional properties:

```
interface Counter {
  (start: number): string;
  interval: number;
  reset(): void;
}

function getCounter(): Counter {
  let counter = function (start: number) {} as Counter;
  counter.interval = 123;
  counter.reset = function () {};
  return counter;
}

let c = getCounter();
c(10);
c.reset();
c.interval = 5.0;
```
When interacting with 3rd-party JavaScript, you may need to use patterns like the above to fully describe the shape of the type.

#### Interfaces Extending Classes
