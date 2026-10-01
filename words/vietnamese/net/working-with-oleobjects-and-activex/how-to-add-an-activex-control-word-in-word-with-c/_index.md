---
category: general
date: 2026-09-30
description: Thêm một điều khiển ActiveX vào tài liệu Word bằng C#. Tìm hiểu cách
  chèn nút ActiveX, thêm nút lệnh và làm cho nó có thể nhấn được.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: vi
lastmod: 2026-09-30
og_description: Thêm một điều khiển ActiveX vào tài liệu Word bằng C#. Hãy theo hướng
  dẫn chi tiết này để chèn một nút ActiveX, thêm một nút lệnh và làm cho nó có thể
  nhấn được.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Thêm một điều khiển ActiveX vào tài liệu Word – hướng dẫn C# từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Cách thêm một điều khiển ActiveX vào Word bằng C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm một ActiveX control word vào Word bằng C#

Nếu bạn cần nhúng một **ActiveX control word** vào tệp Microsoft Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chi tiết. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, chèn một nút có thể nhấp, lưu tài liệu và hoạt động với Aspose.Words for .NET mới nhất.

Thêm một ActiveX control word cho phép bạn tạo các biểu mẫu tương tác, hộp thoại tùy chỉnh hoặc các phần tử UI đơn giản hoạt động giống như các điều khiển gốc của Word. Dù bạn đang xây dựng mẫu hợp đồng cần người dùng tương tác hay báo cáo cần nút “Run”, các bước dưới đây bao phủ mọi thứ bạn cần.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn bạn có:

* .NET 6.0 SDK hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.8)
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#)
* Aspose.Words for .NET đã được cài đặt (`dotnet add package Aspose.Words`)
* Kiến thức cơ bản về C# và cấu trúc tài liệu Word

> **Mẹo chuyên nghiệp:** Phương thức `InsertForms2OleControl` chỉ hoạt động với các điều khiển “Forms 2.0” legacy, là các điều khiển ActiveX mà Word sử dụng cho các trường biểu mẫu. Nếu bạn nhắm tới các phiên bản Office mới hơn, điều khiển vẫn sẽ hiển thị đúng trong client desktop.

## Bước 1: Thiết lập dự án và nhập các namespace

