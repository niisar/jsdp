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
1. Function declaration 2. Function definition. Here are using function definition expression.
It declares a function, which then calls itself immediately.