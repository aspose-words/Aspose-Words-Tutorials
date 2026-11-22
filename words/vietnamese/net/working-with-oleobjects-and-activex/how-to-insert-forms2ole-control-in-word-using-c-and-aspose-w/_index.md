---
category: general
date: 2026-11-22
description: Học cách chèn điều khiển Forms2Ole vào Word bằng C#. Hướng dẫn từng bước
  này bao gồm DocumentBuilder, việc đặt nút lệnh và lưu file .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: vi
lastmod: 2026-11-22
og_description: Chèn điều khiển Forms2Ole vào Word bằng C#. Thực hiện theo hướng dẫn
  này để thêm nút lệnh bằng Aspose.Words và DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Chèn điều khiển Forms2Ole vào Word bằng C# – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách chèn điều khiển Forms2Ole vào Word bằng C# và Aspose.Words
url: /vi/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn điều khiển Forms2Ole vào Word bằng C# và Aspose.Words

Nếu bạn cần **chèn điều khiển Forms2Ole vào Word**, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng C#. Dù bạn đang xây dựng mẫu có thể điền dữ liệu hay tự động tạo biểu mẫu, giải pháp dưới đây cho phép bạn thêm một nút lệnh một cách lập trình.

Bạn sẽ học cách tạo tài liệu trống, sử dụng `DocumentBuilder` để đặt điều khiển, và lưu kết quả dưới dạng `.docx`. Hướng dẫn cũng đề cập đến các lỗi thường gặp, chẳng hạn như hệ thống tọa độ và khả năng tương thích với các phiên bản Word cũ hơn.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.6+)
* Aspose.Words for .NET (gói NuGet `Aspose.Words`)
* Kiến thức cơ bản về C# và mô hình đối tượng Word
* Một IDE như Visual Studio hoặc VS Code

## Bước 1: Thiết lập dự án và nhập các namespace

Tạo một ứng dụng console mới và thêm gói Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

Trong `Program.cs` nhập các namespace cần thiết:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Mẹo:** Sử dụng phiên bản mới nhất của Aspose.Words để nhận được hỗ trợ đầy đủ cho API `Forms2OleControl`.

## Bước 2: Tạo tài liệu trống và khởi tạo DocumentBuilder

Lớp `Document` đại diện cho tệp Word, trong khi `DocumentBuilder` cung cấp các phương thức để chèn nội dung.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` hoạt động như một con trỏ; sau dòng này bạn có thể bắt đầu đặt các phần tử ở bất kỳ vị trí nào trong tài liệu.

## Bước 3: Xác định vị trí và kích thước của nút

Word đo tọa độ bằng điểm (1 pt ≈ 1/72 in). Cấu trúc `Rectangle` từ `System.Drawing` mô tả giới hạn của điều khiển.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` đặt điều khiển ở góc trên‑trái của trang hiện tại.
* Điều chỉnh `x` và `y` để di chuyển nút tới vị trí khác (ví dụ: `new Rectangle(150, 200, 100, 30)`).

## Bước 4: Chèn nút lệnh Forms2Ole

Bây giờ sử dụng `InsertForms2OleControl` để thêm điều khiển. Phương thức yêu cầu loại điều khiển, một tên, và giới hạn đã định nghĩa ở trên.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Đối tượng `Forms2OleControl` trả về cho phép bạn thay đổi các thuộc tính như `Enabled`, `Visible`, hoặc thậm chí gán tên macro sau này.

### Tại sao nên dùng Forms2Ole?

* **Tương thích legacy** – Các điều khiển Forms2Ole hoạt động trong Word 97‑2003 (`.doc`) và các tệp `.docx` mới hơn.
* **Hỗ trợ macro** – Chúng có thể kích hoạt macro VBA, rất thích hợp cho các mẫu tương tác.
* **Đặt vị trí chính xác** – Khác với các content control, bạn kiểm soát tọa độ một cách chính xác.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tệp ra đĩa. Chọn một thư mục mà bạn có quyền ghi.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Mở `output.docx` trong Microsoft Word. Bạn sẽ thấy một nút có nhãn **ClickMe** ở góc trên‑trái của trang đầu. Nhấn nút trong Word sẽ không làm gì cho đến khi bạn gán một macro, nhưng điều khiển đã hoạt động đầy đủ.

## Xử lý các trường hợp đặc biệt thường gặp

| Tình huống | Cách khắc phục |
|-----------|-------------------|
| **Nút xuất hiện ngoài trang** | Kiểm tra các tọa độ `Rectangle` có nằm trong lề trang hay không. Sử dụng `builder.PageSetup.PageWidth` và `PageHeight` để tính toán giới hạn an toàn. |
| **Điều khiển không hiển thị trong các phiên bản Word cũ** | Lưu tài liệu dưới dạng `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) để đảm bảo tương thích Forms2Ole với Word 97‑2003. |
| **Cần thay đổi chú thích** | Sau khi chèn, đặt `commandButton.Caption = "Submit";`. |
| **Gán macro** | Đặt `commandButton.MacroName = "MyMacro"`; macro phải tồn tại trong dự án VBA của tài liệu. |
| **Nhiều nút** | Lặp lại Bước 4 với các giá trị `Rectangle` và tên khác nhau. |

## Ví dụ hoàn chỉnh, có thể chạy được

Kết hợp mọi thứ lại, dưới đây là một chương trình tự chứa mà bạn có thể sao chép, dán và chạy:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi:** Sau khi chạy chương trình, `output.docx` sẽ mở trong Word với một nút có thể nhấn có nhãn *Click Me!* được đặt ở góc trên‑trái của trang đầu.

## Kết luận

Bây giờ bạn đã biết cách **chèn điều khiển Forms2Ole vào Word** bằng C# và Aspose.Words. Quy trình bao gồm tạo một `Document`, xác định một `Rectangle`, và gọi `InsertForms2OleControl` thông qua `DocumentBuilder`. Với mẫu mã đầy đủ và hướng dẫn xử lý các trường hợp đặc biệt, bạn có thể tích hợp các nút lệnh vào bất kỳ quy trình tự động Word nào.

### Các bước tiếp theo

* Khám phá các giá trị `ControlType` khác như `CheckBox` hoặc `OptionButton`.
* Kết hợp các điều khiển Forms2Ole với macro VBA để tạo biểu mẫu tương tác.
* Sử dụng `DocumentBuilder.MoveTo` để đặt nút trên các đoạn văn hoặc bảng cụ thể.
* Xem tài liệu **Forms2Ole** của Aspose.Words để biết các thiết lập thuộc tính nâng cao.

Chúc lập trình vui vẻ, và chúc bạn tạo ra các tài liệu Word phong phú hơn với C# và Aspose.Words!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to insert OLE command button in a Word document using C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [how to add activex control in Word with Aspose.Words – step‑by‑step guide](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}