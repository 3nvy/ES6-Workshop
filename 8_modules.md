> # Modularization

## Export / Import
Modularization was without a doubt one of the most well received features of ES6, as of that point we were able to easily separate the app into different modules.

Up until this point, with ES5, the most usual way to initialize an app was to run every "module" that composes it in order, and assign them to global variables so they could be accessed anywhere on the app. Not only this would occupy unnecessary memory, it was also not very safe as your entire app structure would be exposed for everyone to see. Normaly the code would be uglified prior to be exposed, but this required extra effort and wasnt very performatic.

With ES6 tho, we can now use true modulation, by separating the logic into different modules (files) and we could instantiate them only when necessary, no longer needing to exposed them on global variables and we could bundle everything into a single file and uglify that file, making it hard for prying eyes to take a look into how the application works.

Depending on how we are separating concerns within each module, we may want to export the module as an all, or we may want to export different pieces of the module into separate variables:

## Default Exports
A very usual use-case for a **default export** is a Class module. In this case, the entire module is composed of a single class, so since its a single export, we use the keyword `default` next to `export` so the engine knows the modules is composed of a single export

<pre>
  //  module/TestClass.js
  export <b>default</b> Class TestClass {
    constructor() {
        console.log('This is a Class!')
    }
  };
  
  //  someApp.js
  import <b>TestClass</b> from "module/TestClass"
</pre>

## Named Exports
Although sometimes we may want to export pieces of the modules separately. This is very common on libraries, since it allows us to export only the parts of the library that we need, rather than importing everything and endup not using 90% of it, wasting space and memory.

This are called **named exports**

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
