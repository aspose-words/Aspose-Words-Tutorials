---
category: general
date: 2026-08-23
description: Tìm hiểu cách chèn nút lệnh vào tài liệu Word bằng Java và Aspose.Words.
  Hướng dẫn này chỉ cách thêm điều khiển biểu mẫu, đặt tên nút và nhúng nút ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: vi
lastmod: 2026-08-23
og_description: Chèn nút lệnh vào tài liệu Word bằng Java. Thực hiện theo hướng dẫn
  này để thêm điều khiển biểu mẫu, đặt tên nút và nhúng nút ActiveX với Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Chèn nút lệnh trong Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Cách chèn nút lệnh vào tài liệu Word bằng Java
url: /vi/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn nút lệnh vào tài liệu Word bằng Java

Nếu bạn cần **chèn nút lệnh** vào một tệp Word, hướng dẫn này sẽ cho bạn giải pháp hoàn chỉnh với Aspose.Words for Java. Bạn sẽ thấy cách thêm điều khiển biểu mẫu, cấu hình chú thích của nó và đặt tên nút mà không rời khỏi IDE của mình.

Hướng dẫn bao gồm mọi thứ bạn cần để tạo một tệp `.docx` chứa nút ActiveX sẵn sàng sử dụng trong Microsoft Word. Không cần công cụ bổ sung nào, và ví dụ chạy trên Java 8+.

## Những gì bạn sẽ học

* Cách thêm điều khiển biểu mẫu loại **CommandButton** vào tài liệu Word.  
* Các bước chính xác để **đặt tên nút** và **thêm thuộc tính nút activex**.  
* Cách lưu tài liệu để nút hiển thị đúng khi mở trong Word.  

Bạn nên có môi trường phát triển Java cơ bản và một dự án Maven hoặc Gradle có thể nhập thư viện Aspose.Words.

## Yêu cầu trước

| Requirement | Reason |
|-------------|--------|
| Java 8 hoặc mới hơn | Aspose.Words for Java chạy trên Java 8+. |
| Công cụ xây dựng Maven hoặc Gradle | Đơn giản hoá việc thêm phụ thuộc Aspose.Words. |
| Giấy phép Aspose.Words for Java (hoặc dùng thử miễn phí) | Cần thiết cho bộ tính năng đầy đủ; API hoạt động ở chế độ đánh giá. |
| IDE như IntelliJ IDEA hoặc Eclipse | Giúp việc chỉnh sửa và chạy ví dụ dễ dàng hơn. |

## Bước 1: Thêm Aspose.Words vào dự án của bạn

Nếu bạn dùng Maven, thêm phụ thuộc sau vào `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Đối với Gradle, đặt dòng này vào `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Sau khi phụ thuộc được giải quyết, bạn có thể nhập các lớp thư viện vào tệp nguồn Java của mình.

## Bước 2: Chèn nút lệnh – mã cốt lõi

Tạo một lớp Java mới có tên `InsertCommandButtonDemo`. Đoạn mã dưới thực hiện cả bốn hành động cần thiết để **chèn nút lệnh**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Tại sao mỗi dòng lại quan trọng

* **Document & DocumentBuilder** – Chúng cung cấp đại diện trong bộ nhớ của tệp Word và API để sửa đổi nội dung của nó.  
* **insertForms2OleControl** – Phương thức này **thêm điều khiển biểu mẫu** loại `COMMAND_BUTTON`. Đối tượng `Forms2OleControl` trả về đại diện cho điều khiển ActiveX.  
* **setName** – Gán một định danh lập trình (`btnSubmit`). Macro Word hoặc VBA có thể tham chiếu tới tên này sau này.  
* **setCaption** – Xác định văn bản người dùng nhìn thấy trên nút, trả lời câu hỏi “cách thêm nút”.  
* **save** – Ghi tệp `.docx` ra đĩa, giữ lại nút ActiveX được nhúng.  

Chạy chương trình sẽ tạo `CommandButtonDemo.docx` trong thư mục làm việc. Mở tệp trong Microsoft Word sẽ hiển thị một nút có nhãn **Submit** mà bạn có thể nhấn (nó sẽ hiển thị một hộp thoại ActiveX mặc định ở chế độ đánh giá).

