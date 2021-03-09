---
layout: post
title: Random Forst Algorithm
subtitle: Random Forest Algorithm
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
[Link](https://www.youtube.com/watch?v=J4Wdy0Wc_xQ)

### Part 1 - Buiding, Using and Evaluating

We're gonna be starting part one of a series on random forests, and we're going to to talk about building and evaluating random forests.

Note random forests are built from decision trees. So if you don't already know about these check out my stat quest and breef up

Decision trees are easy to build easy to use and easy to interpret

But in practice they are not awesome 

To quote from the elements of statistical learning aka of Bible of machine learning

Trees have one aspect that prevents them from being the ideal tool for predictive learning 

Namely in accuracy. 

But they are not flexible when it comes to classifying new samples

The good news is that random forest combine the simplicit of decision tree with flexibility. Resulting in a vast improvement in accuracy.

[1:11]