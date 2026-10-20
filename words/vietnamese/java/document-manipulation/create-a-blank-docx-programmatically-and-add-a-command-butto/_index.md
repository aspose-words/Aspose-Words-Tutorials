---
category: general
date: 2026-10-20
description: Tạo một tệp DOCX trống bằng lập trình và nhúng một nút lệnh bằng Java.
  Tìm hiểu toàn bộ mã tạo tài liệu Word để lưu Word có nút và đặt chú thích cho nút
  lệnh.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: vi
lastmod: 2026-10-20
og_description: Tạo một tệp DOCX trống bằng lập trình và nhúng một nút lệnh. Thực
  hiện theo hướng dẫn Java từng bước này để lưu Word có nút và đặt chú thích cho nút
  lệnh.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Tạo một tài liệu DOCX trống bằng lập trình – thêm nút lệnh
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Tạo một tài liệu DOCX trống bằng lập trình và thêm nút lệnh
url: /vi/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu DOCX trống bằng chương trình và thêm nút lệnh

Nếu bạn cần **tạo một tài liệu DOCX trống bằng chương trình**, hướng dẫn này sẽ chỉ cho bạn cách nhúng một nút lệnh trực tiếp vào tệp. Bạn sẽ nhận được toàn bộ *mã tạo tài liệu Word* lưu một tài liệu Word có nút, cho phép bạn **đặt chú thích nút lệnh**, và hoạt động với thư viện Aspose.Words for Java mới nhất.

Việc nhúng các điều khiển tương tác vào tệp DOCX hữu ích khi bạn muốn phân phối các mẫu có thể kích hoạt macro, khởi chạy chương trình bên ngoài, hoặc chỉ đơn giản là hướng dẫn người dùng bằng một nút “Click Me” có thể nhấn. Các bước dưới đây bao gồm mọi thứ từ khởi tạo tài liệu trống đến việc lưu tệp cuối cùng lên đĩa.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java 17 hoặc mới hơn đã được cài đặt.  
* Maven (hoặc công cụ xây dựng ưa thích của bạn) để quản lý các phụ thuộc.  
* Aspose.Words for Java 23.9 hoặc mới hơn. Thêm phụ thuộc vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Một IDE như IntelliJ IDEA hoặc VS Code (bất kỳ trình soạn thảo nào hỗ trợ Java đều được).

## Tạo một tài liệu DOCX trống bằng chương trình – từng bước

Các phần sau chia quy trình thành các bước rõ ràng, được đánh số. Mỗi bước giải thích **tại sao** nó cần thiết, không chỉ **cái gì** để gõ.

### Bước 1: Khởi tạo một tài liệu trống mới

Một tài liệu trống là nền mà bạn sẽ đặt nút lệnh lên. Aspose.Words cung cấp lớp `Document` cho mục đích này.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Why this matters*: Bắt đầu với một `Document` rỗng đảm bảo không có định dạng ẩn hoặc điều khiển tồn tại nào can thiệp vào nút bạn sẽ thêm sau này.

### Bước 2: Thiết lập `DocumentBuilder`

`DocumentBuilder` là một công cụ hỗ trợ cho phép bạn chèn nội dung, bao gồm các điều khiển OLE, mà không cần thao tác ở mức độ node thấp.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: Builder duy trì vị trí con trỏ hiện tại, vì vậy nút sẽ được đặt chính xác ở vị trí bạn chỉ định.

### Bước 3: Chèn một nút lệnh OLE

Word xem các điều khiển tương tác như là các đối tượng OLE (Object Linking and Embedding). Aspose.Words cung cấp `Forms2OleControl` cho việc này.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Why this matters*: Việc chèn điều khiển tạo ra một placeholder mà bạn có thể cấu hình sau (loại, chú thích, vị trí).

### Bước 4: Cấu hình nút – loại, chú thích và vị trí

Bạn phải xác định loại điều khiển (`COMMANDBUTTON`), đặt một chú thích mà người dùng có thể nhìn thấy, và đặt nó trên trang.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Why this matters*:  
* **Type** cho Word biết điều khiển hoạt động như một nút có thể nhấn.  
* **Caption** là văn bản người dùng thấy; việc thay đổi nó là cách bạn **đặt chú thích nút lệnh**.  
* **Left** và **Top** kiểm soát vị trí chính xác, điều này rất quan trọng khi bạn **thêm nút lệnh vào tài liệu Word** cần bố cục chính xác.

