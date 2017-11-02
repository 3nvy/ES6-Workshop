> # Object Literals

Object Literals são basicamente Singletons, sendo assim optimos se quisermos garantir que apenas uma instancia do objecto existe em memória.

<pre>
  const objectLiteral = {
    valueA: 'A',
    valueB : 'B',
    functionA: () => console.log('Returns Function A'),
    functionB: () => console.log('Returns Function A');
  }
</pre>
