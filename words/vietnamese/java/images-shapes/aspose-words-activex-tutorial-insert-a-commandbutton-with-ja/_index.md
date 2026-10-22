---
category: general
date: 2026-08-07
description: Hướng dẫn Aspose.Words ActiveX cho thấy cách thêm điều khiển CommandButton
  vào tài liệu Word bằng Java. Tìm hiểu toàn bộ mã, cấu hình và các bước lưu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: vi
lastmod: 2026-08-07
og_description: Hướng dẫn Aspose.Words ActiveX giải thích cách nhúng điều khiển ActiveX
  CommandButton vào tài liệu Word bằng Java. Thực hiện ví dụ đầy đủ để tạo, cấu hình
  và lưu tài liệu.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Hướng dẫn Aspose.Words ActiveX – Hướng dẫn Java từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Hướng dẫn Aspose.Words ActiveX – chèn CommandButton bằng Java
url: /vi/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hướng dẫn Aspose.Words ActiveX – chèn CommandButton bằng Java

Nếu bạn cần nhúng một điều khiển ActiveX vào tệp Word, **hướng dẫn Aspose.Words ActiveX** này sẽ hướng dẫn bạn qua toàn bộ quá trình. Bạn sẽ thấy cách tạo một tài liệu trống, chèn CommandButton, thiết lập các thuộc tính của nó và lưu kết quả — tất cả bằng mã Java thuần.

Ví dụ sử dụng API Aspose.Words for Java, giúp loại bỏ nhu cầu cài đặt Microsoft Office trên máy chủ xây dựng. Khi hoàn thành hướng dẫn này, bạn có thể tạo các tệp .docx chứa các điều khiển CommandButton hoạt động đầy đủ, sẵn sàng sử dụng trong môi trường Windows.

## Yêu cầu trước

- Java Development Kit (JDK) 8 hoặc mới hơn đã được cài đặt.
- Maven hoặc công cụ xây dựng khác để quản lý các phụ thuộc.
- Giấy phép Aspose.Words for Java (hoặc khóa đánh giá tạm thời) để tránh dấu nước đánh giá.
- Kiến thức cơ bản về cú pháp Java và lập trình hướng đối tượng.

> **Mẹo:** Thêm phụ thuộc Aspose.Words Maven vào file `pom.xml` của bạn để IDE tự động giải quyết các lớp.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Bước 1: Tạo một tài liệu trống mới và một `DocumentBuilder`

`Lớp` `Document` đại diện cho tệp Word trong bộ nhớ, trong khi `DocumentBuilder` cung cấp một API lưu loát để chỉnh sửa tài liệu. Khởi tạo cả hai đối tượng chuẩn bị tài liệu cho các sửa đổi tiếp theo.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Tại sao điều này quan trọng:**  
`DocumentBuilder` theo dõi vị trí con trỏ hiện tại, vì vậy bất kỳ thao tác chèn nào tiếp theo — như thêm một điều khiển — sẽ xuất hiện chính xác ở vị trí bạn mong muốn.

## Bước 2: Chèn điều khiển ActiveX CommandButton

Aspose.Words cung cấp `Forms2OleControl` cho các đối tượng ActiveX. Phương thức `insertForms2OleControl` yêu cầu loại điều khiển, bạn chỉ định thông qua enumeration `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Giải thích:**  
Điều khiển được chèn là một đối tượng dựa trên COM mà Word sẽ hiển thị dưới dạng nút có thể nhấp khi tài liệu được mở trong môi trường Windows.

## Bước 3: Cấu hình các thuộc tính của nút

Sau khi chèn, bạn có thể điều chỉnh tên, chú thích, kích thước và vị trí của nút. Các thuộc tính này ảnh hưởng đến cách điều khiển hiển thị và hoạt động trong Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Tại sao các cài đặt này quan trọng:**  

- **Name** – Cho phép macro VBA tham chiếu đến điều khiển (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Xác định nhãn hiển thị mà người dùng nhấp.
- **Left / Top** – Kiểm soát vị trí so với lề trang.
- **Width / Height** – Đảm bảo kích thước hiển thị nhất quán trên các độ phân giải màn hình khác nhau.

## Bước 4: Lưu tài liệu

Gọi `save` ghi biểu diễn trong bộ nhớ ra một tệp vật lý. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.doc`, `.pdf`, v.v.). Đối với hướng dẫn này, chúng tôi giữ định dạng Word gốc.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Kết quả:**  
Mở `ActiveXDemo.docx` trong Microsoft Word sẽ hiển thị một CommandButton có nhãn **Submit** được đặt tại tọa độ đã chỉ định. Nhấp vào nút sẽ kích hoạt hành vi mặc định (không có mã VBA nào được đính kèm mặc định).

