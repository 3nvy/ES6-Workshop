> # Extras

## TC39 proposals Github

https://github.com/tc39/proposals


## Optional Chaining

`Url`  https://github.com/tc39/proposal-optional-chaining

`Stage`  3

Often when looking at deep nested properties within an object, we have to check whether intermediate nodes exist:

<pre>
var street = user.data && user.data.address && user.data.address.street;
</pre>

**street** will either be `false` if one of the statements resolve to false, or whatever value `user.data.address.street` holds

As we can see, theres a lot of duplicated statements in the validation above so to make it more easier to access and read, this proposal was defined

<pre>
var street = user<b>?.</b>data<b>?.</b>address<b>?.</b>street;
</pre>

This will return the exact same result as the above, but its way easier to understand and prevents duplication.

## Promise.any()

`Url`  https://github.com/tc39/proposal-promise-any

`Stage`  2

`Promised.all` resolves when all promises are fulfilled, but fails if one of them gets rejected. Sometimes we want to execute multiple Promises and resolve if any of those promises is fullfilled, even if all the other are rejected. For that purpose, this proposel was defined

<pre>
Promise.any(promises).then(
  (first) => {
    // Any of the promises was fulfilled.
  },
  (error) => {
    // All of the promises were rejected.
  }
);
</pre>

## Numeric Separator

`Url`  https://github.com/tc39/proposal-numeric-separator

`Stage`  3

> This feature enables developers to make their numeric literals more readable by creating a visual separation between groups of digits. Large numeric literals are difficult for the human eye to parse quickly, especially when there are long digit repetitions. This impairs both the ability to get the correct value / order of magnitude...

<pre>
1_000_000_000           // Ah, so a billion
101_475_938.38          // And this is hundreds of millions

let fee = 123_00;       // $123 (12300 cents, apparently)
let fee = 12_300;       // $12,300 (woah, that fee!)
let amount = 12345_00;  // 12,345 (1234500 cents, apparently)
let amount = 123_4500;  // 123.45 (4-fixed financial)
let amount = 1_234_500; // 1,234,500
</pre>