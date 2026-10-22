---
category: general
date: 2026-08-10
description: Tạo tài liệu Word bằng lập trình với Aspose.Words, sau đó thêm nút Word
  điều khiển ActiveX. Chèn nút lệnh ActiveX trong vài phút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: vi
lastmod: 2026-08-10
og_description: Tạo tài liệu Word bằng lập trình sử dụng Aspose.Words, sau đó thêm
  nút Word điều khiển ActiveX. Tìm hiểu cách chèn nhanh nút lệnh ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Tạo tài liệu Word bằng lập trình – thêm nút ActiveX trong C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Tạo tài liệu Word bằng lập trình và thêm nút ActiveX
url: /vi/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình và thêm nút ActiveX

Nếu bạn cần **tạo tài liệu Word bằng chương trình**, hướng dẫn này sẽ dẫn bạn qua toàn bộ quy trình với Aspose.Words for .NET. Bạn cũng sẽ học cách **thêm các phần tử điều khiển ActiveX** và **chèn đối tượng nút lệnh ActiveX** trong một ví dụ duy nhất, tự chứa.

Việc tạo file Word từ mã loại bỏ bước mở Microsoft Word thủ công, cho phép bạn tự động xây dựng báo cáo, hoá đơn hoặc hợp đồng dựa trên dữ liệu. Khi kết thúc tutorial này, bạn sẽ có một ứng dụng console C# sẵn sàng chạy, tạo ra file `.docx` chứa một **ActiveX CommandButton** tương tác.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
* Visual Studio 2022 hoặc bất kỳ IDE nào hỗ trợ phát triển .NET
* Giấy phép Aspose.Words for .NET hợp lệ (bạn có thể dùng khóa dùng thử miễn phí để thử nghiệm)
* Kiến thức cơ bản về cú pháp C# và khái niệm về điều khiển COM/ActiveX

> **Mẹo chuyên nghiệp:** Nếu bạn dự định phân phối tài liệu đã tạo cho người dùng không có Word được cài đặt, hãy nhúng các file runtime của điều khiển ActiveX cùng với `.docx` hoặc cung cấp một mẫu hỗ trợ macro.

## Tạo tài liệu Word bằng chương trình – cài đặt ban đầu

Đầu tiên, thêm gói NuGet Aspose.Words vào dự án của bạn:

```bash
dotnet add package Aspose.Words
```

Sau đó tạo một dự án console mới (nếu bạn chưa có):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Mở file `Program.cs` đã được tạo – chúng ta sẽ thay thế nội dung của nó bằng giải pháp đầy đủ dưới đây.

## Bước 1: Nhập không gian tên và cấu hình giấy phép

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Lý do quan trọng*: Nhập `Aspose.Words.Drawing` cho phép bạn truy cập `Forms2OleControl`, lớp đại diện cho một điều khiển ActiveX trong tài liệu Word. Đặt giấy phép sớm sẽ ngăn các cảnh báo thời gian chạy trong môi trường production.

## Bước 2: Tạo tài liệu trống và một DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Đối tượng `Document` là biểu diễn trong bộ nhớ của một file `.docx`. `DocumentBuilder` hoạt động như một con trỏ bạn di chuyển trong tài liệu để chèn các phần tử.

## Bước 3: Chèn một điều khiển ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` tạo một đối tượng OLE mà Word xem như một điều khiển ActiveX. Hệ thống tọa độ sử dụng đơn vị point (1 point = 1/72 inch), phù hợp với engine bố cục của Word.

## Bước 4: Đặt chú thích cho nút và các thuộc tính tùy chọn

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Đặt thuộc tính `Caption` là cách phổ biến nhất để gắn nhãn cho nút. Nếu bạn muốn nút thực thi một macro VBA, gán tên macro cho `OnAction`. Tutorial này tập trung vào phần hiển thị; việc tích hợp macro được đề cập trong phần “Các bước tiếp theo”.

## Bước 5: Lưu tài liệu

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Khi chạy chương trình, bạn sẽ thấy một thông báo console xác nhận rằng `ActiveX_CommandButton.docx` đã được ghi vào đĩa.

### Mã nguồn đầy đủ (sẵn sàng sao chép)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Chạy đoạn mã sẽ tạo ra một file Word chứa một **nút lệnh ActiveX** có thể nhấn được. Mở file trong Microsoft Word, chuyển sang **Design Mode** (tab Developer → Design Mode), và bạn sẽ thấy nút được hiển thị đúng vị trí bạn đặt.

## Bước 6: Kiểm tra kết quả

1. Mở `ActiveX_CommandButton.docx` trong Microsoft Word.  
2. Bật tab **Developer** nếu nó không hiển thị (`File → Options → Customize Ribbon → check Developer`).  
3. Nhấn **Design Mode**. Nút sẽ xuất hiện với nhãn “Submit”.  
4. Nếu bạn đã thêm macro `OnAction`, nhấn nút khi Design Mode tắt để kích hoạt macro.

Nếu nút không hiển thị, hãy chắc chắn rằng cài đặt bảo mật của Word cho phép điều khiển ActiveX (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Câu hỏi thường gặp và các trường hợp đặc biệt

| Câu hỏi | Câu trả lời |
|----------|-------------|
| **Tôi có thể chèn các loại ActiveX khác không?** | Có. Enum `Forms2OleControlType` bao gồm `CheckBox`, `OptionButton`, `ComboBox`, v.v. Thay `CommandButton` bằng giá trị enum mong muốn |

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}