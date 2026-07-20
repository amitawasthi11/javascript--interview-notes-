 #  What are Promises? Explain promise states.

  A Promise is a JavaScript object that represents the eventual completion (success)
 or failure   of an asynchronous operation and its resulting value.
   
   Think of a Promise as a placeholder for a value that isn't available yet but will be available in the future.
  
**Creating a Promise**

const promise = new Promise((resolve, reject) => {

    const success = true;

    if (success) {
        resolve("Operation Successful");
    } else {
        reject("Operation Failed");
    }

});

Real-World Example

Fetching data from an API:

fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => response.json())
    .then(user => console.log(user))
    .catch(error => console.log(error));

The fetch() API returns a Promise.

Callback                              Promise
Callback	                            Promise
Can lead to callback            hell	Supports chaining
Manual error handling	            Centralized .catch()
Harder to read	               Cleaner and more maintainable
Older approach	                  Modern approach


