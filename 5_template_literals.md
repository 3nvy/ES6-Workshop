# Template Literals

Template Literals exist to solve a big problem over concatenation of string. On ES5 strings could become very complex and unredabe given their complexity.


## String Interpolation

### ES5
<pre>
  var name = 'Renato';
  var age = 27;
  var job = 'developer';
  var msg = 'Hello, my name is ' <b>+ name +</b> ', I'm ' <b>+ age +</b> ' years old and I work as a ' <b>+ job +</b> '.';

  // => Hello, my name is Renato, I'm 27 years old and I work as a developer.
</pre>

### ES6
<pre>
  var nome = 'Renato';
  var idade = 25;
  var job = 'developer';
  var msg = <b>`</b>Hello, my name is <b>${name}</b>, I;m <b>${age}</b> years old ad I work as a <b>${job}</b><b>`</b>

  // => Hello, my name is Renato, I'm 27 years old and I work as a developer.
</pre>

- Template literals are required to use ` `` `
- JS variables are printed within the template by using `${ }`

## Custom Interpolation

- We can also use Template Literals as interpolated arguments for functions

### ES5
<pre>
  var domain = 'google';
  fetch<b>('www.' + domain + '.pt')</b>
  .then( ()=> console.log('Finished!') )
</pre>

### ES6
<pre>
  var domain = 'google';
  fetch <b>`www.${domain}.pt`</b>
  .then( ()=> console.log('Finished!') )
</pre>
