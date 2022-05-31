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

* The discussion here will not be total, and those who are really looking to understand ECC, I recommend these notes Elliptic Curve notes by Ben Lynn, and the textbox "An Introduction to Mathematical", Jeffrey Hoffstein, Jull Pipher, Joseph H. Silverman

Let's start thinking about ECC by looking at what we mean by an elliptic curve. We will be studying 'Weierstrass equations', which are of the form 

`Y^2 = X^3+AX+B`

Elliptic curves have an amazing feature: We can define an operator that we will call "point addition". This operator takes two points on some curve and produces a third point on the curve. Taking the set of points on an elliptic curve, point addtion defines an Abelian group.

There's a lot of text here. Let's motivate this! We can understand scalar multiplication of a point as the repeated point addition of the same point. Q = 2P = P + P. It turns out that scalar multiplication is a trapdoor function ! ECC relies on the hardness of finding the `n` such that `Q=nP` given `Q` and `P` 

#### So how do we understand point addtion ?

Geometrically, we can understand point addtion `P+Q` like so. Take an elliptic curve and mark the two points `P,Q` along the curve with their `x,y` coordinates. Draw a straight line that passes through both points. Now continue the line until it intersects your curve a third time. Mark this new intersection `R`. Finally, take `R` and reflect it along the `y` direction to produce `R'=R(x,-y)`. The result of the point addition is `P+Q = R'`

What if we want to add two of the same point together: `P+P` ? We can't draw a unique line through one point, but we can pick a unique line by calculating the tangant line to the curve at this point. Calculate the tangent line at the point `P`. Continue the line until it intersects with the curve at point `R`. Reflect this point as before: `P+P=R' = R(x,-y)`

What happens if there is no third intersection ? Sometimes you will pick two points `P,Q` and the line will not touch the curve again. In this case, we say that the line intersects with the point `(O)` which is a single point located at the end of every vertical line at infinity. As such, point addition for an elliptic curve is defined in 2D space, with an additional point located at infinity.

Included below is a diagram as a visual aid to these different cases.

![Imgur](https://i.imgur.com/tscJhQA.png)

The point `O` acts as the identity operator of the group: `P+O=P` and `P+(-P) = O`

This brings us to the point of defining and elliptic curve.

Definition: An elliptic curve E is the set of solutions to a Weierstrass equation

`E: Y^2 = X^3+aX+b`

together with a point at infinity `O`. This constants `a,b` must satisfy the relationship: `4a^3+27b^2 <> 0`

to ensure there are not singularities on the curve.

Formally, let E be an elliptic curve, point addition has the following properties:

(a) `P+O=O+P=P`
(b) `P+(-P)=O`
(c) `( P + Q )+R = P + (Q + R)`
(d) `P + Q = Q + P`

In Ecc, we study elliptic curve over a finite field F_p. This means we look at the curve modulo the charactieristic p and an elliptic curve will no longer be a curve, but a collection of points whose `x,y` coordinates are integers in `F_p`.

The following starter challenges will take you through the calculations for ECC and get you used to the basic opeations that ECC is built upon, have fun!

Property `(d)` shows that point addition is commutative. The flag is the name we give groups with a commutative operation.






