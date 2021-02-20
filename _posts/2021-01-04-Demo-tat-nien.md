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

#### Bài 3. Modular Arithmetic 1

Bài này yêu cầu chúng ta tìm min của $11\text{ % }6 $ và $8146798528947\text{ % }17$

Code:

~~~py
print(min(8146798528947%17,11%6))
~~~

#### Bài 4. Modular Arithmetic 2

Bài này yêu cầu chúng ta tính : $273246787654^{65536}\text{ mod }65537$. Biết rằng $65537$ là số nguyên tố.

Bài này đơn giản ta tìm dư của $273246787654$ cho $65537$ ta được $31167$, do $(31167,65537)=1$ và $65537$ là số nguyên tố nên theo định lý Fermat bé ta có đáp án bài toán đã cho là $1$.

#### Bài 5. Modular Inverting

Bài này yêu cầu chúng ta tìm $d$ sao cho $3.d \equiv 1 \text{ mod } 13$

Code:

~~~py
# 3*d = 1 mod 13
# => d = 3^(-1) mod 13 = 3^(-1).3^12 mod 13 (Vi 3^12 =1 mod 13)
# => d = 3^11 mod 13
ans = 1
for _ in range(0,11):
    ans = ans * 3 %13
print(ans)

~~~

Chú ý: Ở đây dấu = thể hiện đồng dư trong đoạn comment trong code

----------------------------------------------

## MATHEMATICS

### MODULAR MATH

#### Quadratic Residues 

Chúng ta đã học qua phép nhân và phép chia trong Modular Arithmetic, nhưng căn bậc hai modulo của một số nguyên là gì ? 

Chúng ta sẽ trao đổi chúng ở dưới đây, Xét modulo $p=29$. Chúng ta có thể lấy số nguyên $a=11$ và tính được $a^2=5 \text{ mod }19$

Bởi vì $a=11,a^2=5$ nên ta nói căn bậc hai của $5$ modulo $29$ là $11$.

Điều này có vẻ có gì đó hay ho, nhưng bây giờ chúng ta sẽ suy nghĩ một chút về căn bậc hai của $18$ modulo $29$. Từ điều trên, chúng ta cần tìm số nguyên $a$ sao cho $a^2=18$ modulo $29$.

Ý tưởng của chúng ta sẽ bắt đầu từ $a=1$ và lặp cho đến $a=p-1$. Trong bài này, $p$ không quá lớn và chúng ta có thể nhanh chóng tìm được $a$.

Với những gì chúng ta thấy, có nghĩa là với mỗi phần tử của $\mathbb{F}_p^{*}$, không phải phần tử nào cũng có căn bậc hai. Thực tế, những gì chúng ta tìm thấy rằng, đối với khoảng một nữa số phần tử của $\mathbb{F}_p^{ * }$, không có căn bậc hai.

Ghi chú:

Chúng ta nói $x$ là Quadratic Residue nếu tồn tại số $a$ thoả mãn $a^2 = x \text{ mod }p$. Nếu không tồn tại nghiệm, vì số nguyên đó gọi là Quadratic Non-Residue.

Hay nói cách khác, $x$ là một quadratic residue khi nó có thể lấy căn bậc hai của $x$ theo modulo $p$.

Danh sách dưới đây có hai non-quadratic residues và một quadratic residue.

Tìm quadratic residue và sau đó tính căn bậc hai của nó. Bởi vì có hai nghiệm thoả mãn, nên ta lấy nghiệm bé hơn làm cờ.

Chú ý:

Nếu $a^2=x$ thì $(-a)^2=x$. Vì vậy nếu $x$ là quadratic residue ở trường hữu hạn nào đó, thì luôn có hai nghiệm đối với $a$.

Code : 
~~~
p = 29
ints = [14,6,11]

def check_quadratic_residue(x):
    for z in range(1,29):
        tmp=(z*z)%p
        if(tmp==x):
            print('Dap an la : {0} voi so quadratic residue tuong ung la : {1}'.format(z,x))
            break
