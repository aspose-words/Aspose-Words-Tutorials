---
category: general
date: 2026-09-21
description: Học cách tạo mẫu tài liệu, điền dữ liệu vào mẫu Word và thay thế các
  placeholder trong tệp DOCX bằng C# – hướng dẫn từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: vi
lastmod: 2026-09-21
og_description: Tạo mẫu tài liệu trong C# bằng cách điền dữ liệu vào mẫu Word, thay
  thế các placeholder và lưu file DOCX đã hoàn thiện. Hãy làm theo hướng dẫn đầy đủ
  này.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Tạo mẫu tài liệu trong C# – điền dữ liệu vào các tệp DOCX
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Cách tạo mẫu tài liệu và điền dữ liệu vào bằng C#
url: /vi/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo mẫu tài liệu và điền dữ liệu trong C#

Nếu bạn cần **generate document template** các tệp có thể tái sử dụng cho hoá đơn, hợp đồng hoặc báo cáo, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ học cách **populate word template** các placeholder, thay thế chúng bằng giá trị thực và cuối cùng **fill docx template** các tệp một cách lập trình.

Việc tạo một mẫu có thể tái sử dụng loại bỏ việc sao chép‑dán thủ công và đảm bảo tính nhất quán cho tất cả các tài liệu được tạo. Các bước dưới đây hoạt động với bất kỳ tệp `.docx` nào chứa các token placeholder đơn giản như `{{Name}}`.

## Yêu cầu trước

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE nào bạn thích)  
* Gói NuGet **Aspose.Words for .NET** – nó cung cấp lớp `Document` được sử dụng trong ví dụ  

Bạn có thể thêm gói bằng lệnh sau:

```bash
dotnet add package Aspose.Words
```

## Bước 1: Chuẩn bị mẫu Word

Tạo một tài liệu Word (`Template.docx`) chứa các placeholder nơi dữ liệu động sẽ xuất hiện. Quy ước phổ biến là sử dụng dấu ngoặc nhọn kép:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Lưu tệp vào một thư mục mà bạn có thể tham chiếu từ mã, ví dụ `C:\Docs\Template.docx`.

## Bước 2: Tải tài liệu mẫu

Hành động lập trình đầu tiên là tải mẫu vào bộ nhớ. Hàm khởi tạo `Document` đọc tệp và xây dựng một mô hình đối tượng mà bạn có thể thao tác.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Tại sao điều này quan trọng:** Việc tải tệp tạo ra một bản sao sạch mỗi lần, vì vậy mẫu gốc vẫn không bị thay đổi cho các lần chạy sau.

## Bước 3: Thay thế placeholder bằng dữ liệu thực

Aspose.Words cung cấp một phương thức đơn giản `Range.Replace` để quét tài liệu tìm chuỗi cụ thể và thay thế nó. Đóng gói lời gọi này trong một phương thức trợ giúp để giữ luồng chính gọn gàng.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Cách hoạt động:** `Range.Replace` duyệt qua mọi đoạn văn, ô bảng, header và footer, đảm bảo tất cả các lần xuất hiện của token được cập nhật. Đây là cách đáng tin cậy nhất để **how to replace placeholder** văn bản trong tệp DOCX.

### Xử lý nhiều lần xuất hiện và token thiếu

* Nếu một placeholder xuất hiện nhiều hơn một lần, `Replace` sẽ tự động cập nhật tất cả các trường hợp.  
* Nếu một placeholder không tồn tại, phương thức chỉ không làm gì—không ném ngoại lệ.  
* Đối với tài liệu lớn, bạn có thể cải thiện hiệu suất bằng cách tắt `doc.UpdateFields()` cho đến khi tất cả các thay thế hoàn tất.

## Bước 4: Lưu tài liệu đã điền

Sau khi tất cả placeholder đã được thay thế, ghi kết quả vào một tệp mới. Giữ đầu ra riêng biệt bảo tồn mẫu gốc cho các lần chạy sau.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả:** `FilledTemplate.docx` hiện chứa nội dung được cá nhân hoá:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Bước 5: Xác minh đầu ra (tùy chọn)

Nếu bạn muốn xác nhận một cách lập trình rằng các thay thế đã thành công, bạn có thể đọc lại tệp đã lưu và tìm kiếm các giá trị mong đợi:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Chạy bước xác minh sẽ in ra `true` khi placeholder được thay thế đúng.

## Những lỗi thường gặp và mẹo thực hành tốt

| Vấn đề | Nguyên nhân | Giải pháp đề xuất |
|-------|----------------|-----------------|
| **Placeholder có khoảng trắng thừa** | `"{{ Name }}"` không khớp với `"{{Name}}"`. | Giữ token placeholder không có khoảng trắng, hoặc cắt bỏ khoảng trắng ở cả hai phía trước khi thay thế. |
| **Word thêm định dạng ẩn** | Word có thể lưu placeholder bị chia thành nhiều run, khiến `Replace` bỏ lỡ. | Use `Document.Range.Replace` with `FindReplaceOptions` set to `MatchCase = false` và `FindWholeWordsOnly = false`. |
| **Tài liệu lớn gây chậm** | Thay thế token từng cái một gây quét toàn bộ tài liệu mỗi lần. | Thực hiện thay thế hàng loạt trong một lần duy nhất bằng cách gọi `Range.Replace` cho mỗi token trước khi lưu. |
| **Lưu vào thư mục chỉ đọc** | `doc.Save` ném ra `UnauthorizedAccessException`. | Đảm bảo thư mục đích có quyền ghi, hoặc chọn đường dẫn có thể ghi được bởi người dùng (ví dụ, `%TEMP%`). |

## Ví dụ hoàn chỉnh

Dưới đây là chương trình đầy đủ, tự chứa mà bạn có thể sao chép, dán và chạy.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Kết quả console mong đợi**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Mở `FilledTemplate.docx` trong Microsoft Word để xem văn bản đã được cá nhân hoá.

## Kết luận

Bây giờ bạn đã biết cách **generate document template**, **populate word template**, và **fill docx template** các tệp bằng cách **how to replace placeholder** token bằng dữ liệu thực. Cách tiếp cận này hoạt động với bất kỳ số lượng placeholder nào và mở rộng cho tài liệu lớn khi bạn tuân theo các mẹo thực hành tốt.

### Tiếp theo?

* **Bảng động:** Sử dụng `DocumentBuilder` để chèn các hàng dựa trên các collection.  
* **Phần có điều kiện:** Ẩn hoặc hiển thị các phần của mẫu bằng các trường `IF`.  
* **Xuất PDF:** Gọi `doc.Save("output.pdf")` để tạo phiên bản PDF của tài liệu đã điền.  

Thử nghiệm các biến thể này để xây dựng một engine tạo tài liệu đầy đủ tính năng cho hoá đơn, hợp đồng hoặc bất kỳ báo cáo lặp lại nào.

---


## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tài liệu Word - Tìm và Thay thế Văn bản](/words/english/net/find-and-replace-text/)
- [Tạo Tài liệu Word](/words/english/java/word-processing/generate-word-document/)
- [Khôi phục DOCX bị hỏng – Mở & Tải Tài liệu Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}