> # Destructuring Assignment

Destructuring é uma sintaxe que permite separar valores de arrays, ou propriedades de objectos, em variaveis distintas.

## Array Matching

- Permite separar valores especificos de um array e atribuilos directamente para variaveis separadas.

### ES5
<pre>
  var list = [10, 20, 30];
  <b>var a = list[0];
  var b = list[2];</b>
  console.log(a); // 10
  console.log(b); // 30
</pre>

### ES6

<pre>
  var list = [10, 20, 30];
  <b>[a, , b] = list;</b>
  console.log(a); // 10
  console.log(b); // 30
</pre>

- Podemos também usar o spread operator
<pre>
  var list = [10, 20, 30, 40];
  [a, b, <b>...rest</b>] = list;
  console.log(a);     // 10
  console.log(b);     // 20
  <b>console.log(rest);  // [30, 40]</b>
</pre>

## Object Matching

- Permite separar propriedades especificas de um objecto e atribuilas directamente para variaveis separadas.
No caso dos objectos, o nome da variavel a extrair tem de sre o nome do atributo do objecto.

### ES5
<pre>
  var obj = { a: 10, b: 20, c: 30, d: 40 };
  <b>var a = obj.a;
  var c = obj.c;</b>
  console.log(a); // 10
  console.log(c); // 30
</pre>


### ES6
<pre>
  var obj = { a: 10, b: 20, c: 30, d: 40 };
  var { <b>a, c</b> } = obj;
  console.log(a); // 10
  console.log(c); // 30
</pre>

<pre>
  var obj = { a: 10, b: 20, c: 30, d: 40 };
  var { a, b , <b>...rest</b>} = obj;
  console.log(a);     // 10
  console.log(b);     // 20
  <b>console.log(rest);  // { c: 30, d: 40 }</b>
</pre>

## Alias

Como vimos, ao fazer a destructurização de propriedades de um objecto, o nome da variável tem de ser 
equivalente ao nome do atributo, o que nem sempre é a melhor opção, uma vez que pudemos ser obrigados a definir variaveis
já existentes, ou simplesmente porque o nome da variavel não é explicita.

Para resolver este problema, é possivel dar alias às variavies a quando da destructurização:
<pre>
  var obj = { a: 10, b: 20, c: 30, d: 40 };
  var { a<b>: ten</b>, c<b>: thirty</b>} = obj;
  console.log(ten);     // 10
  console.log(thirty);  // 30
</pre>


## Valores Default
Também é possivel usar valores por defeito na destructurização:
<pre>
  //Array
  var list = [ 1 ]
  var [ x, <b>y = 2</b> ] = list
  console.log(x);  // 1
  console.log(y)   // 2
  
  //Object
  var obj = { x: 1 }
  var { x, <b>y = 2</b> } = obj
  console.log(x);  // 1
  console.log(y)   // 2
</pre>
  
 ## Fail-Soft Destructuring
 Na eventualidade de tentarmos destructurizar um valor que não existe e não tem um default, será atribuido o valor de undefined;
 
 <pre>
  var list = [ 7, 42 ]
  var [ a = 1, b = 2, c = 3, d ] = list 
  console.log(a);  // 7
  console.log(b)   // 42
  console.log(c);  // 3
  console.log(d)   // undefined
</pre>

## Parameter Context Matching
Também podemos usar destructurização nos parametros de uma função

### ES5
<pre>
   // Array
   function f (arg) {
      var name = arg[0];
      var val  = arg[1];
      console.log(name, val);
    };
  
  // Object
  function g (arg) {
      var n = arg.name;
      var v = arg.val;
      console.log(n, v);
  };
</pre>

### ES6

<pre>
   // Array
   function f ([name, val]) {
      console.log(name, val);
    };
  
  // Object
  function g ({name, val}) {
      console.log(name, val);
  };
  
  function g ({name: n, val: v}) {
      console.log(n, v);
  };
</pre>