for _ in ints:
    check_quadratic_residue(_)
~~~

------------------------------------------------

#### Legendre Symbol

Trong phần Quadratic Residues, chúng ta đã học được những cái mà nó có nghĩa là lấy căn bậc bậc hai modulo của một số nguyên. Chúng ta còn nhận ra rằng một căn bậc hai không phải lúc nào cũng tồn tại.

May mắn thay cho chúng ta, chúng ta có một cách để kiểm tra liệu rằng một số nguyên có phải là quadratic residures với một phép tính đơn giản dựa vào Legendre. Ở dưới đây, chúng ta giả sử rằng chúng ta làm việc với một số nguyên tố $p$.

Trước khi nhìn vào Legendre's symbol, chúng ta sẽ tóm tắt những tính chất quan trọng của quadratic residues và quadratic non-residues.

~~~
Quadratic Residue * Quadratic residue = Quadratic Residue
Quadratic Residue * Quadratic Non-Residue = Quadratic Non-residue
Quadratic Non-residue * Quadratic Non-residue = Quadratic Residue
~~~

Ghi chú: Để thuận tiện cho việc ghi nhớ , cũng ta thay thế "Quadratic Residue" với +1 và "Quadratic Non-residue" với -1, tất cả ba kết quả trên đều như nhau.

Vì vậy, mẹo ở đây là gì ? Legendre Symbol sẽ cho chúng ta cách hiệu quả để xác định liệu rằng một số nguyên có phải là quadratic residue modulo một số nguyên tố lẻ $p$ hay không ?

Legendre's Sybmol: $(\frac{a}{p})\equiv a^{\frac{(p-1)}{2}}\text{ mod }p$, với :

 + $(\frac{a}{p})=1$ nếu $a$ là quadratic residue và $a\not \equiv 0(\text{ mod }p)$

 + $(\frac{a}{p})=-1$ nếu $a$ là quadratic non-residue mod

 + $(\frac{a}{p})=0$ nếu $a\equiv 0\text{ mod }p$

 Điều này có nghĩa là với mọi số nguyên $a$, tính $pow(a,(p-1)\text{/}2,p)$ là đủ để xác định $a$ là quadratic residue hay không . 

 Bây giờ là vì flag. Cho một số nguyên tố gồm $1024$ bit và $10$ số nguyên, tìm quadratic residue và tính căn bậc hai của nó, căn bậc hai của nó chính là cờ của bạn. Bởi vì có hai nghiệm có thể nên ta in ra nghiệm lớn hơn.

 Ghi chú:

 Vì Legendre's symbol cho chúng ta biết số nào là quadratic residue, nhưng làm thế nào để chúng ta tìm căn bậc hai của chúng ? Số nguyên tố cho ta biết số đó có dạng $p=3 \text{ mod }4$, điều này cho phép chúng ta dễ dàng tính toán căn bậc hai của chúng. Đáp án là online, nhưng bạn có thể nghĩ đến định lý Fermat bé.

 Lời giải của bài này như sau:

 Gọi $a$ là số thoả mãn $(\frac{a}{p})=1$ trong $10$ số nguyên đề cho, khi đó nhiệm vụ còn lại của ta là đi tìm căn bậc 2 của $a$ mod p. Và ta tìm như sau :

 Vì $(\frac{a}{p})=1\implies a^{\frac{(p-1)}{2}}\equiv 1(\text{ mod } p )\implies a^{\frac{(p+1)}{2}}\equiv a(\text{ mod } p )(1)$ 

 Và nhiệm vụ của ta bây giờ là tìm số $z$ sao cho $z^2\equiv a(\text{ mod } p )$

 Ta nhận thấy rằng, vì đề cho $p$ có dạng $p=4k+3$ nên từ $(1)\implies a^{\frac{(p+1)}{2}}\equiv a(\text{ mod } p )\iff a^{\frac{(4k+4)}{2}}\equiv a(\text{ mod } p )\iff a^{2k+2}\equiv a(\text{ mod } p )$

 Đến đây ta dễ dàng suy ra được $z\equiv a^{k+1}(\text{ mod } p )$

 Đến đây nhiệm vụ của ta là đi tìm $k$ và tính $a^{k+1}(\text{ mod } p )$ là xong.

 Code:

 ~~~
 p = 101524035174539890485408575671085261788758965189060164484385690801466167356667036677932998889725476582421738788500738738503134356158197247473850273565349249573867251280253564698939768700489401960767007716413932851838937641880157263936985954881657889497583485535527613578457628399173971810541670838543309159139

