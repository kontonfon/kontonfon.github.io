---
layout: post
title: Học Toán mỗi ngày
subtitle: mathematics
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [latex]

---


<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>

----------------
###  Ngày 30-9-2021

Problem: 

![Imgur](https://i.imgur.com/j4Uerkj.png) 

Solution: 

![Imgur](https://i.imgur.com/qq8cRJa.png)

### Ngày 1-10-2021

Problem:

![Imgur](https://i.imgur.com/w1s1L0u.png)

Solution:

![Imgur](https://i.imgur.com/LuHiVws.png)

## Ngày 4-10-2021

Problem:

![Imgur](https://i.imgur.com/CeL5Mie.png)

Solution:

![Imgur](https://i.imgur.com/8qYsfOO.png)

![Imgur](https://i.imgur.com/Oicdtn9.png)

## Day 22-12-2021

### <span style="color:red"> Problem 1</span>
Let (m,n) be pair of positive integers. Julia has carefully planted m rows of n dandelious is an mxn array in her back garden. Now, Jana un Viviane decides to play a game with a lawnmower they just found. Talking alternating turns and starting with Jana, they can now mow down all the dandelions in a straight horizontal or vertical line (and they must mow down at least one dandelion). The winner is the player who mows down the final dandelion. Determine all pairs of (m,n) of which Jana has a winning strategy.

### <span style="color:red"> Solution 1 </span>

The answer is all the pairs (m,n) with (m-1)(n-1)=0 or m+n odd. Let's prove it.

When m=1 or n=1, Jana can clearly win with a single move. At the other hand, any player with m,n>1 and m+n odd has the winning strategy of first creating a line of symmetry and then playing symmetrically. Not only do this prove m+n odd m,n > 1 is a winning position, but it also proves m+n even, m,n>1 is losing one, as any movement reduces the problem to the situation m+(n-1) or (m-1)+n odd, which are winning positions for the other player. Those, we have proven that the only winning positions are the desired ones, so we are done.

### <span style="color:red"> Problem 2 </span>

![Imgur](https://i.imgur.com/e6Oo87P.png)

### <span style="color:red"> Solution 2 </span>

![Imgur](https://i.imgur.com/Tj77dwC.png)








