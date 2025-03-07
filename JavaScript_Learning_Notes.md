# Logical Operators in JavaScript

1. Logical AND operator
2. Logical OR operator
3. Logical XOR operator: The carat symbol (^) is used for the XOR operator in JS. 
    
    Important properties of XOR operator:
    
    - XOR with the same number gives zero - x XOR x = 0
    - XOR of any number with zero gives the same numbers - x XOR 0 = x (0 is the identity for XOR)
    - x XOR y = y XOR x (XOR is commutative)
    
    The XOR operator can be used to find the number which occurs only once in the array. Refer the code below:
    
    ```jsx
    
    const arr = [1, 2, 5, 4, 6, 8, 9, 2, 1, 4, 5, 8, 9] 
    let v = 0 
    for (i=0; i< arr.length i++){
       v = v ^ arr[i] 
      console.log(value)}
    ```
    

So, if we XOR all the elements in an array, the ones that are paired will cancel out. We can (theoretically) rearrange the XOR so they are next to each other; then they will XOR to zero, and zero doesn’t change the value of the XOR. Because of commutativity, this holds even if the paired elements aren’t next to each other.

If we have an array that has only one unpaired number, then XORing all the numbers will reveal that element.

For example, a XOR b XOR a = (a XOR a) XOR b = 0 XOR b = b

# Strings

Strings are iterables in JavaScript. We can index strings like an array and find the length of string using the length method.

```jsx
const str =  'Hello World'
console.log(str[0]) // H
// indexation can be directly applied on the string to find characters 
console.log('Hello World'[1]) // e
```

Length of a string can be found using the length method:

```jsx
const str = 'ABCDEF';
console.log(str.length) // 6
```

JavaScript has a concept of ‘boxing’ which means that everytime a string method is called on a string, JavaScript will convert it into an string object and put it inside a box or create an object out of the string. Refer the example below:

```jsx
console.log(new String(’Hello’))  // String {'Hello'}
console.log(typeof new String('Hello')) // Object
const newStr = 'Hello'
console.log(typeof newStr) // string
```

JavaScript provides a number of built-in methods for strings that allow developers to manipulate and work with strings in various ways. Here are some of the most commonly used string methods in JavaScript with examples:

1. **`charAt()`**: This method returns the character at the specified index in a string.

```jsx

const str = 'Hello, World!';
console.log(str.charAt(0)); // Output: "H"

```

1.  **`concat()`**: This method concatenates two or more strings and returns a new string.

```jsx

const str1 = 'Hello';
const str2 = 'World';
console.log(str1.concat(', ', str2)); // Output: "Hello, World"

```

1. **`includes()`**: This method checks if a string contains a specified substring and returns true or false.

```jsx

const str = 'Hello, World!';
console.log(str.includes('World')); // Output: true

```

1. **`indexOf()`**: This method returns the index of the first occurrence of a specified substring in a string.

```jsx

const str = 'Hello, World!';
console.log(str.indexOf('World')); // Output: 7

```

1. **`lastIndexOf()`**: This method returns the index of the last occurrence of a specified substring in a string.

```jsx

const str = 'Hello, World!';
console.log(str.lastIndexOf('o')); // Output: 8

```

1. **`replace()`**: This method replaces a specified substring with another string.

```jsx

const str = 'Hello, World!';
console.log(str.replace('World', 'Universe')); // Output: "Hello, Universe!"

```

The replacement can also be done using regex as follows. To create a regex, the replace method is still used but the string to be replaced is specified using ‘/’ (backslash). The ‘g’ flag after the backslash stands for global which replaces all instances of the selected string or character with the replacement. If the global flag is not used then only the first instance of the character or string is replaced. 

```jsx
const str = "DOG DIG DEEP"
console.log(str.replace(/D/g, 'X')) // XOG XIG XEEP
// without the global 'g' flag after the regex
console.log(str.replace(/D/, 'X')) // XOG DIG DEEP
```

1. **`slice()`**: This method extracts a section of a string and returns a new string

```jsx
const str = 'Hello, World!';
console.log(str.slice(0, 5)); // Output: "Hello"
```

1. **`split()`**: This method splits a string into an array of substrings based on a specified separator.

```jsx

const str = 'Hello, World!';
console.log(str.split(',')); // Output: ["Hello", " World!"]

```

1. **`startsWith()`**: This method checks if a string starts with a specified substring and returns a boolean value of either true or false.

```jsx

const str = 'Hello, World!';
console.log(str.startsWith('Hello')); // Output: true

```

1. The `endsWith()` method is a built-in JavaScript string method that is used to determine whether a string ends with a specified substring. It returns `true` if the string ends with the specified substring, and `false` otherwise. This method is often used for simple string manipulation and checking.

Here's the basic syntax of the `endsWith()` method:

```jsx
string.endsWith(searchString[, length])

```

- `string`: The string on which you want to perform the check.
- `searchString`: The substring you want to check if the `string` ends with.
- `length` (optional): An optional parameter that specifies the length of the string to consider for the check. If provided, the method will only check the substring within the first `length` characters of the string. This parameter is useful when you want to perform the check on only a portion of the string.

Here are a few examples of how to use the `endsWith()` method:

```jsx
const str = 'Hello, World!';

console.log(str.endsWith('World!')); // true
console.log(str.endsWith('Hello'));   // false

// Using the optional length parameter
console.log(str.endsWith('Hello', 5)); // true (checks only the first 5 characters)

```

In the first example, the `endsWith()` method returns `true` because the string `'Hello, World!'` ends with the substring `'World!'`.

In the second example, it returns `false` because the string `'Hello, World!'` does not end with the substring `'Hello'`.

In the third example, the optional `length` parameter is used to limit the check to the first 5 characters of the string, and it returns `true` because the substring `'Hello'` is found within those characters.

The `endsWith()` method is handy for tasks like checking file extensions, detecting certain patterns at the end of a string, or verifying user input.

1. **`substr()`**: This method extracts a specified number of characters from a string, starting at a specified index.

```jsx

const str = 'Hello, World!';
console.log(str.substr(0, 5)); // Output: "Hello"

```

1. **`toLowerCase()`**: This method converts a string to lowercase.

```jsx

const str = 'Hello, World!';
console.log(str.toLowerCase()); // Output: "hello, world!"

```

1. **`toUpperCase()`**: This method converts a string to uppercase.

```jsx

const str = 'Hello, World!';
console.log(str.toUpperCase()); // Output: "HELLO, WORLD!"

```

1. **`trim()`**: This method removes whitespace from both ends of a string.

```jsx

const str = '   Hello, World!   ';
console.log(str.trim()); // Output: "Hello, World!"

```

1. The **`padStart()`** and **`padEnd()`** methods are used to pad a string with another string or character to a specified length. These methods are commonly used when formatting strings, such as when masking credit card numbers.The **`padStart()`** method pads a string with another string or character at the beginning of the original string until the resulting string reaches the desired length. 
    
    padStart() and padEnd() return the original string if the targetLength is equal to the length of the string.
    

The syntax for **`padStart()`** is as follows:

```jsx

string.padStart(targetLength,padString)

```

Here, **`targetLength`** is the length of the resulting string, and **`padString`** is the string or character to pad with (default is a space). For example, consider the following code snippet:

```jsx

let creditCardNumber = "1123456744560086";
const masked = creditCardNumber.slice(12).padStart(12, "*");
console.log(masked);// ************0086

```

In this example, we first slice the string and consider only the last 4 digits of the string. Then **`padStart()`** is used to pad the **`creditCardNumber`** string with asterisks (*) for 12 places. The resulting string is stored in the **`maskedNumber`** variable, which is then logged to the console. 

As we can see, the first 12 digits of the credit card number are replaced with asterisks.

The **`padEnd()`** method works in a similar way to **`padStart()`**, but pads the string with another string or character at the end of the original string. The syntax for **`padEnd()`** is as follows:

```jsx

string.padEnd(targetLength [, padString])

```

Consider the following code snippet:

```jsx

const creditCardNumber = "1234567890123456";
const maskedNumber = creditCardNumber.slice(0,12).padEnd(16, "*");
console.log(maskedNumber); // 123456789012****

```

In this example, **`padEnd()`** is used to pad the **`creditCardNumber`** string with asterisks (*) at the end until it reaches a length of 16 characters. The resulting string is stored in the **`maskedNumber`** variable, which is then logged to the console. As we can see, the last 4 digits of the credit card number are replaced with asterisks.

1. The **`repeat()`** method in JavaScript is used to create a new string by repeating the original string a specified number of times. It returns a new string that consists of the original string repeated the specified number of times.

The syntax for the **`repeat()`** method is as follows:

```jsx

string.repeat(count)

```

Here, **`string`** is the original string, and **`count`** is the number of times the string should be repeated. The **`count`** parameter must be a non-negative integer.

Let's look at an example to understand how the **`repeat()`** method works:

```jsx

const message = "Hello, ";
const repeatedMessage = message.repeat(3);
console.log(repeatedMessage);

```

In this example, the **`repeat()`** method is used on the **`message`** string to repeat it three times. The resulting string is stored in the **`repeatedMessage`** variable, which is then logged to the console. The output of this code snippet is:

```jsx

Hello, Hello, Hello,

```

As we can see, the original string "Hello, " is repeated three times, creating a new string that consists of "Hello, " repeated consecutively.

It's important to note that if the **`count`** parameter is 0 or negative, an empty string will be returned. If the **`count`** parameter is not an integer, it will be rounded down to the nearest integer.

1. Join method for arrays

The **`join()`** method in JavaScript is used to join all elements of an array into a single string. It returns a new string where the elements of the array are concatenated with a specified separator.

The syntax for the **`join()`** method is as follows:

```jsx
array.join(separator)
```

The **`separator`** parameter is an optional string that specifies how the elements of the array should be separated in the resulting string. If omitted, the default separator is a comma (**`,`**).

Here's an example to illustrate how the **`join()`** method works:

```jsx
const fruits = ['apple', 'banana', 'orange'];
const result = fruits.join(' and ');

console.log(result);
// Output: "apple and banana and orange"
```

# Functions

## Default Parameters of Functions

Default parameters allow you to specify a default value that will be used if the corresponding argument is not provided when the function is called.

To define a default parameter, you simply assign a value to the parameter in the function declaration. Here's an example:

```jsx
const bookings = [];

const createBooking = function(flightNum, numPassengers = 1, 
price = 1000 * numPassengers){
  const booking = {
    numPassengers,
    flightNum,
    price
  }
  console.log(booking)
}

console.log(createBooking('ABC123',2, 10000)); //{numPassengers: 2, flightNum: 'ABC123', price: 10000}
console.log(createBooking('LSF651')); // {numPassengers: 1, flightNum: 'LSF651', price: 1000}
console.log(createBooking('BHJ712', 25)) // {numPassengers: 25, flightNum: 'BHJ712', price: 25000}x
```

In the above code, default values for parameters numPassengers and price has been given. For the price parameter, we use an expression and use the numPassengers parameter. This is possible only because numPassengers parameter has been declared earlier and has a default value assigned to it.

## Functions - Pass by Value or Pass by reference

In JavaScript, when passing arguments to functions, the behavior can be described as "call by value" or "call by reference" depending on the type of the argument.

1. Call by Value:
When a primitive value (like a string or a number) is passed as an argument, it is passed by value. This means that a copy of the value is created and passed into the function, independent of the original value. Any modifications made to the parameter inside the function do not affect the original value outside the function.
    
    In the provided code, the **`flight`** variable is a string, which is a primitive type. When it is passed to the **`checkIn`** function as **`flightNum`**, a copy of the value is created. Any changes made to **`flightNum`** inside the function do not affect the original **`flight`** variable.
    
2. Call by Reference:
When an object or an array is passed as an argument, it is passed by reference. Instead of creating a copy of the object, a reference to the original object in memory is passed into the function. This means that any modifications made to the object inside the function will affect the original object outside the function.
    
    ```jsx
    const flight = 'LH234';
    const jonas = {
      name: 'Jonas Schmedtmann',
      passport: 24739479284,
    };
    
    const checkIn = function (flightNum, passenger) {
      flightNum = 'LH999';
      passenger.name = 'Mr. ' + passenger.name; // updates the name property in original Jonas object
    
      if (passenger.passport === 24739479284) {
        alert('Checked in');
      } else {
        alert('Wrong passport!');
      }
    };
    
    checkIn(flight, jonas);
    console.log(flight); 
    console.log(jonas);
    
    const newPassport = function (person) {
      person.passport = Math.trunc(Math.random() * 100000000000);
    };
    
    newPassport(jonas);
    checkIn(flight, jonas);
    ```
    

In the provided code, the **`jonas`** object is passed to the **`checkIn`** function as **`passenger`**. Since objects are passed by reference, any changes made to the **`passenger`** object inside the function will also affect the original **`jonas`** object. Therefore, modifying the **`passenger.name`** property updates the **`jonas.name`** property.

**It's important to note that even though objects are passed by reference, the reference itself is still passed by value.** **This means that if the parameter inside the function is reassigned to a new object, it will not affect the original object reference outside the function. However, modifications made to the object properties will be reflected in the original object.**

**In JavaScript, there is no pass by reference, it is only pass by value. This is because even for non-primitives (arrays, objects) the reference is passed by value.**

In the code provided, after calling the **`newPassport`** function, the **`jonas.passport`** property is modified, which is then checked in the **`checkIn`** function. The change in the **`jonas.passport`** property affects the original **`jonas`** object, and the check-in result reflects the updated passport number.

It's essential to be aware of these behaviors when working with functions in JavaScript, as they can have implications for how variables are modified and shared between different parts of your code.

## Arguments are mapped to sequence of Parameters

It is not allowed to skip an argument while calling the function with multiple parameters. The sequence in which the value of arguments is considered by the function depends on the sequence of parameters. 

so the following is not allowed for the createBooking function:

```jsx
const bookings = [];

const createBooking = function(flightNum, numPassengers = 1, 
price = 1000 * numPassengers){
  const booking = {
    numPassengers,
    flightNum,
    price
  }
  console.log(booking)
}

createBooking('DFE455',  ,100); // Syntax Error
// However undefined is allowed
createBooking('DFE455',undefined, 100) // this is allowed
```

## First class Functions

In JavaScript, functions are treated as first-class citizens, which means they can be treated like any other value, such as a string or a number. This allows for a lot of flexibility in programming.

For example, you can assign a function to a variable, pass a function as an argument to another function, or return a function from a function.

Here's an example of a function being assigned to a variable:

```jsx
const add = function(a, b) {
  return a + b;
}

```

Here's an example of a function being passed as an argument to another function:

```jsx

function modifyAndLog(str, modifierFunc) {
  const modifiedStr = modifierFunc(str);
  console.log(modifiedStr);
}

function addExclamation(str) {
  return str + "!";
}

modifyAndLog("Hello, world", addExclamation);

```

In this example, the `modifyAndLog` function takes two arguments: a string and a function. It applies the function to the string and logs the result to the console.

The `addExclamation` function is passed as the second argument to `modifyAndLog` and becomes the modifierFunc() in the code block. This means that it will be applied to the string "Hello, world", resulting in the string "Hello, World!". The final output to the console will be "Hello, World!".

### Higher Order Function

In JavaScript a Higher order function can be created. A higher order function in JS is a function which receives another function as an argument or returns another function or both.

The function which is called as a parameter is called as **Callback function**. Example of function that receives another function as argument:

```jsx
const greet = () => {
console.log('Hello World')
}

// the btnClose function below is a higher order function which accepts
// the greet function defined above as a parameter
btnClose.addEventListener('click', greet); // greet is known as the callback fn.
```

### **Function returning another function**

```jsx
function greet(prefix) {
  return function(name) {
    console.log(prefix + ' ' + name);
  };
}

// Calling greet() returns a new function
const sayHello = greet('Hello');

// Invoking the returned function
sayHello('John');  // Output: Hello John

// We can also directly invoke greet() and its returned function
greet('Hi')('Sarah');  // Output: Hi Sarah
```

In the example above, we have a function called **`greet()`** that takes a **`prefix`** parameter. Inside **`greet()`**, it defines and returns an inner function. The inner function takes a **`name`** parameter and logs the concatenation of the **`prefix`** and **`name`** to the console.

When we call **`greet('Hello')`**, it returns the inner function. We assign this returned function to the variable **`sayHello`**. Now, **`sayHello`** holds a reference to the inner function.

By invoking **`sayHello('John')`**, we're effectively invoking the inner function with the **`name`** parameter set to **`'John'`**. It logs **`'Hello John'`** to the console.

We can also directly invoke **`greet('Hi')('Sarah')`** without assigning the returned function to a variable. This immediately calls **`greet('Hi')`**, which returns the inner function, and then immediately calls the inner function with the **`name`** parameter set to **`'Sarah'`**. It logs **`'Hi Sarah'`** to the console.

Returning a function from another function allows for the concept of function factories or closures, where the returned function retains access to variables defined in its outer scope, even after the outer function has finished executing. This enables powerful and flexible patterns in JavaScript programming.

## Function Invocation vs Method Invocation

In JavaScript, whether a function call is considered a "function invocation" or a "method invocation" depends on how the function is called and the context in which it is called.

1. **Function Invocation:**
    - A function invocation is a straightforward call to a function where the function is not associated with an object or a context.
    - It's a standalone call to a function, and the function operates independently of any specific object.
    - For example, `alert('Hello World!')` is a function invocation. The `alert` function is not associated with any specific object; it's just a built-in function that can be called globally.
2. **Method Invocation:**
    - A method invocation, on the other hand, occurs when a function is called as a property of an object.
    - In this case, the function is tied to an object, and it can access and operate on the properties and methods of that object using the `this` keyword.
    - For example, `console.log('Hello World!')` is a method invocation. Here, `console.log` is a method (a function) that is associated with the `console` object. It operates in the context of the `console` object and can access its properties and methods.

In summary, the key difference between function invocation and method invocation in JavaScript is whether the function is called independently (function invocation) or as part of an object (method invocation). The context in which the function is called, specifically whether it's associated with an object, determines whether it's considered a method invocation or a function invocation.

