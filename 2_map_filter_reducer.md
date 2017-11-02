# Map / Filter / Reduce / forEach

## Ciclo For - *Obsuleto*
<pre>
for(var i = 0; i < 10; i++){
  ...do something
}
</pre>

- O ciclo for foi muito util durante muito tempo, mas à face de novas funcionalidades, tornou-se meio que obsoleto.
- Apresenta alguns problemas como mutabilidade e side-effects

## Map
<pre>
[1, 2, 3, 4].map(num => num * 2);   //return [2, 4, 6, 8]
</pre>

- Não tem side-effects nem mutabilidade

## Filter
<pre>
[1, 2, 3, 4].filter(num => num % 2);   //return [1, 3]
</pre>

- Não tem side-effects nem mutabilidade

## Reducer
<pre>
[['num1', 1], ['num2', 2]].reduce((acc, [k,v]) => ({...acc, [k]:v}), {});   //return {num1: 1, num2: 2}
</pre>

- Não tem side-effects nem mutabilidade

## forEach
<pre>
[1, 2, 3, 4].forEach(num => console.log(num));   // logs 1; logs 2; logs 3; logs 4
</pre>
