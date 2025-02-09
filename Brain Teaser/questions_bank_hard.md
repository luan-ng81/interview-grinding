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
