---
layout: post
title: The Kaunta Collection 003
description: How to develop intuition in competitive programming through deliberate practice.
date: 2020-07-23
permalink: the-kaunta-collection-003
---

TODO: Rewrite all solutions to be clearer and have more comments explaining each
section

Welcome to the Kaunta Collection! If you're new to the series, the Kaunta
Collection is a monthly compilation of the most interesting problems I've solved
within that timeframe along with hints and my own editorial for each. (TODO:
Maybe leave thing here about sharing if they like instead of at the bottom).

## Problem List

- [Reading Books (Hard Version)](https://codeforces.com/contest/1374/problem/E2)
- [Ordinary  Beauty](https://atcoder.jp/contests/soundhound2018-summer-qual/tasks/soundhound2018_summer_qual_c)
- [GCD Sequence](https://atcoder.jp/contests/agc022/tasks/agc022_b)

## Reading Books (Hard Version)

### Hint 1
God knows

### Editorial

Note: My solution uses policy-based data structures, you can find an alternative
without [here](https://codeforces.com/blog/entry/79517).

Let's classify books into 4 categories: ($$A$$) Alice likes, ($$B$$) Bob likes,
($$C$$) both like, and ($$D$$) neither likes. If $$A + C < k$$, $$A + D < k$$,
or the minimum number of books required to satisfy $$k$$ for both Alice and Bob
is greater than $$m$$, it's impossible. To find the best combination of books,
we'll loop through the number of books taken from C starting with the maximum
possible and maintain an ordered multiset of the books not taken along with the
sum for both groups. Each time we decrement C, we'll increase the required sum
by the next two smallest books in A and B while subtracting C[ci]? Make this
bsetter. Using our ordered set, we're able to quickly check if either of the
AB books taken were already and simulate removing them and calculating the new
sum. There's a few cases we have to be careful of here:

- If both books were already being taken, add the (extraTaken - 1)th book to
  satisfy the m condition once more
- If the next smallest books in A & B are the same number, you have to add 1 to
  the index of b to make sure it was actually being taken beforehand.
- If the book we're removing from C is within the first extraTaken books, add
  that to the sum and remove the (extraTaken - 1)th book
(Go into greater depth)

Now that you have the optimal C, you can just greedily take to satisfy the k and
m constraints for the optimal answer.

## Solution

[My Solution](https://codeforces.com/contest/1374/submission/85556592)

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
