---
category: general
date: 2026-10-04
description: Tìm hiểu cách khởi tạo DocumentBuilder cho tài liệu mới và thêm nút ActiveX
  bằng Aspose.Words trong Java. Hướng dẫn từng bước kèm mã đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: vi
lastmod: 2026-10-04
og_description: Khởi tạo DocumentBuilder cho tài liệu mới và nhúng nút lệnh ActiveX
  bằng API Aspose.Words Java. Tham khảo hướng dẫn ngắn gọn này.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Khởi tạo DocumentBuilder cho tài liệu mới – hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Cách khởi tạo DocumentBuilder cho tài liệu mới bằng Aspose.Words
url: /vi/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách khởi tạo DocumentBuilder cho tài liệu mới bằng Aspose.Words

Nếu bạn cần **khởi tạo DocumentBuilder cho tài liệu mới** trong một dự án Java, hướng dẫn này sẽ cho bạn thấy các bước chính xác. Bạn sẽ thấy cách tạo một tệp Word trống, gắn một nút lệnh ActiveX, và lưu kết quả — tất cả trong một mẫu mã tự chứa duy nhất.

Làm việc với các tài liệu Word một cách lập trình thường đồng nghĩa với việc xử lý các chi tiết cấp thấp như các điều khiển biểu mẫu. Khi kết thúc hướng dẫn này, bạn sẽ có thể nhúng một nút ActiveX mà không rời khỏi IDE, điều này hữu ích cho việc tạo mẫu, báo cáo tự động, hoặc các biểu mẫu tương tác.

## Yêu cầu trước

* Cài đặt Java 17 hoặc mới hơn  
* Maven 3.8+ (hoặc Gradle nếu bạn thích)  
* Giấy phép Aspose.Words for Java (bản dùng thử miễn phí đủ cho việc thử nghiệm)  
* Kiến thức cơ bản về cú pháp Java  

Nếu bạn mới dùng Aspose.Words, thư viện này cung cấp một API cấp cao để tạo, chỉnh sửa và lưu các tài liệu Word. Lớp `DocumentBuilder` là điểm vào chính để xây dựng nội dung tài liệu.

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven mới (hoặc thêm vào dự án hiện có) và bao gồm phụ thuộc Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Mẹo chuyên nghiệp:** Giữ phiên bản thư viện luôn cập nhật; các bản phát hành mới hơn bổ sung hỗ trợ cho các điều khiển biểu mẫu bổ sung và cải thiện hiệu năng.

## Bước 2: Khởi tạo `DocumentBuilder` cho tài liệu mới

Phần cốt lõi của hướng dẫn là thao tác **khởi tạo DocumentBuilder cho tài liệu mới**. Bạn đầu tiên tạo một thể hiện `Document` trống, sau đó truyền nó vào hàm tạo `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*​Tại sao điều này quan trọng:* Việc khởi tạo `DocumentBuilder` gắn builder với một đối tượng `Document` cụ thể, cho phép bạn thêm đoạn văn, bảng, hoặc các điều khiển biểu mẫu trực tiếp vào tài liệu đó. Nếu bỏ qua bước này, builder sẽ không có mục tiêu để làm việc.

## Bước 3: Chèn một điều khiển nút lệnh ActiveX

Aspose.Words cung cấp lớp `Forms2OleControl` để nhúng các điều khiển ActiveX cổ điển. Đoạn mã sau thêm một **nút lệnh Forms2OleControl** vào vị trí con trỏ hiện tại.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Nút lệnh ActiveX là gì?

Nút lệnh ActiveX là một thành phần giao diện người dùng cổ điển có thể chạy macro hoặc kích hoạt sự kiện khi người dùng nhấp vào nó trong tài liệu Word. Mặc dù các phiên bản Office hiện đại ưu tiên Content Controls, nhiều mẫu doanh nghiệp vẫn dựa vào ActiveX để duy trì khả năng tương thích ngược.

## Bước 4: Lưu tài liệu

Sau khi chèn điều khiển, bạn chỉ cần gọi `save`. Tệp sẽ chứa nút ActiveX và có thể mở trong Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Khi bạn mở `ActiveXButton.docx` trong Word, bạn sẽ thấy một nút có nhãn **Click Me**. Nhấp vào nút sẽ không thực hiện gì trừ khi bạn gắn một macro, nhưng điều khiển này vẫn hoạt động đầy đủ.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào `src/main/java/com/example/ActiveXButtonDemo.java`. Nó bao gồm tất cả các import và xử lý lỗi cần thiết cho một thử nghiệm nhanh.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document saved to output/ActiveXButton.docx
```

