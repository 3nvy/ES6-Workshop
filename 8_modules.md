> # Modularização

## Export / Import
A modularização foi sem dúvida uma das features mais bem recebidas do ES6, uma vez que nos permite facilmente dividir toda
a nossa aplicação em módulos.

No tempo do ES5, a maneira mais habitual de inicializar uma aplicação seria correr todos os "bocados" que a compoêm por ordem,
e atribui-los a variáveis globais para que pode-sem ser acedidos em qualquer parte da aplicação. No entanto, com a chegada dos
módulos no ES6, podemos divir a nossa aplicação em pedaços mais pequenos e chama-los / instancia-los apenas quando necessário.


## Named Exports
Se tivermos uma biblioteca com vários metodos / variaveis que queiramos que sejam acessiveis podemos usar **named exports**,
atribuindo sempre um nome ao metodo ou à variavel;

<pre>
  //  lib/math.js
  <b>export</b> function sum (x, y) { return x + y }
  <b>export</b> const pi = 3.141593
  
  //  someApp.js
  <b>import * as</b> math from "lib/math"
  console.log("2π = " + <b>math.sum(math.pi, math.pi)</b>)

  //  otherApp.js
  <b>import { sum, pi }</b> from "lib/math"
  console.log("2π = " + <b>sum(pi, pi)</b>)
</pre>

## Default Exports
No caso de termos uma biblioteca que terá apenas um metodo / variavel acessivel ao exterior, não necessitamos de atribuir um
**named export**, podemos simplesmente usar a palavra reservada `default`.

- Notar que no caso de um **default export**, não necessitamos de atribuir um alias ao import, uma vez que só existe um endpoint,
podems atribuir qualquer nome.

<pre>
  //  lib/double.js
  export <b>default</b> x => x * 2;
  
  //  someApp.js
  import <b>Double</b> from "lib/double"
</pre>
