## Factory Pattern

This pattern focuses on object creation but differs from other patterns because it does not require a constructor function. The factory pattern generally supplies an interface for developers to create new objects through the use of the factory rather than invoking the new operator on an object. 

Imagine that you needed a car door so you might goto a car factory that produces the product you're interested in and ask it to give you what you need. The factory then supervises the creation of the new car door (or object) and gives it to you. This example paints a good picture for how the factory pattern works; you simply ask it for a type of component, it instantiates the component (given it exists), and returns you what you were looking for.

#### Advantages

* Makes complex object creation easy through an interface that can bootstrap this process for you
* Great for generating different objects based on the environment
* Practical for components that require similar instantiation or methods
* Great for decoupling components by bootstrapping the instantiation of a different object to carry out work for particular instances
#### Disadvantages

* Unit testing can be difficult as a direct result of the object creation process being hidden by the factory methods


