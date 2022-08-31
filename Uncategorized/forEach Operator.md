- the `forEach()` operator allows you to do something to each item in the array.
Takes in a callback function.

    - 
```
let numbers = [1,2,3,4,5];
numbers.forEach((item, index, array) => {
	console.log(item) // 1, 2, 3, 4, 5
	console.log(index) // 0, 1, 2, 3, 4
	console.log(array) //[1,2,3,4,5], [1,2,3,4,5], [1,2,3,4,5], [1,2,3,4,5], [1,2,3,4,5]
	})
```
    - Output
```
1
0
[ 1, 2, 3, 4, 5 ]
2
1
[ 1, 2, 3, 4, 5 ]
3
2
[ 1, 2, 3, 4, 5 ]
4
3
[ 1, 2, 3, 4, 5 ]
5
4
[ 1, 2, 3, 4, 5 ]
```
    - 
In this case we are doing an anonymous function, but you can input an actual function.

        - 
```javascript
let doubleArray = []
function doubleNumbers(item){
	doubleArray.push(item * 2)
}

numbers.forEach(doubleNumbers)

console.log(doubleArray) // outputs [2,4,6,8,10]
```

- However, to do the above, and return a new array, you are better off using the `map()` operator.
