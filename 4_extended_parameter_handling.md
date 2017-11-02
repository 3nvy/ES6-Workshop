# Parametros Default

## ES5
<pre>
function defaultParams(argOne, argTwo){
  <b>argOne = argOne || 'default1';</b>
  <b>argTwo = argTwo || 'default2';</b>
  console.log(argOne);
  console.log(argTwo);
}

defaultParams()           // Logs <b>default1</b> e <b>default2</b>
defaultParams('com es5')  // Logs <b>com es5</b> e <b>default2</b>
</pre>

## ES6

<pre>
function defaultParams(<b>argOne = 'default1'</b>, <b>argTwo = 'default2'</b>){
  console.log(argOne);
  console.log(argTwo);
}

defaultParams()           // Logs <b>default1</b> e <b>default2</b>
defaultParams('com es6')  // Logs <b>com es6</b> e <b>default2</b>
</pre>

***

# Parametro Rest

## ES5
<pre>
  function f (x, y) {
      <b>var a = Array.prototype.slice.call(arguments, 2);</b>
      return a.length;
  };
  f(1, 2, <b>"hello", true, 7</b>) // Returns 3
</pre>

- É necessário usar um `slice` na variavel `arguments`. Implica hardcoded slice start.


## ES6
<pre>
  function f (x, y, <b>...a</b>) {
      return a.length;
  };
  f(1, 2, <b>"hello", true, 7</b>) // Returns 3
</pre>

- Usando o parametro `rest (...)` podemos directamente manipular a variavel contendo todos os outros argumentos não listados especificamente

***

# Operador Spread

## ES5
<pre>
  var params = [ 3, 4, 5 ];
  var other = [ 1, 2 ].concat(params); // [ 1, 2, 3, 4, 5 ]
</pre>

<pre>
  var str = "foo";
  var chars = str.split(""); // [ "f", "o", "o" ]
</pre>

## ES6
<pre>
  var params = [ 3, 4, 5 ];
  var other = [ 1, 2, ...params ]; // [ 1, 2, 3, 4, 5 ]
</pre>

<pre>
  var str = "foo";
  var chars = [...str]; // [ "f", "o", "o" ]
</pre>
