# Let e Const

## Var
<pre>
  elem.innerHTML = x;
  var x = 'badjoras';
  
  // elem will have value of "badjoras"
</pre>

- Mutabilidade
- Hoisting

## Hoisting
<pre>
  elem.innerHTML = x;
  <b>var x = 'badjoras';</b>
</pre>
- Variavel `x` usada antes de ser declarada

## Let
<pre>
  <b>elem.innerHTML = x;</b>
  <b>let x = 'badjoras';</b>
  
  //Return error, x is not defined
</pre>

- Igual a `var` mas sem Hoisting

## Const
<pre>
  elem.innerHTML = x;
  <b>const x = 'badjoras';</b>
  
  //Return error, x is not defined
</pre>

<pre>
  const x = "badjoras"
  <b>x = 'undersnight';</b>
  
  //Return error, x cannot be re-assigned
</pre>

- Não tem Hoisting e prevente Mutabilidade*

***

Imutabilidade do tipo **const** prevente re-assignação, mas não prevente mutabilidade do valor.

<pre>
  const x = {key: 'value'}
  <b>x = {key: 'value2}</b>
</pre>
O exemplo acima irá dar erro porque estamos a tentar reassignar a variavel `x` com um novo objecto

<pre>
  const x = {key: 'value'}
  <b>x.key = 'value2'</b>
  
  // x => value2
</pre>

No entanto podemos alterar as propriedade do objecto assignado a `x`, mesmo que este seja uma **constante**


Para prevenir que isto aconteça, teremos de usar um metodo do Objecto chamado `freeze()`. 
Este metodo prevente que qualquer tipo de objecto possa ser manipulado, usando em combinação com **cont** temos entao um verdadeiro objecto imutavel.

<pre>
  const x = Object.freeze({key: 'value'});
  <b>x.key = 'value2'</b>
  
  // x => value
</pre>
