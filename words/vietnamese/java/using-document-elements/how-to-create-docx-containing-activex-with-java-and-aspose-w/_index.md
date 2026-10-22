---
category: general
date: 2026-09-27
description: Tạo file docx chứa ActiveX trong Java bằng Aspose.Words. Học cách chèn
  nút lệnh ActiveX từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: vi
lastmod: 2026-09-27
og_description: Tạo file docx chứa ActiveX trong Java với Aspose.Words. Tham khảo
  hướng dẫn này để chèn nút lệnh ActiveX và lưu tài liệu.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Tạo file docx chứa ActiveX trong Java – hướng dẫn chi tiết
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Cách tạo file docx chứa ActiveX bằng Java và Aspose.Words
url: /vi/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo docx chứa ActiveX bằng Java và Aspose.Words

Nếu bạn cần **tạo docx chứa ActiveX**, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh. Bạn sẽ học cách **chèn nút lệnh ActiveX** vào tệp Word bằng Aspose.Words cho Java, sau đó lưu kết quả dưới dạng .docx có thể mở trong Microsoft Word.

Tạo tài liệu Word một cách lập trình giúp bạn tránh việc chỉnh sửa thủ công và đảm bảo tính nhất quán trong các báo cáo, hợp đồng hoặc mẫu biểu mẫu. Các bước dưới đây bao gồm mọi thứ từ thiết lập dự án đến xử lý các vấn đề thường gặp, để bạn có thể tích hợp kỹ thuật này vào bất kỳ ứng dụng Java nào.

## Yêu cầu trước

* Java Development Kit (JDK) 8 hoặc mới hơn đã được cài đặt.
* Maven 3.6+ (hoặc công cụ xây dựng khác mà bạn ưa thích).
* Tệp giấy phép Aspose.Words cho Java (phiên bản dùng thử miễn phí hoạt động cho việc thử nghiệm).
* Microsoft Word được cài đặt trên máy mục tiêu nếu bạn muốn kiểm tra điều khiển ActiveX một cách trực quan.

Các mục này là bắt buộc vì Aspose.Words cung cấp API tạo tài liệu, trong khi Word cần thiết để hiển thị điều khiển ActiveX.

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven mới hoặc thêm phụ thuộc Aspose.Words vào tệp `pom.xml` hiện có:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Mẹo chuyên nghiệp:** Giữ phiên bản Aspose.Words đồng bộ với ghi chú phát hành chính thức để được hưởng các bản sửa lỗi và tính năng ActiveX mới.

## Bước 2: Viết mã Java tạo tài liệu

Tạo một lớp có tên `ActiveXDocxCreator`. Mã dưới đây bao gồm tất cả các import cần thiết, một phương thức `main`, và các chú thích chi tiết giải thích mỗi thao tác.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Tại sao mỗi dòng lại quan trọng

* `Document` là container cho tất cả nội dung Word. Tạo một instance mới sẽ cung cấp cho bạn một canvas sạch.
* `DocumentBuilder` cung cấp một API lưu loát để chèn các phần tử; nó tự động theo dõi điểm chèn.
* `insertForms2OleControl()` tạo một placeholder điều khiển OLE chung. Aspose.Words coi nó như một container ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` thông báo cho Word rằng placeholder phải hiển thị dưới dạng CommandButton.
* `setCaption("Click Me")` xác định văn bản hiển thị trên nút.
* `setLeft` và `setTop` đặt vị trí nút tương đối với lề trang. Điều chỉnh các giá trị này để phù hợp với bố cục của bạn.
* `setWidth` và `setHeight` là tùy chọn nhưng cải thiện giao diện của nút, đặc biệt khi kích thước mặc định quá nhỏ.
* `doc.save` ghi cấu trúc trong bộ nhớ ra tệp .docx thực tế mà Word có thể mở.

## Bước 3: Xác minh tài liệu đã tạo

Mở `output/ActiveXCommandButton.docx` trong Microsoft Word:

1. Tài liệu sẽ hiển thị một trang duy nhất với một nút có nhãn **Click Me** được đặt gần góc trên‑trái.
2. Nếu nút không xuất hiện, kiểm tra rằng **điều khiển ActiveX đã được bật** trong Trust Center của Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. Nút chỉ hoạt động trên các phiên bản Word cho Windows hỗ trợ ActiveX. Trên macOS hoặc Word dựa trên web, điều khiển sẽ được hiển thị dưới dạng hình ảnh tĩnh.

## Bước 4: Xử lý các trường hợp ngoại lệ phổ biến

| Situation | Reason | Recommended action |
|-----------|--------|--------------------|
| Nút không xuất hiện sau khi mở tệp | Cài đặt bảo mật của Word chặn ActiveX | Bật “Run all controls without restrictions” cho các vị trí tin cậy. |
| Không thể mở .docx đã tạo | Phiên bản Aspose.Words không tương thích | Nâng cấp lên phiên bản Aspose.Words mới nhất; các phiên bản cũ có thể không nhúng đúng các phần OLE cần thiết. |
| Bạn cần nút thực thi macro | ActiveX đơn lẻ không chứa mã macro | Kết hợp điều khiển ActiveX với macro VBA xử lý sự kiện `Click`. Sử dụng phương thức `DocumentBuilder.insertOleObject` để nhúng mẫu hỗ trợ macro. |
| Bố cục sai trên các kích thước trang khác nhau | Tọa độ là điểm tuyệt đối | Sử dụng `builder.getPageSetup().setPageWidth` và `setPageHeight` để chuẩn hoá kích thước trang trước khi đặt vị trí điều khiển. |

## Bước 5: Mở rộng giải pháp

Bạn có thể chèn các điều khiển ActiveX khác bằng cách thay đổi enum `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words cũng hỗ trợ chèn **hộp văn bản ActiveX**, **hộp danh sách**, và **hộp combo**. Các phương pháp định vị tương tự (`setLeft`, `setTop`, `setWidth`, `setHeight`) vẫn áp dụng.

Nếu bạn cần đặt nhiều điều khiển, gọi `builder.insertForms2OleControl()` nhiều lần và điều chỉnh tọa độ của mỗi điều khiển cho phù hợp.

## Tệp nguồn hoàn chỉnh

Dưới đây là toàn bộ tệp `ActiveXDocxCreator.java` sẵn sàng để sao chép và dán:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Chạy chương trình này sẽ tạo ra một **docx chứa ActiveX** mà bạn có thể phân phối cho người dùng cuối cần các biểu mẫu tương tác.

## Kết luận

Bây giờ bạn đã biết cách **tạo docx chứa ActiveX** bằng Java và Aspose.Words, và cách **chèn nút lệnh ActiveX** một cách lập trình. Bài hướng dẫn đã bao gồm thiết lập dự án, mã nguồn đầy đủ, các bước xác minh, và các chiến lược xử lý các vấn đề thường gặp.

Từ đây bạn có thể khám phá:

* Thêm macro VBA để phản hồi khi nhấn nút.
* Nhúng các điều khiển ActiveX khác như hộp kiểm hoặc hộp combo.
* Tự động tạo các biểu mẫu đa trang với dữ liệu động.

Thử nghiệm với các tọa độ, kích thước và loại điều khiển khác nhau để phù hợp với bố cục tài liệu cụ thể của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Sử dụng OLE Objects và ActiveX Controls trong Aspose.Words cho Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}