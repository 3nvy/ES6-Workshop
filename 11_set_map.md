> # Set / Map

ES6 also brough new data structures:

## Set
`Set` is a collection of unique values capable of storing any type of data.

<pre>
  let s = new Set()
  s.add("hello").add("goodbye").add("hello").add({ key: 'value' })
  
  console.log(set) // Set {'hello', 'goodbye', Object {key: 'value'}}
</pre>

## Map
`Map` is a structure that stores data in **key/value** pars.

In reality, the above definition is a normal definition for an object literal `{}`, so some people were confused as to what `Map` differs from it.

One of the big limitation of an Object Literal it that its not iterable, so if we want to go over every entry of the object, we would have to use `Object.entries({...})`.

Another limitation is that the object parameters can only be of type string.

`Map` solves both problems, it makes it so your object is iterable using First-Class functions like `map`, `filter`, `forEach`, ... and you can set the parameter to any type, even an object or an array.

<pre>
  var map = new Map(),
  val2 = 'val2',
  val3 = { key: 'value'};
  map.set(0, 'val1');
  map.set('1', val2);
  map.set(**{ key: 2 }**, val3);
  
  console.log(map); // Map {0 => 'val1', '1' => 'val2', Object {key: 2} => Object {key: 'value'}}
</pre>

