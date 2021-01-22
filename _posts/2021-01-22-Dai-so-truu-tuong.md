---
layout: post
title: Đại số trừu tượng 
subtitle: 
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

## Direct Proof

claim: if $P$ then $Q$

proof: Suppose $P$ then $Q$

------------------

claim: if $m$ and $n$ are odd then $mn$ is odd

proof: Suppose that $m$ and $n$ are odd . 

Thus: $m=2x+1$ and $n=2y+1$ for $x,y\in \mathbb{Z}$

Notice that: $mn=(2x+1)(2y+1) = 4xy+2x+2y+1$ then $mn$ is odd 

----------------------

claim: If $f(x)$ is differentiable at $a\in \mathbb{R}$ then it is continuous at $a$

proof: Suppose $f(x)$ is differentiable at $a$ 

So $\lim\limits_{x\rightarrow} \frac{f(x)-f(a)}{x-a}=f'(a)$ exists and is finite

$0=\lim\limits_{x\rightarrow a}f'(a)(x-a)=(\lim\limits_{x\rightarrow a} x-a)(\lim\limits_{x\rightarrow a} \frac{f(x)-f(a)}{x-a})=\lim\limits_{x\rightarrow a} (f(x)-f(a))$

So, $\lim\limits_{x\rightarrow a} f(x)=f(a)$ so $f(x)$ is continuous at $a$