## Call and Apply method

Both the **`call()`** and **`apply()`** methods in JavaScript are used to invoke functions and explicitly set the value of **`this`** within the function. They allow you to call a function in a specific context, which can be useful for borrowing methods from other objects, setting the value of **`this`** explicitly, and passing arguments to the function.

```jsx
const person = {
  name: 'John',
  greet: function (message) {
    console.log(`${message}, ${this.name}!`);
  }
};

const friend = {
  name: 'Jane'
};

person.greet.call(friend, 'Hello');
// Output: Hello, Jane!
```

### call() method

The **`call()`** method calls a function with a specified **`this`** value and arguments provided individually. It takes the function's context (**`this`**) as its first argument, followed by any arguments the function expects. The arguments are passed as comma-separated values.

Syntax: **`function.call(thisArg, arg1, arg2, ...)`**

```jsx
const person = {
  name: 'John',
  greet: function (message) {
    console.log(`${message}, ${this.name}!`);
  }
};

const friend = {
  name: 'Jane'
};

person.greet.call(friend, 'Hello');
// Output: Hello, Jane!
```

### **`apply()` method**:

The **`apply()`** method is similar to **`call()`**, but it takes the function's context (**`this`**) as the first argument and an array-like object or an array of arguments as the second argument. The arguments are passed as an array or an array-like object.

Syntax: **`function.apply(thisArg, [argsArray])`**

```jsx
const person = {
  name: 'John',
  greet: function (message) {
    console.log(`${message}, ${this.name}!`);
  }
};

const friend = {
  name: 'Jane'
};

person.greet.apply(friend, ['Hello']);
// Output: Hello, Jane!
```

Both **`call()`** and **`apply()`** allow you to invoke a function in a specific context (**`this`** value) and pass arguments to the function. The only difference is in how the arguments are passed: **`call()`** accepts individual arguments, while **`apply()`** accepts an array-like object or an array of arguments.

These methods are particularly useful when you want to borrow methods from other objects, reuse code, or invoke functions with a specific **`this`** value, regardless of the object's original context. 

The code block given below is an example of apply() method without any array of arguments passed to it:

```jsx
 const details = {
  fullName: 'XYZ',
  age: 20,
  salary: 100000,
};

const person = {
  fullName: 'ABC',
  age: 30,
  salary: 200000,
  info: function(){
    console.log(`${this.fullName} is ${this.age} years old and has a salary of ${this.salary}`)
  }
};

person.info.apply(details);
```

### bind() method in JavaScript

In JavaScript, the **`bind()`** method is used to create a new function that has a specified **`this`** value and, optionally, prepends arguments to the original function when the new function is invoked.

The **`bind()`** method is helpful when you want to set the context (**`this`** value) for a function explicitly, regardless of how the function is called later. It allows you to create a new function that, when called, has its **`this`** value set to a specific object.

The syntax for the **`bind()`** method is as follows:

```jsx
function.bind(thisArg[, arg1[, arg2[, ...]]])
```

- **`thisArg`**: The value to be passed as the **`this`** value to the function when the bound function is called.
- **`arg1, arg2, ...`**: Optional arguments that are prepended to the arguments passed to the bound function when invoking it.

Here's an example to illustrate how the **`bind()`** method works:

```jsx
const restaurant = {
  name: 'Legends',
  bookings: [],
  order: function(starter, mainCourse) {
    console.log(`You ordered starter: ${starter} and main course: ${mainCourse}`);
    this.bookings.push(starter);
  }
};

const boundOrder = restaurant.order.bind(restaurant, 'Soup');

boundOrder('Steak'); // Outputs: You ordered starter: Soup and main course: Steak

console.log(restaurant.bookings); // Outputs: ["Soup"]
```

In the above example, the **`bind()`** method is used to create a new function **`boundOrder`** from the **`order`** function of the **`restaurant`** object. The **`this`** value is explicitly set to **`restaurant`**, and the additional argument **`'Soup'`** is also passed during the binding.

When **`boundOrder`** is called with the argument **`'Steak'`**, it invokes the original **`order`** function with the **`this`** value set to **`restaurant`** and the arguments **`'Soup'`** and **`'Steak'`**. As a result, the order is logged to the console, and the **`'Soup'`** starter is added to the **`bookings`** array of the **`restaurant`** object.

The **`bind()`** method is particularly useful when you need to pass a function reference with a specific context or pre-defined arguments, especially in scenarios like event handlers or callback functions.

### Partial Application in JavaScript

Partial application in JS refers to, basically specifying parts of the argument beforehand,
is actually a common pattern. So essentially, partial application means that a part of the arguments of the original function are already applied, so which means, already set. 

In the above code, when you use the **`bind()`** method to create the **`boundOrder`** function, specifying the argument **`'Soup'`**, it can be considered an example of partial application.

Partial application is a technique in functional programming where you create a new function by fixing (or binding) a specific number of arguments of an existing function. The resulting function can then be called with the remaining arguments at a later time.

In the code snippet above, the **`bind()`** method is used to partially apply the argument **`'Soup'`** to the **`order`** function of the **`restaurant`** object. The resulting **`boundOrder`** function is a new function that has the **`'Soup'`** argument already filled in. When you later invoke **`boundOrder('Steak')`**, you provide the remaining argument **`'Steak'`**, and the function is executed with both arguments.

 Partial Application allows you to create a new function with pre-filled arguments, which can be useful in scenarios where you want to reuse a function with some fixed values.

### Immediately Invoked Function Expression (IIFE)

IIFE functions are used when a function needs to run only once and never again. The syntax for IIFE functions is as follows:

```jsx
// The function is wrapped around a set of parenthesis and immediately after the 
// function block we call the function by writing another set of parenthesis
// the set of parenthesis at the end invokes the function 
(function()
{
console.log('This will never run again')
})()
```

### Difference between a standard function and IIFE

IIFE functions are immediately invoked and the value assigned to the variable. In the example below, there is an arrow function, which is immediately invoked and the returned value of the IIFE function is assigned to the variable myfunc:

```jsx
 const myfunc = (() =>{
  let val = 0;
  val += 5;
  console.log(val);
})(); 

console.log(myfunc) // 5
```

The above task can also be accomplished using a standard function, however it needs two steps: 

1. Create the function
2. Assign the return value of the function to a variable 

```jsx
// Using a arrow function
const myfunc1 = () =>{
  let val = 0;
  val += 10;
  console.log(val);
}

const result = myfunc1();
console.log(result) // 10
```

**In the IIFE, the variable myfunc had the returned value of the IIFE function so when the myfunc variable was logged to the console, it printed the return value from the IIFE.**

**However, in the second example, the variable myfunc1 is the function itself, not the returned value of the function. We save the return value in another variable (‘result’) and then log the value of the returned function.**

### Closures In JavaScript

Closures is an inbuilt characteristic of JavaScript. 

Definition: 

1. A closure is the closed over variable environment of the execution context in which a function was created even after that execution context is gone, or in other words, even after the function to which the execution context belongs has returned.
2. A closure gives a function access to all the variables of its parent function. So the function in which it is defined even after that parent function has returned. So the function keeps a reference to its outer scope even after that outer scope is gone, which basically preserves the scope chain throughout time.
3. Analogy is that a closure makes sure that a function does never lose connection to the variables that existed at the function's birthplace. It remembers the variables, even after the birthplace is gone. It's like a person who doesn't lose connection to their hometown. In this analogy, the person is the function and the hometown is the function's parents scope, and the function then doesn't lose the connection to the variables stored in this parent's scope.
4. Some people like to think of this attached variable environment as a backpack. So in this analogy, a function has a backpack, which it carries around wherever it goes. And this backpack contains all the variables that were present in the environment in which the function was created. Then whenever a variable can't be found in the function scope, JavaScript will look into the backpack and take the missing variable from there.

```jsx
const secureBooking = () =>{
	let passengerCount = 0;
	return function(){
			passengerCount++;
			console.log(`${passengerCount} passenger);
			}
	};

const booker = secureBooking()

booker() // 1 passenger
booker() // 2 passenger
booker() // 3 passenger
```

From the above code we can see that the Booker function was in fact able to increment the passengerCount to one, then to two and then to three. But now if we think about this,
then how is this even possible? How can the Booker function update this passengerCount variable that's defined in a secure booking function that actually has already finished executing.
This function has already finished its execution.It is gone. So its execution context is no longer on the stack, but still this inner function here, which is the Booker function, is still able to access the passengerCount variable that's inside of the Booker function that should no longer exist.
What makes this possible is a closure.  So we can say that a closure makes a function
remember all the variables that existed at the function's birthplace essentially, right?
So we can imagine the secureBooking function as being the birthplace of this function.
And so this function remembers everything at its birthplace,by the time it was created.
Anyway, the first thing that's happens is that a new execution context is created and put on top of the call stack and the variable environment of this context is emptied simply because there are no variables declared in this function. Now what about the scope chain? Well, since the booker() function is in the global context, it's simply a child's scope of the global scope. So how will the Booker function access the passengerCount variable? It's nowhere to be found in the scope chain, right? So this is where we start to unveil the secret of the closure and the secret is basically this. Any function always has access to the variable environment of the execution context in which the function was created. Now, in the case of Booker, this function was created. It was born in the execution context of secure booking, which was popped off the stack previously, remember? So, therefore the booker function will get access to this variable environment, which contains the passengerCount variable. And this is how the function will be able to read and manipulate the passengerCount variable. And so it's this connection that we call closure. 

**The closure is then basically this variable environment attached to the function, exactly as it was at the time and place that the function was created.**

**The closure basically has priority over the scope chain.** 

Consider the code below, what will be the output of invoking the function b() ?

```jsx
let a;

const b = function(){
  const c = 23;
  a = function(){
    console.log(c * 2);
  }
}

b() 
```

The above code does not log to the console the value of c * 2.

Only when the function a() is invoked then the value of c * 2 is logged to console. Modified code is below:

```jsx
**let a;

const b = function() {
  const c = 23;
  a = function() {
    console.log(c * 2);
  }
}

b(); // Invoke function b()
a(); // Invoke the function assigned to a**
```

When you run this code, it will log **`46`** to the console, which is the result of **`c * 2`** in the function assigned to **`a`**.

**But Why do I need to call the function a() to see the result of c*2. Should It not be executed when the function b() was invoked?**

In JavaScript, functions are first-class objects, which means they can be assigned to variables and passed around as values. When you assign a function to a variable, such as **`a = function() { ... }`**, you are not immediately executing the function. Instead, you are assigning the function itself to the variable **`a`**.

In the provided code, **`b()`** initializes the variable **`a`** with a new function. However, until you explicitly invoke **`a()`** or call it as a function, the code inside the function will not be executed.

When you call **`a()`** as **`a();`**, it triggers the execution of the function assigned to **`a`**, which then logs the value of **`c * 2`** to the console.

In other words, **`a()`** is necessary to actually execute the code inside the function and see the desired result. Without invoking **`a()`**, the code inside the function will not be executed.

This also reiterates the concept of closures: The function a() has closure over the function b() because the function a() is defined in the execution context of the function b(). Therefore the function a() has access of the variable ‘c’ which is defined in the function b(). 

A variation to the above,  are inbuilt function in JavaScript which are automatically executed without being explicitly invoked. One such example is setTimeout() function. Refer the code below:

```jsx
const boardPassengers = function (n, wait) {
  const perGroup = n / 3;

  setTimeout(function () {
    console.log(`We are now boarding all ${n} passengers`);
    console.log(`There are 3 groups, each with ${perGroup} passengers`);
  }, wait * 1000);

  console.log(`Will start boarding in ${wait} seconds`);
};

const perGroup = 1000; // This is to demonstrate that closure has priority over
// the scope chain. If the perGroup inside the boardPassengers function is not
// created, then the function call to boardPassengers will use the value of 1000
// for number of passengers as it is in the global scope chain. 
// However, when the perGroup variable is created inside the function,that value 
// takes priority over the scope chain value of 1000.
boardPassengers(180, 3);
// We will board in 3 seconds
// We are now boarding all 180 passengers
// There are 3 groups, each with 60 passengers
```

### **Closures can change value after re-assignment**

If we re-assign the value of a child function then the closure of the child function also changes. Refer the code below, the closure of the inner function a() changes and has been highlighted in red below. ( console.dir lists the function properties)

```jsx
let a;

const b = function(){
  const c = 23;
  a = function(){
    console.log(c * 2);
  }
}

const d = function(){
  const e = 777;
  a = function(){
    console.log(e * 2);
  }
}

b()
a() // 46
console.dir(a) 
// a()length: 0
// name: "a"
// prototype: {constructor: ƒ}
// arguments: (...)
// caller: (...)[[FunctionLocation]]: script.js:745
//[[Prototype]]:  Object
//[[Scopes]]: Scopes[0][[Scopes]]: Scopes[3]
	// **0: Closure (b) {c: 23}**
	// 1: Script {a: ƒ, b: ƒ, d: ƒ}
	// 2: Global {window: Window, self: Window, document: document, name: '', location: Location, …}

// Re-assigning value of 'a'
d()
a() // 1554
console.dir(a)
//a()length: 0
// name: "a"
// prototype: {constructor: ƒ}
// arguments: (...)
// caller: (...)[[FunctionLocation]]: script.js:752
// [[Prototype]]: ƒ ()
// [[Scopes]]: Scopes[3]
	// **0: Closure (d) {e: 777}**
	// 1: Script {a: ƒ, b: ƒ, d: ƒ}
	// 2: Global {window: Window, self: Window, document: document, name: '', location: Location, …}
```

# Factory Functions

Factory functions can have different forms depending on the specific requirements of your code and your coding style.

A factory function's primary purpose is to create and return objects, encapsulating the object creation process within a function. The form of the factory function can vary based on how you want to structure your code and what kind of objects you want to create.

Here are a few different forms a factory function can take:

1. **Using Arrow Function with Object Literal:**
    
    ```jsx
    const factoryFunction = (param) => ({
      property: param,
      method: () => {
        // Do something
      }
    });
    
    ```
    
2. **Using Regular Function with Object Literal:**
    
    ```jsx
    function factoryFunction(param) {
      return {
        property: param,
        method: function() {
          // Do something
        }
      };
    }
    
    ```
    
3. **Using Object Creation and Object Linking:**
    
    ```jsx
    function factoryFunction(param) {
      const obj = {};
      obj.property = param;
      obj.method = function() {
        // Do something
      };
      return obj;
    }
    
    ```
    
4. **Using Object.create:**
    
    ```jsx
    function factoryFunction(param) {
      const obj = Object.create(null);
      obj.property = param;
      obj.method = function() {
        // Do something
      };
      return obj;
    }
    
    ```
    
5. **Using Class Inside Factory Function:**
    
    ```jsx
    function factoryFunction(param) {
      class ObjectWithMethod {
        constructor(prop) {
          this.property = prop;
        }
        method() {
          // Do something
        }
      }
      return new ObjectWithMethod(param);
    }
    
    ```
    

All of these forms are valid ways to create a factory function, and you can choose the one that best suits your coding style and the requirements of your project. The key concept is encapsulating object creation and returning objects from a function.

# Single Threaded non concurrency model in JavaScript

In JavaScript, the runtime environment is single-threaded and follows a non-concurrency model. This means that only one task can be executed at a time, and each task must complete before the next one can start.

This model can lead to performance issues when dealing with long-running tasks or heavy computation. To mitigate this, developers often use techniques like asynchronous programming and callbacks to break up tasks into smaller, more manageable chunks.

Asynchronous programming allows tasks to be executed in the background while the main program continues to run. For example, when making an HTTP request to a server, the request is sent asynchronously, allowing the program to continue running while it waits for the response.

Callbacks are functions that are passed as arguments to other functions and are called when the task is complete. They allow for more flexibility in programming and can be used to handle errors or execute code once a task is complete.

Overall, while the single-threaded non-concurrency model in JavaScript can lead to performance issues, it can also be used to write efficient and flexible code.

# JavaScript uses a Just In Time interpretation

A JavaScript engine is a computer program that executes JavaScript code. Every browser has its own JavaScript engine, but the most well-known one is Google's V-Eight, which powers Google Chrome and Node.js. Modern JavaScript engines use just-in-time compilation, which compiles the entire code into machine code at once and then executes it right away. This approach is a lot faster than simple interpretation. Every JavaScript engine always contains a **call stack** and a **heap**. The **call stack** is where our code is actually executed using something called execution contexts. Then the **heap** is an **unstructured memory pool** which stores all the objects that our application needs.

As a piece of JavaScript code enters the engine, the first step is to parse the code into a data structure called the **abstract syntax tree (AST)**. This step also checks for syntax errors, and the resulting tree will later be used to generate the machine code. The next step is **compilation**, which takes the generated AST and compiles it into machine code. This machine code gets executed right away. However there is more to this process as explained below….

Modern JavaScript engines have some pretty clever optimization strategies. They create an unoptimized version of machine code in the beginning just so that it can start executing as fast as possible. Then in the background, this code is being optimized and recompiled during the already running program execution.

A JavaScript runtime is a big container that includes all the things we need to use JavaScript in the browser. The heart of any JavaScript runtime is always a JavaScript engine. In addition to the engine, the runtime includes web APIs, which are functionalities provided to the engine but not part of the JavaScript language itself. The runtime also includes a callback queue, which contains all the callback functions that are ready to be executed. As the event happens, for example a click, the callback function will be called. The event loop takes callback functions from the callback queue and puts them in the call stack so that they can be executed.

Different JavaScript runtimes exist, and they may have slightly different implementations. For example, Node.js JavaScript runtime includes multiple C++ bindings and a thread pool.

In summary, a JavaScript engine executes JavaScript code, and a JavaScript runtime includes a JavaScript engine, web APIs, and a callback queue. Modern JavaScript engines use just-in-time compilation, which is a mix between compilation and interpretation and is a lot faster than simple interpretation.

**CallBack Functions**: Callback functions are functions that are passed as an argument to another function, and are executed after a certain task is completed. They are commonly used in asynchronous programming to handle errors or perform additional actions after an asynchronous operation finishes.

# **Execution Context:**

Steps involved in execution of the code in execution context:

1. Creation of Global Execution context for Top Level code (code outside of functions like variable declarations)

2. User defined functions are not executed till the function call is made.

3. Once the top level code is executed, the functions start to execute..Every time a function call is made a new execution context is created.

4. All the execution context together make up the call stack.

5. **Components of an Execution Context:** Variable environment (arguments, functions, variable declarations), Scope Chain and ‘this’ keyword. Arrow functions do not have the arguments in variable environment and the ‘this’ keyword.

6. The execution context part of the call stack are executed in LIFO. The Global Execution context remains in the call stack till we close the browser.

# **Scoping and Scope Chain**

Scoping controls how a program's variables are organized and accessed by the JavaScript engine. It determines where variables are accessible and where they are not. JavaScript has something called lexical scoping, which means that the way variables are organized and accessed is entirely controlled by the placement of functions and blocks in the program's code.

Scope is the environment in which a variable is declared. In the case of functions, the variable environment is essentially the scope which is stored in the function's execution context. In JavaScript, we have three types of scope: global scope, function scope, and block scope.

Global scope is for top-level code and is for variables declared outside of any function or block. These variables are accessible everywhere in the program.

Each and every function creates a scope, and the variables declared inside that function scope are only accessible inside that function. This is also called a local scope.

Block scopes, created by blocks such as the block of an if statement or a for loop, only apply to variables declared with let or const. Variables declared with var are function-scoped, not block-scoped.

The scope chain is the order in which scopes are searched for a variable. Every scope always has access to all the variables from all its outer scopes, and this is what we call the scope chain. The scope chain only works upwards, not sideways.

Variable lookup is the process by which the engine looks up in the scope chain until it finds the variable it's looking for. It's important to note that the scope chain is a one-way street. A scope will never have access to the variables of an inner scope.

It's important to understand that the order of function calls does not affect the scope chain.

In summary, scoping and the scope chain determine where a variable is accessible, and where it is not. It's important to keep in mind the differences between global scope, function scope, and block scope, as well as the difference between the scope chain and the call stack.

# ‘this’ keyword in JavaScript

- ***this keyword/variable:** is basically a special variable that is created for every execution context and therefore any function.

**this keyword =>** will always take the value of the owner of the function in which, the this keyword is used.

We also say, that it points to the owner of that function.

the value of the **this** keyword is **not static.** So it's not always the same. It depends on how the function is actually called. And its value is only assigned when the function is actually called.

- *But what does that actually mean 🤔? Well, let's analyze four different ways in which functions can be called.

**1. Method:** this = <Object that is calling the method>

So as a function attached to an object. So when we call a method, the this keyword inside that method will simply point to the object on which the method is called.

(it points to the object that is calling the method).

**2. simply calling function as normal functions:** this = undefined

So not as a method and so not attached to any object. In this case, the this keyword, will simply be **undefined**. However, that is only valid for strict mode. So if you're not in strict mode, this will actually point to the global object, which in case of the browser is the window object. And that can be very problematic.

**3. Arrow functions** this = <this of surrounding function (lexical this)>

arrow functions do not get their own 'this keyword'. Instead, if you use 'this.variable' in an arrow function, it will simply be the this keyword of the surrounding function. So of the parent function. and in technical terms, this is called the 'lexical this keyword,' because it simply gets picked up from the outer lexical scope of the arrow function.

**4. Event listener** this = <DOM element that the handler is attached to>

if a function is called as an event listener, then the this keyword will always point to the DOM element that the handler function is attached to.

**=> these are two pretty common misconceptions:**

this keyword will never point to the function in which we are using it.

this keyword will never point to the variable environment of the function.

- ***there are other ways in which we can call a function: new, call, apply, bind:** this keyword points to the window object in three cases:

**a. if the this keyword is outside of any function (just outside in global scope)**

e.g.

```jsx
console.log(this); // Window object {...}
```

**b. If the lexical scope (parent scope) of arrow function is global scope**

e.g.

```jsx
const age = birthYear => {
	console.log(birthYear);
	console.log(this);
 }
