---
title: So sánh các tài liệu để tìm sự khác biệt
linktitle: So sánh các tài liệu để tìm sự khác biệt
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách so sánh các tài liệu để tìm sự khác biệt bằng Aspose.Words trong Java. Hướng dẫn từng bước của chúng tôi đảm bảo quản lý tài liệu chính xác.
weight: 12
url: /vi/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So sánh các tài liệu để tìm sự khác biệt

## Giới thiệu

Bạn đã bao giờ tự hỏi làm thế nào để phát hiện ra mọi điểm khác biệt giữa hai tài liệu Word chưa? Có thể bạn đang sửa đổi một tài liệu hoặc cố gắng tìm những thay đổi do cộng tác viên thực hiện. So sánh thủ công có thể rất tẻ nhạt và dễ xảy ra lỗi, nhưng với Aspose.Words for Java, mọi việc trở nên dễ dàng! Thư viện này cho phép bạn tự động so sánh tài liệu, đánh dấu các bản sửa đổi và hợp nhất các thay đổi một cách dễ dàng.

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, hãy đảm bảo bạn đã chuẩn bị những thông tin sau:  
1. Bộ công cụ phát triển Java (JDK) được cài đặt trên hệ thống của bạn.  
2.  Aspose.Words cho thư viện Java. Bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/java/).  
3. Môi trường phát triển như IntelliJ IDEA hoặc Eclipse.  
4. Có kiến thức cơ bản về lập trình Java.  
5.  Giấy phép Aspose hợp lệ. Nếu bạn không có, hãy lấy một[giấy phép tạm thời ở đây](https://purchase.aspose.com/temporary-license/).

## Nhập gói

Để sử dụng Aspose.Words, bạn cần phải nhập các lớp cần thiết. Dưới đây là các lớp cần nhập:

```java
import com.aspose.words.*;
import java.util.Date;
```

Hãy đảm bảo các gói này được thêm chính xác vào các phụ thuộc của dự án bạn.


Trong phần này, chúng tôi sẽ chia nhỏ quy trình thành các bước đơn giản.


## Bước 1: Thiết lập tài liệu của bạn

Để bắt đầu, bạn cần hai tài liệu: một tài liệu đại diện cho bản gốc và một tài liệu đại diện cho phiên bản đã chỉnh sửa. Sau đây là cách bạn tạo chúng:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Điều này tạo ra hai tài liệu trong bộ nhớ với nội dung cơ bản. Bạn cũng có thể tải các tài liệu Word hiện có bằng cách sử dụng`new Document("path/to/document.docx")`.


## Bước 2: Kiểm tra các bản sửa đổi hiện có

Các bản sửa đổi trong tài liệu Word thể hiện các thay đổi được theo dõi. Trước khi so sánh, hãy đảm bảo không có tài liệu nào chứa các bản sửa đổi đã tồn tại trước đó:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Nếu có bản sửa đổi, bạn có thể chấp nhận hoặc từ chối chúng trước khi tiếp tục.


## Bước 3: So sánh các tài liệu

 Sử dụng`compare` phương pháp để tìm ra sự khác biệt. Phương pháp này so sánh tài liệu mục tiêu (`doc2`) với tài liệu nguồn (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Đây:
- AuthorName là tên của người thực hiện thay đổi.
- Ngày là dấu thời gian so sánh.


## Bước 4: Xử lý sửa đổi

Sau khi so sánh, Aspose.Words sẽ tạo ra các bản sửa đổi trong tài liệu nguồn (`doc1`). Chúng ta hãy phân tích những bản sửa đổi này:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Vòng lặp này cung cấp thông tin chi tiết về từng bản sửa đổi, chẳng hạn như loại thay đổi và văn bản bị ảnh hưởng.


## Bước 5: Chấp nhận tất cả các bản sửa đổi

Nếu bạn muốn tài liệu nguồn (`doc1`) để phù hợp với tài liệu mục tiêu (`doc2`), chấp nhận tất cả các bản sửa đổi:

```java
doc1.getRevisions().acceptAll();
```

 Bản cập nhật này`doc1` để phản ánh tất cả những thay đổi được thực hiện trong`doc2`.


## Bước 6: Lưu tài liệu đã cập nhật

Cuối cùng, lưu tài liệu đã cập nhật vào đĩa:

```java
doc1.save("Document.Compare.docx");
```

Để xác nhận các thay đổi, hãy tải lại tài liệu và xác minh không còn bản sửa đổi nào nữa:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Bước 7: Xác minh tính bình đẳng của tài liệu

Để đảm bảo các tài liệu giống hệt nhau, hãy so sánh văn bản của chúng:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Nếu các văn bản trùng khớp, xin chúc mừng, bạn đã so sánh và đồng bộ hóa các tài liệu thành công!


## Phần kết luận

So sánh tài liệu không còn là công việc nhàm chán nữa, nhờ Aspose.Words for Java. Chỉ với một vài dòng mã, bạn có thể xác định sự khác biệt, xử lý các bản sửa đổi và đảm bảo tính nhất quán của tài liệu. Cho dù bạn đang quản lý một dự án viết cộng tác hay kiểm toán các tài liệu pháp lý, tính năng này là một công cụ thay đổi cuộc chơi.

## Câu hỏi thường gặp

### Tôi có thể so sánh tài liệu với hình ảnh và bảng không?  
Có, Aspose.Words hỗ trợ so sánh các tài liệu phức tạp, bao gồm cả những tài liệu có hình ảnh, bảng và định dạng.

### Tôi có cần giấy phép để sử dụng tính năng này không?  
 Có, cần có giấy phép để có đầy đủ chức năng. Nhận một[giấy phép tạm thời ở đây](https://purchase.aspose.com/temporary-license/).

### Sẽ thế nào nếu đã có bản sửa đổi trước đó?  
Bạn phải chấp nhận hoặc từ chối chúng trước khi so sánh các tài liệu để tránh xung đột.

### Tôi có thể đánh dấu những sửa đổi trong tài liệu không?  
Có, Aspose.Words cho phép bạn tùy chỉnh cách hiển thị bản sửa đổi, chẳng hạn như làm nổi bật các thay đổi.

### Tính năng này có khả dụng trong các ngôn ngữ lập trình khác không?  
Có, Aspose.Words hỗ trợ nhiều ngôn ngữ, bao gồm .NET và Python.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
