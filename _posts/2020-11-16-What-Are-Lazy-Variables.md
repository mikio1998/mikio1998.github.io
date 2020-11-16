---
layout: post
title: What Are Lazy Variables
---

Variables can be <code>lazy</code> to save processing time of your running code. A lazy variable is created only when it is called upon. 

<h2>Example</h2>
Here is a struct called Person, that has an <code>age</code> variable, as well as a <code>fibonacciOfAge</code> variable. Also, <code>Person()</code> has a function that calculates
the fibonacci of a given integer. The function uses recursion, and it gets exponentially complex the higher the input. 

```swift
struct Person {
    var age = 16
    
    lazy var fibonacciOfAge: Int = {
        return fibonacci(of: self.age)
    }()

    func fibonacci(of num: Int) -> Int {
        if num < 2 {
            return num
        } else {
            return fibonacci(of: num - 1) + fibonacci(of: num - 2)
        }
    }
}
```

In this situation, making fibonacciOfAge a lazy variable could save a tremendous amount of processing time, if you don't need the fibonnacci age to be computed by default. 
By making it lazy, fibonacciOfAge will only be computed when it gets called. Imagine if you create 100 instances of <code>Person()</code>, then you would definitely
need to use lazy.

<h3>Notes about the example code</h3>
<ul>
<li>You must declare the variable's data type (<code>Int</code> in the example).</li>
<li>Must use <code>.self</code> inside the function. If using class instead of struct, use <code>[unowned self]</code> to avoid strong reference cycle.</li>
<li>Lazy property must end with parenthesis (You are making a call to the function you just created.)</li>
<li>There is no <code>lazy let</code>, only variables.</li>
</ul>





