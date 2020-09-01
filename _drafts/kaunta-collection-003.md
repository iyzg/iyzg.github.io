---
layout: post
title: The Kaunta Collection 003
description: A collection of interesting competitive programming problems and methods to tackle them.
date: 2020-09-01
permalink: the-kaunta-collection-003
---

Welcome to the Kaunta Collection, a collection of interesting problems with hints and editorials written by yours truly!  For the 3rd installment, I've pivoted a bit from just providing a hint and editorial to try and explain my thinking process for each problem as well. Hope you enjoy!

## Problem List

- [Knapsack for All Subsets](https://atcoder.jp/contests/abc169/tasks/abc169_f){: target="_blank" }
- [Ordinary  Beauty](https://atcoder.jp/contests/soundhound2018-summer-qual/tasks/soundhound2018_summer_qual_c){: target="_blank" }
- [GCD Sequence](https://atcoder.jp/contests/agc022/tasks/agc022_b){: target="_blank" }

## Knapsack for All Subsets

### Hint 1

How much does a valid subset with length k contribute to the answer, what about a subset with k + 1?

### Editorial

With $ 2^n $ subsets, it's clearly too large to consider every subset individually, but we can instead consider only valid subsets which sum to S and how much they contribute. Let's call our valid subset of length K, $ A $. To find its contribution, we have to count how many subsets $ B $ meet the condition $ A \in B $. Since B must contain A, there are $ n - k $ extra elements which we could either take or not take for a total of $ 2^{(n - k)} $ subsets which include subset $ A $. 

A naive solution could use a 2d array for [subset sum][subset size] and update it while iterating through the array.  Unfortunately, this has a runtime of $O(n^3) $ which is far too slow.

Iterating through the array and the sum of a subset are nonnegotiable, so we have to get rid of the [subset size] dimension. Luckily for us, going from a subset of length $ k $ to length $ k + 1 $, the contribution of the subset goes from $ 2^{(n - k)} $ to $ 2^{(n - (k + 1))} $ or simply put - you divide by 2, no matter what k is. This observation allows us to get rid of the size dimension since the transition between sums would simply be $ S[i + a_j] += S[i]/ 2 $.  Now with a runtime of $ O(n^2) $, the solution runs well under TL.

[My Solution](https://atcoder.jp/contests/abc169/submissions/16012612){: target="_blank" }

## Ordinary Beauty

### Hint 1

Linearity of Expectation

### Editorial

Since beauty is determined by pairs of adjacent indices, let's just focus on the $ m - 1 $ adjacent pairs. Although the probability that a pair is beautiful is dependent on adjacent pairs, linearity of expectation states that the sum of two expected values, even if dependent on each other, is simply the sum:

$$ E[x]+ E[y] = E[x + y] $$

This means that the answer will be the probability a pair will be beautiful multiplied by $ m - 1 $, so we'll just find the 2 different cases of what the beauty could be:

1. When $ d = 0 $, the only valid pairs of (a, b) are when $ a = b $, so the probability is $$ \frac{n}{n^2} $$.
2. When $ d \ne 0 $, the number of valid pairs is $2(n - d)$, as all $ a \le (n - d) $  can pair upwards, and all $ a \ge (d + 1) $ can pair downwards. This gives us a probability of 
$$ \frac{2(n - d)}{n^2} $$

[My Solution](https://atcoder.jp/contests/soundhound2018-summer-qual/submissions/14477424){: target="_blank" }

## GCD Sequence

### Hint 1

What's the smallest possible triple?

### Editorial

The first important idea to simplify this problem is that instead of considering the GCD of $ a_i $ and the sum of all other elements $ (S) $, we can instead consider $ GCD(S, a_i) $ since 

$$ GCD(S, a_i) = GCD(S - a_i, a_i) $$

With such tight constraints, it makes sense to take both 2 and 3 since they ensure the overall GCD is 1 while also providing small factors for the other elements to satisfy. From here there are two main paths you could take:

1. Only take multiples of 2 & 3, which you can find an explanation for [here in the official editorial.](https://img.atcoder.jp/agc022/editorial.pdf){: target="_blank" }
2. Find the smallest number to complete the triple, which is the approach I explain here.

With our set {2, 3}, the smallest number to complete the triple is 25. Now the smallest factors we need in all elements are any of {2, 3, 5} while maintaining a sum which is a multiple of 
$ 2 * 3 * 5 = 30 $. A simple implementation is adding pairs which sum to 30,000 where both numbers have one of the required factors. The initial triple and added pairs satisfies all odd N, and adding any unused multiple of 30 satisfies all even N.

[My Solution](https://atcoder.jp/contests/agc022/submissions/15494432){: target="_blank" }
