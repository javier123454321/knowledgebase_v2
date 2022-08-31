---
Title: Demystifying Zero Knowledge Proofs How To Build DApps With zk-SNARKs
Source: 
---
Type:  [[Video]] 
Author: [[Dystopia Labs]]
Subject:[Zero Knowledge Proofs](Zero%20Knowledge%20Proofs.md)[ZK-Proofs](ZK-Proofs.md)
Status: [[In Progress]] 
Abstract:
Summary:
	ZK-Proofs is a way to achieve *Honest Computation* ***NOT*** privacy
	For example mining, proove that I have done the computation to include in  a block, and all the computations are verifiable, so here is a proof. 
	3 main types of ZK-Proofs
		[[SNARKs]] small proof size
			ZCash uses ZK-SNARKS.
		[[STARKs]] large proof size, 
			[[Starkware]]
		[[Bulletproofs]] really small proof size, 
			Range proofs used by Monero. 
	[[Cryptography]]
		Modular math, pretend my world is bound by a particular number.
		[[Diffie Hellman]] - Obsessed with the problem of sharing an decryption key to an encrypted message. 
			How to establish a shared secret so that only the interested parties can decrypt it
			$$p = 23 { (modulous) }$$ $$g = 5 { (base) }$$ 
			Alice chooses a secret `a = 4` and sends Bob the following function: $$A = g^a \mod p$$
			i.e.: $$A = 5^4\mod 23=4$$
			Then Bob chooses a secret `a = 3` and sends Alice $$B = g^b \mod p$$
			i.e.:
			$$B = 5^3 \mod 23 = 10$$
			You can share each other's public key and get enough information to compute a shared secret. So Alice can compute a secret `s` which equals: $$s = B^a \mod p$$
			$$s=g^{ba} \mod p = 10^4 \mod 23 = 18$$
			Bob does the same thing with his private key and gets the same answer:
			$$s=g^{ab} \mod p = 4^3 \mod 23 = 18$$
			18 is the shared secret.
Grokked: