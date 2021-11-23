---
layout: post
title: Nhật ký Training ICPC 2021
subtitle: Algorithm, Math
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [Algorithm]

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

## Ngày 23-11-2021 

#### <span style="color:red;font-weight:bold">Đề thi:</span> [Edinburgh Competition 2019](https://codeforces.com/gym/102416)

#### <span style="color:red;font-weight:bold">Những bài làm được:</span> A,C

#### <span style="color:red;font-weight:bold">Những bài chưa làm được:</span> B,D,E 

#### <span style="color:red;font-weight:bold">Những kiến thức trao dồi:</span> Giá trị kỳ vọng, DP , Hình học 

#### <span style="color:red;font-weight:bold">Những nguồn để khắc phục những kiến thức này:</span>

1) [100 Easy problems of Erichto](https://codeforces.com/group/yg7WhsFsAp/contests)

2) [Sums and Expected Value](https://codeforces.com/blog/entry/62690?fbclid=IwAR3DDMt3gaVzV69YxLj-dbzvyzLOFOmRf4nTLs29iusrJQQrbVaEu2hZwU8)

3) [Geometry: 2D points and lines](https://codeforces.com/blog/entry/48122)

4) [DP Tutorial and Problem List](https://codeforces.com/blog/entry/67679)

#### <span style="color:#53AB77;font-weight:bold">Nhận xét chung:</span>  

+ Đây là đề 3 sao, nhưng nhìn chung là khó ! 

+ Các bài yêu cầu khá cao về kiến thức toán và giải thuật 

+ Lần đầu mình gặp 1 bài B khó như vậy 

+ Các đàn anh lên chiến thuật team khá bài bản

#### <span style="color:#53AB77;font-weight:bold">Code những bài AC</span>

##### Bài A:

~~~
#include<bits/stdc++.h>
using namespace std;
#define MOD 1000000007
string s;
int checkPalindrome(string s){
    for(int i=0;i<s.size();i++){
        if(s[i]!=s[s.size()-i-1]){
            return 0;
        }
    }
    return 1 ;
}
int main() {
    int t ,cnt=0;
    cin >> t ;
    while(t--){
        cin >> s ;
        cnt+=checkPalindrome(s);
    }
    cout << cnt ;

}
~~~

##### Bài C:

~~~
#include<bits/stdc++.h>
using namespace std;
#define ll long long 
int main(){
    ll a,d,tmp1,tmp2,tmp3;
    cin>>a>>d;
    tmp1 = d/a;
    tmp2 = d%a;
    tmp3 = ceil(1.0*tmp2/tmp1);
    cout<<a+tmp3;
    return 0;
}
~~~


--------------------------------------------------------