age(1990); // 1990

// Window object {...}
```

**c. In case of regular function if you are not using *strict mode***

e.g.

```jsx

const age = function (birthYear) {
 console.log(birthYear);
 console.log(this);
 }; 
 age(1990);
// 1990
// Window object {...}
```

# **The difference between how primitive types and objects are stored in memory in JavaScript.**

When a variable is declared as a primitive type, such as a number or a string, it is stored in the call stack. The call stack is a part of the JavaScript engine responsible for keeping track of function calls and variables. In contrast, objects (like arrays, objects, etc…) are stored in the heap, which is an almost unlimited memory pool where objects can be stored.

When a variable is declared as an object, an identifier is created that points to a piece of memory in the stack, which in turn points to a piece of memory in the heap where the object is actually stored. This is because objects may be too large to be stored in the stack, so they are stored in the heap instead. The stack keeps a reference to where the object is stored in the heap so that it can find it whenever necessary.

One of the key aspects of this difference in storage is that while primitive types are immutable, objects are mutable. When a new variable is set equal to an object, it points to the same memory address as the original object, and any changes made to the object will be reflected in both variables because they both point to the same object in memory. This can cause confusion for beginners, but understanding how primitive types and objects are stored in memory can help clarify this aspect of JavaScript.

The text also highlights the importance of understanding the difference between primitive types and objects, as well as the implications of this difference, especially in practice. It emphasizes that whenever a variable is copied, it only creates a new variable that points to the exact same object. This has huge implications for the way JavaScript works in practice and can help developers avoid common mistakes.

Example given below explain the difference between primitive values and reference values in JavaScript. It begins by showing an example of mutating a primitive value, such as a string, and then copying it to another variable. The example then moves on to discuss objects, which are reference values, and how copying them behaves differently.

Here is an example of mutating a primitive value in JavaScript:

```jsx
let lastName = 'Williams';
let oldLastName = lastName;
lastName = 'Davis';
console.log(lastName); // 'Davis'
console.log(oldLastName); // 'Williams'
```

In this example, we set the **`lastName`** variable to 'Williams' and then copied it to **`oldLastName`**. We then mutated **`lastName`** by setting it to 'Davis'. Finally, we logged both variables to the console and saw that they had different values, as we would expect with primitive values.

An example of creating an object in JavaScript and copying it to another variable:

```jsx
const Jessica = {
  firstName: 'Jessica',
  lastName: 'Williams',
  age: 27
};
const marriedJessica = Jessica;
marriedJessica.lastName = 'Davis';
console.log(Jessica); // { firstName: 'Jessica', lastName: 'Davis', age: 27 }
console.log(marriedJessica); // { firstName: 'Jessica', lastName: 'Davis', age: 27 }

```

In this example, we create an object called **`Jessica`** with properties for first name, last name, and age. We then copy this object to **`marriedJessica`** and mutate the **`lastName`** property of **`marriedJessica`** to 'Davis'. Finally, we log both objects to the console and see that they have the same value for the **`lastName`** property.

The reason for this behavior is that objects are reference values in JavaScript, which means that when we copy an object, we are actually copying a reference to the same object in memory. So when we mutate the **`lastName`** property of **`marriedJessica`**, we are also changing the **`lastName`** property of the original **`Jessica`** object because they both reference the same object in memory.

To create a copy of an object that is not a reference to the same object in memory, we can use the **`Object.assign()`** method or the spread operator. Here's an example using the spread operator:

```jsx

const Jessica = {
  firstName: 'Jessica',
  lastName: 'Williams',
  age: 27
};
const marriedJessica = {...Jessica};
marriedJessica.lastName = 'Davis';
console.log(Jessica); // { firstName: 'Jessica', lastName: 'Williams', age: 27 }
console.log(marriedJessica); // { firstName: 'Jessica', lastName: 'Davis', age: 27 }

```

In this example, we use the spread operator to create a copy of the **`Jessica`** object, which is not a reference to the same object in memory. So when we mutate the **`lastName`** property of **`marriedJessica`**, the **`lastName`** property of the original **`Jessica`** object remains unchanged.

```jsx
const Jessica = {
firstName: 'Jessica',
lastName: 'Williams',
age: 27
};
const marriedJessica = {...Jessica};
marriedJessica.lastName = 'Davis';
console.log(Jessica); // { firstName: 'Jessica', lastName: 'Williams', age: 27 }
console.log(marriedJessica); // { firstName: 'Jessica', lastName: 'Davis', age: 27} }
```

In this example, we use the spread operator to create a copy of the **`Jessica`** object, which is not a reference to the same object in memory. So when we mutate the **`lastName`** property of **`marriedJessica`**, the **`lastName`** property of the original **`Jessica`** object remains unchanged.

# Arrays

### Array indexing

In JavaScript, arrays are a special type of object, and the keys of an array are essentially string representations of the indices. When you use bracket notation to assign a value to an array element, JavaScript converts the index to a string and treats it as an object property.

```jsx
const myArr = [1,2,3,4,5]
myArr[myArr.length] = 6;
myArr[-1] = 7;
console.log(myArr);
```

Let's break down the code step by step to understand the behavior:

1. **`const myArr = [1, 2, 3, 4, 5]`**: Initializes an array **`myArr`** with elements **`[1, 2, 3, 4, 5]`**.
2. **`myArr[myArr.length] = 6;`**: This line sets the value at the index **`myArr.length`**, which is equivalent to **`myArr[5]`**, to **`6`**. The array now becomes **`[1, 2, 3, 4, 5, 6]`**.
3. **`myArr[-1] = 7;`**: This line sets the value at the index **`1`** to **`7`**. In JavaScript, when you use a negative index or a non-integer index, it gets converted to a string representation of the index. So, **`1`** gets converted to **`"-1"`**, and the array now becomes **`[1, 2, 3, 4, 5, 6, "-1": 7]`**.

The **`myArr`** array is now a sparse array because it has a non-sequential index (**`"-1"`**) in addition to the sequential indices. The array still has a length of **`6`** (since the highest sequential index is **`5`**), but it also has a property with the key **`"-1"`**.

When you log the **`myArr`**, it displays the array elements as usual, but it also shows the additional property with the key **`"-1"`** and its value **`7`**, which is why you see the output as **`[1, 2, 3, 4, 5, 6, "-1": 7]`**.

However, it's important to note that accessing elements using negative or non-integer indices is generally not recommended in JavaScript, as it can lead to confusion and unexpected behavior. It's best to stick to the conventional positive integer indices when working with arrays.

### **Array slice**

The **`slice()`** method in JavaScript is used to extract a portion of an array and return it as a new array. It doesn't modify the original array; instead, it creates a shallow copy of the selected elements.

The syntax of the **`slice()`** method is as follows:

```jsx
array.slice(startIndex, endIndex)
```

- **`startIndex`** (optional): An integer that specifies where to begin the extraction. It is the index at which the extraction starts. If **`start`** is omitted, **`slice()`** will start from the beginning (index 0) of the array. If **`start`** is negative, it represents an index from the end of the array, with **`-1`** being the last element.
- **`endIndex`** (optional): An integer that specifies where to end the extraction. It is the index at which the extraction ends. The **`slice()`** method extracts up to, but does not include, the element at the index specified by **`end`**. If **`end`** is omitted, **`slice()`** extracts all the elements from **`start`** to the end of the array. Like **`start`**, if **`end`** is negative, it represents an index from the end of the array.
    
    The **`slice()`** method returns a new array containing the extracted elements. The original array remains unchanged.
    
    ```jsx
    const fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry'];
    
    // Extract a portion of the array
    const slicedFruits = fruits.slice(1, 4);
    console.log(slicedFruits); // Output: ['banana', 'cherry', 'date']
    
    // Extract from the third element to the end
    const slicedFruits2 = fruits.slice(2);
    console.log(slicedFruits2); // Output: ['cherry', 'date', 'elderberry']
    
    // Extract the last two elements
    const slicedFruits3 = fruits.slice(-2);
    console.log(slicedFruits3); // Output: ['date', 'elderberry']
    
    // Original array remains unchanged
    console.log(fruits); // Output: ['apple', 'banana', 'cherry', 'date', 'elderberry']
    ```
    

In the first example, **`slice(1, 4)`** extracts elements from index 1 to index 3, resulting in **`['banana', 'cherry', 'date']`**.

In the second example, **`slice(2)`** extracts elements from index 2 to the end of the array, resulting in **`['cherry', 'date', 'elderberry']`**.

In the third example, **`slice(-2)`** extracts the last two elements of the array, resulting in **`['date', 'elderberry']`**.

Lastly, note that the original array **`fruits`** remains unchanged after calling **`slice()`**.

### Array - Shallow Copy

The slice method can be used to create a shallow copy of the existing array. Refer the code below:

```jsx
const arr1 = [10,11,12,13,14,15];
const arr2 = arr1.slice();
console.log(arr2) // [10,11,12,13,14,15]
```

### **Array splice**

The **`splice()`** method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place, meaning that the original array itself is modified.

To create a new array with a segment removed and/or replaced without mutating the original array, use [`toSpliced()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toSpliced).

Array splice can be used for the following:

- Deleting elements from an array
- splitting an array based on some condition
- adding new elements to an array
- inserting new elements into an existing array

```jsx
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2, itemN)
```

`start`: Zero-based index at which to start changing the array, converted to an integer.
• Negative index counts back from the end of the array — if `start < 0`, `start + array.length`is used, for e.g if start = -1, and array.length = 4, then `start + array.length` = 3 which is the index of the last element of the array. 
• If `start < -array.length`, `0` is used.
• **If `start >= array.length`, no element will be deleted, but the method will behave as an adding function, adding as many elements as provided.**

```jsx
const months = ['Jan', 'March', 'April', 'June'];
// start is greater than array length
// as per the sequence of arguments, the next argument has to be the deleteCount
// by specifying it as zero, we ensire that no element is deleted
// and the next element is added at the startIndex position. 
months.splice(5, 0, 'July'); 
console.log(months); // ['Jan', 'March', 'April', 'June', 'July']
```

• If `start` is omitted (and `splice()` is called with no arguments), nothing is deleted. This is different from passing `undefined`, which is converted to `0`.

`deleteCount`: (Optional) An integer indicating the number of elements in the array to remove from `start`. If `deleteCount` is omitted, or if its value is greater than or equal to the number of elements after the position specified by `start`, then all the elements from `start` to the end of the array will be deleted. However, if you wish to pass any `itemN` parameter, you should pass `Infinity` as `deleteCount` to delete all elements after `start`, because an explicit `undefined` gets [converted](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion) to `0`.

If `deleteCount` is `0` or negative, no elements are removed. In this case, you should specify at least one new element (see below).

`item1`, …, `itemN`: (Optional) The elements to add to the array, beginning from `start`.
If you do not specify any elements, `splice()` will only remove elements from the array.

### [Return value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#return_value)

An array containing the deleted elements.

If only one element is removed, an array of one element is returned.

If no elements are removed, an empty array is returned.

### **Array reverse**

This is used to reverse the array. **The reverse method changes the original array to its reversed form**

```jsx
const myArr = ['a','b','c','d','e'];
console.log(myArr.reverse()); //['e', 'd', 'c', 'b', 'a']
```

**To reverse an array without changing the original array, use the toReversed() method.**

```jsx
const myArr = ['a','b','c','d','e'];
console.log(myArr.toReversed()) //['e', 'd', 'c', 'b', 'a']
console.log(myArr); // ['a', 'b', 'c', 'd', 'e']
```

### **Array concat**

Used for concatenating two arrays.

```jsx
const months1 = ['Jan','Feb','Mar'];
const months2 = ['Apr','May','Jun'];
const concatArr = months1.concat(months2) //['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
```

Alternatively, the spread operator can also be used to concat two arrays

```jsx
const concatArr = [...months1, ...months2]
```

### **Arrays ‘at’ method**

The ‘at’ method of arrays is used for accessing elements of the array based on the index provided.

```jsx
const months1 = ['Jan','Feb','Mar'];
console.log(months1.at(0)) //  Jan
console.log(months1.at(-1)) // Mar
```

### **Find method**

The **`find()`** method in JavaScript is used to find the first element in an array that satisfies a specified condition. It iterates over each element of the array and **returns the first element** for which the provided callback function returns **`true`**, or **`undefined`** if no such element is found.

Here's the syntax of the **`find()`** method:

```jsx
array.find(callback function)
```

The **`callback`** function takes three parameters: **`element`**, **`index`**, and **`array`**. It performs a condition check on the **`element`** and returns **`true`** or **`false`** based on that condition. If the callback function returns **`true`** for an element, that element is returned by the **`find()`** method.

Here's an example that demonstrates the usage of **`find()`** to find the first even number from an array:

```jsx

const numbers = [1, 2, 3, 4, 5, 6];

const firstEvenNumber = numbers.find(function(element) {
  return element % 2 === 0;
});

console.log(firstEvenNumber); // Output: 2
```

### FindIndex Method

The **`findIndex()`** method in JavaScript is used to find the index of the first element in an array that satisfies a given condition. It takes a callback function as an argument, which is executed for each element in the array until a match is found.

The syntax of the **`findIndex()`** method is as follows:

```jsx
array.findIndex(callback(element, index, array), thisArg)
```

- **`array`**: The array on which **`findIndex()`** is called.
- **`callback`**: A function that is executed for each element in the array. It can take three parameters:
    - **`element`**: The current element being processed in the array.
    - **`index`** (optional): The index of the current element being processed.
    - **`array`** (optional): The array on which **`findIndex()`** is called.
- **`thisArg`** (optional): A value to use as **`this`** when executing the callback function.

The **`findIndex()`** method returns the index of the first element that satisfies the condition specified in the callback function. If no element satisfies the condition, it returns -1.

Here's an example to illustrate the usage of **`findIndex()`**:

```jsx

const numbers = [2, 4, 6, 8, 10];

const index = numbers.findIndex(function(element) {
  return element > 5;
});

console.log(index); // Output: 2

```

In this example, the **`findIndex()`** method searches for the first element in the **`numbers`** array that is greater than 5. It finds that element at index 2 (value 6), so it returns 2 as the output.

