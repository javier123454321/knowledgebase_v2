# Objects in Js

```js
function foo() {
  console.log( this.a );
}

var obj2 = {
  a: 42,
  foo: foo
};

var obj1 = {
  a: 2,
  obj2: obj2
};

obj1.obj2.foo(); // 42
```

`this` refers to the place where the function is called. (Not the scope of the function)
in `obj1` `this` is the global object. in `obj2` `this` is `obj1`, and in `foo` `this` is obj2

take this example

```js
function foo() {
  console.log( this.a );
}

var obj = {
  a: 2,
  foo: foo
};

var bar = obj.foo; // function reference/alias! -> equivalent to saying bar = foo

var a = "oops, global"; // `a` also property on global object

bar(); // "oops, global"
```

So take the following example of a callback

```js
function logA(){
  console.log(this.a)
}

function callbackExecutor(callback){
  callback()
}

var obj = {
  a: 2,
  objectFunction: logA
};

var a = "global a";

callbackExecutor( obj.objectFunction )
```

To get arround this you bind the function explicitly to the execution context in the call-site. The best way to do that is by using the `call` function.

```js
function foo() {
  console.log( this.a );
}

var obj1 = {
  a: 2,
  foo: foo
};

var obj2 = {
  a: 3,
  foo: foo
};

obj1.foo(); // 2
obj2.foo(); // 3

obj1.foo.call( obj2 ); // 3
obj2.foo.call( obj1 ); // 2
```

## the `new` keyword

Javascript does not have constructors like other OO languages. It is more akin to something like a set of functions that get called when the new keyword is present. Javascript understands the `new` keyword and spits does the following:

1. a brand new object is created (aka, constructed) out of thin air
1. the newly constructed object is [[Prototype]]-linked
1. the newly constructed object is set as the this binding for that function call
1. unless the function returns its own alternate object, the new-invoked function call will automatically return the newly constructed object.

```js
function foo(a) {
  this.a = a;
}

function foo(a) {
  this.a = a;
}

var bar = foo( 2 );
console.log( bar.a ); // undefined

//however
var bar = new foo( 2 );
console.log( bar.a ); // 2
```


so there is an order of precedence in which an execution context is given

```js
function foo(something) {
  this.a = something;
}

var obj1 = {
  foo: foo
};

var obj2 = {};

obj1.foo( 2 );
console.log( obj1.a ); // 2
```

if we then call a function 
```js
obj1.foo.call( obj2, 3 );
console.log( obj2.a ); // 3
```

even if we called foo inside of obj1, we *explicitly* bound foo to obj2 using the call method. `this` inside the foo function is referring to obj2 even if called in obj1.

but if we add a case of the `new` keyword, then that takes even more precedence than the explicit binding. It cannot be called with the `apply` funciton.
```js
var bar = new obj1.foo( 4 );
console.log( obj1.a ); // 2
console.log( bar.a ); // 4
```
 
## Binding with the `new` keyword

the `bind` function makes the function ignore its own `this` alltogether, and replace it with its argument. So if we try to bind to a function with a new keyword, it starts getting crazy.

```js
function foo(something) {
  this.a = something;
}

var obj1 = {};

var bar = foo.bind( obj1 );
bar( 3 );
console.log( obj1.a ); // 3
bar( 2 );
console.log( obj1.a ); // 2

var baz = new bar( 3 );
console.log( obj1.a ); // 2
console.log( baz.a ); // 3
```

Even if it is bound to obj1, the `foo` function is creating a `new` `this` in which its context will be executed. It won't change obj1.a. `new` takes the most preference out of all these, which goes down the preference list as follows, from highest to lowest:

1. new keyword : `this` refers to the object being created
1. explicit binding with `call`, `apply`, or `bind`: `this` is the argument passed down.
1. implicit binding : `this` is the scope of the object in the call-site
1. default binding: this is the window object

## Arrow Functions

They don't have a this. It gets inherited from the parent scope.

```js
j
