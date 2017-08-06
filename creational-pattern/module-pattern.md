## Module Pattern

Module pattern is like a toolbox of function to use. It is just an object literal..

In order to understand Module design pattern, we need to understand these concept first:
* **IIFE (Immediately-Invoked Function Expression)**
* **Closure**

### IIFE

```js
(function () {
  // code
})();
```

There are two ways you can use the functions. 
  
  1. Function declaration 
  2. Function definition. 
  
Here are using _function definition_ expression. It declares a function, which then calls itself immediately.

Now if we add the namespace to the above piece of code then

```js
var Module = (function () {
  // code
})();
```

We then have Module declared in the global scope, which means we can call it wherever we like, and even pass it into another Module.

### Closure
A closure is an inner function that has access to the outer function’s variables in addition to it's own variables and global variables. The inner function has access not only to the outer function’s variables, but also to the outer function’s parameters. This is happen because in Javascript is using something called lexical scoping also known as static scope that means inner functions contain the scope of parent functions.

``` js
var scope = "I am global";
function whatismyscope() {
    var scope = "I am just a local";
    function func() {return scope;}
    return func;
}
whatismyscope()()
```

### Applying Above two concept (IIFE + Closure) Becomes [Module Pattern](https://plnkr.co/edit/ThUZI1DpYRlZbDptFbLn?p=preview)

``` js
var modularpattern = (function() {
    // your module code goes here
    var sum = 0 ;

    return {
        add:function() {
            sum = sum + 1;
            return sum;
        },
        reset:function() {
            return sum = 0;    
        }  
    }   
}());
console.log(modularpattern.add());
console.log(modularpattern.add());
console.log(modularpattern.reset());
```