# TypeScript Notes

# [TypeScript](https://www.typescriptlang.org/) is a typed superset of JavaScript.

## Why we need TypeScript?
- Detect errors at compile time without running the code.
- Transpilation to JavaScript.
- Compile time type checking.

## How to use TypeScript?

- Install TypeScript using [npm](https://www.npmjs.com/): `npm install -g typescript`

- Compile TypeScript code to JavaScript: `tsc hello.ts` 

- Compile TypeScript code to JavaScript and watch for changes: `tsc --watch hello.ts`

- Compile TypeScript code to JavaScript and watch for changes in multiple files: `tsc --watch hello.ts world.ts`

- Compile TypeScript code to JavaScript and watch for changes in multiple files and directories: `tsc --watch hello.ts world.ts src/**/*.ts`

- Compile TypeScript code to JavaScript and watch for changes in multiple files and directories, using a custom `tsconfig.json` file: `tsc --watch --project tsconfig.json`

- Compile TypeScript code to JavaScript using a custom `tsconfig.json` file: `tsc --project tsconfig.json`

- Compile TypeScript code to JavaScript using a custom `tsconfig.json` file and watch for changes: `tsc --watch --project tsconfig.json`

- Usage: `tsc --version` to get the version of the TypeScript compiler

- Usage: `tsc --help` to get help for the TypeScript compiler

- Usage: `tsc --init` to create a new `tsconfig.json` file

## Static Type Checking 

- Static type checking is performed at compile time, before the code is executed.
- Static type checking can help catch errors before they are run.
- Static type checking can also help improve the code quality and maintainability.

## Dynamic Type Checking

- Dynamic type checking is performed at runtime, after the code has been executed.
- Dynamic type checking can help catch errors after the code has been executed.
- Dynamic type checking can also help improve the code quality and maintainability.

--------------------------------------------------------------------

## Type Annotations and any Data Types

- Type annotations are used to specify the type of a variable, parameter, or property.

- The any data type is used to specify that a variable can hold any type of value.

- Example:

```ts
let x: number = 10;
let y: string = "Hello";
let z: boolean = true;
let a: any = "Hello"; // any data type
```

--------------------------------------------------------------------

## Type Annotations with arrays 

- Type Annotations are used to specify the type of a variable, parameter, or property.

- Example :

```ts
let arr : string[] = ["Ahmed","Basant","Ali","Hoda"];

```

-------------------------------------------------------------------------------------

## Type Annotations With Multidimensional Arrays 

- Multidiemnsional Arrays are arrays of arrays.

- Example : 

```ts 
let arr3 : (string | number | boolean)[] = ["Ahmed","Mona",23,14,true,false];
let arr4 : (string | number[] | boolean[])[] = ["Hazem","Menna",[23,132,45,54],[false,true]];
```

-------------------------------------------------------------------------------------

## Type Annotations with Functions 

- noImplicitAny: true in tsconfig.json used to disable the implicit any type.

- noImplicitReturns : will check if a function returns a value or not.

- noUnusedLocals : will check if a local variable is used or not.

- noUnusedParameters : will check if a parameter is used or not.

- Example : 

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

-------------------------------------------------------------------------------------

## Default and Optional Parameters in Functions

- Default parameters are parameters that have a default value. 

- Optional parameters are parameters that are optional.

- Example :

```ts
function showDetails2(name: string, age: number = 20, salary?: number): string {
    return `My Name is ${name} , My Age is ${age} and My Salary is ${salary}`;
}
console.log(showDetails2("Basant"));
```

-------------------------------------------------------------------------------------

## Function Rest Parameters

- Rest parameters are parameters that are passed to a function as an array

- Rest parameters are used to pass a variable number of arguments to a function.

- The rest parameter is denoted by three dots (...).

- Example :

```ts
function showDetails3(name: string, ...rest: number[]): string {
    return `My Name is ${name} , My Age is ${rest[0]} and My Salary is ${rest[1]}`;
}
console.log(showDetails3("Basant",23,1000));
```

-------------------------------------------------------------------------------------

## Anonymous Functions & Arrow Functions

- Anonymous functions are functions that are not named and are defined using a function expression.

- Arrow functions are functions that are defined using a lambda expression.

- Example :

```ts
// Anonymous Function using function expression
const showDetails4 = function(name: string) {
    return `My Name is ${name}`;
}
console.log(showDetails4("Basant"));
```

```ts
// Arrow Function using =>
const showDetails4 = (name: string) => {
    return `My Name is ${name}`;
}
console.log(showDetails4("Basant"));
```

-------------------------------------------------------------------------------------

## Type Aliases

- Type aliases are used to give a name to a type.

- Example :

```ts
type s = number | string;
let stringNum : s = 100 

stringNum = "Basant";
stringNum = 400;

console.log(stringNum); // last value --> 400
```

## Advanced Type Aliases

- Derived Type Aliases are used to create a new type based on an existing type.

- Example :

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
-------------------------------------------------------------------------------------

## Literal Types

- Literal types are used to specify a specific value for a variable.

- Example :

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

-------------------------------------------------------------------------------------

## Tuples Data Types

- Tuples are arrays that have a fixed length. 

- We know the type of each element and the number of elements in the array.

- Example :

```ts
let user : [string,number,boolean] = ["Basant",20,true];

user = ["Ahmed",21,true];

let [username,age,isActive] = user; // destructuring

// to get last value "Ahmed" --> we should do destructuring after re-assigning the tuple 
console.log(username); 
console.log(age);
console.log(isActive);
```
-------------------------------------------------------------------------------------

## Void and Never Data Types

- Void is used to specify that a function does not return a value but show undefined.

- Never is used to specify that a function never returns.

- Never is used to specify that a function throws an error or infinite loop after that 
it never returns (unreachable end point).

- Example :

```ts
function sayHello() : void {
    console.log("Hello Basant");
    // return('sa'); // error , because void type doesn't return a value
    // return; // valid , because void type can return undefined
}
sayHello();

function showError() : never {
    throw new Error("Something Went Wrong");
    // return "Error"; // unreachable end point 
    // return; // unreachable end point
}
showError();

```

-------------------------------------------------------------------------------------

## Enums Data Types

- Enums are used to define a set of named constants.

- Example :

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

### Advanced Enums Data Types

- Enums can have functions inside them.
- Enums can have computed members.
- Enums can be heterogeneous (i.e., they can have both numeric and string members).
- Enums can refer to other enums.
- Enums can refer to itself.

- Example :

```ts
function numberOfAnimalMeals() : number {
    return 2;
}

// animal 
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

-------------------------------------------------------------------------------------

## Data Types - Type Assertions

- Type assertions are used to specify the type of a variable.

- Type assertions are used to specify the type of a variable without using type annotations.

- There are two types of type assertions: "as" and "<>"

- Example :

```ts
let a : any = "Hello";
let b : any = 1000;

let c = a as string;
let d = <number> b;

console.log(c); // Hello
console.log(d); // 1000
```

-------------------------------------------------------------------------------------

## Data Types - Union Types & Intersection Types

- Union types are used to specify that a variable can be of more than one type.

- Intersection types are used to specify that a variable can be of more than one type at the same time.

- Example :

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

-------------------------------------------------------------------------------------

## Type Annotations with Objects

- Objects in type annotations are used to specify the shape of an object.

- Example :

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
-------------------------------------------------------------------------------------

## Interfaces - Methods & Parameters

- Interfaces are used to specify the shape of an object.

- Methods are used to specify the behavior of an object.

- Parameters are used to specify the type of a parameter.

- Example :

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

// user.country = "Mansoura"; // error , because country is readonly

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

### Reopen Interfaces - Use Cases

- Interfaces can be reopened to add new properties and methods.

- Example :

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

### Extending Interfaces 

- Interfaces can be extended to add new properties and methods.

- Example : 

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

### Notes :-

#### Difference between interfaces and type aliases

 1. interfaces can be reopened and extended , but type aliases can't

 2. interfaces can only describe object shapes , but type aliases can describe other types like union types , primitive types , tuples , etc.

 3. interfaces support declaration merging , but type aliases don't

 4. interfaces can implement other interfaces , but type aliases can't

 5. interfaces are generally preferred for defining object shapes , while type aliases are used for more complex types and unions

 6. interfaces can have optional properties and readonly properties , but type aliases can't

 7. interfaces can be used to define the shape of a class , but type aliases can't

 8. interfaces can have methods with implementation , but type aliases can't

 9. interfaces can extend multiple interfaces , but type aliases can't

 10. interfaces can be used to define the shape of a function , but type aliases can't

- Example :

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
-------------------------------------------------------------------------------------

## Classes in TypeScript

- Classes are used to define objects with properties and methods.

- Example :

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

-------------------------------------------------------------------------------------

## Class Access Modifiers & Parameter Properties

- public : can be accessed from anywhere (default)

- private : can be accessed only within the class

- protected : can be accessed within the class and its subclasses

- readonly : can be accessed but not modified

- parameter properties : a shorthand for defining and initializing class properties in the constructor by adding access modifier to the constructor parameter , it will create a class property with the same name and type

- Example :
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
-------------------------------------------------------------------------------------

## Get and Set Accessors

- Get and set accessors are used to define custom getter and setter methods for a class property.

- Get : used to get the value of a property

- Set : used to set the value of a property

- Example :

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
-------------------------------------------------------------------------------------

## Static Members in TypeScript

- Static members are used to define properties and methods that are shared between all instances of a class.

- Example :

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
-------------------------------------------------------------------------------------

## Class - Implementing Interfaces

- Interfaces can be implemented by classes.

- Classes can implement multiple interfaces.

- Example :

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
-------------------------------------------------------------------------------------

## Abstract Classes in TypeScript

- Abstract classes are used to define a blueprint for other classes.

- Abstract classes cannot be instantiated.

- Abstract classes can have abstract & concrete methods.

- Example :

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
-------------------------------------------------------------------------------------

## Polymorphism & method overriding in TypeScript

- Polymorphism is the ability of objects to take on multiple forms.

- Method overriding is the process of defining a method in a subclass that has the same name and parameters as a method in a superclass.

- Example :

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
-------------------------------------------------------------------------------------

## Generics in TypeScript 

- Generics are used to create reusable components that can work with different types of data.

- Example :

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
    // <T,S> is a generic type
  return  `The value1 is ${value1} and the value2 is ${value2}`
};

console.log(multipleTypes<boolean,string>(true,"Hello"));
```
-------------------------------------------------------------------------------------

## Generics with classes

- Example :

```ts

class User <T = string> { // <T = string> is default generic type , if we don't pass any type it will be string
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

let user3 = new User<string | boolean>(true); // we can pass string or boolean
console.log(user3.value);
user.showMsg("Please enter a string or boolean");
```
-------------------------------------------------------------------------------------

## Generics with interfaces

- Example :

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
    constructor(public data : T[] = []){} // data is an array of type T
    add(item : T) : void {
        this.data.push(item); // push the item to the array
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
-------------------------------------------------------------------------------------