> # Object Literals

Object literals are the standartd "object" you would define on JavaScript. All Object Literals are `Singletons` whitch means that only one instance of the object can exist in memory.

<pre>
  const objectLiteral = {
    valueA: 'A',
    valueB : 'B',
    functionA: () => console.log('Returns Function ${this.valueA}'),
    functionB: () => console.log('Returns Function ${this.valueB}');
    factoryExample: () => ({key: 'value'})
  }
</pre>

Object Literals are often used as data repositories, given they can only be instantiated once, it assures that the same data can be accessed on any part of the app.