## Mã nguồn đầy đủ

Kết hợp các phần lại, chương trình hoàn chỉnh, có thể chạy được trông như sau:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Kết quả mong đợi

- Một tệp có tên **ActiveXDemo.docx** nằm trong thư mục `output`.
- Khi mở trong Microsoft Word (Windows), tài liệu hiển thị một nút **Submit** có thể nhấp ở vị trí đã định.
- Nút có thể được chọn, di chuyển, hoặc liên kết với mã VBA qua giao diện Word (Developer → Properties).

## Xử lý các biến thể phổ biến

| Kịch bản | Điều chỉnh |
|----------|------------|
| **Lưu dưới dạng .doc** (định dạng cũ) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Thêm trình xử lý sự kiện** | Word không cung cấp các sự kiện ActiveX thông qua Aspose.Words. Bạn phải thêm mã VBA thủ công sau khi tài liệu được tạo. |
| **Nhiều điều khiển** | Lặp lại khối chèn/cấu hình với các giá trị `setName` và `setCaption` khác nhau. |
| **Loại điều khiển khác (ví dụ: CheckBox)** | Sử dụng `Forms2OleControlType.CHECKBOX` trong lời gọi `insertForms2OleControl`. |
| **Nền tảng không phải Windows** | Các điều khiển ActiveX chỉ hiển thị trên Word Windows. Đối với giải pháp đa nền tảng, hãy xem xét các content control (`StructuredDocumentTag`). |

## Thực hành tốt và những cạm bẫy

- **Đăng ký giấy phép sớm** – Đăng ký giấy phép Aspose.Words của bạn trước khi tạo `Document` để tránh thông báo đánh giá.
- **Hệ thống tọa độ** – Vị trí được đo bằng điểm (1 pt = 1/72 in). Chuyển đổi từ pixel hoặc centimet nếu thiết kế UI của bạn sử dụng các đơn vị đó.
- **Đường dẫn tệp** – Sử dụng đường dẫn tuyệt đối hoặc API `Paths` của Java để tránh `FileNotFoundException` khi thư mục đầu ra không tồn tại.
- **An toàn đa luồng** – `Document` và `DocumentBuilder` không an toàn với đa luồng. Tạo các thể hiện riêng cho mỗi luồng nếu bạn tạo tài liệu song song.
- **Kiểm thử** – Xác minh tài liệu được tạo trên phiên bản Word mục tiêu (ví dụ: Word 2016, Word 365) vì các phiên bản cũ hơn có thể hiển thị điều khiển ActiveX khác nhau.

## Kết luận

Hướng dẫn **Aspose.Words ActiveX** này trình bày cách thêm một điều khiển CommandButton vào tài liệu Word một cách lập trình bằng Java. Bạn đã học được cách:

1. Khởi tạo `Document` và `DocumentBuilder`.
2. Chèn `Forms2OleControl` loại `COMMAND_BUTTON`.
3. Đặt tên, chú thích, kích thước và vị trí của nút.
4. Lưu tài liệu dưới dạng tệp .docx chứa điều khiển ActiveX.

Từ đây, bạn có thể khám phá các loại điều khiển bổ sung, tự động chèn macro VBA, hoặc kết hợp các điều khiển ActiveX với các tính năng khác của Aspose.Words như mail‑merge và content control. Thử nghiệm với các bố cục khác nhau và tích hợp các tài liệu được tạo vào quy trình báo cáo lớn hơn dựa trên Java của bạn.

---

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Sử dụng OLE Objects và ActiveX Controls trong Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Chuyển đổi Word sang RTF với Hướng dẫn Aspose.Words cho Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}