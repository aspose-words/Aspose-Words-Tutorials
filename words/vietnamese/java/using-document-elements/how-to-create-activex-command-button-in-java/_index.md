---
category: general
date: 2026-10-07
description: Tạo nút lệnh ActiveX trong Java và thêm nút lệnh vào tài liệu Word một
  cách lập trình. Tìm hiểu cách đặt vị trí trái và trên của nút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: vi
lastmod: 2026-10-07
og_description: Tạo nút lệnh ActiveX trong Java để nhúng các điều khiển tương tác
  vào tài liệu Word của bạn. Tìm hiểu cách thêm nút lệnh một cách lập trình, đặt vị
  trí và tùy chỉnh giao diện của nó.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Tạo nút lệnh ActiveX trong Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Cách tạo nút lệnh ActiveX trong Java
url: /vi/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo nút lệnh ActiveX trong Java

Nếu bạn cần **tạo nút lệnh ActiveX** trong một tài liệu Word bằng Java, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được mà **thêm nút lệnh một cách lập trình**, đặt vị trí bằng `setLeft` và `setTop`, và lưu kết quả dưới dạng tệp `.docx`.

Nhúng một nút tương tác cho phép bạn xây dựng biểu mẫu, tự động hoá quy trình, hoặc thu thập dữ liệu người dùng trực tiếp trong tệp Word. Các bước dưới đây bao gồm mọi thứ từ thiết lập dự án đến kiểm tra cuối cùng, để bạn có thể sao chép mã vào dự án của mình mà không bỏ sót chi tiết nào.

## Yêu cầu trước

- JDK 17 hoặc mới hơn đã được cài đặt  
- Maven 3.8+ (hoặc công cụ xây dựng bạn ưa thích)  
- Aspose.Words for Java 23.9 hoặc sau – thư viện cung cấp `DocumentBuilder` và hỗ trợ điều khiển OLE  
- Kiến thức cơ bản về cú pháp Java và các khái niệm hướng đối tượng  

Nếu bạn đang sử dụng Maven, thêm phụ thuộc vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Mẹo chuyên nghiệp:** Sử dụng phiên bản Aspose.Words mới nhất để được hưởng các bản sửa lỗi và tính năng OLE mới.

## Bước 1: Tạo tài liệu trống mới và một DocumentBuilder

Bước đầu tiên để **tạo nút lệnh ActiveX** là khởi tạo một `Document` trống và một `DocumentBuilder`. Builder cung cấp cho bạn một API mượt mà để chèn nội dung, bao gồm các điều khiển OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho tệp Word trong bộ nhớ, trong khi `DocumentBuilder` hoạt động như một con trỏ cho phép bạn đặt các phần tử một cách chính xác ở vị trí mong muốn.

## Bước 2: Chèn điều khiển nút lệnh OLE

Các điều khiển ActiveX được chèn dưới dạng đối tượng OLE. Aspose.Words cung cấp lớp `Forms2OleControl` cho mục đích này.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Khi bạn gọi `insertForms2OleControl()`, Aspose tự động tạo một hình dạng placeholder để chứa nút ActiveX.

## Bước 3: Cấu hình thuộc tính của nút

Bây giờ bạn **thêm nút lệnh một cách lập trình** các chi tiết như ProgID, caption và kích thước. ProgID phổ biến nhất cho một nút lệnh là `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Cách đặt vị trí trái trên của nút

Việc đặt vị trí cho nút là nơi từ khóa phụ **how to set button left top** trở nên liên quan. Các phương thức `setLeft` và `setTop` nhận các giá trị tính bằng điểm (1 point = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Điều chỉnh các số này để phù hợp với bố cục của bạn. Ví dụ, để căn nút với một ô bảng, tính toán tọa độ của ô và truyền chúng vào `setLeft`/`setTop`.

## Bước 4: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Tệp sẽ chứa nút ActiveX sẵn sàng để tương tác khi mở trong Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Chạy phương thức `main` sẽ tạo ra `CommandButton.docx`. Mở tệp trong Word, bật nội dung nếu được yêu cầu, và bạn sẽ thấy một nút có thể nhấp được với nhãn **Click Me** được đặt tại tọa độ bạn đã chỉ định.

![Create ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="Ảnh chụp màn hình tạo nút lệnh ActiveX trong Java hiển thị nút bên trong tài liệu Word"}

## Các biến thể phổ biến và trường hợp đặc biệt

### Thêm nhiều nút

Nếu bạn cần nhiều nút, lặp lại **Bước 2** và **Bước 3** cho mỗi điều khiển. Hãy nhớ điều chỉnh `setLeft` và `setTop` để các nút không chồng lên nhau.

### Thay đổi hành vi của nút

Nút ActiveX có thể chạy macro VBA khi được nhấp. Để gắn macro, đặt thuộc tính `setOnAction` với tên macro:

```java
commandButton.setOnAction("MyMacro");
```

Đảm bảo tài liệu mục tiêu chứa mô-đun VBA tương ứng; nếu không Word sẽ hiển thị lỗi.

### Ghi chú về khả năng tương thích

- Nút chỉ hoạt động trong các phiên bản Word trên máy tính để bàn hỗ trợ ActiveX (ví dụ, Word cho Windows). Nó sẽ hiển thị dưới dạng hình ảnh tĩnh trong Word cho Mac hoặc các trình chỉnh sửa trực tuyến.  
- Nếu bạn hướng tới môi trường hỗn hợp, hãy cân nhắc sử dụng **content control** (`RichTextContentControl`) thay vì điều khiển ActiveX.

## Mã nguồn đầy đủ để tham khảo

Dưới đây là ví dụ đầy đủ, tự chứa mà bạn có thể sao chép vào một dự án Maven mới và chạy ngay lập tức.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Kết quả mong đợi:** Sau khi thực thi, bạn sẽ tìm thấy `CommandButton.docx` trong thư mục làm việc của dự án. Mở tệp trong Microsoft Word sẽ hiển thị một nút tại vị trí đã chỉ định với caption “Click Me”.

## Kết luận

Bây giờ bạn đã biết cách **tạo nút lệnh ActiveX** trong Java, **thêm nút lệnh một cách lập trình** vào tài liệu Word, và kiểm soát chính xác bố cục của nó bằng các phương pháp **how to set button left top**. Kỹ thuật này mở ra cánh cửa cho các biểu mẫu Word phong phú, tương tác, có thể kích hoạt macro, khởi chạy ứng dụng bên ngoài, hoặc thu thập dữ liệu người dùng trực tiếp trong tài liệu.

### Các bước tiếp theo

- Khám phá các điều khiển ActiveX khác như `Forms.TextBox.1` hoặc `Forms.CheckBox.1`.  
- Kết hợp nhiều điều khiển với một mô-đun VBA để triển khai các biểu mẫu đầy đủ tính năng.  
- Thay thế ActiveX bằng content controls nếu bạn cần khả năng tương thích đa nền tảng.  

Hãy tự do thử nghiệm với kích thước, caption và vị trí để phù hợp với thiết kế UI của bạn. Nếu gặp vấn đề, hãy kiểm tra lại phiên bản Aspose.Words bạn đang dùng có hỗ trợ điều khiển OLE không, và xác nhận rằng cài đặt bảo mật của Word cho phép thực thi ActiveX. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Nhúng Đối Tượng OLE và Điều Khiển ActiveX trong Tài Liệu Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tạo hình chữ nhật trong Word bằng Java – Hướng Dẫn Đầy Đủ](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}