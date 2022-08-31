---
Title: A Hands-On Tutorial for Zero-Knowledge Proofs Part I
Source: 
---
Type: [[Article]]
Author: 
Subject:
Status: [[In Progress]]
Abstract:
Summary:
## Definition
>Zero Knowledge (AKA ZK) proofs are stories of the following type: side A states a claim and proves it to side B, after some deliberation between them, such that:
>B is sure that the claim is true with 99.99999% certainty.
>B has learnt nothing new in the process, other than that the claim is true.

Example: 
Given a sequence of numbers a0,a1,...,an−1a0,a1,...,an−1, can one partition this sequence into two subsets that sum up to the same number?
> If the sequence in question is 1,9,8,0,2,2  then the answer is clearly yes since 2+9=8+1+2+02+9=8+1+2+0.
> However if the sequence is 2,3,4,5,6,7 then the answer is clearly no, since the sum is odd,

You can do a proof of this if it satisfies the following requirements:
	list m and list l
	true if m consists of a range where all elements are 1 or -1
	len(m) == len(l)
	the dot product of l and m is 0
	$$p_i:=\sum\ _{0≤k<il}[k]⋅m[k]$$


Grokked: