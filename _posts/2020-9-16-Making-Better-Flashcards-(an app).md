---
layout: post
title: Making Better Flashcards (an app)  
visible: 0
---

<div align="center">
<img src="{{ site.baseurl }}/images/How_a_learning_app_should_work_img1.png" alt="Img1" width="400" height="48"/>
</div>

<h3>The Reason</h3>
For someone who wants to do well but doesn't want to spend too much time studying, I wanted a solution that could speed things up. I used flashcards, but I 
had ideas for improvement.

Terms shouldn't be memorized from A to Z start to finish, like in traditional flashcards. In traditional flashcards, the card you recite is returned back to the 
bottom of the stack, and you go through an entire rotation to study it again.

For overall faster retention, your brain should be fed the term you got wrong much earlier than waiting for the entire next rotation, 
in the initial stages of studying. If you struggle with a term, perhaps you could put insert it a few cards behind. This mechanism is what I wanted to 
turn into a new app.

<h3>Algorithm アルゴリズム</h3>
I want to mimic a users retention progress and use it to make the flashcards challenging accordingly to their level of progress.
For this purpose, I wrote an algorithm. 

In a stack of cards, each card would hold it's own retention score. If the user knows the term on the card, the card will gain a retention point. 
If the max score is achieved, the user can dismiss the card from the stack. However, if the user cannot recall the card's term its score will be reset to zero.

Additionally, the retention level of a card will determine how far back the card will be replaced in the stack after it is swiped. 
The higher a card's level, the further back it will be placed in the stack, thus challenging the user based on their state of retetion. 

単語帳アプリは、一枚一枚に自分のスコアを記録することができます。カードへのスコアは、正解すれば1点追加され、不正解なら0点に戻されます。5点獲得した時点で、その単語は記録したとみなし、セットから外すことができます。カードのスコアが高ければ高いほど、カードの順番が後ろに移動されます。点が低い(覚えていない)単語は前のほうに、覚えてきた単語は後ろのほうに自動的に並べ替えられるので効率よく覚えることができます。同じアプリを使っても、操作する人によって順番がかわります。


<h5>Ebbinghaus Curve</h5>
I saw a infographic poster on a wall about retention over time like [this](https://en.wikipedia.org/wiki/Forgetting_curve), I thought about applying within a 
smaller span of time than in the theory, like the interval between flipping cards.




