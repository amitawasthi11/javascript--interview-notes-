# What is the 'this' keyword and how does it work?
   this is a special keyword that refers to the object that is currently executing the function.

 Inside an Object Method

**When a function is called as a method of an object, this refers to that object.**

const person = {
    name: "Amit",
    greet() {
        console.log(this.name);
    }
};

person.greet(); // amit

# Arrow functions do not have their own this.

Arrow functions are a shorter way to write functions in JavaScript, introduced in ES6 (ECMAScript 2015)

const add = (a, b) => {
    return a + b;
};

# Arrow functions do not have their own this. They inherit this from the surrounding (lexical) scope.

normal function :
Can be called before it is declared

    greet(); // works
   function greet() {
    console.log("Hello");
    }

 but arrow function cannot be called before declareation 

 Q1. Why don't arrow functions have their own this?

Answer: Arrow functions capture this from their surrounding lexical scope. This makes them useful in callbacks where you want to preserve the enclosing this.   

Q2. Can arrow functions be constructors?

Answer: No. Arrow functions cannot be used with the new keyword because they don't have a [[Construct]] method or a prototype.

Q4. Should you use arrow functions as object methods?

Answer: Generally, no. Since arrow functions don't have their own this, this usually won't refer to the object.

const person = {
    name: "Amit",
    greet: () => console.log(this.name)
};

person.greet(); // undefined


# When should you use arrow functions instead of regular functions?

Answer:
Use arrow functions for callbacks, array methods, promises, and short utility functions.
Use regular functions for object methods, constructors, and whenever you need your own this or the arguments object.



# What are Higher-Order Functions?
   A Higher-Order Function (HOF) is a function that either:
  Takes one or more functions as arguments, or
  Returns a function as its result.

` #  Function as an Argument`
function greet(name) {
    return `Hello, ${name}`;
}

function processUser(callback) {
    console.log(callback("Amit"));
}

processUser(greet); 

************* map *****************
Using a Higher-Order Function (map):

const prices = [100, 200, 300];

const discounted = prices.map(price => price * 0.9);

console.log(discounted);

Output

[90, 180, 270]

map() is a higher-order function because it accepts a callback.

# common Higher-Order Functions in JavaScript

1. map()

Transforms each element and returns a new array.

const nums = [1, 2, 3];
const square = nums.map(num => num * num);
console.log(square);
Output:
[1, 4, 9]

2. filter()
Returns elements that satisfy a condition.
const nums = [1, 2, 3, 4, 5];
const even = nums.filter(num => num % 2 === 0);
console.log(even);

3. reduce()

Reduces an array to a single value.
const nums = [1, 2, 3, 4];
const sum = nums.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 10

4. forEach()

Executes a callback for each element.

const nums = [1, 2, 3];
nums.forEach(num => {
    console.log(num);
});
Output: [1,2,3]


5. sort()

Accepts a comparison function.

const nums = [4, 1, 3, 2];
nums.sort((a, b) => a - b);
console.log(nums);
Output:
[1, 2, 3, 4]

# Name some built-in higher-order functions in JavaScript.
Answer: map(), filter(), reduce(), forEach(), sort(), find(), some(), every(), setTimeout(), and setInterval().



# What are Callbacks?

A callback is a function that is passed as an argument to another function and is executed later, usually after a task has completed.

Callbacks are commonly used for:
Asynchronous operations
Event handling
Array methods (map, filter, forEach, etc.)

# What is Callback Hell?
Callback Hell is a situation where multiple asynchronous callbacks are nested inside one another, making the code difficult to read, understand, and maintain.

eg :
loginUser(function(user) {

    getOrders(user.id, function(orders) {

        getPayment(orders[0].id, function(payment) {

            updateWallet(payment, function(result) {

                console.log(result);

            });

        });

    });

});