Note that if you want to find the element itself rather than its index, you can use the **`find()`** method instead of **`findIndex()`**.

### Looping through Arrays - The for-of loop

The for-of loop is very helpful in looping through arrays. It provides us ways to access the index position and the element value of the array elements.

Example: 

```jsx
const arr = [10, 20, 30];
for (const i of arr){
console.log(i) // 10,20,30
}

```

To obtain the index position and the values together, we need to use array deconstruction as given below:

```jsx
const arr = [11, 22, 33];
for (const [index, value] of arr.entries()){
	console.log(index,value) 
}
// Output is:
0 11
1 22
2 33
```

### forEach method for Arrays

The **`forEach()`** method is a built-in method available for arrays in JavaScript. It provides an easy way to iterate over each element of an array and perform a specified action or function on each element.

The **`forEach()`** method takes a callback function as its argument. This callback function is executed once for each element in the array in ascending order. The callback function can take up to three arguments:

1. **`currentValue`**: The current element being processed in the array.
2. **`index`** (optional): The index of the current element being processed.
3. **`array`** (optional): The array that **`forEach()`** is being applied to.

Here's an example to demonstrate the usage of **`forEach()`**:

```jsx
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(currentValue, index, array) {
  console.log(`Element at index ${index}: ${currentValue}`);
});

// Output:
// Element at index 0: 1
// Element at index 1: 2
// Element at index 2: 3
// Element at index 3: 4
// Element at index 4: 5
```

**Disadvantage of forEach loop** - You cannot break out of the loop using break and continue statements. The forEach loop will run the complete loop, so in case it is required to break out of the loop in case of any particular condition being met or not being met we should use the for-of loop.

**forEach() always returns undefined** so the following code will always return undefined:

```jsx
const numbers = [1,2,3]
let x = numbers.forEach(function(ele) { return ele * 2})
console.log(x) // undefined

```

### forEach() method for Maps and Sets

In the context of **`Map`** objects, the **`forEach()`** method works similarly to arrays, but with some differences in the callback function signature.

In the code example, you have a **`Map`** called **`currencies`** that maps currency codes to their corresponding names. Here's an explanation of how the **`forEach()`** method is used with **`Map`** objects:

```jsx
const currencies = new Map([
  ['INR', 'Indian Rupees'],
  ['USD', 'United States Dollar'],
  ['EUR', 'Euro'],
  ['GBP', 'Pound Sterling']
]);

console.log(currencies)

// the first argument to be passed is the value of the map, followed by the value
currencies.forEach(function(value, key) {
  console.log(`The currency for ${key} is: ${value}`);
});
```

The **`forEach()`** method is called on the **`currencies`** map object. It takes a callback function as an argument, which is executed once for each entry in the map. The callback function can take up to three arguments:

1. **`value`**: The value of the current entry in the map.
2. **`key`**: The key of the current entry in the map.
3. **`map`**: The map object that **`forEach()`** is being applied to (optional).

In the example above, the callback function logs a message to the console for each entry in the **`currencies`** map. The message includes the key (currency code) and the value (currency name) using string interpolation.

The output of the code will be:

```jsx
Map(4) {
  'INR' => 'Indian Rupees',
  'USD' => 'United States Dollar',
  'EUR' => 'Euro',
  'GBP' => 'Pound Sterling'
}
The currency for INR is: Indian Rupees
The currency for USD is: United States Dollar
The currency for EUR is: Euro
The currency for GBP is: Pound Sterling
```

As you can see, the **`forEach()`** method iterates over each entry in the **`currencies`** map and executes the callback function for each entry, providing the key and value as arguments.

It's important to note that the order of iteration in **`Map`** objects is based on the insertion order. This means that the entries will be processed in the same order they were added to the map.

**forEach() method for Sets:**

The **`forEach()`** method works slightly differently with **`Set`** objects compared to **`Map`** objects. In a **`Set`**, there are no keys and values like in a **`Map`**, so the callback function passed to **`forEach()`** will only receive the value of each element in the set. Here's an example:

```jsx
const currencies = new Set([
  'Indian Rupees',
  'United States Dollar',
  'Euro',
  'Pound Sterling'
]);

console.log(currencies);

currencies.forEach(function(value) {
  console.log(`Currency: ${value}`);
});

// -------------------- Output ----------------------------------//
/* 
Set(4) {
  'Indian Rupees',
  'United States Dollar',
  'Euro',
  'Pound Sterling'
}
Currency: Indian Rupees
Currency: United States Dollar
Currency: Euro
Currency: Pound Sterling 
*/
```

As you can see, the callback function is called for each element in the set, and it receives the value of the element as the argument. In this case, the callback function logs a message to the console for each currency name.

It's important to note that the iteration order of elements in a **`Set`** is based on the order of insertion, similar to **`Map`**. However, unlike in **`Map`**, there is no concept of keys in a **`Set`**, so the order of iteration is based solely on the insertion order of the elements.

The **`forEach()`** method is a convenient way to iterate over elements in a **`Set`** and perform operations on each element.

### Map, Filter and Reduce methods for Arrays

**Map**: map is actually similar to the forEach method that we studied before but with the difference that map creates a brand new array based on the original array. So essentially the map method takes an array, loops over that array and in each alteration,it applies a callback function that we specify on our code to the current array element.

```jsx
const myfunc = function(arr1){
  const myvar = [...arr1].slice(1,3)
  return myvar.map((element) => element * 2);
};

const output = myfunc([10,20,30,40,50]);
console.log(output); // [40,60]
```

**Filter**: The **`filter()`** method in JavaScript is used to create a new array containing elements from the original array that satisfy a certain condition. It iterates over each element of the array and checks if the element meets the specified condition. If the condition is true, the element is included in the new array; otherwise, it is excluded.

Here's the syntax of the **`filter()`** method:

```jsx
array.filter(callback(element, index, array))
```

The **`callback`** function takes three parameters: **`element`**, **`index`**, and **`array`**. It performs some condition check on the **`element`** and returns **`true`** or **`false`** based on that condition. If the callback function returns **`true`**, the element is included in the new array; if it returns **`false`**, the element is excluded.

Here's an example that demonstrates the usage of **`filter()`** to filter out even numbers from an array:

```jsx
const numbers = [1, 2, 3, 4, 5, 6];

const evenNumbers = numbers.filter(function(element) {
  return element % 2 === 0;
});

console.log(evenNumbers); // Output: [2, 4, 6]
```

In the code above, the **`filter()`** method is used on the **`numbers`** array. The callback function checks if each element is divisible by 2 (**`element % 2 === 0`**) to determine if it's an even number. If the condition is true, the element is included in the **`evenNumbers`** array.

After iterating over all the elements of the array, the **`filter()`** method returns a new array containing only the elements that satisfy the condition, in this case, the even numbers.

**Note that the `filter()` method does not modify the original array. It creates and returns a new array based on the filtering condition.**

**Reduce**: The **`reduce()`** method in JavaScript is used to iterate over an array and accumulate a single value based on the elements of the array. It executes a callback function on each element of the array, taking four arguments: accumulator, current value, current index, and the array itself.

Here's the syntax of the **`reduce()`** method:

```jsx
array.reduce(callback function, initialValue)
```

The **`callback`** function takes two parameters: the **`accumulator`** and the **`currentValue`**. It performs some operation on the **`accumulator`** and the **`currentValue`** and returns the updated value of the **`accumulator`**.

The **`initialValue`** is an optional parameter that specifies the initial value of the **`accumulator`**. If not provided, the first element of the array is used as the initial value and the iteration starts from the second element.

Here's an example that demonstrates the usage of **`reduce()`** to calculate the sum of all elements in an array:

```jsx
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce(function(accumulator, currentValue) {
  return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15
```

In the code above, the **`reduce()`** method is used on the **`numbers`** array. The callback function takes two arguments: **`accumulator`** and **`currentValue`**. It adds the **`currentValue`** to the **`accumulator`** and returns the updated value. The initial value of the **`accumulator`** is set to **`0`** using the second argument of **`reduce()`**.

After iterating over all the elements of the array and performing the addition operation, the **`reduce()`** method returns the final accumulated value, which in this case is the sum of all the numbers in the array.

### Using the reduce method to update object properties

```jsx
const sums = accounts.flatMap(acc => acc.movements).reduce((sum,curr) =>{
    curr > 0 ? sum.deposit += curr : sum.withdrawal += curr;
    return sum;},
    {deposit: 0, withdrawal: 0});

console.log(sums);
```

In the provided code, the **`reduce`** method is used to update the properties of an object ‘sums’. The first parameter of the **`reduce`** method is a callback function that takes two parameters: the accumulator (**`sum`**) and the current value (**`curr`**) from the array being reduced.

In this case, the initial value of the accumulator is an object **`{deposit: 0, withdrawal: 0}`**. The callback function is executed for each element of the array, and the returned value is used as the new accumulator for the next iteration.

Inside the callback function, the properties of the **`sum`** object are accessed and modified based on the value of **`curr`**. If **`curr`** is greater than 0, it means it's a deposit and the **`deposit`** property of **`sum`** is incremented by **`curr`**. Otherwise, if **`curr`** is less than 0, it means it's a withdrawal and the **`withdrawal`** property of **`sum`** is incremented by **`curr`**.

The updated **`sum`** object is then returned from the callback function and becomes the accumulator for the next iteration. Finally, the resulting **`sum`** object with the updated **`deposit`** and **`withdrawal`** properties is assigned to the **`sums`** variable.

So, the first parameter of the **`reduce`** method, which is the accumulator (**`sum`**), behaves like an object and allows you to access and update its properties within the callback function. The **`reduce`** method automatically passes the accumulator value to the callback function in each iteration, allowing you to perform the necessary calculations and modifications.

A variation to the above code (which does not work) can be written as :

```jsx
let sumsObj = {deposit:0, withdrawal:0};

const arr = accounts.flatMap((acc) => acc.movements);

sumsObj = arr.reduce((sums,curr) => {
       if (curr >= 0){
            sums.deposit += curr};
       if (curr < 0){
           sums.withdrawal += curr};
       return sums;
});
console.log(sumsObj.deposit, sumsObj.withdrawal);
```

The issue in your modified code is with the assignment inside the **`reduce`** callback function. In the original code, you were directly updating the properties of the **sums** object, whereas in your modified code, you are assigning a new object to the **`sumsObj`** variable in each iteration.

When you assign a new object to **`sumsObj`** within the **`reduce`** callback, it no longer maintains the reference to the original **`sumsObj`** object. As a result, the **`console.log`** statement outside the **`reduce`** loop will print **`undefined`** for both **`sumsObj.deposit`** and **`sumsObj.withdrawal`**.

To fix this, you can modify your code to update the properties of **`sumsObj`** instead of reassigning a new object. Here's the corrected code:

```jsx
let sumsObj = { deposit: 0, withdrawal: 0 };

const arr = accounts.flatMap((acc) => acc.movements);

sumsObj = arr.reduce((sums, curr) => {
  if (curr >= 0) {
    sums.deposit += curr;
  }
  if (curr < 0) {
    sums.withdrawal += curr;
  }
  return sums;
}, sumsObj); // Pass the initial sumsObj as the second parameter

console.log(sumsObj.deposit, sumsObj.withdrawal);
```

### Chaining Methods

It is possible to apply multiple methods in a single expression in JS. The only consideration is the return value and type that each of the methods return. For example if a method returns a single value then it cannot be chained with a method which needs an array as an input. Consider the following example, which does the following: **Take the movement array, collect all the deposit data, convert all deposits into USD, add all deposit value**

```jsx
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
const output = movements.filter((move) => move > 0).map((move) => move * 1.08).reduce((acc, curr) => acc + curr,0);
console.log(`The output value is : ${output}`); // The output value is : 5421.6
```

### ‘Some’ method for arrays

 

The **`some()`** method in JavaScript is used to check if at least one element in an array satisfies a given condition. It iterates over the array and executes a callback function for each element until a match is found.

The syntax of the **`some()`** method is as follows:

```jsx
array.some(callback(element, index, array), thisArg)
```

- **`array`**: The array on which **`some()`** is called.
- **`callback`**: A function that is executed for each element in the array. It can take three parameters:
    - **`element`**: The current element being processed in the array.
    - **`index`** (optional): The index of the current element being processed.
    - **`array`** (optional): The array on which **`some()`** is called.
- **`thisArg`** (optional): A value to use as **`this`** when executing the callback function.

The some() method returns a boolean value as output. The **`some()`** method returns **`true`** if at least one element satisfies the condition specified in the callback function. If none of the elements satisfy the condition, it returns **`false`**.

Here's an example to illustrate the usage of **`some()`**:

```jsx
const numbers = [1, 3, 5, 7, 9];

const hasEvenNumber = numbers.some(function(element) {
  return element % 2 === 0;
});

console.log(hasEvenNumber); // Output: false
```

In this example, the **`some()`** method checks if there is at least one even number in the **`numbers`** array. Since there are no even numbers, it returns **`false`** as the output.

The **`some()`** method is useful when you want to determine if there is any element in an array that satisfies a certain condition without having to iterate over the entire array manually.

### ‘Every’ Method for Arrays

The every() method returns a boolean true or false depending upon the condition provided to it for checking in the array. If all the array entries match the condition only then the every() method returns true, otherwise it returns false.

Example of usage of every method:

```jsx
const movements = [100, -20, 1000, -400, 2000, 3000];

const allDeposit = movements.every((mov) => mov > 0) // false

const even = [2,4,6,8,10,12,14]

const checkEven = even.every((num) => num % 2 === 0) 
console.log(checkEven); // true

```

### **`flat()` method**

The **`flat()`** method is used to flatten a nested array by concatenating all sub-arrays into a single array. It creates a new array with all the elements from the original array and flattens any nested arrays to the specified depth.

The syntax of the **`flat()`** method is as follows:

```jsx
array.flat(depth)
```

- **`array`**: The array to be flattened.
- **`depth`** (optional): The depth level specifying how deep nested arrays should be flattened. The default value is 1 and a value of 2 can be also given. However flat() does not work for depth above 2, so this means that more than 2 levels of nesting in an array cannot be handled by flat().

Here's an example to illustrate the usage of **`flat()`**:

```jsx
const nestedArray = [1, [2, 3], [4, [5, 6]]];

const flattenedArray = nestedArray.flat();

console.log(flattenedArray); // Output: [1, 2, 3, 4, 5, 6]
```

In this example, the **`flat()`** method is called on the **`nestedArray`** to flatten it into a single array.

1. **`flatMap()`**: The **`flatMap()`** method is a combination of **`map()`** and **`flat()`** methods. It first applies a mapping function to each element of an array and then flattens the result into a new array.

The syntax of the **`flatMap()`** method is as follows:

```jsx
array.flatMap(callback(element, index, array), thisArg)
```

- **`array`**: The array on which **`flatMap()`** is called.
- **`callback`**: A function that is executed for each element in the array. It can take three parameters:
    - **`element`**: The current element being processed in the array.
    - **`index`** (optional): The index of the current element being processed.
    - **`array`** (optional): The array on which **`flatMap()`** is called.
- **`thisArg`** (optional): A value to use as **`this`** when executing the callback function.

Here's an example to illustrate the usage of **`flatMap()`**:

```jsx
const numbers = [1, 2, 3, 4, 5];

const mappedAndFlattened = numbers.flatMap(function(element) {
  return [element, element * 2];
});

console.log(mappedAndFlattened); // Output: [1, 2, 2, 4, 3, 6, 4, 8, 5, 10]
```

In this example, the **`flatMap()`** method applies the callback function to each element of the **`numbers`** array. The callback function returns an array with the element and its double. The result is a flattened array with the mapped elements.

The **`flat()`** and **`flatMap()`** methods are useful when working with nested arrays or when you need to transform and flatten arrays in a single operation.

### Array sorting methods

The `sort()` method sorts an array alphabetically

```jsx
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort(); // Apple,Banana,Mango,Orange
```

By default, the `sort()` function sorts values as **strings**.

This works well for strings ("Apple" comes before "Banana").

However, if numbers are sorted as strings, "25" is bigger than "100", because "2" is bigger than "1".

Because of this, the `sort()` method will produce incorrect result when sorting numbers.

You can fix this by providing a **compare function**

**Compare Function**: The purpose of the compare function is to define an alternative sort order.

The compare function should return a negative, zero, or positive value, depending on the arguments:

When the `sort()` function compares two values, it sends the values to the compare function, and sorts the values according to the returned (negative, zero, positive) value.

If the result is negative, `a` is sorted before `b`.

If the result is positive, `b` is sorted before `a`.

If the result is 0, no changes are done with the sort order of the two values.

Refer the code below to understand how an array is sorted in ascending and descending order:

```jsx
const myArr = [10, 20, 25 , 12, 89, 67, 34, 77, 46];

// comparison function for descending order
const compare = function(a,b){
    return b-a;
}

myArr.sort(compare);
console.log(myArr);

// comparison function for ascending order
const compare1 = function(c,d){
    return c-d;
}
myArr.sort(compare1);
console.log(myArr);
```

### Creating Arrays programmatically

Arrays can be created programmatically using the following methods:

- using the Array constructor. This creates an array of empty elements which can be filled using the fill method.

```jsx
const newArr = new Array(5) // creates an array with 5 empty elements
```

- using the fill method to add values to an empty array. Syntax for fill() method is given below

```jsx
array.fill(value, startIndex, endIndex) // value is the number to be filled
// startIndex is included and endIndex is excluded 

newArr.fill(1,2,6) // [empty,empty,1,1,1]

```

- from() method to generate array:

```jsx
array.from({length: num}, callback function)

// Generate a function with length 100, for random dice roll
const diceThrow = Array.from({length:100},function()
	{ 
	  const min = 1;
	  const max = 7;
	  output = (Math.floor(Math.random() * (max-min)) + min)
	  return output;
   });
```

### Which Array method to use

![JS_array_methods.jpg](JavaScript%204a27e97c98354d158f8da9e5693124ac/JS_array_methods.jpg)

# **Destructuring in JavaScript**

