---
date: '2026-08-10'
description: Tìm hiểu cách thêm bình luận java với Aspose.Words for Java. Hướng dẫn
  chi tiết từng bước để tạo, trả lời, in, xóa và đánh dấu bình luận là đã hoàn thành,
  cùng với việc lấy thời gian UTC.
keywords:
- how to add comment java
- comment management Java
- Aspose.Words comments
lastmod: '2026-08-10'
og_description: Tìm hiểu cách thêm bình luận java với Aspose.Words for Java. Hướng
  dẫn chi tiết từng bước để tạo, trả lời, in, xóa và đánh dấu bình luận là đã hoàn
  thành, cùng với việc lấy thời gian UTC.
og_image_alt: Guide showing how to add comment java with Aspose.Words in Word documents
og_title: Cách thêm bình luận java bằng Aspose.Words cho tài liệu Word
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add comment java with Aspose.Words for Java. Step‑by‑step
    guide to create, reply to, print, remove, and mark comments as done, plus retrieve
    UTC timestamps.
  headline: How to add comment java using Aspose.Words for Word docs
  type: TechArticle
- questions:
  - answer: No. The trial works for development only; a full license is required for
      production deployments.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes. Load a protected file by passing the password to the `Document` constructor.
    question: Does the library support password‑protected documents?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, with full feature
      parity across versions.
    question: Which Java versions are compatible?
  - answer: Comment enumeration runs in linear time; a 1,000‑page document processes
      in under 2 seconds on a typical 4‑core server.
    question: How does comment performance scale with document size?
  - answer: Absolutely. Iterate the `CommentCollection` and write each comment’s properties
      to CSV, JSON, or XML as needed.
    question: Can I export comments to a separate file?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
title: Cách thêm bình luận java bằng Aspose.Words cho tài liệu Word
url: /vi/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm bình luận java bằng Aspose.Words cho tài liệu Word

## Giới thiệu
Thêm bình luận một cách lập trình vào tài liệu Word có thể giúp hợp lý hoá việc cộng tác, đánh giá mã, hoặc tạo báo cáo tự động. Trong hướng dẫn này, bạn sẽ học **cách thêm bình luận java** bằng thư viện Aspose.Words, bao gồm tạo, trả lời, in, xóa, đánh dấu đã hoàn thành và trích xuất dấu thời gian UTC. Khi kết thúc, bạn sẽ có thể nhúng phản hồi phong phú trực tiếp vào tài liệu mà không cần can thiệp thủ công.

## Câu trả lời nhanh
- **Câu hỏi đầu tiên là gì?** Tải tệp Word bằng `new Document("input.docx")`.  
- **Tôi có thể trả lời một bình luận không?** Có — tạo một đối tượng `Comment` và gọi `comment.getReplies().add(reply)`.  
- **Làm thế nào để đánh dấu một bình luận là đã hoàn thành?** Đặt `comment.setDone(true)` để đánh dấu nó đã được giải quyết.  
- **Có sẵn thời gian UTC không?** Mỗi bình luận lưu `getDateTime()` ở định dạng UTC, bạn có thể đọc trực tiếp.  
- **Tôi có cần giấy phép không?** Bản dùng thử hoạt động cho phát triển; giấy phép đầy đủ loại bỏ các giới hạn đánh giá.

## “how to add comment java” là gì?
`how to add comment java` đề cập đến quá trình chèn một bình luận vào tài liệu Microsoft Word một cách lập trình bằng mã Java và API Aspose.Words. Thao tác này cho phép vòng phản hồi tự động trong quy trình làm việc tập trung vào tài liệu.

## Tại sao nên sử dụng Aspose.Words để quản lý bình luận?
Aspose.Words hỗ trợ **hơn 35 định dạng nhập và xuất** và có thể xử lý tài liệu vượt quá **500 trang** trong khi giữ mức sử dụng bộ nhớ dưới **100 MB** trên máy chủ điển hình. API bình luận của nó hoạt động mà không cần cài đặt Microsoft Word, cho phép bạn kiểm soát hoàn toàn trong môi trường không giao diện và giảm chi phí giấy phép lên tới **70 %** so với tự động hoá Office.

