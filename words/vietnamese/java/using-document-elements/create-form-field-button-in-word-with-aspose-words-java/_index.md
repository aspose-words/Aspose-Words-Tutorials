---
category: general
date: 2026-10-13
description: Tạo nút trường biểu mẫu trong Word bằng Aspose.Words cho Java. Tìm hiểu
  cách chèn nút lệnh vào các trường biểu mẫu Word và đặt chú thích cho nút lệnh trong
  vài bước đơn giản.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: vi
lastmod: 2026-10-13
og_description: Tạo nút trường biểu mẫu trong Word bằng Aspose.Words cho Java. Hướng
  dẫn này cho thấy cách chèn các trường nút lệnh trong Word và đặt chú thích cho nút
  lệnh một cách nhanh chóng.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Tạo nút trường biểu mẫu trong Word – Hướng dẫn Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Tạo nút trường biểu mẫu trong Word bằng Aspose.Words Java
url: /vi/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo nút trường biểu mẫu trong Word bằng Aspose.Words Java

Nếu bạn cần **tạo nút trường biểu mẫu** trong tài liệu Word, hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình sử dụng Aspose.Words for Java. Cho dù bạn đang xây dựng mẫu biểu mẫu điền sẵn hoặc thêm các điều khiển tương tác vào báo cáo, bạn sẽ học cách **chèn trường biểu mẫu command button word** và **đặt chú thích cho command button** với ít mã nhất.

Bài hướng dẫn bao gồm mọi thứ từ thiết lập Maven đến một ví dụ có thể chạy đầy đủ, vì vậy bạn có thể sao chép‑dán mã, chạy nó và xem tệp `.docx` chứa một nút có thể nhấp chuột sẵn sàng cho việc tùy chỉnh thêm.

## Yêu cầu trước

- Java 17 (hoặc mới hơn) đã được cài đặt và cấu hình trên máy của bạn.
- Maven 3.6+ để quản lý phụ thuộc.
- Một IDE hoặc trình soạn thảo văn bản mà bạn chọn (ví dụ: IntelliJ IDEA, VS Code).
- Giấy phép Aspose.Words for Java hợp lệ (bản dùng thử miễn phí hoạt động cho việc đánh giá).

## Bước 1: Thêm Aspose.Words vào dự án Maven của bạn

Tạo một tệp `pom.xml` (hoặc chỉnh sửa tệp hiện có) và thêm phụ thuộc Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Mẹo:** Giữ số phiên bản luôn cập nhật. Các bản phát hành mới bổ sung hỗ trợ cho các tính năng Word mới nhất và cải thiện hiệu năng.

## Bước 2: Khởi tạo tài liệu trống và một `DocumentBuilder`

`Lớp DocumentBuilder` cung cấp một API lưu loát để chỉnh sửa tài liệu Word. Trong bước này chúng ta tạo một `Document` rỗng và gắn một builder vào nó.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Việc tạo tài liệu là nền tảng cho các đối tượng **tạo nút trường biểu mẫu** sau này trong hướng dẫn.

## Bước 3: Chèn trường biểu mẫu nút lệnh

