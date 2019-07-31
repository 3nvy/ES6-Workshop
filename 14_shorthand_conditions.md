# Shorthand Conditions 

## And Gate

Only when all contitions are True, the statement is True

![And Gate](https://i.imgur.com/5NtwcuX.png)

- If condition
<pre>
if(user.data && user.data.address && user.data.address.street) {
    return user.data.address.street;
}
</pre>

 - AND ShortHand statement
<pre>
var street = user.data && user.data.address && <b>user.data.address.street</b>
</pre>

```
street === user.data.address.street
```

> 0, null, undefined, '', false => false

> 'string', 1, {}, [], (anything else really) => true


## OR Gate

The statement is True as soon as one of the conditions are true

![Or Gate](https://i.imgur.com/voGLXhJ.png)

- If condition
<pre>
if(user.data) {
    return user.data.address.street;
}
else {
    return 'default value';
}
</pre>

 - OR Short-Hand statement
<pre>
var street = user.data || <b>'default value'</b>;
</pre>

```
street === user.data  #if user.data is true
```

```
street === 'default value'  #if user.data is false
```


## Combined Short-Hand statements

<pre>
var street = user.data && user.data.address && <b>user.data.address.street</b> || <b>'default value'</b>;
</pre>
