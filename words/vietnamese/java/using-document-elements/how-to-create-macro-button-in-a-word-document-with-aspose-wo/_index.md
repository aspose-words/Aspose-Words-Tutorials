---
category: general
date: 2026-11-22
description: Tạo nút macro trong tài liệu Word bằng Java. Học cách chèn nút lệnh,
  đặt văn bản cho nút và liên kết macro với nút để tạo tài liệu tương tác.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: vi
lastmod: 2026-11-22
og_description: Tạo nút macro trong tài liệu Word bằng Java. Hướng dẫn này chỉ cách
  chèn nút lệnh, đặt văn bản cho nút và liên kết macro với nút để có tính tương tác
  đầy đủ.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Tạo nút macro trong tài liệu Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Cách tạo nút macro trong tài liệu Word bằng Aspose.Words cho Java
url: /vi/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo nút macro trong tài liệu Word bằng Aspose.Words cho Java

Nếu bạn cần **tạo nút macro** trong một tệp Word, hướng dẫn này sẽ đưa bạn qua các bước chính xác cần thiết. Bạn sẽ học cách **chèn nút lệnh**, **đặt văn bản nút**, và **liên kết macro với nút** để tài liệu trở nên hoàn toàn tương tác.

Các nhà phát triển thường nhúng các điều khiển OLE để kích hoạt macro VBA từ bên trong tài liệu. Bài hướng dẫn này bao gồm toàn bộ quy trình làm việc, từ thiết lập dự án đến ví dụ Java có thể chạy được, thêm một **nút tương tác** vào tệp .docx. Không cần script bên ngoài—mọi thứ chạy trong quá trình Java.

## Yêu cầu trước

* JDK 17 hoặc mới hơn đã được cài đặt.
* Maven 3.8+ (hoặc Gradle) để quản lý phụ thuộc.
* Aspose.Words for Java 23.9 hoặc mới hơn – thư viện cung cấp `DocumentBuilder` và API điều khiển OLE.
* Kiến thức cơ bản về Java và macro VBA.

Nếu bất kỳ mục nào trong số này còn thiếu, hãy cài đặt chúng trước; phần còn lại của hướng dẫn giả định chúng đã sẵn sàng.

## Cách tạo nút macro với Aspose.Words cho Java

Cốt lõi của giải pháp bao gồm bốn hành động:

1. **Chèn nút lệnh** điều khiển OLE vào tài liệu.
2. **Đặt văn bản nút** (caption) mà người dùng thấy.
3. **Liên kết macro với nút** để khi nhấp sẽ chạy quy trình VBA mong muốn.
4. **Lưu tài liệu** với macro được nhúng.

Mỗi hành động được giải thích trong phần riêng của nó bên dưới.

### Bước 1: Chèn nút lệnh vào tài liệu

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

`DocumentBuilder.insertForms2OleControl` tạo một điều khiển OLE của loại được chỉ định. Hằng số `Forms2OleControlType.COMMAND_BUTTON` cho Aspose.Words biết tạo một nút lệnh có thể chứa macro.

**Tại sao điều này quan trọng:** Điều khiển OLE hoạt động như một container cho macro. Nếu không chèn nó, sẽ không có phần tử trực quan nào để người dùng nhấp.

### Bước 2: Đặt văn bản nút (caption)

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

Caption là nhãn hiển thị trên nút. Sử dụng `setCaption` để xác định những gì người dùng nhìn thấy.

**Tại sao điều này quan trọng:** Văn bản nút rõ ràng cải thiện khả năng sử dụng. Phương thức `setCaption` cập nhật thuộc tính `Caption` của điều khiển OLE, mà Word hiển thị như nhãn nút.

### Bước 3: Liên kết macro với nút

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

Macro được xác định bằng tên của nó, ví dụ `MyMacro`. Phương thức `setOnClick` lưu tên này vào trình xử lý sự kiện `OnClick` của nút.

**Tại sao điều này quan trọng:** Liên kết macro tạo ra hành vi tương tác. Khi người dùng nhấp vào nút trong Word, quy trình VBA liên quan sẽ được thực thi.

### Bước 4: Thêm nút tương tác vào tài liệu Word

