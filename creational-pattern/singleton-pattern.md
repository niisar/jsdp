## Singleton Pattern

This pattern restricts instantiation of an object to a single reference thus reducing its memory footprint and allowing a "delayed" initialization on an as-needed basis. This isn't too common amongst JavaScript projects today but more common in WordPress.

#### Advantages

* Reduced memory footprint
* Single point of access
* Delayed initialization that prevents instantiation until required

#### Disadvantages

* Once instantiated, they're hardly ever "reset"
* Harder to unit test and sometimes introduces hidden dependencies

#### Example

``` js
var mySingleton = ( function( window, undefined ) {
  
  var instance = null;
  
  // revealing module pattern that handles initialization of our new module
  function initializeNewModule() {
    
    function myMethod() {
      alert( 'my method' );
    }
    
    function myOtherMethod() {
      alert( 'my other method' );
    }
    
    return {
      someMethod : myMethod,
      someOtherMethod : myOtherMethod
    };
    
  }
  
  // handles the prevention of additional instantiations
  function getInstance() {
    if( ! instance ) {
      instance = new initializeNewModule();
    }
    return instance;
  }
  
  return {
    getInstance : getInstance
  };
  
} )( window );

// example usage
mySingleton.getInstance().someMethod(); // alerts "my method"
mySingleton.getInstance().someOtherMethod(); // alerts "my other method"
```