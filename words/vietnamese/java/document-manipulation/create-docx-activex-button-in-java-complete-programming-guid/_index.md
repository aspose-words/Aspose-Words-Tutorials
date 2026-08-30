---
category: general
date: 2026-08-14
description: Tạo nút ActiveX trong tài liệu docx bằng Java với Aspose.Words. Tìm hiểu
  cách thêm nút biểu mẫu vào Word một cách lập trình và lưu tài liệu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: vi
lastmod: 2026-08-14
og_description: Tạo nút ActiveX trong file docx bằng Java sử dụng Aspose.Words. Hướng
  dẫn này chỉ cho bạn cách thêm nút biểu mẫu trong Word, cấu hình nó và lưu file.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Tạo nút ActiveX cho docx trong Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Tạo nút ActiveX cho docx trong Java – hướng dẫn lập trình đầy đủ
url: /vi/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo nút ActiveX trong file docx bằng Java – hướng dẫn lập trình đầy đủ

Nếu bạn cần **tạo nút ActiveX trong file docx** bằng Java, hướng dẫn này sẽ đưa bạn qua toàn bộ quy trình. Bạn sẽ thấy cách thêm nút biểu mẫu trong Word, cấu hình các thuộc tính của nó, và tạo ra một file .docx sẵn sàng sử dụng.

Làm việc với các điều khiển ActiveX là yêu cầu phổ biến khi tự động hoá các biểu mẫu Word cũ. Trong tutorial này, bạn sẽ học cách **thêm nút biểu mẫu vào tài liệu Word** bằng thư viện Aspose.Words for Java, để có thể nhúng các điều khiển tương tác mà không cần chỉnh sửa thủ công.

## Những gì bạn cần

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java 17 trở lên (mã có thể biên dịch với các phiên bản cũ hơn, nhưng Java 17 được khuyến nghị).
* Aspose.Words for Java 23.10 hoặc mới hơn – tải JAR từ trang web Aspose hoặc thêm phụ thuộc Maven.
* Một IDE (IntelliJ IDEA, Eclipse, hoặc VS Code) hoặc một trình soạn thảo văn bản đơn giản và công cụ xây dựng dòng lệnh.
* Kiến thức cơ bản về cú pháp Java và lập trình hướng đối tượng.

## Cách tạo nút ActiveX trong docx bằng Aspose.Words

Các bước sau đây cho thấy trình tự chính xác cần thiết để **tạo nút ActiveX trong docx** và nhúng chúng vào tài liệu Word.

### Bước 1: Thiết lập dự án và nhập Aspose.Words

Thêm phụ thuộc Aspose.Words vào `pom.xml` nếu bạn dùng Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Hoặc, nếu bạn thích Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Sau khi phụ thuộc được giải quyết, nhập các lớp cần thiết vào file nguồn Java của bạn:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Các import này cho phép bạn truy cập `Document`, `DocumentBuilder`, và API `Forms2OleControl` dùng để chèn các điều khiển ActiveX.

### Bước 2: Tạo một tài liệu trống mới

Khởi tạo một đối tượng `Document`, đại diện cho một file Word rỗng sẵn sàng nhận nội dung.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Việc tạo tài liệu trước đảm bảo rằng builder tiếp theo sẽ hoạt động trên một canvas sạch sẽ.

### Bước 3: Khởi tạo DocumentBuilder

`DocumentBuilder` cung cấp giao diện fluent để chèn văn bản, hình ảnh và các điều khiển. Gắn nó vào tài liệu bạn vừa tạo.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder theo dõi vị trí con trỏ hiện tại trong tài liệu, vì vậy việc chèn tiếp theo sẽ diễn ra đúng nơi bạn cần.

### Bước 4: Chèn một điều khiển ActiveX CommandButton

Sử dụng phương thức `insertForms2OleControl` để nhúng một ActiveX `CommandButton`. Phương thức này trả về một thể hiện `Forms2OleControl` mà bạn có thể cấu hình thêm.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Tại thời điểm này file .docx chứa một placeholder cho nút, nhưng chưa có chú thích hay kích thước hiển thị.

### Bước 5: Cấu hình các thuộc tính của nút

Đặt tên, chú thích và các thuộc tính bố cục cho điều khiển. Những giá trị này quyết định cách nút hiển thị trong Word và cách bạn có thể tham chiếu tới nó sau này qua VBA hoặc các script tự động.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Mẹo chuyên nghiệp:** Word đo vị trí bằng điểm (1 pt ≈ 1/72 in). Điều chỉnh `setTop` và `setLeft` để căn chỉnh nút với nội dung xung quanh.

### Bước 6: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Sử dụng phần mở rộng `.docx` để giữ file ở định dạng Office Open XML hiện đại.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Khi bạn mở file kết quả trong Microsoft Word, bạn sẽ thấy một nút **Submit** được đặt tại tọa độ bạn chỉ định. Nhấn nút trong Word sẽ không kích hoạt hành động nào trừ khi bạn gắn mã VBA, nhưng điều khiển này hoàn toàn hoạt động cho các quy trình làm việc dựa trên biểu mẫu.

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| **Tôi có cần phiên bản Word đặc biệt không?** | Các điều khiển ActiveX được hỗ trợ trong phiên bản desktop của Microsoft Word trên Windows. Chúng không khả dụng trong Word cho Mac hoặc Word Online. |
| **Tôi có thể dùng với file `.doc` không?** | Có. Lưu tài liệu với phần mở rộng `.doc` (`document.save("ActiveXButton.doc")`). API tương tự hoạt động cho định dạng nhị phân cũ hơn. |
| **Nếu nút không hiển thị thì sao?** | Đảm bảo **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** cho phép các điều khiển ActiveX. Ngoài ra, kiểm tra xem tài liệu có được mở ở “Protected View” không. |
| **Tôi có thể thêm các điều khiển ActiveX khác không?** | Chắc chắn. Thay `Forms2OleControlType.COMMAND_BUTTON` bằng `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, v.v. |
| **Có giới hạn kích thước không?** | Kích thước của điều khiển chỉ bị giới hạn bởi bố cục trang. Kích thước quá lớn có thể gây tràn layout. |

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là một lớp Java hoàn chỉnh mà bạn có thể sao chép, biên dịch và chạy. Nó bao gồm tất cả các import, phương thức `main`, và các chú thích nội dòng để dễ hiểu.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Kết quả mong đợi:** Sau khi chạy chương trình, file `ActiveXButton.docx` sẽ xuất hiện trong thư mục làm việc. Mở nó trong Microsoft Word sẽ hiển thị một nút **Submit** có thể nhấn, nằm gần góc trên‑trái của trang đầu tiên.

## Kết luận

Bây giờ bạn đã biết cách **tạo nút ActiveX trong docx** bằng Java sử dụng Aspose.Words, và bạn đã thấy cách **thêm nút biểu mẫu vào tài liệu Word** một cách lập trình. Các bước—cài đặt dự án, tạo tài liệu, chèn điều khiển, cấu hình thuộc tính, và lưu—bao quát toàn bộ quy trình từ đầu đến cuối.

Tiếp theo, bạn có thể khám phá:

* Thêm macro VBA phản hồi khi nhấn nút.
* Nhúng các điều khiển ActiveX khác như hộp kiểm hoặc danh sách.
* Tự động tạo các biểu mẫu đa trang với nhiều yếu tố tương tác.

Hãy thoải mái thử nghiệm với kích thước, vị trí và chú thích để phù hợp với yêu cầu thiết kế biểu mẫu cụ thể của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cách tải HTML và lưu dưới dạng DOCX bằng Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Cách tạo tài liệu PDF với Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}