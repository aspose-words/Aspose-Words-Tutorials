---
category: general
date: 2026-10-26
description: Học cách chèn điều khiển nội dung văn bản thuần bằng Aspose.Words trong
  C#. Hướng dẫn từng bước bao gồm StructuredDocumentTag, tiêu đề và ID thẻ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: vi
lastmod: 2026-10-26
og_description: Chèn điều khiển nội dung văn bản thuần bằng Aspose.Words trong C#.
  Thực hiện theo hướng dẫn này để thêm tiêu đề, ID thẻ và tùy chỉnh giao diện.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Chèn điều khiển nội dung văn bản thuần trong Word bằng C# – hướng dẫn đầy
  đủ
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách chèn điều khiển nội dung văn bản thuần trong tài liệu Word bằng C#
url: /vi/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn kiểm soát nội dung văn bản thuần trong tài liệu Word bằng C#

Nếu bạn cần **chèn kiểm soát nội dung văn bản thuần** vào một tệp Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác bằng cách sử dụng Aspose.Words for .NET. Dù bạn đang xây dựng dịch vụ tạo tài liệu tự động hay tự động hoá việc tạo biểu mẫu, các bước dưới đây cho phép bạn thêm một vùng có thể tái sử dụng, có thể chỉnh sửa mà người dùng cuối có thể điền.

Bạn sẽ học cách tạo một `Document`, sử dụng `DocumentBuilder` để đặt một Structured Document Tag (SDT) dạng văn bản thuần, đặt tiêu đề thân thiện và gán một định danh thẻ duy nhất. Hướng dẫn cũng giải thích các biến thể phổ biến—như thay đổi giao diện hoặc lồng các kiểm soát—để bạn có thể điều chỉnh giải pháp cho bất kỳ dự án nào.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
- Giấy phép Aspose.Words for .NET hợp lệ (hoặc khóa đánh giá miễn phí)
- Visual Studio 2022 hoặc bất kỳ IDE nào hỗ trợ C#
- Kiến thức cơ bản về cú pháp C#

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng bản đánh giá miễn phí, hãy nhớ rằng tài liệu đầu ra sẽ chứa một watermark. Phiên bản có giấy phép sẽ tự động loại bỏ nó.

## Cách chèn kiểm soát nội dung văn bản thuần bằng Aspose.Words

Cốt lõi của giải pháp là một quy trình ba bước:

1. **Tạo một `Document` và một `DocumentBuilder`.**  
2. **Chèn một Structured Document Tag (SDT) dạng văn bản thuần với giao diện mặc định.**  
3. **Gán tiêu đề và định danh thẻ cho SDT.**  

Mỗi bước được giải thích dưới đây, kèm theo mã hoàn chỉnh, có thể chạy được.

### Bước 1: Khởi tạo tài liệu và builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cung cấp các phương thức như `InsertParagraph`, `InsertImage`, và quan trọng nhất cho hướng dẫn này, `InsertStructuredDocumentTag`. Khởi tạo chúng trước sẽ cho bạn một “canvas” để đặt **kiểm soát nội dung văn bản thuần**.

### Bước 2: Chèn kiểm soát nội dung văn bản thuần (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` báo cho Aspose.Words tạo một **kiểm soát nội dung văn bản thuần**, hoạt động giống như một hộp văn bản đơn giản mà người dùng có thể chỉnh sửa. `SdtAppearance.Default` hiển thị kiểm soát với nền nhẹ, làm cho vùng này rõ ràng trong tài liệu là có thể chỉnh sửa.

> **Tại sao lại dùng `SdtAppearance.Default`?**  
> Giao diện mặc định là kiểu tương thích nhất trên mọi phiên bản Word. Nếu bạn cần giao diện không viền, có thể chuyển sang `SdtAppearance.Hidden` sau này.

