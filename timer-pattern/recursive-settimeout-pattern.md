### Recursive setTimeout pattern

The Recursive setTimeout pattern is most commonly used when we want periodically running a piece of functionality, related to duration (most commonly used to query a data source).

This may sounds like what setInterval does, but there is a problem with using setInterval. 

* setInterval ignores errors. 
* setInterval does not care about network latency. 

Because JavaScript is asynchronous, setInterval method actually does not wait for the previous function to finish it's execution before begins the next time period. What if the function was waiting for an AJAX response? Function execution can get out of order.

So, the idea is to use setTimeout. setTimeout can ensure order of execution.

``` js
$(document).ready(function() {
    setTimeout(function getDate() {
        $get('someUrl', function(date) {
            setTimeout(getDate, 5000);
        });
    }, 5000);
});
```