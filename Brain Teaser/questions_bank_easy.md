###########################################################
1. Bridge Crossing
David, Emma, Frank, and Grace need to cross a river. The only possible way to cross the river is a bridge that can only hold at maximum
2 people at once. It's night time, so they can only cross the bridge using a lantern and they only have 1 lantern. Each pair of people can only cross at the pace of the slowest person. All people need to get across as fast as possible. Their crossing times are as follows: David takes 10 minutes, Emma takes 5 minutes, Frank takes 2 minutes, and Grace takes 1 minute. What is the minimum time required for all of them to get across to the other side?

A: 14. key is to pair the first two fastest people together than take the fastest person back, then pair the slowest ppl together, and then take the fastest person back from the other side. then use the fastest guy to take other guy back and forward.

1 vs 2 -> 2

1 return -> 1

5 vs 10-> 10'
2 return -> 2
1 vs 2 -> 2


###########################################################
2. What is the least positive multiple of 15 whose digits consist of 1's and 0's only?

A: 1110. In order for a number to be a multiple of 15, it must be perfectly divisible by both 3 and 5. The number must end by 0. and the sum of digits must be divided by 3.

###########################################################
3. Seating Drama


On a circular table of 5 seats, five people denoted 1,2,3,4,5 are seated.
4 wishes to sit immediately to the right of 2 while 2 sits immediately to the right of 5. Additionally 1 does not want to sit next to either one of 2 or 5. Who is to the left of 5?

A: 3

station 1 first -> can only sit next to 4 and 3

###########################################################
https://quantquestions.io/problems/2d-paths-i
You are playing a 2D game where your character is trapped within a 6×6 grid.
Your character starts at (0,0) and can only move up and right. How many possible
paths can your character take to get to (6,6)?
1. DP solution: 924
   - middle coeff of (x+y) ^ (6+6)
   - 12C6  = 12! / (6!*6!)
2. Combinatorics way:
   - path = [xxxxxx] [xxxxxx] (0,0 ->6,6: +x 6 times, +y 6 times)
   - 12 steps, doesn't matter order of ups or downs. but the sum ups or downs must
     be equal to 6.

```
| 1 |   |   |   |   | 462 | 924 |
|---+---+---+---+---+-----+-----|
| 1 |   |   |   |   |     | 426 |
|---+---+---+---+---+-----+-----|
| 1 |   |   |   |   |     |     |
|---+---+---+---+---+-----+-----|
| 1 |   |   |   |   |     |     |
|---+---+---+---+---+-----+-----|
| 1 | 3 | 6 |   |   |     |     |
|---+---+---+---+---+-----+-----|
| 1 | 2 | 3 | 4 | 5 |   6 |   7 |
|---+---+---+---+---+-----+-----|
| 0 | 1 | 1 | 1 | 1 |   1 |   1 |
|---+---+---+---+---+-----+-----|
```

###########################################################
https://quantquestions.io/problems/couple-handshakes
A room of four couples greet each other by shaking hands. If each person shakes
the hand of every other person besides their partner, how many handshakes occur?

(1,2) (3,4) (5,6) (7,8)

- Ans 1: 8*6/2 =24 (divided by 2 to remove dups)
  + 8 people to start. Each of these can only share with the other 6's (since we
    exclude the person and its partner)
- Ans 2: 8C2 - 4  ( 8 people, choose 2 people to shake hand with each other => 8C2, also minus 4 illegal handshakes between the couple itself => 24)


###########################################################
https://quantquestions.io/problems/theater-seating
You're taking your 10 students to the theater, the 5 boys and 5 girls are seated in a row.
To ensure that the children are engaged during the movie, the teacher states that no two children of the same gender can sit next to each other.
How many arrangements are possible for the kids?

- Ans: There are 2 patterns (boy-girl-boy-girl... or girl-boy-girl-boy...): the arrangements of the boys (5!) and the arrangements of the girls (5!).
Total arrangements = 2⋅5!⋅5! = 28800

###########################################################
https://quantquestions.io/problems/number-50
How many 10 digit numbers are there whose digits are prime and whose product of
its digits is exactly 100000?
- Ans: 10 C 5
  - 100000 = 10^5 = 2^5 * 5^5
  - among 10 places, we eval number of ways to arrange five 2's and five 5's

