---
layout: post
title: Học jsp và servlet cơ bản
subtitle: jsp và servlet
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [jsp,servlet]

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

## Bài 1. Giới thiệu về Java Servlet


![Imgur](https://i.imgur.com/4l8xhZP.png)

Hình 1. 

![Imgur](https://i.imgur.com/huX6C5y.png)

Hình 2.

![Imgur](https://i.imgur.com/Npwwgvm.png)

Hình 3.

![Imgur](https://i.imgur.com/rqMhZhj.png)

Hình 4.

![Imgur](https://i.imgur.com/W11zHoa.png)

## Bài 2. Thiết lập môi trường Java Servlet - Tomcat 8

![Imgur](https://i.imgur.com/xMuUc6y.png)

Hình 1. Search google Tomcat và chọn Tomcat 8

![Imgur](https://i.imgur.com/Puyf4Ll.png)

Hình 2. Chọn phiên bản 8.0.41

![Imgur](https://i.imgur.com/N34LjDN.png)

HÌnh 3. Chọn file zip để tải về

![Imgur](https://i.imgur.com/YOgfDGc.png)

Hình 4. Vào Window -> Show View -> Others 

![Imgur](https://i.imgur.com/ivY3q6d.png)

Hình 5. Tiếp theo gõ server -> Chọn Servers

![Imgur](https://i.imgur.com/WhdaZBd.png)

Hình 6. Khi đó sẽ hiện thị mục servers như trên ảnh

![Imgur](https://i.imgur.com/qThywsQ.png)

HÌnh 7. Click chuột phải -> Chọn New -> Chọn Servers -> 

![Imgur](https://i.imgur.com/DgNOcS8.png)

Hình 8. Chọn Tomcat v8.0 Server

![Imgur](https://i.imgur.com/Y23RiYx.png)

Hình 9. Chọn tên cho Server's host name và Server name  và bấm next

![Imgur](https://i.imgur.com/JWIHtSv.png)

Hình 10. Sau đó chúng ta sẽ bấm vào Browser để chọn file Tomcat vừa mới tải lúc nãy (file đã giải nén nhé !)

![Imgur](https://i.imgur.com/nIn49zY.png)

Hình 10. Chọn thư mục đã giải nén sau đó bấm open và chọn finish

![Imgur](https://i.imgur.com/oZ3LFeg.png) 

Hình 11. Khi đó chúng ta sẽ thấy folder server đã xuất hiện

## 3. Chu kỳ sống của Servlet và ví dụ Hello Servlet 

![Imgur](https://i.imgur.com/cTb34nu.png)

Hình 1. Mô tả chu kỳ sống của servlet

![Imgur](https://i.imgur.com/gMlJUQ0.png)

Hình 2. Tạo một dynamic Web Project

![Imgur](https://i.imgur.com/aElgCI9.png)

Hình 3. Chọn tên project và bấm next

![Imgur](https://i.imgur.com/Oif6bom.png)

Hình 4. Bấm next

![Imgur](https://i.imgur.com/g1MOVv2.png)

Hình 5. Bấm tick và ô generate.... (phải bấm) sau đó bấm Finish

![Imgur](https://i.imgur.com/yUJjad9.png)

Hình 6. Mở file web.xml

![Imgur](https://i.imgur.com/j8NKnRY.png)

Hình 7. Vào src -> Tạo một package có tên là com.trungtamjava

![Imgur](https://i.imgur.com/l8SPF1j.png)

Hình 8. Trong package tạo class có tên HelloServlet.java

![Imgur](https://i.imgur.com/xgs7HLo.png)

Hình 9. Trong file HelloServlet.java chúng ta extends HttpServlet 

![Imgur](https://i.imgur.com/JaYcj9t.png)

Hình 10. Tạo hàm init()

![Imgur](https://i.imgur.com/UEWwiLX.png)

Hình 11. Tạo thêm hàm destroy

![Imgur](https://i.imgur.com/MJa05mG.png)

Hình 12. Gọi các hàm service và doget 

![Imgur](https://i.imgur.com/htY3CKp.png)

Hình 13. Vào file web.xml để cấu hình thêm cho file servlets

![Imgur](https://i.imgur.com/DE63Eie.png)

Hình 14. Chúng ta nhân giữ phím Ctrl và click chuột để hiển thị file class tương ứng

![Imgur](https://i.imgur.com/ClPeVZ8.png)

Hình 15. Tạo servlet mapping 

![Imgur](https://i.imgur.com/aXrXhtl.png)

Hình 16. Click chuột phải vào Tomcat 8 và chọn Add and remove

![Imgur](https://i.imgur.com/dlY7lDK.png)

Hình 17. Chọn HelloServlet -> Add -> Finish

![Imgur](https://i.imgur.com/CFrGy4K.png)

Hình 18. Sau đó ta click chuột phải vào Tomcat 8 --> Clean

![Imgur](https://i.imgur.com/1TPtuM8.png)

Hình 19. click chuột phải vào Tomcat 8 --> start

![Imgur](https://i.imgur.com/IAAzp4g.png)

Hình 20. Lên trình duyệt và gõ link như hình vẽ ta sẽ thấy được kết quả như mong muốn 

![Imgur](https://i.imgur.com/HDNLMYS.png)

Hình 21. Phương trình request là GET

![Imgur](https://i.imgur.com/wauxlb9.png)

Hình 22. Khi ta stop server thì hàm destroy sẽ được gọi







