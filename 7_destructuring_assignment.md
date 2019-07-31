> # Destructuring Assignment

Destructuring is a syntax that allows to separate values from arrays or properties from object literals, into distinct variables

## Array Matching

- Allows to separate specific  values from an array into separate variables.

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

- We can also use a rest operator
<pre>
  var list = [10, 20, 30, 40];
  [a, b, <b>...rest</b>] = list;
  console.log(a);     // 10
  console.log(b);     // 20
  <b>console.log(rest);  // [30, 40]</b>
</pre>

## Object Matching

- Allows to separate object literals properties into separate variables. 

- Contrary to arrays, the destructured properties need to match the property names within the object.

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

As explained before, the destructured properties from an object literal need to match the property names within the object, but this isnt always ideal, especially if we dont control the data structure, for example, if it comes from an external API call, or if the destructured property name already exists.

To solve this problem, ES6 allows you to give an alias to every destructured property, effectively  exporting it into a different variable name:
<pre>
  var obj = { a: 10, b: 20, c: 30, d: 40 };
  var { a<b>: ten</b>, c<b>: thirty</b>} = obj;
  console.log(ten);     // 10
  console.log(thirty);  // 30
</pre>


## Default Values
It's also possible to define default values to destructured properties:
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
  
 ## Soft-Fail Destructuring
 If we try destructuring a value that doesnt exist, is out-of-bounds and doesnt have a default value, it will sof-fail by giving the property an undefined value.
 
 <pre>
  var list = [ 7, 42 ]
  var [ a = 1, b = 2, c = 3, d ] = list 
  console.log(a);  // 7
  console.log(b)   // 42
  console.log(c);  // 3
  console.log(d)   // undefined
</pre>

## Parameter Context Matching
We cal also use destructuring on parameters from a function

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