ints = [25081841204695904475894082974192007718642931811040324543182130088804239047149283334700530600468528298920930150221871666297194395061462592781551275161695411167049544771049769000895119729307495913024360169904315078028798025169985966732789207320203861858234048872508633514498384390497048416012928086480326832803, 45471765180330439060504647480621449634904192839383897212809808339619841633826534856109999027962620381874878086991125854247108359699799913776917227058286090426484548349388138935504299609200377899052716663351188664096302672712078508601311725863678223874157861163196340391008634419348573975841578359355931590555, 17364140182001694956465593533200623738590196990236340894554145562517924989208719245429557645254953527658049246737589538280332010533027062477684237933221198639948938784244510469138826808187365678322547992099715229218615475923754896960363138890331502811292427146595752813297603265829581292183917027983351121325, 14388109104985808487337749876058284426747816961971581447380608277949200244660381570568531129775053684256071819837294436069133592772543582735985855506250660938574234958754211349215293281645205354069970790155237033436065434572020652955666855773232074749487007626050323967496732359278657193580493324467258802863, 4379499308310772821004090447650785095356643590411706358119239166662089428685562719233435615196994728767593223519226235062647670077854687031681041462632566890129595506430188602238753450337691441293042716909901692570971955078924699306873191983953501093343423248482960643055943413031768521782634679536276233318, 85256449776780591202928235662805033201684571648990042997557084658000067050672130152734911919581661523957075992761662315262685030115255938352540032297113615687815976039390537716707854569980516690246592112936796917504034711418465442893323439490171095447109457355598873230115172636184525449905022174536414781771, 50576597458517451578431293746926099486388286246142012476814190030935689430726042810458344828563913001012415702876199708216875020997112089693759638454900092580746638631062117961876611545851157613835724635005253792316142379239047654392970415343694657580353333217547079551304961116837545648785312490665576832987, 96868738830341112368094632337476840272563704408573054404213766500407517251810212494515862176356916912627172280446141202661640191237336568731069327906100896178776245311689857997012187599140875912026589672629935267844696976980890380730867520071059572350667913710344648377601017758188404474812654737363275994871, 4881261656846638800623549662943393234361061827128610120046315649707078244180313661063004390750821317096754282796876479695558644108492317407662131441224257537276274962372021273583478509416358764706098471849536036184924640593888902859441388472856822541452041181244337124767666161645827145408781917658423571721, 18237936726367556664171427575475596460727369368246286138804284742124256700367133250078608537129877968287885457417957868580553371999414227484737603688992620953200143688061024092623556471053006464123205133894607923801371986027458274343737860395496260538663183193877539815179246700525865152165600985105257601565]

def po(a,n):
    res=a
    ans=1
    while(n>0):
        if(n%2==1):
            ans=ans*res%p 
        res=res*res%p 
        n=n//2
    return ans

mu = (p-1)//2
dem=0
a=0
for z in ints:
    if(po(z,mu)==1):
        a=z
        dem+=1
print('Dem la: {0}'.format(dem))

k = (p-3)//4

z = po(a,k+1)

