---
category: general
date: 2026-09-05
description: Tạo tài liệu Word bằng Aspose.Words, đặt văn bản placeholder, thêm điều
  khiển và lưu tài liệu dưới dạng docx trong C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: vi
lastmod: 2026-09-05
og_description: Tạo tài liệu Word bằng Aspose.Words cho .NET, đặt văn bản placeholder,
  thêm điều khiển và lưu tài liệu dưới dạng docx. Thực hiện theo hướng dẫn đầy đủ
  này.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Tạo tài liệu Word với các điều khiển nội dung trong C# – hướng dẫn từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Cách tạo tài liệu Word với các điều khiển nội dung trong C#
url: /vi/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word với các control nội dung trong C#

Nếu bạn cần **tạo tài liệu word** có chứa các control nội dung có cấu trúc, hướng dẫn này sẽ chỉ cho bạn cách thêm một thẻ plain‑text, **đặt văn bản placeholder**, và **lưu tài liệu dưới dạng docx** bằng Aspose.Words cho .NET. Ví dụ được cung cấp có thể chạy đầy đủ và minh họa cách tiếp cận được khuyến nghị cho việc tạo Word một cách lập trình.

Bạn sẽ học được cách:

* Khởi tạo một tệp Word trống bằng `Document` và `DocumentBuilder`.
* **Cách thêm control** (một `StructuredDocumentTag`) vào phần thân tài liệu.
* **Cách tạo thẻ** với tiêu đề và placeholder giúp người dùng cuối.
* Lưu kết quả bằng `document.Save`, đảm bảo tệp là một `.docx` hợp lệ.

Hướng dẫn giả định bạn đã có môi trường phát triển C# cơ bản và giấy phép cho Aspose.Words (phiên bản dùng thử miễn phí đủ cho mục đích học tập).

---

## Yêu cầu trước

| Yêu cầu | Lý do |
|-------------|--------|
| .NET 6.0 trở lên | Cung cấp môi trường chạy cho Aspose.Words cho .NET. |
| Gói NuGet Aspose.Words cho .NET | Cung cấp các lớp `Document`, `DocumentBuilder` và `StructuredDocumentTag`. |
| IDE như Visual Studio 2022 | Giúp dễ dàng chạy và gỡ lỗi mẫu. |

Cài đặt gói bằng .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## Bước 1: Thiết lập dự án để **tạo tài liệu word**

Tạo một dự án console mới (hoặc thêm mã vào dự án hiện có). Các dòng đầu tiên khởi tạo một tệp Word trống và một `DocumentBuilder` cho phép bạn ghi nội dung.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` đại diện cho cấu trúc tệp, trong khi `DocumentBuilder` theo dõi vị trí chèn. Mô hình này là nền tảng cho bất kỳ kịch bản tạo Word nào.

---

## Bước 2: **Cách thêm control** – tạo một control nội dung plain‑text (thẻ)

Một control nội dung trong Word được gọi là *structured document tag* (SDT). Đoạn mã sau tạo một SDT plain‑text, gán tiêu đề và định nghĩa placeholder sẽ hiển thị khi tài liệu được mở.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Tại sao điều này quan trọng:**  
* Thuộc tính `Title` hoạt động như một định danh ổn định, cho phép bạn tìm hoặc thay thế control một cách lập trình sau này.  
* `PlaceholderName` cung cấp hướng dẫn trực quan cho người dùng tài liệu mà không cần mã UI bổ sung.

![Tạo tài liệu word với placeholder của control nội dung](image.png)

*Văn bản thay thế ảnh: Tạo tài liệu word với một control nội dung hiển thị văn bản placeholder.*

---

## Bước 3: Di chuyển con trỏ vào trong control và ghi văn bản mặc định

Sau khi chèn control, con trỏ của builder vẫn nằm ngoài nó. Di chuyển con trỏ vào thẻ để các lệnh ghi tiếp theo trở thành một phần của nội dung control.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Nếu bạn muốn để control trống, chỉ cần bỏ qua lệnh `Write`. Placeholder sẽ vẫn hiển thị cho đến khi người dùng nhập giá trị.

---

## Bước 4: **Đặt văn bản placeholder** (cách tiếp cận thay thế)

Đôi khi bạn cần thay đổi placeholder sau khi thẻ đã được tạo. Bạn có thể sửa trực tiếp thuộc tính `PlaceholderName`:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Thay đổi placeholder **không** ảnh hưởng đến nội dung hiện có, giúp bạn cập nhật gợi ý UI mà không làm thay đổi dữ liệu do người dùng nhập.

---

## Bước 5: **Lưu tài liệu dưới dạng docx**

Lưu tài liệu đang ở bộ nhớ vào một tệp vật lý. Phương thức `Save` tự động xác định định dạng dựa trên phần mở rộng của tệp.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Nếu bạn cần định dạng khác (ví dụ: PDF hoặc HTML), cung cấp giá trị enum `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Bước 6: Ví dụ đầy đủ, có thể chạy

