TypeScript 是 JavaScript 的超集，它提供了静态类型检查、面向对象编程等特性，帮助提高代码质量。以下是 TypeScript 基本语法的概览：

### 1. **类型注解（Type Annotations）**

- TypeScript 允许你显式地指定变量、函数参数和返回值的类型。
    

```ts
let num: number = 10;
let name: string = "Alice";
let isActive: boolean = true;
```

### 2. **基本类型**

- **number**: 数字类型，支持整数和浮动小数。
    
- **string**: 字符串类型。
    
- **boolean**: 布尔类型，`true` 或 `false`。
    
- **any**: 任意类型，可以赋予任何类型的值，类似于 JavaScript 中的普通变量。
    
- **void**: 用于表示没有返回值的函数类型。
    

```ts
let count: number = 10;
let message: string = "Hello, TypeScript!";
let isCompleted: boolean = false;
let anything: any = "Can be anything";
```

### 3. **数组和元组**

- **数组（Array）**：使用 `[]` 或 `Array<type>` 来指定数组类型。
    

```ts
let numbers: number[] = [1, 2, 3];
let strings: Array<string> = ["apple", "banana"];
```

- **元组（Tuple）**：允许你定义固定数量的不同类型的元素。
    

```ts
let person: [string, number] = ["Alice", 25];  // 元组类型：字符串 + 数字
```

### 4. **对象类型**

- **对象（Object）**：你可以通过 `type` 或 `interface` 定义对象的类型。
    

```ts
let employee: { name: string; age: number } = { name: "John", age: 30 };
```

- **接口（Interface）**：定义对象的结构和约束。
    

```ts
interface Employee {
  name: string;
  age: number;
}

let employee: Employee = { name: "John", age: 30 };
```

### 5. **函数类型**

- **函数声明和类型注解**：你可以为函数的参数和返回值添加类型注解。
    

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}

let sum = (a: number, b: number): number => a + b;
```

### 6. **类型推断**

- TypeScript 会根据赋值自动推断出类型，不需要显式声明类型。
    

```ts
let age = 25;  // 推断为 number 类型
let greeting = "Hello, world!";  // 推断为 string 类型
```

### 7. **联合类型（Union Types）**

- 允许一个变量是几种类型中的一种。
    

```ts
let id: number | string;
id = 123;  // 可以是数字
id = "abc";  // 也可以是字符串
```

### 8. **类型别名（Type Alias）**

- 通过 `type` 关键字为类型创建别名。
    

```ts
type StringOrNumber = string | number;

let id: StringOrNumber;
id = 123;
id = "abc";
```

### 9. **枚举（Enum）**

- 枚举用于定义一组命名常数。
    

```ts
enum Color {
  Red = 1,
  Green,
  Blue,
}

let c: Color = Color.Green;  // c 值为 2
```

### 10. **类（Class）**

- TypeScript 支持面向对象编程，提供类、继承、访问修饰符等特性。
    

```ts
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): string {
    return `Hello, my name is ${this.name}`;
  }
}

const person = new Person("Alice", 25);
console.log(person.greet());  // Hello, my name is Alice
```

### 11. **接口与类的结合**

- 可以使用接口约束类的结构。
    

```ts
interface Greeter {
  greet(): string;
}

class Person implements Greeter {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): string {
    return `Hello, my name is ${this.name}`;
  }
}
```

### 12. **泛型（Generics）**

- 泛型允许你在定义函数、类或接口时，指定类型的占位符，从而实现类型的复用和更高的灵活性。
    

```ts
function identity<T>(arg: T): T {
  return arg;
}

let result = identity("Hello");  // T 被推断为 string
let numberResult = identity(123);  // T 被推断为 number
```

### 13. **类型断言（Type Assertion）**

- 你可以通过类型断言告诉 TypeScript 你确定某个变量的类型。
    

```ts
let someValue: any = "Hello, TypeScript";
let strLength: number = (someValue as string).length;
```

### 14. **模块（Module）**

- TypeScript 支持 ES6 模块语法，可以使用 `import` 和 `export` 导入和导出模块。
    

```ts
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

// main.ts
import { add } from "./math";
console.log(add(1, 2));  // 3
```

### 小结

- **类型注解**：TypeScript 允许你为变量、函数等添加类型注解，增强代码可读性和可维护性。
    
- **类型推断**：TypeScript 会自动推断出类型，但你可以显式声明类型以增强代码的严谨性。
    
- **面向对象**：TypeScript 支持类、接口、继承等面向对象的特性。
    
- **泛型**：可以编写可复用的代码，增强类型安全。
    

通过逐步学习并在实际项目中应用，你将能更好地掌握 TypeScript，提高代码的质量和可维护性。