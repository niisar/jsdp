## Observable Properties Pattern ECMA5 


With ECMAScript5 properties can have methods body (similar to how .NET properties look) and it's very powerful

``` js
function Book() {
    var name = '';

    Object.defineProperty(this, 'name', {
        get: function() {
            return name;
        },
        set: function(val) {
            name = val;
        }
    });
}
```