###########################################################
https://quantquestions.io/problems/car-crashes

On a given busy intersection, the probability of at least one car crash in a 1
hour time interval is 8/9 ​ Assuming that car crashes occur independently of one
another and at a constant rate throughout time, find the probability of at least
one car crash in a 30 minute interval.

A1:
- X = >=1 crash in 1 hr
- ~X = no crash in 1 hr
  + P(~X) = 1- 8/9 = 1/9
- Y_1 = no crash in 1st half.5 hours
- 1/9 = P(~X) = P(no crash 1 crash in 1 hours) = P(Y1*Y2) ->P(Y1)^2 = 1/9 ->
  P(Y1) = 1/3
- Ans: P(~Y1) = 1-1/3 =2/3


Z = number of car accidents, mean(Z) = mu. rare event: n*mu = lambda when n->
infty
--> then Z follow Poisson(lambda)

A2: X- number of car cash in 1 hour
 P(X=0) = no crash in 1 hr = (lambda ^k e -lambda )/ k!

=> lambda = log 9
lambda = rt => log 9 = r *1 => r = log 9
P (X=0 in interval 0.5) = (rt)^k e^(-rt)/k!
                        = e^ (-log(9)* 0.5)
                        = e^ -log (1/3) = 1/3

P (x> 1 in interval)  = 1 - P(X=0 in interval 0.5) = 1 - 1/3 = 2/3


###########################################################
https://quantquestions.io/problems/car-crashes
10 pairs of socks, each with a distinct color, are in a drawer. You draw out 2
socks at random. Find the probability that you obtain a matching pair.

10/20C2 = 1/19

###########################################################
https://quantquestions.io/problems/modified-even-coins
n coins are laid out in front of you. One of the coins is fair, while the other
n−1 have probability 0<λ<1 of showing heads. If all n coins are flipped, find
the probability of an even amount of heads.

- X = 1 H in the fair coin
- Y = number of heads is odd in n-1 tosses for unfair coins
- Z = number of heads is even in n-1 tosses for unfair coins
- Ans = P(Y and X) + P(Z and ~X) = P(X)*P(Y|X) + P(~X)*P(Z|~X)
  = 0.5*(P(Y|X) + P(Z|X)) = 0.5(P(Y) + P(Z)) = 0.5P(Y or Z) = 0.5 x 1  = 0.5

###########################################################
https://quantquestions.io/problems/poker-hands-i
A poker hand consists of five cards drawn from a standard deck of 52 cards. Let
p represent the probability of having a four-of-a-kind (i.e four of the five
cards share the same rank). Calculate the reciprocal of p.

- number of four-of-a-kind = 13
- p = (13 * (52-4)) / 52C5 -> 1/p = 4165

###########################################################
https://quantquestions.io/problems/poker-hands-i

You have a pile of 100 coins. 1 of the coins is an unfair coin and has heads on both sides. The remaining
99 coins are fair coins. You randomly select a coin from the pile and flip it 10 times. The coin lands heads all
10 times. Calculate the probability that the coin you selected is the unfair coin.

F - Pick fair coin
U - Pick unfair coin
H - Coin land head 10 times
F - Pick fair coin

P (U| H) = (P( H|U) P(U) ) /  P (H)

P( H|U) P(U) = 1 * 1/100 = 1/100


P (H) = P (U) P(H |U ) + P (F)    P (H|F)
      = 1/100 * 1      + 99/100 *   (1/2)^ 10

      = 1024/1123  = 0.912


###########################################################
https://quantquestions.io/problems/the-last-airbender
Four cards labelled water, earth, fire, and air are placed in front of you faced
down. You flip each of the cards over one at a time. You win if you flip over
both the air and water cards before the fire card. Otherwise, you lose. What is
the probability that you win?

Solution 1

```
|---+---+---+---+--------------------|
| A | W | F | E | x2 (swaps A and W) |
| E | A | W | F | x2 (swaps A and W) |
| A | W |   | F | x2 (swaps A and W) |
| W |   | A | F | x2 (swaps A and W) |

```


