---
layout: post
title: "The Kaunta Collection - 002"
description: The second collection of quality problems from CodeForces and AtCoder that help teach you common motifs within competitive programming.
date: 2020-05-01
permalink: the-kaunta-collection-002
---

## Intro

Welcome to the second installment of the Kaunta Collection! If you're new to the series, the Kaunta Collection is a monthly compilation of some of my favorite problems I've solved in the past month alongside my own editorials for each problem. So strap on your seat belts, and let's get this show on the road.

## Problem List

- [Ehab The Exorcist](https://codeforces.com/contest/1325/problem/D)
- [Flatten](https://atcoder.jp/contests/abc152/tasks/abc152_e)
- [Multiple of 2019](https://atcoder.jp/contests/abc164/tasks/abc164_d)

## Ehab The Exorcist

### Hint 1

What's the upper bound on the number of elements you need in the array, and when would the input be invalid?

### Editorial

First off, let's determine when the base case for when the input is invalid. If U > V, it's invalid because to get a xor of U, the sum must 
be at least equal to U. There is one other special case for when U = V that you only need 1 number to satisfy both conditions. 

To answer the question I posed in Hint 1, the upper bound on the number of elements needed to satisfy the conditions is always 3. You can always have an array with 
[U, (V - U) / 2, (V - U) / 2] to meet both conditions, **UNLESS** V and U are differing parities; in which case, it's impossible. Now the challenge
is to see how we could optimize this to pass tests like Sample Case 1 where you only need 2 elements. Since xor essentially acts as addition if the 
two numbers share no common bits, you can combine U and one (V - U) / 2 into one element to keep the same sum and use the second (V - U) / 2 to return the 
xor to U.

[Solution](https://codeforces.com/contest/1325/submission/75616773)

## Flatten

### Hint 1

Since the LCM is too large to store in a long long, store it as an array.

### Editorial

The LCM is way too large to be stored in any form of integer, so we can instead store it as an array of its prime factors.
You can then recreate the LCM % 1e9 + 7 by going through each factor with:

```c++
// Factor, number of times it occurs
map<ll, ll> factorCnt;
LCM = 1;
for (auto& i : factorCnt) {
    LCM *= modular_exponentiation(i.f, i.s);
    LCM % MOD;
}
```

Since you're looking for the sum of each `LCM / a[i]`, you can modular inverse each element to convert it to 1/a[i] % MOD then multiply
by LCM to get the final answer.

[Solution](https://atcoder.jp/contests/abc152/submissions/11765236)

## Multiple of 2019

### Hint 1

Try representing the number by each digit.

### Editorial

The first thing you want to do is reverse the string which makes it so your number is now `S[0]*10^0+S[1]*10^1` and so on.
Now we can take prefix sums:

```c++
ps[0] = S[0]*10^0 % 2019;
ps[1] = S[0]*10^0 + S[1]*10^1 % 2019;
// Etc...
```

The mod for the prefix sum is 2019 because you care about the remainder each number has when divided by 2019. Now consider what
happens when you do `ps[r] - ps[l - 1]`.

```c++
ps[r] = S[0] * 10^0 + S[1] * 10^1 ... + S[r] * 10^r;
ps[l - 1] = S[0] * 10^0 + S[1] * 10^1 ... + S[l - 1] * 10^(l - 1);
ps[r] - ps[l - 1] = S[l] * 10^l + S[l + 1] * 10^(l + 1) ... + S[r] * 10^r;
// You can conveniently factor out a 10^l to get 
ps[r] - ps[l - 1] = 10^l * (S[l] * 10^0 + S[l + 1] * 10^1 ... + S[r] * 10^(r - l));

```

Since 10 has no common factors with 2019, `ps[r] - ps[l - 1]` is a multiple of 2019 iff (if and only if) 
`(S[l] * 10^0 + S[l + 1] * 10^1 ... + S[r] * 10^(r - l)` is a multiple of 2019. Since the prefix sum is the prefix % 2019, 
you're essentially looking for `ps[r] - ps[l - 1] = 0` so the remainders cancel out. This is equal to `ps[r] = ps[l - 1]` where
you're simply counting for pairs again, so you can use the same map trick found in the Palindrome Pairs problem from 
[Kaunta Collection 001](https://kauntaofficial.github.io/2020/04/01/the-kaunta-collection-001.html).

(Thanks to summitwei for helping me solve this problem <3)

[Solution](https://atcoder.jp/contests/abc164/submissions/12497180)


## Outro

Thanks for reading! I hope you guys enjoy the problems, and if you find anything wrong or need help with a problem, don't hesitate to ask 
in the comments below. I have some exciting things in the works that will be coming to fruition soon so keep your eyes peeled, but until next 
time, Kaunta out.
