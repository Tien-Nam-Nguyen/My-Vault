---
type:
  - Tech
tags:
  - Java
  - OOP
published: true
created: 2023-11-01 16:34
modified: 2023-11-02T21:45:00
folder: Tech
---
# What is design patterns?

- Design patterns are optimal programming prototypes to solve some usual problems in OOP.
- Design patterns can be implemented in any programming language.

# Some design patterns

## Creational pattern

### Singleton
[https://gpcoder.com/4190-huong-dan-java-design-pattern-singleton/](https://gpcoder.com/4190-huong-dan-java-design-pattern-singleton/)

- Ensure having just one created instance and methods which can be accessed in the entire program.

![Singleton|300][https://gpcoder.com/wp-content/uploads/2018/09/singleton-pattern.png]

### Factory method
[https://gpcoder.com/4352-huong-dan-java-design-pattern-factory-method/](https://gpcoder.com/4352-huong-dan-java-design-pattern-factory-method/)

- Manage and return required objects by implementing class factory that provides method to return subclass object.

![Factory|650][https://gpcoder.com/wp-content/uploads/2018/09/design-patterns-factory-method-diagram.png]

### Abstract factory
[https://gpcoder.com/4365-huong-dan-java-design-pattern-abstract-factory/](https://gpcoder.com/4365-huong-dan-java-design-pattern-abstract-factory/)

- A super-factory class is created to return other factories. This is the higher level pattern of [[Design pattern#Factory method | Factory method]]

![Abstract factory|650][https://gpcoder.com/wp-content/uploads/2018/09/design-patterns-abstract-factory-diagram.png]

### Builder
[https://gpcoder.com/4434-huong-dan-java-design-pattern-builder/](https://gpcoder.com/4434-huong-dan-java-design-pattern-builder/)

- Is a pattern to create complex objects (with many parameters) by creating object with just one parameter each time until all parameter are passed.

![Builder][https://gpcoder.com/wp-content/uploads/2018/09/design-patterns-builder-diagram.png]

### Prototype 
[https://gpcoder.com/4413-huong-dan-java-design-pattern-prototype/](https://gpcoder.com/4413-huong-dan-java-design-pattern-prototype/)

### Object pool
[https://gpcoder.com/4456-huong-dan-java-design-pattern-object-pool/](https://gpcoder.com/4456-huong-dan-java-design-pattern-object-pool/)

## Structural pattern

### Adapter
[https://gpcoder.com/4483-huong-dan-java-design-pattern-adapter/](https://gpcoder.com/4483-huong-dan-java-design-pattern-adapter/)

- Adapter allows interfaces of unrelated classes can work together. The object which helps connecting is called an adapter.

![Adapter][https://gpcoder.com/wp-content/uploads/2018/10/design-patterns-adapter-diagram-translator-example.png]

### Bridge
[https://gpcoder.com/4520-huong-dan-java-design-pattern-bridge/](https://gpcoder.com/4520-huong-dan-java-design-pattern-bridge/)

### Composite
[https://gpcoder.com/4554-huong-dan-java-design-pattern-composite/](https://gpcoder.com/4554-huong-dan-java-design-pattern-composite/)

### Decorator
[https://gpcoder.com/4574-huong-dan-java-design-pattern-decorator/](https://gpcoder.com/4574-huong-dan-java-design-pattern-decorator/)

### Facade 
[https://gpcoder.com/4604-huong-dan-java-design-pattern-facade/](https://gpcoder.com/4604-huong-dan-java-design-pattern-facade/)

### Flyweight
[https://gpcoder.com/4626-huong-dan-java-design-pattern-flyweight/](https://gpcoder.com/4626-huong-dan-java-design-pattern-flyweight/)

### Proxy
[https://gpcoder.com/4644-huong-dan-java-design-pattern-proxy/](https://gpcoder.com/4644-huong-dan-java-design-pattern-proxy/)

## Behavioral pattern

### Chain of Responsibility
[https://gpcoder.com/4665-huong-dan-java-design-pattern-chain-of-responsibility/](https://gpcoder.com/4665-huong-dan-java-design-pattern-chain-of-responsibility/)

- Allows an object to send a request without knowing which object will receive and process it. It is implemented by concatenating objects into a chain and sending requests along the chain until an object processes it
![Chain][https://gpcoder.com/wp-content/uploads/2018/12/design-patterns-chain-of-responsibility-example-1.png]

![Chain of responsibility][https://gpcoder.com/wp-content/uploads/2018/12/design-patterns-chain-of-responsibility-diagram.png]

### Command 
[https://gpcoder.com/4686-huong-dan-java-design-pattern-command/](https://gpcoder.com/4686-huong-dan-java-design-pattern-command/)

### Interpreter
[https://gpcoder.com/4702-huong-dan-java-design-pattern-interpreter/](https://gpcoder.com/4702-huong-dan-java-design-pattern-interpreter/)

### Iterator
[https://gpcoder.com/4724-huong-dan-java-design-pattern-iterator/](https://gpcoder.com/4724-huong-dan-java-design-pattern-iterator/)

### Mediator
[https://gpcoder.com/4740-huong-dan-java-design-pattern-mediator/](https://gpcoder.com/4740-huong-dan-java-design-pattern-mediator/)

### Memento
[https://gpcoder.com/4763-huong-dan-java-design-pattern-memento/](https://gpcoder.com/4763-huong-dan-java-design-pattern-memento/)

### Observer
[https://gpcoder.com/4747-huong-dan-java-design-pattern-observer/](https://gpcoder.com/4747-huong-dan-java-design-pattern-observer/)

### State
[https://gpcoder.com/4785-huong-dan-java-design-pattern-state/](https://gpcoder.com/4785-huong-dan-java-design-pattern-state/)

### Strategy
[https://gpcoder.com/4796-huong-dan-java-design-pattern-strategy/](https://gpcoder.com/4796-huong-dan-java-design-pattern-strategy/)

### Template method
[https://gpcoder.com/4810-huong-dan-java-design-pattern-template-method/](https://gpcoder.com/4810-huong-dan-java-design-pattern-template-method/)

### Visitor
[https://gpcoder.com/4813-huong-dan-java-design-pattern-visitor/](https://gpcoder.com/4813-huong-dan-java-design-pattern-visitor/)

- Allows defining operations on a set of objects of different types without changing the class definition. This also allows recovery of lost data type.

- VisitorImple class implements visit methods for each different type of objects. In visit method, the object's own method will be called.

 - In each class of different type objects implement accept method having parameter which is a visitor. Accept method will call the parameter's visit method.

- Only use accept method after all

![visitor][https://gpcoder.com/wp-content/uploads/2019/01/design-patterns-visitor-example.png]



