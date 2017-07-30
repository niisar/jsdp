## Timer Pattern

* ###Asynchronous Execution Pattern

    Browser are single threaded, that means that the browser can only be doing either updates to the UI or executing JavaScript at any given point of time because it's incapable of doing both simultaneously.

    The long-running JavaScript can cause the UI to become unresponsive or appear to be unresponsive.

    One way we can get around this is to create a function which will allow us to defer the execution on multiple periods of time.

