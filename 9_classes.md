> # Classes

Javascript is a multi-paradigm programming language, but the architecture used for OOP is a bit different than the standard OOP paradigm found in other higher-level programing languages. In JavaScript we call it `Prototypes`, and altough the concepts are very similar, the application is a bit different, and because of it a lot of people had trouble using JavaScript for OOP.

Because of this, there has been multiple proposals along the years to make a proper OOP paradigm to JavaScript implementing conventional Classes and Hierarchies, and finally with ES6 we are now heading into the right direction.

ES6 brought a new Object called `Class`, that while its not a native Class found on other languages with OOP paradigm, it creates an abstraction that gives the programmer a more familiar look.

Note that while it looks like a proper Class, the compiler transpiles the Class Object into prototypes in run time.

Its also missing multiple functionalities found in native Classes like private field/methods, final statments, interfaces, ... 


## Class Definition
The definition of a `Class` its identical to other programming languages, its composed of multiple methods, and a constructor that initializes it.

<pre>
  class Shape {
    constructor (id, x, y) {
        this.id = id
        this.move(x, y)
    }
    move (x, y) {
        this.x = x
        this.y = y
    }
  }
</pre>

### ES5 Prototype Equivalent
<pre>
  //Object Initializer => Equivalent to Class `constructor`
  var Shape = function (id, x, y) {
    this.id = id;
    this.move(x, y);
  };
  
  // Every method is then defined as prototypes of the object
  Shape.<b>prototype</b>.move = function (x, y) {
      this.x = x;
      this.y = y;
  };
</pre>


## Class Inheritance
Inheritance on a `Class` its much more intuitive then on `Prototypes`, using the reserved word `extend` and the method `super()` to initialize the parent constructor

<pre>
  class Rectangle <b>extends</b> Shape {
    constructor (id, x, y, width, height) {
        <b>super(id, x, y)</b>
        this.width  = width
        this.height = height
    }
  }
</pre>

## Static Members
Its also possible to create static methods. These are methods that can be accessed w/t instantiating the `Class`

```
  class Rectangle extends Shape {
    …
    static defaultRectangle () {
        return new Rectangle("default", 0, 0, 100, 100)
    }
  }
```
var defRectangle = ~~new~~ Rectangle.defaultRectangle();



