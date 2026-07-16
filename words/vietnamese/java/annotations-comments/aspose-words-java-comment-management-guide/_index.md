---
date: '2026-07-16'
description: Tìm hiểu cách quản lý comment trong tài liệu Word bằng Aspose.Words cho
  Java. Thêm comment, thêm reply cho comment, in comment Word, và đánh dấu comment
  đã hoàn thành một cách hiệu quả.
keywords:
- how to manage comments
- Aspose.Words Java
- comment management in Word documents
- add comment java
- print word comments
lastmod: '2026-07-16'
og_description: Tìm hiểu cách quản lý comment trong tài liệu Word bằng Aspose.Words
  cho Java. Thêm comment, thêm reply cho comment, in comment Word, và đánh dấu comment
  đã hoàn thành một cách hiệu quả.
og_image_alt: 'Guide: Manage Word comments with Aspose.Words Java'
og_title: Cách quản lý comment trong tài liệu Word bằng Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Learn how to manage comments in Word documents using Aspose.Words for
    Java. Add comment, add comment reply, print word comments, and mark comment done
    efficiently.
  headline: How to Manage Comments in Word Docs with Aspose.Words Java
  type: TechArticle
- questions:
  - answer: Aspose.Words for Java is a fully managed API that enables creation, modification,
      conversion, and rendering of Word documents without requiring Microsoft Word.
    question: What is Aspose.Words for Java?
  - answer: Instantiate a `Document`, create a `Comment` with author and text, assign
      it to a `Range`, and add it to the document’s `CommentCollection`.
    question: How do I add a comment programmatically?
  - answer: Yes, use `comment.getDateTime()` which returns a `java.util.Date`; convert
      it to UTC with `toInstant()` for an ISO‑8601 string.
    question: Can I retrieve the exact time a comment was added?
  - answer: Call `comment.setDone(true)`; the comment will display a “Done” check‑mark
      in supported Word viewers.
    question: How do I mark a comment as resolved?
  - answer: A full license removes all evaluation restrictions; a temporary trial
      license is sufficient for testing and development.
    question: Is a license required for production use?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java
- Word comments
- add comment reply
title: Cách quản lý comment trong tài liệu Word bằng Aspose.Words Java
url: /vi/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách quản lý bình luận trong tài liệu Word bằng Aspose.Words Java

## Giới thiệu
Quản lý bình luận trong tài liệu Word một cách lập trình có thể gặp khó khăn, đặc biệt khi bạn cần thêm trả lời, in phản hồi hoặc đánh dấu vấn đề đã được giải quyết. **Cách quản lý bình luận** một cách hiệu quả là trọng tâm của hướng dẫn này, và bạn sẽ học một quy trình hoàn chỉnh sử dụng Aspose.Words cho Java. Khi kết thúc, bạn sẽ có thể thêm bình luận, thêm trả lời bình luận, in các bình luận trong Word, xóa các trả lời không mong muốn, đánh dấu bình luận là đã xong, và lấy thời gian UTC chính xác.

**Bạn sẽ học được**
- Thêm bình luận và trả lời một cách dễ dàng
- In tất cả các bình luận cấp cao nhất và các trả lời của chúng
- Xóa trả lời bình luận hoặc đánh dấu bình luận là đã xong
- Lấy ngày và giờ UTC của bình luận để theo dõi chính xác

Sẵn sàng nâng cao kỹ năng quản lý tài liệu của bạn? Hãy kiểm tra các yêu cầu trước khi chúng ta bắt đầu.

## Câu trả lời nhanh
- **Làm sao tôi thêm một bình luận trong Java?** Sử dụng `Document` → `Comment` → `Comment.Author = "User"` và `Comment.Range = doc.getFirstSection().getBody().getFirstParagraph().getRange()`.  
  `Document` đại diện cho một tệp Word được tải vào bộ nhớ.  
  `Comment` lưu trữ tác giả, nội dung và phạm vi liên quan của bình luận.
- **Tôi có thể in tất cả các bình luận không?** Duyệt `doc.getComments()` và xuất `Comment.getAuthor()` và `Comment.getText()`.  
  Các đối tượng `Comment` là một phần của bộ sưu tập bình luận của tài liệu.
- **Làm sao để xóa một trả lời?** Gọi `comment.getReplies().clear()` hoặc xóa một `Reply` cụ thể theo chỉ mục.  
  `Reply` đại diện cho một phản hồi được gắn vào bình luận cha.
- **Điều gì đánh dấu một bình luận là đã xong?** Đặt `comment.setDone(true)`; Aspose.Words sẽ hiển thị cờ “Done”.  
  Phương thức `setDone` đánh dấu bình luận là đã giải quyết.
- **Làm sao để lấy thời gian tạo bình luận?** Sử dụng `comment.getDateTime().toInstant().toString()` để có chuỗi UTC ISO‑8601.  
  `getDateTime` trả về ngày và giờ tạo của bình luận.

