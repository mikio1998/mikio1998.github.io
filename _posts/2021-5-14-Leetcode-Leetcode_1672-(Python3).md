---
layout: post
title: Leetcode 1672 (Python3)
visible: 1
---
<h2>Prompt:</h2>
Given the array candies and the integer extraCandies, where candies[i] represents the number of candies that the ith kid has.

For each kid check if there is a way to distribute extraCandies among the kids such that he or she can have the greatest number of candies among them. Notice that multiple kids can have the greatest number of candies.


```python
Input: candies = [2,3,5,1,3], extraCandies = 3
Output: [true,true,true,false,true] 

Input: candies = [4,2,1,1,2], extraCandies = 1
Output: [true,false,false,false,false] 

Input: candies = [12,1,12], extraCandies = 10
Output: [true,false,true]
```


<h3>Minimum solution</h3>
```python
def kidsWithCandiesA(candies: [int], extraCandies: int):
    possible_distribution = []
    for kid in candies:
        if kid+extraCandies >= max(candies):
            possible_distribution.append(True)
            continue
        possible_distribution.append(False)
    return possible_distribution
```

<h3>List Comprehension and built-in functions</h3>
```python
def kidsWithCandiesB(candies: [int], extraCandies: int):
    return [True if kid + extraCandies >= max(candies) else False for kid in candies]

# Test Case
def test(actual, expected):
    if actual == expected:
        print("SUCCESS")
    else:
        print("FAILURE")
        print("Actual", actual)
        print("Expected", expected)

test(kidsWithCandiesB([2,3,5,1,3], 3), [True, True, True, False, True]) #SUCCESS
test(kidsWithCandiesB([4,2,1,1,2], 1), [True, False, False, False, False]) #SUCCESS
test(kidsWithCandiesB([12,1,12], 10), [True, False, True]) #SUCCESS
```