Destructuring is a feature in JavaScript that allows you to extract values from arrays or objects and assign them to variables in a more concise way.

## Array Destructuring

Destructuring is a powerful feature in JavaScript that can be used to simplify code and make it more readable. It allows for easily unpacking values from arrays or objects into separate variables, making it easier to work with complex data structures.

With destructuring, it is possible to retrieve elements from an array and store them into variables in a very easy way. This is done by using square brackets and declaring variables for each element. This makes it much simpler to work with arrays, as retrieving elements no longer requires writing out the full syntax.

Destructuring allows us to unpack values from arrays or objects into separate variables. This means that we can break down a complex data structure into a smaller data structure like a variable. When we want to retrieve elements from an array and store them into variables, destructuring is very useful. 

For instance, given an array [2, 3, 4], without destructuring, we would assign variables like 

**`let a = arr[0]; let b = arr[1]; let c = arr[2];`** to retrieve the elements of the array. However, with destructuring, we can assign all the variables at once using a syntax like 

**`const [x, y, z] = arr;`**.

Here's the code for these examples:

```jsx
// Assigning array elements to different variables - TRADITIONAL METHOD
const arr = [2, 3, 4];
let a = arr[0];
let b = arr[1];
let c = arr[2];
console.log(a, b, c); // 2 3 4

```

```jsx
// Using array destructuring to assign array values to variables
const [x, y, z] = arr;
console.log(x, y, z); // 2 3 4
```

```jsx
// Destructuring in case one of the value from the array has to be ommitted
// In such a case, we leave a space in between the array destructure
const arr = [2,3,4];
const [first, , third] = arr;
console.log(first, third); // 2 4
```

Destructuring can also be used to switch variable values, which can be very useful in certain scenarios. Without destructuring, switching two variables would require creating a temporary variable to store the value of one variable before swapping it with the other. However, with destructuring, it is possible to switch variables by creating an array with the two variables inverted and then destructuring it. This makes the code much more concise and easier to read.

Here's an example of switching variable values using the traditional method of creating an intermediate variable:

```jsx
let a = 5;
let b = 10;

let temp = a;
a = b;
b = temp;

console.log(a); // 10
console.log(b); // 5
```

Here's an example of **switching variable values using array destructuring:**

```jsx

let b = 10;

[a, b] = [b, a];

console.log(a); // 10
console.log(b); // 5
```

As you can see, the second method using array destructuring is much more concise and easier to read. It also does not require the creation of an intermediate variable.

Another use of destructuring is to **return multiple values from a function**. This can be done by having the function return an array, which can then be destructured into different variables. This is a very handy way of creating multiple variables out of one function call, and it can simplify code significantly.

Here's an example of how array destructuring can be used to return multiple values from a function:

```
function getValues() {
  return [1, 2, 3];
}

const [a, b, c] = getValues();

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3

```

In this example, the `getValues` function returns an array of three values. When the function is called and assigned to a variable using destructuring, each value in the array is automatically assigned to a separate variable. This allows for multiple values to be returned from a function in a concise and readable way.

***Note that the number of variables used in the destructuring assignment must match the number of values returned by the function. Otherwise, an error will be thrown.***

Destructuring can also be used to handle nested arrays. In this case, destructuring is done inside of destructuring, allowing for individual values to be extracted from nested arrays. This can be a bit more complex, but it allows for more granular control over the data.

```jsx
const nestedArr = [1, [2, 3], 4];
const [a, [b, c], d] = nestedArr;
console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
console.log(d); // 4
```

In this example, we have an array **`nestedArr`** with three elements, where the second element is another array. We want to extract each element of **`nestedArr`** into separate variables using array destructuring. To do this, we declare three variables **`a`**, **`[b, c]`**, and **`d`**, and assign them to **`nestedArr`** using the square bracket notation.

Notice that we're using nested destructuring for the second element of **`nestedArr`**, which is an array itself. By wrapping **`[b, c]`** in square brackets, we're destructuring the second element of **`nestedArr`** into two separate variables, **`b`** and **`c`**.

Finally, default values can be set for variables when using destructuring. This can be very useful in cases where the length of the array is unknown or shorter than expected. Setting default values ensures that the code will not break if the array is shorter than anticipated, and it can help to make code more robust.

```jsx
const [p,q,r] = [8,9]; // the variable r does not have any value for assignment 
// in case no value is available for assignment, then the variable is assigned a 
// value of undefined
console.log(r) // undefined
// To prevent this from happening, default values can be assigned:
const [p = 0, q = 0, r = 1] = [8,9]
console.log(p, q, r) // 8 9 1

```

## Object Destucturing

Object destructuring is a useful feature in JavaScript that allows you to extract specific properties from an object and store them in variables. You can use curly braces to destructure an object, and provide variable names that match the property names you want to retrieve. The order of the elements in an object does not matter, so you don't need to skip elements manually like you would in an array.

```jsx
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],

  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // Open 24 hours
      close: 24,
    }
  },
  orderPizza: function(mainIngredient, ...otherIngredient){
    return (mainIngredient)
    // console.log(otherIngredient)
  },
  orderPasta(ing1, ing2, ing3) {
    console.log(
      `Here is your declicious pasta with ${ing1}, ${ing2} and ${ing3}`
    );
  },
  order: function(starterIndex, mainIndex){
    return (this.starterMenu[starterIndex], this.mainMenu[mainIndex])
  }, 
	orderDelivery: function(obj){
		console.log(obj)
	}
};
```

For example, using the  **`restaurant`** object from above with properties like **`name`**, **`location`**, **`categories`**, and **`openingHours`**. You can use object destructuring to extract specific properties like so:

```jsx
// The curly braces are used for object destructuring
const { name, openingHours, categories } = restaurant;
```

This will create three variables **`name`**, **`openingHours`**, and **`categories`**, and assign them the corresponding values from the **`restaurant`** object.

You can also rename the variables to something else using the colon **`:`** notation. For example:

```jsx
const {name: restaurantName, openingHours: hours, categories: tags} = restaurant;
```

This will create variables **`restaurantName`**, **`hours`**, and **`tags`**, and assign them the values of **`name`**, **`openingHours`**, and **`categories`**, respectively.

### Setting default value

In addition, you can set default values for properties that may not exist in the object. This is useful when dealing with third-party data from an API call, where some properties may not exist. For example:

```jsx
const { menu = [], starterMenu: starters = [] } = restaurant;
```

This will create variables **`menu`** and **`starters`**, and assign them the values of **`restaurant.menu`** and **`restaurant.starterMenu`**, respectively. If **`menu`** does not exist in the **`restaurant`** object, it will default to an empty array. Similarly, if **`starterMenu`** does not exist, it will default to an empty array and be assigned to the **`starters`** variable.

### **Mutating variable values using objects**

Similar to how variable values can be exchanged in array destructuring, we can perform the same operation using objects, with the only change that the expression needs to be enclosed in parenthesis:

```jsx
let a = 111;
let b = 222;
// the variable names inside the object have to be the same as the ones whose value
// needs to be swapped. Otherwise 'undefined' is returned.
const obj = {a:23, b: 7, c: 10}; 
({a, b} = obj) // parenthesis is a must, otherrwise it results in error.
console.log(a,b)
```

### **Nested Object destructuring**

In the restaurant object defined above, the property openingHours is inside of the object restaurant and it further has two additional properties: open and close. Now if we want to access the open and close property of Friday, we can do it by: 

```jsx
// for the JS engine to identify that we are looking for friday the left variable
// needs to have the same name as the original variable present in the object
const {fri} = restaurant.openingHours;
console.log(fri) // {open: 11, close: 23}
```

If we want to destructure this even further and access the open and close variables only, then this can be done as depicted below:

```jsx
// basically we destructure the friday object further by using the colon(:) and
// curly braces({}). Additionally the original variable names of open and close 
// can be changed as depicted below to 'o' and 'c' using the colon(:) operator.
const {fri: { open: o, close: c }} = openingHours;
console.log(o, c);
```

### Passing object as parameter to object methods which are functions

Consider the orderDelivery method from the restaurant object defined below:

```jsx
const restaurant = {
name: 'Classico Italiano',
location: 'Via Angelo Tavanti 23, Firenze, Italy',
categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
mainMenu: ['Pizza', 'Pasta', 'Risotto'],
openingHours: {
thu: {
open: 12,
close: 22,
},
fri: {
open: 11,
close: 23,
},
sat: {
open: 0, // Open 24 hours
close: 24,
}
},
orderPizza: function(mainIngredient, ...otherIngredient){
return (mainIngredient)
// console.log(otherIngredient)
},
orderPasta(ing1, ing2, ing3) {
console.log(
Here is your declicious pasta with ${ing1}, ${ing2} and ${ing3}
);
},
order: function(starterIndex, mainIndex){
return (this.starterMenu[starterIndex], this.mainMenu[mainIndex])
},
**orderDelivery**: function(obj){
console.log(obj)
}
};
```

The orderDelivery method is a function which takes an object as a parameter. When the object is passed as a parameter, the function immediately destructures the object. Example is given below:

```jsx
restaurant.orderDelivery({
  time: '22:30',
  address: 'Via del Sole, 21',
  mainIndex: 2,
  starterIndex: 2,
});

// The above function call returns :
// {time: '22:30', address: 'Via del Sole, 21', mainIndex: 2, starterIndex: 2}
```

This way of destructuring objects is very useful when handling API related data.

# Spread and Rest operator in JavaScript

In JavaScript, the spread and rest operators are used for working with arrays and objects. The major difference between spread and rest operator is that spread operator is used on the right side of ‘=’ and rest operator is used on the left side of ‘=’. 

```jsx
// SPREAD, because on RIGHT side of =
const arr = [1, 2, ...[3, 4]];

// REST, because on LEFT side of =
const [a, b, ...others] = [1, 2, 3, 4, 5];
console.log(a, b, others);// 1,2,[3,4,5]
```

The spread operator is represented by three dots (**`...`**) and can be used to spread the contents of an array or object into another array or object. This operator can be used to create a new array or object with the combined properties of two or more arrays or objects.

For example, let's consider a **`restaurant`** object that has properties like **`name`**, **`location`**, **`cuisine`**, and **`menu`**:

```jsx
const restaurant = {
name: 'Example Restaurant',
location: 'New York',
cuisine: 'Italian',
menu: ['pizza', 'pasta', 'salad', 'dessert']
};
```

If we want to create a new object with all the properties of the **`restaurant`** object and add a new property **`rating`**, we can use the spread operator like this:

```jsx
const newRestaurant = {
...restaurant,
rating: 4.5
};
```

This will create a new object **`newRestaurant`** with all the properties of the **`restaurant`** object and a new property **`rating`** with the value of **`4.5`**.

The spread operator can be used on arrays as well 

```jsx
const arr = [1,2,3,4,5]
const newArr = [10,20,…arr]
console.log(newArr) // [10,20,1,2,3,4,5]
```

The rest operator, also represented by three dots (**`...`**), can be used to capture an arbitrary number of arguments into an array. This operator is used in function definitions to allow a variable number of arguments to be passed into the function.

For example, let's consider a **`printMenu`** method for the **`restaurant`** object that takes in a variable number of arguments and prints them to the console:

```jsx
const restaurant = {
name: 'Example Restaurant',
location: 'New York',
cuisine: 'Italian',
menu: ['pizza', 'pasta', 'salad', 'dessert'],
printMenu: function(...items) {
console.log('Menu:');
for (let item of items) {
	console.log('- ' + item);
}
}
};
```

Now, if we call **`restaurant.printMenu('pizza', 'pasta', 'salad')`**, it will print the following output to the console:

```jsx
Menu:
- pizza
- pasta
- salad
```

Here, the rest operator **`...items`** is used to capture the arguments **`pizza`**, **`pasta`**, and **`salad`** into an array called **`items`**.

# **Optional Chaining**

The optional chaining operator **`?.`** is a new feature in JavaScript that allows developers to access nested properties of an object, without having to worry about whether the intermediate properties actually exist. This is particularly useful when dealing with data that may be undefined or null.

The optional chaining operator works by checking each intermediate property for existence before trying to access the next property in the chain. If any of the properties in the chain are undefined or null, the operator returns undefined immediately, without trying to access the next property.

Here's an example to illustrate this. Suppose you have an object **`user`** that contains a nested object **`address`**, which in turn contains a property **`street`**. If any of these properties are missing, trying to access the **`street`** property directly would result in a TypeError. However, with the optional chaining operator, you can access the **`street`** property safely like this:

```jsx
const user = {
name: "John Doe",
address: {
city: "New York",
// street is not defined
}
};
const streetName = user?.address?.street;//first check if user exists, then check 
// if address exists and then check for street
console.log(streetName); // output: undefined
```

In the above example, **`streetName`** is assigned **`undefined`** because the **`street`** property is not defined in the **`address`** object. However, if the **`street`** property existed, its value would be returned.

The optional chaining operator can also be used with function calls. If a function in the chain is undefined or null, the operator returns undefined without calling the function. Here's an example:

```jsx
const user = {
name: "John Doe",
address: {
city: "New York",
getFullAddress() {
return ${this.street}, ${this.city};
}
}
};
const fullAddress = user?.address?.getFullAddress?.();
console.log(fullAddress); // output: undefined
```

In this example, the **`getFullAddress()`** function is not called because the **`address`** object is missing the **`street`** property. Therefore, **`fullAddress`** is assigned **`undefined`**.

Overall, the optional chaining operator is a useful addition to JavaScript that helps developers write more concise and robust code.

Consider the below example for the restaurant object described above. 

**Note**: 1. *day is an iterator and not an actual property of the restaurant object and therefore we need to use the [] to access. The dot (.) operator will not work.*

1. *The nullish coalescing operator is used because on Fri the open value is 0. If we do not use the ?? operator and use the logical OR operator || then we will return ‘closed’ on Friday.*  

```jsx
const days = ['mon','tue','wed','thu','fri','sat','sun']
for (const day of days){
   console.log(restaurant.openingHours[day]?.open ?? 'closed');
 }
```

### Optional Chaining on Methods

Optional chaining also works with methods. Using the restaurant object again, the example illustrates the use of optional chaining on methods:

```jsx
// For reference the restaurant.order method is written below:

 order: function(starterIndex, mainIndex){
    return (this.starterMenu[starterIndex], this.mainMenu[mainIndex])

// the code below checks first if the restaurant.order object exists
// if it exists then we call the method with parameters (0,1)
// if the method does not exist then because of the ?? operator the text is logged
console.log(restaurant.order?.(0, 1) ?? 'Method does not exist');
console.log(restaurant.orderRisotto?.(0, 1) ?? 'Method does not exist');

```

### Optional chaining with Arrays

Optional chaining also works on arrays as explained in the example below

```jsx
// Arrays
const users = [{ name: 'Jonas', email: 'hello@jonas.io' }];
console.log(users[0]?.name ?? 'User array empty'); // Jonas
```

### Looping through objects - keys, values and entries

It is possible to iterate through objects using the keys(), values() and the entries() method. Example :

```jsx
const person = {
  firstName: 'Saurav',
  lastName: 'Banerjee',
  birthYear: 1980 }

//to get all keys
for (const key of Object.keys(person)){
  console.log(key)
}

//to get all values
for (const value of Object.values(person)){
  console.log(value)
}

//to get all key, value pairs
for (const [key, value] of Object.entries(person)){
  console.log(key,value)
}

```

## Creating Objects with hidden properties

In JavaScript, properties on an object can be made "hidden" (non-enumerable) by using the `Object.defineProperty` method. These properties will not show up during normal enumeration (like when using `for...in` loops or `Object.keys`), but they can be accessed directly if you know their names. 

Here's how you can create hidden properties in an object:

### Using `Object.defineProperty`

```jsx
const obj = {};

// Define a hidden property 'hiddenProperty'
Object.defineProperty(obj, 'hiddenProperty', {
  value: 'This is a hidden value',
  enumerable: false, // This makes the property non-enumerable (hidden)
  configurable: true, // This allows the property to be redefined or deleted
  writable: true // This allows the property value to be changed
});

console.log(Object.keys(obj)); // Outputs: []
console.log(obj.hiddenProperty); // Outputs: This is a hidden value

const util = require('util');
console.log(util.inspect(obj, { showHidden: true, depth: null }));
// Outputs: { [hiddenProperty]: 'This is a hidden value' }

```

### Explanation

1. **`Object.defineProperty()`**: This method is used to define a new property directly on an object or modify an existing property on an object, and returns the object.
2. **Property Descriptors**: The property descriptor can include properties like `value`, `writable`, `enumerable`, and `configurable`.
    - `value`: The value associated with the property.
    - `writable`: If `false`, the value of the property cannot be changed.
    - `enumerable`: If `false`, the property will not be included in enumerations (e.g., `for...in` loops or `Object.keys()`).
    - `configurable`: If `false`, the property cannot be deleted nor can its descriptors be changed.

### Full Example

```jsx
const obj = {
  visibleProperty: 'This is visible'
};

// Define hidden properties
Object.defineProperty(obj, 'hiddenProperty1', {
  value: 'Hidden Value 1',
  enumerable: false
});

Object.defineProperty(obj, 'hiddenProperty2', {
  value: 'Hidden Value 2',
  enumerable: false
});

console.log(Object.keys(obj)); // Outputs: [ 'visibleProperty' ]
console.log(obj.hiddenProperty1); // Outputs: Hidden Value 1
console.log(obj.hiddenProperty2); // Outputs: Hidden Value 2

const util = require('util');
console.log(util.inspect(obj, { showHidden: true, depth: null }));
// Outputs:
// {
//   visibleProperty: 'This is visible',
//   [hiddenProperty1]: 'Hidden Value 1',
//   [hiddenProperty2]: 'Hidden Value 2'
// }

```

By using `Object.defineProperty` with `enumerable` set to `false`, you can create hidden properties in an object that will not show up during standard property enumeration but can be revealed using `util.inspect` with the `showHidden` option set to `true`.

# Sets

A set is basically just a collection of unique values. So that means that a set can never have any duplicates. A set can hold mixed data types.

