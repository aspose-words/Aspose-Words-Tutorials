---
category: general
date: 2026-09-18
description: Tạo tài liệu trống trong Java và thêm nút ActiveX. Học cách chèn nút
  lệnh, xây dựng biểu mẫu tương tác và lưu tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: vi
lastmod: 2026-09-18
og_description: Tạo tài liệu trống trong Java và nhúng nút lệnh ActiveX. Hãy làm theo
  hướng dẫn từng bước này để xây dựng một biểu mẫu tương tác và lưu tệp Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Tạo tài liệu trống với nút lệnh tương tác trong Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Tạo tài liệu trống với nút lệnh tương tác trong Word bằng Java
url: /vi/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu trống với nút lệnh tương tác trong Word bằng Java

Nếu bạn cần **create blank document** chứa một nút có thể nhấp, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words for Java. Bạn sẽ học cách xây dựng một biểu mẫu tương tác, thêm một nút ActiveX, và cuối cùng lưu tệp Word—tất cả trong một vài bước ngắn gọn.

Nhúng một nút lệnh biến một tệp .docx tĩnh thành một biểu mẫu chức năng mà người dùng cuối có thể tương tác trực tiếp trong Microsoft Word. Bài hướng dẫn này cũng đề cập đến **how to insert command button**, xử lý các vấn đề thường gặp, và mở rộng giải pháp cho các biểu mẫu phức tạp hơn.

## Yêu cầu trước

* Java 17 hoặc mới hơn (mã được biên dịch với JDK 17+)
* Aspose.Words for Java 23.9 hoặc mới hơn – thư viện cung cấp `Document`, `DocumentBuilder`, và `Forms2OleControl`.
* Một IDE hoặc công cụ xây dựng (Maven/Gradle) có thể thêm phụ thuộc Aspose.Words.
* Kiến thức cơ bản về cú pháp Java và các khái niệm tài liệu Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Bước 1: Tạo tài liệu trống

Hoạt động đầu tiên là khởi tạo một đối tượng `Document` mới. Đối tượng này đại diện cho một tệp Word trống sẵn sàng cho nội dung.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Tạo một tài liệu trống cung cấp cho bạn một canvas sạch, điều này rất quan trọng khi bạn muốn **create word document** một cách lập trình mà không có bất kỳ mẫu nào có sẵn.

## Bước 2: Khởi tạo DocumentBuilder

`DocumentBuilder` là lớp chính để thêm văn bản, bảng và các điều khiển biểu mẫu. Nó hoạt động trên `Document` mà bạn vừa tạo.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder duy trì vị trí chèn hiện tại, vì vậy các lệnh tiếp theo sẽ ảnh hưởng đến vị trí đúng trong tệp.

## Bước 3: Chèn điều khiển nút lệnh Forms2Ole

Aspose.Words cung cấp lớp `Forms2OleControl` cho các điều khiển ActiveX. Để **add activex button**, bạn yêu cầu loại `COMMANDBUTTON` từ builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Phương thức `insertForms2OleControl` chèn điều khiển tại vị trí con trỏ hiện tại của builder. Vì điều khiển này là đối tượng ActiveX, nó chỉ hoạt động trong phiên bản desktop của Microsoft Word, không phải trong Word Online.

## Bước 4: Cấu hình giao diện và vị trí của nút

Bạn có thể đặt chú thích, kích thước và vị trí của nút bằng các phương thức setter của điều khiển. Giá trị vị trí được đo bằng điểm (1 point = 1/72 inch).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Tại sao cần cấu hình các thuộc tính này?* Đặt `Top` và `Left` đảm bảo nút hiển thị ở vị trí mong muốn trên trang, trong khi `Caption` xác định nhãn hiển thị cho người dùng. Nếu bạn bỏ qua chiều rộng/chiều cao, Word sẽ gán kích thước mặc định, có thể không phù hợp với thiết kế của bạn.

### Mẹo chuyên nghiệp
Nếu bạn dự định thêm nhiều điều khiển, hãy gọi `builder.moveToDocumentEnd()` trước mỗi lần chèn để tránh các đối tượng chồng lên nhau.

