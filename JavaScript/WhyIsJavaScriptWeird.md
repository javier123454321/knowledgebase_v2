# Why is JS so weird

As far as I understand it (and this is more of an attempt at me
explaining it to myself than anything else) JS is weird by design, as it
was conceived as a tool to make the web interactive. 

Looking through the LearnCode.academy Youtube Videos about this topic,
there are 5 language quirks that make it incredible 

I found this playlist that gives a quick explanation on 5 elements of js:
[Playlist](https://www.youtube.com/watch?v=JEq7Ehw-qk8)


1. **Functions are Objects**
1. **JS is Event-Driven**
1. **JS keeps its state in Memory after a Function has been executed (Closure)**
1. **Scope** allows you to access data declared in the memory of the
parent.

The following is an attempt to explain this to myself.

## Functions are objects in Javascript
Actually, almost everything is an object in JavaScript. Arrays are
objects and functions are objects. That makes it so you can declare a
function in many different ways i.e.
```js
function regularFunction(){
	console.log("regularFunction")
	}

var functionExpression = function(){
	console.log("functionExpression")
	}

var arrowFunction = ()=>{
	console.log("arrowFunction")
	}
```

You can pass any of these functions as parameters in other functions.
```js
function callBackDemo(func1, func2, func3){
	func1();
	func2();
	func3();
	}

callBackDemo(regularFunction, functionExpression, arrowFunction);
//or you can declare it in the argument itself:
callBackDemo(
	regularFunction, 
	regularFunction, 
	()=>{
		console.log("callback declared in the argument");
	})
```
### Output
>
> regularFunction
> functionExpression
> arrowFunction
> 
> regularFunction
> regularFunction
> callback declared in the argument 
>

This is useful for handling click and other events
so if we declare a `handleclick` function, for example:

```js
function handleClick(){
	alert("click happened")
	}

document.getElementById("btn1").addEventListener("click", handleClick);
```

## JS is event-driven
Javascript was built for making the web interactable.
it therefre keeps listeners for certain events, like button clicks,
mouseovers, async responses, and many other quircky things. 

so in the last example:
```js
function handleClick(){
	alert("click happened")
	}

document.getElementById("btn1").addEventListener("click", handleClick);
``` 

this will make it so that handleClick is called everytime a person
clicks button of id `[[btn1]]`. 

This is different than scripting languages where once the program reaches the bottom of the file, it 'dies'. 

In Javascrpit, the alert will not happen UNTIL the button is clicked. 

JS keeps its memory open for events when you instruct it to.

likewise if you run:
```js
var buttonMessage = "button clicked";
console.log("initial set-up");

function handleClick(){
	console.log(buttonMessage)
	}

document.getElementById("btn1").addEventListener("click", handleClick);
```

### Output:
> initial set-up

And after btn1 is clicked:
> button clicked

The second message ("button clicked") is the output after a button click, meaning that the entire file does not have to run from the top again (there is no initial set-up message on the console). Javascript keeps the variable in working memory while there is an event listener for it.

This allows Node to be so performant, making it only call the parts of memory which are necessary to perform for that portion of the application.

## JS keeps its state in Memory after a Function has been executed ([Closures](Closures.md))


Take the example of the function above, but wrap it into an initializing function:
```js
function setUp(){

    var buttonMessage = "button clicked";

    console.log("initial set-up");

    function handleClick(){
        console.log(buttonMessage)
        }

    document.body.innerHTML += `<button id="btn1">click me!</button>`;

    document.getElementById("btn1").addEventListener("click", handleClick);
};

//Remember to call it so that everything runs at least once.
setUp();
```

The outcome is the same as above:
### Output:
> initial set-up

And after btn1 is clicked:
> button clicked

This is incredibly useful because JS only keeps the bits in memory which it needs to. It is calling only the part of the function which it needs (even if the scope of variable `buttonMessage` is not even on the handleclick function);

```js
function setUp(){
    var buttonClicks = 0;

    function handleClick(){
        var buttonMessage = `button clicked ${buttonClicks} times`;
        console.log(buttonMessage);
		buttonClicks += 1;
        }

    document.body.innerHTML += `<button id="btn1">click me!</button>`;

    document.getElementById("btn1").addEventListener("click", handleClick);
};

//Remember to call it so that everything runs at least once.
setUp();
```

### Output

>button clicked 0 times
>button clicked 1 times
>button clicked 2 times
>button clicked 3 times
>button clicked 4 times
>button clicked 5 times
>button clicked 6 times
>button clicked 7 times

The problem with this is that it can leave a lot of things in memory, which we might want to avoid in a large application to ensure performance. 

If that is the case, you can run:
```js 
document.getElementById("btn1").removeEventListener("click", handleClick);
```
to free that memory space back up (garbage collection).

**Closure** is a refrence to the place in memory that is kept 'alive' after the the function has finished running (even if it will not be called again)

## [[Scope]]
JavaScript allows you to call variables 