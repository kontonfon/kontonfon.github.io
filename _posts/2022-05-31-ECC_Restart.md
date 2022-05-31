---
layout: post
title: ECC
subtitle: Crypto
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [paper]

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

#### ELLIPTIC CURVES

The use of elliptic curves for public-key cryptography was first suggested in 1985. After resisting decades of attacks, they started to see widespread use from around 2005,
providing several benefits over previous public-key cryptosystems such as RSA

Smaller EC keys offer greater strength, with a 256-bit EC key having the same security level as a 3072-bit RSA key. Furthermore, several operations using those keys (including sigining) can be more efficient both time - and memory - wise. Finally, since ECC is more complex than RSA, is has the welcome effect of encouraging developers to make use of trusted libraries rather than rolling their own.

These challenges aim to give you an intuition for the trapdoor function behind ECC; dip your toes into the mathematical structure underlying it; and have you breaking popular schemes like ECDSA

#### BACKGROUND
Elliptic Curve Cryptography (ECC) is an asymmetric cryptographic protocol that, like RSA and Diffie-Hellman (DH), relies on a trapdoor function. To recap: trapdoor functions allow a client to keep data secret by performing a mathematical operation which is computationally easy to do, but currently understood to be very expensive to undo.

For RSA, the trapdoor function relies on the hardness of factoring large numbers. For Diffie-Hellman, the trapdoor relies on the hardness of the descrete log problem. For both RSA and DH, the operatons that run through the veins of the protocol are familiar to us. Multiplying numbers and taking powers of numbers are things we are taught to do in school. ECC stands out, because the group operation in ECC won't pop up in your life unless you are looking for it.

* The discussion here will not 





