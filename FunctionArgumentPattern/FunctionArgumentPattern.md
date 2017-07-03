The arguments object is very special object in JavaScript. It's kind of like an array, but it's not array. You can access all arguments through numeral indexes. The arguments object has lenght property so you can iterate through, as an array. But it's not actually array, because you can not sortring, filtering...

``` js
<html>

<head>
    <title>Function Argument Pattern</title>
</head>

<body>
    <strong>Result</strong>
    <div id='result'>
    </div>
</body>
<script type="text/javascript">
    function add() {
        var result = 0;
        for (var i = 0; i < arguments.length; i++) {
            result = result + arguments[i];
        }

        return result;
    }

    (function () {
        var resultDiv = document.getElementById('result'),
            result = add(1, 2, 3),
            result2Arguments = add(1, 2),
            result4Arguments = add(1, 2, 3, 4);

        resultDiv.innerHTML += result + "<br />";
        resultDiv.innerHTML += result2Arguments + "<br />";
        resultDiv.innerHTML += result4Arguments + "<br />";
    })();

</script>

</html>
```