Kết hợp các phần lại sẽ tạo ra một chương trình ngắn gọn, minh họa **cách tạo thẻ**, đặt placeholder và **lưu tài liệu dưới dạng docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Kết quả mong đợi:**  
Chạy chương trình sẽ tạo ra `SdtExample.docx` chứa một đoạn văn duy nhất với một control nội dung plain‑text có tiêu đề *CustomerName*. Control hiển thị “John Doe” làm nội dung ban đầu; nếu văn bản mặc định bị xóa, placeholder “Enter name” sẽ xuất hiện màu xám nhạt khi tệp được mở trong Microsoft Word.

---

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Điều chỉnh đề xuất |
|----------|------------------------|
| **Nhiều control** | Lặp lại các bước 2‑4 cho mỗi trường, đặt mỗi `Title` là duy nhất. |
| **Control rich‑text** | Sử dụng `SdtType.RichText` thay vì `PlainText`. |
| **Phần lặp lại** | Chọn `SdtType.RepeatingSection` và thêm các control con bên trong phần. |
| **Tài liệu hiện có** | Tải tệp hiện có bằng `new Document("template.docx")` và chèn control tại vị trí mong muốn. |
| **Placeholder Unicode** | Đặt `PlaceholderName` thành bất kỳ chuỗi Unicode nào; Word sẽ hiển thị đúng. |
| **Tài liệu lớn** | Giải phóng `DocumentBuilder` sau khi dùng để giải phóng bộ nhớ (`builder.Dispose();`). |

**Mẹo chuyên nghiệp:** Khi cần lấy giá trị do người dùng nhập sau này, gọi `StructuredDocumentTag.GetText()` sau khi tài liệu đã được lưu và mở lại. Phương thức này trả về văn bản nội bộ mà không bao gồm placeholder.

**Cảnh báo:** Sử dụng placeholder trùng với văn bản mặc định có thể gây nhầm lẫn, vì Word ẩn placeholder khi có bất kỳ văn bản nào hiện diện. Hãy giữ chúng khác nhau.

---

## Kết luận

Bạn đã biết cách **tạo tài liệu word** một cách lập trình, **thêm control**, **tạo thẻ**, **đặt văn bản placeholder**, và **lưu tài liệu dưới dạng docx** bằng Aspose.Words cho .NET. Ví dụ hoàn chỉnh có thể sao chép vào bất kỳ dự án C# nào và mở rộng để hỗ trợ các loại control bổ sung, phần lặp lại, hoặc tích hợp với nguồn dữ liệu.

Các bước tiếp theo bạn có thể khám phá:

* Thêm **control nội dung hình ảnh** (`SdtType.Picture`) để nhúng đồ họa do người dùng cung cấp.  
* Sử dụng **binding** để ánh xạ SDT tới dữ liệu XML cho các kịch bản mail‑merge.  
* Chuyển đổi DOCX đã tạo sang PDF (`SaveFormat.Pdf`) để phân phối.

Hãy thử nghiệm các loại thẻ và thông điệp placeholder khác nhau để phù hợp với quy trình làm việc của ứng dụng của bạn. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}