Aspose.Words cung cấp lớp `Forms2OleControl` cho các điều khiển biểu mẫu OLE. Để **chèn trường biểu mẫu command button word**, gọi `insertForms2OleControl` với giá trị enum `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Phương thức trả về một thể hiện `Forms2OleControl` mà chúng ta có thể cấu hình trước khi lưu.

## Bước 4: Xác định kích thước và vị trí của nút

Một nút lệnh cần kích thước và vị trí cụ thể trên trang. Điều chỉnh chiều rộng, chiều cao và tọa độ cho phù hợp với bố cục của bạn.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Tinh chỉnh các giá trị này đảm bảo nút xuất hiện chính xác ở vị trí bạn muốn trong tài liệu cuối cùng.

## Bước 5: **Đặt chú thích cho command button**

Văn bản hiển thị trên nút được điều khiển bởi phương thức `setCaption`. Đây là nơi chúng ta **đặt chú thích cho command button** để hướng dẫn người dùng.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Bạn có thể thay thế `"Click Me"` bằng bất kỳ nhãn nào phù hợp với mục đích của biểu mẫu, chẳng hạn như `"Submit"` hoặc `"Approve"`.

## Bước 6: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Tệp kết quả chứa nút tương tác và có thể mở trong Microsoft Word hoặc LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Chạy chương trình sẽ tạo ra `CommandButtonDemo.docx`. Mở nó trong Word sẽ hiển thị một nút có nhãn **Click Me** được đặt cách bên trái 50 pts và cách trên 100 pts của trang.

### Kết quả mong đợi

- Một tệp `.docx` có tên `CommandButtonDemo.docx`.
- Tài liệu chứa một trang duy nhất với một trường biểu mẫu nút lệnh.
- Nút hiển thị chú thích bạn đã đặt (ví dụ, **Click Me**).

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cách thích nghi |
|-----------|-----------------|
| **Nhiều nút** | Gọi `insertForms2OleControl` nhiều lần, điều chỉnh `setLeft`/`setTop` cho mỗi nút mới. |
| **Chú thích khác nhau cho mỗi nút** | Sử dụng `setCaption` với một chuỗi duy nhất sau mỗi lần chèn. |
| **Nút trong ô bảng** | Di chuyển con trỏ vào ô mong muốn bằng `builder.moveTo(cell.getFirstParagraph())` trước khi chèn điều khiển. |
| **Định dạng Word cũ (.doc)** | Lưu bằng `doc.save("Demo.doc", SaveFormat.DOC);` – nút lệnh được giữ lại. |
| **Biểu mẫu chỉ đọc** | Sau khi chèn, đặt `commandButton.setEnabled(false);` để ngăn người dùng tương tác. |

## Mẹo cho triển khai vững chắc

- **Xác thực kích thước**: Chiều rộng quá lớn có thể khiến nút tràn lề trang.
- **Áp dụng giấy phép**: Nếu không có giấy phép hợp lệ, Aspose.Words sẽ thêm watermark vào tài liệu được tạo. Áp dụng giấy phép sớm bằng `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Kiểm thử**: Mở tệp đã tạo trong Word và bật **Design Mode** (Developer → Design Mode) để xem thuộc tính của nút.

## Tổng hợp mã nguồn đầy đủ

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Sao chép mã vào tệp có tên `InsertCommandButtonDemo.java`, biên dịch bằng Maven (`mvn compile`), và chạy (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Tài liệu được tạo sẽ xuất hiện trong thư mục gốc của dự án.

## Kết luận

Bây giờ bạn đã biết cách **tạo nút trường biểu mẫu** trong Word bằng Aspose.Words for Java, cách **chèn trường biểu mẫu command button word**, và cách **đặt chú thích cho command button** một cách lập trình. Ví dụ toàn diện này cung cấp cho bạn nền tảng vững chắc để xây dựng các tài liệu Word phong phú, tương tác hơn — dù bạn cần một nút gửi duy nhất hay một bộ đầy đủ các điều khiển biểu mẫu.

### Tiếp theo là gì?

- Khám phá các điều khiển biểu mẫu khác như hộp kiểm (`Forms2OleControlType.CHECKBOX`) và hộp văn bản (`Forms2OleControlType.TEXTBOX`).
- Kết hợp các trường biểu mẫu với mail‑merge để tạo ra các bảng câu hỏi cá nhân hoá.
- Sử dụng API `FormField` của Aspose.Words để đọc dữ liệu do người dùng nhập sau khi tài liệu đã được điền.

Hãy tự do thử nghiệm với các kích thước, chú thích và vị trí khác nhau. Khi bạn đã thành thạo các nút lệnh, việc thêm các biểu mẫu đầy đủ tính năng vào quy trình tự động Word của bạn sẽ trở nên đơn giản. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}