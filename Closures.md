- [[Javascript]] functions have access to the parent's variables and state. 
- For example: 
- ```javascript
- let globalVariable = "Global Scope";
- function grandparent(paramVariable){
    - let grandparentVariable = "Grandparent Scope"; 
    - //here we have access to globalVariable, paramVariable, and grandparentVariable   
    - console.log(`\n=============================\ngrandparent Scope: \n${globalVariable} | ${paramVariable} | ${grandparentVariable} \n=============================\n\n`); 
- }
- grandparent("Parameter Variable");```
- Output:
    - ```javascript
=============================
grandparent Scope: 
Global Scope | Parameter Variable | Grandparent Scope
=============================```
- if we add a function within the grandparentFunction, we could still access all the same variables
- ```javascript
let globalVariable = "Global Scope";
function grandparent(paramVariable){
	let grandparentVariable = "Grandparent Scope"; 
		
	function parentFunction(){	
		console.log(`\n=============================\nparent Scope: \n${globalVariable} | ${paramVariable} | ${grandparentVariable} \n=============================\n\n`); 
	}
	parentFunction();
}

grandparent("Parameter Variable");```
- Outputs:
    - ```javascript
let globalVariable = "Global Scope";
function grandparent(paramVariable){
	let grandparentVariable = "Grandparent Scope"; 
		
	function parentFunction(){	
		console.log(`\n=============================\nparent Scope: \n${globalVariable} | ${paramVariable} | ${grandparentVariable} \n=============================\n\n`); 
	}
	parentFunction();
}

grandparent("Parameter Variable");```
        - Basically nothing changes, but the scope which is being used to call the function. 
