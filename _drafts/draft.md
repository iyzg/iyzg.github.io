---
layout: post
title: "The Kaunta Collection - 001"
date: 2020-05-02
---

## Intro

Welcome to the Kaunta Collection! This is going to be a monthly series where I compile 3 - 5 of the most interesting, thought provoking problems I've found in the past month along with mini editorials I write and share them with the community. These problems are going to all be roughly around my practice range which is currently 

## Problem List

- [Palindrome Pairs](https://codeforces.com/problemset/problem/1045/I)
- [Array and Segments (Easy Version)](https://codeforces.com/contest/1108/problem/E1)
- [Bears and Blocks](https://codeforces.com/contest/574/problem/D)
- [Rem of Sum is Num](https://atcoder.jp/contests/abc146/tasks/abc146_e)

## Palindrome Pairs

<details>
    <summary>Hint 1</summary>

    The only thing that matters about each string is the letter count parity.
</details>

<details>
    <summary>Test</summary>

    ```
    this is code
    ```
</details>

<details>
    <summary>Editorial</summary>


    Once you notice that you really only care the parity of each letter count, it's an easy observation to see that a string can only make a palindrome with strings that have at most one differing parity. For example, aa and b (00 and 01) could combine but not aa and bc(000 and 011). So the question becomes, how can we efficiently count the number of valid pairs? To solve this question we're going to use an interesting 1-2 punch of common tricks. The first trick is hashing our string with powers of 2 to maintain a list in number form of all numbers that have an odd parity. (elaborate)


    ```c++
    int key = 0;
    for (int i = 0; i < 26; i++) {
        // The + 0.5 is to make sure loss precision doesn't give us an answer one too low
        if (parities[i]) key += (pow(2, i) + 0.5); 
    }
    ```


    After that, we can use a map to count pairs and count how many strings differ to get our final solution. (elaborate)
</details>



**My Solution:** [link](https://codeforces.com/contest/1045/submission/67131577)

## Array and Segments (Easy Version)

**Hint 1:** Is the preserving the current maximum in the array always the best solution?

**Editorial:** The answer to the hint is no, and because it isn't true, there's no way to tell which element will end up being the maximum element in the correct configuration. For that reason, we have to go through each point and act as if it's the maximum and apply all segments that don't include that point and see what answer we would get.

## Bear and Blocks

**Hint 1:** The number of blocks in each tower isn't important; but rather, how long it takes for the tower to disappear.

**Editorial:** Once you see that you only care about how long it takes for each tower, this problem reduces down to simple DP on the maximum amount of turns it'll take for a stack to be destroyed. Either the tower gets destroyed from the top first or it'll get destroyed from the side.

**My Solution:** [link](https://codeforces.com/contest/574/submission/68096347)

## Rem of Sum is Num

**Hint 1:** What happens to the problem if you subtract all the elements by 1?

**Editorial:** [Geothermal's Editorial](https://codeforces.com/blog/entry/71699) Geothermal makes amazing editorials for ABCs and Div 3s, and I felt like whatever I wrote wouldn't add too much to his editorial for ABC146. I also highly recommend joining his [CP Academy](https://discordapp.com/invite/VxVnGHu) if you're looking for a community with great mentors and other like minded students!

**My Solution:** [link](https://atcoder.jp/contests/abc146/submissions/11202164)

## Outro

Hope you guys found these problems interesting and learned something new! If you guys enjoyed or found this helpful, be sure to let me know through comments, so I can see that this is a series you guys like. See you this Sunday for the regular scheduling, cheers!







