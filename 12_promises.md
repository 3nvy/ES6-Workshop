> # Promises

A **Promise** is an Object that allows asynchronous code execution.

JavaScript is a single-thread programming language which makes it impossible to execute multiple code chunks at the same time, which leads to slowness and blocked UI when we have to wait for certain  bloks to finish. What JavaScript does is a kind of concurrency to emulate parallel execution, by switching between the main code execution and **callbacks**.
 
Events like button clicks or mouse move events are executed asynchronously using **callbacks**, but those are hardly the best solution for async code execution.
 
For a long time, multiple libraries have implemented the concept of **Promises**, the most known one being JQuery by the use of `Deferreds`, but with ES6 we finally have native `Promises` implementation.
 

## Promise LifeCycle
 
 ![Promise LifeCycle](https://cdn.rawgit.com/Vectaio/a76330b025baf9bcdf07cb46e5a9ef9e/raw/26c4213a93dee1c39611dcd0ec12625811b20a26/js-promise.svg)
 
 ## Exemples
 
<pre>
  const myFirstPromise = new Promise(<b>(resolve, reject)</b> => {
   
    ... Read Image (Asynchronous process)
    
    return (/* Is the promise is fulfilled */) ? resolve(data) : reject(err);
   
  });
</pre>

<pre>
  const mySecondPromise = new Promise(<b>(resolve, reject)</b> => {
   
    fetch(/* JSON File */)
    <b>.then(resolve)
    .catch(reject)</b>
    
  });
</pre>

We may also need to wait for the result of 2 or more distinct promises to continue our code execution. One wait to do that is to chain Promises, so after one promise is fulfilled, we trigger another Promise and when that one is fulfilled as well we continue code execution.

While this is possible is not recommended because it can lead to something called [Callback Hell](http://callbackhell.com/)

So to avoid this, ES6 `Promise` comes with the method `all()` that takes multiple Promises as parameters, and resolves when all of them are either fulfilled.

<pre>
  Promise.all(<b>[myFirstPromise, mySecondPromise]</b>).then(data => { 
    ... Do Something
  });
</pre>
