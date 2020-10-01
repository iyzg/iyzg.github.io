How To Take Advantage of Constraints

When I was just starting out in competitive programming, understanding how to utilize constraints seemed like some arcane topic only high rated people could understand. To me, constraints were only there to ensure I couldn't brute force everything. If you feel like this is an accurate description of where you're at, hopefully today's post helps you get a better grasp of constraints through two illustrative examples. I'm going to be using the socratic message to pose questions, answer before reading on!

# The Process

It's honestly as simple as it gets. Write down the bounds of the constraints, (ex. $ 0 \le n \le 10^5 $) then note what the worst runtime you could have is. For reference, a general mark for C++ is about 4*10^9 operations per second. This is a general guide for people from 1200-1800 CodeForces so we won't delve into optimizing constants here, just keep it simple and have some general note like I need something faster than O(n^3) is good enough.

## Will This Slow Me Down?

Yes.

When you first start out doing this, it's going to feel cumbersome and completely unworthy of the time spent. But 
You might be thinking that this is too slow and convoluted for a format that has speed at its crux, and you aren't wrong. Doing this **is** slow. But what you invest in the upfront pays dividends when it helps you solve the problem afterwards. And after doing this for a while, the process becomes so subconscious that it doesn't slow you down much at all.

## Level 1

Problem: []()

This problem is naturally intimidating. How do we even start to tackle this? Well, like any good boy, let's take a look at the constraints. We quickly notice that N is bounded <= 500 which means that not only could we get away with n^2, we could even get away with n^3! Once you see that a pure brute force is fast enough, the rest is simple. This is a great example of how some problems are deceptively scary, it just takes turning on the constraint light to realize they're actually not scary whatsoever. Sometimes you'll get these sorts of problems on graphs or commonly where you can try every permutation where a common trick is to do

```c++
for (int i = 0; i < (1 << n); ++i) {
    for (int j = 0; j < n; ++j) {
        if ((1 << j) && i) {
            // Include the j'th element in the current permutation.
        }
    }
    // Calculate the sum, product, or whatever of this permutation.
}

```


# Level 2

Problem: [Expected Damage](https://codeforces.com/problemset/problem/1418/E)

> What can't you do under these constraints?

We have two variables that are important for runtime here, $ n $ and $ m $. Both of these could go up to $ 2*10^5 $ which means the product of $ 4*10^10 $ is far too large to have an $ O(n^2) $ runtime pass under time limit. This means we **could** use any of prefix sums, segment trees, fenwick trees, binary search, etc. to either precompute or reduce one of the n's to logn. I don't want to spoil the rest of the problem, but you can see how just by analyzing the constraints, we're able to quickly establish a set of tools we could use to solve this problem and direct our thinking.

This problem also shows off a trick I apply to my thinking which is treating it like there are subtasks. You start at the caveman level brute force and slowly work out how to optimize it. The one caveat is where a brute force greedy won't work and you might need to use DP; but again, analyzing the constraints show you whether dp is even an option or not.

# Outro

This isn't some clickbait youtube video, I won't claim using this process to start problems will make you gain 200 rating points. I can't even guarantee you'll get any rating out of this at first, you might lose rating because this slows you down and forces you to think about things you haven't thought about before. But while I can't promise some overnight success, I can guarantee that in the long term, this kind of thinking will help you solve problems faster and more accurately. Well guess it's time for runtime... get it? Time for me to run... ok that was terrible. Best of luck and until next time, Ivy out.