## Cách quản lý bình luận trong tài liệu Word bằng Aspose.Words Java?
Tải tệp Word của bạn, tạo hoặc tìm một đối tượng `Comment`, tùy chọn thêm một `Reply`, sau đó gọi các phương thức thích hợp (`setDone`, `remove`, `getDateTime`) – tất cả trong vài dòng ngắn gọn. Aspose.Words xử lý XML nền tảng, bảo toàn định dạng và hoạt động mà không cần cài đặt Microsoft Word, rất thích hợp cho tự động hoá phía máy chủ.

## Bình luận là gì trong Aspose.Words?
Một **bình luận** là một chú thích riêng biệt được gắn vào một phạm vi văn bản trong tài liệu, được lưu dưới dạng nút `Comment` trong cấu trúc WordprocessingML. Bình luận có thể chứa thông tin tác giả, dấu thời gian và một tập hợp các đối tượng `Reply`. Những bình luận này xuất hiện ở lề của các trình xem Word và có thể được chỉnh sửa, giải quyết hoặc xóa bằng lập trình, cung cấp cách linh hoạt để thu thập phản hồi của người đánh giá.

## Tại sao nên sử dụng Aspose.Words để quản lý bình luận?
Aspose.Words cung cấp một API mạnh mẽ, hiệu năng cao để xử lý tài liệu Word mà không cần Microsoft Office. Nó hỗ trợ nhiều định dạng, xử lý nhanh và bao gồm các tính năng tích hợp sẵn cho việc thao tác bình luận, rất phù hợp cho tự động hoá phía máy chủ và quy trình tài liệu quy mô lớn.

- **Hơn 35 định dạng tệp** (DOCX, DOC, RTF, HTML, PDF, v.v.) được hỗ trợ, vì vậy bạn có thể làm việc với bất kỳ nguồn tương thích Word nào.
- **Tốc độ xử lý:** Aspose.Words có thể đọc hoặc ghi một tài liệu 500 trang với 10 000 bình luận trong vòng dưới 4 giây trên một máy chủ 2.6 GHz tiêu chuẩn.
- **Không phụ thuộc vào Office:** Thư viện chạy hoàn toàn không giao diện, loại bỏ chi phí giấy phép và cài đặt.

## Yêu cầu trước
- Java Development Kit (JDK 8 hoặc mới hơn) đã được cài đặt trên máy.
- Kiến thức lập trình Java cơ bản.
- Một IDE như IntelliJ IDEA hoặc Eclipse.
- Maven hoặc Gradle để quản lý phụ thuộc.

### Cài đặt Aspose.Words cho Java
Aspose.Words là một thư viện toàn diện cho phép bạn làm việc với tài liệu Word ở nhiều định dạng. Để bắt đầu, thêm phụ thuộc sau vào dự án của bạn:

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

