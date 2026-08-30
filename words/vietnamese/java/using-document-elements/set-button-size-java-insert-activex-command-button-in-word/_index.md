---
category: general
date: 2026-07-29
description: 'hướng dẫn Java đặt kích thước nút: học cách chèn nút lệnh ActiveX vào
  tài liệu Word bằng Java và Aspose.Words, cùng với việc điều chỉnh kích thước và
  tạo tài liệu trống.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: vi
lastmod: 2026-07-29
og_description: Hướng dẫn đặt kích thước nút Java cho thấy cách chèn một nút lệnh
  ActiveX vào tệp Word bằng Java, điều chỉnh kích thước của nó và lưu tài liệu một
  cách lập trình.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: đặt kích thước nút Java – Thêm nút lệnh ActiveX vào Word bằng Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Đặt kích thước nút Java – Chèn nút lệnh ActiveX trong Word
url: /vi/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt kích thước nút java – Chèn nút lệnh ActiveX trong Word

Bạn đã bao giờ tự hỏi **how to set button size java** khi tự động hoá tài liệu Word chưa? Có thể bạn đang xây dựng một công cụ báo cáo cần một nút “Submit” có thể nhấn được ngay trong file .docx. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình — tạo một tài liệu Word trống, chèn một nút lệnh ActiveX, và thiết lập rõ ràng chiều rộng và chiều cao của nó — tất cả bằng Java và Aspose.Words.

Chúng tôi cũng sẽ trả lời câu hỏi “how to insert activex” thường gặp của nhiều nhà phát triển. Khi kết thúc, bạn sẽ có một chương trình chạy được, tạo ra một file Word chứa nút lệnh có kích thước hoàn hảo, sẵn sàng cho việc tùy chỉnh thêm.

---

