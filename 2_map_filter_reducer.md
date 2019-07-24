# Map / Filter / Reduce / forEach

## For Loop - *Obsulete*
<pre>
for(var i = 0; i < 10; i++){
  ...do something
}
</pre>

- Mutability
- Side-effects

## Map
<pre>
[1, 2, 3, 4].map(num => num * 2);   //return [2, 4, 6, 8]
</pre>

- Always returns the same amount of data, if the array had 5 entries, it wiill always return 5 entries
- Allows for different data to be returned

## Filter
<pre>
[1, 2, 3, 4].filter(num => num % 2);   //return [1, 3]
</pre>

- Allows to return different amount of data
- Data returned can't be mutaded

## Reducer
<pre>
[['num1', 1], ['num2', 2]].reduce((acc, [k,v]) => ({...acc, [k]:v}), {});   //return {num1: 1, num2: 2}
</pre>

- Allows to return different amount of data
- Allows for different data to be returned

## forEach
<pre>
[1, 2, 3, 4].forEach(num => console.log(num));   // logs 1; logs 2; logs 3; logs 4
</pre>

 - Iterates over each entrie