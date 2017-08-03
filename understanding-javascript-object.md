

Javascript properties are enumerable, writable and configurable by default.

For Example.. Below we are able to assign any value to `toString` function.

``` js
var task = {
 title: 'My title',
 description: 'My Description'
}

Object.defineProperty(task, 'toString', {
  value: function(){
    return this.title + ' ' + this.description;
  },
  writable: true,
  enumerable: true,
  configurable: true
});

task.toString = 'hi';
console.log(task.toString());
```

