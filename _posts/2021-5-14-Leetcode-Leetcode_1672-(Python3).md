---
layout: post
title: Leetcode 1672 (Python3)
---
<h2>Prompt:</h2>
You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the i'th customer has in the j'th bank. Return the wealth that the richest customer has.

A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.


```python
Input: accounts = [[1,2,3],[3,2,1]]
Output: 6

Input: accounts = [[1,5],[7,3],[3,5]]
Output: 10
```


<h3>Bare Minimum solution</h3>
```python
def maximumWealth(accounts) -> int:
        # loop accounts
            # sum of array, add to new array
        # find the largest value in the array, return the index.
        
        net_worths = []
        sum = 0
        for account in accounts: 
            for bank in account:
                sum = sum + bank
            print(sum)
            net_worths.append(sum)
            sum = 0
            
        largest_wealth = 0
        for net_worth in net_worths:
            if net_worth > largest_wealth:
                largest_wealth = net_worth
            continue
            
        return largest_wealth

# Test Case
def test(actual, expected):
    if actual == expected:
        print("SUCCESS")
    else:
        print("FAILURE") 
        print("Expected", expected)  

test(maximumWealth([[1,2,3],[3,2,1]]), 6)
test(maximumWealth([[1,5],[7,3],[3,5]]), 10)
test(maximumWealth([[2,8,7],[7,1,3],[1,9,5]]), 17)
```

<h3>List Comprehension & built-in functions</h3>
```python
def maximumWealth(accounts) -> int:
  return max([sum(account) for account in accounts])
```

