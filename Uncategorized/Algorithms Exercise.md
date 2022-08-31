## Two Sum
### Problem
Given a **1-indexed** array of integers `numbers` that is already **_sorted in non-decreasing order_**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.
>**Example 2:**
**Input:** numbers = [2,3,4], target = 6
**Output:** [1,3]
**Explanation:** The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].

>**Example 3:**
**Input:** numbers = [-1,0], target = -1
**Output:** [1,2]
**Explanation:** The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].

Simple solution, check items linearly, keep a hash table of visited items to check whether the solution has already been checked.
```ts
function twoSum(numbers: number[], target: number): number[] {
    const visited = {};
    visited[numbers[0]] = 0;
    for (let i = 1; i < numbers.length; i++) {
        if(visited[target - numbers[i]] !== undefined){
	        return [visited[target - numbers[i]] + 1, i+1];
		}
        visited[numbers[i]] = i;
    }
    return []
};
```


```ts
function twoSum(numbers: number[], target: number): number[] {
    const visited = {};
	let left = 0;
	let right = numbers.length;
	let curr = Math.floor((left + right) / 2)
    while (Math.floor(left - right) <= 1) {
	    
        if(visited[target - numbers[i]] !== undefined){
	        return [visited[target - numbers[i]] + 1, i+1];
		}
        visited[numbers[i]] = i;
    }
    return ans
};
```
## Three Sum
Given an integer array nums, return all the triplets 
`[nums[i], nums[j], nums[k]]` 
such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**
```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```

Dumb approach: 
make an array of arrays for every possible 3 combination of numbers, filter out those that don't add to 0