### Bước 3: Đặt tiêu đề và định danh thẻ

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) xuất hiện trong bảng *Content Controls* của Word, giúp người dùng cuối hiểu mục đích của trường.  
- **Tag** (`sdt.Tag`) là định danh dành cho nhà phát triển, bạn có thể truy vấn sau này bằng `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** cung cấp văn bản hướng dẫn màu xám, cải thiện trải nghiệm người dùng.

Mã hoàn chỉnh ở trên tạo thành một chương trình tự chứa mà bạn có thể biên dịch và chạy. Sau khi thực thi, `output.docx` sẽ chứa một kiểm soát nội dung văn bản thuần duy nhất với tiêu đề *MyTag* và thẻ *TagId*.

![Sơ đồ minh họa cách chèn kiểm soát nội dung văn bản thuần trong tài liệu Word](image.png){alt="chèn kiểm soát nội dung văn bản thuần"}

## Hiểu về StructuredDocumentTag (SDT) và các thuộc tính của nó

Một **Structured Document Tag** (SDT) là mô hình đối tượng nền tảng cho các kiểm soát nội dung Word. Các thuộc tính quan trọng nhất để chèn một kiểm soát văn bản thuần là:

| Thuộc tính | Mục đích | Giá trị thường gặp |
|------------|----------|--------------------|
| `SdtType` | Xác định loại điều khiển (plain text, rich text, picture, v.v.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Kiểu hiển thị của điều khiển | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Tên dễ đọc được hiển thị trong bảng *Content Controls* | Bất kỳ chuỗi ngắn nào |
| `Tag` | Định danh có thể đọc được bởi máy, được sử dụng trong mã | Chuỗi alphanumeric |
| `PlaceholderName` | Văn bản hiển thị khi điều khiển trống | Văn bản gợi ý tùy chỉnh |

Khi bạn đặt `SdtType.PlainText`, Word sẽ giới hạn nội dung chỉ ở các ký tự thuần, ngăn việc định dạng phong phú. Điều này làm cho kiểm soát trở nên lý tưởng cho các trường biểu mẫu đơn giản như *Tên*, *Email* hoặc *Số điện thoại*.

### Các biến thể bạn có thể cần

| Kịch bản | Thay đổi mã |
|----------|-------------|
| **Không có màu nền** (không viền) | Dùng `SdtAppearance.Hidden` thay vì `Default`. |
| **Trường chỉ đọc** | Sau khi chèn, đặt `sdt.LockContentControl = true`. |
| **Tiền điền dữ liệu** | Đặt `sdt.Text = "John Doe";` sau khi tạo thẻ. |
| **Nhiều kiểm soát trong bảng** | Chèn SDT vào ô bảng bằng `builder.InsertCell();` trước lệnh `InsertStructuredDocumentTag`. |

## Những lỗi thường gặp và cách tránh

1. **Quên đặt tiêu đề** – Word vẫn sẽ tạo kiểm soát, nhưng người dùng sẽ không thấy mô tả có ý nghĩa trong bảng *Content Controls*. Luôn luôn gán `sdt.Title`.  
2. **Sử dụng sai `SdtType`** – Nếu bạn cần văn bản thuần nhưng vô tình chọn `RichText`, kiểm soát sẽ cho phép định dạng, có thể gây lỗi trong quá trình xử lý sau. Kiểm tra lại giá trị enum.  
3. **Lưu vào thư mục chỉ đọc** – Lệnh `doc.Save` sẽ ném ra `UnauthorizedAccessException`. Đảm bảo thư mục đích có quyền ghi hoặc dùng `Path.GetTempPath()` để thử nghiệm.  
4. **Chưa áp dụng giấy phép** – Nếu không có giấy phép hợp lệ, tài liệu đầu ra sẽ chứa watermark đánh giá. Áp dụng giấy phép sớm trong chương trình của bạn:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Ví dụ đầy đủ, có thể chạy

Dưới đây là toàn bộ chương trình, sẵn sàng để sao chép‑dán vào một dự án console mới.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi:** Mở `output.docx` trong Microsoft Word sẽ hiển thị một dòng văn bản *“Please fill in the following field:”* tiếp theo là một vùng hộp màu xám nhạt có nhãn *MyTag*. Placeholder *Enter your text here* xuất hiện màu xám nhạt cho đến khi người dùng nhập dữ liệu.

## Kết luận

Bạn giờ đã biết cách **chèn kiểm soát nội dung văn bản thuần** vào một tài liệu Word bằng Aspose.Words for .NET. Hướng dẫn đã bao gồm việc khởi tạo `Document`, chèn `StructuredDocumentTag` loại `PlainText`, và tùy chỉnh tiêu đề, thẻ và placeholder. Bằng cách hiểu các tùy chọn `SdtAppearance` và các lỗi thường gặp, bạn có thể tự tin xây dựng các biểu mẫu, mẫu tài liệu và báo cáo tự động dựa trên các kiểm soát có thể chỉnh sửa.

### Tiếp theo là gì?

- Khám phá các loại SDT khác như `RichText` hoặc `ComboBox` cho danh sách thả xuống.  
- Kết hợp nhiều kiểm soát nội dung trong bảng hoặc lặp lại chúng bằng `RepeatingSection`.  
- Sử dụng `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` để đọc hoặc sửa giá trị của kiểm soát một cách lập trình.

Hãy thoải mái thử nghiệm các biến thể đã nêu ở trên, và tích hợp mẫu này vào quy trình tạo tài liệu tự động lớn hơn của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo kiểm soát nội dung trong C# với Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Tạo tài liệu Word mới và chèn kiểm soát nội dung trong C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Thêm nội dung bằng Document Builder trong Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}