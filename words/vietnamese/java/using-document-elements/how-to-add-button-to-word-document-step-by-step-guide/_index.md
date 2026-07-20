---
category: general
date: 2026-07-20
description: Cách thêm nút vào tài liệu Word bằng Aspose.Words. Học cách chèn nút
  Forms2OleControl với DocumentBuilder trong vài phút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: vi
lastmod: 2026-07-20
og_description: Cách thêm nút vào tài liệu Word với Aspose.Words. Theo dõi hướng dẫn
  thực tế này để nhúng Forms2OleControl CommandButton bằng Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Cách Thêm Nút Vào Tài Liệu Word – Hướng Dẫn Đầy Đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Cách Thêm Nút Vào Tài Liệu Word – Hướng Dẫn Từng Bước
url: /vi/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Thêm Nút Vào Tài Liệu Word – Hướng Dẫn Đầy Đủ Aspose.Words

Bạn đã bao giờ tự hỏi **cách thêm nút vào tài liệu Word** mà không cần mở giao diện người dùng và nhấp chuột không? Bạn không phải là người duy nhất. Nhiều nhà phát triển cần nhúng các điều khiển tương tác một cách lập trình—hãy nghĩ đến nút “Submit” trong một mẫu mà sau này người dùng cuối sẽ điền. Tin tốt? Với Aspose.Words for Java, bạn có thể thực hiện trong vài dòng mã.

Trong tutorial này, chúng ta sẽ đi qua các bước chính xác để chèn một `Forms2OleControl` loại **CommandButton** bằng cách sử dụng `DocumentBuilder`. Khi hoàn thành, bạn sẽ có một file `.docx` sẵn sàng sử dụng, hiển thị một nút có thể nhấn được với nhãn “Click Me”. Không có bí ẩn, chỉ có mã rõ ràng và lý do cho mỗi dòng.

## Những Điều Bạn Sẽ Học

- Cách tạo một tài liệu Word mới từ đầu.
- Cách sử dụng **DocumentBuilder** để đặt một **Forms2OleControl**.
- Tại sao bạn nên đặt caption cho nút và kích thước như chúng tôi làm.
- Cách lưu và xác minh kết quả.
- Các lỗi thường gặp (ví dụ: thiếu thư viện, loại điều khiển không được hỗ trợ) và cách tránh chúng.

**Prerequisites** – Bạn cần Java 8+ (hoặc mới hơn) và thư viện Aspose.Words for Java (phiên bản 23.12 hoặc sau). Một IDE như IntelliJ IDEA hoặc Eclipse sẽ giúp công việc suôn sẻ hơn, nhưng bất kỳ trình soạn thảo văn bản nào cũng được.

---

## Bước 1: Thiết Lập Dự Án và Nhập Các Phụ Thuộc

Trước khi bất kỳ mã nào chạy, Maven (hoặc Gradle) phải biết nơi lấy Aspose.Words. Thêm đoạn mã này vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Nếu bạn thích Gradle, tương đương là:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Mẹo chuyên nghiệp:** Sử dụng phiên bản mới nhất; các phiên bản cũ hơn có thể thiếu API `Forms2OleControl`.

Khi phụ thuộc đã được giải quyết, bạn đã sẵn sàng viết mã Java.

## Bước 2: Tạo Tài Liệu Mới và Lấy DocumentBuilder

Lớp `Document` đại diện cho toàn bộ gói `.docx`, trong khi `DocumentBuilder` là cây cọ bạn dùng để vẽ nội dung lên đó. Hãy nghĩ `DocumentBuilder` như “con trỏ” biết vị trí phần tử tiếp theo sẽ được đặt.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:** Khởi tạo một `Document` mới cho bạn một canvas sạch. Builder tự động trỏ tới đoạn văn đầu tiên, vì vậy bạn không cần quản lý các section hay trang một cách thủ công.

## Bước 3: Chèn Forms2OleControl Loại CommandButton

Bây giờ là phần trọng tâm: `insertForms2OleControl`. Phương thức này tạo một điều khiển OLE (Object Linking and Embedding) mà Word xem như một phần tử form. Chúng ta sẽ truyền ba đối số:

1. `Forms2OleControlType.COMMANDBUTTON` – cho Word biết chúng ta muốn một nút.
2. `100` – chiều rộng tính bằng point (≈1.39 inch).
3. `30` – chiều cao tính bằng point (≈0.42 inch).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Cách hoạt động:** Bên trong, Aspose.Words tạo XML thích hợp trong phần `word/document.xml`, tham chiếu tới đối tượng OLE. Các kích thước bạn cung cấp sẽ được engine bố cục của Word tôn trọng, vì vậy nút sẽ xuất hiện chính xác ở vị trí con trỏ builder đang đứng.

