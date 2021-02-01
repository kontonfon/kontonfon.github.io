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

Đối với bài này, ta chuyển hex sang bytes và sau đó từ bytes chuyển sang base64 là xong

Code:

~~~py
import base64
hex_string = "72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf"
tmp = bytes.fromhex(hex_string)
aka = "ZW50b21iX3B1cHBlZF9MZWlwemlncw=="
res = base64.b64decode(aka)
print(res)
~~~
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

---------------------------------------------------
### Phần 3.2 XOR

#### Bài 1. XOR start

Bài này yêu cầu ta lấy mỗi phần tử của xâu "label" xor với 13 và sau đó lấy chuỗi kết quả làm flag

Code:

~~~py
s ="label"
res=""
for _ in range(0,len(s)):
    res=res+chr(ord(s[_])^13)
print('crypto{{{0}}}'.format(res))
~~~

Ta được kết quả là:

![Imgur](https://i.imgur.com/cwINeeq.png)

#### Bài 2. XOR Properties

Bài này yêu cầu chúng ta sử dụng 4 tính chất đặc biệt của phép xor chuỗi đó là:

$1. A\oplus B = B \oplus A$

$2. A\oplus (B \oplus C) = (A \oplus B) \oplus C$

$3. A\oplus 0 = A$

$4.A\oplus A =0$

Code:

~~~py
from pwn import xor
# xor two string
def f(s1,s2):
    if len(s1) != len(s2):
        raise "XOR EXCEPTION: Strings are not of equal length!"

    return ''.join(format(int(a, 16) ^ int(b, 16), 'x') for a,b in zip(s1,s2))
key1= "a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313"

key2_xor_key1="37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e"

key2_xor_key3="c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1"

flag_xor_key1_xor_key3_xor_key1="04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf"

flag =f(f(flag_xor_key1_xor_key3_xor_key1,key2_xor_key3),key1)
#print(len(flag_xor_key1_xor_key3_xor_key1))
#print(len(key2_xor_key3))
res =bytes. fromhex(flag)
print(res)


~~~ 

và kết quả thu được là:

![Imgur](https://i.imgur.com/osLPq9t.png)

#### Bài 3. Favourite byte

Đề bài của bài này như sau: Cho một chuỗi hex đã được encode , nhiệm vụ của chúng ta là đem dãy đó xor với 1 bytes để có được flag 

Code:

~~~py
def f(s1,s2):
    if len(s1) != len(s2):
        raise "XOR EXCEPTION: Strings are not of equal length!"

    return ''.join(format(int(a, 16) ^ int(b, 16), 'x') for a,b in zip(s1,s2))
s = "73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d"
print('Do dai cua s la {0}'.format(len(s)))
s_b = bytes.fromhex(s)
lala=""
for j in range(0,16): lala = lala+str(j)
tmp=""
ans =""
ll=[]
print(lala)
for i in range(0,16):
    for j in range(0,16):
        ans
        if(i<10):
            fi = str(i)
        if(j<10):
            se=str(j)
        if(i>=10):
            fi=chr(ord('a')+(i%10))
        if(j>=10):
            se=chr(ord('a')+(j%10))
        tmp = fi+se
        ll.append(tmp)
for aka in ll:
    ans=""
    for i in range(0,33):
        tmp = s[2*i]+s[2*i+1]
        ans = ans + f(aka,tmp)
    print(bytes.fromhex(ans))

~~~

Và thu được kết quả là:

![Imgur](https://i.imgur.com/GfAJ3Q7.png)

#### Bài 4. You either know, XOR you don't

Đây là bài toán theo mình khá hay, vì nó rất mẹo. Bài toán này đơn giản chỉ là , giả sử ta có $A\oplus B=C$. Cho $A$ và $C$. Nhiệm vụ của ta là phải tìm $B$.

Thì để tìm $B$ đơn giản ta lấy $A\oplus C$ vì $A\oplus C=A\oplus A\oplus B = B$

Từ đó ta rút ra thêm một tính chất khá hay nữa là nếu $A\oplus B = C$ thì ta suy ra được $A \oplus C = B$

Code:

~~~py
import binascii
###############
def f(s1,s2):
    if len(s1) != len(s2):
        raise "XOR EXCEPTION: Strings are not of equal length!"

    return ''.join(format(int(a, 16) ^ int(b, 16), 'x') for a,b in zip(s1,s2))
###############
key_tam = "crypto{"

## Lenh chuyen tu bytes sang hex 
key_tam_hex = binascii.hexlify(key_tam.encode('utf8')).decode("utf-8")

print("{0}---{1}".format(key_tam_hex,len(key_tam_hex)))

data = "0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104"

key_7_dau = ""
for _ in range(0,len(key_tam_hex)):
    key_7_dau = key_7_dau + data[_]

print("key 7 dau {0}".format(key_7_dau))
key = f(key_tam_hex,key_7_dau)

print("key that la: {0}".format(bytes.fromhex(key)))

## Suy ra ket that la: 

key_that = "myXORkey"

print("Key that la: {0}".format(key_that))

print("Do dai cua data o che do bytes la: {0}".format(len(bytes.fromhex(data))))

# Chuoi ket can ma hoa la: myXORkeymyXORkeymyXORkeymyXORkeymyXORkeymy

key_can_ma_hoa = "myXORkeymyXORkeymyXORkeymyXORkeymyXORkeymy"

key_can_ma_hoa_hex = binascii.hexlify(key_can_ma_hoa.encode("utf8")).decode("utf-8")

ketqua = f(key_can_ma_hoa_hex,data)

print(bytes.fromhex(ketqua))



~~~

và ta thu được kết quả là :

![Imgur](https://i.imgur.com/DW4W2ww.png)

#### Bài 5. Lemur XOR

Đây là bài toán khá hay, 2 hay bức ảnh và nhiệm vụ của chúng ta là tìm ra bức ảnh key

Code:

~~~py
#!/usr/local/bin/python3
import numpy as np
from PIL import Image

# Open images
im1 = Image.open("anh1.png")
im2 = Image.open("anh2.png")

# Make into Numpy arrays
im1np = np.array(im1)*255
im2np = np.array(im2)*255

# XOR with Numpy
result = np.bitwise_xor(im1np, im2np).astype(np.uint8)

# Convert back to PIL image and save
Image.fromarray(result).save('result.png')
~~~

và kết quả là:

![Imgur](https://i.imgur.com/km4pfKg.png)

-------------------------------------------------------

### Phần 3.3. MATHEMATICS

#### Bài 1. Greatest Common Divisor

Bài này đơn giản tìm UCLN của hai số là xong

Code:

~~~py
def gcd(a,b):
    if(a==0 or b==0):
        return a+b
    return gcd(b%a,a)
print(gcd(66528,52920))
~~~  

#### Bài 2. Extended GCD

Bài này là cho hai số nguyên tố $p$ và $q$. Tìm hai số $u,v$ sao cho $p*u+q*v = gcd(p,q)$

Code trâu:

~~~py
def gcd(a,b):
    if(a==0 or b==0):
        return a+b
    return gcd(b%a,a)
#print(gcd(66528,52920))
print(gcd(26513,32321))

# u * 26513 + v * 32321 = 1
u=0
for v in range(-26514,26514):
    u = 1 - v*32321
    if(abs(u)%26513==0):
        u=u//26513
        print(u)
        print(v)
        print("{0}--{1}".format(u,v))
        break
~~~