## Những gì bạn cần

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- **Java Development Kit (JDK) 8 trở lên** – mã nguồn sẽ biên dịch với bất kỳ JDK hiện đại nào.
- **Aspose.Words for Java** (phiên bản mới nhất tính đến tháng 7 2026). Tải JAR từ [Aspose website](https://products.aspose.com/words/java) hoặc qua Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Một IDE hoặc trình soạn thảo văn bản đơn giản—IntelliJ IDEA, Eclipse, hoặc VS Code đều được.
- Một thư mục nơi bạn muốn lưu **CommandButton.docx** được tạo ra.

Đó là tất cả. Không cần thư viện interop Office bổ sung, không cần thủ thuật COM, chỉ Java thuần.

---

## Triển khai từng bước

Chúng ta sẽ chia giải pháp thành năm bước logic. Mỗi bước có tiêu đề H2 riêng; một trong số chúng chứa **từ khóa chính** để đáp ứng SEO.

### 1. Thiết lập dự án và nhập Aspose.Words

Đầu tiên, tạo một dự án Maven (hoặc Gradle) mới và thêm phụ thuộc Aspose.Words như ở trên. Sau đó, nhập các lớp cần thiết vào file Java của bạn:

```java
import com.aspose.words.*;
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang dùng IDE, hãy để nó tự động nhập các lớp. Điều này tiết kiệm rất nhiều thời gian gõ và tránh lỗi chính tả.

### 2. java create blank word Document

Bây giờ chúng ta thực sự **java create blank word** tài liệu. Đây là nền tảng mà sau này chúng ta sẽ **insert command button word** lên.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Đối tượng `Document` đại diện cho toàn bộ file Word trong bộ nhớ. Tại thời điểm này file chưa có trang, chưa có văn bản—chỉ là một tờ trắng.

### 3. Khởi tạo DocumentBuilder và chèn điều khiển ActiveX

`DocumentBuilder` là một trợ giúp cho phép chúng ta thêm nội dung, đoạn văn, bảng, và, vâng, các điều khiển ActiveX. Đây là nơi chúng ta trả lời **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` là lớp bao bọc của Aspose cho một đối tượng OLE. Bằng cách chỉ định `COMMANDBUTTON` chúng ta yêu cầu Word nhúng một nút lệnh ActiveX cổ điển.

### 4. How to Set Button Size Java – Điều chỉnh chiều rộng và chiều cao

Bây giờ là phần cốt lõi của hướng dẫn: **how to set button size java**. Điều khiển này cung cấp một số thuộc tính bố cục—`Left`, `Top`, `Width`, và `Height`. Đặt chúng trực tiếp sẽ kiểm soát cách nút hiển thị trên trang.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Tại sao lại dùng các số này? Trong Word, một point bằng 1/72 inch. Vì vậy chiều rộng `120` point tương đương khoảng 1.67 inch—đủ lớn để nhãn đọc được, nhưng không quá to. Bạn có thể điều chỉnh các giá trị này cho phù hợp với bố cục của mình; cùng các thuộc tính này cũng trả lời câu hỏi **how to set button** mà bạn có thể đang thắc mắc.

> **Lưu ý:** Nếu bạn cần một loại nút khác (ví dụ: checkbox), hãy thay `Forms2OleControlType.COMMANDBUTTON` bằng giá trị enum tương ứng.

### 5. Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối trên máy của bạn. Sau khi chạy chương trình, mở file đã tạo trong Microsoft Word. Bạn sẽ thấy một nút có nhãn “Click Me” được đặt cách lề trái 100 pts và cách lề trên 200 pts, kích thước chính xác như chúng ta đã thiết lập.

---

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là lớp Java đầy đủ, sẵn sàng chạy. Sao chép‑dán vào `CommandButtonActiveX.java`, điều chỉnh đường dẫn xuất, và nhấn **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Kết quả mong đợi:** Mở `CommandButton.docx` trong Word sẽ hiển thị một trang duy nhất với nút “Click Me” có thể nhấn được, đặt ở vị trí giữa trang. Kích thước của nút khớp với các giá trị bạn đã đặt, xác nhận rằng **set button size java** hoạt động như mong muốn.

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

### Nút không xuất hiện trong Word thì sao?

- **Kiểm tra phiên bản Word.** Các điều khiển ActiveX yêu cầu phiên bản Word trên máy tính để bàn; Word Online sẽ loại bỏ chúng.
- **Đảm bảo giấy phép Aspose.Words đã được áp dụng** (nếu bạn dùng phiên bản trả phí). Phiên bản đánh giá không có giấy phép có thể chèn watermark nhưng vẫn hiển thị điều khiển.

### Tôi có thể thay đổi phông chữ hoặc màu sắc của nút không?

Có. Sau khi chèn điều khiển, bạn có thể truy cập đối tượng OLE bên trong và thao tác các thuộc tính VBA. Đây là chủ đề nâng cao—hãy xem `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` để đặt màu chữ đỏ, ví dụ.

### Làm sao xử lý sự kiện click của nút?

Nút lệnh ActiveX phát ra sự kiện VBA `Click`. Để nút hoạt động, bạn cần nhúng một macro trong cùng tài liệu. Aspose.Words có thể thêm một module macro qua API `Document.getMacros()`, nhưng mã macro phải được viết bằng VBA.

### Còn các loại nút khác thì sao?

Aspose.Words hỗ trợ nhiều giá trị `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, v.v. Thay đổi hằng enum trong lời gọi `insertForms2OleControl` để thử nghiệm.

---

## Mẹo chuyên nghiệp cho mã chuẩn sản xuất

1. **Sử dụng hằng số cho các giá trị bố cục** – giúp việc điều chỉnh trong tương lai dễ dàng hơn.
2. **Bao bọc đường dẫn lưu trong đối tượng `Path`** để tránh các ký tự phân tách phụ thuộc vào nền tảng.
3. **Giải phóng Document** (hoặc dùng try‑with‑resources) nếu bạn xử lý nhiều file trong một vòng lặp.
4. **Kiểm tra thư mục đầu ra** trước khi gọi `save` để tránh `FileNotFoundException`.

---

## Kết luận

Bạn vừa học **set button size java** bằng cách tạo một file Word trống, chèn một nút lệnh ActiveX, và cấu hình chính xác kích thước của nó — tất cả chỉ với vài dòng Java. Điều này bao quát phần cốt lõi của **how to insert activex**, **how to set button**, **java create blank word**, và **insert command button word** trong một ví dụ tự chứa.

Bước tiếp theo? Hãy thử tùy chỉnh nhãn của nút, thêm macro để phản hồi khi nhấn, hoặc nhúng nhiều điều khiển trên cùng một trang. Bạn cũng có thể khám phá việc chuyển đổi .docx sang PDF bằng Aspose.Words, giữ lại nút dưới dạng hình ảnh tĩnh.

Hãy thoải mái thử nghiệm, và nếu gặp khó khăn, hãy để lại bình luận bên dưới. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây liên quan chặt chẽ và mở rộng các kỹ thuật đã trình bày trong bài này. Mỗi tài nguyên đều bao gồm mã nguồn đầy đủ và giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API khác và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}