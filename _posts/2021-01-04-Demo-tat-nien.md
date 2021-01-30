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

## Phần 1: Giới thiệu

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

------------------------------------------------------

## Phần 2. Introduction

Trong phần này chúng ta sẽ có 3 challenges, ở mức giới thiệu để ta làm quen với crypto

### Bài 1. Finding Flags

Bài này đơn giản ta copy: crypto{y0ur_f1rst_fl4g} vào và submit là xong

### Bài 2. Great Snakes

Bài này, ta tải file great_snakes.py về và sau đó chạy trên terminal là xong

![Imgur](https://i.imgur.com/oAtewVS.png)

### Bài 3. Network Attacks

Đối với bài này, ta tải file python về là thay đổi value trong file đó thành flag là xong

![Imgur](https://i.imgur.com/sTyWulL.png)

Và sau đó ta chạy file này là sẽ hiện ra cờ (mình chạy trên Kali Linux nhé )

![Imgur](https://i.imgur.com/w7PeJG1.png)

Như vậy là ta đã hoàn tất 3 bài của phần Introduction, tiếp theo ta sẽ đến phần General 

-------------------------------------------------------------------

## Phần 3. General

### Phần 3.1 ENCODING 

#### Bài 1. ASCII

Ở bài này, nhiệm vụ của chúng ta là phải đưa list đã cho thành chuỗi ASCII tương ứng

Code:

~~~py
l = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
res=""
for p in l:
	res=res+chr(p)
print(res)
~~~

và ta được kết quả là : 

![Imgur](https://i.imgur.com/3PXixW7.png)

#### Bài 2. Hex

Đối với bài này, chúng ta sẽ chuyển chuổi hex sang bytes và khi đó sẽ lấy được cờ:

Code:

~~~py
hex_string = "63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d"
res = bytes.fromhex(hex_string)
print(res)
~~~

và ta được kết quả là :

![Imgur](https://i.imgur.com/JIhs9Zh.png)

#### Bài 3. Base64

Đối với bài này, ta chuyển hex sang bytes và sau đó từ bytes chuyển sang base64 và xong

và ta được kết quả là :

![Imgur](https://i.imgur.com/QvfoA5U.png)

#### Bài 4.  Bytes and Big Integers

Đối với bài này, ta chỉ cần sử dụng hai thư viện đã gợi ý là xong

Code:

~~~py
from Crypto.Util.number import bytes_to_long
from Crypto.Util.number import long_to_bytes
s = "11515195063862318899931685488813747395775516287289682636499965282714637259206269"
res = long_to_bytes(s)
print(res)

~~~

và kết quả là :

![Imgur](https://i.imgur.com/nvmsEY2.png)

--------------------------------------------------------------

#### Bài 5. Encoding Challenge

Đây là bài toán tổng hợp tất cả các bài toán trên, mình đánh giá bài này khá hay vì nó tổng hợp đầy đủ những kĩ thuật liên quan đến encoding của 4 bài trước đó, dưới đây là code 

~~~py
from pwn import * # pip install pwntools
import json
import base64
import codecs
from Crypto.Util.number import bytes_to_long
from Crypto.Util.number import long_to_bytes
rot13 = lambda s : codecs.getencoder("rot-13")(s)[0]

r = remote('socket.cryptohack.org', 13377, level = 'debug')

def json_recv():
    line = r.recvline()
    return json.loads(line.decode())

def json_send(hsh):
    request = json.dumps(hsh).encode()
    r.sendline(request)

for _ii in range(0,100):
    print(_ii+1)
    received = json_recv()
    #print(received)
    #print("Received type: ")
    _type =received["type"] 
    #print(received["type"])
    #print("Received encoded value: ")
    #print(received["encoded"])
    _encoded = received["encoded"]
    res=""
    if(_type=="utf-8"):
        print("Hello UTF-8")
        for p in _encoded:
            res=res+chr(p)
    if(_type=="base64"):
        print("Hello BASE64")
        ans = base64.b64decode(_encoded)
        res = ans.decode("utf-8")
    if(_type=="hex"):
        print("HELLO HEX")
        ans=bytes.fromhex(_encoded)
        res = ans.decode("utf-8")
    if(_type=="bigint"):
        print("HELLO BIGINT")
        tmp=""
        for _ in range(0,len(_encoded)):
            if(_!=0 and _!= 1):tmp=tmp+_encoded[_]
        ans =bytes.fromhex(tmp)
        #res.decode("utf-8")
        res = ans.decode("utf-8")
    if(_type=="rot13"):
        print("HELLO ROT13")
        ans=rot13(_encoded)
        #res.decode("utf-8")
        res = ans
    print("Ket qua la: ")
    print(res)
    to_send = {
        "decoded": res
    }
    json_send(to_send)
s=json_recv()
print(s)
~~~
Và kết quả là :

![Imgur](https://i.imgur.com/pI8CJUI.png)
