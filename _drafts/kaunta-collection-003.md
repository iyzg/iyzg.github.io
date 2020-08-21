--
layout: post
title: The Kaunta Collection 003
description: How to develop intuition in competitive programming through deliberate practice.
date: 2020-07-23
permalink: the-kaunta-collection-003
---

Welcome to the Kaunta Collection! If you're new to the series, the Kaunta
Collection is a monthly compilation of the most interesting problems I've solved
within that timeframe along with hints and my own editorial for each. 

## Problem List

- [Knapsack for All Subsets](https://atcoder.jp/contests/abc169/tasks/abc169_f)
- [Ordinary  Beauty](https://atcoder.jp/contests/soundhound2018-summer-qual/tasks/soundhound2018_summer_qual_c)
- [GCD Sequence](https://atcoder.jp/contests/agc022/tasks/agc022_b)

## Knapsack for All Subsets

### Hint 1

How much does a valid subset with length k contribute to the answer, what about
a subset with k + 1?

### Editorial

Using the knowledge that each subset contributes 2^(n - k) to the answer, we
could store a 2d map of sum and size, but this runs in $ O(n^3) $ which is
clearly too slow. We can't get rid of looping through all elements or the sum,
so we'll have to find a way to get rid of size.
Let's start with the naive version where we have a 3d $ dp[index][sum][size] $
and fill it accordingly. Clearly $ O(n^3) $ will timeout, so we need to find a
way to get rid of one of the dimensions. Index and sum are nonnegotiable, so we
need to find a way to get rid of size. Each time you extend the length of a
sequence, the contribution goes from 2^(n - k) to 2^(n - (k + 1)), which is / 2.

### Solution

[My Solution](https://atcoder.jp/contests/abc169/submissions/16012612)

## Ordinary Beauty

### Hint 1
Linearity of Expectation

### Editorial

Since you're concereed with the difference betewen two indecies, we'll just
consider the m - 1 pairs of adjacent pairs. Although the probabilities are
dependent on adjacent pairs, linearity of expecatation states that the sum of
two expected values, even if they're dependent of each other, are just the sum:


$$ E[x]+ E[y] = E[x + y]$$

This means that the answer will be the probability a pair will be beautiful
multiplied by m - 1, so we'll just find the 2 different cases:

1. When $ d = 0 $, the only valid pairs of (a, b) are when $ a = b $, so the
probability is $$ \frac{n}{n^2} $$.
2. When $ d \ne 0 $, the number of valid pairs is $2(n - d)$, as all $ a \le (n - d) $ 
can pair upwards and all $ a \ge (d + 1) $ can pair downwards.

### Solution

[My Solution](https://atcoder.jp/contests/soundhound2018-summer-qual/submissions/14477424)

## GCD Sequence

### Hint 1
What's the smallest possible triple?

### Editorial

The first important idea to simplify this problem is that instead of
considering the GCD of $ a_i $ and the sum of all other elements, we can instead
consider $ GCD(S, a_i) $ since 

$$ GCD(S, a_i) = GCD(s - ai, ai) $$

With such tight constraints on our options, it makes sense to take both 2 and 3
since they ensure the overall GCD is 1 while also providing small factors for
the other elements to satisfy. The [official
editorial](https://img.atcoder.jp/agc022/editorial.pdf) uses a solution with
just multiples of 2 & 3, but I'll introduce a different approach here.  With our
set {2, 3}, the smallest number to complete the triple is 25. Now the smallest
factors we need in all elements are any of {2, 3, 5} while maintaining a sum
which is a multiple of $ 2 * 3 * 5 = 30 $. A simple way to do this is by adding
pairs which sum to 30,000 and both numbers have one of the valid factors. If N
is even, we can fill out the array by adding 15,000.

### Solution
[My Solution](https://atcoder.jp/contests/agc022/submissions/15494432)
