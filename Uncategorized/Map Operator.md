- Taking the example from the `forEach` operator:
```
let numbers = [1, 2, 3, 4, 5]
let doubleArray = []
function doubleNumbers(item){
	doubleArray.push(item * 2)
}

numbers.forEach(doubleNumbers)

console.log(doubleArray) // outputs [2,4,6,8,10]
```
- 
we can achieve the same results with a `map` function, as this returns an array.
```
let numbers = [1, 2, 3, 4, 5]
function doubleNumbers(item){
	return (item * 2)
}

console.log(numbers.map(doubleNumbers)) // outputs [2,4,6,8,10]
```
- Much cleaner and understandable.

the `map` function also takes on 3 parameters, like the `forEach` they are the same also
```
[].map((item, index, array) => {} )
```

- It can just be an operator on each item. Map is nice to iterate over objects

```javascript
let users = [
    {name: "Javier", lastName: "Gonzalez", age: 28, membershipYears: 2},
    {name: "Phillip", lastName: "Reiner", age: 54, membershipYears: 5},
    {name: "Michael", lastName: "Lehlan", age: 21, membershipYears: 9}
]

let userAge = users.map((user)=>{
    return {
        userName: user.name + " " + user.lastName,
        ageWhenBecomingMember: (user.age - user.membershipYears)
    }
});

console.log(userAge);
//[
//  { userName: 'Javier Gonzalez', ageWhenBecomingMember: 26 },
//  { userName: 'Phillip Reiner', ageWhenBecomingMember: 49 },
//  { userName: 'Michael Lehlan', ageWhenBecomingMember: 12 }
//]
```

