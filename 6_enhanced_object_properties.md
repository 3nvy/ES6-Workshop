# Enhanced Object Properties

- Com a chegada do ES6, foram também introduzidas algumas simplicidades nas definições de objectos.

## Property Shorthand
- É uma sintaxe simplificada para definir propriedades de um objecto;

### ES5
<pre>
  var x = 1;
  var y = 2;
  
  var obj = { <b>x: x</b>, <b>y: y</b> }
</pre>

### ES6
- Se o nome da propriedade for igual ao nome do atributo, podemos ocultar o último.

<pre>
  var x = 1;
  var y = 2;
  
  var obj = { <b>x, y</b> } // => { x: x, y: y }
</pre>

## Computed Property Names
- Permite usar nomes calculados na definição de objectos

### ES5
- Em ES5, não podemos calcular o nome directamente na definição do objecto, tendo posteriormente de adicionar a propriedade manualmente

<pre>
  var name = 'propriedade';
  var obj = {
    foo: "bar"
  };
  <b>obj[ name + '2' ] = 42;</b>
  
  // => {foo: 'bar', propriedade2: 42}
</pre>

### ES6
- Em ES6, podemos agora calcular o nome da propriedade directamente na definição do objecto

<pre>
  var name = 'propriedade';
  var obj = {
    foo: "bar",
    <b>[name + '2']</b>: 42
  };

  // => {foo: 'bar', propriedade2: 42}
</pre>
