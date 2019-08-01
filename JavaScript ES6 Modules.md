### Strict Mode
Using strict mode is the default in ES6 Modules, therefore specifying “use
strict” is not required.

### The `let` and `const` syntax
In ES6, you may declare your variables with var, let or const. Which one
should you choose? 

 - `const`:- It should be chosen if you’re not planning on changing the value
   of this variable (which then becomes a constant). This should be your
   default choice unless you absolutely need to re-assign it during
   runtime. Why should it be the default? Because it keeps your code
   explicit and clear.
- `let` :- It should be your second choice – use it whenever you need to re-assign variables. This will mostly be the case in mathematical algorithms or loops. It's scope is limited inside the block where it's defined. 
- `var` :- It should probably never be chosen. When using it, you may have a
constant or a variable – but no one knows! Therefore, use const or let
instead.  It is using for declaring variables with global scope.

#### `var`

    var age = 18
    console.log(age);
    if(true){
      var age= 25;
      console.log(age);
    }
    console.log(age);

output

	    18        
	    25        
	    25

#### `let`

    let age = 18
    console.log(age);
    if(true){
      let age= 25;
      console.log(age);
    }
    console.log(age);

output is 

    18        
    25        
    18

#### `const`

    const PIE = 3.14
    PIE = 18.9
    console.log(PIE);

If we tried to change the value of `const` after once it has been initialized,his will leads to the below error  

> TypeError: Assignment to constant variable

In case of constant array as well as constant object, we can change it's value, because the array and objects are reference types. They are not holding their values, they are holding the reference or pointer to their values in the memory. So while changing the value of the array or object, we are not changing the pointer stored in the it, we are changing the value where the pointer is pointing.
	
    const FRUITS = ['Apple','Orange']
    console.log(FRUITS)
    FRUITS.push('BANANA')
    console.log(FRUITS)
    
    const PERSON = {'name':'Adam'}
    console.log(PERSON)
    PERSON.name = 'Hawa'
    console.log(PERSON)
	
Output
	
    ["Apple",  "Orange"]    
    ["Apple",  "Orange",  "BANANA"]    
    [object  Object]  {  
        name:  "Adam"  
    }    
    [object  Object]  {  
        name:  "Hawa"  
    }
	
### Hoisting
Hoisting is the method of defining the variable after it's initialisation and usage. Hoisting is possible with `var`. At the same time `let` and `const` doesn't support hoisting.

    name = 'Adam'
    console.log(name)
    var name

### Fat Arrow Function
It allow you to use a shorter syntax to create functions. 
Syntax :- `const fn = (arg1, arg2) => return arg1 + arg2`	

> You may leave out the parenthesis around the arguments if only one argument is passed.

    var fun = a => a+200;
    console.log(fun(100))
	
> If no argument is passed, empty parentheses are required.

    var fun = () => 300+200;
    console.log(fun())

> The function body may be written inline and without curly braces if you’re only writing a return statement (return then also may be left out).

    var fun = (a,b,c) => a+b+c;
    console.log(fun(250,350,450))   

#### `this` keyword
Besides the shorter syntax, fat arrow functions also change the behaviour of the this keyword. Inside a fat arrow function, the this keyword will always refer to the context of the function instead of the caller of the function.

    function bike() {
      console.log(this);
    }
in the above code, it will print the context where it's called. 

     var bike = () => {
          console.log(this);
      }
But in the above fat arrow functions `this` will refer to the context where the function is defined. So in the above code, it will print the context where it's defined. 

### Default parameter
Default parameters allow you specify default values for parameters passed to functions.
Syntax :- `function fn(arg1 = ‘default string’, arg2 = 23) { return arg1 + arg2 }`

      var check = (number=10, compare = number) => {
          console.log(number+' and '+compare);
          return number == compare
      }
      console.log(check(10))
      console.log(check(10,20))
      
Output

    "10 and 10"
    true
    "10 and 20"
    false
    
### Literal Notation Extensions
There are some improvements to Literal Notation syntax. We can directly add the variable to the object as follows. The property name will be the variable name in this case. In other way, if we have not specified the value of a property, then will look for the variable with the same property name. If found, then the value of the variable will be taken as the property value.

    let name = 'Adam';
    let age = 25;
    let obj = {
      name,
      age
    };
    console.log(obj)
Output

    [object Object] {
      age: 25,
      name: "Adam"
    }

We can define function inside an object as follows.

    let name = 'Adam';
    let age = 25;    
    let obj = {
    	name,
    	age: 60,
    	details() {
    		console.log(this.name + ' is ' + this.age + ' years old')
    	}
    };
    obj.details()
    
We can also use text as function name inside curly braces as follows.

    let name = 'Adam';
    let age = 25;
    let obj = {
    	name,
    	age: 60,
    	"personal details" () {
    		console.log(this.name + ' is ' + this.age + ' years old')
    	}
    };
    obj["personal details"]()
    
We can set property as variable as follows.

    let name = 'Adam';
    let age = 25;
    let ageField = 'age';    
    let obj = {
    	name,
    	[ageField]: age,
    	"personal details" () {
    		console.log(this.name + ' is ' + this.age + ' years old')
    	}
    };
    obj["personal details"]()
    console.log(obj[ageField])

### Rest & Spread Operators (…)
ES6 added two important new operators: Rest and Spread. Technically they look the same ( … => three dots) but they are used in different places.

#### Rest Operator
Transforms a list of arguments (1, 2, 3) into an array ([1, 2, 3]) which may be used inside the function. This behavior is triggered when used inside of a function argument list.

    let sumUp = (...numbers) => {
    	console.log(numbers)
    	let result = 0
    	for (let i = 0; i < numbers.length; i++) {
    		result += numbers[i]
    	}
    	return result
    }
    console.log(sumUp(10, 20, 30, 40))

#### Spread Operator
Transforms an array into a list of arguments. This behaviour is triggered when used outside of a function argument  list.

    let numArray = [10, 20, 30, 40, 50]
    let sumUp = (...numbers) => {
    	console.log(numbers)
    	let result = 0
    	for (let i = 0; i < numbers.length; i++) {
    		result += numbers[i]
    	}
    	return result
    }
    console.log(sumUp(...numArray))
Output

    [[10, 20, 30, 40, 50]]
    "010,20,30,40,50"
    [10, 20, 30, 40, 50]
    150
### The `for-of` loop
A new loop was added: The for-of loop which allows you to loop through an array of items.

    let numbers = [10, 20, 30, 40, 50]
    for (let number of numbers){
      console.log(number)
    }

