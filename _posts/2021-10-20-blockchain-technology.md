---
layout: post
title: CÔNG NGHỆ BLOCKCHAIN VỚI CÁC ỨNG DỤNG THỰC TIỄN ĐA DẠNG
subtitle: blockchain, Tạp chí PI
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

Tác giả: Phạm Huy Điển

Trích: Tạp chí PI - Tập 3 Số 1 Tháng 1.2019

-----------------

### BLOCKCHAIN LÀ GÌ ? 

Vào tháng 9 năm 2009, Satoshi Nakamoto đã giới thiệu hai ý tưởng có ảnh hưởng trong bài báo: "Bitcoin: Hệ thống tiền mặt điện tử ngang hàng". Ý tưởng đầu tiên là "Bitcoin" - một loại tiền tệ trực tuyến phi tập trung, ngang hàng có thể duy trì giá trị mà không có bất kỳ sự hỗ trợ nào từ một cơ quan trung ương. Sau khi thu được sự chú ý ngày càng tăng từ những người chấp nhận sớm và các nhà làm luật, Bitcoin được công nhận là một phương pháp rẻ tiền, nhanh chóng và đáng tin cậy trong việc luân chuyển giá trị kinh tế trên internet theo cách phi tập trung. 

Với hơn 4 triệu người dùng và hơn 125.000 giao dịch mỗi ngày(trong khoảng thời gian 1 năm, tính từ tháng 9 năm 2014 đến tháng 9 năm 2015), Bitcoin đã biến thành một trong những mạng máy tính mạnh nhất hiện thời.

Ý tưởng thứ hai, quan trọng không kém là "Blockchain", một cơ sở dữ liệu theo thời gian mang tính công khai của các giao dịch được ghi lại bởi một mạng lưới các agent (đại lý). Ở đây, các giao dịch riêng lẻ chứa thông tin chi tiết về ai đã gửi những gì cho ai được nhóm vào các tập dữ liệu được gọi là "các khối". Các khối chứa thông tin liên kết với nhau, theo cách khối sau chứa thông tin về khối trước và qua được như được "xích" vào với nhau.

Bây giờ, có thể chắc chắn rằng không mấy ai trong số bạn đọc của PI chưa từng nghe nói về Bitcoin và Blockchain, vì chúng là những chủ đề yêu thích của truyền thông những ngày này. 

Ngay cả những người chưa bao giờ "đào" tiền điện tử hoặc hiểu cách thức hoạt động của nó, cũng đang nói không ít về nó. Đương nhiên là họ đều muốn được hiểu rõ hơn về những thuật ngữ mới mẻ nhưng đã trở nên thông dụng này. Không ít bạn đọc của PI có thể đã làm quen với tiền mật mã và Bitcoin, nhưng với Blockchain chưa chẳn đã là như vậy. Khuôn khổ eo hẹp của bài viết ngắn gọn về tiền mật mã trên PI đã nói ở trên không cho phép đề cập đến Blockchain một cách thấu đáo, mà chỉ có thể nói sơ lược về khía cạnh toán học của nó. Tuy nhiên, bạn đọc của PI không chỉ là những người học toán và làm toán, mà thậm chí phần đông là những người không đi sâu vào kỹ thuật, cho nên sẽ không lấy gì làm hấp dẫn khi ta chỉ nói về bản chất Toán học của những khái niệm này. Sẽ hợp lý hơn khi chúng được trình bày theo cách mà phần lớn người dùng Internet thông thường đều có thể hiểu.

Bởi vậy, không giống như các bài viết theo phong cách toán học truyền thống, thay vì trước hết tìm cách định nghĩa Blockchain, ta hãy hiểu cho rõ vấn đề mà nó giải quyết.

Hãy tưởng tượng, Bình là một anh Bạn tốt của bạn. Anh ấy bất ngờ gặp sự cố khi đang đi du lịch nước ngoài, nên đã gọi cho bạn và nói: "Tớ cần một ít tiền để xử lý sự cố". Bạn trả lời: "Tớ sẽ gửi ngay" và gác máy.

