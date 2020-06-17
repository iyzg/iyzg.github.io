---
layout: post
title: "Lecture 001 - Z-Algorithm"
description: None.
date: 2020-06-14
permalink: lecture-001-z-algorithm
---

## Preface

These "lectures" are mostly to help myself understand concepts in depth since
the best way to learn something is to teach it to others. To try and make these
concepts as intuitive as possible, I've taught this to multiple people
beforehand to refine my explanations. Hope you enjoy.

## What is Z-Algorithm?  

Z-Algorithm takes a string $$s$$ of length $$n$$ and returns an array where each
$$z[i]$$ is the length of the longest common prefix between $$s$$ and the suffix
starting at $$i$$.

$$z[0]$$ isn't well defined, but it doesn't change the implementation or outcome
so we'll just set it to 0.

## Examples
### TODO: Change the examples to something other than the cp-algo ones

- aaaaa -> [0, 4, 3, 2, 1]
- aabaab -> [0, 2, 1, 0, 2, 1, 0]
- abacaba -> [0, 0, 1, 0, 3, 0, 1]


## Trivial Algo

This is the simple $$O(n^2)$$ implementation which acts as the basis for the
eventual $$O(n)$$ algorithm.

```c++
vector<int> z_algo(string s) {
    int n = (int)s.length();
    vector<int> z(n);
    for (int i = 1; i < n; i++) {
        while (i + z[i] < n && s[z[i]] == s[i + z[i]]) 
            ++z[i];
    return z;
}

```

Going through each index $$i$$, continue incrementing $$z[i]$$ until the two
characters don't match or you go past the end of the string.

## Efficient Algo

To reduce the runtime, we'll want to keep track of previous computed values
instead of running the trivial algorithm each time. To do this, we'll keep $$[l,
r]$$ indecies of the rightmost segment. This acts as a "boundary" for what we've
scanned so far.

Next, we have to deal with two cases: when $$i > r$$, and when $$i <= r$$.

When $$i > r$$, we resort back to the trivial agorithm since we can't tell if
the letters pass the boundary continue to match.

When $$i <= r$$, we'll use our stored right segment to speed up the
calculations. Since the rightmost segment we've stored $$s[l, r]$$ and 
$$s[0, r - l]$$ match, we know that $$s[i]$$ is the same letter as $$s[i - l]$$.
We've already calculated the score for $$i - l$$ so we can initialize $$z[i]$$
to $$z[i - l]$$.

One precaution to take when doing this is that the length may extend past r
which isn't allowed because there isn't any information on the letters past r
yet. 

An example of the scenario:

$$
s = "aaaabaa"
$$

Once we reach $$i = 6$$, the current segment is $$[5, 6]$$ which means $$i = 6$$
is equivalent to $$i = 1$$ which has a value of 3. We can't initialize $$z[i] =
3$$ because it extends past $$r$$.  To safeguard against this, you can instead
set $$z[i]$$ to:

$$
z[i] = min(r - i + 1, z[i - 1])
$$


### Implementation

```c++
vector<int> z_algo(string s) {
    int n = (int)s.length();
    vector<int> z(n);
    for (int i = 1, l = 0, r = 0; i < n; ++i) {
        if (i <= r)
            z[i] = min(r - i + 1, z[i - l]);
        while (i + z[i] < n && s[z[i]] == s[i + z[i]])
            ++z[i];
        if (i + z[i] - 1 > r)
            l = i, r = i + z[i] - 1;
    }
    return z;
}
```

When the current index is within the bounds of the rightmost segment, we can
use our previous computations to go as far as we possibly can. If we go past the
right boundary, we resort back to the trivial algorithm to check each character
and then update the rightmost segment as needed.

### Runtime

The for loop clearly runs in $$O(n)$$ time and besides the inner while loop, all
other operations run in constant time.

For the while loop to run, it means that the current segment goes beyond the
current boundary. This can only happen a max of (n

## Applications


## Problems
- [Who Says a Pun?](https://atcoder.jp/contests/abc141/tasks/abc141_e)
- [Password](https://codeforces.com/problemset/problem/126/B)

## Sources
- [CP-Algorithms](https://cp-algorithms.com/string/z-function.html)

## Special Thanks (Unfortunate Test Subjects)