## Bước 5: Lưu tài liệu với nút lệnh được nhúng

Cuối cùng, ghi tài liệu ra đĩa. Phần mở rộng tệp phải là `.docx` (hoặc `.doc` cho các phiên bản Word cũ) để giữ lại điều khiển ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Khi bạn mở `CommandButton.docx` trong Microsoft Word, bạn sẽ thấy một nút có nhãn **Click Me**. Nhấp vào nó sẽ kích hoạt hành động ActiveX mặc định (mặc định không làm gì). Bạn có thể sau này gắn macro hoặc script VBA để định nghĩa hành vi tùy chỉnh.

## Cách chèn nút lệnh vào biểu mẫu hiện có (tùy chọn)

Nếu bạn đã có một biểu mẫu với các trường văn bản và muốn **create interactive form** bao gồm một nút, hãy thực hiện các bước bổ sung sau:

1. Tải tài liệu hiện có: `Document doc = new Document("ExistingForm.docx");`
2. Di chuyển builder đến vị trí mong muốn: `builder.moveToParagraph(5, 0); // 6th paragraph, first node`
3. Chèn nút như đã mô tả ở Bước 3.
4. Điều chỉnh `Top`/`Left` của nút dựa trên bố cục của đoạn văn.

Cách tiếp cận này cho phép bạn làm phong phú bất kỳ mẫu Word đã có sẵn nào với một nút ActiveX mà không cần tạo lại toàn bộ tệp.

## Các trường hợp đặc biệt và khắc phục sự cố

| Tình huống | Cần kiểm tra | Cách khắc phục đề xuất |
|-----------|---------------|-----------------|
| Nút không hiển thị trong Word | Đảm bảo bạn mở tệp trong phiên bản desktop của Word (Word Online sẽ loại bỏ ActiveX). | Mở tệp trong Word 2016+ desktop. |
| Chú thích bị cắt ngắn | Kiểm tra độ rộng của nút có đủ để chứa văn bản hay không. | Tăng `setWidth` cho đến khi chú thích vừa. |
| Lưu gây ra `IOException` | Xác nhận thư mục đầu ra tồn tại và bạn có quyền ghi. | Tạo thư mục hoặc chạy chương trình với quyền cao hơn. |
| Nhiều nút chồng lên nhau | Con trỏ của builder có thể chưa di chuyển sau lần chèn trước. | Gọi `builder.moveToDocumentEnd()` trước khi chèn mỗi điều khiển mới. |

## Ví dụ đầy đủ có thể chạy

Dưới đây là một chương trình Java hoàn chỉnh, tự chứa mà bạn có thể sao chép, biên dịch và chạy. Nó minh họa **create blank document**, **add activex button**, và **save word document** trong một luồng.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Kết quả mong đợi**

```
Document created: CommandButton.docx
```

Mở `CommandButton.docx` sẽ hiển thị một trang duy nhất với một nút có nhãn **Click Me** được đặt cách mép trên và trái 100 pt.

## Kết luận

Bây giờ bạn đã biết cách **create blank document**, nhúng một **ActiveX button**, và biến một tệp Word đơn giản thành một **interactive form**. Bằng cách nắm vững **how to insert command button**, bạn có thể mở rộng mẫu này để thêm các hộp kiểm, hộp combo, hoặc thậm chí logic tùy chỉnh dựa trên VBA.

Tiếp theo, hãy xem xét khám phá các chủ đề liên quan sau:

* **Create interactive form** với các trường văn bản (`builder.insertField`)  
* **Add activex button** chạy macro VBA (`builder.insertOleObject`)  
* **Create word document** từ mẫu bằng cách sử dụng `Document(docTemplatePath)`  
* Chuyển đổi .docx kết quả sang PDF trong khi giữ lại nút (lưu ý: PDF sẽ hiển thị nút dưới dạng hình ảnh tĩnh).

Bạn có thể tự do thử nghiệm kích thước, vị trí và chú thích của nút để phù hợp với thiết kế UI của mình. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tạo dự án Vba trong tài liệu Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Tạo tài liệu Word mới](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}