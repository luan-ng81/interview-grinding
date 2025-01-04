###########################################################
1. 100 Lights

There are 100 light bulbs in a room, each initially off and with its switch by its side. The first person enters and flips every switch. The second person enters and flips every other switch. The third person enters and flips every third switch. This process continues until the 100-th person flips every 100-th switch, or the last switch. How many lights are on?


A: 10

From ceil(n//2) ppl, the effect of their options only applies to themself.
Also impact of p1 always affects on everyone 
Also, prime number person only takes actions from itself, and action from p1 -> always off. 

The rest will have at least 2 actions. 
Another note: each person is multiple of at least 1 person (because it's not prime, so it's either a x b  or a* a). If it has two different decompositions then it's always off. but if it only has 1 unique decomposition -> then it only has at most one more additional effect.> it turns on. 
Important: the question turns out to count the number of n^2 between 1-100 which is basically from 1-> 10 


###########################################################
Q: Digit Sum: Calculate the sum of the digits from 1 to 1 million, inclusive? For example, the sum of the digits of 46 is 10.

A: 27000001: 27 x 10^5 + 1 

[000000   000010
 000001   000011
 ...
 000009
]