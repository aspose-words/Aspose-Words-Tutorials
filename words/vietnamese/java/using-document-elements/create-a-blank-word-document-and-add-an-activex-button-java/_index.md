---
category: general
date: 2026-10-16
description: Tạo một tài liệu Word trống bằng Java và tìm hiểu cách thêm nút ActiveX,
  đặt chú thích cho nó và điều chỉnh kích thước bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: vi
lastmod: 2026-10-16
og_description: Tạo một tài liệu Word trống bằng Java, sau đó thêm một nút ActiveX,
  đặt tiêu đề cho nó và xác định kích thước bằng Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Tạo tài liệu Word trống và nhúng nút ActiveX – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Tạo một tài liệu Word trống và thêm nút ActiveX (Java)
url: /vi/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu Word trống và thêm nút ActiveX (Java)

Nếu bạn cần **tạo một tài liệu Word trống** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Java và Aspose.Words. Bạn cũng sẽ học cách **thêm một nút ActiveX**, **đặt chú thích cho nút**, và **đặt kích thước nút** sao cho điều khiển hiển thị chính xác như bạn mong muốn.

Hướng dẫn này bao gồm:

* Khởi tạo một tệp Word rỗng bằng Aspose.Words for Java.  
* Chèn một điều khiển ActiveX `CommandButton`.  
* Cấu hình chú thích và kích thước của nút.  
* Lưu tệp `.docx` cuối cùng.

Bạn nên có kiến thức cơ bản về Java và phiên bản mới nhất của thư viện Aspose.Words for Java (mã hoạt động với 23.9 trở lên). Không cần phụ thuộc bổ sung.

![Tạo một tài liệu Word trống với nút ActiveX](/images/activex-button-example.png){: .align-center alt="Tạo một tài liệu Word trống với nút ActiveX"}

## Tạo một tài liệu Word trống với Aspose.Words

Bước đầu tiên là tạo một đối tượng `Document` trống. Đối tượng này đại diện cho toàn bộ tệp Word trong bộ nhớ và cung cấp lớp `DocumentBuilder` để chỉnh sửa.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Tại sao điều này quan trọng:**  
Tạo một tài liệu trống cung cấp cho bạn một nền sạch, tránh các kiểu hoặc phần ẩn có thể gây cản trở cho các phép tính bố cục sau này.

## Thêm nút ActiveX vào tài liệu

Aspose.Words cho phép bạn nhúng các điều khiển ActiveX cổ điển thông qua lớp `Forms2OleControl`. Đoạn mã sau chèn một điều khiển `CommandButton` tại vị trí con trỏ hiện tại.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Mẹo:** Giá trị `setOleClassName` `"Forms.CommandButton.1"` là ProgID cho nút Microsoft Forms tiêu chuẩn. Sử dụng một ProgID khác (ví dụ, `"Forms.CheckBox.1"`) sẽ chèn một loại điều khiển khác.

## Đặt chú thích cho nút

Chú thích là văn bản xuất hiện trên mặt nút. Bạn có thể thay đổi nó bất kỳ lúc nào trước khi lưu tài liệu.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Tại sao bạn cần điều này:** Người dùng chỉ hiểu một điều khiển khi mục đích của nó rõ ràng. Đặt một chú thích có ý nghĩa cải thiện tính khả dụng, đặc biệt khi tài liệu được mở trong Word trên Windows.

## Đặt kích thước nút

Vị trí và kích thước được chỉ định bằng điểm (1 point = 1/72 inch). Điều chỉnh các giá trị để phù hợp với bố cục của bạn.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Các biến thể phổ biến:**

| Kịch bản | Điều chỉnh |
|----------|------------|
| Nút lớn hơn cho màn hình cảm ứng | Tăng `setWidth` và `setHeight` một cách tỷ lệ |
| Nút được căn giữa trên trang | Tính `left = (pageWidth - width) / 2` |
| Nhiều nút trong một cột | Tăng `setTop` cho mỗi nút mới |

## Lưu tài liệu chứa nút ActiveX

Cuối cùng, ghi tài liệu ra đĩa. Định dạng `.docx` giữ lại điều khiển ActiveX cho các phiên bản Windows của Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Kết quả mong đợi:** Mở `ActiveXCommandButton.docx` trong Word (Windows) sẽ hiển thị một trang trống với một nút có thể nhấp được mang nhãn **Click Me** được đặt cách lề trái 100 pt và cách lề trên 200 pt.

## Ví dụ đầy đủ, có thể chạy

Sao chép toàn bộ lớp dưới đây vào IDE của bạn, thêm JAR Aspose.Words for Java vào classpath của dự án, và chạy nó.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Chạy chương trình sẽ tạo `ActiveXCommandButton.docx` trong thư mục làm việc. Mở nó bằng Microsoft Word (Windows) để xác nhận rằng nút xuất hiện chính xác như đã cấu hình.

## Tại sao cách tiếp cận này được đề xuất

* **Sự đơn giản:** Chỉ sử dụng API cốt lõi của Aspose.Words; không cần COM interop hay thư viện bổ sung.  
* **Tính di động:** Mã chạy trên bất kỳ nền tảng nào hỗ trợ Java, mặc dù điều khiển ActiveX chỉ hoạt động trên các phiên bản Windows của Word.  
* **Dễ bảo trì:** Tất cả các thuộc tính (chú thích, kích thước, vị trí) được đặt qua các phương thức rõ ràng, tự mô tả, giúp việc điều chỉnh trong tương lai trở nên đơn giản.

## Những khó khăn thường gặp và cách tránh chúng

| Rủi ro | Giải pháp |
|---------|------------|
| Nút không hiển thị trong Word trên macOS hoặc Linux | Các điều khiển ActiveX chỉ hỗ trợ Windows. Sử dụng một điều khiển khác (ví dụ, một content control) cho tài liệu đa nền tảng. |
| Chú thích bị cắt ngắn | Đảm bảo chiều rộng nút đủ rộng cho văn bản; tăng `setWidth` hoặc sử dụng chú thích ngắn hơn. |
| Nút chồng lên nội dung khác | Điều chỉnh giá trị `setTop` và `setLeft`, hoặc chèn một đoạn văn mới trước điều khiển để tạo không gian riêng. |

## Các bước tiếp theo

Bây giờ bạn đã có thể **tạo một tài liệu Word trống**, **thêm một nút ActiveX**, **đặt chú thích cho nút**, và **đặt kích thước nút**, bạn có thể khám phá:

* Thêm mã xử lý sự kiện qua macro VBA (cần nhúng mô-đun macro).  
* Chèn nhiều điều khiển trong bố cục bảng cho các tài liệu dạng biểu mẫu.  
* Sử dụng API **FormField** của Aspose.Words cho các giải pháp biểu mẫu đa nền tảng.

Thử nghiệm với các kích thước, vị trí và chú thích khác nhau để phù hợp với thiết kế tài liệu của bạn. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Thêm watermark vào tài liệu bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}