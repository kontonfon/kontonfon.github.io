---
layout: post
title: Luyện tập Crypto
subtitle: Trên cryptohack.org
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
### Tạo tài khoản trên cryptohack.org

Khi click vào Register trên trang [Cryptohack.org](Cryptohack.org) thì chúng ta sẽ thấy một bài toán kinh điển trong crypto đó là:

![Imgur](https://i.imgur.com/dmzOFw1.png)

Thì bài toán này , theo cách thông thường trong dân gian, chúng ta sẽ sử dụng một công cụ như từ điển, hai dãy A-Z được xếp theo hình tròn, rồi chúng ta xoay và tìm cho đến khi tìm được kết quả hợp lý thì ta sẽ dừng

![Imgur](https://i.imgur.com/ZkzY3oU.png)

Thì cách giải bài này đơn giản chỉ là chúng ta sẽ viết chương trình, duyệt qua tất cả các khả năng của chúng là xong

~~~cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long 
#define db double
#define inf 1000000000000000000
typedef pair<ll,ll> ok;
int main(){
    freopen("output.txt","w",stdout);
    string s;
    s="TMXXSDG OWL KHGJL GTNAGMK";
    // cout<<int('Z');
     ll chay,i;
     string res;
     cout<<s<<'\n';
    //  cout<<int('Z'-'A')<<'\n';
     for(chay = 0;chay<26;chay++){
         res="";
         for(i=0;i<s.size();i++){
            if(!(0<=s[i]-'A'&&s[i]-'A'<=25)) {res=res+s[i];continue;}
            ll tmp = (ll)(s[i]-'A'+chay)%26;
            cout<<tmp<<'\n';
            res = res + (char)(tmp+'A');
        }
        cout<<res<<'\n';
        cout<<"---\n";
     }
    return 0;
}
~~~

Và đây là kết quả của bài toán trên:

![Imgur](https://i.imgur.com/HMn3wqS.png)