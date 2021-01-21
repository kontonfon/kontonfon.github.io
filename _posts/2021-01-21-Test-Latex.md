---
layout: post
title: Tập tành latex
subtitle: Một số lệnh latex cơ bản
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
### 1. Phân số 

$\frac{x^2}{y^2}$

Cú pháp:

~~~
$\frac{x^2}{y^2}$
~~~

### 2. Tên tập hợp

$\mathbb{N}$

Cú pháp:

~~~
$\mathbb{N}$
~~~

### 3. Khác

Link: https://tanphong.wordpress.com/latex/mot-so-lenh-latex-thuong-su-dung/