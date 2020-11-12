---
layout: post
title: Classes & Structs
---

<h2>Distinguishing Between Classes and Structs</h2>

However similar Classes and Structs are, they have slight but important differences.
It's important to know the difference to understand which to use.  

<h3>Commonalities of Class and Struct</h3>
<ul> 
<li> They can define properties to store values, and they can define functions. </li>
<li> They can define initializers to set their initial state. <code">init()</code> </li>
<li> They can be extended, with <code">extension</code> </li>
<li> They can conform to protocols. </li>
</ul>

<h3>Class has these additional features:</h3>
<ul> 
<li> Class can inherit from a parent class. </li>
<li> Classes can be deinitialized, i.e. you can call a function before the class is destroyed.? </li>
<li> Classes are reference types, while Structs are value types. </li>
</ul>


<h2>Reference types and value types</h2>

<h3>Value type:</h3>
When a value type is copied (ie, if it gets assigned, initialized, or passed into a function), each instance holds a unique copy of the data.
Meaning, even if one instance of the data is changed, it does not affect any other existing instance.

<h3>Reference type:</h3>
When a reference type is copied, each instance shares the data. 
Meaning, if one instance of the data is changed, the change will be inflicted on all other instances.

<h2><b>Value or Reference</b> - Examples:</h2>
Imagine you are a shop clerk, and you must report to your boss what you sell every day....

<h3>Value Type senario:</h3>
You write the products you sold on a piece of paper. Around closing hour, you send a copy of the paper to your boss. 
However, just as you send it a customer comes in and buys a product. Although you make a new sales entry, your boss will still have the old data.

<h3>Reference Type senario:</h3>
The business has a centralized cloud-based database, and you use a software to make sales records. 
Your boss uses the same software, and keeps track of the changes you record. Therefore if you change the data, it changes for your boss as well.

If you copy a class, you'll have two references to one instance of the data. 
If you copy a struct, you'll have two instances, each with unique copies of the data.

<h2>When to use which?</h3>
Generally, structs should be used over classes by default, unless you need the additional capabilties (mentioned earlier) the class provides.

<h3>Reading:</h3>
https://learnappmaking.com/struct-vs-class-swift-how-to/#:~:text=In%20Swift%2C%20structs%20are%20value,choice%20between%20classes%20or%20structs.
