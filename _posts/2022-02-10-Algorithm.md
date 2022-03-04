---
layout: post
title: Luyện thuật toán
subtitle: Algorithm
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

#### <span style="color:#4cbb17">Bài 1: </span>

`467C - George and Job`

The solution to this problem is dynamic programming. Initially, you need to calculate `psum_R`, where `psum_R` is the sum on the prefix of the array `p` of length `R`.

Let's denote `dp_(i,j)` - the maximum profit that Jura can get if we have already chosen `i` sequences and the last element in the `i-th` sequence has index `j`.

Obviously, if `i.m>j` then `do_(i,j)=0`. Otherwise `dp_(i,j)=max(dp_(i,j-1),dp_(i-1,j-m)+psum_j-psum_(j-m))`. The answer is `dp_(k,n)`.

You also had to remember to use `long long` in calculations.

Asymptotics: `O(NK)`

```cpp
#include <iostream>
#define ll long long
using namespace std;
ll n,m,k,s[5005],d[5005][5005],i,j;
int main()
{
cin>>n>>m>>k;
for(i=1;i<=n;i++)cin>>s[i],s[i]+=s[i-1];
for(i=1;i<=k;i++)for(j=m;j<=n;j++)d[i][j]=max(d[i][j-1],d[i-1][j-m]+s[j]-s[j-m]);
cout<<d[k][n];
}
```

Link: https://drive.google.com/file/d/10ElcA9Gd_T_EgFrZIzLpLNavoomqMVNR/view?usp=sharing









