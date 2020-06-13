# KL 001 - Z-Algorithm

## What is it?
Z-Algorithm is algorithm that determines the longest common prefix between a string and the 
substring starting at index i in O(n) time.

z[0] isn't well defined, but it also doesn't matter so we'll just set it as 0

## Examples
# TODO: Change the examples to something other than the cp-algo ones
aaaaa -> [0, 4, 3, 2, 1]
aabaab -> [0, 2, 1, 0, 2, 1, 0]
abacaba -> [0, 0, 1, 0, 3, 0, 1]

# TODO: Get mathjax and make it look good with mathematical notation
## O(n^2)
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






## Problems


