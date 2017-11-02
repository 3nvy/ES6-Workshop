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


## ES6
<pre>
  function f (x, y, <b>...a</b>) {
      return a.length;
  };
  f(1, 2, <b>"hello", true, 7</b>) // Returns 3
</pre>
