# Let and Const

## Var
<pre>
  elem.innerHTML = x;
  var x = 'badjoras';
  
  // elem will have value of "badjoras"
</pre>

- Mutability
- Hoisting

## Hoisting
<pre>
  elem.innerHTML = x;
  <b>var x = 'badjoras';</b>
</pre>
- Variable `x` is used before being declared

## Let
<pre>
  <b>elem.innerHTML = x;</b>
  <b>let x = 'badjoras';</b>
  
  //Return error, x is not defined
</pre>

- Equals to `var` but doesn't allow Hoisting or re-declaration

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

- No Hoisting or Mutability*

***

**const** only prevents the re-assignment of the variable, not the mutability of the value itself.

<pre>
  const x = {key: 'value'}
  <b>x = {key: 'value2}</b>
</pre>
On the above example, we are trying to re-assign a new object to `x`, which is going to thrown an error

<pre>
  const x = {key: 'value'}
  <b>x.key = 'value2'</b>
  
  // x => value2
</pre>
Altho in here, we are trying to change a property of the object already assigned to x, which is going to work

To prevent this, we can use the Object method called `freeze()`
Once called onto a variable, the value itself can't be modified either (doesnt work with types like Set or Map)

<pre>
  const x = Object.freeze({key: 'value'});
  <b>x.key = 'value2'</b>
  
  // x => value
</pre>
