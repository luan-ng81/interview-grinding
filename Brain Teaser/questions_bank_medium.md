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

- DN's solution

- https://quantquestions.io/problems/digit-sum
  Calculate the sum of the digits from 1 to 1 million, inclusive? For example, the sum of the digits of 46 is 10.

C1 = 45*10^5
c2 = [0*10 + 1*10 + ... + 9*10] * 10^4 = 10*(0+...+9) * 10^4
c3 = [0*100 + 1*100 + ... + 9*100] = 10^2*45*[10 ^3] = 45*10^5
...

ans = c1 + c6 = 6*10^5*45 + 1 = 27,000,001
```
| c6| c5| c4| c3| c2| c1|
|---+---+---+---+---+---|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 0 | 0 | 2 |
| 0 | 0 | 0 | 0 | 0 | 3 |
| 0 | 0 | 0 | 0 | 0 | 4 |
| 0 | 0 | 0 | 0 | 0 | 5 |
| 0 | 0 | 0 | 0 | 0 | 6 |
| 0 | 0 | 0 | 0 | 0 | 7 |
| 0 | 0 | 0 | 0 | 0 | 8 |
| 0 | 0 | 0 | 0 | 0 | 9 |
|---+---+---+---+---+---|
| 0 | 0 | 0 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 1 | 1 |
| 0 | 0 | 0 | 0 | 1 | 2 |
| 0 | 0 | 0 | 0 | 1 | 3 |
| 0 | 0 | 0 | 0 | 1 | 4 |
| 0 | 0 | 0 | 0 | 1 | 5 |
| 0 | 0 | 0 | 0 | 1 | 6 |
| 0 | 0 | 0 | 0 | 1 | 7 |
| 0 | 0 | 0 | 0 | 1 | 8 |
| 0 | 0 | 0 | 0 | 1 | 9 |
...
| 0 | 0 | 0 | 0 | 9 | 0 |
| 0 | 0 | 0 | 0 | 9 | 1 |
| 0 | 0 | 0 | 0 | 9 | 2 |
| 0 | 0 | 0 | 0 | 9 | 3 |
| 0 | 0 | 0 | 0 | 9 | 4 |
| 0 | 0 | 0 | 0 | 9 | 5 |
| 0 | 0 | 0 | 0 | 9 | 6 |
| 0 | 0 | 0 | 0 | 9 | 7 |
| 0 | 0 | 0 | 0 | 9 | 8 |
| 0 | 0 | 0 | 0 | 9 | 9 |
....
|  9| 9 | 9 | 9 | 9 | 9 |
```
1000 000

###########################################################


Q: Egg Drop I

You have two identical eggs in a 100-story building, you don't know the floor the eggs will break on. If an egg is dropped at an elevation under story X then the egg will survive; else, the egg breaks. What is the minimum number of drops required to determine X in the worst-case scenario?

A: 14
The key observation in this questions is that the answer is the minimum number of trials to figure out X in the worst scenario.

If only one egg is available and we wish to be sure of obtaining the right result, the experiment can be carried out in only one way. Drop the egg from the first-floor window; if it survives, drop it from the second-floor window. Continue upward until it breaks. In the worst case, this method may require 100 droppings.
Suppose 2 eggs are available. What is the least number of egg droppings that are guaranteed to work in all cases?
The problem is not actually to find the critical floor, but merely to decide floors from which eggs should be dropped so that the total number of trials is minimized.

If we use Binary Search Method to find the floor and we start from the 50’th floor, then we end up doing 50 comparisons in the worst case. The worst-case happens when the required floor is 49’th floor.

Optimized Method: The idea is to do optimize the solution using the below equation:


Let us make our first attempt on x'th floor.

If it breaks, we try remaining (x-1) floors one by one.
So in worst case, we make x trials.

If it doesn't break, we jump (x-1) floors (Because we have
already made one attempt and we don't want to go beyond
x attempts.  Therefore (x-1) attempts are available),
    Next floor we try is floor x + (x-1)

Similarly, if this drop does not break, next need to jump
up to floor x + (x-1) + (x-2), then x + (x-1) + (x-2) + (x-3)
and so on.

Since the last floor to be tried is 100'th floor, sum of
series should be 100 for optimal value of x.

 x + (x-1) + (x-2) + (x-3) + .... + 1  = 100

 x(x+1)/2  = 100
         x = 13.651

Therefore, we start trying from 14'th floor. If Egg breaks on 14th floor
we one by one try remaining 13 floors, starting from 1st floor.  If egg doesn't break
we go to 27th floor.
If egg breaks on 27'th floor, we try floors form 15 to 26.
If egg doesn't break on 27'th floor, we go to 39'th floor.

An so on...

- DN's reference: Solution: [[https://medium.com/@khopsickle/2-eggs-and-100-floors-a032beb77aaa][2 Eggs and 100 Floors. Let’s talk about the 2 Egg problem… | by Catherine Kwa...]]
  + x + (x-1) + (x-2) + (x-3) + .... + 1
  + x(x+1)/2 = 100 x = 13.651 -> ans = 14

###########################################################
https://quantquestions.io/problems/picture-day
Ten students of distinct heights are lining up for a picture. The photographer
requires that the two tallest students stand in the two center positions and
that the remaining students line up such that the heights strictly descend
outwards. How many ways can the students line up?
- Ans: 2 * 8C2

  WLOG, heights = [1,...,10]. The number of ways that 4 spots to the left of
  position 5th (center) be filled is 8C4 since there are 8 heights left and
  combination disregard of orders (hence, taking into account of descending
  condition)

- Arrange 10 first, 9 second
```
| pos     | 1 | 2 | 3 | 4 |  5 | 6 | 7 | 8 | 9 | 10 |
|---------+---+---+---+---+----+---+---+---+---+----|
| heights |   |   |   |   | 10 | 9 |   |   |   |    |
```

- Arrange 9 first, 10 second
```
| pos     | 1 | 2 | 3 | 4 | 5 |  6 | 7 | 8 | 9 | 10 |
|---------+---+---+---+---+---+----+---+---+---+----|
| heights |   |   |   |   | 9 | 10 |   |   |   |    |
```
