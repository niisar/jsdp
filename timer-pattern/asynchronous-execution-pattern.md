### Asynchronous Execution Pattern [Example](https://plnkr.co/edit/zwU1E2O16Z076ind5UYp?p=preview)

Browser are single threaded, that means that the browser can only be doing either updates to the UI or executing JavaScript at any given point of time because it's incapable of doing both simultaneously.

The long-running JavaScript can cause the UI to become unresponsive or appear to be unresponsive.

So the idea of the asynchronous execution pattern is to split out long-running JavaScript block using several setTimeouts calls.

``` js
<html>
<body>
    <ul id="ul">
    </ul>
</body>
<script>
    var demoArray = [];
    for (var i = 1; i <= 1000; i++) {
        demoArray.push(1 + Math.floor(Math.random() * 50));
    }

    (function() {
        var buffer = function(items, iterFunction, callback) {
            var i = 0.
            len = items.length;
            setTimeout(function() {
                var result;
                // +new Date returns the number of milliseconds   
                //((+new Date) - start < 50 => buffer of 50 milliseconds            
                for (var start = +new Date; i < len && result !== false && ((+new Date) - start < 50); i++) {
                    result = iterFunction.call(items[i], items[i], i);
                }
                /* callee is a property of the arguments object. It can be used to refer to the currently executing function inside the function body of that function. This is for example useful when you don't know the name of this function, which is for example the case with anonymous functions. */
                if (i < len && result !== false) {
                    setTimeout(arguments.callee, 20);
                } else {
                    callback();
                }
            }, 20);
        };
        var html = '';
        buffer(demoArray, function(item) {
            html += '<li>' + item + '</li>';
        }, function() {
            document.getElementById('ul').innerHTML = html;
        });
    })();
</script>
</html>
```

### [View and Download Demo](https://plnkr.co/edit/zwU1E2O16Z076ind5UYp?p=preview)