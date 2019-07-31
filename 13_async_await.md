> # Async / Await

With Promises, using asynchronous code became very easy, but the code can become unreadable very easily due to the use of **callbacks**

With **stage-2**, we now have 2 new reserved words `async` and `await` which allows us to write asynchronous in a synchronous structure.

### W/t Async / Await

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


### With Async / Await

<pre>
  (<b>async</b> () => {
    const data1 = <b>await</b> new Promise( { /* do something */ } )
    console.log(data1)
    
    const data2 = <b>await</b> new Promise( { /* do something with data1 */ } )
    console.log(data2)
  })()
</pre>

## Debugging
Debugging Promises and Callbacks was always a pain. For instances:

1. Its not possible to place breakpoints on arrow functions that return expressions; (Its now possible with the use of a [library](https://github.com/georgebonnr/bug))

2. Its not possible to use shortcuts like `step-over` to go over to the next `then()` because those shortcuts only work o synchronous code

Use Async / Await we dont need arrow functions and we can use the shortcuts, making debug easier an linear.

## Error Handling
The errors are handled by the use of `try-catch` statements. Although the code can become very messy with a cascade of try-catche's for each condition, as per the example bellow:

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
> From [blog.grossman.io](http://blog.grossman.io/how-to-write-async-await-without-try-catch-blocks-in-javascript/)


There are some libraries that allows us to handle the errors in a different fashion. My favourite and recommended is [await-to-js](https://github.com/scopsy/await-to-js) and its based on GO syntax, making each Promise return 2 statements, the response and the error, making the code cleaner.

<pre>
async function asyncTask(cb) {
     let err, user, savedUser, notification;

     <b>[ err, user ]</b> = await to(UserModel.findById(1));
     if(err) return console.log(err);
     if(!user) return cb('No user found');

    ...
}
</pre>