## Yêu cầu trước
- Java Development Kit (JDK) 17 hoặc mới hơn đã được cài đặt.  
- Một IDE như IntelliJ IDEA hoặc Eclipse.  
- Maven hoặc Gradle để quản lý phụ thuộc.  
- Giấy phép Aspose.Words for Java hợp lệ (dùng thử hoặc đầy đủ).

### Cài đặt Aspose.Words cho Java
Aspose.Words được cung cấp dưới dạng một tệp JAR duy nhất. Thêm phụ thuộc phù hợp với công cụ xây dựng của bạn.

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### Nhận giấy phép
Aspose.Words là sản phẩm thương mại; bạn có thể bắt đầu với bản dùng thử miễn phí hoặc yêu cầu giấy phép tạm thời để truy cập đầy đủ tính năng. Truy cập [trang mua hàng](https://purchase.aspose.com/buy) để khám phá các tùy chọn cấp phép.

## Cách thêm bình luận trong Java bằng Aspose.Words?
Tải tài liệu của bạn, tạo một đối tượng `Comment`, và gắn nó vào một `Paragraph`. Mẫu hai bước này chèn bình luận vào vị trí mong muốn và là nền tảng cho tất cả các thao tác sau này. Bằng cách chỉ định tác giả, nội dung và dấu thời gian, bạn có thể ngay lập tức cung cấp ngữ cảnh cho người đánh giá, và bình luận sẽ trở thành một phần của cấu trúc tài liệu.

Lớp `Document` là đối tượng cấp cao nhất của Aspose.Words, đại diện cho một tệp Word duy nhất trong bộ nhớ. Sau khi khởi tạo, tất cả các thao tác đọc và ghi đều diễn ra qua đối tượng này.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

Tiếp theo, bạn tạo bình luận. Lớp `Comment` lưu trữ thông tin tác giả, nội dung và dấu thời gian.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Cuối cùng, thêm một trả lời bằng cách sử dụng bộ sưu tập `Replies` của bình luận. Đối tượng `Comment` tự động theo dõi cấu trúc trả lời.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Cách in tất cả bình luận và các trả lời của chúng?
Đệ quy qua `CommentCollection` của tài liệu và xuất ra văn bản, tác giả và dấu thời gian UTC của mỗi bình luận. Các trả lời được lồng trong mỗi bình luận, cho phép bạn hiển thị toàn bộ chuỗi hội thoại. Bằng cách duyệt bộ sưu tập một cách đệ quy, bạn có thể giữ nguyên cấu trúc, định dạng đầu ra cho log hoặc giao diện người dùng, và tùy chọn lọc theo tác giả hoặc ngày.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

Sử dụng vòng lặp đơn giản để duyệt bộ sưu tập và in chi tiết.  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```  

## Cách xóa các trả lời bình luận?
Bạn có thể xóa một trả lời cụ thể hoặc xóa tất cả các trả lời khỏi một bình luận. Việc loại bỏ các trả lời giúp tài liệu sạch sẽ hơn sau khi phản hồi đã được tích hợp. Sử dụng phương thức `getReplies().remove(index)` để xóa mục tiêu hoặc gọi `clear()` để xóa toàn bộ danh sách trả lời, đảm bảo không còn cuộc thảo luận lẻ loi.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

Gọi `comment.getReplies().clear()` hoặc xóa các trả lời riêng lẻ theo chỉ mục.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## Cách đánh dấu bình luận là đã hoàn thành?
Đặt cờ `Done` cho một bình luận cho biết vấn đề đã được giải quyết. Dấu hiệu trực quan này hữu ích cho người đánh giá và các công cụ xử lý tiếp theo. Khi gọi `setDone(true)`, Word sẽ hiển thị một dấu kiểm bên cạnh bình luận, và bạn có thể sau này truy vấn cờ này để tạo báo cáo các mục còn tồn đọng.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

Áp dụng cờ sau khi bạn đã xử lý nội dung bình luận.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## Cách lấy ngày và giờ UTC từ một bình luận?
Mỗi bình luận lưu thời gian tạo của nó ở UTC, có thể truy cập qua `getDateTime()`. Dấu thời gian này không thể thiếu cho các bản ghi kiểm tra và quản lý phiên bản. Đối tượng `DateTime` trả về có thể được định dạng bằng mẫu ISO‑8601, cho phép bạn ghi lại các thời điểm phản hồi chính xác và đồng bộ dữ liệu bình luận trên các hệ thống phân tán.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Bạn có thể định dạng dấu thời gian dưới dạng ISO‑8601 để dễ ghi log.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Ứng dụng thực tế
Hiểu các API này cho phép bạn xây dựng các giải pháp mạnh mẽ cho:
- **Nền tảng chỉnh sửa cộng tác** – nhúng vòng phản hồi trực tiếp vào các báo cáo được tạo.  
- **Quy trình đánh giá tự động** – đánh dấu, giải quyết và kiểm tra bình luận mà không cần can thiệp của con người.  
- **Tài liệu tuân thủ** – ghi lại dấu thời gian của người đánh giá cho các cuộc kiểm toán quy định.

## Các cân nhắc về hiệu năng
Khi xử lý các tệp lớn (hơn 500 trang), hãy tuân theo các thực hành tốt sau:
- Xử lý bình luận theo lô để tránh tải toàn bộ bộ sưu tập vào bộ nhớ.  
- Sử dụng `Document.optimizeResources()` để thu nhỏ tài liệu trước khi lưu.  
- Giữ Aspose.Words luôn cập nhật; phiên bản 24.12 đã giới thiệu tăng tốc 30 % cho việc liệt kê bình luận.

## Kết luận
Bây giờ bạn đã có bộ công cụ hoàn chỉnh cho **cách thêm bình luận java** với Aspose.Words: tạo bình luận, trả lời, in, xóa, đánh dấu đã hoàn thành và trích xuất dấu thời gian UTC. Tích hợp các đoạn mã này vào dịch vụ Java hiện có của bạn để tự động hoá phản hồi, thực thi chính sách đánh giá và duy trì một bản ghi kiểm tra sạch sẽ.

**Các bước tiếp theo**
- Thử nghiệm lọc bình luận theo tác giả hoặc ngày.  
- Kết hợp quản lý bình luận với API “track changes” của Aspose.Words để kiểm soát phiên bản đầy đủ.  
- Khám phá xuất dữ liệu bình luận sang JSON cho phân tích downstream.

## Câu hỏi thường gặp

**Q: Tôi có thể sử dụng Aspose.Words mà không có giấy phép trong môi trường sản xuất không?**  
A: Không. Bản dùng thử chỉ hoạt động cho phát triển; giấy phép đầy đủ là bắt buộc cho triển khai sản xuất.

**Q: Thư viện có hỗ trợ tài liệu được bảo vệ bằng mật khẩu không?**  
A: Có. Tải tệp được bảo vệ bằng cách truyền mật khẩu vào hàm khởi tạo `Document`.

**Q: Các phiên bản Java nào tương thích?**  
A: Aspose.Words for Java hỗ trợ JDK 8 đến JDK 21, với đầy đủ tính năng trên mọi phiên bản.

**Q: Hiệu năng của bình luận tăng như thế nào khi tài liệu lớn?**  
A: Việc liệt kê bình luận chạy theo thời gian tuyến tính; tài liệu 1.000 trang được xử lý dưới 2 giây trên máy chủ 4 nhân điển hình.

**Q: Tôi có thể xuất bình luận ra tệp riêng không?**  
A: Chắc chắn. Duyệt `CommentCollection` và ghi các thuộc tính của mỗi bình luận ra CSV, JSON hoặc XML theo nhu cầu.

---

**Cập nhật lần cuối:** 2026-08-10  
**Được kiểm thử với:** Aspose.Words for Java 24.12  
**Tác giả:** Aspose  

{{< blocks/products/products-backtop-button >}}

## Hướng dẫn liên quan

- [Thành thạo Annotations & Comments với các hướng dẫn Aspose.Words cho Java](/words/java/annotations-comments/)
- [Theo dõi thay đổi trong tài liệu Word bằng Aspose.Words Java: Hướng dẫn toàn diện về sửa đổi tài liệu](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Hướng dẫn toàn diện về xử lý tài liệu Word](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}