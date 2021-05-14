---
layout: post
title: Making Old App Perform Better
visible: 1
---

Currently, I've finished my rework up to the point the app is ready to smoothly take some data. 

<h3>Notes:</h3>

<ol>
  <li>Significant reduction of coding.</li>
  <li>Pre-networking data is beneficial.</li>
  <li>Need to improve skills with UI constraints</li>
  <li>More realistic plans for the project, new ideas.</li>
</ol> 


Point #1: <i>It's running on much less code.</i><br />
The new code is much more efficient, legible, and disciplined. Ever since the first time I made this app, I have implemented new skills such as using a design pattern for organization.

Point #2: <i>I pre-network the data, and overall it reduces the number of reads.</i><br />
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

Point #3: <i>Setting constraints is... difficult.</i><br />
I spent a lot of time struggling with constraints, which I'm inclined to study in the future.

Point #4 <i>New plans:</i><br />
While I believe the barcoding/QRcoding feature would make my app a great solution for the workspace, <b>I've recently been exposed to how difficult it actually is to implement due to real-world issues.</b> The main culprit issue is the inconsistency of the barcodes provided by the manufacturors, which often contain errors or have various codes for the same product. While it's unfortunate, I might plan other new solutions in the future.
