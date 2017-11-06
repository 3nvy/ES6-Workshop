> # Async / Await

Com o uso de Promises, fazer código asincrono tornou-se muito simples, no entanto em termos de estrutura pode não ser o melhor, uma vez que temos sempre de usar callbacks.

Com a chegada do ES7 (ou stage-2), temos agora duas novas palavras reservadas, **async** e **await**. Estas duas palavras reservadas trabalham em conjunto e permitem escrever código asincrono de forma sincrona!

### Sem Async / Await

<pre>
  (() => {
    new Promise( { /* do something */ } )
    <b>.then</b>(data => {
      console.log(data)
        new Promise( { /* do something */ } )
        <b>.then</b>(data => {
          console.log(data)
        })
    })
  })()
</pre>


### Com Async / Await

<pre>
  (<b>async</b> () => {
    const data1 = <b>await</b> new Promise( { /* do something */ } )
    console.log(data1)
    
    const data2 = <b>await</b> new Promise( { /* do something */ } )
    console.log(data2)
  })()
</pre>