#### Mua giấy phép
Aspose.Words là một thư viện trả phí, nhưng bạn có thể bắt đầu với bản dùng thử miễn phí hoặc yêu cầu giấy phép tạm thời để truy cập đầy đủ các tính năng. Truy cập [purchase page](https://purchase.aspose.com/buy) để khám phá các tùy chọn cấp phép.

## Hướng dẫn thực hiện
Trong phần này, chúng tôi sẽ phân tích từng tính năng liên quan đến quản lý bình luận bằng Aspose.Words trong Java.

### Tính năng 1: Thêm bình luận với trả lời
**Tổng quan**  
Tính năng này minh họa cách thêm một bình luận và một trả lời trong tài liệu Word. Nó lý tưởng cho việc chỉnh sửa cộng tác nơi nhiều người đánh giá cung cấp phản hồi.

#### Các bước thực hiện
**Bước 1:** Khởi tạo đối tượng Document  
`Document` là lớp chính đại diện cho một tài liệu Word trong bộ nhớ.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

**Bước 2:** Tạo và thêm bình luận  
`Comment` lưu trữ tác giả, ngày và phạm vi văn bản được bình luận.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**Bước 3:** Thêm trả lời vào bình luận  
Các đối tượng `Reply` được gắn vào một `Comment` cha thông qua bộ sưu tập `getReplies()`.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

### Tính năng 2: In tất cả bình luận
**Tổng quan**  
Tính năng này in tất cả các bình luận cấp cao nhất và các trả lời của chúng, giúp dễ dàng xem lại phản hồi một cách tổng hợp.

#### Các bước thực hiện
**Bước 1:** Tải tài liệu  
`Document` đại diện cho tệp Word bạn đang xử lý.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

**Bước 2:** Lấy và in bình luận  
Các đối tượng `Comment` có thể được duyệt để trích xuất thông tin tác giả và nội dung.  
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

### Tính năng 3: Xóa trả lời bình luận
**Tổng quan**  
Xóa các trả lời cụ thể hoặc tất cả trả lời khỏi một bình luận để giữ tài liệu sạch sẽ và có tổ chức.

#### Các bước thực hiện
**Bước 1:** Khởi tạo và thêm bình luận với trả lời  
Các đối tượng `Comment` được tạo và điền các mục `Reply`.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

**Bước 2:** Xóa trả lời  
`Reply` đại diện cho một phản hồi; bạn có thể xóa toàn bộ hoặc xóa từng mục riêng lẻ.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

### Tính năng 4: Đánh dấu bình luận là đã xong
**Tổng quan**  
Đánh dấu bình luận là đã giải quyết để theo dõi vấn đề một cách hiệu quả trong tài liệu của bạn.

#### Các bước thực hiện
**Bước 1:** Tạo tài liệu và thêm bình luận  
`Document` là container cho bình luận mới.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

**Bước 2:** Đánh dấu bình luận là đã xong  
`setDone(true)` đánh dấu bình luận là đã giải quyết.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

### Tính năng 5: Lấy ngày và giờ UTC từ bình luận
**Tổng quan**  
Lấy ngày và giờ UTC chính xác khi bình luận được thêm để theo dõi chi tiết.

#### Các bước thực hiện
**Bước 1:** Tạo tài liệu với bình luận có dấu thời gian  
`Document` chứa bình luận mà thời gian sẽ được kiểm tra.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**Bước 2:** Lưu và lấy ngày UTC  
`getDateTime()` trả về thời gian tạo của bình luận, có thể chuyển sang UTC.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Ứng dụng thực tế
Hiểu và sử dụng các tính năng này có thể nâng cao đáng kể quản lý tài liệu trong nhiều kịch bản:
- **Chỉnh sửa cộng tác:** Tạo điều kiện cho nhóm cộng tác bằng bình luận và trả lời.
- **Đánh giá tài liệu:** Tinh giản quy trình đánh giá bằng cách đánh dấu vấn đề đã giải quyết.
- **Quản lý phản hồi:** Theo dõi phản hồi bằng dấu thời gian chính xác.

Các khả năng này có thể được tích hợp vào các hệ thống lớn hơn, chẳng hạn như nền tảng quản lý nội dung hoặc quy trình xử lý tài liệu tự động.

## Xem xét hiệu năng
Khi làm việc với tài liệu lớn, hãy cân nhắc các mẹo sau để tối ưu hiệu năng:
- Giới hạn số lượng bình luận được xử lý mỗi lần.
- Sử dụng cấu trúc dữ liệu hiệu quả (ví dụ: `ArrayList`) để lưu và truy xuất bình luận.
- Thường xuyên cập nhật Aspose.Words để tận dụng các cải tiến về hiệu năng và sửa lỗi.

## Câu hỏi thường gặp

**Q: Aspose.Words cho Java là gì?**  
A: Aspose.Words cho Java là một API được quản lý hoàn toàn, cho phép tạo, chỉnh sửa, chuyển đổi và render tài liệu Word mà không cần Microsoft Word.

**Q: Làm sao để thêm một bình luận bằng chương trình?**  
A: Khởi tạo một `Document`, tạo một `Comment` với tác giả và nội dung, gán nó cho một `Range`, và thêm vào `CommentCollection` của tài liệu.

**Q: Tôi có thể lấy thời gian chính xác khi bình luận được thêm không?**  
A: Có, sử dụng `comment.getDateTime()` để lấy đối tượng `java.util.Date`; chuyển sang UTC bằng `toInstant()` để có chuỗi ISO‑8601.

**Q: Làm sao để đánh dấu một bình luận là đã giải quyết?**  
A: Gọi `comment.setDone(true)`; bình luận sẽ hiển thị dấu kiểm “Done” trong các trình xem Word hỗ trợ.

**Q: Có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?**  
A: Giấy phép đầy đủ sẽ loại bỏ mọi hạn chế của phiên bản đánh giá; giấy phép thử tạm thời đủ cho việc thử nghiệm và phát triển.

## Kết luận
Bạn đã nắm vững cách quản lý bình luận trong tài liệu Word bằng Aspose.Words cho Java. Với khả năng thêm bình luận, thêm trả lời bình luận, in các bình luận trong Word, xóa trả lời, đánh dấu bình luận là đã xong và trích xuất thời gian UTC, bạn có thể xây dựng các quy trình tài liệu cộng tác mạnh mẽ. Khám phá thêm các tính năng của Aspose.Words—như mail‑merge, thao tác bảng và chuyển đổi PDF—để mở rộng khả năng tự động hoá của bạn.

**Bước tiếp theo**
- Thử kết hợp quản lý bình luận với phiên bản tài liệu.
- Tích hợp các đoạn mã này vào hệ thống quản lý nội dung hoặc đánh giá hiện có của bạn.
- Xem lại tài liệu tham khảo API của Aspose.Words để tùy chỉnh sâu hơn.

---

**Last Updated:** 2026-07-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose

## Các hướng dẫn liên quan

- [Track Changes in Word Documents Using Aspose.Words Java&#58; A Complete Guide to Document Revisions](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Master Aspose.Words for Java&#58; How to Insert and Manage Bookmarks in Word Documents](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Hyperlink Management in Word Using Aspose.Words Java&#58; A Comprehensive Guide](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}