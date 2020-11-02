---
layout: post
title: App Became Smoother After Changes
---

Currently, I've finished my rework up to the point the app is ready to smoothly take some data. Designing and coding took about 4-5 work days.

<h3>Notes:</h3>

<ol>
  <li>Significant reduction of coding.</li>
  <li>Pre-networking data is beneficial.</li>
  <li>Need to improve skills with UI constraints</li>
  <li>More realistic plans, new ideas.</li>
</ol> 


1.It's running on much less code.
The new code is much more efficient and legible. It's mostly because I'm more skilled than before, and I'm also using a design pattern for organization.

2.I pre-network the data, and overall it reduces the number of reads.
In the previous version of the app, networking occured in so many instances; swiping collections, entering and exiting pages, etc. 
In this version, I fetched the data during the launch screen. Here is a look at how smooth the collection View has become:

(Old version)
<video width="320" height="240" controls>
  <source type="video/mp4" src="https://mikio1998.github.io/images/11_2_2020//Collection_Recording_1.mp4">
</video>

(New version, no more blank spaces)
<video width="320" height="240" controls>
  <source type="video/mp4" src="https://mikio1998.github.io/images/11_2_2020//Collection_Recording_2.mp4">
</video>

3.Setting constraints is confusing
I spent a lot of time struggling with constraints, so I'll study it in the future.

4.New plans
While barcoding/QRcoding would make my app a great solution for the workspace, it would be really difficult to implement (non-code issues) so realistically, I
would work on it last. Instead, I might plan solutions for Warehouse operations since recently I find work there a pain in the ass (make real-time replenishment map or something).