Mở tệp đã tạo trong Microsoft Word 2016 hoặc phiên bản mới hơn; bạn sẽ thấy một nút có nhãn *Click Me* được đặt ở đầu trang đầu tiên.

## Các biến thể phổ biến và trường hợp đặc biệt

| Scenario | Adjustment |
|----------|------------|
| **Thêm nút vào một đoạn văn cụ thể** | Di chuyển con trỏ của builder bằng `builder.moveToParagraph(index, NodeType.PARAGRAPH);` trước khi gọi `insertForms2OleControl`. |
| **Đặt kích thước nút** | Sử dụng `commandButton.setWidth(100);` và `commandButton.setHeight(30);` để xác định kích thước bằng điểm. |
| **Thêm macro vào nút** | Sau khi lưu tài liệu, mở nó trong Word, bật tab Developer, và gắn một macro VBA vào nút một cách thủ công (các điều khiển ActiveX không thể được script trực tiếp từ Aspose.Words). |
| **Định dạng .doc (nhị phân) mục tiêu** | Thay đổi `doc.save(outputPath, SaveFormat.DOC);` để tạo tệp Word 97‑2003 cổ điển. |
| **Chạy trên Android** | Sử dụng Aspose.Words cho Android thông qua API Java của nó; cùng một đoạn mã sẽ hoạt động miễn là thư viện được bao gồm trong APK. |

## Mẹo khắc phục sự cố

* **`java.lang.NoClassDefFoundError`** – Đảm bảo JAR Aspose.Words nằm trong classpath. Maven sẽ tự động thêm nó; đối với các build thủ công, đặt JAR vào `libs/` và thêm vào thư viện của IDE.  
* **Button does not appear in Word** – Kiểm tra tùy chọn *Show legacy forms* đã được bật trong Trust Center của Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – Nếu bạn chạy mã mà không có giấy phép hợp lệ, Aspose.Words sẽ chèn watermark. Đăng ký bản dùng thử miễn phí hoặc mua giấy phép để loại bỏ nó.

## Kết luận

Bây giờ bạn đã biết cách **khởi tạo DocumentBuilder cho tài liệu mới**, chèn một nút lệnh ActiveX, và lưu kết quả bằng Aspose.Words cho Java. Mẫu này cho phép bạn tạo các mẫu Word tương tác một cách lập trình, đặc biệt hữu ích cho báo cáo tự động hoặc quy trình làm việc dựa trên biểu mẫu.

Từ đây bạn có thể khám phá các điều khiển biểu mẫu bổ sung (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, v.v.), kết hợp nút với các macro VBA tùy chỉnh, hoặc tạo các tài liệu đầy đủ tính năng bao gồm bảng, hình ảnh và kiểu dáng — tất cả đều sử dụng cùng một quy trình `DocumentBuilder`.

---

*​Sẵn sàng xây dựng tự động hoá Word phức tạp hơn? Xem các hướng dẫn của chúng tôi về **chèn bảng với DocumentBuilder**, **áp dụng kiểu dáng bằng lập trình**, và **xuất ra PDF với Aspose.Words**.*

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cách lưu tài liệu dưới dạng pdf với Aspose.Words cho Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Thêm watermark vào tài liệu bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}