```jsx
//Creating a set-while creating a new set it is important to mention the 'new' keyword
const mySet = new Set([10,20,30,40,50])

// duplicate values are not allowed in a Set
const newSet = new Set(["apple","pizza","pizza","orange"])
console.log(newSet) // {apple,pizza,orange}

// set can hold mixed data types
const setMixed = new Set(["apple",10,1.345,true])
console.log(setMixed)
```

### Size of a set

Unlike arrays where they have a length, Sets do not have a length. However, they have a size which is the equivalent of the length of the array.

```jsx
const mySet = new Set([10,11,12,13,14,15,16])
console.log(mySet.size) // 7
```

### Finding if an element exists in a Set

We can find out if an element exists in a set using the ‘has’ method. The ‘has’ method returns a boolean value : true/false. 

```jsx
const mySet = new Set(['pizza','pasta','cheese','jalapenos','olives'])
console.log(mySet.has('olives')) // true
```

### Adding a new element to the Set

We can add a new element to a existing Set using the ‘add’ method:

```jsx
const mySet = new Set([10,20,30])
mySet.add(40)
console.log(mySet) // {10,20,30,40}
```

### Deleting a element from a Set

Elements of a set can be deleted using the delete method :

```jsx
const mySet = new Set([10,20,30,40, 'Pizza'])
mySet.delete("Pizza")
console.log(mySet) //{10,20,30,40}
```

### Iterating a Set

```jsx
const mySet = new set([11,22,33,44,55]);
for (const item of mySet){
	console.log(item)
}  
// 11
// 22
// 33
// 44
// 55
```

### Filtering out duplicate values from an array using a Set

Since a Set cannot have duplicate values it can be used to remove the duplicate values which are present in an array. 

```jsx
const myArr = [10,11,12,14,12,16,10];
const Unique = new Set(myArr)
console.log(Unique) // 10,11,12,14,16
```

However, in the above code the Unique variable returned is a set and not an array. A set can be converted to an array as given below.

### Converting a Set into an array

```jsx
// Using the Unique set from above
// We just use the spread operator to expand the Set elements and convert into an array
const newArr = [...Unique]
```

### Using the ‘size’ method of Set to determine the unique letters in a string or unique elements in an array

Any array or string can be converted as a Set since they are iterables. Since a Set contains only unique elements we can use this property of a Set to count the number of unique elements in a String or find out the number of unique elements in an Array.

```jsx
// finding the unique number of characters in a string
const myName = "SauravBanerjee"
const uniqueChar = new Set(myName)
console.log(uniqueChar.size) // 9

// finding the number of unique elements in an array
const myArray = [10,11,12,14,11,15,12]
const uniqueArray = new Set(myArray)
console.log(uniqueArray.size) // 5

```

Set elements do not have any index. **Set is not to be used if the objective is to store values and later retrieve them as Sets do not allow for retrieval of elements**. 

## Specific use cases of Sets

### Adding Elements of an Array to an existing Set

```jsx
function mySet(set,arr){
  arr.forEach(set.add, set)
  return set;
}

console.log(mySet(new Set([1, 2, 3]), [4, 5, 6])); // {1,2,3,4,5,6}
```

In the above given code, the `forEach` function is used to iterate over each element of the `arr` array. The `forEach` function takes two arguments: a callback function and an optional context object.

In this case, `set.add` is passed as the callback function to `forEach`. The `forEach` function internally calls the callback function for each element of the array.

Now, the `set.add` function is a method of the `set` object. When `forEach` invokes the callback function, it automatically sets the `this` keyword to the provided context object, which in this case is the `set` object. By passing `set` as the second argument to `forEach`, it ensures that the `this` inside the `set.add` function refers to the `set` object.

The `set.add` function itself takes the element of the array as an argument and adds the element to the set. However, you might be wondering why the element is not explicitly passed to `forEach`.

In a `forEach` loop, the callback function is automatically called with three arguments: the current element, the index of the current element, and the array being iterated over. However, if you don't explicitly use those arguments inside the callback function, you don't need to provide them when passing the callback to `forEach`. In this case, the element itself is not used inside the `set.add` function, so it doesn't need to be explicitly passed.

To summarize, in the given code, `forEach` is used to iterate over the elements of the `arr` array. The `set.add` function is passed as the callback, and the `set` object is passed as the context object to ensure that `this` inside `set.add` refers to the `set` object. The callback is automatically called with the current element, but since it is not used inside `set.add`, it doesn't need to be explicitly passed.

# Maps

In JavaScript, **`Map`** is a built-in data structure that allows you to store key-value pairs. It's similar to an object, but with some important differences.

Here are some key characteristics of **`Map`**:

- **Keys can be of any data type, including objects, whereas keys in objects are always strings - This is the biggest difference between Maps and Objects**
- The order of entries is preserved, unlike in objects where the order of properties is not guaranteed.
- The size of the **`Map`** can be determined using the **`size`** property, whereas the size of an object needs to be determined manually by counting its properties.

```jsx
// create a new Map
const myMap = new Map();

// add some key-value pairs
myMap.set('a', 1);
myMap.set('b', 2);
myMap.set('c', 3);

// get a value by key
console.log(myMap.get('a')); // 1

// get the size of the map
console.log(myMap.size); // 3

// loop over the keys and values
for (const [key, value] of myMap) {
console.log(${key}: ${value});
}
```

Calling the ‘set’ method on a map returns the updated map object. 

The set method can be used for chaining as shown below:

```jsx
 const myMap = new Map();
 myMap.set('one',1).set('two',2).set('three',3)
```

### Retrieving values from a Map

The map object has inbuilt get() method which is used to retrieve the entries from a map object.

In the example below, we set a key value using a boolean value of true/false to specify the output.

```jsx
// we use the get() method to retrieve values from the myMap object 
const myMap = new Map();
myMap.set(true, 'Shop is Open').set(false,'Shop is closed')
console.log(myMap.get(true)) // Shop is Open

```

### Caution: Data type while using the get() method

It is important to specify the same data type for the get() method that was used while specifying the set() method. For e.g 

```jsx
console.log(myMap.get('true')) // returns undefined because we used true as boolean 
// however in the .get() method we specified 'true' as string 
```

### Combining logical operator and get() method

Logical operators like && and || can be combined with the get() method to make multstep conditional which provides a single output.

```jsx
const time = 21;
const myMap = new Map();
myMap.set('open', 10).set('close', 23).set(true, 'We are open').set(false,'We are Closed')
console.log(myMap.get(time > myMap.get('open') && time < myMap.get('close'))
// We are Open
/*In the above code block, the inner conditional block: 

time > myMap.get('open') && time < myMap.get('close') 

evaluates to either true or false. We then again call the myMap.get() method on it which becomes 

myMap.get(true) or myMap.get(false). 
So now depending upon the value of the variable time 
we get an output of either ‘We are open’ or ‘We are close’.*/
```

### Checking if an element exists in a map

Map objects have the has() method to check for the existence of any element in the object.

```jsx
const myMap = new Map()
myMap.set(true, 'Shop is Open').set(false,'Shop is closed')
console.log(myMap.has(true)) // true
```

The above code block checks for the presence of the boolean value of true in the myMap object and returns true to confirm it exists in the object.

### Deleting an element from the map object

```jsx
const myMap = new Map()
myMap.set(true, 'Shop is Open').set(false,'Shop is closed')
myMap.delete(false)
console.log(myMap) // {true => 'Shop is Open'}
```

The above code block deletes the false key from the myMap object.

### Deleting all key:value pairs from the map object using clear() method

Map objects have a clear() method which deletes all key:value pairs from an existing map object

```jsx
const myMap = new Map()
myMap.set(true, 'Shop is Open').set(false,'Shop is closed')
myMap.clear()
console.log(myMap) // Map(0) {size: 0}
```

### Using Objects as keys in Map

Keys in a map object can be arrays, objects as well. However to be used as keys they needs to be first assigned to a variable and then the variable can be used as the key in the map object. directly assigning a object as key will result in error.x

```jsx
const arr = [1,2,3]; // creating a array object
const myMap = new Map();
myMap.set(arr, "Hello"); // using the object as key in a Map
console.log(myMap.get(arr)) // Hello
```

While the above code block is correct, if we modify the code as given below then it results in an error:

```jsx
//directly passing an array as the key will result in error
const myMap = new Map();
myMap.set([1,2,3],"hello");
console.log (myMap.get([1,2,3])) // undefined
```

The last statement in the code block returns **`undefined`** because the **`get()`** method of a **`Map`** object retrieves a value associated with a given key from the map. In the code block, a new array **`[1,2,3]`** is created and used as a key to associate the value **`"hello"`** with it in the **`myMap`** object using the **`set()`** method. However, when the **`get()`** method is called with the same array **`[1,2,3]`** as the argument, **it creates a new array object which is not the same as the array object used as the key in the `set()` method.** Therefore, the **`get()`** method is not able to find a value associated with the new array object and returns **`undefined`**.

### Alternative way of creating Map

1. Instead of using the set() method, we can pass an array of arrays to a map object to create the map. Refer example below:

```jsx
const question = new Map([['question', 'Best programming language'],[1, 'C++'],[2, 'Java'],[3,'Python'],[4,'JavaScript'],['correct',3]])
console.log(question.get(question.get('correct')))// Python
```

1. If there is an existing object and values from the object are to be used for creating a map then we can use the entries() method on the object to create the map. refer example below:

```jsx
const restaurant = {
	 restaurantName: "Yalos",
   address: "Exo Gialos Thiras 847 00",
   starter: ['ceviche', 'tzatziki', 'spanakopita', 'bruschetta'],
   mainMenu: ['mackarel_smoked', 'mousaka', 'chicken_souvlaki','briam']
   timings: {
   monTothur: {open: 11,close: 9},
   friandsat: {open: 11,close: 11},
   sun: {open:'closed', close: 'closed'}
  }}

const hoursMap = new Map(Object.entries(restaurant.timings));
console.log(hoursMap) // {'monTothur' => {…}, 'friandsat' => {…}, 'sun' => {…}}

```

### Iterating over Maps

Since Maps are iterables,so we can use a ‘for’ loop to iterate over the Map

```jsx
const question = new Map([['question', 'Best programming language'],
[1, 'C++'],[2, 'Java'],[3,'Python'],[4,'JavaScript'],['correct',3]])
for (const [key,value] of question){
	if (typeof key === 'number'){
		console.log(`Answer ${key} : ${value})
	}
	}
```

### Convert Map to an array

A map object can be converted into an array object by using the spread operator. Refer below.

```jsx
const myMap = new Map()
myMap.set(true, 'Shop is Open').set(false,'Shop is closed')
const newArray = [...myMap]
console.log(newArray)
//  0: (2) [true, 'Shop is Open']
//  1: (2) [false, 'Shop is closed']
//  length: 2
//  [[Prototype]]: Array(0)
```

# Choosing between Sets, Maps, Objects and Arrays

There are 3 sources of data for a web app:

- From the program itself: Data directly written in the source code (e.g status messages)
- From the UI: Data input from the user or data written in DOM (e.g tasks in todo app)
- From external sources: like a Web API

These collection of data sources have to be written in a data structure. 

Deciding  on a data structure to be used:

- If the requirement is to store the data like a simple list then Arrays or Sets can be used
- If the requirement is to store the data in the form of key: value pairs then objects or Maps can be used. **Remember that keys are used to describe the values** and therefore if we need a description of the values then a key:value pair makes more sense.

**The use case for arrays**: 

- Data needs to be stored as a ordered list
- Data has duplicates and these duplicates have to be retained
- Data manipulation is required

**The use case for sets**:

- Only unique values need to be stored
- Order of the data elements are of no significance
- For higher performance - set operations are much more faster than arrays
- To remove duplicate values  from arrays

**The use case for Maps:**

- Better performance than objects
- Keys can be of any data type inclusive of objects
- Easy to iterate
- Easy to compute size

**The use case for objects**:

- Easier to write and access values with . and []
- When methods have to be functions
- Widely used when working with JSON
- Accessing variables declared in other methods using the ‘this’ keyword. (**Maps can’t do this**)

# Numbers, Dates, International Formats and Timers

The section below discusses numbers in JavaScript, including their internal representation, limitations when working with fractions, and different methods to manipulate numbers.

Numbers in JavaScript are internally represented as floating-point numbers, regardless of whether they are written as integers or decimals. The numbers **`23`** and **`23.0`** are considered equivalent in JavaScript.

```jsx
console.log(23 === 23.0) //true
```

However, there are challenges of accurately representing fractions in binary, which is the base-2 format used by JavaScript. Fractions like **`0.1`** can result in imprecise calculations, leading to unexpected results like 

```jsx
console.log(**0.1 + 0.2) // 0.30000000000000004**.
```

It is emphasized that these limitations may impact precise scientific or financial calculations, and users should be mindful of them.

There are different techniques for converting strings to numbers. The conventional approach is to use **`Number()`** function, although a shortcut is to use the unary plus operator (**`+`**) for type coercion.

```jsx
console.log(+'23') // 23
```

### parseInt() and parseFloat()

Parsing numbers from strings can be done by the **`parseInt()`** and **`parseFloat()`** functions. The  **`parseInt()`** takes a second argument of numeral system (e.g., base 10) and this can prevent potential bugs. parseInt() when used on floating point numbers returns the integer value only.

**parseInt() only works if the string begins with a number**

```jsx
console.log(Number.parseInt('40px',10)) // 40
console.log(Number.parseInt('e32',10)) // NaN
console.log(Number.parseInt('3.14', 10)) // 3
```

Some of the practical usecase of **`parseInt()`** and **`parseFloat()`**, are in extracting values from CSS units such as **`rem`** in CSS. 

```jsx
console.log(Number.parseFloat('2.5rem',10)) // 2.5
```

Finally, the **`isNaN()`** function is discussed, which determines whether a value is NaN (Not a Number). Examples showcase the behavior of **`isNaN()`** with different values, indicating that it returns **`false`** for regular numbers and strings representing numbers, while returning **`true`** for strings that cannot be parsed into numbers.

Overall, these explanatory notes provide an overview of numbers in JavaScript, covering their internal representation, string-to-number conversion methods, and the usage of relevant functions for number manipulation.

### **isNaN() method in JavaScript**

The **`isNaN()`** function in JavaScript is used to determine whether a value is NaN (Not a Number). It returns a boolean value: **`true`** if the value is NaN, and **`false`** if it is a valid number or can be parsed into a number.

Here's how the **`isNaN()`** function works:

1. If the argument passed to **`isNaN()`** is not of type **`number`** or cannot be implicitly converted to a number, the function returns **`true`**.

```jsx
isNaN("Hello"); // true
isNaN("123"); // false (can be parsed into a number)
isNaN(true); // false (converted to 1, a valid number)
```

If the argument is of type **`number`**, the function checks if it is NaN.

```jsx
isNaN(NaN); // true
isNaN(123); // false
isNaN(Infinity); // false
```

Note that **`NaN`** is a special numeric value in JavaScript that represents the result of an invalid or undefined mathematical operation. It is considered a numeric value, but it is not equal to any other value, including itself.

It's important to be aware that **`isNaN()`** performs implicit type conversion. If you want to strictly check if a value is a valid number without any type coercion, you can use other techniques, such as the **`typeof`** operator or regular expressions.

```jsx
typeof value === "number"; // strict type check
/^-?\d+(\.\d+)?$/.test(value); // regular expression check for numbers
```

Keep in mind that **`isNaN()`** can be useful for scenarios where you need to validate whether a value is a number or,  to handle potential NaN values in your code.

### `isFinite()` and `isInteger()` methods in JavaScript

**`isFinite()`**: The **`isFinite()`** function is used to check if a value is a finite number or not. It returns a boolean value: **`true`** if the value is a finite number, and **`false`** if it is either **`NaN`**, positive infinity (**`Infinity`**), or negative infinity (**`-Infinity`**).

```jsx
isFinite(123); // true
isFinite(Infinity); // false
isFinite(-Infinity); // false
isFinite(NaN); // false
```

Note that **`isFinite()`** performs a strict check and does not perform any implicit type conversion. It returns **`false`** for non-numeric values or values that cannot be converted to a number.

**`isInteger()`**: The **`isInteger()`** method is used to check if a value is an integer. It returns a boolean value: **`true`** if the value is an integer, and **`false`** if it is not.

```jsx
isInteger(5); // true
isInteger(5.1); // false
isInteger("5"); // false (string)
isInteger(Infinity); // false
```

The **`isInteger()`** method checks if the value is a whole number without any fractional or decimal part. Note that it also returns **`false`** for non-numeric values or values that cannot be converted to a number.

It's important to note that **`isInteger()`** does not perform any rounding or conversion to an integer type. It simply checks if the value is conceptually an integer.

Both **`isFinite()`** and **`isInteger()`** are helpful methods for performing specific checks on numeric values in JavaScript. They can be used to validate numbers or handle specific number-related conditions in your code.

### Random numbers

The Math.random() generates a random number between 0 and 1 excluding 1. 

### Generating a random number between a min and max given value

```jsx
function minMax(min, max){
	return Math.floor(Math.random() * ((max-min) + 1)) + min
}
```

In the above code, Math.random() generates a floating point number between 0 and 1 ( excluding 1). The portion of the code in which we add (max-min) +1 increases the returned random number range to a number which is 1 less than the ‘max’ number when it is first truncated using Math.trunc() and then later the ‘min’ value is added. For e.g consider the example below:

```jsx
minMax(15,20) 
// Assume that Math.random() returns a number 0.995. Then we add (max-min) + 1
// which in this case is (20-15) + 1 = 6. Now 6 * 0.995 = 5.97
// Here lies the catch. No matter whatever number Math.random returns, the resulting
// number after adding (max-min)+1 will be max 5.99. 
// Now this number gets truncated by Math.floor(), so the max value returned will be 5
// Since the floor() method is used, it will work with -ve numbers as well.
// Now if we add the 'min' ( which is present in the end) then the max will be 20
// This is how, we get a number between the "max" and "min" numbers 
```

### Math functions

**sqrt()** - This is used for finding the square root of the number

```jsx
console.log(Math.sqrt(25)) // 5
```

**min()** - Used for finding the minimum among the sequence of numbers. The min() method performs a type coercion so if a number is passed as string, it gets coerced as a number and then evaluated.

```jsx
console.log(Math.min(10, 23, 34, 41, 52)) // 10

