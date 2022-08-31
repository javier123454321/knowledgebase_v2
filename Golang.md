- Constants
    - You cannot declare a constant that is a result of a function execution
        - Constants are declared at compile time, and function executions are handled at run time, making this: `const myConst float64 = math.Sin(1.57)`  an invalid expression
        - Also means you cannot set constants equal to flags that get set when your app runs.
    - A constant gets replaced immediately during compile time so the type of b is int:
        - ```c++
main() {
	const a = 15  
  	var b int16 = 2
  	fmt.PrintF("%v, %T\n", a + b, a + b) //here a gets replaced by 15 at compile time
}```
- Arrays
    - You need to specify the type of data you will store
        - `grades := [3]int{93, 97, 72}`
    - Elements are contiguous in memory (Hence why we need the fixed length)
        - Access is really fast
    - in `grades := [3]int{93, 97, 72}` we are repeating the array size twice, you can omit the length in this declaration:
        - `grades := [...]int{93, 97, 72}`
    - You can also declare an aray with fixed size but no values yet.
    - copying a variable whose value is an array creates a copy of the entire array (unless you use a pointer)
        - ```javascript
a := [...]int{93, 97, 72} 
b := a // b is a copy of the entire array
b := &a //b is a pointer to the same memory which is storing the array of a```
- Slices
    - Create a subarray (which points to the underlying value)
    - `grades := [...]int{93, 97, 72, 18}`  `finalgrades := grades[2:]`
    - Can slice an array or a slice
    - Slices can be appended, go copies the underlying array and creates an assignment to a new pointer in memory
    - created with the standard `make()` function
    - When you append to a slice, the new slice is created if the capacity for the previous slice is exceeded. It is usually double the previous capacity, so using append() right above the limit can create a lot of memory space that is not used.
- Maps
    - A fixed type for key and a fixed type for value.
    - The key Has to be testeable for equality (no slices)
    - the make() function also makes a map
    - The return order of a map is not guaranteed, it's not mapped to consecutive bits of memory
    - After deleting a value, when you try todirectly access it like `population["Ohio"]`  the value could read 0 if it is not defined.
        - to verify that the key has a value, you usually use `population, ok := population["Ohio"]`
        - Maps are passed by reference
    - 
