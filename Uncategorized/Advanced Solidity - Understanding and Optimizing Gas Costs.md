---
Title: Advanced Solidity - Understanding and Optimizing Gas Costs
Source: https://www.udemy.com/course/advanced-solidity-understanding-and-optimizing-gas-costs/learn/lecture/31856136#overview
---
Type:  [[Lecture]] 
Author: [Jeffrey Scholz](https://www.udemy.com/user/jeffrey-scholz/)
Subject: [[Solidity]] [Ethereum](Uncategorized/Ethereum.md) [Programming](Uncategorized/Programming.md)
Status: [[finished]] [[In Progress]] [[want to read]]
Abstract:
Summary:
	Each slot can be accessed by the assembly code {variablename}.slot
	so for example: 
```js
contract Storage {
	uint256 a = 2
	uint90 b = 20
	uint90 c = 40
	function getSlot() external view returns (uint256) {
		uint slotA;
		uint slotB;
		uint slotC
		assembly {
			slotA := a.slot // 0
			slotB := b.slot // 1
			slotC := c.slot // 1
		}
		
	}
}
```
When you call a function like:
```js
uint a = 3
function aPlusOne() {
	return a + 1;
}
```
The computer translates it to assembly in this way:
```js
PUSH 0 // pushes the number 0 to the top of the stack
LOAD   // get the bytes from the storage location 0 (the number at the top of the stack) and loads them to memory
PUSH 1 // pushes the value 1
ADD    // Only looks at the top of the stack to do the operation
```
```js
try: 5x + 3y where x = 10 and y = 20

//stack []
PUSH 5 // refering to the value 5
//stack [5]
PUSH 0
//stack [5, 0]
LOAD   // gets the variable at storage 0
//stack [5, 10]
PUSH 3
//stack [5,10,3]
PUSH 1
//stack [5,10,3,1]
LOAD
//stack [5,10,3,20]
MUL // the last two items in the stack
//stack [5,10,60]
SWAP 2
// stack [60,10,5]
MUL
//stack [60,50]
ADD
//stack[110]

```
Grokked: