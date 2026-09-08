---
category: general
date: 2026-09-08
description: Cách lưu file docx khi chèn một điều khiển ActiveX trong C#. Hãy làm
  theo hướng dẫn từng bước này để thêm một nút lệnh một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: vi
lastmod: 2026-09-08
og_description: Cách lưu file docx khi chèn điều khiển ActiveX trong C#. Hướng dẫn
  này sẽ chỉ cho bạn cách tạo tài liệu Word bằng lập trình, thêm nút lệnh và lưu trữ
  file.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Cách lưu file docx và nhúng nút ActiveX trong C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Cách lưu file docx và chèn nút ActiveX bằng C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách lưu docx và chèn nút ActiveX bằng C#

Nếu bạn cần tạo tài liệu Word một cách lập trình và sau đó lưu docx với một nút tương tác, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ học cách chèn một điều khiển ActiveX, thêm nút ActiveX, và lưu tệp .docx kết quả bằng C# và thư viện Aspose.Words.

Bài học bao gồm mọi bước cần thiết để **tạo tài liệu Word một cách lập trình**, nhúng **nút lệnh**, và lưu tệp trên đĩa. Không yêu cầu kinh nghiệm trước với các đối tượng COM, nhưng bạn nên có kiến thức cơ bản về C# và đã cài Visual Studio.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc mới hơn  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  
* Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
* Hiểu biết về cấu trúc dự án C#  

Những mục này đảm bảo mã của bạn biên dịch và chạy mà không cần cấu hình bổ sung.

## Bước 1: Thiết lập dự án console C# mới

Tạo một ứng dụng console sẽ chứa logic tự động hoá Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Lệnh trên tạo một thư mục có tên **WordActiveXDemo**, thêm tham chiếu tới Aspose.Words, và chuẩn bị dự án để biên dịch.

## Bước 2: Tạo tài liệu Word một cách lập trình

Mở tệp `Program.cs` đã tạo và thêm các chỉ thị `using` cần thiết.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Bây giờ khởi tạo một đối tượng `Document` trống. Đối tượng này đại diện cho toàn bộ tệp Word trong bộ nhớ.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

Lớp `Document` là điểm vào cho mọi thao tác xử lý Word. Ở giai đoạn này tài liệu chưa có trang nào, nhưng Aspose.Words sẽ tự động tạo một phần mặc định khi bạn thêm nội dung.

## Bước 3: Chèn điều khiển ActiveX – thêm nút activex

Một đối tượng **Forms2OleControl** cho phép bạn nhúng một điều khiển ActiveX vào một đoạn văn trong Word. Đoạn mã sau chèn một **CommandButton** với độ rộng 150 pt và chiều cao 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` tạo điều khiển và trả về một thể hiện `Forms2OleControl` đã được định kiểu mạnh, bạn có thể cấu hình thêm. Phương thức này tự động thêm một đoạn mới để chứa điều khiển, vì vậy bạn không cần quản lý các đối tượng đoạn thủ công.

## Bước 4: Cấu hình nút lệnh – cách thêm thuộc tính cho nút lệnh

Đặt các thuộc tính **Name** và **Caption** cho nút để nó có thể nhận dạng được khi chạy và thân thiện với người dùng trong giao diện.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

Thuộc tính `Name` hữu ích khi bạn sau này xử lý sự kiện click của nút qua VBA hoặc macro Word. `Caption` là văn bản người dùng cuối sẽ thấy trên bề mặt nút.

### Mẹo chuyên nghiệp
Nếu bạn dự định tự động xử lý sự kiện click từ C#, hãy nhúng một macro VBA tham chiếu tới `cmdSubmit`. Word sẽ yêu cầu người dùng bật macro khi tài liệu mở, đây là hành vi bảo mật tiêu chuẩn cho các điều khiển ActiveX.

## Bước 5: Cách lưu docx

Sau khi điều khiển đã được đặt, lưu tài liệu thành tệp .docx. Phương thức `Save` tự động chọn định dạng phù hợp dựa trên phần mở rộng tệp.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lưu tệp hoàn thành quy trình **cách lưu docx**. Tệp kết quả có thể mở trong Microsoft Word, nơi nút ActiveX sẽ xuất hiện trên trang đầu. Khi bạn nhấn nút, Word sẽ hiển thị một thông báo placeholder trừ khi đã gắn macro.

## Bước 6: Chạy chương trình và kiểm tra kết quả

Biên dịch và thực thi ứng dụng console:

```bash
dotnet run
```

Sau khi chương trình kết thúc, mở `C:\Temp\CommandButton.docx` trong Microsoft Word:

* Tài liệu chứa một trang duy nhất với nút **Submit** gần đầu trang.  
* Khi di chuột qua nút, tooltip hiển thị tên `cmdSubmit`.  
* Không có nội dung nào bị mất, và kích thước tệp tương đương với một .docx trống tiêu chuẩn.

Nếu nút không xuất hiện, hãy xác nhận rằng:

1. Cài đặt **Trust Center** của Word cho phép điều khiển ActiveX.  
2. Tệp đã được lưu với phần mở rộng `.docx` (không phải `.doc`).  

## Các trường hợp đặc biệt và biến thể thường gặp

| Tình huống | Điều chỉnh đề xuất |
|-----------|--------------------|
| Bạn cần kích thước nút khác | Thay đổi các đối số width và height trong `InsertForms2OleControl`. |
| Bạn muốn nút ở một trang cụ thể | Sử dụng `builder.MoveToDocumentEnd();` sau khi thêm trang, hoặc chèn ngắt trang trước điều khiển. |
| Bạn phải hỗ trợ môi trường không có Aspose.Words | Dùng Open XML SDK để chèn phần tử `w:object`, nhưng mã sẽ phức tạp hơn đáng kể. |
| Cần tài liệu hỗ trợ macro | Lưu với phần mở rộng `.docm` (`document.Save("MyDoc.docm");`) và nhúng module VBA xử lý `cmdSubmit_Click`. |

## Mã nguồn hoàn chỉnh

Dưới đây là chương trình đầy đủ, tự chứa, bạn có thể sao chép vào `Program.cs` và chạy mà không cần chỉnh sửa (ngoại trừ đường dẫn đầu ra).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Đầu ra dự kiến trong console

```
Document saved to C:\Temp\CommandButton.docx
```

Mở tệp trong Word sẽ hiển thị một nút có nhãn **Submit**. Nhấn nút sẽ kích hoạt hành vi mặc định của ActiveX (hộp thoại thông báo cho biết không có macro được gắn).

## Kết luận

Bài hướng dẫn này đã minh họa **cách lưu docx** đồng thời nhúng một **điều khiển ActiveX**, cụ thể là **thêm nút activex** hoạt động như một nút lệnh. Bạn đã biết cách **tạo tài liệu Word một cách lập trình**, cấu hình các thuộc tính của nút, và lưu tệp để người dùng cuối tương tác.

Từ đây bạn có thể khám phá:

* Thêm macro VBA để xử lý `cmdSubmit_Click`.  
* Chèn các điều khiển ActiveX khác như hộp kiểm hoặc combo box.  
* Tạo tài liệu đa trang với nhiều yếu tố tương tác.  

Thử nghiệm với các loại điều khiển và tùy chọn bố cục khác nhau để xây dựng các mẫu Word phong phú, tương tác, giúp tối ưu hoá quy trình kinh doanh của bạn.

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong bài này. Mỗi tài nguyên đều có mã mẫu đầy đủ và giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}