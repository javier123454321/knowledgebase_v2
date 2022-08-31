- # [[Javascript]] Object Prototypes
- JS has the ability to assign a value to an abject upon its creation.
    - i.e.:
```javascript
function P[[Article]](){
	this.x = 5;
	this.y = 5;
	}

let p = new P[[Article]]();

console.log(p);```
- Outputs: 
    - ```javascript
P[[Article]] {x: 5, y: 5}
x: 5
y: 5
__proto__: Object```

- You can also set up a function on its creation
- ```javascript
function P[[Article]](){
	this.show = function(){
		console.log(this.x, this.y);
		};

	this.x = 5;
	this.y = 5;
	}

let p = new P[[Article]]();

console.log(p);```
- However, this is inneficient as it would create a new show function for each object instance. Given that the functionality does not change depending on the P[[Article]] object (only its coordinates) a better approach is to declare it on the Object Prototype.
- ```javascript
function P[[Article]](){
	//Instead of using this method:
    //this.show = function(){
	//    console.log(this.x, this.y);
    //    };

    this.x = 5;
    this.y = 5;
    }

//We can give an attribute to the Prototype of P[[Article]]

P[[Article]].prototype.show = function(){
	console.log(this.x, this.y);
	}

let p = new P[[Article]]();

console.log(p);
Outputs:

P[[Article]] {x: 5, y: 5} 
	x: 5 
	y: 5 
	__proto__: 
		show: ƒ () 
		constructor: ƒ P[[Article]]() 
		__proto__: Object```
- Outputs
    - ```javascript
P[[Article]] {x: 5, y: 5} 
	x: 5 
	y: 5 
	__proto__: 
		show: ƒ () 
		constructor: ƒ P[[Article]]() 
		__proto__: Object```
