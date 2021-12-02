---
layout: post
title: ICPC training 
subtitle: algorithm
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

### <span style="color:red"> Bài 1 </span>

~~~
Dạng bài: hoán vị, tổ hợp
~~~

#### <span style="color:green"> Đề bài: </span>

Điền vào bảng $n\text{x}n$ với các số trong đoạn $[1;n^2]$, mỗi số xuất hiện một lần. Với mỗi cách điền số, gọi $a_i$ là giá trị nhỏ nhất của hàng thứ $i$ và gọi $S=$ { $a_1,a_2,...,a_n$ } $\cap$ { $1,2,...,n$ } 

Bạn cần tính $\sum G(S)$  (mod 998244353), nghĩa là tổng tất cả lực lượng của $S$ qua tất cả các trường hợp có thể. (trong đó $G(S)$ chính là số lượng phần tử của tập $S$)

#### <span style="color:orange"> Input: </span>

- Bài toán có nhiều testcase

- Dòng đầu tiên chứa số $T(1\le T\le 30)$

- $T$ dòng tiếp theo, mỗi dòng chứa số nguyên $n(1\le n\le 5000)$

#### <span style="color:orange"> Output: </span>

- Ứng với mỗi testcase, in ra đáp án cần tìm

#### <span style="color:orange"> Ví dụ : </span>

Input:

~~~
1
2
~~~

Output:

~~~
40
~~~

#### <span style="color:purple"> Lời giải : </span>

- Xem xét sự đóng góp của số $i$ vào câu trả lời. Trước tiên, hãy chọn $n-1$ số trong số các số lớn hơn $i$ trong $n^2-i$ và đặt chúng vào cùng một dòng, tức là có $\binom{n^2-i}{n-1}$ cách chọn có thể. Bạn có thể chọn $n$ hàng. Khi đó ta có tổng cộng $n!$. Tất cả các số còn lại là $(n^2-n)!$

Do đó ta có công thức là: ![Imgur](https://i.imgur.com/5ezSxsj.png) 

#### <span style="color:brown"> Code tham khảo : </span>

```cpp
#include<bits/stdc++.h>
using namespace std;
#define debug(x) cout<<"###"<<x<<"###"<<endl;
typedef long long ll ;
const double eps = 1e-8 ;
const int INF = 0x3f3f3f3f;
const ll mod = 998244353;
const int N = 25e6;
ll fac[N+5];
void init(){
    fac[0]=1;
    for(int i=1;i<=N;i++){
        fac[i] = fac[i-1]*i%mod;
    }
    return ;
}
ll binpow(ll a,ll b){
    ll res = 1;
    while(b){
        if(b&1){
            res=res*a%mod;
        }
        b>>=1;
        a=a*a%mod;
    }
    return res;
}
ll C(int n,int m){
    ll up = fac[n];
    ll down = fac[m]*fac[n-m]%mod;
    return (up*binpow(down,mod-2))%mod;
}
int main(){
    int t;
    init();
    scanf("%d",&t);
    while(t--){
        int n;
        scanf("%d",&n);
        ll ans = 0;
        for(int i=1;i<=n;i++){
            ans = (ans + C(n*n-i,n-1))%mod;
        }
        ans = ans * fac[n]%mod*n%mod*fac[n*n-n]%mod;
        printf("%lld\n",ans);
    }
}
```
















