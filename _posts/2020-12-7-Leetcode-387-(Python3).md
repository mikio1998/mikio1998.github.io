---
layout: post
title: Leetcode 387 (Python3)
visible: 1
---
<h2>Prompt:</h2>
Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.


```python
s = "leetcode"
return 0.

s = "loveleetcode"
return 2.
```


<h3>Solution</h3>

```python
def firstUniqChar(s: str):
    count = {}
    for index in range(len(s)):
        current_char = s[index]
        if current_char not in count:
            count[s[index]] = (1, index)
        else:
            count[s[index]] = (count[s[index]][0] + 1, index)
    for character, occurrence_counter in count.items():
        if occurrence_counter[0] == 1:
            return occurrence_counter[1]
    return -1

# Test Case
def test(actual, expected):
    if actual == expected:
        print("SUCCESS")
    else:
        print("FAILURE")
        print("Actual", actual)
        print("Expected", expected)

test(firstUniqChar("leetcode"), 0) # SUCCESS
test(firstUniqChar("loveleetcode"), 2) # SUCCESS
test(firstUniqChar(""), -1) # SUCCESS
```

<h2>Explained</h2>

<ol> 
<li>Builds a dictionary by iteratinng through given string. Hashes the occurrence as well as index position.</li>
<li>Iterates through dictionary and returns first hit of unique character, where occurrence value is 1.</li>
</ol>

<ul> <h3>Other points:</h3>
<li> Dictionary is ordered in added order. The first hit is the earliest occurrence and can be returned as the solution, as stated in 2.</li>
<li> Corner case of empty string <code>""</code> returns -1.</li>
</ul>

<ul> <h3>Topics:</h3>
<li>Linear Search</li>
<li>Hash map (python dict)</li>
</ul>







