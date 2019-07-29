# Default Parameters

## ES5
<pre>
function defaultParams(argOne, argTwo){
  <b>argOne = argOne || 'default1';</b>
  <b>argTwo = argTwo || 'default2';</b>
  console.log(argOne);
  console.log(argTwo);
}

defaultParams()           // Logs <b>default1</b> and <b>default2</b>
defaultParams('with es5')  // Logs <b>with es5</b> and <b>default2</b>
</pre>

## ES6

<pre>
function defaultParams(<b>argOne = 'default1'</b>, <b>argTwo = 'default2'</b>){
  console.log(argOne);
  console.log(argTwo);
}

defaultParams()           // Logs <b>default1</b> e <b>default2</b>
defaultParams('with es6')  // Logs <b>with es6</b> e <b>default2</b>
</pre>

***

# Rest Parameter

## ES5
<pre>
  function f (x, y) {
      <b>var a = Array.prototype.slice.call(*arguments*, 2);</b>
      return a.length;
  };
  f(1, 2, <b>"hello", true, 7</b>) // Returns 3
</pre>

- `arguments` is a reserved word that contains every parameter passed into the function
- We than slice `arguments` from index 2 so we get all remaining parameters


## ES6
<pre>
  function f (x, y, <b>...a</b>) {
      return a.length;
  };
  f(1, 2, <b>"hello", true, 7</b>) // Returns 3
</pre>

- Using `rest (...)`, as the word indicates, we get all other parameters other than the ones explicitly passed into the function definition.

***

# Spread Parameter

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
