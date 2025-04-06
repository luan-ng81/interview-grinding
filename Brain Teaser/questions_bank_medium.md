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
- Ans: 2 * 8C4

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

###########################################################
https://quantquestions.io/problems/dice-order-i

You roll two fair dice. What is the probability that the highest value rolled is a four?

X - Max of all coins

P(X=4) = P(X<=4) - P(X<=3)
       = (4/6)^2 - (3/6)^2
       = 7/36

###########################################################
https://quantquestions.io/problems/odd-coin-flips
You flip 100 fair coins simultaneously. What is the probability that you observe
an odd number of heads?

Ans: X is the number of heads odd. P(X) = 1 - P(number of heads even) = 1 - P(X)
due to symmetry -> P(X) = 0.5

###########################################################
https://quantquestions.io/problems/better-in-red-i
A 10×10×10 cube is painted red on the surface and then cut into 1000 =1×1×1= cubes
and one is selected uniformly at random. Find the expected number of red faces
on this cube.

numbers of

```
| 3-face | 2-face | 1-face |
|--------+--------+--------|
|      8 | 8*4*3  | 8^2*6  |

Expected val = (1*384 + 2*96 + 3*8) / 1000 = .6
```



###########################################################
https://quantquestions.io/problems/collecting-toys-i
Every box of cereal contains one toy from a group of five distinct toys, each of
which is mutually independent from the others and is equally likely to be within
a given box. On average, how many boxes of cereal will you need to open in order
to collect all five toys?

https://math.stackexchange.com/questions/4810444/toy-collection-question

```
5/5+5/4+5/3+5/2+5/1=137/12
```


###########################################################

https://quantquestions.io/problems/heads-and-tails-i
On average, how many flips of a fair coin will it take until you observe heads immediately followed by tails?

Hint: If you get tails on your first toss, then you must start over again. If
you gets heads on your first toss, then you can either get HH or If you get HT,
then you are done. Otherwise, you only need one more tail to finish the game on
the next turn. How can you set up an equation with these cases in mind?

X = # flips till getting HT

E (X) = 1. + 2. = 1/2 * (3) + 1/2 * (1 + E(X))
E(X) = 4

1. 1st flip = H
   1/2 * E(X | 1st flip = H)
      E(X | 1st flip = H) = 1 + E(# of flips till getting a T)
                          = 1 + 1/(1/2)
2. 1st flip = T
   1/2 * E(X | 1st flip = T)
       E(X | 1st flip = T) = 1 + E(X)

https://quantquestions.io/problems/repetitious-game-ii
(coupon collection problem)

Audrey repeatedly draws cards from a standard 52-card deck with replacement.
Compute the expected number of draws for Audrey to get at least one card from
each suit.

1 + 52/39 + 52/26 + 52/13 = 8.3333

X1 = number of draws for the first suite
X2 = number of draws for the 2nd suite, different than 1st suite
X3 = number of draws for the 3rd suite, different than 1st suite and 2nd suite
X4 = number of draws for the 3rd suite, different than 1st suite and 2nd suite,
and 3rd suite

X2, X3, X4 ~ geometric distributions
E(X1 + X2 + X3 + X4) = 1 + 52/39 + 52/26 + 52/13 = 8.3333
