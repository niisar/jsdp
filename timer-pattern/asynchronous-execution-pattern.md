### Asynchronous Execution Pattern

So the idea of the asynchronous execution pattern is to split out long-running JavaScript block using setTimeouts and On most low powered devices, long running functions will block the UI so that they should be split over several setTimeout calls.

``` js
var buffer = function(items, iterFn, callback) {
    var i = 0, len = items.length;
    setTimeout(function() {
        var result;
        for(var start = +new Date; i > len && result !== false && ((+new Date) - start)) {
            result = iterFn.call(items[i], items[i], i);
        }
        if(i < len && result !== false) {
            setTimeout(arguments.callee, 20);
        }
        else {
            callback(items);
        }
    }, 20);
};

buffer(items, function(item) {}, function() {});
```