### Bước 5: Lưu tài liệu với nút đã nhúng

Cuối cùng, ghi tệp ra đĩa. Tệp kết quả có thể mở trong Microsoft Word, nơi nút sẽ hoạt động đầy đủ.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Why this matters*: Bước này **lưu Word có nút** để điều khiển tồn tại trên các máy khác nhau. Tệp có thể được phân phối như một mẫu hoặc dùng trong các pipeline tạo báo cáo tự động.

## Ví dụ hoàn chỉnh hoạt động

Sao chép toàn bộ lớp dưới đây vào một tệp có tên `CommandButtonDemo.java`, điều chỉnh `YOUR_DIRECTORY` thành đường dẫn thực tế, và chạy nó bằng `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Kết quả mong đợi

Khi bạn mở `CommandButton.docx` trong Microsoft Word:

* Tài liệu hoàn toàn trống ngoại trừ một nút có nhãn **Click Me**.  
* Nhấn nút sẽ hiển thị hành vi mặc định của Word (nó không làm gì trừ khi có macro được gắn), xác nhận rằng điều khiển OLE đã được nhúng đúng cách.

## Các câu hỏi thường gặp & trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Can I change the button size?** | Có. Sử dụng `commandButton.setWidth(double)` và `commandButton.setHeight(double)` để điều chỉnh kích thước tính bằng điểm. |
| **What if I need a macro attached to the button?** | Nút chỉ là một điều khiển OLE. Bạn phải thêm macro VBA vào tài liệu thủ công hoặc qua các tiện ích `addMacro` của API `Document` trong Aspose.Words. |
| **Will the button work in LibreOffice?** | LibreOffice hỗ trợ một số điều khiển OLE hạn chế. Nút sẽ hiển thị, nhưng hành vi khi nhấn có thể khác nhau. |
| **How to add multiple buttons?** | Lặp lại Các Bước 3‑4 với một thể hiện `Forms2OleControl` mới. Điều chỉnh `setLeft`/`setTop` cho mỗi nút để tránh chồng lấn. |
| **Is the code compatible with .NET?** | Logic tương tự áp dụng, nhưng bạn sẽ dùng các lớp của `Aspose.Words` cho .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Mẹo thực tiễn

* **Pro tip:** Sử dụng `builder.moveToDocumentEnd()` trước khi chèn nút nếu bạn muốn nó ở cuối cùng của tài liệu, bất kể nội dung trước đó.  
* **Watch out for:** Giá trị `Left`/`Top` quá nhỏ có thể đặt nút ra ngoài khu vực có thể in, khiến nó không hiển thị trong chế độ xem bố cục của Word.  
* **Performance note:** Chèn nhiều điều khiển OLE có thể làm tăng kích thước tệp. Nếu bạn chỉ cần một dấu hiệu trực quan, hãy cân nhắc dùng một `Shape` đơn giản với siêu liên kết thay thế.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu DOCX trống bằng chương trình** và nhúng một nút lệnh hoạt động đầy đủ bằng Java. Hướng dẫn đã bao quát toàn bộ quy trình *mã tạo tài liệu Word*, minh họa cách **lưu Word có nút**, chỉ ra cách đúng để **thêm các phần tử nút lệnh vào Word**, và giải thích cách **đặt chú thích nút lệnh**.

Từ đây bạn có thể:

* Thêm nhiều điều khiển OLE (checkbox, combo box) để tạo các biểu mẫu phong phú hơn.  
* Gắn macro VBA để nút thực hiện các hành động tùy chỉnh.  
* Kết hợp kỹ thuật này với mail‑merge tài liệu để tạo các mẫu động, tương tác.

Hãy tự do thử nghiệm các kiểu nút, vị trí và các điều khiển bổ sung để phù hợp với yêu cầu kinh doanh cụ thể của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong bài viết này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word trống với nút lệnh – hướng dẫn chi tiết](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Cách chèn nút ActiveX trong Word – Đặt chú thích nút](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Tạo tài liệu Word trống bằng Java – Hướng dẫn đầy đủ Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}