---
Title: A Proof Of Stake Design Philosophy
Source: https://medium.com/@VitalikButerin/a-proof-of-stake-design-philosophy-506585978d51
---
Type: [[Article]]
Author: [Vitalik Buterin](Vitalik%20Buterin.md)
Subject: [Proof of Work](Proof%20of%20Work) [Proof of Stake](Proof%20of%20Stake.md)
Status: [[finished]] 
Abstract:
> -   Because proof of work security can only come from block rewards (in Dominic Williams’ terms, it [lacks two of the three Es](https://twitter.com/dominic_w/status/648330685963370496)), and incentives to miners can only come from the risk of them losing their future block rewards, **proof of work necessarily operates on a logic of massive power incentivized into existence by massive rewards**. Recovery from attacks in PoW is very hard: the first time it happens, you can hard fork to change the PoW and thereby render the attacker’s ASICs useless, but the second time you no longer have that option, and so the attacker can attack again and again. Hence, the size of the mining network has to be so large that attacks are inconceivable. Attackers of size less than X are discouraged from appearing by having the network constantly spend X every single day. **I reject this logic because (i) it** [**kills trees**](http://digiconomist.net/beci)**, and (ii) it fails to realize the cypherpunk spirit — cost of attack and cost of defense are at a 1:1 ratio, so there is no defender’s advantage**.

> -   **[Proof of stake](Proof%20of%20Stake.md) breaks this symmetry by relying not on rewards for security, but rather penalties**. Validators put money (“deposits”) at stake, are rewarded slightly to compensate them for locking up their capital and maintaining nodes and taking extra precaution to ensure their private key safety, but the bulk of the cost of reverting transactions comes from penalties that are hundreds or thousands of times larger than the rewards that they got in the meantime. **The “one-sentence philosophy” of [proof of stake](Proof%20of%20Stake.md) is thus not “security comes from burning energy”, but rather “security comes from putting up economic value-at-loss”**. A given block or state has $X security if you can prove that achieving an equal level of finalization for any conflicting block or state cannot be accomplished unless malicious nodes complicit in an attempt to make the switch pay $X worth of in-protocol penalties

Summary:
	Actors in a consensus adversarial system have different incentives. There is the extra economic incentive of taking down an entire network beyond the cost benefit analysis. Proof of Work requires ASIC chips that can be acquired and turned on or off immediately, and whose cost is exogenous to the system. If you make a failed attack you still have the hardware. Proof of Work relies on the cost of acquiring enough resources for an attack, while Proof of Stake relies on the penalty for behaving maliciously.
	T

Grokked: