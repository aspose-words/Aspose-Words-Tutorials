---
category: general
date: 2026-09-11
description: Tìm hiểu cách tạo tài liệu Word bằng C# và thêm nút lệnh một cách lập
  trình sử dụng Aspose.Words trong vài bước đơn giản.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: vi
lastmod: 2026-09-11
og_description: Tạo tài liệu Word bằng C# và lập trình thêm nút lệnh với Aspose.Words.
  Hãy theo dõi hướng dẫn đầy đủ này để có giải pháp hoạt động.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Tạo tài liệu Word C# – thêm nút lệnh một cách lập trình
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Cách tạo tài liệu Word bằng C# và thêm nút lệnh một cách lập trình
url: /vi/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word bằng C# và thêm nút lệnh một cách lập trình

Nếu bạn cần **create word document c#** và nhúng một nút tương tác, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Sử dụng Aspose.Words, bạn có thể thêm một nút **CommandButton** một cách lập trình chỉ với vài dòng mã, loại bỏ nhu cầu thực hiện UI thủ công trong Word.

Trong tutorial này bạn sẽ học cách:

* Khởi tạo một tệp Word trống bằng C#.
* Chèn một điều khiển ActiveX **CommandButton**.
* Đặt các thuộc tính của nút như tên và chú thích.
* Lưu tài liệu để nút hiển thị khi tệp được mở trong Microsoft Word.

Không cần công cụ bên ngoài nào ngoài thư viện Aspose.Words for .NET, và các bước hoạt động với .NET 6+ hoặc .NET Framework 4.6.2 trở lên.

## Prerequisites

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

| Yêu cầu | Lý do |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | Cung cấp môi trường chạy cho dự án C#. |
| Visual Studio 2022 (or any C# IDE) | Giúp viết, biên dịch và chạy mã một cách dễ dàng. |
| Aspose.Words for .NET NuGet package | Cung cấp các lớp `Document`, `DocumentBuilder` và `Forms2OleControl` được sử dụng trong ví dụ. |
| Basic knowledge of C# syntax | Cho phép bạn theo dõi mã mà không cần học thêm. |

Bạn có thể thêm gói Aspose.Words qua console NuGet:

```powershell
Install-Package Aspose.Words
```

## Step 1: Set up a new C# console project

Tạo một ứng dụng console sẽ tạo ra tệp Word. Mở terminal và chạy:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Tệp `Program.cs` được tạo sẽ chứa mã được trình bày trong các bước tiếp theo.

## Step 2: Create a blank document and a DocumentBuilder

Hoạt động đầu tiên là khởi tạo một đối tượng `Document`, đại diện cho một tệp `.docx` trống, và một `DocumentBuilder` cho phép bạn chỉnh sửa nội dung tài liệu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:**  
`Document` là container cho tất cả các yếu tố Word (đoạn văn, bảng, điều khiển). `DocumentBuilder` cung cấp một API fluent để chèn đối tượng tại vị trí con trỏ hiện tại mà không cần xử lý các bộ sưu tập node cấp thấp.

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words hỗ trợ chèn các điều khiển ActiveX legacy thông qua phương thức `InsertForms2OleControl`. Phương thức này yêu cầu loại điều khiển và kích thước mong muốn tính bằng point.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Điều gì xảy ra bên trong:**  
Word xem một điều khiển ActiveX như một đối tượng OLE (Object Linking and Embedding). Lớp `Forms2OleControl` bọc dữ liệu OLE và cung cấp các thuộc tính như `Name` và `Caption`.

## Step 4: Configure the button’s name and caption

Sau khi điều khiển được đặt, bạn có thể tùy chỉnh các thuộc tính runtime của nó. Đặt một `Name` có ý nghĩa giúp bạn nhận diện nút sau này, trong khi `Caption` xác định văn bản hiển thị trên nút.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Mẹo chuyên nghiệp:**  
Nếu bạn dự định xử lý sự kiện click của nút bằng VBA, `Name` sẽ trở thành tên macro bạn tham chiếu, ví dụ `Sub btnSubmit_Click()`.

## Step 5: Save the document to disk

Cuối cùng, ghi tài liệu ra một tệp `.docx`. Chọn thư mục bạn có quyền ghi; ví dụ sử dụng đường dẫn tương đối, sẽ được giải quyết tới thư mục output của dự án.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Chạy chương trình sẽ tạo ra `CommandButton.docx`. Mở tệp trong Microsoft Word sẽ hiển thị một nút **Submit** có thể nhấp được:

![Tài liệu Word có nút lệnh Submit](/images/command-button.png "Ảnh chụp màn hình tài liệu Word chứa nút lệnh Submit được tạo bằng C#")

*Image alt text (og_image_alt):* `Ảnh chụp màn hình tài liệu Word chứa nút lệnh Submit được tạo bằng C#`

## Verifying the result

1. Mở Word và mở `CommandButton.docx`.  
2. Bạn sẽ thấy một nút có nhãn **Submit** trong phần thân tài liệu.  
3. Di chuột lên nút sẽ hiển thị tên `btnSubmit` trong bảng **Properties** (tab Developer → Properties).  

Nếu nút không xuất hiện, hãy đảm bảo tab **Developer** được bật trong Word (File → Options → Customize Ribbon → check *Developer*). Các điều khiển ActiveX sẽ bị ẩn khi tab này bị tắt.

## Handling common variations and edge cases

| Tình huống | Điều chỉnh đề xuất |
|-----------|------------------------|
| **Different button size** | Thay đổi các đối số width và height trong `InsertForms2OleControl`. Ví dụ, `150, 40` tạo một nút lớn hơn. |
| **Multiple buttons** | Gọi `InsertForms2OleControl` nhiều lần, di chuyển con trỏ của builder giữa các lần gọi (`builder.Writeln();`). |
| **Button without ActiveX** | Sử dụng `InsertFormField` để thêm một trường biểu mẫu legacy (ví dụ: checkbox) nếu bạn cần tương thích với các phiên bản Word cũ hơn chặn ActiveX. |
| **Cross‑platform usage** | Các điều khiển ActiveX chỉ hoạt động trên phiên bản Word cho Windows. Đối với Mac hoặc trình xem web, hãy cân nhắc chèn một hyperlink được định dạng như nút thay thế. |
| **Security warnings** | Word có thể hiển thị cảnh báo bảo mật khi mở tài liệu chứa điều khiển ActiveX. Ký tài liệu bằng chứng chỉ tin cậy sẽ giảm thiểu phiền toái này. |

## Full, runnable example

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào `Program.cs`. Nó biên dịch và chạy mà không cần sửa đổi sau khi đã thêm gói NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả mong đợi trong console:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Mở tệp đã tạo sẽ hiển thị nút **Submit** sẵn sàng cho tương tác.

## Conclusion

Bạn giờ đã biết cách **create word document c#** và **programmatically add command button** bằng Aspose.Words. Quy trình chỉ gồm việc khởi tạo một `Document`, chèn một `Forms2OleControl`, cấu hình các thuộc tính, và lưu tệp. Từ đây bạn có thể:

* Thêm nhiều điều khiển hơn (ví dụ: checkbox, trường văn bản) bằng cách thay đổi `ControlType`.
* Gắn macro VBA vào nút để thực hiện logic tùy chỉnh.
* Kết hợp kỹ thuật này với các tính năng khác của Aspose.Words như mail merge hoặc điền mẫu.

Hãy thử nghiệm với các kích thước, chú thích và nhiều nút khác nhau để phù hợp với kịch bản tự động hoá của bạn. Chúc lập trình vui vẻ!

## What Should You Learn Next?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word với Header và Footer bằng Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Tạo tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}