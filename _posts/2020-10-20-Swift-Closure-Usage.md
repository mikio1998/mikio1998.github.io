---
layout: post
title: Swift Closure Usage 
---

A closure is a function packaged in a block, which can then be passed around such as be assigned to a variable.

```swift
// Simple closure assigned to variable.
let announcement = {
    print("And the winner is...")
}
announcement()
```


A closure more in depth:

```swift
// Closure structure example
let closureName: (parameter types) -> return type = {
  (parameter name: parameter type) -> return type in 
  ...
}
```

<ol>
  <li>closureName</li>
  The name of the closure which you assign as a variable.
  <li>(parameter types) -> return type</li>
  The parenthesis contain the various data types you will be inputting to your closure, same way you would to a function.
  The return type is the data type of what is returned. For instance, (String, String) -> String if you return the strings attached.
  <li>(parameter name: parameter type) -> return type</li>
  Here, the parameters are given names that can be used internally. 
  <li>in ...</li>
  Following the "in" is the closure's expression. 
</ol> 

Here's a realistic example using the structure above:
```swift
let announcement: (String, String) -> String = {
  (firstName: String, lastName:String) -> String in 
  return "And the winner is \(firstName) \(lastName)!"
}

let text = announcement("Mikio", "Nakata")
print(text)
```

Other return types:
<ul>
  <li>() -> ()</li>
  Here, the closure has no parameters. Neither does it have a return type.
  <li>() -> Void</li>
  In Swift, Void means literally nothing, not even nil type.
</ul>  

<h2>Type inference in Closures</h2>

Take a look at the following code.
```swift
let myAge = 21
// Inferred to be an integer
```
No data type is specified. However, the Swift language can infer the types of objects without the 
programmer having to imply it.
Type inference is great to know with closures. With it, you can write short but consise closures.

Here's an Example of type inference, as well as other Swift syntax uses to shorten a closure...
```swift
// We have an array of names...
let names = ["Scottie", "Dennis", "Michael"]

// Sorting an array of strings...
names.sorted(by: <)
```
In the above example, we have the sorted(by:) function, which sorts a sequence in order. <br>
The by: parameter takes a closure. See the following code for an expanded look at it.

```swift
// Now, shown below is the expanded version of the < closure.
// With type inference we can simplify it down -->

names.sorted(by: { (s1: String, s2: String) -> Bool in
    return s1 < s2
})

// -> 
// (Notice the inference)
names.sorted(by: { s1, s2 in return s1 < s2 } )

// ->

names.sorted(by: { s1, s2 in s1 < s2 } )

// ->
// Further simplification.
names.sorted(by: { $0 < $1 } )

// ->
// Trailing closure syntax

names.sorted { $0 < $1 }

// Finally, you can use < operator as a function:
names.sorted(by: <)
```

<h2>Closure Capturing</h2>
A closure can "capture" objects outside its scope. Specifically, the closure can capture objects that 
are available within the scope environment that the closure is defined in. <br>

Here is an example.
```swift
func addWealth(_ money: Int) -> Int
{
  let account = 55 // account is defined here. It shares the same scope as calculate.
  
  let calculate = {
    return account + money // account is captured from outside the closures scope.
  }
  
  return calculate()
}
```
As long as an object shares the same scope as the closure, the closure can "capture" the object and use it. 

Additional notes:
- Capturing is only one way. While a closure can capture the surrounding scope, the scope cannot extract anything from within a closure.
- Closures can capture variables, constants, and object properties. Same scope functions can be called within a closure, but they
are not captured since functions are not variables or "stored".

<h3>Strong/Weak References, Capture Lists</h3>

<p><b>What is a Strong reference?</b></p>

Check out this code:
```swift
class Person {
    let name: String?
    let age: Int?
    
    init(name: String, age: Int) {
    self.name = name
    self.age = age
    }
}
var heisenberg = Person(name: "Walter White", age: 52)
```
<p><i>A strong reference means the referenced object cannot be deallocated as long as the variable referencing it exists.</i></p>

Here, heisenberg holds a "strong" reference to the Person object. (In Swift, references are strong by default.) 
While the heisenberg variable exists, the Person object that it points to will exist too.
<br>
Opposite of strong, is weak.
A weak reference is no longer strong. It simply becomes a pointer reference to the existing object. 

<p><b>What is a strong reference cycle?</b></p>
It's when objects hold strong references mutually, and this prevents objects from being removed from memory. As they remain,
it causes <b>memory leaks</b> where there is no way to remove the excess memory usage.

<p><i>When closures capture values, they create a strong reference to that value by default.  </i></p>

<b>Capture Lists</b><br>
To break strong reference cycles, capture lists can be used.
Anything contained in the capture list is referenced as weak, or unowned. 

<b>weak or unowned?</b><br>
Both weak and unowned work are the opposite of strong, but they are slightly different from each other.

unowned is used when the closure and the captured value will always refer to each other, and will always be deallocated at the same time.
An example is [unowned self] in a view controller, where the closure will never outlive the view controller. 

weak is used if the captured value at some point becomes nil. This can happen when the closure outlives the context it was created in.
Such as, a view controller that's deallocated before a lengthy task is completed. As a result, the captured value is an optional.
<br>
You should consider reviewing capture lists when you use self in a closure.



<h2>Completion Handlers and closures</h2>
Closures are commonly applied as completion handlers.
You may be in such a situation: <br>
You are doing some lengthy networking such as getting data from your database, or executing a lengthy function. When the task is done, you want to execute some code.
<br>
For a lengthy networking task, you can provide a completion handler with a closure as such,

```swift
// Getting a document in Firestore example.
let docRef = db.collection("cities").document("SF")

docRef.getDocument { (document, error) in
    // Doing things...
}
```
You can code the completion handler at the same time you start your networking or lengthy task. <br>
The completion handler {} both starts the networking request, as well as defines the completion handler at point A. 
At point B, the networking is being processed.<br>
You can code things that are executed upon completion of your networking request. Additionally, the completion handler captures 
the closure scope at point A, so variables and constants defined within the scope can be used. <br>
As such, using a closure completion handler makes networking requests  extremely convenient. 

Imagine getting data for your UILabel:
```swift
// Firestore example again.
let titleLabel = UILabel()

let docRef = db.collection("cities").document("SF")

docRef.getDocument { (document, error) in
    if let error = error {
        print("Error getting data: \(error)")
    } else {
        titleLabel.text = document.data().field("cityName")
    }
}
```
Explaination:<br>
We define a a UILabel as titleLabel. Furthermore, we execute our networking request getDocument whilst coding 
our completion handler. In the else segment, we capture the titleLabel object and therefore have reference to it.
Like this, we can code our lengthy networking request, and code the completion handler as if they happen at the same time.



