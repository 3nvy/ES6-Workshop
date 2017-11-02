> # Classes

JavaScript é uma linguagem de programação de multi-paradigma, no entanto quando se fala em POO usa um estilo de programação chamado `Prototype`, que não é o mais convencional no mundo de POO. 

Por causa disto, muita gente tem dificuldades em usar JS para fazer POO e o suporte para Classes e Herança mais convencionais em POO tem sindo um dos requesitos mais pedidos para a linguagem.

Com a chegada do ES6, veio tambem um novo tipo de objecto chamado `Class`, que apesar de não ser um objecto de Class nativo como noutras linguagens, cria uma espécie de abstração permitindo ao utilizador programar como se estivesse efectivamente a trabalhar numa Class, enquanto que o objecto é posteriormente convertido em prototipos em tempo de execução.

## Class Definition
A definição de um objecto de tipo `Class` é identico ao de outras linguagens, é um objecto com vários metodos sendo que um deles é o contrutor da class, servindo como inicializador da mesma.

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
  //Inicializador do objecto => equivalente ao constructor da class
  var Shape = function (id, x, y) {
    this.id = id;
    this.move(x, y);
  };
  
  //Todos os metodos do objecto são posteriormente definidos como prototipo do mesmo
  Shape.<b>prototype</b>.move = function (x, y) {
      this.x = x;
      this.y = y;
  };
</pre>


## Class Inheritance
Herança num objecto do tipo `Class` é muito mais intuitivo que o uso de prototipos, usando para isso a palavra reservada `extends` e o metodo `super()` para inicializar o construtor da class pai.

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
Também é possivel criar metodos estáticos numa `Class`. Um metodo estático é um metodo que pode ser chamado sem instanciar o objecto a que ele pertence.

```
  class Rectangle extends Shape {
    …
    static defaultRectangle () {
        return new Rectangle("default", 0, 0, 100, 100)
    }
  }
```
var defRectangle = ~~new~~ Rectangle.defaultRectangle();

