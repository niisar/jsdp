## Chaining Pattern [Example](https://plnkr.co/edit/T3Q8AjJpNX7dsJrorGfr?p=preview)

Method chaining is a common technique for invoking multiple method calls in object-oriented programming languages. Each method returns an object (possibly the current object itself), allowing the calls to be chained together in a single statement (Wikipedia definition). This technique was made popular in several libraries, like jQuery.

``` js
<html>
<head>
    <title>chaining pattern</title>
</head>
<body>
    <strong>Result</strong>
    <div id='result'>
    </div>
</body>
<script type="text/javascript">
    var Calculator = function (start) {
        var that = this;

        this.add = function (x) {
            start = start + x;
            return that;
        };

        this.multiply = function (x) {
            start = start * x;
            return that;
        };

        this.equals = function (calback) {
            calback(start);
            return that;
        };
    };

    (function () {
        var resultDiv = document.getElementById('result');
        new Calculator(0)
            .add(1)
            .add(2)
            .multiply(3)
            .equals(function (result) {
                resultDiv.innerHTML = result;
            });
    })();

</script>

</html>
```

### [View and Download Demo](https://plnkr.co/edit/T3Q8AjJpNX7dsJrorGfr?p=preview)