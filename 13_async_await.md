> # Async / Await

Com o uso de Promises, fazer código asincrono tornou-se muito simples, no entanto em termos de estrutura pode não ser o melhor, uma vez que temos sempre de usar callbacks.

Com a chegada do ES7 (ou stage-2), temos agora duas novas palavras reservadas, **async** e **await**. Estas duas palavras reservadas trabalham em conjunto e permitem escrever código asincrono de forma sincrona!

### Sem Async / Await

<pre>
  (() => {
    new Promise( { /* do something */ } )
    <b>.then</b>(data => {
      console.log(data)
        new Promise( { /* do something with data1*/ } )
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
    
    const data2 = <b>await</b> new Promise( { /* do something with data1 */ } )
    console.log(data2)
  })()
</pre>

## Debugging
Fazer debug usando Promises e Callbacks sempre trouxe os seus problemas:

1. Não é possivel colocar breakpoints em arrow functions que retornem uma expressão;

2. Não é possivel usar atalhos como `step-over` para passar para o proximo `then`, pois estes atalhos só funcionam em código sincrono.

Usando Aync / Await, reduzimos a necessidade de uso de arrow functions, e podemos usar os atalhos para debug.

## Error Handling
Os erros são tratados usando `try-catch`. Apesar de funcionar, eu acho que o uso de try-catch não fica muito bonito e em alguns casos pode até criar uma cascata de try-catches que fazem com que o código nem seja mais legivel.

<pre>
async function asyncTask(cb) {  
    <b>try</b>  {
       const user = await UserModel.findById(1);
       if(!user) return cb('No user found');
    } <b>catch(e)</b>  {
        return cb('Unexpected error occurred');
    }

    <b>try </b> {
       const savedTask = await TaskModel({userId: user.id, name: 'Demo Task'});
    } <b>catch(e)</b>  {
        return cb('Error occurred while saving task');
    }

    if(user.notificationsEnabled) {
        <b>try</b>  {
            await NotificationService.sendNotification();  
        } <b>catch(e)</b>  {
            return cb('Error while sending notification');
        }
    }

    if(savedTask.assignedUser.id !== user.id) {
        <b>try</b>  {
            await NotificationService.sendNotification();
        } <b>catch(e)</b> {
            return cb('Error while sending notification');
        }
    }

    cb(null, savedTask);
}
</pre>
> Retirado de [blog.grossman.io](http://blog.grossman.io/how-to-write-async-await-without-try-catch-blocks-in-javascript/)


Existem no entanto diversas bibliotecas que tratam os erros em funçoes async de uma maneira mais legivel. A minha favorita chama-se [await-to-js](https://github.com/scopsy/await-to-js) e baseia-se na syntax de GO, fazendo com que a função retorne 2 parametros, o erro e a resposta, tornando o código mais limpo e simples de entender.

<pre>
async function asyncTask(cb) {
     let err, user, savedUser, notification;

     <b>[ err, user ]</b> = await to(UserModel.findById(1));
     if(err) return console.log(err);
     if(!user) return cb('No user found');

    ...
}
</pre>
