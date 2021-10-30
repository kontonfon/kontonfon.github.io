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

#### What tools do I actually need, right now ? 

Đó trông giống như một danh sách đáng sợ, nhưng may mắn thay, bạn có thể bắt đầu phát triển web mà không cần biết gì về hầu hết những thứ này. Trong bài viết này, chúng tôi sẽ chỉ thiết lập cho bạn mức tối thiểu - một trình soạn thảo văn bản và một số trình duyệt web hiện đại.

##### Installing a text editor

Bạn có thể đã có một trình soạn thảo văn bản cơ bản trên máy tính của mình. Theo mặc định, Windows bao gồm `Notepad` và macOS đi kèm với `TextEdit`. Các bản phân phối Linux khác nhaul Ubuntu đi kèm với `gedit` theo mặc định.

Đối với phát triển web, bạn có thể làm tốt hơn `Notepad` hoặc `TextEdit`. Chúng tôi khuyên bạn nên bắt đầu với `Visual Studio`, đây là một trình chỉnh sửa miễn phí, cung cấp các bản xem trước trực tiếp và gợi ý mã.

##### Installing modern web browser.

Hiện tại, chúng tôi sẽ cài đặt một số trình duyệt web dành cho máy tính để bàn để kiểm tra mã của chúng tôi. Chọn hệ điều hành của bạn bên dưới và nhấp vào liên kết có liên quan để tải xuống trình cài đặt cho các trình duyệt yêu thích của bạn:

+ Linux: `Firefox`, `Chrome`, `Opera`, `Brave`

+ Windows: `Firefox`, `Chrome`, `Opera`, `Internet Explorer`, `Microsoft Edge`, `Brave`
(Window 10 đi kèm với Edge theo mặc định ; nếu bạn có window 7 trở lên, bạn có thể cài đặt Internet Explorer 11 ; nếu không , bạn nên cài đặt một trình duyệt thay thế)

+  macOS: `Firefox`, `Chrome`, `Opera`, `Safari` and `Brave`

Trước khi tiếp tục, bạn nên cài đặt ít nhất hai trong số các trình duyệt này và chuẩn bị sẵn sàng để thử nghiệm.

Chú ý: Internet Explorer không tương thích với một số tính năng web hiện tại và nó có thể không chạy được dự án của bạn. Bạn thường không cần lo lắng về việc làm cho các dự án web của mình tương thích với nó, vì rất ít người vẫn sử dụng nó - chắc chắn đừng lo lắng quá nhiều về điều đó khi bạn đang học. Đôi khi bạn có thể gặp phải một dự án yêu cầu hỗ trợ cho nó.

##### Install a local web server 

Một số ví dụ sẽ cần được chạy bởi một máy chủ web để hoạt động thành công. Bạn có thể tìm hiểu cách thực hiện việc này trong [How do you set up a local testing server?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server)

### What will your website look like ?

Trang web của bạn sẽ như thế nào ? Thảo luận về công việc lập kế hoạch và thiết kế mà bạn phải làm cho trang web của mình trước khi viết mã, bao gồm "Trang web của tôi cung cấp thông tin gì ? ", "Tôi muốn phông chữ và màu sắc nào ?", và "Trang web của tôi làm gì ? "

##### First things first: planning

Trước khi làm bất cứ điều gì , bạn cần có một số ý tưởng. Trang web của bạn thực sự nên làm gì ? Về cơ bản, một trang web có thể làm được mọi thứ, nhưng với lần thử đầu tiên, bạn nên đơn giản hoá mọi thứ. Chúng ta sẽ bắt đầu bằng cách tạo một vài trang web đơn giản với tiêu đề, hình ảnh và một vài đoạn văn.

Để bắt đầu, bạn cần trả lời những câu hỏi sau:

1. Trang web của bạn nói về cái gì ? Bạn thích chó, New York hay PacMan ? 

2. Bạn đang trình bày thông tin gì về chủ đề này ? Viết tiêu đề và một vài đoạn văn và nghĩ về hình ảnh bạn muốn hiển thị trên trang của mình.

3. Trang web của bạn trông như thế nào, theo thuật ngữ cấp cao đơn giản ? Màu nền là gì ? Loại phông chữ nào phù hợp : trang trọng, hoạt hình, đạm và to, tinh tế ? 

Note: Các dự án phức tạp cần có hướng dẫn chi tiết đi vào tất cả các chi tiết về màu sắc, phông chữ, khoảng cách giữa các mục trên một trang, phong cách viết phù hợp, v.v. Đây đôi khi được gọi là hướng dẫn thiết kế, hệ thống thiết kế hoặc sách thương hiệu và bạn có thể xem ví dụ tại Hệ thống thiết kế Firefox Photon.

