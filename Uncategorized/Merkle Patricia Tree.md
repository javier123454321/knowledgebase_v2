A data structure that allows you to verify that an element exists in an array without having to go through the entire array.

Start with a non-empty array that is of length `2^n`
You then hash the elements of the array in pairs
```
[num1, num2, num3, num4, num5, num6, num7, num8]

[hash(num1), hash(num2)] -> hashed1_2
[hash(num3), hash(num4)] -> hashed3_4
[hash(num5), hash(num6)] -> hashed5_6
[hash(num7), hash(num8)] -> hashed7_8

[hashed1_2, hashed3_4, hashed5_6, hashed7_8]
```
The benefit of Merkle proofs is that it allows you to verify if a hash should be included in the chain without having to compute the hash of every single item in the original array.
