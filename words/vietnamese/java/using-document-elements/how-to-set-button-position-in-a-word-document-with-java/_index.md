---
category: general
date: 2026-09-24
description: Đặt vị trí nút trong tài liệu Word bằng Java và Aspose.Words. Tìm hiểu
  cách chèn nút, thêm điều khiển ActiveX và tạo tài liệu Word theo phong cách Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: vi
lastmod: 2026-09-24
og_description: Đặt vị trí nút trong tài liệu Word bằng Java. Hướng dẫn này cho thấy
  cách chèn nút, thêm điều khiển ActiveX và tạo tài liệu Word bằng Java với Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Đặt vị trí nút trong tài liệu Word bằng Java – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Cách đặt vị trí nút trong tài liệu Word bằng Java
url: /vi/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách đặt vị trí nút trong tài liệu Word bằng Java

Nếu bạn cần **set button position** trong một tệp Word, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, có thể chạy được. Dù bạn đang xây dựng một mẫu yêu cầu tương tác người dùng hay tự động hoá một biểu mẫu, bạn sẽ học chính xác **how to insert button** bằng cách sử dụng Aspose.Words for Java và kiểm soát vị trí của nó.

Bài hướng dẫn bao gồm mọi thứ bạn cần để **add ActiveX control** vào tài liệu Word, giải thích cách **add button to Word**, và trình bày quy trình đầy đủ để **create Word document Java**. Không cần tham chiếu bên ngoài—chỉ cần sao chép, chạy và xác minh kết quả.

## Yêu cầu trước

* Java 17 (hoặc bất kỳ môi trường chạy Java 8+ nào) đã được cài đặt.
* Maven hoặc Gradle để quản lý các phụ thuộc.
* Giấy phép Aspose.Words for Java (bản dùng thử miễn phí hoạt động cho mục đích đánh giá).
* Kiến thức cơ bản về cú pháp Java.

> **Pro tip:** Giữ các tệp JAR của Aspose.Words trong thư mục `libs/` và thêm chúng vào classpath của dự án để tránh xung đột phiên bản.

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven đơn giản (hoặc sử dụng Gradle) và thêm phụ thuộc Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Chạy `mvn clean compile` để tải thư viện và chuẩn bị đường dẫn biên dịch.

## Bước 2: Tạo tài liệu Word mới

Hoạt động đầu tiên là **create Word document java**. Bạn khởi tạo một đối tượng `Document` và một `DocumentBuilder` cho phép bạn chỉnh sửa tệp.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Lớp `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp một API lưu loát để chèn nội dung.

## Bước 3: Cách chèn nút – add ActiveX control

Aspose.Words cung cấp lớp `Forms2OleControl` để chèn các điều khiển ActiveX cổ điển như CommandButton. Bước này cho thấy cách chính xác để **how to insert button** vào tài liệu.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Phương thức `insertForms2OleControl` trả về một thể hiện `Forms2OleControl` mà bạn có thể cấu hình. Đây là phần cốt lõi của quy trình **add ActiveX control**.

## Bước 4: Đặt vị trí nút

Bây giờ chúng ta thực sự **set button position**. Các phương thức `setLeft` và `setTop` của điều khiển chấp nhận giá trị tính bằng điểm (1 pt = 1/72 in). Để căn chỉnh nút với tọa độ màn hình thông thường, bạn có thể chuyển đổi pixel sang điểm (1 px ≈ 0.75 pt). Trong ví dụ, chúng tôi đặt nút cách mép trái 100 px và cách mép trên 150 px.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Vì logic **set button position** được đóng gói ở đây, bạn có thể tái sử dụng các dòng này bất cứ khi nào cần di chuyển một điều khiển. Điều chỉnh các số để phù hợp với yêu cầu bố cục của bạn.

## Bước 5: Xác định kích thước và chú thích

Một nút không có nhãn sẽ gây nhầm lẫn. Sử dụng `setWidth`, `setHeight`, và `setCaption` để tạo cho nó một giao diện hiển thị.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Kích thước cũng được biểu thị bằng điểm, vì vậy chúng tôi chuyển đổi từ pixel để đồng nhất.

## Bước 6: Lưu tài liệu – hoàn thiện quy trình **create Word document java**

Cuối cùng, lưu tệp vào đĩa. Đường dẫn có thể là tuyệt đối hoặc tương đối so với thư mục gốc của dự án.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Chạy chương trình sẽ tạo ra `CommandButtonDemo.docx` trong thư mục `output`. Mở tệp trong Microsoft Word sẽ hiển thị một nút có thể nhấp được, được đặt chính xác ở vị trí bạn đã thiết lập.

### Kết quả mong đợi

* Một tệp `.docx` có tên **CommandButtonDemo.docx**.
* Trong tài liệu, một **CommandButton** có nhãn “Click Me” xuất hiện cách lề trái 100 px và cách lề trên 150 px.
* Nút phản hồi khi nhấp khi tài liệu được mở trong Word (nó sẽ hiển thị thông báo ActiveX mặc định trừ khi bạn đính kèm mã VBA tùy chỉnh).

## Bước 7: Các biến thể phổ biến và trường hợp đặc biệt

### Thêm nhiều nút

Nếu bạn cần **add button to Word** nhiều lần, lặp lại các bước 3‑5 với một thể hiện `Forms2OleControl` mới mỗi lần. Hãy nhớ điều chỉnh giá trị `setTop` để các nút không chồng lên nhau.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Sử dụng mà không có giấy phép

Aspose.Words sẽ thêm watermark khi được sử dụng mà không có giấy phép. Đối với mã sản xuất, mua giấy phép và áp dụng nó ở đầu hàm `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Tương thích với các phiên bản Office cũ hơn

