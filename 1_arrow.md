# Arrow Functions

## ES5
<pre>
function es5this(someService) {
  this.foo = 'Hello';
  someService.doSomething(function (response) {
    <b>this.foo</b> = response;
  });
}
</pre>

O scope do **this** é arbitrario, neste caso:

`this.foo === undefined`

### ES5 Hacks
<pre>
function es5HackOne (someService) {
  this.foo = 'Hello';
  someService.doSomething(function (response) {
    this.foo = response;
  }<b>.bind(this)</b>);
}
</pre>

ou

<pre>
function es5HackTwo (someService) {
  <b>var self = this;</b>
  that.foo = 'Hello';
  someService.doSomething(function (response) {
    <b>self</b>.foo = response;
  });
}
</pre>

## ES6

<pre>
function es5HackTwo (someService) {
  this.foo = 'Hello';
  someService.doSomething(<b>(response) =></b>  {
    this.foo = response;
  });
}
</pre>

### Abreviações

<pre>
<b>(parameter)</b> => <b>{
  return parameter;
}</b>
</pre>

- Body Expression
<pre>
(parameter) => <b>parameter + " benfica"<b>;
</pre>

- Statement Expression
<pre>
<b>parameter</b> => parameter + " benfica";
</pre>
