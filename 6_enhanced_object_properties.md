> # Enhanced Object Properties

- With ES6, there's been multiple improvements on object definitions.

## Property Shorthand
- Simplified syntax to define object properties

### ES5
<pre>
  var x = 1;
  var y = 2;
  
  var obj = { <b>x: x</b>, <b>y: y</b> }
</pre>

### ES6

<pre>
  var x = 1;
  var y = 2;
  
  var obj = { <b>x, y</b> } // => { x: x, y: y }
</pre>

- If the property has the same name as the attribute, the latest can be omited.

## Computed Property Names
- Allows computed property names on object definition

### ES5
- On ES5, we can't use computed property names on the object definition, so we have to mutate the object afterwards

<pre>
  var name = 'property';
  var obj = {
    foo: "bar"
  };
  <b>obj[ name + '2' ] = 42;</b>
  
  // => {foo: 'bar', property2: 42}
</pre>

### ES6
- But with ES6, we can now do it on object definition, the same way we would do after the definition on ES5

<pre>
  var name = 'property';
  var obj = {
    foo: "bar",
    <b>[`${name}2`]</b>: 42
  };

  // => {foo: 'bar', property2: 42}
</pre>