console.log(Math.min('5', 10, 12, 14, 15)) // 5
```

**max()** - Used for finding the maximum among the sequence of numbers. The max() method performs a type coercion so if a number is passed as string, it gets coerced as a number and then evaluated.

```jsx
console.log(Math.max(10, 23, 34, 41, 52)) // 52

console.log(Math.max('90', 80, 70, 60, 50)) // 90
```

### Rounding off Numbers

**trunc()** - This is for truncating numbers, such that the decimal part of the number is removed

```jsx
console.log(Math.trunc(32.7765)) // 32

console.log(Math.trunc(-32.7765)) // -32
```

**round()** - Rounds off the number. If decimal part of the number is less than 0.5 then the original number is returned otherwise the next higher integer is returned

```jsx
console.log(Math.round(32.7765)) // 33

console.log(Math.round(32.50)) // 33

console.log(Math.round(32.4)) // 32 ( decimal part is less than 0.5)

console.log(Math.round(32.2)) // 32

```

**ceil()** - This is the ceiling method which rounds up a floating number to the next higher number 

```jsx
console.log(Math.ceil(24.6)) // 25

console.log(Math.ceil(-25.8)) // -25

console.log(Math.ceil(-25)) // -25
```

**floor()** - The floor() method returns the rounded down number. If a negative float point number is given then it returns the next negative number as it is smaller than the number given

```jsx
console.log(Math.floor(24.6)) // 24

console.log(Math.floor(-25.8)) // -26

console.log(Math.floor(-25)) // -25
```

**BigInt()**

In JavaScript, the **`BigInt`** data type is used to represent arbitrary precision integers. It allows you to work with numbers that are larger than the maximum safe integer value (**`Number.MAX_SAFE_INTEGER`**), which is approximately 9 quadrillion (9 * 10^15). **`BigInt`** is particularly useful when dealing with extremely large numbers or when precise integer calculations are required.

To create a **`BigInt`** value, you can use the **`BigInt()`** function and prefix the number with **`n`**:

```jsx

const largeNumber = BigInt(12345678901234567890n);
```

In the example above, **`largeNumber`** is assigned a **`BigInt`** value. The **`n`** suffix indicates that the literal is a **`BigInt`** rather than a regular **`Number`**.

Here are a few key points to note about **`BigInt`**:

1. **Exceptions**: The **`BigInt`** constructor throws an exception if the argument is not a valid **`BigInt`** value. For example, **`BigInt('123abc')`** would throw an error because **`'123abc'`** is not a valid representation of a **`BigInt`**.
2. **Operators and Methods**: You can perform arithmetic operations and use various methods with **`BigInt`** values, similar to regular numbers. However, **`BigInt`** values cannot be mixed with regular numbers in arithmetic operations, and the comparison operators (**`<`**, **`>`**, **`<=`**, **`>=`**) cannot be used between **`BigInt`** and **`Number`** values.
3. **Type Coercion**: When using operators or methods with mixed types, JavaScript will attempt to coerce the operands to compatible types. For example, **`3n + 2`** would coerce **`2`** to a **`BigInt`** and return **`5n`**. However, **`3n + 2.5`** would throw an error because it cannot safely coerce **`2.5`** to a **`BigInt`**.
4. **Numeric Literals**: Numeric literals in JavaScript cannot be directly assigned as **`BigInt`** values. For example, **`const x = 123n;`** is valid, but **`const y = 123n;`** would throw an error because the numeric literal **`123`** is interpreted as a regular **`Number`**. To assign a numeric literal as a **`BigInt`**, you need to use the **`BigInt()`** function, such as **`const y = BigInt(123);`**.
5. **Compatibility**: **`BigInt`** is a relatively new feature introduced in ECMAScript 2020, so it may not be supported in older browsers or environments. It's recommended to check for browser compatibility or use appropriate fallbacks or polyfills if you need to support older environments.

Overall, **`BigInt`** provides a way to work with arbitrarily large integers in JavaScript, overcoming the limitations of the regular **`Number`** type. However, due to its differences and limitations, it's important to be mindful of how **`BigInt`** interacts with other data types and to use it where it's specifically needed for working with large integers.

**Date - creation and some common methods**

**Creation** - the Date() constructor needs to be called to create a new Date()

```jsx
// The sequence of parameters - year, month, day, hour, minutes, seconds
const newDate = new Date(2023, 10, 5, 9,15,10)
// Sun Nov 05 2023 09:15:10 GMT+0530 (India Standard Time)
```

**Getting the current date and time**

Using the Date.now() method we can obtain the current date and time. However the Date.now() returns a large integer number, so to convert it into a Date and time format, we need to call the Date() constructor. Refer the code below:

```jsx
console.log(Date.now()) // 1688913332958

console.log(new Date(Date.now())) // Sun Jul 09 2023 20:05:59 GMT+0530 (India Standard Time)
```

**Getting the Year, Month, Day, Hour, Minutes and Seconds from a Date**

The index for Month and Day starts from 0, so Sunday = 0 and January = 0

```jsx
const newDate = new Date(2023, 10, 5, 9,15, 10)

console.log(newDate.getFullYear()) // 2023

console.log(newDate.getMonth()) // 10 (This represents November which is 
// actually  11, but since the index starts from 0, it is shown as 10

console.log(newDate.getDay()) // 0 ( this represents Sunday)

console.log(newDate.getHours()) // 9

console.log(newDate.getMinutes()) // 15

console.log(newDate.getSeconds()) // 10
```

JavaScript auto corrects if we enter a wrong date. For example, if a date of November 31 is given then JS returns Dec 1 as the date. 

**Note**: JS increments the date to return the next date. So Dec 32 returns Jan 1 and Dec 33 returns Jan 2.

```jsx
console.log(new Date(2023, 11, 32)) // Mon Jan 01 2024 00:00:00 GMT+0530 (India Standard Time)
console.log(new Date(2023, 11, 33)) //Tue Jan 02 2024 00:00:00 GMT+0530 (India Standard Time)

console.log(new Date(2023, 13, 01)) //Thu Feb 01 2024 00:00:00 GMT+0530 (India Standard Time)

```

### International Date Format

International Date formats in JavaScript can be achieved using the **`toLocaleDateString()`** method.

This method provides a way to format and display dates using the user's local time zone and language preferences. The **`toLocaleDateString()`** method takes two optional parameters: a **`locales`** parameter for specifying the user's language and region, and an **`options`** parameter for specifying the date format.

Here's an example of using **`toLocaleDateString()`** to display the current date in different formats:

```
const date = new Date();

console.log(date.toLocaleDateString()); // "7/9/2023" (default format)

console.log(date.toLocaleDateString('en-US')); // "7/9/2023" (US format)

console.log(date.toLocaleDateString('en-GB')); // "09/07/2023" (UK format)

console.log(date.toLocaleDateString('de-DE')); // "09.07.2023" (German format)

console.log(date.toLocaleDateString('fr-FR')); // "09/07/2023" (French format)

```

In the example above, the **`toLocaleDateString()`** method is called with different language and region codes to display the date in different formats.

The **`options`** parameter can be used to customize the date format further. It accepts an object with different properties, such as **`weekday`**, **`year`**, **`month`**, **`day`**, and more. Here's an example:

```
const date = new Date();

const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };

console.log(date.toLocaleDateString('en-US', options)); // "Saturday, July 9, 2023"

```

In the example above, the **`options`** object is used to specify a long weekday and month format, along with a numeric year and day format.

Overall, the **`toLocaleDateString()`** method provides a flexible and customizable way to format and display dates in different languages and regions, making it a useful tool for internationalization in web applications.

### `setTimeout()` and `setInterval()` methods in JavaScript

In JavaScript, the **`setTimeout()`** and **`setInterval()`** functions are used to delay the execution of code or repeatedly execute code at specified intervals.

### `setTimeout()`

The **`setTimeout()`** function is used to execute a function after a specified amount of time has elapsed. It takes two arguments: the function to be executed, and the time (in milliseconds) to wait before executing the function.

Here's an example:

```
function delayedGreeting() {
  console.log('Hello after 2 seconds!');
}

setTimeout(delayedGreeting, 2000);

```

In the example above, the **`delayedGreeting()`** function is executed after a delay of 2 seconds (2000 milliseconds) using **`setTimeout()`**.

### `setInterval()`

The **`setInterval()`** function is used to repeatedly execute a function at a specified interval. It takes two arguments: the function to be executed, and the time (in milliseconds) between each execution.

Here's an example:

```
function countUp() {
  let count = 0;

  function increment() {
    count++;
    console.log(count);
  }

  setInterval(increment, 1000);
}

countUp();

```

In the example above, the **`countUp()`** function repeatedly executes the **`increment()`** function every second (1000 milliseconds) using **`setInterval()`**. The **`increment()`** function increments a counter and logs its value to the console.

### Using `clearTimeout()` and `clearInterval()`

Both **`setTimeout()`** and **`setInterval()`** return a value that can be used to cancel the delayed or repeated execution of the function. The **`clearTimeout()`** and **`clearInterval()`** functions are used to cancel the execution of the corresponding **`setTimeout()`** or **`setInterval()`** function.

Here's an example:

```jsx
function delayedGreeting() {
  console.log('Hello after 2 seconds!');
}

const timeoutId = setTimeout(delayedGreeting, 2000);

clearTimeout(timeoutId);

```

In the example above, the **`setTimeout()`** function is called with a delay of 2 seconds and the resulting timeout ID is stored in a variable. The **`clearTimeout()`** function is then used to cancel the execution of the timeout before it occurs.

Similarly, the **`clearInterval()`** function can be used to cancel the repeating execution of a function with **`setInterval()`**.

```jsx
function countUp() {
  let count = 0;

  function increment() {
    count++;
    console.log(count);
  }

  const intervalId = setInterval(increment, 1000);

  if (count >= 5) {
    clearInterval(intervalId);
  }
}

countUp();

```

In the example above, the **`countUp()`** function uses **`setInterval()`** to repeatedly execute the **`increment()`** function every second. The interval ID is stored in a variable and used to cancel the interval after the counter reaches a value of 5 or greater using **`clearInterval()`**.

Overall, the **`setTimeout()`** and **`setInterval()`** functions are useful tools for delaying or repeating the execution of code in JavaScript, and can be combined with **`clearTimeout()`** and **`clearInterval()`** to control their behavior.

# DOM Manipulation

### How the DOM really works behind the scenes

So first, remember that the DOM is basically the interface between all JavaScript code
and the browser, or more specifically HTML documents that are rendered in and by the browser.
DOM can be used to make JavaScript interact with the browser and again more specifically we can create and modify and delete elements, set styles and classes and attributes and listen and respond to events. In practice **this works because a DOM tree is generated from any HTML document and a DOM tree is a tree like structure made out of nodes**.  And we can then interact with this tree. Now how does that interaction actually work? Well the DOM is a very complex API
which remember stands for application programming interface. So it's the interface we can use to programmatically interact with the DOM. In practice that means that the DOM contains a ton of methods and properties that we use to interact with the DOM tree such as the querySelector, addEventListener or createElement methods, or also the innerHTML, textContent or children properties and many, many more. Now in the DOM there are different types of nodes. For example some nodes are HTML elements but others are just text, remember? And this is really important to understand because all these DOM methods and properties are organized into these different types of objects. 

 So first, every single node in the DOM tree is of the type, node. And such as everything else in JavaScript, each node is represented in JavaScript by an object. This object gets access to special node methods and properties, such as text content, child nodes, parent nodes, clone nodes and many others.

Now we already know that there are different types of nodes. So how should these be represented? Well, this node type has a couple of child types so to say. And these are the element type, the text type, the comment type and also the document type.

So whenever there is text inside any element, we already know that it gets its own node.
And that node will be of the type, text. And the same actually happens for HTML comments
and that's because the rule is that everything that's in the HTML has to go into the DOM as well.
Now for the element itself there is the element type of node. And this type of node gives each HTML access to a ton of useful properties such as innerHTML, classList, children or parent element. There are also many useful methods like append, remove, insertAdjacentHTML, querySelector, closest and that's just to name a few. So again, each element will be represented internally as an object. 

Now just to make this complete, the element type has internally an HTML element,child type. And that element type itself has exactly one child type for each HTML element that exists in HTML. So we have a special type for buttons, a special type for images,
for links, and so on and so forth. And that's important because each of these HTML elements
can have different unique properties. For example and image has a source attribute in HTML which no other element has. Or the anchor element for links has the HREF attribute which also no other element has. And so the DOM needs a way of storing these different attributes and therefore different types of HTML elements were created in the DOM API. 

What makes all of this work is something called inheritance. So what is inheritance? Well inheritance means that all the child types will also get access to the methods and properties of all their parent node types. For example an HTML element will get access to everything from the element type, like innerHTML, or classList or all these other methods and properties. And besides that it will also get access to everything from the node type because that is also its parent type. So we can think of this as though the HTML button element for example, is also an element and also a node.  

 Each of these types of nodes has access to different properties and methods and that some of them even inherit more properties and methods from their ancestors in this organization. Now we didn't talk yet about the documents node type. So document, which we use all the time in DOM manipulation is in fact just another type of node so it contains important methods, such as querySelector, createElement and getElement by I.D. And note how querySelector is available on both the document and element types. 

The DOM API actually needs a way of allowing all the node types to listen to events. And remember we usually listen for events by calling the addEventListener method on an element or the document. Right? So why does that actually work? Well its because there is a special node type called EventTarget which is a parent of both the node type and also the window node type. And so with this, thanks to inheritance, we can call addEventListener on every single type of node in the DOM API because all elements as well as document and window, and even text and comment will inherit this method and therefore we will be able to use addEventListener on all of them just as if it was their own method. 

We do never manually create an eventTarget object. This is just an abstract type that we do not use in practice. This all really happens behind the scenes to make all the functionality work as we expect it to work. So in a nutshell this is how the DOM API works and is structured behind the scenes. 

### DOM - HTML Collection and Node List

Cetain DOM methods return HTML collection while some others return a node list. The main difference between an [HTMLCollection](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection) and a [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) is that one is **live** and one is **static**. This means that when an element is [appended](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) to the DOM, a live node will recognize the new element while a static node will not. HTMLCollection is live whereas NodeList is static.

HTML collection : The element methods *getElementsByClassName()* and 

*getElementsByTagName()* return a live HTMLCollection. It only includes the matching elements (e.g. class name or tag name) and does not include text nodes, it provides only two methods *item* and *namedItem*.

In the example below, all the elements with the class name of *fruits* is selected. The *item()* method is then used to access the fruit at index 0 and a class name of *fruit__01* is added to that element.

```jsx
const fruits = document.getElementsByClassName(‘fruits’);
fruits.item(0).classList.add(‘fruit__01’)
```

NodeList: NodeLists behave differently depending on how you access them; if you access elements using *childNodes*, the returned list is live and will update as more elements are added to the node. If it’s accessed using *querySelectorAll()*, the returned list is static and will not update if more elements are added to the node.

```jsx
// Using childnodes to return a live list
const nl = document.querySelector('.lnk')
const childnode = nl.childNodes
console.log(childnode);

// Returning a static list 
const nl = document.querySelectorAll('.lnk')
console.log(nl)
```

### DOM Methods

1. document.documentElement() : selects the whole web page
2. document.getElementByTagName(): use tag name like ‘div’, ‘img’, etc to select HTML elements. Returns a HTML collection.
3. document.getElementByClassName(): select HTML element using class name
4. document.classList : Used for modifying - add, delete, toggle classes of CSS from JavaScript. It has sub methods - 
    1. **add():** The add() method is used for adding one or more classes to the element.
    2. **remove():** The remove() method is used for removing one or more classes from the number of classes present in the element.
    3. **toggle():** The toggle() method is used for toggling the specified class names of an element. It means on one click the specified class gets added and on another click the class gets removed. It is known as the toggle property of an element.
    4. **replace():** The replace() method is used for replacing an existing class with a new class.
    5. **contains():** The contains() method of the JavaScript classList property is used for returning the Boolean value as an output. If the class is present, the value is returned as true otherwise false is returned.
    6. **item():** The item() method is used for displaying the name of the classes at the particular index. Thus, it returns the class name.
5. Prepend and Append : Prepend is used to add a HTML element before another element, whereas Append will add after a element. One of the example of append is to display - “Cookie Acceptance Policy on a Web Page”

```jsx
const message = document.createElemnt('div')
message.innerHTML = "We use cookies for improved functionality and analytics. 
										<button class ='cookie-message'> Got It! </button>";
document.body.append(message) // the cookie message is displayed at the bottom of the page
```

1. Single instance of DOM : Only a single instance of a DOM element should exist in the DOM tree. If multiple instances of the same element needs to be displayed in the web page then we use 

### innerText() vs textContent() vs innerHTML()

innerText(): returns the text of an element along with all CSS styling like ‘bold’, ‘underline’ etc..

textContent(): returns the text of all nodes : parent and child nodes of an element without the CSS styling 

innerHTML(): returns the content of parent and child nodes with the HTML tags of the child nodes

# Object Oriented Programming in JS

## Inheritance between classes

There are 3 ways in which inheritance between classes can happen in JS. First, using constructor functions. Second, using ES6 classes. Third, using Object.create.

Let's illustrate each of these three techniques of inheritance in JavaScript with code examples.

1. **Inheritance using Constructor Functions:** 

```jsx
// Parent Constructor Function
function Animal(name) {
  this.name = name;
}

Animal.prototype.sayHello = function() {
  console.log(`Hello, I'm ${this.name}`);
};

// Child Constructor Function
function Dog(name, breed) {
  Animal.call(this, name); // Call parent constructor
  this.breed = breed;
}

// Inherit from Animal prototype
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog; // Reset constructor

