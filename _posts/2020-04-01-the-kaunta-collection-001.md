---
layout: post
title: "The Kaunta Collection - 001"
date: 2020-03-30
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
<summary>Editorial</summary>

Once you notice that you really only care the parity of each letter count, it's an easy observation to see that a string can only make a palindrome with strings that have at most one differing parity. For example, aa and b (00 and 01) could combine but not aa and bc(000 and 011). So the question becomes, how can we efficiently count the number of valid pairs? To solve this question we're going to use an interesting 1-2 punch of common tricks. The first trick is hashing our string with powers of 2 to maintain a list in number form of all letter counts that have an odd parity. Like our example above, a string of bc would be 011 which ends up being 6 in base 10. By using the power of 2, we'll be able to check the parity of each letter later using basic bitwise operations.

```c++
int key = 0;
for (int i = 0; i < 26; i++) {
    // The + 0.5 is to make sure loss precision doesn't give us an answer one too low
    if (parities[i]) key += (pow(2, i) + 0.5); 
}
```

After that, we use another common trick of using a map to count pairs of the same kind like so:

```c++
ans += map[key];
map[key]++;
```
Finally, we have to check for combinations of different strings that can create a palindrome when combined. Since we converted all the strings to a base 2 hash, we can now find all other valid key pairings by checking if they differ by one bit. After a careful check to make sure you don't double count pairings, you're all done! 

</details>

<details>
<summary>My Solution</summary>

https://codeforces.com/contest/1045/submission/67131577

</details>

## Array and Segments (Easy Version)

<details>
<summary>Hint 1</summary>

Is preserving the current maximum in the array always the best solution?

</details>

<details>
<summary>Editorial</summary>

The answer to the hint is no, and because it isn't true, there's no way to tell which element will end up being the maximum element in the correct configuration. For that reason, we have to go through each point and act as if it's the maximum and apply all segments that don't include that point and see what answer we would get.

</details>

## Bear and Blocks

<details>
<summary>Hint 1</summary>

The number of blocks in each tower isn't important; but rather, how long it takes for the tower to disappear.

</details>

<details>
<summary>Editorial</summary>

Once you see that you only care about how long it takes for each tower, this problem reduces down to simple DP on the maximum amount of turns it'll take for a stack to be destroyed. Either the tower gets destroyed from the top first or it'll get destroyed from the side. To get the answer for that, you can do a simple sweep going left to right and then right to left.

</details>

<details>
<summary>My Solution</summary>

https://codeforces.com/contest/574/submission/68096347

</details>


## Rem of Sum is Num

<details>
<summary>Hint 1</summary>

What happens to the problem if you subtract all the elements by 1?

</details>

<details>
<summary>Editorial</summary>

[Geothermal's Editorial](https://codeforces.com/blog/entry/71699) Geothermal makes amazing editorials for ABCs and Div 3s, and I felt like whatever I wrote wouldn't add too much to his editorial for ABC146. I also highly recommend joining his [CP Academy](https://discordapp.com/invite/VxVnGHu) if you're looking for a community with great mentors and other like minded students!

</details>

<details>
<summary>My Solution</summary>

https://atcoder.jp/contests/abc146/submissions/11202164

</details>

## Outro

Hope you guys found these problems interesting and learned something new! If you guys enjoyed or found this helpful, be sure to let me know through comments and share, so I can see that this is a series you guys like. See you this Sunday for the regular scheduling, cheers!







