---
category: general
date: 2026-11-15
description: Chỉnh sửa tài liệu Word bằng lập trình để chèn nút lệnh. Tìm hiểu cách
  thêm nút, đặt tên nút lệnh và tạo nút biểu mẫu Word trong vài phút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: vi
lastmod: 2026-11-15
og_description: Chỉnh sửa tài liệu Word bằng lập trình và chèn nút lệnh. Hướng dẫn
  này chỉ cách thêm nút, đặt tên nút lệnh và tạo nhanh nút biểu mẫu trong Word.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Chỉnh sửa tài liệu Word bằng lập trình – thêm nút lệnh
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Chỉnh sửa tài liệu Word bằng lập trình và thêm nút lệnh
url: /vi/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chỉnh sửa tài liệu Word bằng chương trình và thêm nút lệnh

Nếu bạn cần **chỉnh sửa tài liệu Word bằng chương trình**, cách nhanh nhất là sử dụng API Aspose.Words. Hướng dẫn này cho bạn thấy chính xác **cách thêm nút** vào các điều khiển, cấu hình chú thích của chúng, và **đặt tên nút lệnh** để tài liệu có thể hoạt động như một biểu mẫu đơn giản. Khi kết thúc, bạn sẽ có một tệp *.docx* có thể chỉnh sửa hoàn toàn chứa một nút lệnh hoạt động sẵn sàng cho việc xử lý tiếp theo.

Bạn sẽ học cách **chèn từ nút lệnh**, **tạo từ nút biểu mẫu**, và quản lý các thuộc tính của nút mà không cần mở Word thủ công. Yêu cầu duy nhất là môi trường phát triển Java cơ bản và thư viện Aspose.Words for Java.

## Yêu cầu trước

