> # Promises

 Uma **Promise** é um objecto que permite a execução de código asincrono.
 
 JavaScript é uma linguagem single-thread o que faz com que não seja possivel executar multiplos blocos de código ao mesmo tempo, fazendo com que o codigo corra procedimentalmente muitas vezes tornando a aplicação lenta e bloquiando o UI ao utilizador.
 
 Código asincrono não é algo novo no JS, eventos como o click de um botão, ou o movimento do rato são eventos executados asincronamente usando **callbacks** (uma função que é executada como retorno do resultado de outra função asincrona). No entanto os eventos são raramente a melhor opção para escrever código asincrono pois têm muitos senãos.
 
 Há já algum tempo que existem diversas bibliotecas que implementam o conceito de **Promise**, incluido a biblioteca mais conhecida para js, **jQuery** usando `Deferreds`, no entanto o ES6 trouxe-nos **Promises** nativas.
 

## Promise LifeCycle
 
 ![Promise LifeCycle](https://cdn.rawgit.com/Vectaio/a76330b025baf9bcdf07cb46e5a9ef9e/raw/26c4213a93dee1c39611dcd0ec12625811b20a26/js-promise.svg)
 
 ## Exemplos
 
<pre>
  const myFirstPromise = new Promise(<b>(resolve, reject)</b> => {
   
    ... Ler imagem (Processo asincrono)
    
    return (/* Se tudo correr bem */) ? resolve(data) : reject(err);
   
  });
</pre>

<pre>
  const mySecondPromise = new Promise(<b>(resolve, reject)</b> => {
   
    fetch(/* link para ficheiro JSON */)
    <b>.then(resolve)
    .catch(reject)</b>
    
  });
</pre>

E se quisermos fazer algo somente quando estas duas Promises tiverem concluidas? Poderiamos usar uma Promise como como callback de outra, efectivamente encadeando ambas as Promises e conseguido o efeito pretendido, no entanto e ainda que neste exemplo não seja muito visivel, encadear callbacks desta maneira pode levar-nos a um fenomeno chamado [Callback Hell](http://callbackhell.com/)

<pre>
  Promise.all(<b>[myFirstPromise, mySecondPromise]</b>).then(data => { 
    ... Fazer Algo
  });
</pre>