Tạo một dự án console mới và thêm các câu lệnh `using` cần thiết. Điều này giúp trình biên dịch tìm thấy các lớp `Document`, `DocumentBuilder` và `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Namespace `Aspose.Words` cung cấp các API cấp cao để xử lý Word, trong khi `Aspose.Words.Drawing` chứa enumeration `OleControlType` cần dùng để chỉ định loại ActiveX control.

## Bước 2: Tải tài liệu Word nguồn

Bạn phải bắt đầu với một tệp Word mà bạn muốn chỉnh sửa. Đoạn mã dưới đây tải `input.docx` từ thư mục bạn chỉ định.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Nếu tệp không tồn tại, Aspose.Words sẽ ném ra `FileNotFoundException`. Hãy bao bọc lời gọi trong khối `try/catch` nếu bạn cần xử lý lỗi một cách nhẹ nhàng.

## Bước 3: Tạo DocumentBuilder để chỉnh sửa tài liệu

`DocumentBuilder` là công cụ chính để chèn văn bản, hình ảnh và các điều khiển. Nó duy trì một con trỏ chỉ tới vị trí mà phần tử tiếp theo sẽ được đặt.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Mặc định, con trỏ của builder được đặt ở đầu phần đầu tiên. Bạn có thể di chuyển nó bằng các phương thức như `MoveToDocumentEnd()` hoặc `MoveToParagraph(index)` nếu muốn nút xuất hiện ở vị trí khác.

## Bước 4: Chèn một điều khiển ActiveX CommandButton

Bây giờ là phần cốt lõi của hướng dẫn: chèn một **ActiveX control word** dưới dạng nút có thể nhấp. Phương thức `InsertForms2OleControl` nhận hai đối số — loại điều khiển và chú thích (hoặc tên) cho điều khiển.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Tại sao dùng `OleControlType.CommandButton`?**  
  Nó yêu cầu Word tạo một nút command Forms 2.0 cổ điển, hiển thị chú thích và có thể được gắn macro hoặc script VBA sau này.

* **Chú thích làm gì?**  
  Chuỗi `"ClickMe"` sẽ trở thành văn bản hiển thị trên nút. Bạn có thể thay đổi nó thành bất kỳ nội dung nào phù hợp với giao diện người dùng của mình.

### Chèn nút vào vị trí cụ thể

Nếu bạn muốn nút xuất hiện sau một đoạn văn bản nhất định, hãy di chuyển builder trước:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Bước 5: Lưu tài liệu đã chỉnh sửa

Sau khi chèn điều khiển, lưu các thay đổi vào một tệp mới (hoặc ghi đè tệp gốc).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Khi mở `output.docx` trong phiên bản desktop của Word, bạn sẽ thấy nút có nhãn **ClickMe** (hoặc **Submit**, tùy vào chú thích bạn đã dùng). Nhấp vào nút trong chế độ thiết kế sẽ không thực hiện gì cả; bạn có thể gán macro sau này qua tab **Developer** của Word.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là một chương trình tự chứa minh họa toàn bộ quy trình. Sao chép nó vào `Program.cs` của một ứng dụng console mới và chạy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

* Console sẽ in thông báo thành công cùng với đường dẫn đầu ra.
* Mở `output.docx` sẽ hiển thị một nút **ClickMe** ở vị trí mà builder đã chèn.
* Nút có thể được chọn, thay đổi kích thước hoặc gán macro qua **Developer → Design Mode** của Word.

## Các câu hỏi thường gặp và xử lý trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| **Cách chèn nút ActiveX vào header/footer?** | Di chuyển builder tới header/footer bằng `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` trước khi gọi `InsertForms2OleControl`. |
| **Nếu tôi cần checkbox thay vì nút?** | Dùng `OleControlType.CheckBox` và cung cấp chú thích như `"Agree"`. |
| **Nút có hoạt động trong Word Online không?** | Không. Word Online không hỗ trợ các điều khiển Forms 2.0 legacy. Nút chỉ hiển thị trong client desktop. |
| **Có thể đặt kích thước của nút bằng mã không?** | Sau khi chèn, lấy đối tượng `Shape` qua `builder.CurrentParagraph.Runs[0].GetShape()` và điều chỉnh `Width`/`Height`. |
| **Có cách gán macro từ code không?** | Aspose.Words không cung cấp API chỉnh sửa macro. Bạn phải mở tài liệu trong Word và gắn macro thủ công hoặc dùng Office Interop API. |

## Mẹo cho môi trường production

* **Tránh đường dẫn cứng** – sử dụng `Path.Combine` và file cấu hình.
* **Giải phóng `Document`** – bọc trong khối `using` nếu làm việc với tệp lớn để giải phóng bộ nhớ kịp thời.
* **Xác thực đầu ra** – kiểm tra chương trình rằng tài liệu chứa một shape loại `OleControl` bằng cách duyệt `doc.GetChildNodes(NodeType.Shape, true)`.
* **Lưu ý bảo mật** – Điều khiển ActiveX có thể chạy mã trên máy khách. Chỉ phân phối tài liệu cho người dùng tin cậy và cân nhắc sử dụng chữ ký số.

## Kết luận

Bây giờ bạn đã biết cách thêm một **ActiveX control word** vào tài liệu Word bằng C#. Bằng việc tải tài liệu, tạo `DocumentBuilder`, chèn nút command bằng `InsertForms2OleControl` và lưu tệp, bạn có thể tự động tạo các biểu mẫu Word tương tác. Hãy thử các giá trị `OleControlType` khác, đặt điều khiển trong header hoặc bảng, và kết hợp chúng với macro để có trải nghiệm người dùng phong phú hơn.

---

*Bước tiếp theo*: khám phá **cách chèn các loại ActiveX** khác, học **cách thêm trình xử lý sự kiện cho command button** bằng VBA, và đọc về **các thực hành tốt nhất khi chèn nút ActiveX** để đảm bảo tương thích đa nền tảng.

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ cùng với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}