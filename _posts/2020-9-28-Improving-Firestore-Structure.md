---
layout: post
title: Improving Firestore Structure
---

The clothing store app I made was one of my first Swift projects, and I have improved my skills since then. While I am proud of it, I am planning to rework the 
app with better coding and architectural principles. First, I plan to rework the database.


<div align="center">
<img src="{{ site.baseurl }}/images/Old_firestore.png" alt="OldFirestore" width="600" height="408"/>
<h5>My old database is a long list to get through</h5>
</div>


Something new is that I am exploring the possibility of printing my own barcodes/qrcodes to stick to the products. Without considering my concern about the 
amount of hands-on labor this might take, I think it would make cash-registers much quicker and easier than before. 

<h2>Drafting the new Database (json/firebase format)</h2>

My original firebase would have one collection containing every existing product. This, is a very long list. To start, I wanted to divide products by
brands. After some consideration, I am ultimately planning to proceed with this structure:

- Brand:  Houston
    - Name:   MA1
        - Price:      18800
        - Color:     [OD, Black, Navy]
        - Size:       [S, M, L, XL]

I favor having sizes and colors in arrays. This would also work with a qr/bar code schema because I plan on making my own, which gives me a lot of freedom 
(because I don't have to make a document for every size-color variant, which eliminates a huge amount of necessary space). 
The codes would probablylook like this:

18800-hou-ma1-od-s

The structure here is price-brand-product-colorway-size. I plan on using dictionaries to deal with shortened abbreviations for brand names. 

Making the orginal database took about 3-4 days of work of planning, data collection, 
and data entry (so many documents I had to write a script that writes data entries). I'm relieved that half of it is already done.