##### Sketching out your design (Phác thảo thiết kế của bạn)

Tiếp theo, lấy giấy bút và phác thảo đại khái cách bạn muốn trang web của mình trông giống như thế nào. Đối với trang web đơn giản đầu tiên của bạn, không có nhiều thứ để phác thảo, nhưng bạn nên tập thói quen làm điều này ngay bây giờ. Nó thực sự hữu ích - bạn không cần phải là Van Gogh ! 

![Imgur](https://i.imgur.com/cgfMM7R.png)

Chú ý: Ngay cả trên các trang web thực, phức tạp, các nhóm thiết kế thường bắt đầu với các bản phác thoả thô trên giấy và sau đó xây dựng các mô hình kỹ thuật số bằng cách sử dụng trình chỉnh sửa đồ hoạ hoặc công nghệ web.

Nhóm web thường bao gồm cả nhà thiết kế đồ hoạ và nhà thiết kế trải nghiệm người dùng (UX). Các nhà thiết kế đồ hoạ tập hợp các hình ảnh trực quan của trang web. Người thiết kế UX có một vai trò hơi trừu tượng hơn trong việc giải quyết cách người dùng sẽ trải nghiệm và tương tác với trang web.

##### Choosing your assets 

Tại thời điểm này, thật tốt để bắt đầu tập hợp nội dung cuối cùng sẽ xuất hiện trên trang web của bạn

+ Text 

Bạn vẫn nên có các đoạn văn và tiêu đề của bạn từ trước đó. Giữu những thức này gần đó.

+ Theme color

Để chọn màu, hãy chuyển đến Bộ chọn màu và tìm màu bạn thích. Khi bạn nhấp vào một màu, bạn sẽ thấy một mã gồm sáu ký tự như `#660066`. Đó được gọi là mã hex (viết tắt của hệ thập lục phân) và đại diện cho màu của bạn. Sao chép mã xuống một nơi nào đó an toàn ngày bầy giờ.

![Imgur](https://i.imgur.com/t77p8o5.png)

+ Images 

Để chọn một hình ảnh, hãy truy cập `Google Images`  và tìm kiếm thứ gì đó phù hợp.

1. Khi bạn tìm thấy hình ảnh bạn muốn, hãy nhấp vào hình ảnh để xem phóng to nó.

2. Nhấp chuột phải chọn hình ảnh (Ctrl + click trên máy Mac), chọn `Save Image As...` và chọn một nơi an toàn để lưu hình ảnh của bạn. Ngoài ra, hãy sao chép địa chỉ web của hình ảnh từ thanh địa chỉ của trình duyệt để sử dụng sau này.

![Imgur](https://i.imgur.com/2XxdBcH.png)

Lưu ý rằng, hầu hết các hình ảnh trên web, bao gồm cả Google Hình ảnh, đều có bản quyền. Để giảm khả năng vi phạm bản quyền, bạn có thể sử dụng bộ lọc giấy phép của Google.

![Imgur](https://i.imgur.com/m51d9xR.png)

+ Font 

Để chọn phông:

1. Truy cập `Google Fonts` và tìm cái mà bạn thích

2. Sao chép các dòng mã mà Google cung cấp cho bạn vào trình soạn thảo văn bản của bạn để lưu lại sau này 

3. Để biết thêm chi tiết về cách sử dụng Phông chữ Google, hãy xem trang này.

----------------------------------------

### Dealing with files (Xử lý các tệp tin)

Một trang web bao gồm nhiều tệp: nội dung văn bản, mã, bảng định kiểu, nội dung phương tiện, v.v. Khi bạn đang xây dựng một trang web, bạn cần tập hợp các tệp này thành một cấu trúc hợp lý trên máy tính cục bộ của mình, đảm bảo rằng chúng có thể nói chuyện với nhau và khiến tất cả nội dung của bạn trông như ý trước khi cuối cùng bạn tải chúng lên máy chủ. 

Xử lý tệp thảo luận về một số vấn đề bạn cần lưu ý để bạn có thể thiết lập cấu trúc tệp hợp lý cho trang web của mình.

#### Where should your website live on your computer?

Khi bạn đang làm việc trên một trang web cục bộ trên máy tính của mình, bạn nên giữ tất cả cac tệp liên quan trong một thư mục duy nhất phản ánh cấu trúc tệp của trang web đã xuất bản trên máy chủ. Thư mục này có thể tồn tại ở bất cứ đâu bạn thích, nhưng bạn nên đặt nó ở nơi nào đó bạn có thể dễ dàng tìm thấy, có thể trên Màn hình nền, trong thư mục Trang chủ hoặc ở thư mục gốc của ổ cứng.

1. Chọn một nơi để lưu trữ các dự án trang web của bạn. Bên trong địa điểm bạn đã chọn, hãy tạo một thư mục mới có tên là `web-project`(hoặc tương tự). Đây là nơi tất cả các dự án trang web của bạn sẽ sống.

2. Bên trong thư mục đầu tiên này, hãy tạo một thư mục khác để lưu trữ trang web đầu tiên của bạn. Gọi là là `test-site` (hoặc một cái gì đó giàu trí tưởng tượng hơn)

#### An aside on casing and spacing (Một khía cạnh về viết hoa và khoảng trống)

Bạn sẽ nhận thấy rằng trong suốt bài viết này, chúng tôi yêu cầu bạn đặt tên cho các thư mục và tệp hoàn toàn bằng chữ thường và không có khoảng trắng. Điều này là do:

1. Nhiều máy tính, đặc biệt là máy chủ web, phân biệt chữ hoa và chữ thường. Vì vậy ,ví dụ: nếu bạn đặt một hình ảnh trên trang web của mình tại `test-site/MyImage.jpg` và sau đó trong một tệp khác, bạn cố gọi hình ảnh đó là `test-site/myimage.jpg`, nó có thể không hoạt động.

2. Trình duyệt, máy chủ web và ngôn ngữ lập trình không xử lý khoảng trống một cách nhất quán. Ví dụ: neus bạn sử dụng khoảng trắng trong tên tệp của mình, một số hệ thống có thể coi tên tệp là hai tên tệp. Một số máy chủ sẽ thay thế các vùng trong tên tệp của bạn bằng `%20` (mã ký tự cho khoảng trắng trong URIs), dấn đến tất cả các liên kết của bạn bị hỏng. Tốt hơn nên phân tách các từ bằng dấu gạch ngang, thay vì dấu gạch dưới: `my-file.html` và `my_file.html`

Câu trả lời ngắn gọn là bạn nên sử dụng dấu gạch ngang cho tên tệp của mình. Công cụ tìm kiếm của google coi dấu gạch ngang là dấu tách từ nhưng không coi dấu gạch dưới theo cách đó. Vì những lý do này, tốt nhất bạn nên tập thói quen viết thư mục và tên tệp của mình bằng chữ thường, không có khoảng trắng và các từ được phân tách bằng dâu gạch ngang, ít nhất là cho đến khi bạn biết mình đang làm gì . Bằng cách đó bạn sẽ ít vấn đề hơn sau này.

#### What structure should your website have ? (Cấu trúc trang web của bạn nên có ? )

Tiếp theo, hãy xem trang web thử nghiệm của chúng ta nên có cấu trúc nào. Những thứ phổ biến nhất mà chúng ta sẽ có trong bất kỳ dự án trang web nào mà chúng ta tạo là tệp HTML lập chỉ mục (file index.html) và các thư mục để chứa hình ảnh, tệp kiểu và tệp tập lệnh. Hãy tạo những thứ này ngay bây giờ.

1. `index.html`: Tệp này thường sẽ chứa nội dung trang chủ của bạn, nghĩa là văn bản và hình ảnh mà mọi người nhìn thấy khi họ truy cập trang web của bạn lần đầu tiên. Sử dụng trình soạn thảo văn bản của bạn, tạp một tệp mới có tên là `index.html` và lưu nó ngay bên trong thư mục trang web thử nghiệm của bạn.

2. `images floder`: Thư mục này sẽ chứa tất cả các hình ảnh mà bạn sử dụng trên trang web của mình. Taok một thư mục có tên là `images`, bên trong thư mục `test-side`

3. `styles folder`: Thư mục này sẽ chứa mã `CSS` được sử dụng để tạo kiểu cho nội dung của bạn (ví dụ: đặt văn bản và màu nền). Tạp một thư mục được gọi là `styles`, bên trong thư mục `test-side`

4. `scripts folder`: Thư mục này sẽ chứa tất cả các mã `JavaScript` được sử dụng để thêm chức năng tương tác vào trang web của bạn. (Ví dụ: Các nút tải dữ liệu khi được nhấp vào). Tạo một thưc mục có tên là `scripts`, bên trong thư mục `test-side`

To be contined : https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Dealing_with_files






















