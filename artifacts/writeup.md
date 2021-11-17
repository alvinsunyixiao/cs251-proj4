Name: [Alvin Sun]

## Question 1

In the following code-snippet from `Num2Bits`, it looks like `sum_of_bits`
might be a sum of products of signals, making the subsequent constraint not
rank-1. Explain why `sum_of_bits` is actually a _linear combination_ of
signals.

```
        sum_of_bits += (2 ** i) * bits[i];
```

## Answer 1

Since `b` is known at compile time, the loop can be unrolled with 
pre-calculated `2 ** i` as compile time constants. Treating the `2 ** i` as constants weights, `sum_of_bits` is just a weighted linear combination of 
the `bits` signal array.

## Question 2

Explain, in your own words, the meaning of the `<==` operator.

## Answer 2

The `<==` operator is an operator combining assigment (`<--`) and constraint
`===`. Not only does it assign the logic between input and output signals,
it also generate constraints that verify the correctness of the desired logic.

## Question 3

Suppose you're reading a `circom` program and you see the following:

```
    signal input a;
    signal input b;
    signal input c;
    (a & 1) * b === c;
```

Explain why this is invalid.

## Answer 3

This is invalid because constraints are applied on a non-quadratic expression 
(`a & 1`:is the non-quadratic term in this expression).
