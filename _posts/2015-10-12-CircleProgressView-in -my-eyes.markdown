---
layout: post
title:  "CircleProgressView in my eyes"
date:   2015-10-12 
categories: [Android]

---
Recently i released one ___[CircleProgressView](https://github.com/jackL-e-e/CircleProgressView)___ with dot and dash effect  in my github .
Here i wanna make some explain about this view.

There are two ways to make it looks like circleProgressView.

 1. Just draw three round oval with different radius(strictly the one between top and bottom layer is a  filled ARC,100% then it's a round oval...),so we just draw the arc ,its degree indicates the progress.

 2. And the second way to make it a CircleProgressView is draw two  roundel(not filled) ,one as background and another arc(not filled) as progress.

 Well,at this time you realize this CircleProgress is just a trick of arc,yes exactly!

 Simple as it is ? yes ,go to see the __[source code](https://github.com/jackL-e-e/CircleProgressView)__  to explore more :)









 



