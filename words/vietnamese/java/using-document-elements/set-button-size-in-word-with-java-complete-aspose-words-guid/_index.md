---
category: general
date: 2026-07-16
description: Đặt kích thước nút một cách lập trình trong tài liệu Word bằng Aspose.Words
  cho Java. Tìm hiểu cách chèn nút ActiveX, đặt vị trí nút và nhiều hơn nữa.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: vi
lastmod: 2026-07-16
og_description: Đặt kích thước nút trong tài liệu Word bằng Java. Hướng dẫn chi tiết
  này chỉ cách chèn nút ActiveX, đặt vị trí nút và thêm nút một cách lập trình.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Đặt Kích Thước Nút trong Word bằng Java – Hướng Dẫn Toàn Diện Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Đặt kích thước nút trong Word bằng Java – Hướng dẫn đầy đủ Aspose.Words
url: /vi/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt Kích Thước Nút trong Word bằng Java – Hướng Dẫn Toàn Diện Aspose.Words

Bạn đã bao giờ tự hỏi làm thế nào để **đặt kích thước nút** bên trong một tệp Word mà không cần mở giao diện người dùng chưa? Bạn không phải là người duy nhất. Khi bạn cần tạo một tài liệu điền form một cách nhanh chóng—ví dụ, một gói chào mừng nhân viên mới với nút “Submit”—việc thực hiện bằng mã sẽ tiết kiệm hàng giờ công việc thủ công.

Trong tutorial này, chúng ta sẽ đi qua các bước **chèn nút ActiveX**, điều chỉnh kích thước, đặt vị trí chính xác, và cuối cùng lưu tệp. Khi hoàn thành, bạn sẽ có thể **thêm nút** một cách lập trình vào bất kỳ tài liệu Word nào bằng Aspose.Words for Java.

## Prerequisites – What You Need Before You Start

- **Java Development Kit (JDK) 8+** – mã chạy trên bất kỳ JDK hiện đại nào.
- Thư viện **Aspose.Words for Java** (tải JAR mới nhất từ trang chính thức).  
- Một **IDE** mà bạn thích—IntelliJ IDEA, Eclipse, hoặc thậm chí một trình soạn thảo văn bản đơn giản cũng được.
- Kiến thức cơ bản về cú pháp Java; không cần hiểu sâu về tự động hoá Word.

> *Pro tip:* Đặt JAR của Aspose.Words vào classpath của dự án, nếu không bạn sẽ gặp `ClassNotFoundException` ngay khi cố gắng import `com.aspose.words.*`.

## Step 1: Create a New Word Document

Điều đầu tiên chúng ta làm là khởi tạo một tài liệu trống và một `DocumentBuilder`. Hãy nghĩ tới builder như một cây bút cho phép chúng ta vẽ bất cứ thứ gì bên trong tệp.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** Đối tượng `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` là công cụ chính cho phép chúng ta chèn đoạn văn, bảng, và—đúng vậy—các điều khiển ActiveX.

## Step 2: Insert ActiveX Button – The “Insert ActiveX Button” Moment