Dog.prototype.bark = function() {
  console.log(`Woof! I'm a ${this.breed}`);
};

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.sayHello(); // Output: Hello, I'm Buddy
myDog.bark();     // Output: Woof! I'm a Golden Retriever

```

**Why do we need to reset the constructor using the following line of code?**

**Dog.prototype.constructor = Dog; // Reset constructor**

In JavaScript, when you create a prototype chain, like in the example of inheritance using constructor functions, the **`.prototype.constructor`** property is an important property that by default points back to the constructor function itself. However, when you create a new prototype for a child constructor function, you're effectively overwriting the **`.prototype`** object of the child function, which also changes the **`.prototype.constructor`** property. It no longer points to the child constructor, but instead to the parent constructor.

To fix this mismatch and ensure the **`.prototype.constructor`** property of the child constructor points to the child constructor itself, you need to manually reset it.

Let's break down the process step by step:

1. When you create a constructor function, its **`.prototype.constructor`** property points to the constructor function itself.
2. When you create a child constructor and set its prototype to **`Object.create(Parent.prototype)`**, the child constructor's **`.prototype.constructor`** property points to the parent constructor. This happens because you're essentially replacing the child's prototype with a new object that inherits from the parent prototype.
3. To correct this situation, you manually reset the child constructor's **`.prototype.constructor`** property to point to the child constructor.

2. **Inheritance using ES6 Classes:**

```jsx
// Parent Class
class Animal {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
}

// Child Class
class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call parent constructor
    this.breed = breed;
  }

  bark() {
    console.log(`Woof! I'm a ${this.breed}`);
  }
}

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.sayHello(); // Output: Hello, I'm Buddy
myDog.bark();     // Output: Woof! I'm a Golden Retriever

```

1. **Inheritance using Object.create:**

```jsx
// Parent Object
const animalPrototype = {
  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
};

// Create a Child Object with a link to the Parent Object
const dog = Object.create(animalPrototype);
dog.init = function(name, breed) {
  this.name = name;
  this.breed = breed;
};

dog.bark = function() {
  console.log(`Woof! I'm a ${this.breed}`);
};

const myDog = Object.create(dog);
myDog.init("Buddy", "Golden Retriever");
myDog.sayHello(); // Output: Hello, I'm Buddy
myDog.bark();     // Output: Woof! I'm a Golden Retriever

```

All three techniques achieve inheritance in slightly different ways, but they all allow you to create a hierarchical relationship between classes or objects, where child classes/objects inherit properties and methods from parent classes/objects.

# **Asynchronous  JavaScript**

## CallBack Hell

**Callback Hell** in JavaScript, particularly in the context of making AJAX calls to fetch data from an API sequentially, where one call depends on the result of another. Here's a breakdown of the key points and the concept of Callback Hell explained:

### **Sequence of AJAX Calls**

- The example provided involves fetching data about a country from an API and then making a second AJAX call to fetch data about a neighboring country based on the first call's result.
- This sequence is necessary because the second call's required data (the neighboring country's code) is obtained from the first call.

### **Callback Hell**

- **Definition**: Callback Hell, also known as "Pyramid of Doom," refers to the problem that arises when multiple asynchronous operations need to be performed one after another, leading to a situation where callbacks are nested within callbacks.
- **Characteristics**: This results in code that is hard to read, maintain, and debug due to the deep nesting and the "triangular" shape that the code structure takes on.
- **Problems**: It makes the code less understandable, which can lead to more bugs and difficulties in adding new features or functionality.

### **Example of Callback Hell**

- In the given example, a function for fetching country data makes an AJAX call, and within the success callback of this call, another AJAX call is made to fetch the neighboring country's data.
- This pattern of nesting callbacks within callbacks is what leads to Callback Hell.

### **Solving Callback Hell**

- **Promises**: Introduced in ECMAScript 2015 (ES6), promises are a feature in JavaScript that provides a cleaner and more manageable way to handle asynchronous operations compared to traditional callback-based approaches.
- **Benefits**: Promises allow asynchronous operations to be chained sequentially in a more readable and maintainable way, helping to avoid Callback Hell.
- **Synchronous JavaScript**: Executes code line by line in the order it's written. If a line of code takes a long time to execute (e.g., **`alert`** statements), it blocks further execution until it completes. This approach can lead to inefficiencies, especially with operations that inherently take time, like network requests.
- **Asynchronous JavaScript**: Allows certain operations, like timers (**`setTimeout`**) or data fetching, to run in the background. Asynchronous operations use callbacks to handle the result once the operation completes, without blocking the main thread. This makes the code non-blocking and responsive, improving user experience for operations like API calls, file reading, etc.

## **Ajax and APIs**

- **Ajax (Asynchronous JavaScript and XML)**: A technique for making asynchronous requests in a web application to a server. Ajax allows for fetching data dynamically without reloading the page, enabling the development of fast and dynamic web applications.
- **APIs (Application Programming Interfaces)**: APIs in web development are endpoints on servers that can be called from client-side code to fetch data or perform operations. They allow applications to communicate with each other and exchange data.
- **Online/Web APIs**: Specifically refer to APIs accessible over the web, which are crucial for fetching data from remote servers. They enable functionalities like retrieving weather data, currency conversion, sending emails, and more in your application.

### **Event Listeners and Asynchronous Behavior**

- **Event Listeners**: Adding an event listener (e.g., for image load events) in itself doesn’t make code asynchronous. What makes certain operations asynchronous is their inherent behavior (like image loading or **`setTimeout`**), not the fact that they are being listened to with event listeners.

### **Data Formats**

- **XML vs. JSON**: While Ajax historically stands for Asynchronous JavaScript and XML, XML is rarely used now for transmitting data. JSON (JavaScript Object Notation) has become the standard due to its simplicity and compatibility with JavaScript, making it easy to work with in web applications.

## **Consuming a promise**

The Fetch API is used to make AJAX calls in JavaScript. The Fetch API provides a modern, promise-based mechanism for making network requests, which simplifies handling asynchronous operations compared to the older **`XMLHttpRequest`** method. Here's a breakdown of the concept:

### **Fetch API and Promises**

1. **Making AJAX Calls**: The **`fetch()`** function is used to make AJAX calls. When called, **`fetch()`** returns a promise that resolves with a **`Response`** object representing the response to the request.
    
    ```jsx
    
    fetch(`https://countries-api-836d.onrender.com/countries/${country}`)
    
    ```
    
2. **Handling Fulfilled Promises**: The **`.then()`** method is used to handle the promise returned by **`fetch()`**. It takes a callback function that receives the resolved value of the promise (in this case, the **`Response`** object).

### **Consuming the Fetch Promise**

- **Accessing the Response Data**: The **`Response`** object provides a **`.json()`** method, which reads the response body and returns another promise that resolves with the result of parsing the response body text as JSON.

### **Chaining `.then()` Methods**

- To access and process the JSON data, you chain another **`.then()`** method after the first one. The second **`.then()`** receives the parsed JSON data as its argument.

### **Simplified Code Example**

```jsx

function getCountryData(country) {
  fetch(`https://countries-api-836d.onrender.com/countries/${country}`)
    .then(response => response.json()) // Parse JSON data from response
    .then(data => console.log(data)); // Handle the JSON data
}

```

### **Key Points**

- **Promises Over Callbacks**: Using promises (via the Fetch API) improves readability and manageability of asynchronous code compared to nested callbacks, reducing the complexity and avoiding "callback hell."
- **Chainability**: Promises can be chained, allowing for sequential asynchronous operations to be performed in a clean and readable way.
- **Asynchronous Function**: The **`.json()`** method is asynchronous and returns a promise, which is handled by chaining another **`.then()`** method.
- **Promises and Callbacks**: While promises use callbacks (**`.then()`** method), they provide a more structured approach to handling asynchronous operations and avoid the pitfalls of nested callbacks (callback hell).

## **Chaining Promises with Fetch API**

To demonstrate chaining promises, let's consider fetching data about a country and its neighboring country from **`"https://countries-api-836d.onrender.com/countries/"`** in sequence. The first AJAX call fetches data about the initial country, and based on that data, a second AJAX call fetches information about a neighboring country.

### **Step-by-Step Explanation**

1. **Fetch Data for the Initial Country**:
Use the Fetch API to make an AJAX call to retrieve data about the specified country. **`fetch()`** returns a promise that resolves with a **`Response`** object.
    
    ```jsx
    
    function getCountryAndNeighbor(country) {
      fetch(`https://countries-api-836d.onrender.com/countries/${country}`)
        .then(response => response.json())
        .then(data => {
          console.log(data); // Handle the data for the first country
          const neighbor = data[0].borders[0]; // Assume first neighbor for simplicity
          if (!neighbor) return;
    
          // Continue to fetch neighbor country inside the first .then()
          return fetch(`https://countries-api-836d.onrender.com/countries/${neighbor}`);
        })
    
    ```
    
2. **Chain a Second AJAX Call**:
Inside the **`.then()`** method for the first fetch, return another **`fetch()`** call to retrieve data about the neighboring country. By returning this fetch call, you create a new promise that can be handled by chaining another **`.then()`** method.
    
    ```jsx
    
        .then(response => response.json())
        .then(data => console.log(data)); // Handle the data for the neighbor country
    }
    
    ```
    

### **Key Points on Chaining Promises**

- **Sequential Execution**: The second AJAX call is made only after the first call completes successfully, ensuring the operations are performed in sequence.
- **Avoiding Nested Callbacks**: By returning the promise from the second **`fetch()`** inside the **`.then()`** and chaining another **`.then()`**, you maintain a flat structure, avoiding the nested callbacks characteristic of "callback hell."
- **Error Handling**: Error handling in promise chains can be streamlined by adding a **`.catch()`** at the end of the chain to catch any errors that occur during any of the asynchronous operations.

### **Example Usage**

```jsx

getCountryAndNeighbor('Portugal');

```

This function fetches data about Portugal and its first neighboring country, handling both operations sequentially using a chain of promises.

### **Conclusion**

Promise chaining is a powerful feature in JavaScript that simplifies handling multiple dependent asynchronous operations, like AJAX calls. It allows for cleaner, more readable code compared to nested callbacks, and provides a systematic way to handle asynchronous data flow and error handling in web applications.

## **Error Handling in Promises**

1. **Promise Rejection**: An error occurring in a promise leads to its rejection. Handling these rejections is crucial in web development to ensure robust applications.
2. **Simulating Errors**: For testing error handling, scenarios like losing an internet connection can be simulated by setting the network status to offline in browser dev tools.
3. **Adding Event Listeners for User-Initiated Requests**: To better control the timing of AJAX requests (for simulating errors, for example), you can tie the request to a button click event.

### **Two Methods to Handle Promise Rejections**

1. **Using `.then()` Second Callback**: The **`.then()`** method can accept a second callback function specifically for handling errors or promise rejections.
    
    ```jsx
    
    fetch(`https://countries-api-836d.onrender.com/countries/${country}`)
      .then(response => response.json(), err => console.error(err));
    
    ```
    
2. **Using `.catch()`**: A more elegant and centralized way to handle errors from any promise in the chain is to use the **`.catch()`** method at the end of the promise chain.
    
    ```jsx
    
    fetch(`https://countries-api-836d.onrender.com/countries/${country}`)
      .then(response => response.json())
      .catch(err => console.error(err));
    
    ```
    

### **Handling Specific Errors**

- The Fetch API treats most HTTP errors (like 404 Not Found) as successful promises, so these don't automatically trigger **`.catch()`**. To handle such cases, you need to explicitly check the response status and throw an error if it indicates a failure.
    
    ```jsx
    
    .then(response => {
      if (!response.ok) throw new Error(`Country not found (${response.status})`);
      return response.json();
    })
    
    ```
    

### **Global Error Handling with `.catch()`**

- Using **`.catch()`** at the end of a promise chain allows for a centralized error handling mechanism, catching any error that occurs in any of the preceding promises.

### **Finally Method**

- The **`.finally()`** method can be used to execute code regardless of the promise's outcome, fulfilling or rejecting. It's helpful for actions that should occur after all asynchronous operations are complete, such as hiding loading spinners.
    
    ```jsx
    
    .finally(() => {
      // Actions that should always occur, regardless of promise outcome
    });
    
    ```
    

### **Practical Example: Fetching Data and Handling Errors**

```jsx

function getCountryData(country) {
  fetch(`https://countries-api-836d.onrender.com/countries/${country}`)
    .then(response => {
      if (!response.ok) throw new Error(`Country not found (${response.status})`);
      return response.json();
    })
    .then(data => {
      console.log(data); // Process country data
      const neighbor = data[0].borders[0];
      if (!neighbor) throw new Error('No neighbor found.');
      return fetch(`https://countries-api-836d.onrender.com/countries/${neighbor}`);
    })
    .then(response => response.json())
    .then(data => console.log(data)) // Process neighbor country data
    .catch(err => console.error('Error:', err))
    .finally(() => console.log('Fetch attempt finished.'));
}

```

# Asynchronous JavaScript - Behind the scenes

## **JavaScript Runtime Components**

- **JavaScript Engine**: Executes code and stores objects in memory. It operates on a single thread, meaning it can only execute one task at a time.
- **Web APIs**: Provided by the browser, these APIs handle tasks like DOM manipulation, AJAX calls, and timers asynchronously, outside the JavaScript engine.
- **Callback Queue**: Holds callback functions ready to be executed. These are functions associated with asynchronous operations that have completed.
- **Event Loop**: Coordinates between the call stack and callback queue. When the call stack is empty, the event loop transfers callbacks from the queue to the stack for execution.

### **Asynchronous Behavior**

- Asynchronous tasks, like image loading or fetching data with AJAX, are processed outside the JavaScript engine in the Web APIs environment. This approach prevents blocking the main thread, allowing the rest of the code to run while waiting for these tasks to complete.
- Event listeners and **`fetch()`** operations are examples of asynchronous tasks that use callbacks. These callbacks are registered with the corresponding events or promises and executed once the asynchronous task completes.

### **Handling Asynchronous Tasks**

- **Event Listeners**: When an event occurs (e.g., an image loads), the associated callback is moved to the callback queue, waiting for the event loop to execute it.
- **Promises**: Callbacks associated with promises are treated as microtasks, which have their own queue (the microtasks queue) with higher priority than the callback queue. The event loop checks and executes all microtasks before moving on to the callback queue.

### **Event Loop and Microtasks**

- The event loop plays a critical role in ensuring asynchronous code runs in a non-blocking manner. It continuously checks if the call stack is empty and then moves callbacks from the microtasks queue and, subsequently, the callback queue to the call stack for execution.
- Microtasks created by promises can "cut in line" before callbacks in the callback queue, ensuring promise resolutions are handled promptly.

### **Practical Implications**

- Understanding the event loop and the distinction between tasks and microtasks is crucial for writing efficient asynchronous JavaScript code. It explains why certain operations may take precedence over others and how JavaScript manages to handle asynchronous operations despite being single-threaded.

### **Example**

Here's a simplified example to illustrate how you might use **`fetch()`** to handle asynchronous data fetching, with error handling and a simulated loading process:

```jsx
javascriptCopy code
function fetchData(url) {
  fetch(url)
    .then(response => {
      if (!response.ok) throw new Error(`Failed to fetch (${response.status})`);
      return response.json();
    })
    .then(data => console.log('Data:', data))
    .catch(err => console.error('Error:', err))
    .finally(() => console.log('Fetch attempt completed.'));
}

// Usage
fetchData('https://countries-api-836d.onrender.com/countries/USA');

```

# Design Patterns in JavaScript

## Retry in Promises

Implementing a retry mechanism for promises in JavaScript can be particularly useful when dealing with operations that may fail under transient conditions, such as network requests, API calls, or other asynchronous operations that can intermittently fail due to temporary issues.

To create a retry mechanism using promises, you can write a function that accepts the promise-returning function as a parameter, along with the maximum number of attempts. Here’s a basic example of how you could implement such functionality:

**Basic Retry Function:**

```jsx
function retry(promiseFunc, maxAttempts, delay = 1000) {
    return new Promise((resolve, reject) => {
        let attempts = 0;

        function attempt() {
            attempts++;
            promiseFunc()
                .then(resolve)
                .catch((error) => {
                    if (attempts < maxAttempts) {
                        setTimeout(attempt, delay); // Wait before retrying
                    } else {
                        reject(`Failed after ${attempts} attempts`);
                    }
                });
        }

        attempt();
    });
}
```

### **Explanation**

- **promiseFunc**: This is the function that returns a promise. It's called within the **`attempt`** function to execute the operation you want to retry.
- **maxAttempts**: The maximum number of times to attempt the operation before giving up.
- **delay**: The delay between retries in milliseconds. Default is set to 1000 milliseconds (1 second).

The function **`attempt()`** is defined within **`retry()`** and is called recursively if the promise returned by **`promiseFunc()`** rejects. It will continue to retry until it either resolves (in which case it will **`resolve`** the outer promise) or until it exceeds the maximum number of allowed attempts (in which case it will **`reject`** the outer promise).

### **Usage Example**

Let’s say you have a function **`fetchData()`** that returns a promise which might fail:

```jsx
function fetchData() {
    return new Promise((resolve, reject) => {
        // Simulating a network request that might fail
        if (Math.random() > 0.5) {
            resolve("Success!");
        } else {
            reject("Network Error");
        }
    });
}
```

You can use the **`retry`** function to attempt to resolve **`fetchData`**:

```jsx
retry(fetchData, 5, 2000)
    .then(data => console.log(data))
    .catch(error => console.error(error));

```

In this example, **`fetchData`** will be retried up to 5 times with a delay of 2 seconds between attempts. If it fails all attempts, it will log the error message.

### **Considerations**

- **Error Handling**: It's crucial to handle possible errors within your retry logic to avoid unhandled promise rejections.
- **Delay Strategy**: You might want to implement a more sophisticated backoff strategy, such as exponential backoff, where the delay between retries increases exponentially.
- **Maximum Attempts**: Be cautious with the number of retries and delay times, especially in production environments, to avoid excessive load on your servers or the services you are consuming.

Using this retry mechanism, you can make your applications more robust against transient failures in external services or other operations prone to temporary disruptions.