Sau khi cấu hình điều khiển OLE, bạn có thể muốn định vị nó, thay đổi kích thước hoặc thêm văn bản xung quanh. `DocumentBuilder` vẫn tiếp tục thao tác trên tài liệu, vì vậy bạn có thể chèn các đoạn văn trước hoặc sau nút.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Tại sao điều này quan trọng:** Lưu dưới dạng `.docm` giữ lại mã macro. Nếu lưu dưới dạng `.docx`, tham chiếu macro sẽ bị mất.

## Ví dụ đầy đủ có thể chạy

Dưới đây là chương trình Java hoàn chỉnh, bao gồm các import, xử lý ngoại lệ và chú thích giải thích từng bước. Sao chép mã vào một dự án Maven có phụ thuộc Aspose.Words và chạy nó.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Kết quả mong đợi

Chạy chương trình sẽ tạo ra `MacroButtonDemo.docm`. Mở tệp trong Microsoft Word sẽ hiển thị:

* Một đoạn văn có nội dung *“Press the button to execute the macro:”*.
* Một nút có nhãn **Run Report** ngay dưới đoạn văn.
* Khi bạn nhấp vào nút, Word sẽ cố gắng chạy macro `MyMacro`. (Bạn phải thêm mã VBA thực tế vào tài liệu một cách thủ công hoặc qua một bước tự động khác.)

Nếu macro không tồn tại, Word sẽ hiển thị cảnh báo bảo mật, đây là hành vi tiêu chuẩn cho các tài liệu hỗ trợ macro.

## Các biến thể phổ biến và trường hợp đặc biệt

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Caption nút khác** | Thay đổi chuỗi truyền vào `setCaption`. |
| **Nhiều nút** | Gọi `insertForms2OleControl` nhiều lần, mỗi lần với `setCaption` và `setOnClick` riêng. |
| **Tên macro tùy chỉnh** | Thay thế `"MyMacro"` bằng bất kỳ tên thủ tục VBA hợp lệ nào, ví dụ `"ExportToExcel"`. |
| **Ràng buộc kích thước nút** | Điều chỉnh giá trị `setWidth` và `setHeight`; Word sẽ tuân theo các điểm bạn cung cấp. |
| **Nhúng macro bằng chương trình** | Sử dụng `Document.getBuiltInDocumentProperties().add("Macros", …)` hoặc một bước tiêm VBA riêng; Aspose.Words không tự viết mã VBA. |

**Mẹo chuyên nghiệp:** Luôn kiểm tra `.docm` được tạo trên máy có cài đặt bảo mật macro là *Enable all macros* cho việc phát triển. Trong môi trường sản xuất, ký macro bằng chứng chỉ tin cậy để tránh các thông báo bảo mật.

## Danh sách kiểm tra khắc phục sự cố

* **Nút không hiển thị** – Kiểm tra tài liệu đã được lưu dưới dạng `.docm` và mở trong phiên bản Word hỗ trợ điều khiển OLE.
* **Macro không chạy** – Đảm bảo tên macro khớp chính xác, bao gồm cả chữ hoa/thường, và macro tồn tại trong dự án VBA của tài liệu.
* **Caption nút bị cắt ngắn** – Tăng chiều rộng nút bằng `setWidth` để chứa văn bản dài hơn.
* **Sự dịch chuyển bố cục không mong muốn** – Sử dụng `builder.moveTo` để định vị con trỏ chính xác trước khi chèn điều khiển.

## Kết luận

Bây giờ bạn đã biết cách **tạo nút macro** trong tài liệu Word bằng Java, **chèn nút lệnh**, **đặt văn bản nút**, và **liên kết macro với nút** để có tính tương tác đầy đủ. Ví dụ hoàn chỉnh minh họa mọi lời gọi API cần thiết, giải thích lý do mỗi bước quan trọng, và cung cấp hướng dẫn cho các biến thể phổ biến.

Tiếp theo, bạn có thể khám phá:

* **Thêm nút tương tác** vào các mẫu hiện có thay vì tài liệu mới.
* **Tiêm mã VBA bằng chương trình** sử dụng Open XML SDK hoặc công cụ tự động hoá phụ.
* **Kết hợp nhiều điều khiển OLE** (checkbox, list box) để xây dựng các biểu mẫu phong phú.

Thử nghiệm với các caption, tên macro và kích thước nút khác nhau để phù hợp với trường hợp sử dụng của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách chèn nút lệnh vào tài liệu Word bằng Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Cách đặt vị trí nút trong tài liệu Word bằng Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Cách chèn nút ActiveX trong Word – Đặt Caption cho nút](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}