# Class decorator: 
được khai báo trước khi khai báo class ngay bên trên và nó apply cho contructor của class để sử dụng, chỉnh sửa or thay thế định nghĩa của class.
Ví dụ:

JavaScript
```javascript
@sealed
class Student {}
```
Tương ứng với nó, decorator function sẽ nhận 1 param – constructor của class được decorate. Ví dụ:

JavaScript
```javascript
@sealed
class Student {
    stdName: string;
    constructor(message: string) {
        this.stdName = message;
    }
    greet() {
    return "Hello, " + this.stdName;
    }
}
function sealed(constructor: Function) {
    console.log(Object.seal(constructor));
    console.log(Object.seal(constructor.prototype));
}
```

decorator trên sẽ log ra mỗi khi có 1 instance mới của class được khởi tạo.

JavaScript
console.log(new Student("Alice"));
1
console.log(new Student("Alice"));
Method decorator

# Method decorator:
 Method decorator được khai báo với 3 params:
– Target: class chứa method đó
– Tên member được decorate (chính là tên method)
– Property descriptor
Ví dụ:
```javascript
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    @enumerable(false)
    greet() {
        return "Hello, " + this.greeting;
    }
}
function enumerable(value: boolean) {
    return function (target: any, propertyKey: string, descriptor: PropertyDescriptor) {
        descriptor.enumerable = value;
    };
}
```
 

@enumerable(false) ở đây là một method decorator, khi decorator @enumerable(false) được gọi, nó sữa sửa đổi thuộc tính enumerable của descriptor.

# Accessor decorator
Tương tự với 2 decorator trên, accessor decorator dùng để decorate cho accessor của 1 property nào đó, tuy nhiên chúng ta chỉ định nghĩa decorate với accessor nào (get or set ) được viết trước tiên.
Ví dụ dưới đây là 1 accessor decorator được áp dụng cho 1 member của Demo class :

JavaScript
```javascript
class Demo {
    private _name: string;

    @modify
    get name(): string {
        return `My name is ${this._name}`;
    }
}
```

// ở đây ko cần viết @modify nữa
set name(input: string): void {
}

# Parameter decorator
Decorator loại này được định nghĩa ngay trước 1 parameter – có thể là 1 param của 1 function hoặc của constructor của Class.
Parameter decorator nhận đầu vào là 3 params
* class đầu vào.
* tên của param được decorate.
* thứ tự của param trong list các params của function cha.
Parameter decorator chỉ được sử dụng để kiểm tra sự tồn tại của params trong function , và thường được dùng kết hợp với method decorator hoặc accessor decorator
Ví dụ:
```javascript
class Greeter {
    greeting: string;

    constructor(message: string) {
        this.greeting = message;
    }

    @validate
    greet(@required name: string) {
        return "Hello " + name + ", " + this.greeting;
    }
}

```

Tài liệu tham khảo:

– https://www.typescriptlang.org/docs/handbook/decorators.html