print(z)
 ~~~

 ---------------------------------------------------------------
 
 #### Chinese Remainder Theorem

 Định lý thặng dư Trung Hoa sẽ cho một nghiệm duy nhất cho tập hợp các đồng dư tuyến tính nếu moduli của chúng nguyên tố cùng nhau từng đôi một.

 Điều này có nghĩa là, có một tập $a_i$ bất kì, và một tập $n_i$ nguyên tố với nhau từng đôi một bất kì thoả mãn hệ đồng dư sau: 

 $x\equiv a_1 \text{ mod }n_1$

 $x\equiv a_2 \text{ mod }n_2$

 ...
 
 $x\equiv a_n \text{ mod }n_n$

 Thì chỉ có duy nhất một nghiệm $x\equiv a \text{ mod }N$ với $N=n_1*n_2...n_n$.

 Trong cryptograph, chúng ta thường sử dụng CRT (Chinese Remainder Theorem) để giúp chúng ta giảm thiểu việc tính toán số lớn thành một tập các số nhỏ hơn, dễ tính toán.

 Cho một hệ đồng dư tuyến tính sau:

 $x\equiv 2 \text{ mod }5$

 $x\equiv 3 \text{ mod }11$

 $x\equiv 5 \text{ mod }17$

 Tìm số nguyên $a$ thoả mãn $x\equiv a \text{ mod }935$

 Ghi chú:

 Để giải bài này, chúng ta sẽ bắt đầu với modulus lớn nhất, sử dụng $x\equiv a \text{ mod }p$, chúng ta có thể viết lại $x=a+k*p$ với $k$ bất kì.

 Lời giải: Bài này, đơn giản ta chỉ việc duyệt trâu $a$ từ $1$ đến $934$ và kiếm tra xe chúng có thoả mãn hệ trên hay không là được

 Code:

 ~~~
 for z in range(1,935):
    if(z%5==2 and z%11==3 and z%17==5):
        print(z)
        break
 ~~~

 --------------------------------------------------------

 ### LATTICES

 #### Vectors

 Trước khi định nghĩa a lattice hay nói về làm thế nào lattices xuất hiện trong cryptography, hãy để chúng tôi review một vài kiến thức cơ bản về linear algebra. Những bài tập dưới đây được xem như là bài tập ôn tập, nếu điều này hoàn toàn mới với bạn, có lẻ bạn nên đọc một chút về kiến thức nền. Thông thường, chúng tôi khuyến nghị "An Introduction to Mathematical Cryptography" by Hoffstein, Pipher, Silverman cũng như thử thách này và những ứng dụng của nó.

 Một không gian vector V trên trường F là một tập được định nghĩa với hai phép toán nhị phân. Với mỗi vector $v\in V$ và một scalar $a\in F$, vector addition takes two vectors and produces another vector: $v+w=z$ for $v,w,z\in V$ and scalar multiplication takes a vector and a scalar and produces a vector: $a*v=w$ for $v,w\in V,a\in F$.

 Ghi chú: Có thể bạn sẽ thấy vector lần đầu tiên của không gian vector hai chiều được xác định trên thực. Chúng tôi sẽ sử dụng điều này để làm ví dụ.

 Chúng ta xét một không gian vector 2 chiều trên số thực. Một vector $v\in V$ có thể được xem như một cặp số: $v=(a,b)$ với $a,b\in \mathbb{R}$. Vector addition hoạt động như sau: $v+w=(a,b)+(c,d)=(a+c,b+d)$, và scalar multiplication được xác định như sau: $c\text{ * }v=c*(a,b)=(c * a,c * b)$

 Một phép toán có thể định nghĩa đó là inner product (also called dot product), cái mà khi ta nhân hai vector với nhau sẽ cho ra một scalar. Một cách hình thức, chúng ta nghĩ về việc đó như sau: $v . w = a$ for $v,w \in V,a\in F$. Ở ví dụ 2 chiều này của chúng ta, the inner product hoạt động như sau: $v.w = (a,b)*(c,d) = a * c + b * d$.

 Bây giờ là đến tìm flag ! Cho không gian vector 3 chiều trên miền số thực, với $v=(2,6,3),w=(1,0,0)$ và $u=(7,7,2)$. Tính $3\text{ * }(2\text{ * }v-w) \cdot 2 \text{ * } u$

 Code:

~~~
def sum(x,y):
    res=[0,0,0]
    for _ in range(0,3):
        res[_]=x[_]+y[_]
    return res
def inner_product(x,y):
    res=0
    for _ in range(0,3):
        res=res+x[_]*y[_]
    return res
def scalar_product(x,z):
    res = [0,0,0]
    for _ in range(0,3):
        res[_] = z * x[_]
    return res
v=[2,6,3]
w=[1,0,0]
u=[7,7,2]

#print(scalar_product(v,3))
fi = scalar_product(sum(scalar_product(v,2),scalar_product(w,-1)),3)
se = scalar_product(u,2)
ans = inner_product(fi,se)
print(ans)
~~~

-------------------------------------------------------

#### Size and Basis

Chúng ta nói một tập vectors $v_1,v_2,...,v_k\in V$ là linearly independent nếu chỉ có một nghiệm xảy ra với phương trình sau:

$a_1 * v_1 + a_2 * v_2 + ... + a_k * v_k = 0$

đó là nghiệm $a_1=a_2=...=a_k=0$

Ghi chú:

~~~
Để hình dùng điều này, hãy nghĩ về một vector chỉ ra một điểm. Cho một tập các vector độc lập tuyến tính, cách duy nhất để quay trở lại điểm ban đầu là di chuyển deo theo vector ban đầu, không có sự kết hợp nào của bất kỳ vector nào khác sẽ đưa bạn đến đó.
~~~

A basis là một tập các vectors độc lập tuyến tính $v_1,v_2,...,v_n\in V$ thoả mãn bất kỳ vector $w\in V$ đều có thể viết được dưới dạng : 

$w = a_1 * v_1 + a_2 * v_2 + ... + a_k * v_n$

Số lượng phần tử trong basis cũng là chiều của không gian vector.

Chúng ta định nghĩa size of vector,kí hiệu là  $\lVert v \rVert$, sử dụng inner product ta có: $\lVert v \rVert ^ 2 = v \cdot v$

A basis is orthogonal if for a vector basis $v_1,v_2,...,v_n\in V$, the inner product between any two different vectors is zero: $v_i\cdot v_j=0,i\ne j$

A basis is orthonormal if it is orthogonal and $\lVert v_i \rVert=1$, for all $i$.

That's a lot of stuff, but we'll be needing it. 

Bây giờ là thời gian để bắt cờ. Cho vector $v=(4,6,2,5)$. Tính size của nó.

Code:

~~~
import math
v = [4,6,2,5]

res = 0

for _ in v:
    res += _*_
print(res)
print(int(math.sqrt(res)))
~~~

----------------------------------------------------------------

#### Gram Schmidt 

Ở challenge trước, chúng ta nhận thấy rằng có một loại basis đặc biệt được gọi là orthogonal basis. Cho một basis $v_1,v_2,...,v_n\in V$ trong không gian vector, thuật toán Gram-Schmidt tính một orthogonal basis $u_1,u_2,...,u_n\in V$

In "An Introduction to Mathematical Cryptography", Jeffrey Hoffstein, Jill Pipher, Joseph H. Silverman, the Gram-Schmidt algorithm is given as:

Thuật toán của Gram-Schmidt

$u_1=v_1$

Loop $i=2,3,...,n$

Compute $\mu_{ij} = v_i \cdot u_j / \lVert u_j \rVert ^ 2,1\le j < i $

Set $u_i = v_i -\sum\limits_{1\le j< i } \mu_{ij} * u_j$ 

End loop

Để kiểm tra code của bạn, cho một basis sau:

$v1 = (4,1,3,-1), v2 = (2,1,-3,4), v3 = (1,0,-2,7), v4 = (6, 2, 9, -5)$

sử dụng thuật toán Gram-Schmidt để xác định orthogonal basis. Cờ là giá trị thập phân của thành phần thứ hai của $u_4$ chính xác đến chữ số thập phân thứ 5.

Code:

~~~
from array import *
def inner_product(x,y):
    res = 0
    for _ in range(4):
        res=res+x[_]*y[_]
    return res
def size_of_vector(v):
    return inner_product(v,v)
def add_vector(x,y):
    res = [0]*4
    for _ in range(4):
        res[_]=x[_]+y[_]
    return res
def scalar_multiple(scala,v):
    for _ in range(4):
        v[_]*=scala
    return v 
fi = [1,2,3,4]
se = [1,2,3,4]

v=[[4,1,3,-1],[2,1,-3,4],[1,0,-2,7],[6, 2, 9, -5]]
u=[[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
muy = [[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
u[0] = [4,1,3,-1]
print(u)
for i in range(1,4):
    for j in range(0,i):
        muy[i][j] = inner_product(v[i],u[j]) / size_of_vector(u[j])
    tmp=[0,0,0,0]
    for j in range(0,i):
        tmp = add_vector(tmp,scalar_multiple(muy[i][j],u[j]))
    tmp = scalar_multiple(-1,tmp)
    u[i]=add_vector(v[i],tmp)
print(u[3])

~~~

-------------------------------------------------

#### What's a Lattice ?

Bây giờ chúng ta sẽ bắt đầu nói về lattices. Cho một tập linearly independent vectors $v_1,v_2,...,v_n \in \mathbb{R}^{m}$, the lattice $L$ generated by $v_1,v_2,...,v_n$ is the set of linearly independent vectors $v_1,v_2,...,v_n$ with integer coefficients.

$L=${$a_1 * v_1 + a_2 * v_2 +...+a_k * v_k : a_1,a_2,...,a_n\in \mathbb{Z}$}

The basis for the lattice $L$ is any set of independent vectors that generates $L$. The choice of basis is far from unique. In the image below, we show a two dimension lattice with two different basis vectors given by $u_1,u_2$ and $v_1,v_2$.

![Imgur](https://i.imgur.com/M6gM8yo.png)

Using a basis, we can reach any point within the lattice with integer multiples of basis vectors. The basis vectors also define the function domain:

$F(v_1,...,v_n)=${$t_1v_1+t_2v_2+...+t_nv_n: 0\le t_i<1$}.

As a two dimensional example, the fundamental domain is the parallelogram with sides $u_1$ and $u_2$.

We can calculate the volume of the fundamental domain from the basis vectors. As an example, let us take a two dimensional lattice with basis vectors $v=(2,5),u=(3,1)$. Create a matrix $A$ with rows corresponding to the basis vectors: $A=[[2,5],[3,1]]$. The volume of the fundamental domain is the magnitude of the determinant of $A:Vol(F)= \lvert det(A) \rvert = \lvert 2 * 1-5 * 3 \rvert=\lvert -13 \rvert=13.$

For the flag, calculate the volumne of the fundamental domain with the basis vectors: $v_1=(6,2,-3),v_2=(5,1,4),v_3=(2,7,1)$.

Cấu trúc lệnh cài đặt pyPi( matplotlib , numpy) in Windows:

~~~
python -m pip install matplotlib
~~~

Link tham khao: [Link](https://code.visualstudio.com/docs/python/python-tutorial)

Code:

~~~
import numpy as np 
a = np.array([[6,2,-3],[5,1,4],[2,7,1]])
d = np.linalg.det(a)
print(d)
~~~

------------------------------------------------------------------------

#### Gaussian Reduction

If you look closely enough, lattices start appearing everywhere in cryptography. Sometimes they appear through manipulation of a cryptosystem, breaking parameters which were not generated securely enough. The most famous example of this is Coppersmith's attack against RSA cryptography.

Lattices can also be used to build cryptographic protocols, whose secutiry is based on two fundamental "hard" problems:

The "Shortest Vector Problem(SVP)": find the shortest non-zero vector in a lattice L. In other words, find the non-zero vector within $v\in L$ such that $\lVert v\rVert$ is minimised.

The "Closest Vector Problem(CVP)": Given a vector $w\in \mathbb{R}^m$ that is not in $L$, find the vector $v\in L$ that is the closest to $w$,i,e find the vector $v\in L$ such that $\lVert v-w \rVert$ is minimised.

The SVP is hard for a generic lattice, but for simple enough cases there are efficient algorithms to compute either a solution or an approximation for the SVP. When the dimension of the lattices is four or less, we can compute this exactly in polynomial time; for higher dimensions, we have to settle for an approximation.

Gauss developed his algorithm to find an optimal basis for a two-dimensional lattice given an arbitrary basis. Moreover, the output $v_1$ of the algorithm is a shortest nonzero vector in $L$, and so solves the $SVP$.

Ghi chú: 

~~~
For higher dimensions, there's a basis lattice reduction algorithm called the LLL algorithm, named after Lenstra, Lenstra and Lovasz. If you play CTFs regularly, you'll already know about it. The LLL algorithm runs in polynomial time. For now though, lets stay in two dimensions.
~~~

Gauss's algorithm roughly works by suntracting multiples of one basis vector from the other until it's no longer possible to make them any smaller. As this works in two-dimensions, it's nice to visualise. Here's a description of the algorithm from "An introduction to Mathematical Cryptography",  Jeffrey Hoffstein, Jill Pipher, Joseph H. Silverman:

Algorithm for Gaussian Lattice reduction

Loop

(a) If $\lVert v1 \rVert < \lVert v2 \rVert$, swap v1,v2

(b) Compute m = floor(v1.v2/v1.v1)

(c) If m=0, return v1,v2

(d) v2 = v2 - m*v1

Continue Loop

Note the similarity to Euclid's GCD algorithm with the "swap" and "reduction" steps, and that we have to use the floor, as on a lattice we may only use integer cofficients for our basis vectors.

For the flag, take the two vectors $v=(846835985, 9834798552),u=(87502093, 123094980)$ and by applying Gauss's algorithm, find the optimal basis. The flag is the inner product of the new basis vectors.

This is my code:

~~~
import math
def inner_product(x,y):
    res = 0
    for _ in range(2):
        res=res+x[_]*y[_]
    return res
def size_of_vector(v):
    return inner_product(v,v)

def add_vector(x,y):
    res = [0]*2
    for _ in range(2):
        res[_]=x[_]+y[_]
    return res
def scalar_multiple(scala,v):
    for _ in range(2):
        v[_]*=scala
    return v 
def compute_m(x,y):
    return inner_product(x,y)//inner_product(x,x)
# Thuat toan khu Gauss
v1 = [846835985,9834798552]
v2 = [87502093,123094980]
while(True):
    if size_of_vector(v2)<size_of_vector(v1):
        tmp = v1
        v1 = v2
        v2 = tmp
    m = compute_m(v1,v2)
    if(m==0):
        break 
    else:
        v2[0] = v2[0] - m*v1[0]
        v2[1] = v2[1] - m*v1[1]
ans = inner_product(v1,v2)
print(ans)
~~~

-------------------------------------------------------

Find the lattice

As we've seen, lattices contain hard problem which can form trapdoor functions for cryptosystems. We also find that in cryptanalysis, lattices can break cryptographic protocols which seem at first to be unrelated to lattices.

This challenges uses modular arithmetic to encrypt the flag, but hidden within the protocol is a two-dimensional lattice. We highly recommend spending time with this challenge and finding how you can break it with a lattice. This is a famous example with plenty of resources available, but knowing how to sport the lattice within a system is often the key to breaking it.

As a hint, you will be able to break this challenge using Gaussian reduction from the previous challenge

Chua giai duoc

----------------------------------------------------------------------------------

### BLOCK CIPHERS

#### Keyed Permutations 

AES (Advanced Encryption Standard), like all good ciphers, performs a "keyed permutation". This means that it maps every possible input block to a unique output block, with a key determining w
Đáp án của bài này là: 

~~~
crypto{bijection}
~~~

#### Resisting Bruteforce