Bây giờ chúng ta **chèn nút activex** vào tài liệu. Aspose.Words cung cấp phương thức tiện lợi `insertForms2OleControl` trả về một đối tượng `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *What’s happening under the hood?* `Forms2OleControlType.COMMAND_BUTTON` thông báo cho Word rằng chúng ta muốn một CommandButton cổ điển, giống như nút bạn kéo từ tab Developer trong giao diện người dùng.

## Step 3: Set Button Size and Location – The Core “Set Button Size” Logic

Đây là nơi từ khóa chính tỏa sáng. Chúng ta sẽ **đặt kích thước nút** và đồng thời **đặt vị trí nút** để điều khiển xuất hiện đúng nơi chúng ta muốn trên trang.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Why you should care:** Điểm (point) là đơn vị đo gốc trong Word (1 point = 1/72 inch). Bằng cách điều chỉnh `setLeft`, `setTop`, `setWidth`, và `setHeight` bạn sẽ có được kiểm soát chính xác từng pixel—không còn “trông ổn trên màn hình của tôi nhưng lại sai trên máy in”.

> *Common pitfall:* Quên đặt chiều rộng hoặc chiều cao sẽ để lại nút ở kích thước mặc định, có thể quá nhỏ để nhấn. Luôn luôn chỉ định cả hai.

## Step 4: Save the Document – “Create Word Document Button” Completed

Cuối cùng, chúng ta ghi tệp ra đĩa. Tên này gợi ý rằng chúng ta đang **tạo một nút trong tài liệu Word** bên trong một .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Khi bạn mở `CommandButtonDemo.docx` trong Microsoft Word, bạn sẽ thấy một nút **Submit** được đặt cách mép trái 100 pt và cách mép trên 150 pt, kích thước 80 × 30 pt. Nhấn vào nó trong giao diện sẽ kích hoạt hành vi mặc định của ActiveX (bạn có thể gắn VBA sau này nếu cần).

### Expected Output Screenshot

![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png "Screenshot of a Word file where the button size has been set using Aspose.Words for Java")

*Alt text:* set button size in a Word document using Java

## Step 5 (Optional): Add More Controls or Style the Button

Nếu bạn cần **thêm nút** một cách lập trình ngoài một nút Submit duy nhất, chỉ cần lặp lại khối chèn với tên và chú thích mới. Bạn cũng có thể điều chỉnh phông chữ, màu nền, hoặc thậm chí gắn macro VBA sau này.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* Giữ mọi kích thước nút đồng nhất để tạo cảm giác chuyên nghiệp. Một cách nhanh là lưu chiều rộng/chiều cao trong các hằng số.

## Common Questions & Edge Cases

### “Can I set the button size using centimeters instead of points?”
API của Word chỉ chấp nhận điểm, nhưng bạn có thể chuyển đổi centimet sang điểm (`points = cm * 28.3465`). Viết một phương thức trợ giúp nhỏ nếu bạn muốn dùng đơn vị mét.

### “What if I need the button to appear on a specific page?”
Sau khi chèn nút, bạn có thể di chuyển con trỏ tới một trang cụ thể bằng `builder.moveToPage(pageNumber)`. Chèn điều khiển ngay sau khi di chuyển, rồi đặt vị trí như đã mô tả ở trên.

### “Does this work with .doc (Word 97‑2003) files?”
Có—Aspose.Words tự động xử lý các định dạng cũ. Chỉ cần thay đổi phần mở rộng tệp trong `doc.save("Demo.doc")`.

## Full, Runnable Example

Dưới đây là toàn bộ chương trình mà bạn có thể sao chép‑dán vào một lớp Java và chạy ngay (giả sử JAR của Aspose.Words đã có trong classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Chạy chương trình, mở `CommandButtonDemo.docx` đã tạo, và bạn sẽ thấy hai nút được kích thước hợp lý, sẵn sàng cho tương tác.

## Conclusion – You’ve Mastered Setting Button Size in Word

Chúng ta vừa đi qua một giải pháp hoàn chỉnh, từ đầu tới cuối cho **đặt kích thước nút** và **đặt vị trí nút** bằng Aspose.Words for Java. Bằng cách làm theo các bước, bạn có thể **chèn nút activex**, **thêm nút** một cách lập trình, và cuối cùng **tạo nút trong tài liệu Word** hoạt động chính xác như mong muốn.

Tiếp theo bạn muốn làm gì? Hãy thử nhúng nút vào trong một ô bảng, hoặc gắn macro VBA để kiểm tra các trường form trước khi gửi. Mẫu này cũng áp dụng cho các điều khiển ActiveX khác như hộp kiểm hay combo box—chỉ cần thay `Forms2OleControlType.COMMAND_BUTTON` bằng giá trị enum phù hợp.

Nếu gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới. Chúc bạn lập trình vui vẻ và tận hưởng sức mạnh của việc tự động tạo tài liệu Word!

## What Should You Learn Next?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ và giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to remove footers from Word documents using Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}