var, let, and const are used to declare variables in JavaScript. They differ in scope, hoisting, redeclaration, and reassignment

**1. var**
var is the older way of declaring variables (before ES6).

# Characteristics
-Function-scoped
-Can be redeclared
-Can be reassigned
-Hoisted and initialized with undefined

2. let
Introduced in ES6 (2015).

# Characteristics
-Block-scoped
-Cannot be redeclared in the same scope
-Can be reassigned
-Hoisted but stays in the Temporal Dead Zone (TDZ) until declared

**3. const**

Also introduced in ES6.

# Characteristics
-Block-scoped
-Cannot be redeclared
-Cannot be reassigned
-Must be initialized when declared
-Hoisted but in the Temporal Dead Zone

**note : const prevents changing the reference, not the object's contents.**

`const person = {
    name: "Amit"
};

person.name = "Rahul";

console.log(person);

output :
 {
  name: "Rahul"
}`
```


# Temporal Dead Zone (TDZ)

The Temporal Dead Zone is the period between entering a scope and executing a let or const declaration. During this time, the variable exists but cannot be accessed.

`2. Why does var print undefined but let throws an error before declaration?`

:-Because var is hoisted and initialized with undefined, while let is hoisted but remains in the Temporal Dead Zone until its declaration.


# What is hoisting?

Hoisting is JavaScript's behavior of moving declarations to the top of their scope before execution. With var, the variable is initialized as undefined. With let and const, the declaration is hoisted but not initialized, so accessing them before declaration throws a ReferenceError.


