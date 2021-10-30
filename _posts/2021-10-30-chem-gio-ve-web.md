---
layout: post
title: Vi vu về web
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

Hôm nay rãnh rỗi, lên mạng học về những cái căn bản cũng như những thứ ẩn dụ hay ho về web, nên mình viết blog này để lưu lại những kỉ niệm

## Phần 1: Web hoạt động như thế nào ?

Blog này mình viết dựa trên [How the Web works](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works?retiredLocale=vi) nên có gì các bạn có thể tham khảo thêm tại trang gốc nhé ! 

Nào , bắt đầu thôi ! 

`How the web works` cung cấp cho ta một cái nhìn đơn giản về những gì xảy ra khi bạn xem một trang web trong trình duyệt web trên máy tính hoặc điện thoại của mình.

Lý thuyết này không cần thiết đề viết mã web trong ngắn hạn, nhưng trước mắt bạn sẽ thực sự bắt đầu hưởng lợi từ việc hiểu những gì đang xảy ra trong nền tảng của nó.

### Clients và Servers

Máy tính kết nối với web được gọi là `clients` và `servers`. Một sơ đồ đơn giản về cách chúng tương tác vó thể trông như thế này:

![Imgur](https://i.imgur.com/YLRu3eL.png)

+ `Clients` là thiết bị được kết nối internet của người dùng web điển hình (ví dụ: máy tính được kết nối với wi-fi của bạn hoặc điện thoại được kết nối với mạng di động của bạn) và phần mềm truy cập web có sẵn trên các thiết bị đó (thường là trình duyệt web như firefox hoặc Chrome)

+ `Servers` là máy tính lưu trữ các trang, trang web hoặc ứng dụng. Khi thiết bị khách muốn truy cập một trang web, một bản sao của trang web được tải xuống từ máy chủ vào máy khách để hiển thị trong trình duyệt web của người dùng.

### The other parts of the toolbox

Máy khách và máy chủ mà chúng tôi đã mô tả ở trên không kể toàn bộ câu chuyện. Có nhiều phần khác liên quan và chúng tôi sẽ mô tả chúng bên dưới.

Bây giờ, hãy tưởng tượng rằng web là một con đường. Ở một đầu của con đường là khách hàng, giống như ngôi nhà của bạn. Ở đầu kia là con đường là máy chủ, là cửa hàng bạn muốn mua thứ gì đó.

![Imgur](https://i.imgur.com/RoOa556.png)

Ngoài máy khách và máy chủ, chúng ta cũng cần gửi lời chào đến:

+ `Your internet connection`: Cho phép bạn gửi và nhận dữ liệu trên web. Về cơ bản nó giống như con đường giữa nhà của bạn và cửa hàng.

+ `TCP/IP`: Giao thức điều khiển và Giao thức internet là các giao thức truyền thông xác định cách dữ liệu sẽ truyển trên internet. Điều này giống cơ chế vận chuyển cho phép bạn đặt hàng, đến cửa hàng và mua hàng hoá của mình. Trong ví dụ của chúng tôi, điều này giống như một chiếc ô tô hoặc một chiếc xe đạp (hoặc tuy nhiên, bạn có thể đi xung quang khác)

+ `DNS`: Máy chủ tên miền giống như một sổ địa chỉ cho các trang web. Khi bạn nhập địa chỉ web vào trình duyệt của mình, trình duyệt sẽ nhìn vào DNS để tìm địa chỉ thực của trang web trước khi có thể truy xuất trang web. Trình duyệt cần tìm ra máy chủ mà trang web đang sống, để có thể gửi thông điệp HTTP đến đúng nơi (xem bên dưới). Việc này giống như việc tra cứu địa chỉ của shop để bạn có thể truy cập.

+ `HTTP`: Giao thức truyền siêu văn bản là một giao thức ứng dụng xác định ngôn ngữ để máy khách và máy chủ nói chuyện với nhau. Đây giống như ngôn ngữ bạn sử dụng để đặt hàng.

+ `Components files`: Một trang web được tạo thành từ nhiều tệp khác nhau, chúng giống như các phần khác nhau của hàng hoá bạn mua từ cửa hàng. Các tệp này có hai loại chính:

 + `Code files`: Các trang web được xây dựng chủ yếu từ HTML, CSS và JavaScript, mặc dù bạn sẽ gặp các công nghệ khác sau đó một chút

 + `Assets`: Đây là tên chung cho tất cả các nội dung khác tạo nên một trang web, chẳng hạn như hình ảnh, nhạc, video, tài liệu word và PDF

### So what happens, exactly ?

Khi bạn nhập địa chỉ web vào trình duyệt của mình (ví dụ của chúng tôi, giống như đi bộ đến của hàng):

1. Trình duyệt chuyển đến máy chủ DNS và tìm địa chỉ thực của máy chủ mà trang web đang tồn tại (bạn tìm địa chỉ của cửa hàng)

2. Trình duyệt sẽ gửi một thông báo yêu cầu HTTP đến máy chủ, yêu cầu nó gửi một bản sao của trang web cho khách hàng (bạn đến của hàng và đặt hàng của bạn). Thông báo này và tất cả dữ liệu khác được gửi giữa máy khách và máy chủ, được gửi qua kết nối internet của bạn bằng `TCP/IP`

3. Nếu máy chủ chấp thuận yêu cầu của khách hàng, máy chủ sẽ gửi cho máy khách một thông báo `200 OK`, có nghĩa là "Tất nhiên bạn có thể xem trang web đó! Here it is" và sau đó bắt đầu gửi các tệp của trang web đến trình duyệt dưới dạng một loạt các phần nhỏ được gọi là gói dữ liệu (cửa hàng giao hàng cho bạn và bạn mang hàng về nhà).

4. Trình duyệt tập hợp các phần nhỏ thành một trang web hoàn chỉnh và hiện thị nó cho bạn (hàng đã đến cửa nhà bạn- thứ sáng bóng mới, thật tuyệt !)

### Order in which component files are parsed (Thứ tự các tệp thành phần được phân tích cú pháp)

Khi trình duyệt gửi yêu cầu đến máy chủ cho các tệp `HTML`, các tệp `HTML` đó thường chứa các phần thử `link` tham chiếu đến các bảng định kiểu `CSS` bên ngoài và các phần tử `script` tham chiếu đến các tập lệnh `JavaScript` bên ngoài.

Điều quan tọng là phải biết thứ tự mà các tệp đó được trình duyệt phân tích cú pháp khi trình duyệt tải trang.

+ Trình duyệt phân tích cú pháp tệp `HTML` trước tiên và điều đó dẫn đến trình duyệt nhận ra bất kỳ tham chiếu `link` nào tới bảng định kiểu CSS bên ngoài và mọi tham chiếu `script` tới tập lệnh

+ Khi trình duyệt phân tích cú pháp HTML, nó sẽ gửi yêu cầu trở lại máy chủ đối với bất kỳ tệp `CSS` nào mà nó đã tìm thấy từ các phần tử `link` và bất kỳ tệp `CSS` nào mà nó đã tìm thấy từ các phần tử `script` và từ những tệp đó, sau đó phân tích cú pháp `CSS` và `JavaScript`

+ Trình duyệt tạo cây `DOM` trong bộ nhớ từ `HTML` được phân tích cú pháp, tạo cấu trúc `CSSOM` trong bộ nhớ từ `CSS` được phân tích cú pháp, biên dịch và thực thi `JavaScript` đã được phân tích cú pháp.

+ Khi trình duyệt xây dựng cây `DOM` và áp dụng các kiểu từ cây `CSSOM` và thực thi `JavaScript`, phần rình bày trực quan của trang được vẽ trên màn hình và người dùng nhìn thấy nội dung trang và có thể bắt đầu tương tác với nó.

### DNS explained.

Địa chỉ web thực không phải là những chuỗi đẹp, dễ nhớ mà bạn nhập vào thành địa chỉ để tìm các trang web yêu thích của mình, Chúng là những con số đặc biệt có dạng như sau: `63.245.215.20`

Đây được gọi là địa chỉ IP và nó đại diện cho một vị trí duy nhất trên web. Tuy nhiên, nó không phải là rất dễ nhớ, phải không ? Đó là lý do tại sao máy chủ tên miền được phát minh. Đây là những máy chủ đặc biệt khớp địa chỉ web bạn đang nhập vào trình duyệt của mình (như `mozilla.org`) với địa chỉ `IP` thực của trang web.

Các trang web có thể được truy cập trực tiếp qua địa chỉ IP của chúng. Bạn có thể tìm thấy địa chỉ IP của một trang web bằng cách nhập tên miền của nó vào một công cụ như Trình kiểm tra IP

### Packets explained

Trước đó, chúng tôi đã sử dụng thuật ngữ "gói" để mô tả định dạng dữ liệu được gửi từ máy chủ đến máy khách. Chúng tôi muốn nói gì ở đây ? Về cơ bản, khi dữ liệu được gửi trên web, nó sẽ được gửi theo hàng nghìn phần nhỏ. Có nhiều lý do tại sao dữ liệu được gửi trong các gói nhỏ. Đôi khi chúng bị rơi hoặc bị hỏng và việc thay thế các khối nhỏ sẽ dễ dàng hơn khi điều này xảy ra. Ngoài ra, các gói tin có thể được định tuyến theo các đường dẫn khác nhau, làm cho việc trao đổi nhanh hơn và cho phép nhiều người dùng khác nhau tải xuống cùng một trang web một lúc. Nếu mỗi trang web được gửi dưới dạng một doạn lớn duy nhất, chỉ có một người dùng có thể tải nó xuống tại một thời điểm, điều này rõ ràng sẽ làm cho trang web trở nến rất kém hiệu quả và không thú vị khi sử dụng.

----------------------------------------

## Phần 2: Getting started with the Web

`Getting started with the Web` là một loạt bài ngắn gọn giới thiệu cho bạn những thực tế của việc phát triển web. Bạn sẽ thiết lập các công cụ cần thiết để tạo một trang web đơn giản và xuất bản mã đơn giản của riêng bạn.

### The story of your first website

Việc tạo ra một trang web chuyển nghiệp còn rất nhiều công việc, vì vậy nếu bạn mới bắt đầu phát triển web, chúng tôi khuyến khích bạn nên bắt đầu từ quy mô nhỏ. Bạn sẽ khoogn xây dựng một Facebook khác ngay lập tức, nhưng không khó để tạo trang web đơn giản của riêng bạn trực tuyến, vì vậy chúng ta sẽ bắt đầu ở đó.

Bằng cách làm việc thông qua các bài viết được liệt kê dưới đây, bạn sẽ từ con số không để đưa trang web đầu tiên của mình lên mạng. Hãy bắt đầu cuộc hành trình của chúng ta ! 

#### Installing basic Software

Khi nói đến các công cụ để xây dựng một trang web, có rất nhiều thứ để bạn lựa chọn. Nếu mới bắt đầu, bạn có thể bối rối trước hàng loạt các trình soạn thảo mã, khung công tác và công cụ kiểm tra ngoài kia. Trong `Installing basic software` , chúng tôi sẽ hướng dẫn bạn từng bước cách cài đặt phần mềm bạn cần để bắt đầu một số phát triển web cơ bản và cách cài đặt chúng đúng cách.

##### What tools do the professionals use ? 

+ `A computer`: Có thể điều đó nghe rõ ràng đối với một số người nhưng một số bạn đang đọc bài viết này trên điện thoại hoặc máy tính của thư viện. Để phát triển web nghiêm túc, tốt hơn bạn nên đầu tư vào một máy tính để bàn hoặc máy tính xách tay chạy windows, macOS hoặc Linux.

+ `A texteditor`, để viết mã, đây có thể là một trình soạn thảo văn bản (Ví dụ : `Visual Sutdio Code`, `Notepad++`, `Sublime Text`, `Atom`, `GNU Emacs` hoặc `Vim`) hoặc một trình soạn thảo kết hợp (Ví dụ `Dreamweaver` hoặc `WebStorm`). Các trình chỉnh sửa tài liệu Office không thích hợp cho việc sử dụng này, vì chúng dựa vào các yếu tố ẩn gây trở ngại cho các công cụ kết xuất được sử dụng bởi các trình duyệt web.

+ `Web browser`, để kiểm tra mã. Hiện tại, các trình duyệt được sử dụng nhiều nhất là `Firefox`, `Chrome`, `Opera`, `Safari`, `Internet Explorer` và `Microsoft Edge`. Bạn cũng nên kiểm tả cách trang web của mình hoạt động trên thiết bị di động và trên bất kỳ trình duyệt cũ nào mà đối tượng mục tiêu của bạn có thể vấn đang sử dụng (chẳng hạn như `IE 8-10 Lynx`), một trình duyệt web đầu cuối dựa trên văn bản, rất tốt để xem trang web của bạn được người dùng khiếm thị trải nghiệm như thế nào. ! 

+ `A graphics editors`, như `HIMP`, `figma`, `Paint.NET`, `Photoshop`, `Sketch` hoặc `XD` để tạo hình ảnh hoặc đồ hoạ cho các trang web của bạn.

+ `A version control system`, để quản lý tệp trên máy chủ, cộng tác trong một dự án với nhóm ,chia se mã và nội dung và tránh xung đột chỉnh sửa. Hiện tại, `Git` là hệ thống kiểm soát phiên bản phổ biến nhất cùng với dịch vụ lưu trữ `GitHub` hoặc `GitLab`

+ `An FTP program`, được sử dụng trên các tài khoản lưu trữ web cũ hơn để quản lý tệp trên máy chủ (Git đang ngày càng thay thế FTP cho mục dích này). Có rất nhiều chương trình `(S)FTP` có sẵn bao gồm `Cyberduck`, `Fetch` và `FileZilla`

+ `An automation system`, như `Webpack`, `Grunt` hoặc `Gulp` để tự động thực hiện các tác vụ lặp đi lặp lại, chẳng hạn như rút gọn mã và chạy thử nghiệm.

+ Thư viện, frameworks,... để tăng tốc độ viết chức năng chung. Thư viện có xu hướng là một tệp JavaScript hoặc CSS hiện có cung cấp chức năng cuốn sẵn để bạn sử dụng trong mã của mình. Một framework có xu hướng đưa ý tưởng này đi xa hơn, cung cấp một hệ thống hoàn chỉnh với một số cú pháp tuỳ chỉnh để bạn viết một ứng dụng web.

+ Nhiều công cụ khác bên cạnh

To be contined : https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Installing_basic_software






















