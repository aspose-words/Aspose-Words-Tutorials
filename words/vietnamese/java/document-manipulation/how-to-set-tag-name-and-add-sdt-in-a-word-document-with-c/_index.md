---
category: general
date: 2026-09-08
description: Đặt tên thẻ và tạo một điều khiển nội dung (SDT) trong tài liệu Word
  bằng C#. Tìm hiểu cách thêm SDT, ghi văn bản vào thẻ và chỉnh sửa tài liệu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: vi
lastmod: 2026-09-08
og_description: Đặt tên thẻ và tạo một điều khiển nội dung (SDT) trong tài liệu Word
  bằng C#. Tham khảo hướng dẫn từng bước này để thêm SDT, ghi văn bản vào thẻ và chỉnh
  sửa tài liệu.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Đặt tên thẻ và thêm SDT trong tài liệu Word – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách đặt tên thẻ và thêm SDT trong tài liệu Word bằng C#
url: /vi/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách đặt tên thẻ và thêm SDT trong tài liệu Word bằng C#

Nếu bạn cần **đặt tên thẻ** cho một StructuredDocumentTag (SDT) khi làm việc với các tệp Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, **tạo một content control**, ghi văn bản vào thẻ, và **sửa đổi tài liệu Word** từ đầu đến cuối.

Các nhà phát triển thường hỏi, *“cách thêm sdt* vào một .docx hiện có và sau đó *ghi văn bản vào thẻ*?” – câu trả lời nằm ở việc sử dụng API Aspose.Words cho .NET. Khi kết thúc tutorial này, bạn sẽ có thể mở một tệp Word, chèn một SDT dạng plain‑text, đặt tên thẻ, điền nội dung vào và lưu các thay đổi mà không để lại tài nguyên rò rỉ.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt.
* Giấy phép hợp lệ của Aspose.Words cho .NET (hoặc bạn có thể dùng phiên bản đánh giá).
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#).
* Một tài liệu Word đầu vào (`input.docx`) được đặt trong thư mục mà bạn có thể tham chiếu từ mã.

## Bước 1: Thiết lập dự án và nhập các namespace

Tạo một dự án Console App mới và thêm gói NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Sau đó, thêm các chỉ thị `using` cần thiết ở đầu file `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Các namespace này cung cấp cho bạn quyền truy cập vào `Document`, `DocumentBuilder` và lớp `StructuredDocumentTag`, những thành phần thiết yếu để **sửa đổi tài liệu Word**.

## Bước 2: Tải tài liệu Word hiện có

Hoạt động đầu tiên là tải tệp mà bạn muốn chỉnh sửa. Bước này là bắt buộc cho mọi kịch bản **sửa đổi nội dung tài liệu Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Tại sao chúng ta phải tải tài liệu trước** – Đối tượng `Document` đại diện cho toàn bộ gói .docx trong bộ nhớ. Chỉ sau khi tải, bạn mới có thể an toàn chèn các node mới như SDT.

## Bước 3: Chèn StructuredDocumentTag (SDT) và đặt tên thẻ

Bây giờ chúng ta trả lời câu hỏi cốt lõi: **cách thêm sdt** và **đặt tên thẻ**. Chúng ta sử dụng `DocumentBuilder.InsertStructuredDocumentTag` với `SdtType.PlainText`. Tham số thứ hai là tên thẻ, bạn có thể tham chiếu sau này bằng mã hoặc qua giao diện Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Giải thích** – `InsertStructuredDocumentTag` trả về một thể hiện `StructuredDocumentTag`. Bằng cách truyền `"MyTag"` chúng ta **đặt tên thẻ** ngay khi tạo. Nếu cần thay đổi sau này, bạn có thể gán giá trị mới cho `sdt.Tag`.

## Bước 4: Ghi văn bản vào thẻ vừa tạo

Sau khi SDT tồn tại, bạn thường muốn **ghi văn bản vào thẻ** để người dùng cuối thấy nội dung placeholder hoặc mặc định. Phương thức `SetText` thực hiện đúng chức năng này.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Tại sao dùng SetText** – Gán trực tiếp vào thuộc tính `Text` sẽ thay thế toàn bộ cấu trúc node. `SetText` an toàn cập nhật văn bản bên trong content control trong khi giữ nguyên cấu trúc của nó.

## Bước 5: Lưu tài liệu đã sửa đổi

Cuối cùng, ghi các thay đổi vào một tệp mới. Điều này hoàn thành quy trình **sửa đổi tài liệu Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Khi bạn mở `output.docx` trong Microsoft Word, sẽ thấy một content control dạng plain‑text có nhãn **MyTag** chứa văn bản “Sample content”. Control này có thể được chỉnh sửa thủ công, và tên thẻ vẫn có thể truy cập qua công cụ phát triển của Word.

## Mã nguồn đầy đủ

Dưới đây là chương trình hoàn chỉnh, tự chứa. Sao chép vào `Program.cs` và chạy; không cần bất kỳ đoạn mã bổ sung nào.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Đầu ra mong đợi trên console

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Hình ảnh tài liệu Word kết quả

![Tài liệu Word hiển thị một content control có tên MyTag và văn bản “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Ví dụ đặt tên thẻ trong tài liệu Word"}

*Ảnh chụp màn hình minh họa SDT với **tên thẻ** được đặt là *MyTag* và văn bản nhúng hiển thị.*

## Các biến thể phổ biến và trường hợp góc cạnh

| Tình huống | Cách xử lý |
|-----------|------------|
| **Tạo một SDT dạng rich‑text** | Sử dụng `SdtType.RichText` thay vì `PlainText`. |
| **Đặt tên thẻ khác sau khi chèn** | `sdt.Tag = "NewTag";` – bạn có thể gán lại tên thẻ bất kỳ lúc nào. |
| **Thêm SDT vào một đoạn văn cụ thể** | Di chuyển con trỏ của builder (`builder.MoveToParagraph(index)`) trước khi gọi `InsertStructuredDocumentTag`. |
| **Nhiều SDT trong cùng một tài liệu** | Lặp lại các bước 3‑4 cho mỗi control; mỗi control có thể có một tên thẻ duy nhất. |
| **Làm việc với tài liệu được bảo vệ** | Đảm bảo tài liệu không được bảo vệ (`doc.Unprotect()`) trước khi chèn SDT. |

## Mẹo chuyên nghiệp cho tự động hoá Word mạnh mẽ

* **Cấp phép sớm** – Gọi `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` ở đầu phương thức `Main` để tránh dấu watermarks đánh giá.
* **Giải phóng đối tượng** – Bao `Document` trong một khối `using` nếu bạn nhắm tới .NET Framework để đảm bảo các handle tệp được giải phóng.
* **Xác thực sự tồn tại của thẻ** – Khi đọc tài liệu sau này, sử dụng `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` để tìm các thẻ theo thuộc tính `Tag`.
* **Hiệu năng** – Đối với tài liệu lớn, chỉ tải các phần cần thiết bằng `LoadOptions` kết hợp `LoadFormat.Docx` và `LoadFormat.Auto`.  

## Kết luận

Bây giờ bạn đã biết cách **đặt tên thẻ**, **tạo một content control**, **ghi văn bản vào thẻ**, và **sửa đổi tài liệu Word** bằng C#. Ví dụ hoàn chỉnh minh họa mẫu chuẩn cho **cách thêm sdt** và lưu các thay đổi một cách an toàn.  

Từ đây


## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thêm nội dung bằng Document Builder trong Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/)
- [Tài liệu Word - Cách xóa nội dung](/words/english/net/remove-content/)
- [Tạo tài liệu Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}