- Java 17 hoặc mới hơn (mã cũng hoạt động với Java 8+)
- Aspose.Words for Java (tải xuống từ [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Một tài liệu Word hiện có (`input.docx`) mà bạn muốn chỉnh sửa
- Quen thuộc với Maven hoặc Gradle để thêm phụ thuộc Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Bước 1: Tải tài liệu Word

Hoạt động đầu tiên khi bạn **chỉnh sửa tài liệu Word bằng chương trình** là tải tệp nguồn vào một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp Word trong bộ nhớ, cho phép bạn thao tác nội dung của nó.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Tại sao điều này quan trọng:** Việc tải tài liệu tạo ra một cấu trúc giống DOM mà Aspose.Words có thể duyệt và sửa đổi. Bỏ qua bước này sẽ khiến bạn không có đối tượng để chèn nút.

## Bước 2: Tạo một `DocumentBuilder` để chỉnh sửa tài liệu

`DocumentBuilder` hoạt động như một con trỏ bên trong tệp Word. Nó cho phép bạn chèn văn bản, hình ảnh và các điều khiển biểu mẫu tại vị trí hiện tại.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mẹo:** Nếu bạn cần nút trong một đoạn cụ thể, hãy di chuyển builder trước bằng `builder.moveToParagraph(index, true);`.

## Bước 3: Chèn một Forms2OleControl (nút lệnh)

Bây giờ chúng ta trả lời câu hỏi trung tâm **cách thêm nút** trong tệp Word. Phương thức `insertForms2OleControl()` tạo ra một nút lệnh *Forms2.0* kế thừa, là điều khiển tương thích nhất trên các phiên bản Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Trường hợp đặc biệt:** Điều khiển Forms2.0 chỉ hiển thị trong *Design Mode* của Word. Nếu bạn cần một nút ActiveX mới hơn, hãy xem xét `insertOleControl()` thay thế, nhưng điều khiển kế thừa này hoạt động cho hầu hết các kịch bản tự động.

## Bước 4: Cấu hình các thuộc tính của nút

Sau khi chèn điều khiển, bạn có thể **đặt tên nút lệnh** và **chèn từ nút lệnh** (chú thích) để làm cho nó thân thiện với người dùng.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Tại sao lại cần các thuộc tính này?**  
> - `setName` cung cấp cho nút một định danh mà VBA hoặc các công cụ bên ngoài có thể tham chiếu.  
> - `setCaption` là nhãn hiển thị, thực tế **tạo từ nút biểu mẫu** mà người dùng cuối nhấp.

Bạn cũng có thể điều chỉnh kích thước, vị trí, hoặc thêm macro bằng cách truy cập đối tượng OLE bên dưới, nhưng những chủ đề này nằm ngoài phạm vi của hướng dẫn nhanh này.

## Bước 5: Lưu tài liệu đã chỉnh sửa

Cuối cùng, lưu các thay đổi vào một tệp mới. Bước này **tạo từ nút biểu mẫu** trong tài liệu đầu ra.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Kết quả:** Khi mở `output.docx` trong Microsoft Word, bạn sẽ thấy một nút có nhãn “Submit”. Khi chuyển Word sang *Design Mode* (Developer → Design Mode), bạn có thể nhấp đúp vào nút để gắn macro hoặc đơn giản sử dụng nó như một chỗ giữ chỗ trong biểu mẫu.

### Kết quả mong đợi

Khi bạn mở tệp đã lưu:

- Điểm chèn con trỏ được thay thế bằng một nút.
- Nút hiển thị chú thích **Submit**.
- Tên nội bộ của nút là **cmdSubmit**, bạn có thể tham chiếu trong VBA hoặc các script tự động bên ngoài.

## Câu hỏi thường gặp và các biến thể

### Cách thêm nút vào một đoạn cụ thể?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Cách chèn nút vào trong ô bảng?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Nếu tôi cần một nút lớn hơn thì sao?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Cách **chèn từ nút lệnh** bằng một ngôn ngữ khác (ví dụ, C#)?

Logic tương tự; thay thế cú pháp Java bằng các tương đương trong C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Mẹo chuyên nghiệp và những lưu ý

- **Mẹo:** Luôn gọi `builder.moveToDocumentEnd()` trước khi chèn nút nếu bạn muốn nó ở cuối cùng của tài liệu.  
- **Cẩn thận:** Lưu vào cùng một tệp bạn đã mở có thể làm hỏng tài liệu nếu xảy ra ngoại lệ. Hãy sử dụng đường dẫn đầu ra riêng như đã minh họa.  
- **Tương thích:** Nút Forms2.0 kế thừa hoạt động trong Word 2007‑2021. Đối với Word trên web, hãy cân nhắc sử dụng các điều khiển nội dung thay thế.  
- **Hiệu suất:** Tải các tài liệu rất lớn (>100 MB) có thể tiêu tốn nhiều bộ nhớ. Sử dụng `Document.load(InputStream, LoadOptions)` với `LoadOptions.setLoadFormat(LoadFormat.DOCX)` để giới hạn việc sử dụng tài nguyên.

## Ví dụ đầy đủ hoạt động

Dưới đây là chương trình Java hoàn chỉnh, sẵn sàng chạy. Sao chép nó vào một lớp có tên `WordButtonDemo.java`, điều chỉnh đường dẫn tệp, và chạy `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Chạy chương trình và mở `output.docx` để xác nhận nút xuất hiện như mong đợi.

## Kết luận

Bạn bây giờ đã biết cách **chỉnh sửa tài liệu Word bằng chương trình** để **chèn từ nút lệnh**, **tạo từ nút biểu mẫu**, và **đặt tên nút lệnh** bằng Aspose.Words for Java. Cách tiếp cận này loại bỏ việc chỉnh sửa thủ công, cho phép xử lý hàng loạt các biểu mẫu, và tích hợp liền mạch với các quy trình làm việc tự động.

Tiếp theo, bạn có thể khám phá:

- Thêm macro VBA vào nút (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Sử dụng **content controls** để có trải nghiệm biểu mẫu phong phú hơn (`builder.insertCheckBox()` v.v.)  
- Tự động chèn hàng loạt trên nhiều tài liệu bằng một vòng lặp  

Hãy tự do thử nghiệm với kích thước, vị trí và xử lý sự kiện của nút để phù hợp với kịch bản cụ thể của bạn. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}