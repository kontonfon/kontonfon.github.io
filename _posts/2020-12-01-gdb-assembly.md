---
layout: post
title: Một số lệnh thường gặp khi debug C hoặc C++ sang Assembly trong Linux
subtitle: GDB
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [debug,gdb]

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

## 1.Tạo một file bất kì

Cú pháp:

~~~
nano exv.c
~~~

![Imgur](https://i.imgur.com/fmaqjzw.png)

## 2. Thực thi file đã tạo

Cú pháp:

~~~
gcc -g exv.c -o t
~~~

## 3. Chạy file đã thực thi

Cú pháp :

~~~
./t
~~~

## 4. Liệt kê các thư mục

Cú pháp:

~~~
ls -la
~~~

## 5. Thực hiện Debug 

![Imgur](https://i.imgur.com/iUz0s05.png)

Cú pháp:

~~~
gdb t
~~~

------------------------------

## Các lệnh trong quá trình debug

### 1. Liệt kê các câu lệnh C

![Imgur](https://i.imgur.com/xYivOmA.png)

Cú pháp:

~~~
list
~~~

### 2. Đặt breakpoint

Cú pháp: 

~~~
b main
~~~

### 3. Xem thông tin breakpoint

Cú pháp:

~~~
info b
~~~

### 4. Triển khai sang assembly

![Imgur](https://i.imgur.com/3SHXOEw.png)

Cú pháp: 

~~~
disass
~~~

### 5. Chuyển con trỏ debug sang dòng tiếp theo

Cú pháp :

~~~
nextin
~~~

### 6 . In giá trị các biến ra xem kiểm tra

![Imgur](https://i.imgur.com/AuWgMEa.png)

Cú pháp : 

~~~
print a
~~~

### 7. Hiển thị thông tin của các thanh ghi

![Imgur](https://i.imgur.com/njooF9W.png)

Cú pháp: 

~~~
info reg
~~~

### 8. Thoát khỏi debug

Cú pháp: 

~~~
q
~~~