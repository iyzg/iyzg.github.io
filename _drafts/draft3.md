Testing season is finally over which (hopefully) means some more posts coming in the near future! For this month's collection, I challenge you to not give up and checked the editorial too early. These problems all took me >2 hours to solve, so keep don't feel discouraged if you're struggling to work something out.



### Problem List

- [Balanced Path](https://atcoder.jp/contests/abc147/tasks/abc147_e)
- [Bracket Sequencing](https://atcoder.jp/contests/abc167/tasks/abc167_f)
- [Handshake](https://atcoder.jp/contests/abc149/tasks/abc149_e)



## Balanced Path

<details>
<summary>Hint 1</summary>

How can you use the constraints to your advantage?

</details>

<details>
<summary>Editorial</summary>

Because the constraints are so small, you're able to do 3D dp where dp[i][j][k] is whether you can have an unbalanced score of k @ (i, j).
To fill in the dp, just iterate

</details>

<details>
<summary>My Solution</summary>

https://atcoder.jp/contests/abc147/submissions/13362463

</details>

## Bracket Sequencing

<details>
<summary>Hint 1</summary>

<details>

<details>
<summary>Editorial</summary>

I split brackets into 4 groups, sequences with only left brackets, only right brackets, both but more left, and both but more right.
Clearly sequences with only one type of bracket belong on their respective end so the question becomes how do you add the other sequences?


</details>


<details>
<summary>My Solution</summary>

https://atcoder.jp/contests/abc167/submissions/13937915

</details>

## Handshake



