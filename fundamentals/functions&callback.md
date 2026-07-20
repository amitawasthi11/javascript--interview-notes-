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

