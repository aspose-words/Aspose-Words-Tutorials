---
category: general
date: 2026-10-13
description: Tìm hiểu cách thêm nút lệnh một cách lập trình bằng Aspose.Words. Hướng
  dẫn này cũng chỉ cách tạo nút trong tài liệu Word với mã C# đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: vi
lastmod: 2026-10-13
og_description: Thêm một nút lệnh vào tài liệu Word một cách lập trình bằng Aspose.Words.
  Tham khảo hướng dẫn đầy đủ này để tạo nút trong tài liệu Word bằng C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Thêm nút lệnh vào tài liệu Word bằng cách lập trình – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách thêm nút lệnh bằng cách lập trình trong tài liệu Word
url: /vi/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm nút lệnh một cách lập trình trong tài liệu Word  

Nếu bạn cần **thêm một nút lệnh một cách lập trình**, Aspose.Words cung cấp một API sạch sẽ cho phép bạn nhúng các điều khiển biểu mẫu OLE trực tiếp vào tệp .docx. Hướng dẫn này sẽ dẫn bạn qua từng bước cần thiết để **tạo một nút trong tài liệu Word** hoạt động như một nút biểu mẫu thông thường khi tài liệu được mở trong Microsoft Word.  

Bạn sẽ học cách thiết lập môi trường phát triển, chèn nút, cấu hình các thuộc tính của nó và xác minh kết quả. Không cần công cụ bên ngoài—chỉ cần một dự án .NET và thư viện Aspose.Words for .NET.  

## Prerequisites  

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:  

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt.  
* Phiên bản mới nhất của Aspose.Words for .NET (các ví dụ sử dụng 23.12, nhưng bất kỳ bản phát hành 22.x+ nào cũng hoạt động).  
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code.  

Mã chạy trên Windows, macOS và Linux vì Aspose.Words không phụ thuộc vào nền tảng.  

## Step 1: Set up the project and reference Aspose.Words  

1. Tạo một dự án console mới:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Thêm gói NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Mở **Program.cs** và thay thế nội dung của nó bằng khung mẫu được hiển thị trong các bước tiếp theo.  

Việc thiết lập dự án theo cách này đảm bảo trình biên dịch có thể tìm thấy các namespace `Aspose.Words` và `Aspose.Words.Drawing.Forms` cần thiết cho các điều khiển biểu mẫu.  

## Step 2: Initialize a blank document and a DocumentBuilder  

Lớp `Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cung cấp một API trôi chảy để thêm nội dung.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Why this step matters* – Without a `DocumentBuilder` you cannot position the button precisely on the page. The builder also respects the current cursor location, making it easy to insert multiple controls later.  

## Step 3: Insert the command button OLE control  

Aspose.Words treats a command button as an OLE control of type `ControlType.CommandButton`. You define its location and size with a `RectangleF` measured in points (1 point = 1/72 inch).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Các điểm chính**  

* Gốc của hình chữ nhật (X, Y) tính tương đối so với góc trên‑trái của trang.  
* Thay đổi `Width` hoặc `Height` sẽ thay đổi kích thước hiển thị của nút.  
* `InsertForms2OleControl` trả về một đối tượng `Forms2OleControl` mà bạn có thể cấu hình thêm.  

## Step 4: Configure the button’s name and caption  

**Tên** được sử dụng bởi engine macro của Word để xác định điều khiển, trong khi **caption** là văn bản người dùng nhìn thấy.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Nếu bạn dự định thêm macro VBA sau này, hãy sử dụng một tên mô tả vì trình ghi macro của Word sẽ tham chiếu tới thuộc tính này.  

## Step 5: (Optional) Save the document and verify the result  

Lưu tệp cho phép bạn mở nó trong Microsoft Word để xác nhận rằng nút xuất hiện và hoạt động.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Khi bạn mở *CommandButtonDemo.docx* trong Word, bạn sẽ thấy một nút có nhãn **Submit** được đặt khoảng 1.4 inch từ lề trái và 2.1 inch từ phía trên của trang. Nhấn nút sẽ không thực hiện gì mặc định vì không có macro được gắn, nhưng điều khiển hiển thị hoàn toàn hoạt động.  

## Step 6: Edge cases and common pitfalls  

| Tình huống | Cần chú ý gì | Cách khắc phục đề xuất |
|-----------|-------------------|-----------------|
| **Nút chồng lên văn bản hiện có** | Hình chữ nhật có thể giao nhau với một đoạn văn, gây ra vấn đề bố cục. | Chèn nút sau khi gọi `builder.Writeln()` để di chuyển con trỏ tới dòng mới, hoặc điều chỉnh tọa độ `Y`. |
| **Tài liệu mở kèm cảnh báo** | Một số phiên bản Word đánh dấu các điều khiển OLE không có chương trình liên kết. | Đảm bảo loại điều khiển là `CommandButton`; Word coi nó là một phần tử biểu mẫu tiêu chuẩn và không yêu cầu chương trình bên ngoài. |
| **Chạy trên Linux trong môi trường không giao diện** | Word không thể khởi chạy để kiểm tra giao diện, nhưng tệp vẫn hợp lệ. | Sử dụng kiểm thử đơn vị đọc các thuộc tính của điều khiển (`commandButton.Name`, `commandButton.Caption`) để xác minh chúng đã được đặt đúng. |
| **Cần nhiều nút** | Sử dụng lại cùng một `DocumentBuilder` mà không di chuyển con trỏ sẽ đặt nút lên trên nút trước. | Gọi `builder.MoveToDocumentEnd()` hoặc điều chỉnh giá trị `Y` của hình chữ nhật trước mỗi lần chèn. |

Việc giải quyết những trường hợp này từ sớm sẽ tiết kiệm thời gian khi mở rộng giải pháp thành các biểu mẫu đầy đủ với hàng chục điều khiển.  

## Step 7: Full, runnable example  

Dưới đây là một chương trình tự chứa mà bạn có thể sao chép, dán và chạy mà không cần sửa đổi (ngoại trừ việc khôi phục NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Kết quả mong đợi**  

Chạy chương trình sẽ in ra một đường dẫn tương tự như:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Mở *CommandButtonDemo.docx* được tạo ra sẽ hiển thị một nút **Submit** duy nhất được đặt tại các tọa độ được định nghĩa trong mã. Không có thành phần UI nào khác xuất hiện, xác nhận rằng quy trình **add command button programmatically** đã thành công.  

## Conclusion  

Bạn giờ đã biết cách **add a command button programmatically** vào tài liệu Word bằng Aspose.Words, và cũng hiểu cách **create a Word document button** mà sau này có thể gắn với macro VBA hoặc công cụ tự động hóa bên ngoài. Quy trình bao gồm khởi tạo tài liệu, chèn điều khiển OLE `CommandButton`, cấu hình các thuộc tính và lưu tệp.  

Từ đây bạn có thể:  

* Thêm nhiều điều khiển hơn (ô kiểm, trường văn bản) bằng cách lặp lại bước 3 với các giá trị `ControlType` khác nhau.  
* Gắn macro VBA vào nút để thực hiện các hành động như lưu biểu mẫu hoặc gửi email.  
* Tạo toàn bộ biểu mẫu một cách động bằng cách lặp qua một bộ sưu tập các định nghĩa trường dựa trên dữ liệu.  

Thử nghiệm với các tọa độ hình chữ nhật và caption của nút để phù hợp với thiết kế UI của bạn. Chúc lập trình vui!  


## What Should You Learn Next?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thêm trường Combo Box vào tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Thêm trường Check Box vào tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Tạo tài liệu Word trống với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}