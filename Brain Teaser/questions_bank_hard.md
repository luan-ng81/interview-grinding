###########################################################
https://quantquestions.io/problems/forming-a-triangle
A stick of 1 metre is randomly broken into three pieces. Given each break
follows a uniform distribution along the stick, what is the probability that the
three segments can form a valid triangle?

Hint: Graph the sample space in 2D space. Let x∈[0,1] be the first break and
y∈[0,1] be the second break. What points in space work, what points don't? From
there how do you represent this algebraically. (Note: the conditions of a valid
triangle are that each side length must be less than the sum of the other two
side lengths.)

- Let X1, and X2 be uniformly distributed [0,1]. WLOG X1 <= X2
- Then, S1 = X1, S2 = X2-X1; S3=1-X2

```
|  0 | X1 | X2 |  1 |
|----+----+----+----|
| S1 | S1 |    |    |
|    |    | S2 |    |
|    |    |    | S3 |
```

- The conditions of a valid triangle are that each side length must be less than
  the sum of the other two side lengths
  1) P(S1 + S2 > S3) -> P(X2 > 0.5)
  2) P(S1 + S3 > S2) -> P(X2 > X1 + 0.5)
  3) P(S2 + S3 > S1) -> P(X1 < 0.5)
- Draw a unit square, the area of condition 2) is 1/4. In addition, the region
  of (X1, X2) also satisfies conditions 1) and 2). Hence the answer is 1/4


###########################################################
https://quantquestions.io/problems/marble-runs

You repeatedly draw marbles from a bag containing 50 red and 50 blue marbles until there are no more marbles left, recording the order of red and blue marbles drawn. You then count the number of "runs,'' where a run is defined as any number of consecutive marbles of the same color. For example, RBBRRRBRR contains 5 runs. What is the expected number of runs that you observe?

The number of runs is equal to the number of starts of runs. Let X_i be an indicator of whether color change at each run, X_i \in {0, 1}. 

So we want to compute: E(X1 + ... + X_100) = E(X_1) + ... + E(X_100)

E(X_1)=1

Now we want to compute E(X_i) = 1 * P(color changed) + 0 * P (no color changed)

P (color changed) = P(picking a pair with different color) = # of pairswith different color / # of pairs 

Compute: # of pairs = 100 * 99 
Compute: # of pairs with different color: 100 * 50

=> P(picking a pair with different color) = 50 /99 

=> E(X_i) = 50/99
=>  E(X1 + ... + X_100) = 1 + 99 * 50/99 = 51


###########################################################
https://quantquestions.io/problems/marble-runs

You uniformly select two random points from the circumference of the unit circle. Find the expected length of the chord (line segment) between the two points, with the answer is in the form x/\pi for some rational number x. Find x. 

Picking the two points uniform on the circumference is equivalent to picking these two angles. The measure of the angle between 
is \theta.  

Fix one of the points at (1, 0). Pick the other point uniform (0, \pi) (as symmetry)
=> \theta also go from (0, \pi) due to symmetry.
Use formula of chord length on unit circle: 2 * sin (\theta /2) (derive from Eucledian distance and each point on unit circle has cordinate (cos(\theta), sin(\theta))

Thus :

$$
E(X) = \int_0^\pi \frac{1}{\pi} \times 2 \sin\left(\frac{\theta}{2}\right) \, d\theta  = \frac{4}{\pi} \int_0^{\pi/2} \sin(u) \, du = \frac{4}{\pi}
$$