## Bước 3: Xác minh nút đã chèn trong Word

1. Mở `CommandButtonDemo.docx` bằng Microsoft Word (2016 hoặc mới hơn).  
2. Nút **Submit** xuất hiện ở vị trí con trỏ đã được đặt trong quá trình chèn.  
3. Nhấp chuột phải vào nút và chọn **Properties** để thấy trường **Name** chứa `btnSubmit`.  

Nếu nút không hiển thị, hãy đảm bảo **ActiveX controls** được bật trong cài đặt Trust Center của Word.

## Bước 4: Tùy chỉnh nút (tùy chọn)

Bạn có thể tùy chỉnh thêm nút bằng cách điều chỉnh kích thước, vị trí hoặc thêm macro VBA. Lớp `Forms2OleControl` cung cấp các thuộc tính bổ sung như `setWidth`, `setHeight`, và `setLeft`. Dưới đây là một ví dụ làm nút lớn hơn:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Các dòng này có thể được đặt sau lời gọi `setCaption`. Chúng minh họa việc tùy chỉnh **add activex button** vượt ra ngoài việc chèn cơ bản.

## Những lỗi thường gặp và cách tránh

| Symptom | Cause | Fix |
|---------|-------|-----|
| Nút không hiển thị trong Word | Tài liệu được lưu trước khi điều khiển được thêm | Đảm bảo `insertForms2OleControl` được gọi trước `doc.save`. |
| Chú thích nút trống | `setCaption` không được gọi hoặc được gọi với chuỗi rỗng | Cung cấp một chuỗi không rỗng, ví dụ, `"Submit"`. |
| VBA không thể tìm thấy nút | Tên không khớp giữa mã VBA và giá trị `setName` | Giữ tên nhất quán; sử dụng `setName("btnSubmit")` và tham chiếu `btnSubmit` trong VBA. |
| Cảnh báo bảo mật khi mở tệp | Bảo mật macro của Word chặn các điều khiển ActiveX | Điều chỉnh Trust Center > Macro Settings, hoặc ký tài liệu bằng chứng chỉ tin cậy. |

## Ví dụ đầy đủ, có thể chạy

Dưới đây là tệp nguồn hoàn chỉnh, sẵn sàng sao chép‑dán vào IDE của bạn. Nó bao gồm các câu lệnh import, xử lý ngoại lệ, và một khối chú thích giải thích mỗi bước chính.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Kết quả mong đợi:** Sau khi chạy chương trình, `CommandButtonDemo.docx` chứa một nút **Submit** duy nhất. Mở tệp trong Word sẽ hiển thị nút chính xác tại vị trí con trỏ `DocumentBuilder` đã đặt.

## Các bước tiếp theo

* **Thêm nhiều điều khiển biểu mẫu** – Sử dụng `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, hoặc `TEXT_BOX` để xây dựng các biểu mẫu Word đầy đủ.  
* **Kết hợp với mail merge** – Chèn nút vào tài liệu mail‑merged để tạo các biểu mẫu tương tác cá nhân hoá.  
* **Gắn macro VBA** – Nhúng VBA một cách lập trình để phản hồi sự kiện `Click` của nút cho tự động hoá nâng cao.  

Những chủ đề này mở rộng tự nhiên kỹ thuật **add form control** mà bạn vừa nắm vững.

---

### Tóm tắt

Bây giờ bạn đã biết cách **chèn nút lệnh** vào tài liệu Word bằng Java, cách **thêm điều khiển biểu mẫu**, cách **đặt tên nút**, và cách tùy chỉnh **add activex button**. Ví dụ hoàn chỉnh chạy ngay mà không cần cấu hình thêm, và bạn có thể điều chỉnh nó cho bất kỳ quy trình tạo tài liệu nào. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ với hướng dẫn từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Chèn trường biểu mẫu Combo Box trong tài liệu Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Chèn trường biểu mẫu Check Box trong tài liệu Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}