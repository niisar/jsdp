## Observable Properties Pattern [Example](https://plnkr.co/edit/4iUanTTjYr8XmUNPXFbI?p=preview)

If you’re familiar with C#, think about the INotifyPropertyChanging and INotifyPropertyChanged interface to implement observable properties.

Here are some points before we implement observable properties in JavaScript:

- Properties  implemented as methods
- Check the incoming value and decide if you want to update
- Return private variable
- Store event handlers in an array
- Utilise return values to abort the updating process

``` js
< html>
    <head>
        <title>Observable properties pattern</title>
    </head>

    <body>
        <strong>Result</strong>
        <div id='result'>
        </div>
        <hr>
        <strong>Changed</strong>
        <div id="changed">
        </div>
    </body>
    <script type="text/javascript">
        var Book = function(name, price) {

            var priceChanging = [],
                priceChanged = [];

            this.name = function(val) {
                return name;
            };

            this.price = function(val) {
                if (val !== undefined && val !== price) {
                    for (var i = 0; i < priceChanging.length; i++) {
                        if (!priceChanging[i](this, val)) {
                            return price;
                        }
                    }

                    price = val;

                    for (var i = 0; i < priceChanged.length; i++) {
                        priceChanged[i](this);
                    }
                }
                return price;
            };

            this.onPriceChanging = function(callback) {
                priceChanging.push(callback);
            };

            this.onPriceChanged = function(callback) {
                priceChanged.push(callback);
            };
        };

        (function() {
            var resultDiv = document.getElementById('result'),
                changedDiv = document.getElementById('changed');

            var book = new Book('Java Script: The Good Parts', 23.99);

            resultDiv.innerHTML = 'The name is: ' + book.name() + "<br />";
            resultDiv.innerHTML += 'The price is $ ' + book.price();

            book.onPriceChanging(function(b, price) {
                if (price > 100) {
                    changedDiv.innerHTML += 'System error, price has gone unexpectedly high<br/>';
                    return false;
                }

                return true;
            });

            book.onPriceChanged(function(b) {
                changedDiv.innerHTML += 'The price is $' + b.price() + "<br/>";
            });

            book.price(19.99);
            book.price(200);
            book.price(77);
        })();
    </script>

    </html>
```

### [View and Download Demo](https://plnkr.co/edit/4iUanTTjYr8XmUNPXFbI?p=preview)