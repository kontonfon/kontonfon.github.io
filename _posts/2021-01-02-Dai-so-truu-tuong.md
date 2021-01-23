---
layout: post
title: Đại số trừu tượng 
subtitle: Abstract Algbra
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [abstract algebra]

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

proof: Suppose $P$ ... then $Q$

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

-----------------------

claim: If $a$ is odd then $a^2+4a+7$ is even.

proof: Suppose that $a$ is odd. So we can write $a=2k+1$ for $k\in \mathbb{Z}$

Notice that: $a^2+4a+7=(2k+1)^2+4(2k+1)+7=4k^2+4k+1+8k+4+7=4k^2+12k+12=2(2k^2+6k+6)=2k'$, which is even.

-----------------------

## Proof by contrapositive  | $P\implies Q \equiv \text{~}Q \implies\text{~}P$

claim: If $x^2-8x+11$ is even then $x$ is odd

$P:x^2-8x+11$ is even

$\text{~}P: x^2-8x+11$ is odd

$Q: x$ is odd

$\text{~}Q: x$ is even

Proof: Suppose that $x$ is even 

Thus $x=2k$ for $k\in \mathbb{Z}$

Notice: $x^2-8x+11=(2k)^2-8(2k)+11=4k^2-16k+10+1=2(2k^2-8k+5)+1=2k'+1$

which is odd. 


------------------------

claim: If 	$3\nmid xy$ then $3 \nmid x$ and $3 \nmid y$

$P:3\nmid xy $

$Q:3\nmid x\text{ and } 3\nmid y$

$\text{~}P:3\mid xy$

$\text{~}Q:3\mid \text{ or } 3\mid y$ 

proof: Suppose that: $3\mid x \text{ or }3\mid y$. Without loss of generality assume $3\mid x$. So, $x=3k$ for $k\in \mathbb{Z}$. Thus $xy=(3k)y=3k'$. So $3 \mid xy$

----------------------------

## Proof by contradiction

claim: if $a,b\in \mathbb{Z}$ then $a^2-9b\ne 3$

proof: Suppose that $a,b\in \mathbb{Z}$ such that $a^2-9b=3$

So $a^2=9b+3=3(3b+1)$

and thus $3\mid a^2$

So $3\mid a$ and we can write $a=3k$ for $k\in \mathbb{Z}$ 

$\implies (3k)^2=3(3b+1)\implies 3k^2=3b+1$

Thus $1=3(k^2-b)$ and $3\mid 1$, a contradiction

-----------------------------

Theorem: There are infinitely many primes

Proof: Suppose there are finitely many primes $p_1,...,p_n$

Consider: $\frac{1}{1-\frac{1}{p_1}}.\frac{1}{1-\frac{1}{p_2}}...\frac{1}{1-\frac{1}{p_n}}=(1+\frac{1}{p_1}+\frac{1}{p_1^2}+...)...(1+\frac{1}{p_n}+\frac{1}{p_n^2}+...)=1+\frac{1}{2}+\frac{1}{3}+\frac{1}{4}+\frac{1}{5}+\frac{1}{6}+...=\sum\limits_{n=1}^{\infty} \frac{1}{n}$, so the harmonic series converges, a contradiction

------------------------------

## Principles of Mathematical Induction 

$1=1=1^2$

$1+3=4=2^2$

$1+3+5=9=3^2$

$1+3+5+7=16=4^2$

prop: For all $n\in \mathbb{N}$, we have $1+3+5+...+(2n-1)=n^2$

Proof: (PMI)

Base case: $(n=1)$ Observe that $1=1^2$

Induction hypothesis

Suppose for $k\ge 1$, we have $1+3+...+(2k-1)=k^2$

Consider $1+3+5+...+(2k-1)+(2k+1)=k^2+2k+1 = (k+1)^2$

-------------------------------------

claim: For all $n\in \mathbb{N}$, we have: $3\mid 5^{2n}-1$

proof: (PMI)

Base: $(n=1)$ notice that $5^2-1=24=3.8$ so $3\mid 5^{2.1}-1$ 

Induction hypothesis: 

Suppose for some $k\ge 1$, we have $3\mid 5^{2k}-1 \iff 5^{2k}-1=3m$

Consider: $5^{2(k+1)}-1=5^{2k}.5^{2}-1=5^{2k}.5^{2}-5^2+5^2-1=5^2(5^{2k}-1)+5^2-1=5^2.3m+3.8=3(25m+8)$

$\implies 5^{2(k+1)}-1=3(25m+8)=3m'$

$\implies 3\mid 5^{2(k+1)}$

So $3\mid 5^{2n}-1$.

--------------------------------------------

## A relation on a set

Def: A relation on a set A is a subset $R\subseteq A\text{x} A$

write 

 - $(x,y)\in R$ as $xRy$

 - $(x,y)\notin R$ as $x\not R y$ 

 ex: $A$ = any set, $R$ is equality 

 $(x,y)\in R\iff x=y$

 R = {$(a,a)\mid a\in A$}

 A = {1,2,3}, R = {(1,1),(2,2),(3,3)}

 ex: A= {1,2,3}, R is less than or equal

 $1\le 1\implies (1,1)\in R,1\le 2\implies (1,2)\in R,1\le 3\implies (1,3)\in R,..$

 R={(1,1),(1,2),(1,3),(2,2),(2,3),(3,3)}