###  Template Literals
Template literals allow you to easily write more complex text in strings (e.g. including line breaks) as well as to output variables in a string. Template literals are used by starting and ending the string with back-ticks ( ` ) instead of quotation marks.

    let name = "Adam"
    let age = 29
    let status = "Single"
    let print = `Hello I am ${name}
			    I am ${age} years old.
			    I am ${status}`
    console.log(print)
Output

    "Hello I am Adam
    I am 29 years old.
    I am Single"


### Destructuring
Destructuring is a cool new feature which allows you to easily extract
values from an object or an array.

#### Arrays Destructuring
This is the method of pulling array elements into other variables in a single step. Using the method we can separate the array element to variables without changing the original array,

    let numbers = [10,20,30]
    let [a,b,c,d='default',e] = numbers
    console.log(a)
    console.log(b)
    console.log(c)
    console.log(d)
    console.log(e)

Output

    10
    20
    30
    "default"
    undefined

Using `Rest Operator` we can split array to sub array as follows

    let numbers = [10,20,30]
    let [y,...z] = numbers
    console.log(y)
    console.log(z)
Output

    10
    [20, 30]

We can exchange the value of two variable each other using destructuring as follows

    let a = 10;
    let b = 20;
    console.log('Before a=' + a + ' and b=' + b);
    [a, b] = [b, a];
    console.log('After a=' + a + ' and b=' + b);
Output

    "Before a=10 and b=20"
    "After a=20 and b=10"
    
While destructuring, we can skip elements in any specific position by putting blank space as follows.

    let numbers = [1, 2, 3];
    [a, , c] = numbers;
    console.log(a)
    console.log(c)
Output

    1
    3

#### Object Destructuring
This is the method of pulling out values of object into different variables without effecting the object. Like array  In case of object we are pulling out the element based on it's property name other than position in array destructuring. It's as follows.

    let person = {
    	name: "Adam",
    	age: 29,
    	about() {
    		console.log(name + 'is ' + age + ' years old')
    	}
    }
    
    let {name,age,about} = person
    console.log(name, age)
    about()
Output

    "Adam"
    29
    "Adamis 29 years old"
Like array object's elements are not ordered. So we can't skip any position by white space. But instead of skipping we need to specify only the required keys we want.

    let {name,age} = person
    console.log(name,age)
Output

    "Adam"
    29
In case of destructuring of object, we want to specify the variable in the same name of the key of the object. To avoid this problem, we can use alias in the object destructuring as follows.

    let {name,age,about:details} = person
    console.log(name, age)
    details()
Here the function `about` is alias as `details`


### Modules
ES6 finally, officially, adds Modules to JavaScript. This means, that you may split up your code over multiple files, which of course is a good practice. 

#### Setting up a module structure
If we don't have actual server we can use Plnkr (http://plnkr.co/) for testing our code. It will have multi file support like our local server. Before starting the module we need to add some ES6 supporting tools. Traceur is the main thing we need to add.. We can add it from the google git repository (https://github.com/google/traceur-compiler) or directly we can call it's live path. Traceur is a JavaScript.next-to-JavaScript-of-today compiler that allows you to use features from the future **today**. Traceur supports ES6 as well as some experimental ES.next features. For adding the traceur support, we need to specify it's path in our index,html file. We can use the live path of traceur for using it directly by adding the following code.

    <script data-require="traceur@*" data-semver="0.0.0-20140302" src="https://google.github.io/traceur-compiler/bin/traceur.js"></script>

Add we need to add system.js too by adding the following code index.html.

    <script data-require="systemjs@*" data-semver="0.21.4" src="https://cdn.rawgit.com/systemjs/systemjs/master/dist/system.js"></script>

Now we want to create a JavaScript file called `script.js` and need to import it into out body part of the index.html.  After these our index.html page will be as follows

    <!DOCTYPE html>
    <html>
    
      <head>
        <script data-require="traceur@*" data-semver="0.0.0-20140302" src="https://google.github.io/traceur-compiler/bin/traceur.js"></script>
        <script data-require="systemjs@*" data-semver="0.21.4" src="https://cdn.rawgit.com/systemjs/systemjs/master/dist/system.js"></script>
        <link rel="stylesheet" href="style.css" />
      </head>
    
      <body>
        <script>
          //System.import('./script.js') // Not working. So using below one
          <script  src="./script.js"  type="module"></script>
        </script>
      </body>
    
    </html>  
Here a style file called `style.css` also found. It's for styling our page.

### import/export
To split up your code, you basically export variables, functions, objects etc in one file and import it in another. If we want to use one property (function or variable) of once file from another file, we need to export it from where it's created and import it to where we want to use that. Her we have are trying to export the variable `keyValue` and function `test()` from external.js and importing in into script.js

    //external.js
    export let keyValue = 1000;
	export let test = () => {
	    console.log("Function executed")
	}
We have added `export` in front of the variable `keyValue` and `test()` for exporting it. 

    //script.js
    import {keyValue} from "./external.js";
    import {test} from "./external.js";
	console.log(keyValue)
	test();
We have importing the exported `keyValue` and `test()` variable in the above code. If more than one import or export in one file, we can group them as follows
 

    //external.js
     let keyValue = 1000;
     let test = () => {
        console.log("Function executed")
    }
    export{keyValue,test};
---
	//script.js
	import { keyValue, test } from "./external.js";
	console.log(keyValue)
	test();
	
While importing a variable, we are importing it's reference, not it's value. So any change made it that variable will be reflected in the place where we imported it.

#### `default`
In one file we can set one export as default. While making it default , we can import it in different syntax with any variable name. Here we are exporting variable `className` as default, so importing it as different name `defaultValue`.

    //external.js
    let keyValue = 1000;
    let test = () => {
        console.log("Function executed")
    }
    let className = "Class Name";
    export{keyValue,test};
    export default className;
---

    //script.js
    import { keyValue, test } from "./external.js";
    import defaultValue from './external.js'
    console.log(keyValue)
    test();
    console.log(defaultValue)
    
in case of multiple import, we can import the default import with other imports as follows

    import defaultValue, { keyValue, test } from "./external.js";
Here `defaultValue` is the default import. The default important should be front of the other always as this.

#### Alias
Aliasing is possible in case of import. So we can change the name of the variable which we are importing. `as` keyword is using for aliasing.

    //script.js
    import { keyValue as key} from "./external.js";
    console.log(key)
    
#### `import` all
We can import all as one object in a file. The we can get the values using the object. We are using start symbol (`*`) for these process and aliasing it in to another name.

    import * as all from "./external.js";
    console.log(all.keyValue)
    all.test();
Here `all` is the imported object.

### Strict Mode and Global Scope
There are two important Rules, which you need to understand if you're working with ES6 Modules:

1.  Modules are  _always_  in  **Strict Mode**  (no need to define  `"use strict"`)
2.  Modules don't have a shared, global Scope. Instead each Module has its own Scope

### Class
Classes are now also available via the class keyword. You may of course continue using other ways to create objects, but here’s the class-way. We are defining the class using the keyword `class` in front of the class name. Inside the class we can have variables. constructor and function. As we know, we can use the constructor for initialisation. A simple model of the class is as follows.

    class Person{
        constructor(name, age){
            this.name = name;
            this.age = age;
        }    
        about(){
            console.log(`I am ${this.name}. I am ${this.age} years old.`);
        }
    }    
    let person = new Person("Adam",29);
    person.about();

Prototype of the object of a class should be exactly same as the prototype of the class. We can prove that using the following code.

    console.log(person.__proto__  ===  Person.prototype)
    
This will print `true`.

#### Inheritance
You may also use inheritance with ES6 classes. One class can inherits the properties of other. `extends` keyword is using for the inheritance.

 - If parent class has a constructor and child class has not, then child class's object can create only by passing the parameters that are required by parent constructor.
 - If parent class has constructor and child class need to have, then we need to call the parent constructor inside child constructor by using `super` keyword.
 - If parent class and child class have same function (function with same name and parameters), then child class can use `super` keyword for accessing the parent function and `this` keyword for accessing it's own function. 

---

    class Person {
    	constructor(name, age) {
    		this.name = name;
    		this.age = age;
    	}
    	about() {
    		console.log(`I am ${this.name}. I am ${this.age} years old.`);
    	}
    }
    class Employee extends Person {
    	constructor(name, age, salary) {
    		super(name, age);
    		this.salary = salary;
    	}
    	about() {
    		super.about();
    		console.log(`My salary is ${this.salary}`);
    	}
    }
    let employee = new Employee("Adam", 29, 5000);
    employee.about();
Output

> I am Adam. I am 29 years old.
> My salary is 5000

Prototype of the object of a child class should be exactly same as the prototype of the child class (not the parent class). We can prove that using the following code.

    console.log(employee.__proto__  ===  Employee.prototype)
    
This will print `true`.

#### Inherit Built-in Objects
Like user defined object we can inherit the properties of built-in object in out class.

    class SumArray extends Array{
        sum(){
            let sume = 0;
            this.forEach(element => {
                sume+=element;
            });
            return sume;
        }
    }
    let sumArray = new SumArray();
    sumArray.push(1);
    sumArray.push(2);
    sumArray.push(3);
    sumArray.push(4);
    console.log(sumArray.sum());
    
Here class `SumArray` extending Built-in Object `Array`. So `SumArray` has all the properties of `Array` like `push()` and it has it's own properties like `sum()`.


#### Static Function
Static functions are also possible. A static function is a member function of a class that can be called even when an object of the class is not initialised. A static function cannot access any variable of its class except for static variables.

    class Common{
        static findMax(a,b){
            if(a>b){
                return a;
            }
            else{
                return b;
            }
        }
    }
    console.log(Common.findMax(25,24));
#### import/export
Like function and variables, we import/export the class too. 

    export class Config{
    
    }
#### Setters and Getters
We are using setter and getter for setting and getting properties of each class. This is using for providing data encapsulation. Here we are representing class variable name with an underscore prefix. `set<space>variableName` is the standard format of a setter and `get<space>variableName` is the standard format of a getter.

class Person {
    constructor(name, age){
        this._name = name;
        this._age = age;
    }

    set salary(salary){
        this._salary = salary
    }

    get salary(){
        return `${this._name} with age ${this._age} has salary ${this._salary}`
    }
}

let person = new Person("Adam",29);
person.salary = 10000; // Setting value
console.log(person.salary);  // Getting value

Output

> Adam with age 29 has salary 10000

### Symbols
`Symbols` are a new primitive data type just like the `Number`, `String`, and `Boolean`. Symbols have a `Symbol()` function which can be used to create them. Unlike the other primitives, Symbols do not have a literal syntax (e.g how Strings have `' '` ) - the only way to make them is with the Symbol constructor-not-constructor-thingy.```

    var symbol = Symbol();
    
Symbols have debuggability built in. It can be given a description, which is really just used for debugging to make life a little easier when logging them to a console.

    var symbol = Symbol('debug_key');
    console.log(symbol.toString());

Output

> "Symbol(debug_key)"

Symbols can be used as Object keys. This is where Symbols get really interesting. They are heavily intertwined with Objects. Symbols can be assigned as keys to Objects (kind of like String keys), meaning you can assign an unlimited number of unique Symbols to an object and be guaranteed that these will never conflict with String keys, or other unique Symbols.

    let symbolUsername = Symbol('username');
    let symbolPassword = Symbol('password');
    let user = {
      "Name" : "Adam",
      "Age" : 29,
      [symbolUsername] : 'adam123',
      [symbolPassword] : "ABDJDJ12355#"
    }
    console.log(user);

Output

    [object Object] {
      Age: 29,
      Name: "Adam"
    }
    
Here the `[symbolUsername]` key and its value and `[symbolPassword]` keys and it's value are hidden. If we want to see the value, we should call like this.

    let symbolUsername = Symbol('username');
    let symbolPassword = Symbol('password');
    let user = {
      "Name" : "Adam",
      "Age" : 29,
      [symbolUsername] : 'adam123',
      [symbolPassword] : "ABDJDJ12355#"
    }
    console.log(user);
    console.log(user[symbolUsername])
    console.log(user[symbolPassword])

The above code part will output the following too

    [object Object] {
      Age: 29,
      Name: "Adam"
    }
    "adam123"
    "ABDJDJ12355#"

By default, each new Symbol has a completely unique value. If you create a symbol (var mysym = Symbol()) it creates a completely new value inside the JavaScript engine. If you don’t have the reference for the Symbol, you just can’t use it. This also means two symbols will never equal the same value, even if they have the same description.

    let symbol1 = Symbol('foo');
    let symbol2 = Symbol('foo');
    console.log(symbol1 == symbol2); 
    
Output

    false

But we have a function `Symbol.for()`, will make possible to create identical symbols. This method creates a Symbol in a “global Symbol registry”.

    let symbol1 = Symbol.for('foo');
    let symbol2 = Symbol.for('foo');
    console.log(symbol1 == symbol2); 
    
Output

    true
The following example shows what is simple difference of the implementation of both unique and shared symbol.

The following is a small implementation of the advantage of unique key

    let home = {
      "name":"Thaj"
    }
    let lockDoor = (key) => {  
      home[key] = "SOMETHING"
      console.log("Door Closed");
    }
    let openDoor = (key) => {
      console.log((home[key] !== undefined)?"Door Opened":"Wrong Key");
    }
    
    let ownerKey = Symbol("key");
    let rentalKey = Symbol("key");
    
	lockDoor(ownerKey); // "Door Closed"
	openDoor(rentalKey); // "Wrong Key"
	openDoor(ownerKey); // "Door Opened"

Here both keys are unique. So the key having by owner is different from the key having by the rental. So only the owner can open the door.

    let home = {
      "name":"Thaj"
    }
    let ownerKey = Symbol.for("key");
    let rentalKey = Symbol.for("key");
    let lockDoor = (key) => {  
      home[key] = "SOMETHING"
      console.log("Door Closed");
    }
    let openDoor = (key) => {
      console.log((home[key] !== undefined)?"Door Opened":"Wrong Key");
    }
    
    lockDoor(ownerKey); // "Door Closed"
    openDoor(rentalKey); // "Door Opened"
    openDoor(ownerKey); // "Door Opened"
Here the both keys are similar. So both owner and rental can open the door with their key.

However, we can use the function `Symbol.keyFor()` for finding whether a key is share or unique. The Symbol.keyFor() is an inbuilt function in JavaScript which is used to retrieve the key which has been shared with the given symbols and this key is retrieved from the global symbol registry.

    var localFooSymbol = Symbol('foo');
    var globalFooSymbol = Symbol.for('foo');
    console.log(Symbol.keyFor(localFooSymbol));
    console.log(Symbol.keyFor(globalFooSymbol));

Output

    undefined
    "foo"
    
So if a symbol is unique, it's key which is retrieved from global symbol registry will be `undefined`. Otherwise we will get the exact key as the response of the function `Symbol.keyFor()`. 

Symbols will never conflict with Object string keys. This makes them great for extending objects you’ve been given (e.g. as a function param) without affecting the Object in a noticeable way.

    let person = {
      "name":"Adam",
      "age" : 29
    }
    
    let ageSymbol = Symbol("age");
    person[ageSymbol] = 30;
    console.log(person["age"]);
    console.log(person[ageSymbol]);
Output

    29
    30
#### Built-in Symbols
There are some built-in symbols you may utilize to overwrite default behaviors of JavaScript. This is also called meta-programming (i.e. changing parts of the language/ its behavior).

    class Person {
      
    }    
    let person = new Person();
    console.log(person);
    Person.prototype[Symbol.toStringTag] = 'Person Class';
    console.log(person);
Output

    [object Object] { ... }
    [object Person Class] { ... }

### Iterators & Generators
#### Iterators
Iterator is a function that iterate a collection inside the object. Iterators probably sound more complex than they are. Basically an iterator has a function `next()` which allows you to output values step by step. In the following example , we are using an `array`. Array has built-in iterator function. That is the reason why we can iterate an array through the for-each and for of loops etc. If we want to iterate an object, the object should contain a iterator function. 

    let obj = {
      name : "Adam",
      age : 29
    }
    console.log(typeof obj[Symbol.iterator]);
    
    let array = [1,2,3];
    console.log(typeof array[Symbol.iterator]);
    let it = array[Symbol.iterator]();
    console.log(it.next())
    console.log(it.next())
    console.log(it.next())
    console.log(it.next())
   
Output

    "undefined"
    "function"
    [object Object] {
      done: false,
      value: 1
    }
    [object Object] {
      done: false,
      value: 2
    }
    [object Object] {
      done: false,
      value: 3
    }
    [object Object] {
      done: true,
      value: undefined
    }

As mentioned above, an object should contain an iterator, if we want iterate it. Object doesn't have an iterator function, that is why the statement `console.log(typeof obj[Symbol.iterator])` printing `"undefined"`. At the same time an array have an iterator function by default. So the statement `console.log(typeof array[Symbol.iterator])` is printing `"function"`.  After that we are calling the iterator function of the array and iterating each element by calling the `next()` function from the array iterator. 

We can customise the iterator function of any object even it has default iterator object. Before start we should know one thing that, in case of iteration done by loops (for-each, for-of etc.), the loop will stop only when the value `done` become `true`. until the iteration will continue. So this may be leads to infinite iteration by a mistake while customising iterator function. 

    let array = [1,2,3];
    array[Symbol.iterator] = function(){
      return{
        next : function(){
         return{
             done : false,
             value : 10
         } 
        }
      }
    }
    
    let it = array[Symbol.iterator]();
    console.log(it.next())
    console.log(it.next())
    console.log(it.next())
    
Output

    [object Object] {
      done: false,
      value: 10
    }
    [object Object] {
      done: false,
      value: 10
    }
    [object Object] {
      done: false,
      value: 10
    }

Here we are customising the iterator of the array. So we are getting `10` instead of `1` as we customised in the code. Whenever we are trying to iterate it by calling the `next()`, it will return the same value for `'done'`and `'value'`. So in case of looped iteration, the loop will call the `next()` until the `done` become `true`. So in the case of this customisation, it will leads to infinite looping. So we are modifying the above code with a condition that limit the iteration based on some condition as follows.

    let array = [1,2,3];
    array[Symbol.iterator] = function(){
      let index = 10;
      return{
        next : function(){
         index++;
         return{
             done : index>15?true:false,
             value : index
         }
        }
      }
    }
    for(item of array){
      console.log(item)
    }

Output

    11
    12
    13
    14
    15

After the value `15`, the `done` become `true` and the iteration process will terminate. So `16` will not be printed.

    let persons = {
      name : "Adam",
      subjects : ["Englis", "Hindi", "Malayalam"]
    }
    for (let subjects of persons){
        console.log(subjects);
    }

Output

    Uncaught TypeError: persons is not iterable

In the above example. the object doesn't have an iterator function, so it's making error while trying to iterate it. So we can customise it's iterator as follows

    let persons = {
        name : "Adam",
        subjects : ["Englis", "Hindi", "Malayalam"],
        [Symbol.iterator] : function () {
            let i = -1;
            let subjects = this.subjects;
            return{
                next: function(){
                    i++;
                    return{
                        done : i >= subjects.length ? true : false,
                        value : subjects[i]
                    }
                }
            }
        }
    }
    
    console.log(typeof persons[Symbol.iterator]);
    console.log("--------");
    for (let subjects of persons){
        console.log(subjects);
    }

Output

    "function"
    "--------"
    "Englis"
    "Hindi"
    "Malayalam"

In the above example, we have customised the object for making iteration possible in it. As we wrote the iteration code, while iterating the object, it will iterate it's element `subjects` array.

#### Generator
A generator is a function that can stop midway and then continue from where it stopped. In short, a generator appears to be a function but it behaves like an iterator. Generator can have the following definitions too:

- Generators are a special class of functions that simplify the task of writing iterators. 
- A generator is a function that produces a sequence of results instead of a single value, i.e you generate ​a series of values.


For creating a generator function, we use `function * ` syntax instead of just `function`. Any number of spaces can exist between the `function` keyword, ` *`, and the `function name`. Since it is just a function, you can use it anywhere that a function can be used i.e inside objects, and class methods. Inside the function body, we don’t have a `return`. Instead, we have another keyword `yield`. It’s an operator with which a generator can pause itself. Every time a generator encounters a yield, it “returns” the value specified after it. We can also `return` from a generator. However, `return` sets the `done` property to `true` after which the generator cannot generate any more values.

    function * fruits(){
      yield "Apple";
      yield "Banana";
      yield "Orange";
      
    }
    
    
    let f = fruits();
    console.log(f.next());
    console.log(f.next());
    console.log(f.next());
    console.log(f.next());

Output

    [object Object] {
      done: false,
      value: "Apple"
    }
    [object Object] {
      done: false,
      value: "Banana"
    }
    [object Object] {
      done: false,
      value: "Orange"
    }
    [object Object] {
      done: true,
      value: undefined
    }

A generator is a function which returns an object on which you can call next(). The value property will contain the `value`. The `done` property is either `true` or `false`. When the done becomes `true`, the generator stops and won’t generate any more values.

    function * fruits(end){      
      if(end>0){    
        for(let i=0; i<end; i++){
          yield i;
        }
      }
      else{
        return
      }  
    }
    
    let f1 = fruits(0);
    console.log(f1.next());
    console.log("----------")
    
    let f2 = fruits(2);
    console.log(f2.next());
    console.log(f2.next());
    console.log(f2.next());

Output

    [object Object] {
      done: true,
      value: undefined
    }
    "----------"
    [object Object] {
      done: false,
      value: 0
    }
    [object Object] {
      done: false,
      value: 1
    }
    [object Object] {
      done: true,
      value: undefined
    }
    

### Promise
Imagine that you’re a top singer, and fans ask day and night for your upcoming single. To get some relief, you promise to send it to them when it’s published. You give your fans a list to which they can subscribe for updates. They can fill in their email addresses, so that when the song becomes available, all subscribed parties instantly receive it. And even if something goes very wrong, say, if plans to publish the song are cancelled, they will still be notified. Everyone is happy, because the people don’t crowd you anymore, and fans, because they won’t miss the single.

This is a real-life analogy for things we often have in programming:

1.  A “producing code” that does something and takes time. For instance, the code loads data over a network. That’s a “singer”.
2.  A “consuming code” that wants the result of the “producing code” once it’s ready. Many functions may need that result. These are the “fans”.
3.  A  _promise_  is a special JavaScript object that links the “producing code” and the “consuming code” together. In terms of our analogy: this is the “subscription list”. The “producing code” takes whatever time it needs to produce the promised result, and the “promise” makes that result available to all of the subscribed code when it’s ready.

A promise is an object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved. A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection. The Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.  Promises are used to handle asynchronous operations in JavaScript.

    let promise = new Promise(function(resolve, reject){
      let delay = 2000;
      setTimeout(function(){
       resolve(`Stopped after ${delay} milliseconds`)
      },delay) ; 
    })
    
    console.log("Starting the processing")
    promise.then(function(value){
      console.log(value)
    });
    
Output

    Starting the processing 
    another processing start running // These two lines print one by one
    Stopped after 2000 milliseconds // This line print after 2000 millisecond

Rejecting a request
Is there any error or anything wrong the promise can be rejected with the error and the error will be triggered in another function inside` then()`.
	
    let promise = new Promise(function(resolve, reject){
      reject(`Can't do First Process`)
    })
    
    console.log("First proces started")
    promise.then(function(value){
      console.log(value)
    }, function(error){
      console.log(error)
    });
    console.log("another processing start running")

Output

    First proces started
    another processing start running
    Can't do First Process

We can use the promise in many places depends upon our requirement. We can use the nested promise for asynchronous process.

    function waitASecond(second){
      return new Promise(function(resolve, reject){
        second++
        resolve(second);
      })
    }
    
    waitASecond(0).then(waitASecond).then(function(second){
      console.log(second)
    })
Output

    number 0 incremented and resolved
    number 1 incremented and resolved
    2
    
In the above code, first the `waitASecond()` function is called with the `second` as `0`. The variable `second` is increment by 1 and calling `resolve().` The `then()` function with  `waitASecond(second)` as argument is called. The actual parameter of `then()` is `function(value)`. Here the `waitASecond(second)` is similar to the `function(value)` in format, that is why this implementation is possible. That time again the  `waitASecond()` function called and number incremented by 1 and called `resolve()` This return triggered in the next then and the console is printed with the value 2,

    function waitASecond(second){
      return new Promise(function(resolve, reject){
        if(second<2){
          second++;
          resolve(second);
        }
        else{
          reject("Exceeds and rejected");
        }
      })
    }
    
    waitASecond(0)
      .then(waitASecond)
      .then(waitASecond)
      .catch(function(second){
        console.log("catch:"+second)
      })

Output

    catch:Exceeds and rejected

We can use the catch block for getting all the error in a promise execution while using a chain promise call. The catch block will execute whenever the reject statement called.

#### Built-in Functions
We have two main built-in function for promise they are `Promise.all()` and `Promise.race()`. Both of them are the function for processing group of promises. The `Promise.all()` will process all the process and return value only after all the promise completed.

    let promise1 = new Promise(function(resolve, reject){
      setTimeout(function(){
        console.log("Step 1 Executed")
        resolve("Step Result");
      },1000)
    });
    
    let promise2 = new Promise(function(resolve, reject){
      setTimeout(function(){
        console.log("Step 2 Executed")
        resolve("Step 2 Result");
      },2000)
    });
    
    Promise.all([promise1,promise2])
      .then(function(value){
        console.log(value);
      }).catch(function(error){
        console.log(error);
      })

Output

    "Step 1 Executed"
    "Step 2 Executed"
    ["Step Result", "Step 2 Result"]

Here the both promises are completed execution on their time, but the result triggered in the `then()` only after both promise competed.

    let promise1 = new Promise(function(resolve, reject){
      setTimeout(function(){
        console.log("Step 1 Executed")
        reject("Step 1 Error");
      },1000)
    });
    
    let promise2 = new Promise(function(resolve, reject){
      setTimeout(function(){
        console.log("Step 2 Executed")
        resolve("Step 2 Result");
      },2000)
    });
    
    Promise.all([promise1,promise2])
      .then(function(value){
        console.log("result:"+value);
      }).catch(function(error){
        console.log("catch:"+error);
      })

Output

    "Step 1 Executed"
    "catch:Step 1 Error"
    "Step 2 Executed"

In case of any rejection, it won't wait till all promise done, it will trigger error on `catch()` block and continue to wait for all other promise to be done. 

The `Promise.race()` is just opposite `Promise.all()`. It will execute all the promise but take only the first promise's result and return it at the same time it's completion and all other promise's result should be avoided. If the first promise is rejected, the catch block will trigger with the error and all other promises should be avoided.

    let promise1 = new Promise(function(resolve, reject){
      setTimeout(function(){
        console.log("Step 1 Executed")
        reject("Step 1 Result");
      },1000)
    });
    
    let promise2 = new Promise(function(resolve, reject){
      setTimeout(function(){
        console.log("Step 2 Executed")
        resolve("Step 2 Result");
      },2000)
    });
    
    Promise.race([promise1,promise2])
      .then(function(value){
        console.log("result:"+value);
      }).catch(function(error){
        console.log("catch:"+error);
      })

Output

    "Step 1 Executed"
    "catch:Step 1 Result"
    "Step 2 Executed"

### Extension of Built-In Objects
#### `Object.assign()`
The `Object.assign()` method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

    let obj1 = {
      a : 2
    }    
    let obj2 = {
      b : 4
    }    
    let obj = Object.assign(obj1,obj2);
    console.log(obj);
    
    console.log("obj === obj1");
    console.log(obj === obj1);
    
    console.log("obj === obj2");
    console.log(obj === obj2);

Output

    "obj (Merge result)"
    [object Object] {
      a: 2,
      b: 4
    }
    
    "obj === obj1"
    true
    
    "obj === obj2"
    false
    
Here other objects are merging with the first object So the first object become modified as merged one. `Object.assign()` copies property values. If the source value is a reference to an object, it only copies that reference value.

    obj2.b = 4000;    
    console.log(obj2);
    console.log(obj);

Output

    [object Object] {
      b: 4000
    }
    
    [object Object] {
      a: 2,
      b: 4
    }
    

#### `Math.sign()`
This will return the sign of a number. `1` for positive numbers, -`1` for negative, `0` for 0 and `NaN`  for other string etc.

    console.log(Math.sign(1)); // 1
    console.log(Math.sign(0)); // -1
    console.log(Math.sign(-1)); // 0
    console.log(Math.sign(NaN)); // NaN
    console.log(Math.sign("String")) // NaN

#### `Math.trunc()`
This is for trimming the decimal part from a decimal number. 

    console.log(Math.trunc(1.0)); // 1
    console.log(Math.trunc(1.1)); // 1
    console.log(Math.trunc(1.9)); // 1
    console.log(Math.trunc(0.0)); // 0
    console.log(Math.trunc(0.9)); // 0
    console.log(Math.trunc(0.1)); // 0
    console.log(Math.trunc(-1.0)); // -1
    console.log(Math.trunc(-1.1)); // -1
    console.log(Math.trunc(-1.9)); // -1

#### `Math.floor()`

This function will return the lower integer number.

    console.log(Math.floor(2.1)); // 2
    console.log(Math.floor(1.0)); // 1
    console.log(Math.floor(1.1)); // 1
    console.log(Math.floor(1.9)); // 1
    console.log(Math.floor(0.0)); // 0
    console.log(Math.floor(0.9)); // 0
    console.log(Math.floor(0.1)); // 0
    console.log(Math.floor(-1.0)); // -1
    console.log(Math.floor(-1.1)); // -2
    console.log(Math.floor(-1.9)); // -2

#### `String.startsWith()`
This function will check whether a string start with specific text.

    let country = "INDIA";
    console.log(country.startsWith("IND")); // true
    console.log(country.startsWith("ind")); // false
    console.log(country.startsWith("INS")); // false

#### `String.endsWith()`
This function will check whether a string ends with specific text.

    let country = "INDIA";
    console.log(country.endsWith("DIA")); // true
	console.log(country.endsWith("dia")); // false
    console.log(country.endsWith("DI")); // false

#### `String.includes()`
This function will check whether a string includes a specific text.

    let country = "INDIA";
    console.log(country.includes("NDI")); // true
    console.log(country.includes("ndi")); // false
    console.log(country.includes("AI")); // false
#### `Number.isNaN()`
This function will check whether it's NaN or not.

    let number = NaN
    console.log(Number.isNaN(number)); // true
    number = 124
    console.log(Number.isNaN(number)); // false
    number = "NaN"
    console.log(Number.isNaN(number)); // false

#### `Number.isFinite()`
This function will check whether it's finite or not.

    let number = 1000
    console.log(Number.isFinite(number)); // true
    number = Infinity
    console.log(Number.isFinite(number)); // false
    number = 10/0
    console.log(Number.isFinite(number)); // false
    
#### `Number.isInteger()`
This function will check whether it's integer or not.

    let number = 10
    console.log(Number.isInteger(number));
    number = 10.2
    console.log(Number.isInteger(number));
    number = Infinity
    console.log(Number.isInteger(number));

#### `Array.of()`
The `Array.of()` method creates a new Array instance from a variable number of arguments, regardless of number or type of the arguments.

    var array = Array(5);
    console.log(array); // [undefined, undefined, undefined, undefined, undefined]
    
    array = Array(5,10);
    console.log(array); // [5, 10]
    
    array = Array.of(5);
    console.log(array); // [5]
    
    array = Array.of(5,10);
    console.log(array); // [5, 10]

The difference between `Array.of()` and the `Array()` is in the handling of integer arguments: `Array.of(7)` creates an array with a single element, 7, whereas `Array(7)` creates an empty array with a length property of 7.

#### `Array.from()`
The `Array.from()` method creates a new, shallow-copied Array instance from an array-like or iterable object.

    var array = [10,100,1000];
    console.log(array); // [10,  100,  1000]
    
    let newArray = Array.from(array, val => val*2);
    console.log(newArray); // [20,  200,  2000]

#### `Array.fill()`  
The `fill()` method fills (modifies) all the elements of an array from a start index (default zero) to an end index (default array length) with a static value. It returns the modified array.

    var array = [10,100,1000];
    array.fill("x");
    console.log(array); // ["x",  "x",  "x"]
    
    var array2 = [10,100,1000];
    array2.fill("x",1,2);
    console.log(array2); // [10,  "x",  1000]

#### `Array.find()`

The `find()` method returns the value of the first element in the array that satisfies the provided testing function. Otherwise undefined is returned.

    var array = [5, 12, 8, 130, 44];
    console.log(array.find(val => val>10)); // 12
    
    var array2 = [5, 12, 8, 130, 44];
    var found = array2.find(function(element) {
      return element > 10;
    });
    console.log(found); // 12

Another method of finding in an array,

    let fruits = [
      {name : 'Apple', price: 85},
      {name : 'Pineapple', price: 110},
      {name : 'Grape', price: 150}
    ];
    console.log(fruits)

    let res = fruits.find(function(fruite){
       return fruite.name = "Apple"
    })
    console.log(res)

Output

    [[object Object] {
      name: "Apple",
      price: 85
    }, [object Object] {
      name: "Pineapple",
      price: 110
    }, [object Object] {
      name: "Grape",
      price: 150
    }]

    [object Object] {
      name: "Apple",
      price: 85
    }

#### `Array.copyWithin()`
The copyWithin() method shallow copies part of an array to another location in the same array and returns it without modifying its length.

> Syntax : arr.copyWithin(copyTo, copyingFrom, copyingTo)

    var array1 = ["A", "B", "C", "D","E","F","G"];
    console.log(array1); // ["A",  "B",  "C",  "D",  "E",  "F",  "G"]
    console.log(array1.copyWithin(2, 0, 4)); // ["A",  "B",  "A",  "B",  "C",  "D",  "G"]

Here copying item from 0th position to 4th position (means 4th position not included. i.e., "A", "B", "C", "D") in the place of item in the 2nd position without modifying array length.

    var array1 = ["A", "B", "C", "D","E","F","G"];
    console.log(array1); // ["A",  "B",  "C",  "D",  "E",  "F",  "G"]
    console.log(array1.copyWithin(3, 0, 4)); // ["A",  "B",  "C",  "A",  "B",  "C",  "D"]
If we have not specified the last position, it will take the array's last position as the default.

#### `Array.entries()`
The entries() method returns a new Array Iterator object that contains the key/value pairs for each index in the array.

    var array1 = ["A", "B", "C", "D","E","F","G"];
    let entry = array1.();
    for (element of entry){
      console.log(element);
    }

Output

    [0, "A"]
    [1, "B"]
    [2, "C"]
    [3, "D"]
    [4, "E"]
    [5, "F"]
    [6, "G"]

### Map
The Map object holds key-value pairs and remembers the original insertion order of the keys. Any value (both objects and primitive values) may be used as either a key or a value. A Map object iterates its elements in insertion order, a `for-of` loop returns an array of [key, value] for each iteration.

    let apple = {
      name:"Apple"
    }    
    let banana = {
      name:"Banana"
    }
    let cherries = {
      name:"Cherries"
    }
    let blackberry = {
      name:"Blackberry"
    }
    
    let map = new Map();
    map.set("A",apple);
    map.set("B",banana);
    map.set("C",cherries);
    
    console.log(map)
    //[object Map] { ... }
        
    console.log(map.size)
    //3
        
    map.set("B",blackberry)    
    console.log(map.size)
    //3
        
    console.log(map.get("A"))
    /*
    [object Object] {
      name: "Apple"
    }
    */
        
    console.log(map.delete("C"))
    //true
    
    console.log(map.get("C"))
    //undefined
        
    for(item of map){  
      console.log(item)
    }
    /*
    ["A", [object Object] {
      name: "Apple"
    }]
    ["B", [object Object] {
      name: "Blackberry"
    }]
    */
        
    for(keys of map.keys()){  
      console.log(keys)
    }
    /*
    "A"
    "B"
    */
    
    for(values of map.values()){  
      console.log(values)
    }
    /*
    [object Object] {
      name: "Apple"
    }
    [object Object] {
      name: "Blackberry"
    }
    */
        
    map.clear()
    console.log(map.size);
    //0

#### WeakMap
The WeakMap object is a collection of key/value pairs in which the keys are weakly referenced. The keys must be JavaScript objects and the values can be anything. We can't use primitives like number, string etc as key. WeakMap differ from Map in it's Garbage collecting feature. If the key we have inserted in the WeakMap is not using anymore, the entry in the map against the key will be deleted automatically by the JavaScript. For executing this mechanism, the WeakMap only support object as key. WeakMap is not iterable. So we can't fetch the item through looping as done in map. We can get the value by `get()` method. We also not able to find it's size because it's size might be change any time.

### Set
The Set object lets you store unique values of any type, whether primitive values or object references. It won't allow to add the same item already present. We can check the presence of the value instead of getting the value because we already know the value.

    let set = new Set([1,2,3,2]);
    set.add(3); // It won't work because '3' is already there.
    set.add(4);
    
    for(item of set){
      console.log(item)
    }
    
    /*
    1
    2
    3
    4
    */
    
    console.log(set.delete(1));
    //true
    console.log(set.has(1));
    //false
    set.clear();
`Set` has the function `entries()`, `keys()` and `values()`. It's not useful. It's giving result like a key value pair with same key and value.

    let set = new Set(["A","B"]);
    for(item of set.entries()){
      console.log(item)
    }
    
    /*
    ["A", "A"]
    ["B", "B"]
    */
        
    for(item of set.keys()){
      console.log(item)
    }
    /*
    "A"
    "B"
    */
    
    for(item of set.values()){
      console.log(item)
    }
    /*
    "A"
    "B"
    */
#### WeakSet
The `WeakSet` object lets you store weakly held objects in a collection. We can't use primitives like number, string etc as item. `WeakSet` differ from `Set` in it's Garbage collecting feature. If the object we have inserted in the WeakSet is not using anymore, the entry in the set will be deleted automatically by the JavaScript. For executing this mechanism, the `WeakSet` only support objects. `WeakSet` is not iterable. So we can't fetch the item through looping as done in set. We can check the item by `has()` method. We also not able to find it's size because it's size might be change any time.


    let obj1 = {
      name : "A"
    }

    let obj2 = {
      name : "B"
    }

    let set = new WeakSet([obj1,obj2]);
    console.log(set.has(obj1))
    //true
    set.delete(obj2)
    console.log(set.has(obj2))
    //false

### Reflect API
Reflect is a built-in object that provides methods for interceptable JavaScript operations. The methods are the same as those of proxy handlers. Reflect is not a function object, so it's not constructible. Unlike most global objects, Reflect is not a constructor. You cannot use it with a `new` operator or invoke the Reflect object as a function. All properties and methods of Reflect are static (just like the Math object).

#### `Reflect.construct()`
This function is equivalent to `new ClassName(...args)`. This is using for creating class objects. 

    class Person {
      constructor(name){
        this.name = name;
      }
    }
    
    let normalObj  = new Person("Adam");
    console.log(normalObj.name);
    //Adam
    
    let reflectObj = Reflect.construct(Person,["Hawa"]); 
    console.log(reflectObj.name);
    //Hawa
    
    console.log(reflectObj instanceof Person);
    //true

This function provides also the optional possibility to specify a different prototype.

    class Person {
      constructor(name){
        this.name = name;
      }
    }
    
    function TopObj(){
      return 100;
    }
    function TopObj2(){
      return 100;
    }
    
    let reflectObj = Reflect.construct(Person,["Hawa"],TopObj); 
    console.log(reflectObj instanceof Person);
    //false
    console.log(reflectObj.__proto__ == TopObj.prototype);
    //true

#### `Reflect.apply()`
The `Reflect.apply()` method calls a function with a given `this` value, and `args` provided as an array (or an array-like object).

    class Person{
      constructor(name){
        this.name = name;
      }      
      about(){
        console.log(`Name of the owner is ${this.name}`);
      }
    }    
    
    let owner = Reflect.construct(Person,["Adam"]);
    Reflect.apply(owner.about, owner,[])
    //"Name of the owner is Adam"    
    
    let staff = Reflect.construct(Person,["Hawa"]);
    Reflect.apply(owner.about, staff,[])
    //"Name of the owner is Hawa"
    
Here in case of first `apply()` we have passed the same `this`, so we got the name of actual owner object. But in the second `apply()` we have passes staff object as the `this`. So we got staff's name as the owner name. We can pass any object as the `this`, but the object should have the required properties which is using inside the function. Here we need the `name` parameter in both object because we are using `this.name` inside the function `about()`.

#### `Reflect.getPrototypeOf() and Reflect.setPrototypeOf()`
`Reflect.getPrototypeOf()` method returns the prototype of the specified object. 

    class Person{
      constructor(){
        this.name = "Adam";
      }
    }
    
    let animal ={
      name : "Dog"
    }
    
    let person = new Person();
    console.log(Reflect.getPrototypeOf(person) == Person.prototype)
    //true
    
    Reflect.setPrototypeOf(person,animal);
    console.log(Reflect.getPrototypeOf(person));
    /*
    [object Object] {
      name: "Dog"
    }
    */
    
    console.log(Reflect.getPrototypeOf(person) == Person.prototype)
    //false

#### Combination of all Reflect functions

    class Person{
      constructor(){
        this.name = "Adam";
      }
    }
    
    
    let animal ={
      name : "Dog",
      getAnimalName(){
        console.log(`Animal name is ${this.name}`)
        //"Animal name is Adam"
      }
    }
    
    let person = Reflect.construct(Person,[]);
    Reflect.setPrototypeOf(person,animal);
    Reflect.apply(person.getAnimalName,person,[]);    

Creating object `person` as the object of class `Person`. Changing it's prototype to `Animal` object. Then calling the `getAnimalName()` function of Animal object with person object as `this`. The Person class will have the function `getAnimalName()` because it's prototype is changed to Animal class.

#### `Reflect.get()` and `Reflect.set()`
A function that returns the value of properties. Using this function we can change the required property name dynamically in code.

    class Person{
      constructor(name,age){
        this._name = name;
        this.age = age;
      }  
      get name(){
        return this._name;
      }  
      set name(age){
        this._name = age;
      }
    }
    
    let person = new Person("Adam",27);
    console.log(Reflect.get(person,"name"));
    //"Adam"
    console.log(Reflect.get(person,"age"));
    //27
    
    Reflect.set(person,"name","Hawa");
    Reflect.set(person,"age","21");
    
    console.log(Reflect.get(person,"name"));
    //"Hawa"
    console.log(Reflect.get(person,"age"));
    //"21"
    
We can use these same methods by changing `this` reference as follows.

    class Person {
    	constructor(name, age) {
    		this._name = name;
    		this.age = age;
    	}
    	get name() {
    		return this._name;
    	}
    	set name(age) {
    		this._name = age;
    	}
    }
    
    let mum = {
    	_name: "Mother",
    }
    
    let person = new Person("Adam", 27);
    
    console.log(Reflect.get(person, 'name', mum));
    //"Mother"
    
    Reflect.set(person, 'name', "Monalisa", mum);
    
    console.log(person)
    /*
    [object Object] {
      _name: "Adam",
      age: 27
    }
    */
    
    console.log(mum)
    /*
    [object Object] {
      _name: "Monalisa"
    }
    */
Here we are using `mum` as the this reference. So the `get()` or `set()` method not touching the properties  of `Person` class, it's effecting `mum` object's properties. 

#### `Reflect.has()`
This will check whether function has a object has a property.

    class Person{
      constructor(name,age){
        this.name = name;
        this.age = age;
      }
    }
    let person = new Person("Adam",27);
    console.log(Reflect.has(person,"name"));
    //true

#### `Reflect.set()`
This function returns a boolean indicating whether an own or inherited property exists.

    class Person{
      constructor(name,age){
        this.name = name;
        this.age = age;
      }
    }
    let person = new Person("Adam",27);
    console.log(Reflect.has(person,'name'));
    //true
#### `Reflect.ownKeys()`
Returns an array of the target object's own (not inherited) property keys.

    class Person{
      constructor(name,age){
        this._name = name;
        this._age = age;
      }
      
      get name(){
        return this._name;
      }
      
      get age(){
        return this.age;
      }
      
      set name(name){
        this._name = name;
      }  
      
      set age(age){
        this._age = age;
      }
      
    }
    let person = new Person("Adam",27);
    console.log(Reflect.ownKeys(person));
    //["_name", "_age"]

#### `Reflect.defineProperty()`
It help's to define new property for an object.

    class Person{
      constructor(name,age){
        this._name = name;
        this._age = age;
      }
    }
    let me = new Person("Adam",27);
    let other = new Person("Adam",27);
    console.log(Reflect.ownKeys(other));
    //["_name", "_age"]
    
    Reflect.defineProperty(me,"language",{
      writable:true,
      value : ["Malayalam","English"]
    })
    console.log(Reflect.ownKeys(me));
    //["_name", "_age", "language"]
    
    console.log(Reflect.ownKeys(other));
    //["_name", "_age"]

#### `Reflect.deleteProperty()`
It will delete a property of an object by it's name.

    class Person{
      constructor(name,age){
        this.name = name;
        this.age = age;
      }
    }
    let me = new Person("Adam",27);
    let other = new Person("Adam",27);
    console.log(Reflect.ownKeys(other));
    //["name", "age"]
    
    Reflect.deleteProperty(me,"age",{
      writable:true,
      value : ["Malayalam","English"]
    })
    console.log(Reflect.ownKeys(me));
    //["name"]
    
    console.log(Reflect.ownKeys(other));
    //["name", "age"]

#### `Reflect.preventExtensions()` and `Reflect.isExtensible()`
`Reflect.preventExtensions()` prevents the modification of an object, at the same time `Reflect.isExtensible()` will check whether the object is modifiable or not.

    class Person{
      constructor(name,age){
        this.name = name;
        this.age = age;
      }
    }
    let person = new Person("Adam",27);
    console.log(Reflect.isExtensible(person));
    //true
    
    Reflect.preventExtensions(person)
    
    Reflect.defineProperty(person,"language",{
      writable:true,
      value : ["Malayalam","English"]
    })
    console.log(Reflect.isExtensible(person));
    //false
    
    console.log(person.language);
    //undefined

### Proxy
The Proxy object is used to define custom behaviour for fundamental operations (e.g. property lookup, assignment, enumeration, function invocation, etc). The object is wrapping by the proxy and we can access it only through the proxy.

#### `get:function()` and `set:function()`

    let person = {
      name : "Adam",
      age : 18
    }    
    let handler = {      
      get: function(target, prop){
        return prop in target? target[prop] : `Filed '${prop}' not found`;
      },
      set: function(obj, prop, value){
        if(value.length>2){
          Reflect.set(obj,prop,value);
        }
      }
    }    
    
    let proxyObj = new Proxy(person, handler);
    console.log(proxyObj.name);
    //"Adam"
    console.log(proxyObj.age);
    //18
    proxyObj.name = "A"
    console.log(proxyObj.name);
    //"Adam"
    proxyObj.name = "Hawa"
    console.log(proxyObj.name);
    //"Hawa"

Here the `proxyObj` act as a wrapper above the person. 

#### Proxy as Prototype

We can use the proxy as the prototype for an object for proxy protection.

    let person = {
      name : "Adam",
      age : 18
    };    
    let handler = {
      get: function(target, prop){
        return prop in target? target[prop] : (`Filed '${prop}' not found`);
      },
      set: function(obj, prop, value){
        if(value.length>2){
          Reflect.set(obj,prop,value);
        }
      }
    };
    let proxyObj = new Proxy({}, handler);
    Reflect.setPrototypeOf(person,proxyObj);
    console.log(person.name)
    //"Adam"
    person.name = "Hawa"
    console.log(person.name)
    //"Hawa"

#### Proxy of Proxy
We can use proxy over proxy

    let person = {
      name : "Adam",
      age : 18
    };    


    let handler = {
      
    }
    

    let protoHandler = {
      get: function(target, prop){
        return prop in target? target[prop] : (`Filed '${prop}' not found`);
      },
      set: function(obj, prop, value){
        if(value.length>2){
          Reflect.set(obj,prop,value);
        }
      }
    };
    let proxy = new Proxy({}, handler);
    let proxyProxy = new Proxy(proxy, protoHandler);
    Reflect.setPrototypeOf(person,proxyProxy);
    console.log(person.name)
    //"Adam"
    person.name = "Hawa"
    console.log(person.name)
    //"Hawa"

#### Proxy for Functions
We can use proxy for calling the function directly.

    function log(message){
      console.log(`Message is ${message}`)
    }
    
    let handler = {
      apply: function(target, thisArg, argumentsList) {
        if(argumentsList.length > 0){
          return Reflect.apply(target, thisArg, argumentsList);
        }
        else{
           console.log("No args")
        }
      }
    }
    
    let proxy = new Proxy(log,handler);
    proxy("Hi")
    //"Message is Hi"
    proxy()
    //"No args"

#### Revocable Proxy
We can cancel the proxy after it's use is over.

    let person = {
      name : "Adam"
    }    
    let handler = {
      get: function(target, prop) {
        return Reflect.get(target, prop)
      }
    }
    
    let {proxy,revoke} = Proxy.revocable(person,handler);    
    console.log(proxy.name) 
    //"Adam"   
    revoke();
    console.log(proxy.name)
    /*
	   "error"    
	   "TypeError: Cannot perform 'get' on a proxy that has been revoked  
	    at sivuhocuya.js:16:44  
	    at https://static.jsbin.com/js/prod/runner-4.1.7.min.js:1:13924  
	    at https://static.jsbin.com/js/prod/runner-4.1.7.min.js:1:10866"
	*/