Total: 8

8/4! = 1/3


A: 4 slots to choose
P (1st card is fire) = 1/3! ( only three slots remaining)
P(2nd card is fire) = 1/2! ( the slots remaining)
P(wnining) = 1 - 1/6 - 1/2 = 1/3

###########################################################
https://quantquestions.io/problems/the-last-airbender

A chess tournament has 128 players, each with a distinct rating. Assume that the player with the higher rating always wins against a lower rated opponent and that the winner proceeds to the subsequent round. What is the probability that the highest rated and second-highest rated players will meet in the final?

A: Devide set of players into 2 bracket (sets). If the hightest and second highest is in the same half then those players are guarantees to meet each other at some point before the final. so those 2 players have to be in 2 different sets.
- the first player can be anywhere in 128 positions
- the second player has to be in diffrent half => 64/127 (64 availables for 2nd half, 127 remaining total positions)
=======

###########################################################
Comparing Flips II


You and your friend are playing a game with a fair coin, tossing it and writing down the outcomes. You win if HTH appears before HHT, else your friend wins. What is the probability that your friend wins?

F: Friend wins (HHT)
Y; you wins ( HTH)
Roll the coin till H. From H, we have 2 branches: HT and HH => P_hh = P_ht = 1/2

P(HTH) = P(HH) P (HTH | HH) + P(HT) P(HTH | HT)

  = 1/2 * 0 +   1/2  P(HTH|HT)



P(HTH|HT) = P(HTH | HTH) P(HTH) + P(HTH | HTT) P(HTT)

          = 1/2            +    P(HTH | HTT) * 1/2


P(HTH|HTT) = P(HTH)


=> P(HTH) = 1/2 * 0 +   1/2  * [1/2  +   P(HTH) * 1/2 ]


=> P(HTH) = 1/3

=> P(HHT) = 1 - 1/3 = 2/3

###########################################################
https://quantquestions.io/problems/basic-dice-game-i
A casino offers you a game with a 6-sided die where you are paid the value of
the roll. The casino lets you roll the first time. If you are happy with your
roll, you can cash out. Else, you can choose to re-roll and cash out on this
second value. What is the fair value of this game?

- =E(X) = E(X* [X < 3.5] ) + E(X* [X >= 3.5]) = 4.25
  1. E(X* [X < 3.5] )  = 3/6 * (1+2+3) = 3
  2. E(X* [X >= 3.5] ) = E(X*[X>3.5] | X>3.5) = P(X>3.5) * E(X | X>3.5)
      = 1/2 * (4/6+5/6+6/6) = 15/12

###########################################################
https://quantquestions.io/problems/dangerous-doubles
Two fair coins are flipped at once. You receive $2 if exactly one heads that
appears, but you lose
$7 if you flip two heads. What is your expected profit/loss on this game if you
play once?

Ans: 2*0.5 - 7*0.25 = -0.75

###########################################################
https://quantquestions.io/problems/magic-doors
Jeff is trapped in a room with 5 indistinguishable doors. Behind 2 of the doors
are paths to freedom; one path is 2 miles long, and the other path is 5 miles
long. Behind 3 of the doors are paths that magically lead back to the room; one
path is 1 miles long, another path is 3 miles long, and the final path is 4 mile
long. If Jeff returns to the room, the order of the doors are scrambled and the
5 doors are once again indistinguishable. What is the expected number of miles
Jeff will travel before reaching freedom?

X - number of miles that Jeff travels given that Jeff didn't choose freedom door

E(X) = P(freedom) * E( distance if choosing freedom) + P( return) * [ E
(distance traveled if choosing back door to return to the start) + E ( total
distance traveled until freedom) ]

   E(X) = E(X*[Pick freedom door]) + E(X*[Pick return door])
        = 2/5*(1/2(2+5)) + 3/5*(8/3 + E(X))

   --> E(X)    = 2/5  * 7/2    + 3/5 *8/ 3 +  3/5*E(X)
               = 14/10  +  24/15 + 3/5 * E(X)
--> 2/5 E(X) = 3 --> E(x) = 7.5
