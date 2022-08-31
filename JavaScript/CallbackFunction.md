# Callback Function

A function which will be passed as a parameter to be called later.

i.e.
```js

function example(fn){
	//do some computation
	return fn();
}

function fn(){
	return 3;
}

console.log(example(fn));

```
Outputs:

```
3
```