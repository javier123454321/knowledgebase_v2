- [[The Law Of Leaky Abstractions]]
    - https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/
    - TCP is a reliable abstraction built over IP. 
    - [[Internet Protocol]] (IP) does not guarantee order, does not guarantee data delivery, and has no information about whether a packet has arrived. The [[Transmission Control Protocol]] (TCP) is what adds an abstraction that looks at whether something has arrived, in what order, and polls the source if it was sent but got lost on the way.
