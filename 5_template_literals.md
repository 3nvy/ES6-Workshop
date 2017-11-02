# Template Literals

Template Literals vieram resolver um dos grandes problemas na construção de strings, no ES5
muitas das strings eram bastante confusas devido à complexidade necessária para as criar

## String Interpolation

### ES5
<pre>
  var nome = 'Renato';
  var idade = 25;
  var job = 'developer';
  var msg = 'Olá, o meu nome é ' <b>+ nome +</b> ', tenho ' <b>+ idade +</b> ' anos e trabalho como ' <b>+ developer +</b> '.';

  // => Olá o meu nome é Renato, tenho 25 anos e trabalho como developer.
</pre>

### ES6
<pre>
  var nome = 'Renato';
  var idade = 25;
  var job = 'developer';
  var msg = <b>`</b>Olá, o meu nome é <b>${nome}</b>, tenho <b>${idade}</b> anos e trabalho como <b>${developer}</b><b>`</b>

  // => Olá o meu nome é Renato, tenho 25 anos e trabalho como developer.
</pre>

## Custom Interpolation

- Também podemos usar Template Literals como argumento interpolado para algumns metodos arbitrarios.

### ES5
<pre>
  var domain = 'google';
  fetch<b>('www.' + domain + '.pt')</b>
  .then( ()=> console.log('Acabou!') )
</pre>

### ES6
<pre>
  var domain = 'google';
  fetch <b>`www.${domain}.pt`</b>
  .then( ()=> console.log('Acabou!') )
</pre>