![Imgur](https://i.imgur.com/2ZgHzQa.png)

Sau đó, bạn ra ngân hàng để làm thủ tục chuyển $1000 từ tài khoản của bạn sang tài khoản Bình. Nhân viên ngân hàng sẽ mở sổ đăng ký, kiểm tra số dư tài khoản của bạn để xem bạn có đủ số dư để chuyển $1000 cho Bình hay không. Nếu thấy đủ, anh ta đưa vào một mục trong sổ đăng ký như sau:

![Imgur](https://i.imgur.com/H0SrM4Q.png)

~~~
Bản ghi giao dịch
~~~

Bạn gọi cho Bình và nói với anh ta. "Tớ đã chuyển tiền. Cậu đến ngân hàng của mình và có thể rút $1000 mà tớ vừa chuyển".

Chuyện gì vừa xảy ra vậy ? Bạn và Bình đều tin ngân hàng quản lý tiền của bạn. Không có chuyển động thực sự của các tờ hoá đơn (vật lý) chuyển tiền. Tất cả những gì cần thiết là một mục tin nhập vào sổ đăng ký. Hay chính xác hơn, một mục trong sổ đăng ký mà cả bạn và Bình đều không kiểm soát hoặc sở hữu.

Và đó là vấn đề của các hệ thống hiện tại: Để tạo lập lòng tin giữa chúng ta, chúng ta phải phụ thuộc vào một bên thứ ba.

Trong nhiều năm, chúng ta đã phụ thuộc vào những "người trung gian" này để tin tưởng lẫn nhau.

Bạn có thể hỏi, "việc phụ thuộc vào họ thì có vấn đề gì ?". Vấn đề là:

+ Điều gì xảy ra nếu bản ghi giao dịch bị thiêu rụi trong một đám cháy ?

+ Điều gì xảy ra nếu người quản lý tài khoản đã nhầm lẫn, viết $1500 thay vì $1000 ?

+ Điều gì sẽ xảy ra nếu anh ta không nhầm lẫn mà cố tính viết như thế trong bản ghi ?

Câu hỏi này sinh tự nhiên là có chăng một hệ thống mà chúng ta vẫn có thể chuyển tiền cho nhau mà không cần ngân hàng ?

Để trả lời câu hỏi này, cũng cần phải đi sâu hơn và tự hỏi mình một câu hỏi tốt hơn (xét cho cùng, chỉ những câu hỏi tốt hơn mới dẫn đến câu trả lời tốt hơn). Hãy suy nghĩ về nó trong một chút, chuyển tiền có nghĩa là gì ? Chỉ là "đưa vào" một mục trong bản ghi. Câu hỏi tốt hơn sau đó sẽ là: "Có cách nào để chúng ta tự duy trì bản ghi, thay vì người khác làm điều đó cho chúng ta ?"

Đó mới là một câu hỏi đáng để khám phá. Và câu trả lời là những gì bạn có thể đã đoán. Blockchain chính là câu trả lời cho câu hỏi sâu sắc đó. Đó là một phương pháp để duy trì bản ghi giữa chúng ta thay vì phụ thuộc vào người khác để làm điều đó cho chúng ta.

### Vậy nó làm như thế nào ?

Bây giờ, khi một số câu hỏi đã bắt đầu xuất hiện trong đầu bạn, chúng ta sẽ có hứng thú để tìm hiểu cách hoạt động của kiểu lưu "bản ghi" phân tán này.

Yêu cầu của phương pháp này là phải có đủ số người cùng chí hướng, không muốn phụ thuộc vào bên thứ ba. Chỉ khi đó nhóm này có thể tự duy trì đăng ký của mình. Bao nhiêu là đủ ? Ít nhất là ba, nhưng càng nhiều thì càng tốt. Trong ví dụ của mình, chúng ta giả sử rằng có mười cá nhân muốn từ bỏ ngân hàng hoặc bất kỳ bên thứ ba nào. Theo thoả thuận chung, họ luôn có thông tin chi tiết về tài khoản của nhau - mà không cần biết đến danh tính của người kia.

![Imgur](https://i.imgur.com/ii3FgV2.png)

Mỗi người đều có một thư mục trống để bắt đầu. Khi tiến hành hoạt động, tất cả mười cá nhân này sẽ tiếp tục thêm vào các trang vào các thư mục hiện đang trống của họ. Và tập hợp các trang này sẽ tạo thành sổ đăng ký theo dõi các giao dịch.

Tiếp theo, mọi người trong mạng ngồi với một trang trống và một cây bút trong tay. Mọi người đều sẵn sàng viết bất kỳ giao dịch nào xảy ra trong hệ thống.









