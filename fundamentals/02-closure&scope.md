01 - `#  What are closures? Give a practical example.`
    A closure allows an inner function to access variables of its outer function even after the outer function has returned.

eg :: function outer() {
    let count = 0;

    function inner() {
        count++;
        console.log(count);
    }

    return inner;
}

const counter = outer();

counter(); // 1
counter();//2
counter();//3

`Practical Example 1: Event Listener`
 function attachEvent() {
    let clicks = 0;

    document.getElementById("btn").addEventListener("click", function () {
        clicks++;
        console.log(clicks);
    });
}

attachEvent();

`Each button click increases the clicks variable, even though attachEvent() has already finished.`

# Practical Example 3: setTimeout

function delayedGreeting(name) {
    setTimeout(function () {
        console.log(`Hello ${name}`);
    }, 2000);
}

delayedGreeting("Amit");


`Why are Closures Useful?
`
**Closures are commonly used for:**

-Data privacy
-Maintaining state
-Event listeners
-Callbacks
-Timers (setTimeout, setInterval)
-Function factories
-Memoization
-Currying

# What is Currying?
Currying is a technique in JavaScript where a function that takes multiple arguments is transformed into a sequence of functions, each taking one argument.

function add(a) {
    return function (b) {
        return function (c) {
            return a + b + c;
        };
    };
}

console.log(add(2)(3)(4));

**Currying converts a function with multiple parameters into a chain of functions, each taking one parameter.**


# Lexical Scope

A function can access variables from the scope in which it was created.

let x = 100;

function outer() {
    let y = 200;

    function inner() {
        console.log(x);
        console.log(y);
    }

    return inner;
}

const fn = outer();

fn(); // 100 200

**
Scope = Where a variable is accessible.
Scope Chain = The path JavaScript follows to find a variable.**