## Bước 4: Đặt Caption (Văn Bản) Cho Nút

Một nút không có nhãn sẽ gây nhầm lẫn—hãy tưởng tượng một nút thang máy im lặng. Phương thức `setCaption` đặt văn bản hiển thị:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Bạn có thể thay đổi caption thành bất kỳ gì: “Submit”, “Approve”, hoặc ngay cả một chuỗi đã được địa phương hoá. Caption được lưu trong thuộc tính của đối tượng OLE, vì vậy Word sẽ hiển thị nó một cách tự nhiên.

## Bước 5: Lưu Tài Liệu và Xác Minh Kết Quả

Cuối cùng, ghi file ra đĩa. Chọn một thư mục mà bạn có quyền ghi; nếu không sẽ gặp `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Mở `button-demo.docx` trong Microsoft Word. Bạn sẽ thấy một nút có nhãn **Click Me** được đặt ở đầu tài liệu. Nhấn vào nó trong Word sẽ kích hoạt hành vi OLE mặc định (thường là một thông báo placeholder, trừ khi bạn gắn macro).

## Các Trường Hợp Cạnh Thường Gặp và Cách Xử Lý

| Situation | Why It Happens | Fix |
|-----------|----------------|-----|
| **Missing `Forms2OleControl` type** | Older Aspose.Words versions didn’t expose this enum. | Upgrade to 23.12+ or later. |
| **Button appears as a picture** | Word’s security settings block OLE controls. | Enable “Trust access to the VBA project object model” in Trust Center, or use a macro‑enabled `.docm`. |
| **Incorrect size** | Points vs. pixels confusion. | Remember 1 point = 1/72 inch. Adjust numbers accordingly. |
| **Saving throws `FileNotFoundException`** | Path does not exist. | Ensure the directory (`output/`) is created before `doc.save`. Use `new File("output").mkdirs();`. |

## Mở Rộng Ví Dụ: Thêm Nhiều Nút Hoặc Các Điều Khiển Khác

Nếu bạn cần hơn một nút, chỉ cần di chuyển con trỏ builder bằng `builder.moveTo` hoặc `builder.writeln()` trước khi gọi lại `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Bạn cũng có thể chèn **CheckBox**, **ComboBox**, hoặc **ListBox** bằng cách thay `Forms2OleControlType.COMMANDBUTTON` bằng giá trị enum phù hợp (`CHECKBOX`, `COMBOBOX`, v.v.). Các tham số chiều rộng/chiều cao vẫn áp dụng.

## Cách Thức Này Phù Hợp Với Các Quy Trình Tự Động Hóa Word Lớn Hơn

- **Template Generation:** Xây dựng mẫu hợp đồng có chứa nút “Approve” cho việc phê duyệt downstream.
- **Reporting:** Tạo báo cáo hàng ngày với nút “Refresh Data” kích hoạt macro.
- **Form Distribution:** Gửi bảng câu hỏi với các điều khiển tương tác đã được điền sẵn.

Tất cả các kịch bản này đều hưởng lợi từ cách tiếp cận **Word automation** mà chúng tôi đã trình bày. Bằng cách nhúng các điều khiển một cách lập trình, bạn loại bỏ việc chỉnh sửa thủ công và giảm lỗi con người.

## Mã Nguồn Đầy Đủ (Sẵn Sàng Sao Chép)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** Khi bạn mở `output/button-demo.docx` trong Microsoft Word, bạn sẽ thấy hai nút—“Click Me” và “Submit”—được xếp chồng nhau theo chiều dọc ở đầu file.

## Kết Luận

Chúng tôi đã trả lời **cách thêm nút vào tài liệu Word** bằng Aspose.Words for Java, từng bước một. Bắt đầu từ một `Document` trống, chúng tôi đã tận dụng **DocumentBuilder** để chèn một `Forms2OleControl` loại **CommandButton**, đặt caption thân thiện và lưu kết quả. Cách tiếp cận này có thể mở rộng cho nhiều điều khiển và tích hợp mượt mà vào các pipeline **Word automation** rộng hơn.

Sẵn sàng cho thử thách tiếp theo? Hãy thử thay nút bằng một **CheckBox**, hoặc gắn macro để phản hồi khi người dùng nhấn nút trong file `.docm`. Mẫu tương tự vẫn áp dụng—chỉ cần đổi enum và điều chỉnh caption.

Nếu gặp bất kỳ khó khăn nào, hãy kiểm tra lại phiên bản thư viện và quyền truy cập thư mục đầu ra. Đừng ngại để lại bình luận bên dưới với câu hỏi hoặc chia sẻ trường hợp sử dụng của bạn. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}