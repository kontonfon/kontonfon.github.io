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
-----------

### <span style="color:red"> Bài 2</span>

~~~
Dạng bài: Segment tree, bitwise
~~~

#### <span style="color:green"> Đề bài </span>

Lucida có một chuỗi gồm $n$ số nguyên $a_1,a_2,...,a_n$. Anh ấy yêu cầu bạn thực hiện $2$ phép toán cho anh ấy, chúng được mô tả như sau:

- 1 L R, thêm $lowbit(a_i)$ vào mỗi $a_i$ trong đoạn [L,R]

- 2 L R, trả về tổng các số trong đoạn [L,R]

Trong đó: $lowbit(a_i)$ được định nghĩa là luỹ thừa lớn nhất của $2$ và là ước của $x$.

Ví dụ: $lowbit(4)=4,lowbit(5)=1$, Đặc biệt: $lowbit(0)=0$

Lucida muốn bạn cho kết quả mod 998244353 cho mỗi query của anh ấy.

#### <span style="color:orange"> Input </span>

- Bài toán có nhiều testcase

- Dòng thứ nhất, chứa số $T(1\le T\le 20)$ - Thể hiện số testcase

- Ứng với mỗi testcase, dòng thứ nhất chứa một số nguyên $n(1\le n\le 10^5)$ - Độ dại của chuỗi số nguyên

- Dòng tiếp theo, chứa $n$ số nguyên $a_i(1\le a_i<998244353)$

- Dòng tiếp theo, chứa số nguyên $m(1\le m\le 10^5)$ - số lượng phép toán.

- $m$ dòng tiếp theo, mỗi dòng chứa $3$ số nguyên $op,L,R(1\le op\le 2,1\le L\le R\le n)$ - Thể hiện các phép toán.


#### <span style="color:orange"> Output </span>

- Ứng với mỗi query, in ra kết quả mod 998244353

#### <span style="color:orange"> Ví dụ </span>

Input:

~~~
1
5
1 2 3 4 5
5
2 2 4
1 1 3
2 2 4
1 1 5
2 4 5
~~~

Output:

~~~
9
12
14
~~~

#### <span style="color:purple"> Lời giải </span>

- `lowbit(x)=x&-x`

![Imgur](https://i.imgur.com/DtPGBbk.png)

- `Dựng cây segment`

![Imgur](https://i.imgur.com/pQAJiOe.png)

- `Query: 2 2 4`

![Imgur](https://i.imgur.com/oIfrgaY.png)

- `Update: 1 1 3`

![Imgur](https://i.imgur.com/IPLdtYt.png) 

- `Query: 2 2 4`

![Imgur](https://i.imgur.com/txsS9oj.png)

- `Update: 1 1 5`

![Imgur](https://i.imgur.com/56OS1B4.png)

- `Query 2 4 5`

![Imgur](https://i.imgur.com/R9hs8La.png)

#### <span style="color:brown"> Code tham khảo </span>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long
#define pii pair<int, int>
#define re register
#define lc rt << 1
#define rc rt << 1 | 1
const int maxn = 1e5 + 10;
const int max = 40;
const ll mod = 998244353;
const ll inf = 34359738370;
const int INF = 1e9 + 7;
const double pi = acos(-1.0);
inline ll lowbit(ll x)
{
    return x & (-x);
}
struct node
{
    int ok;
    ll sum;
    int l, r;
    ll tag2;
} tree[maxn << 2];
inline void pushup(int rt)
{
    tree[rt].ok = tree[lc].ok & tree[rc].ok;
    tree[rt].sum = (tree[lc].sum + tree[rc].sum) % mod;
}
inline void build(int rt, int l, int r)
{
    tree[rt].l = l, tree[rt].r = r;
    tree[rt].tag2 = 1;
    if (l == r)
    {
        ll d;
        scanf("%lld", &d);
        if (d == lowbit(d))
            tree[rt].ok = 1;
        else
            tree[rt].ok = 0;
        tree[rt].sum = d;
        return;
    }
    int mid = (l + r) >> 1;
    build(lc, l, mid);
    build(rc, mid + 1, r);
    pushup(rt);
}
inline void change(int rt, ll v)
{
    tree[rt].tag2 = tree[rt].tag2 * v % mod;
    tree[rt].sum = tree[rt].sum*v%mod;
}
inline void pushdown(int rt)
{
    if (tree[rt].tag2 > 1)
    {
        change(lc, tree[rt].tag2);
        change(rc, tree[rt].tag2);
        tree[rt].tag2 = 1;
    }
}
inline void upd(int rt, int vl, int vr)
{
    int l = tree[rt].l, r = tree[rt].r;
    if (vr < l || r < vl)
        return;
    if (vl <= l && r <= vr)
    {
        if (tree[rt].ok)
        {
            change(rt, 2ll);
            return;
        }
    }
    if (l == r)
    {
        if (tree[rt].ok)
            change(rt, 2ll);
        else
        {
            tree[rt].sum += lowbit(tree[rt].sum);
            if (tree[rt].sum == lowbit(tree[rt].sum))
            {
                tree[rt].ok = 1;
            }
        }
        return;
    }
    pushdown(rt);
    upd(lc, vl, vr);
    upd(rc, vl, vr);
    pushup(rt);
}
inline ll query(int rt, int vl, int vr)
{
    int l = tree[rt].l, r = tree[rt].r;
    if (vr < l || r < vl)
        return 0;
    if (vl <= l && r <= vr)
        return tree[rt].sum;
    pushdown(rt);
    return (query(lc, vl, vr) + query(rc, vl, vr)) % mod;
}
int n;
int main()
{
    int t;
    cin >> t;
    while (t--)
    {
        scanf("%d", &n);
        build(1, 1, n);
        int m;
        scanf("%d", &m);
        while (m--)
        {
            int f, x, y;
            scanf("%d %d %d", &f, &x, &y);
            if (f == 1)
            {
                upd(1, x, y);
            }
            else
            {
                cout << query(1, x, y) << '\n';
            }
        }
    }
    return 0;
}
```






















