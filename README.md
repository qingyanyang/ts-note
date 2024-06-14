# ts-note
learning typescript

# type

Definition: Declaration and assignment
```typescript
  let a = 1; // Declaration + assignment, the type of a is fixed
  a='hello' //error

  let a: "male" | "female"
```

basic
```typescript
  let a: number; //string, boolean, number[], string[], 
  a = 10;
  a = 30;
  a = 'hello'; // error

  let b: {name: string, age: number}
  let b: {name: string, age?: number}
  let b: {name: string, [propName: string]:any}
  let b:{name: string} & {age: number}
  b={name:'ajax',age:12}
```
tuple
```typescript
  let tuple: [string, number];
  tuple = ['hello', 10];
  tuple = [10, 'hello']; // error
```
enum
```typescript
  enum Color { Red, Green, Blue }
  let color: Color;
  color = Color.Red;
  color = 1; // This is fine because enums are number-based
```
any & unknown
```typescript
  let anyType: any;
  anyType = 'hello';
  anyType = 10;
  anyType = true;

let anyType; // hidden any
  anyType = 'hello';
  anyType = 10;
  anyType = true;

// avoid using any
  let e: unknown;
  e = 10;
  e = "hello";
  e = true;

  let s: string;
  s = anyType; // correct
  e = "hello";
  s = e; // error

  if(typeof e === 'string') {
    s = e; // correct
  }

  // same as dynamic in Dart
  s = e as string;
  s = <string> e;
  
```
void
```typescript
  function logMessage(message: string): void {
    console.log(message);
  }
```
null & undefined
```typescript
let u: undefined = undefined;
let n: null = null;
```
never
```typescript
  function error(message: string): never {
    throw new Error(message);
  }
```
union
```typescript
  let union: string | number;
  union = 'hello';
  union = 10;
  union = true; // error
```
customed type
```typescript
  type StringOrNumber = string | number;
  let union: StringOrNumber;
  union = 'hello';
  union = 10;
  union = true; // error
```
function
```typescript
   let d: (a:number,b:number)=>number
      d = function(a:number,b:number):number {
        return a+b;
      }
```
interface
```typescript
  interface Person {
    name: string;
    age: number;
  }
  let person: Person;
  person = { name: 'John', age: 30 };
  person = { name: 'John' }; // error, missing property 'age'
```
class
```typescript
  class Animal {
  public name: string;
  private age: number;
  protected species: string;

  constructor(name: string, age: number, species: string) {
    this.name = name;
    this.age = age;
    this.species = species;
  }

  public getAge() {
    return this.age;
  }
}

class Dog extends Animal {
  constructor(name: string, age: number, species: string) {
    super(name, age, species);
  }

  public getSpecies() {
    return this.species; // 可以访问 protected 成员
  }
}

const dog = new Dog('Buddy', 5, 'Canine');
console.log(dog.name); // Output: Buddy
console.log(dog.getAge()); // Output: 5
// console.log(dog.age); // Error: Property 'age' is private and only accessible within class 'Animal'.
// console.log(dog.species); // Error: Property 'species' is protected and only accessible within class 'Animal' and its subclasses.
console.log(dog.getSpecies()); // Output: Canine

```

