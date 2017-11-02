> # Object Literals

Object Literals são basicamente Singletons, sendo assim optimos se quisermos garantir que apenas uma instancia do objecto existe em memória. A sua estrutura também é muito simples sendo bastante mais fácil do que criar um Singleton usando um construtor.

<pre>
  const objectLiteral = {
    valueA: 'A',
    valueB : 'B',
    functionA: () => console.log('Returns Function ${this.valueA}'),
    functionB: () => console.log('Returns Function ${this.valueB}');
    factoryExample: () => ({key: 'value'})
  }
</pre>

Normalmente são usados como repositorio de dados, uma vez que só podem ser instanciados uma unica vez, garantimos assim que o acesso a esses dados seja unico em qualquer parte da aplicação
