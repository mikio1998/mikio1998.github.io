---
layout: post
title: How a learning app should work 
---

<h3>The Reason</h3>
For someone who wants good grades but doesn't want to spend too much time studying, I wanted a solution that could speed things up. I used flashcards, but I 
had ideas for improvement.

Terms shouldn't be memorized from A to Z start to finish, like in traditional flashcards. In traditional flashcards, the card you recite is returned back to the 
bottom of the stack, and you go through an entire rotation to study it again.

For overall faster retention, your brain should be fed the term you got wrong much earlier than waiting for the entire next rotation, 
in the initial stages of studying. If you struggle with a term, perhaps you could put insert it a few cards behind. This mechanism is what I wanted to 
turn into a new app.

<h3>Mechanism</h3>
I want to mimic a users retention progress and use it to make the flashcards challenging accordingly to their level of progress.
For this purpose, I wrote an algorithm. 

In a stack of cards, each card would hold it's own retention score. If the user knows the term on the card, the card will gain a retention point. 
If the max score is achieved, the user can dismiss the card from the stack. However, if the user cannot recall the card's term its score will be reset to zero.

Additionally, the retention level of a card will determine how far back the card will be replaced in the stack after it is swiped. 
The higher a card's level, the further back it will be placed in the stack, thus challenging the user based on their state of retetion. 

<h5>Ebbinghaus Curve</h5>
As I was interested in the Ebbinghaus [study](https://www.semanticscholar.org/paper/The-Forgetting-Curve-and-Learning-Algorithms-Hanks-Zhan/3eda1f89d845a893cd4c8848b41697d39af19195#paper-header)

I thought I could try applying the  
but within a smaller spectrum of time than in the theory, such as within the time of a flashcard study session.


