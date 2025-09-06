# 📘 TypeScript Notes

## 🌐 [TypeScript](https://www.typescriptlang.org/) is a typed superset of JavaScript.

---

### ❓ Why we need TypeScript?
- ⚡ Detect errors at compile time without running the code.
- 🔄 Transpilation to JavaScript.
- 🛡️ Compile time type checking.

---

### 🚀 How to use TypeScript?

- 📦 Install TypeScript using [npm](https://www.npmjs.com/): `npm install -g typescript`
- 📝 Compile TypeScript code to JavaScript: `tsc hello.ts`
- 👀 Watch for changes: `tsc --watch hello.ts`
- 📂 Watch multiple files: `tsc --watch hello.ts world.ts`
- 📁 Watch directories: `tsc --watch hello.ts world.ts src/**/*.ts`
- ⚙️ Use custom config: `tsc --watch --project tsconfig.json`
- 🛠️ Compile with config: `tsc --project tsconfig.json`
- 👓 Check version: `tsc --version`
- 🆘 Get help: `tsc --help`
- 🏗️ Init config: `tsc --init`

---

### 🏷️ Static Type Checking 

- 🕵️‍♂️ Performed at compile time.
- 🛑 Catch errors before running.
- 🧹 Improves code quality and maintainability.

---

### 🔄 Dynamic Type Checking

- ⏱️ Performed at runtime.
- 🐞 Catch errors after execution.
- 🧹 Improves code quality and maintainability.

---

## 📝 Type Annotations and `any` Data Types

- 🏷️ Specify type of variable, parameter, or property.
- 🧩 `any` type allows any value.

```ts
let x: number = 10;
let y: string = "Hello";
let z: boolean = true;
let a: any = "Hello"; // any data type
```

---

## 📚 Type Annotations with Arrays 

- 🏷️ Specify array element types.

```ts
let arr : string[] = ["Ahmed","Basant","Ali","Hoda"];
```

---

## 🧮 Type Annotations With Multidimensional Arrays 

- 🗂️ Arrays of arrays.

```ts 
let arr3 : (string | number | boolean)[] = ["Ahmed","Mona",23,14,true,false];
let arr4 : (string | number[] | boolean[])[] = ["Hazem","Menna",[23,132,45,54],[false,true]];
```

---

## 🛠️ Type Annotations with Functions 

- ⚙️ Useful compiler options:
    - `noImplicitAny`
    - `noImplicitReturns`
    - `noUnusedLocals`
    - `noUnusedParameters`

```ts
let showMsg = true;
function showDetails(name: string, age: number , salary : number): string {
        if(showMsg){
                return `My Name is ${name} , My Age is ${age} and My Salary is ${salary}`;
        }
        return 'Thanks';
}
console.log(showDetails('Ahmed',23,1000));
```

---

## 🎛️ Default and Optional Parameters in Functions

- 🧩 Default values and optional parameters.

```ts
function showDetails2(name: string, age: number = 20, salary?: number): string {
        return `My Name is ${name} , My Age is ${age} and My Salary is ${salary}`;
}
console.log(showDetails2("Basant"));
```

---

## 📦 Function Rest Parameters

- 📥 Pass variable number of arguments.

```ts
function showDetails3(name: string, ...rest: number[]): string {
        return `My Name is ${name} , My Age is ${rest[0]} and My Salary is ${rest[1]}`;
}
console.log(showDetails3("Basant",23,1000));
```

---

## 🕵️‍♀️ Anonymous Functions & Arrow Functions

- 🧑‍💻 Function expressions and arrow functions.

```ts
// Anonymous Function
const showDetails4 = function(name: string) {
        return `My Name is ${name}`;
}
console.log(showDetails4("Basant"));
```

```ts
// Arrow Function
const showDetails4 = (name: string) => {
        return `My Name is ${name}`;
}
console.log(showDetails4("Basant"));
```

---

## 🏷️ Type Aliases

- 🏷️ Give a name to a type.

```ts
type s = number | string;
let stringNum : s = 100 

stringNum = "Basant";
stringNum = 400;

console.log(stringNum); // last value --> 400
```

---

## 🧬 Advanced Type Aliases

- 🧩 Derived types.

```ts
type bug = {
        name: string,
        type : string,
}
type bug2 = bug & {
        color: string
}

let getBugs = ( b : bug2) => {
        console.log(`My Name is ${b.name} , My Type is ${b.type} and My Color is ${b.color}`);
}

getBugs({
        name : "Error Bug",
        type : "run time error", 
        color : "red"
})
```

---

## 🔢 Literal Types

- 🔢 Specify exact values.

```ts
type nums = -1 | 0 | 1;

function showNums(num1 : number , num2 : number) : nums {
        if(num1 === num2) return 0;
        else if(num1 > num2) return 1;
        else return -1;
}

console.log(showNums(10,20)); // -1
console.log(showNums(10,10)); // 0
console.log(showNums(40,30)); // 1
```

---

## 👫 Tuples Data Types

- 📏 Fixed-length arrays.

```ts
let user : [string,number,boolean] = ["Basant",20,true];

user = ["Ahmed",21,true];

let [username,age,isActive] = user; // destructuring

console.log(username); 
console.log(age);
console.log(isActive);
```

---

## 🚫 Void and Never Data Types

- 🚫 `void`: no return value.
- ⛔ `never`: never returns.

```ts
function sayHello() : void {
        console.log("Hello Basant");
}
sayHello();

function showError() : never {
        throw new Error("Something Went Wrong");
}
showError();
```

---

## 🎨 Enums Data Types

- 🏷️ Named constants.

```ts
const RED = 10;
const BLUE = 20;
const GREEN = 30;

enum Color {
        RED = 1,
        GREEN = 2,
        BLUE = 3,
}
let color : Color = Color.GREEN;
console.log(color); // 2
```

### 🧩 Advanced Enums Data Types

- 🧑‍🍳 Functions, computed, heterogeneous, references.

```ts
function numberOfAnimalMeals() : number {
        return 2;
}

enum FOOD {
        MEAT = "meat",
        FISH = "fish",
        BANANA = "banana",
        MILK = "milk"
}

enum ANIMAL {
        CAT = FOOD.MILK,
        DOG = 'dog',
        MONKEY = numberOfAnimalMeals(),
        ELEPHANT = 'elephant'
}

console.log(ANIMAL.CAT); // milk
console.log(ANIMAL.DOG); // dog
console.log(ANIMAL.MONKEY); // 2
console.log(ANIMAL.ELEPHANT); // elephant
```

---

## 🧩 Data Types - Type Assertions

- 🏷️ Specify type without annotation.

```ts
let a : any = "Hello";
let b : any = 1000;

let c = a as string;
let d = <number> b;

console.log(c); // Hello
console.log(d); // 1000
```

---

## 🔗 Data Types - Union Types & Intersection Types

- 🔗 Union: multiple possible types.
- 🔗 Intersection: combine types.

```ts
type A = {
        one : string,
        two : number,
        three : boolean
}

type B = A & {
        four : number
}

type C = {
        five : string
}

type mix = A & C;

function getActions(mixx : mix){
        console.log(mixx.one);
        console.log(mixx.two);
        console.log(mixx.three);
        console.log(mixx.five);
}

getActions({
        one : "Onneeeee",
        two : 222222,
        three : true,
        five : "Fiveeeee",
})
```

---

## 🧑‍💻 Type Annotations with Objects

- 🏷️ Specify object shape.

```ts
let myObject : {
        name : string,
        id : number ,
        hire : boolean,
        skills : string[],
        sayHello : () => string
}= {
        name : "Basant Elsaey",
        id : 12345,
        hire : true,
        skills : ["HTML","CSS","JavaScript","TypeScript"],
        sayHello : function() : string {
                return `Hello ${this.name}`;
        }
}
```

---

## 🧑‍🏫 Interfaces - Methods & Parameters

- 🏷️ Object shape, behavior, parameters.

```ts
interface User {
        name : string,
        id : number,
        readonly country : string,
        age? : number, // optional property
        sayHello() : string,
        getSalary(salary : number) : number,
        sayMsg : () => string
}

let user : User = {
        name : "Basant",
        id : 123,
        country : "Egypt",
        sayHello() : string { // function with no parameter
         return `Hello ${user.name}`
        },
        getSalary(salary : number) : number { // with parameter 
                return salary;
        },
        sayMsg : () => { // arrow function 
                return `Hello from Arrow Function`
        }
}

console.log(user.name);
console.log(user.id);
console.log(user.country);
console.log(user.sayHello());
console.log(user.getSalary(10000));
console.log(user.sayMsg());

function getUser (data : User){
        console.log(`My name is ${data.name} , My country is ${data.country}`)
}

getUser(user);
```

### 🔄 Reopen Interfaces - Use Cases

- 🔄 Add new properties/methods.

```ts
interface Settings {
        theme : string,
        fontSize : number,
        showNotifications : boolean
}

interface Settings {
        language : string,
        autoSave : boolean
}

let userSettings : Settings = {
        theme : "light",
        fontSize : 20,
        showNotifications : true,
        language : "English",
        autoSave : false
}
```

### 🧬 Extending Interfaces 

- ➕ Add new properties/methods.

```ts
interface Person {
        name : string,
        age? : number,
        getInfo() : string,
}

interface Employee {
        getSalary(salary : number) : number,
        jobTitle : string
}

interface Developer extends Employee,Person {
        level : string
}

let dev : Developer = {
        name : "Nada",
        getInfo() : string {
                return `My Name is ${dev.name}`;
        },
        getSalary(salary : number) : number {
                return salary;
        },
        jobTitle : "Frontend Developer",
        level : "Junior"
}
```

### 📝 Notes :-

#### ⚖️ Difference between interfaces and type aliases

1. 🔄 Interfaces can be reopened/extended, type aliases can't
2. 🧩 Interfaces describe object shapes, type aliases can describe unions, primitives, tuples, etc.
3. 🧬 Interfaces support declaration merging, type aliases don't
4. 🏗️ Interfaces can implement other interfaces, type aliases can't
5. 👍 Interfaces preferred for object shapes, type aliases for complex types/unions
6. 🏷️ Interfaces can have optional/readonly properties, type aliases can't
7. 🏛️ Interfaces can define class shapes, type aliases can't
8. 🧑‍💻 Interfaces can have methods with implementation, type aliases can't
9. ➕ Interfaces can extend multiple interfaces, type aliases can't
10. 🧑‍💻 Interfaces can define function shapes, type aliases can't

```ts
interface User {
        name : string,
        age : number
        getInfo() : string
}
type UserType = {
        name : string,
        age : number
        getInfo() : string
}
type UserType = {
        country : string
}
```

---

## 🏛️ Classes in TypeScript

- 🏗️ Define objects with properties and methods.

```ts
class User {
        n : string;
        s : number;
        showInfo : () => string;
        constructor(name : string,salary : number){
                this.n = name;
                this.s = salary;
                this.showInfo = function () {
                    return `My Name is ${this.n} and my Salary is ${this.s}`
                }
        }
        sayHello() : string {
                return `Hello ${this.n}`
        }
}

let user = new User("Basant",20000);
console.log(user.n);
console.log(user.s);
console.log(user.showInfo()); // property
console.log(user.sayHello()); // method
```

---

## 🔒 Class Access Modifiers & Parameter Properties

- 🌍 `public`: accessible anywhere
- 🔐 `private`: accessible only in class
- 🛡️ `protected`: accessible in class/subclasses
- 🏷️ `readonly`: can't be modified
- 🏗️ Parameter properties: shorthand for class properties

```ts
class User {
        sayHello : () => string;
        constructor(public name : string , private salary : number , protected readonly country : string){
                this.sayHello = function (){
                        return `Hello ${this.name}`;
                }
        }
        showInfo() : string {
                return `My Name is ${this.name} , My Salary is ${this.salary} and My Country is ${this.country}`;
        }
}

let user = new User("Basant",20000,"Egypt");
console.log(user.name);
console.log(user.salary); // error , because salary is private
console.log(user.country) // error , because country is protected
console.log(user.sayHello())
```

---

## 🧲 Get and Set Accessors

- 👁️ Get value, ✍️ Set value.

```ts
class User {
        sayHello : () => string;
        constructor(
                private _username : string,
                protected salary : string
        ){
            this.sayHello = function(){
                return `Hello ${this._username}`
            }
        }
        basicInfo(){
                return `My Username is ${this._username} and My Password is ${this.salary}`
        }

        get username() : string {
                return this._username;
        }
        set username(name : string){
                this._username = name;
        }
}

let user = new User("Basant","123");
console.log(user.username);
user.username = "Mona";
console.log(user.username); // Mona
console.log(user.sayHello()); // Hello Mona
console.log(user.basicInfo()); // My Username is Mona and My Password is 123
```

---

## 🏷️ Static Members in TypeScript

- 🏷️ Shared properties/methods.

```ts 
class User {
        static created : number = 0;
        static getCreated() : string {
                return `Created ${this.created} Users`;
        }
        constructor(public username : string){
                User.created++;
        }

}

let user = new User("Basant");
let user1 = new User("Mohamed");
let user2 = new User("Elsaey");
console.log(user.username); // Basant
console.log(User.created); // 3
console.log(User.getCreated()); // Created 3 Users
```

---

## 🏗️ Class - Implementing Interfaces

- 🏗️ Classes can implement interfaces.

```ts
interface Person {
        name : string,
        country : string,
        age? : number,
        saveUser() : void
}

interface Employee extends Person {
        salary : number,
        hire : boolean,
        sayHello() : string 
}

interface Developer extends Employee {
        skills : string[],
        jobTitle : string,
        level : string
}

class User implements Developer {
        constructor(
                public name : string,
                public country : string,
                public age : number,
                public salary : number,
                public hire :  boolean,
                public skills : string[],
                public jobTitle : string,
                public level : string
        ){}
        saveUser() : void {
                console.log(`User Saved Successfully`);
        }
        sayHello() : string {
                return `Hello ${this.name}`
        }
}

let user = new User("Ahmed","Egypt",20,20000,true,
        ["HTML","CSS","JavaScript","TypeScript"],
        "Frontend Developer",
        "Junior");

console.log(user.name); // Ahmed
console.log(user.country); // Egypt
console.log(user.age); // 20
console.log(user.salary); // 20000
console.log(user.hire); // true 
console.log(user.skills); // ['HTML', 'CSS', 'JavaScript', 'TypeScript']
console.log(user.jobTitle); // Frontend Developer
console.log(user.level); // Junior
console.log(user.sayHello()); // Hello Ahmed
```

---

## 🏛️ Abstract Classes in TypeScript

- 🏗️ Blueprint for other classes.

```ts
abstract class User {
        constructor(public username : string){}
        abstract saveUser() : void;
        abstract sayHello() : string;
}

class Admin extends User {
        constructor(username : string){
                super(username);
        }
        saveUser() : void {
                console.log(`User Saved Successfully`);
        }
        sayHello() : string {
                return `Hello Admin`;
        }
}

let admin = new Admin("Basant");
admin.saveUser();
console.log(admin.sayHello()); // Hello Admin
```

---

## 🦸‍♂️ Polymorphism & method overriding in TypeScript

- 🦸‍♂️ Multiple forms, override methods.

```ts
class Player {
        constructor(public name : string){}
        attack() : void {
                console.log("Attacking from Player");
        }
}

class Amazon extends Player {
        constructor(name : string, public spears : number){
                super(name);
        }
        override attack() : void { // method overriding
                console.log("Attacking from Amazon");
                this.spears -= 1;
        }
} 

class Barbarian extends Player { 
        constructor(name : string, public axeDurability : number){
                super(name);
        }
        override attack() : void { // method overriding
                console.log("Attacking from AXE");
                this.axeDurability -= 1;
        }
} 

let bar = new Barbarian("Barb",100);
let amazon = new Amazon("Amaz",50);
amazon.attack(); // Attacking from Amazon
console.log(amazon.spears) // 49
bar.attack(); // Attacking from AXE
console.log(bar.axeDurability); // 99
```

---

## 🧬 Generics in TypeScript 

- 🔄 Reusable components for any type.

```ts
function returnType<T>(value : T) : T { // <T> is a generic type
        return value;
}

console.log(returnType<number>(100)); 
console.log(returnType<string>("Hiiiiiii Basant"));
console.log(returnType<boolean>(true));
console.log(returnType<object>({name : "Basant",country : "Egypt"}));
console.log(returnType<number[]>([1,2,3,4,5]));

// arrow function

const returnTypeArrow =  <T>(value : T) :  T => value; 
console.log(returnTypeArrow<number>(50));

// multiple types 

const multipleTypes = <T,S>(value1 : T,value2 : S) : string => { 
    return  `The value1 is ${value1} and the value2 is ${value2}`
};

console.log(multipleTypes<boolean,string>(true,"Hello"));
```

---

## 🏛️ Generics with classes

```ts
class User <T = string> { // <T = string> is default generic type
        constructor(public value : T){}
        showMsg(msg : T) : void {
                console.log(`${msg} - ${this.value}`);
        }
}

let user = new User("Basant");
console.log(user.value); 
user.showMsg("This is a string");

let user2 = new User(100);
console.log(user2.value);
user.showMsg("This is a number");

let user3 = new User<string | boolean>(true);
console.log(user3.value);
user.showMsg("Please enter a string or boolean");
```

---

## 📚 Generics with interfaces

```ts
interface Book {
        title : string,
        price : number,
        pages : number
}

interface Magazine {
        title : string,
        price : number,
        issue : number
}

class Library<T> {
        constructor(public data : T[] = []){}
        add(item : T) : void {
                this.data.push(item);
        }
}

let book = new Library<Book>(); 
book.add({title : "Nodejs Design Patterns",price : 100,pages : 300});
book.add({title : "ES6",price : 100,pages : 200});
console.log(book);

let magazine = new Library<Magazine>();
magazine.add({title : "Nodejs",price : 100,issue : 1});
magazine.add({title : "ES6",price : 100, issue : 2});
console.log(magazine); 
```
