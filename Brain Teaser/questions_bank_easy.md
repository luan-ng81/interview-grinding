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