Các điều khiển ActiveX được hỗ trợ trong định dạng `.doc` (Word 97‑2003). Để tạo tệp legacy, thay đổi định dạng lưu:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Mã nguồn đầy đủ (có thể chạy)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Lưu tệp dưới tên `src/main/java/CommandButtonDemo.java`, chạy `mvn exec:java -Dexec.mainClass=CommandButtonDemo`, và mở tài liệu đã tạo để xem kết quả.

## Câu hỏi thường gặp

**Q: Điều này có hoạt động với OpenJDK không?**  
A: Có. Aspose.Words là Java thuần và chạy trên bất kỳ triển khai JDK 8+ nào, bao gồm OpenJDK.

**Q: Tôi có thể thay đổi phông chữ hoặc màu sắc của nút không?**  
A: Giao diện nút ActiveX được điều khiển bởi ứng dụng chủ (Word). Bạn có thể đính kèm mã VBA để thay đổi thuộc tính tại thời gian chạy, nhưng giao diện tĩnh bị giới hạn ở kiểu mặc định.

**Q: Nếu tôi cần đặt nút bên trong một ô bảng thì sao?**  
A: Di chuyển con trỏ `DocumentBuilder` vào ô trước khi gọi `insertForms2OleControl`. Điều khiển sẽ kế thừa bố cục của ô, và bạn vẫn có thể sử dụng `setLeft`/`setTop` để tinh chỉnh.

## Kết luận

Bây giờ bạn đã biết cách **set button position** trong tài liệu Word bằng Java, cách **how to insert button**, cách **add ActiveX control**, và cách **add button to Word** đồng thời tuân thủ các thực hành tốt nhất cho các dự án **create Word document java**. Ví dụ hoàn chỉnh minh họa toàn bộ quy trình—từ thiết lập dự án đến tệp `.docx` đã lưu chứa một CommandButton hoạt động.

### Các bước tiếp theo

* Khám phá các giá trị `Forms2OleControl.ControlType` khác (ví dụ: `CHECKBOX`, `TEXTBOX`) để xây dựng các biểu mẫu phong phú hơn.
* Kết hợp nút với macro VBA để xử lý sự kiện nhấp tùy chỉnh.
* Sử dụng tính năng mail‑merge của Aspose.Words để tạo tài liệu cá nhân hoá đã chứa sẵn các điều khiển tương tác.

Chúc lập trình vui vẻ, và tận hưởng việc tự động hoá tài liệu Word bằng Java!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao phủ các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh có thể chạy kèm theo giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}