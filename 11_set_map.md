> # Set / Map

O ES6 tambem trouxe com ele duas novas estruturas de dados:

## Set
É uma colecção de valores unicos capaz de armazenar qualquer tipo de dados.

<pre>
  let s = new Set()
  s.add("hello").add("goodbye").add("hello").add({ key: 'value' })
  
  console.log(set) // Set {'hello', 'goodbye', Object {key: 'value'}}
</pre>

## Map
É uma estrutura que guarda informação em pares **key/value**.

<pre>
  var map = new Map(),
  val2 = 'val2',
  val3 = { key: 'value'};
  map.set(0, 'val1');
  map.set('1', val2);
  map.set({ key: 2 }, val3);
  
  console.log(map); // Map {0 => 'val1', '1' => 'val2', Object {key: 2} => Object {key: 'value'}}
</pre>

Na verdade, a definição acima é a definição de um objecto `{}` em JS, e algumas pessoas têm dificuldade em perceber porque devem usar um `Map` am invez de `{}`.

É verdade que na maioria das vezes, usar um simples objecto `{}` pode ser mais simples que um `Map`, no entanto existem demasiadas limitações se quiser-mos realmente usar algo complexo.

Uma das maiores limitações é que um `{}` não é iteravel, obrigando-nos a usar algo como `Object.entries({...})` para transformar o objecto num array e podermos assim iterar sobre ele.

Outra grande limitação é que os atributos de um `{}` só podem ser do tipo string.

Num `Map` não existe nenhuma destas limitações, ele tem um iterador próprio, e aceita qualquer tipo de dado, tanto para o atributo como para o valor.
