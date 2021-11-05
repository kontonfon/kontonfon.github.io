---
layout: post
title: Express JS and Heroku
subtitle: paper, web
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

Dựa trên hướng dẫn của trang [này](https://www.freecodecamp.org/news/how-to-deploy-your-site-using-express-and-heroku/), mình muốn note lại một số thứ để sau này sử dụng 

#### Bước 1: Tạo một repo trên github của bạn nhé ! 

![Imgur](https://i.imgur.com/asFb0bj.png)

#### Bước 2: Bạn git clone về ở local nhé ! 

![Imgur](https://i.imgur.com/EJ2ZDDi.png)

#### Bước 3: Các bạn cd vào thư mục với tên project bạn đã tạo nhé ! 

![Imgur](https://i.imgur.com/4gZoBYJ.png)

#### Bước 4: Các bạn vào trang chủ của Heroku, tạo một account free để sử dụng nhé, sau đó vào CLI gõ lệnh `heroku login -i` để đăng nhập

![Imgur](https://i.imgur.com/cBwl7Ct.png)

#### Bước 5: Ta sẽ tạo một project trên heroku nhé  với câu lệnh `heroku create <yournameproject>`

![Imgur](https://i.imgur.com/DnCc4iK.png)

#### Bước 6: Sau khi tạo xong rồi, ta bắt đầu build web của chúng ta nhé, trước hết ta sử dụng lệnh `npm init -y` để cái packets

![Imgur](https://i.imgur.com/ahoJ9Nm.png)

#### Sau khi cài xong, ta sẽ thấy một file json để ta config, tiếp tục ta cài `Express` với câu lệnh `npm install express --save` nhé ! 

![Imgur](https://i.imgur.com/xMk8wj3.png)

#### Tiếp theo, ta sẽ tạo file `app.js` để tiến hành build project của chúng ta, đối với window chúng ta có thể sử dụng câu lệnh: `type nul > app.js` hoặc đối với Linux, các bạn có thể dùng `touch app.js` nhé ! 

![Imgur](https://i.imgur.com/y8vjteI.png)

#### Tiếp theo, ta sẽ tiến hành code một số cái cơ bản nhất trong file `app.js` nhé ! 

```javascript
// create an express app

const express = require("express")
const app = express()

// use the express-static middle ware

app.use(express.static("public"))

// define the first route

app.get("/",function(req,res){
    res.send("<h1>Hello World!")
})

// start the server listening for requests 

app.listen(process.env.PORT || 3000, ()=> console.log("Server is runnning..."))
```

#### Bước 10. Tiếp theo, ta sẽ chạy app trên local với câu lệnh `node app.js` và sau đó truy cập : `localhost:3000` bạn sẽ thấy kết quả hiện ra:

![Imgur](https://i.imgur.com/QomrWWz.png)

#### Bước 11: Chúng ta sẽ tiến hành thêm `npm start` bằng cách config lại file json ban đầu một chút nhé ! :

![Imgur](https://i.imgur.com/eVaxkm9.png)

Ps: Các bạn thêm dòng lệnh `"start":"node app.js"` vào `script`, và có thể test lại trên CLI bằng câu lệnh `npm start`

![Imgur](https://i.imgur.com/vPDoTqi.png)

#### Bước 12: Để app này chạy trên được Heroku, chúng ta phải thêm file `Procfile`, file này sẽ có chứng năng giúp cho server nhận diện được script cần để build, cụ thể các bạn dùng lệnh như sau: `type nul > Procfile`

![Imgur](https://i.imgur.com/X7T82wq.png)

Và ta tiếp tục chèn các dòng lệnh : `web: node app.js` vào file `Procfile` này !

#### Bước 13: Tiếp theo, để trang web thêm sinh động, ta có thể thêm các file HTML, CSS và JS vào app trên bằng cách tạo ra thư mục public, và tạo ra thêm các file HTML, CSS và JS vào trong nó

![Imgur](https://i.imgur.com/GtKysGU.png)

![Imgur](https://i.imgur.com/04uAtFd.png)

#### Tiếp theo, ta sẽ code trang trí web trong này nhé ! 

- index.html

```html
<!DOCTYPE html>
<head>
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
	<link href="https://fonts.googleapis.com/css?family=Alegreya|Source+Sans+Pro&display=swap" rel="stylesheet">
	<link rel="stylesheet" type="text/css" href="styles.css">
</head>
<html>
<body>
<h1>Lorem Ipsum generator</h1>
  <p>How many paragraphs do you want to generate?</p>
  <input type="number" id="quantity" min="1" max="20" value="1">
  <button id="generate">Generate</button>
  <button id="copy">Copy!</button>
<div id="lorem">
</div>
<script type="text/javascript" src="script.js"></script>
</body>
</html>
```

- styples.css

```css
h1 {
	font-family: 'Alegreya' ;
}

body {
	font-family: 'Source Sans Pro' ;
	width: 50%;
	margin-left: 25%;
	text-align: justify;
	line-height: 1.7;
	font-size: 18px;
}

input {
	font-size: 18px;
	text-align: center;
}

button {
	font-size: 18px;
	color: #fff;
}

#generate {
	background-color: #09f;
}

#copy {
	background-color: #0c6;
}
```
- script.js

```js
$("#generate").click(function(){
	var lorem = $("#lorem");
	lorem.html("");
	var quantity = $("#quantity")[0].valueAsNumber;
	var data = ["Lorem ipsum", "quia dolor sit", "amet", "consectetur"];
	for(var i = 0; i < quantity; i++){
		lorem.append("<p>"+data[i]+"</p>");
	}
})

$("#copy").click(function() {
	var range = document.createRange();
	range.selectNode($("#lorem")[0]);
	window.getSelection().removeAllRanges();
	window.getSelection().addRange(range);
	document.execCommand("copy");
	window.getSelection().removeAllRanges();
	}
)
```

Sau đó, các bạn chạy lại và thấy được kết quả như thế này:

![Imgur](https://i.imgur.com/DUN0ILi.png)

#### Bước 15: Chúng ta sẽ tiến hành deploy trên heroku nhé ! 

Chúng ta thực hiện các lệnh sau:

~~~
git add .
git commit -m "your comment"
~~~

và sau đó là:

~~~
git push heroku main
~~~

#### Bước 16: Các bạn có thể sử dụng câu lệnh `heroku logs --tail` để xem lịch sử log trên server của heroku nhé !

- Nếu bạn thấy `starting to crashed`: Tức là ta chưa thành công nhé :v 

![Imgur](https://i.imgur.com/dC5e5TI.png)

- Thì sau một hồi edit, một điều chú ý khi ta ghi ở file `Profile` đó là: `web: node app.js`

- Và sau khi fix xong, ta có thể dùng lệnh `heroku open` để chạy thử, và kết quả thật bất ngờ đó là: 

![Imgur](https://i.imgur.com/5LvWuba.png)

và để kiểm tra lần nữa cho chắc chắn, ta có thể sử dụng lệnh `heroku logs --tail` để xem sự thành công khi build 1 trang lên heroku nhé !:

![Imgur](https://i.imgur.com/vHoWMdr.png)

OKIE, ta thấy `starting to up`, tức là lúc này ta đã hoàn tất !! 

#### Lời kết, cuối cùng việc heroku đã hoàn tất, xin cảm ơn các bạn đã quan tâm theo dõi ! 

#### Ngoài ra để có thể fix lại, thì bạn chỉ cần fix trong này là được nhé ! Bye Bye !

#### Code tham khảo [Link](https://github.com/kontonfon/note_express_js)





