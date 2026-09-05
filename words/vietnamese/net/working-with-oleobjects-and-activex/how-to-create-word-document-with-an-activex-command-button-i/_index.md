---
category: general
date: 2026-09-05
description: Tạo tài liệu Word bằng Aspose.Words C# và tìm hiểu cách chèn nút lệnh
  ActiveX, thiết lập kích thước nút và thêm chức năng tương tác cho nút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: vi
lastmod: 2026-09-05
og_description: Tạo tài liệu Word bằng C# và chèn một nút lệnh ActiveX. Hướng dẫn
  này chỉ cách thiết lập kích thước nút và thêm các tính năng tương tác cho nút.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Tạo tài liệu Word với nút lệnh ActiveX trong C# – hướng dẫn chi tiết
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Cách tạo tài liệu Word có nút lệnh ActiveX trong C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word với nút lệnh ActiveX trong C#

Nếu bạn cần **tạo tài liệu Word** một cách lập trình và chèn một thành phần giao diện có thể nhấp, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Sử dụng Aspose.Words cho .NET, bạn có thể **tạo tài liệu Word**, **thêm nút lệnh**, và kiểm soát giao diện của nó — tất cả mà không cần mở Microsoft Word.

Bạn sẽ học **cách chèn điều khiển ActiveX**, **đặt kích thước nút**, và làm cho nút hoạt động như một thành phần UI tương tác. Không cần kinh nghiệm trước về COM hay VBA; chỉ cần môi trường phát triển .NET và thư viện Aspose.Words.

## Những gì bạn sẽ đạt được

Kết thúc tutorial này, bạn sẽ:

* **Tạo tài liệu Word** từ đầu bằng C#.
* **Chèn một nút lệnh ActiveX** (điều khiển “Click Me” cổ điển).
* **Đặt kích thước** và vị trí của nút một cách chính xác.
* Tùy chọn thêm logic **nút tương tác** đơn giản (ví dụ, chỗ giữ macro).
* Lưu file dưới dạng `.docx` có thể mở trong Microsoft Word hoặc bất kỳ trình xem tương thích nào.

### Yêu cầu trước

| Yêu cầu | Lý do |
|-------------|--------|
| .NET 6.0 hoặc mới hơn | Cung cấp môi trường chạy cho mã C#. |
| Aspose.Words cho .NET (phiên bản mới nhất) | Cung cấp các API `Document`, `DocumentBuilder`, và `Forms2OleControl` được sử dụng trong ví dụ. |
| Visual Studio 2022 (hoặc bất kỳ IDE C# nào) | Giúp biên dịch và chạy mẫu một cách dễ dàng. |
| Kiến thức cơ bản về C# | Cần thiết để hiểu luồng mã. |

> **Mẹo chuyên nghiệp:** Nếu bạn đang dùng phiên bản dùng thử của Aspose.Words, hãy chắc chắn thiết lập giấy phép trước khi chạy mã để tránh watermark đánh giá.

## Quy trình tạo tài liệu Word – tổng quan

Quá trình bao gồm bốn bước logic:

1. **Khởi tạo tài liệu mới** và một `DocumentBuilder` để chỉnh sửa.  
2. **Chèn nút lệnh ActiveX** bằng `InsertForms2OleControl`.  
3. **Cấu hình nút** – tiêu đề, kích thước và vị trí.  
4. **Lưu** tài liệu vào đĩa.

Mỗi bước được giải thích trong phần riêng bên dưới.

![Word document with an ActiveX button](/images/activex-button.png "Screenshot of a Word document that contains an ActiveX command button created with C#")

## Cách chèn nút lệnh ActiveX

Phần **cách chèn activex** bắt đầu với phương thức `InsertForms2OleControl`. Phương thức này tạo một điều khiển dựa trên COM mà Word xem như một đối tượng ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Tại sao cách này hoạt động:** `OleControlType.CommandButton` báo cho Aspose.Words tạo nút kiểu VB cổ điển. Kích thước và vị trí được biểu thị bằng điểm (1 point = 1/72 inch), cho phép kiểm soát bố cục một cách chính xác.

## Cách thêm nút lệnh và đặt kích thước nút

Sau khi chèn điều khiển, bạn có thể điều chỉnh các thuộc tính hiển thị. Bước **thêm nút lệnh** cũng bao gồm **đặt kích thước nút**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Giải thích:**  

* `Caption` là nhãn hiển thị trên nút.  
* `Width` và `Height` cho phép bạn **đặt kích thước nút** sau khi chèn ban đầu — hữu ích khi kích thước phụ thuộc vào dữ liệu thời gian chạy.  
* `Left` và `Top` di chuyển điều khiển mà không cần tạo lại tài liệu.

> **Cạm bẫy phổ biến:** Quên sử dụng đơn vị điểm thay vì pixel sẽ khiến nút quá nhỏ hoặc quá lớn. Luôn chuyển đổi giá trị pixel (`px * 72 / DPI`) nếu bạn bắt đầu từ đo lường trên màn hình.

## Cách thêm nút tương tác (tùy chọn)

Một nút ActiveX có thể thực thi macro khi được nhấp, nhưng nhúng mã VBA từ C# nằm ngoài phạm vi của quy trình Aspose.Words thuần. Thay vào đó, bạn có thể thêm một thuộc tính chỗ giữ mà Word sẽ nhận diện là tên macro.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Khi người dùng mở file `.docx` được tạo trong Word, việc nhấp nút sẽ cố gắng chạy `MyMacroName`. Nếu macro không tồn tại, Word sẽ yêu cầu người dùng tạo nó.

**Tại sao bạn có thể muốn dùng cách này:** Đối với các mẫu doanh nghiệp mà macro điền vào các trường, mã C# chỉ cần đặt nút; logic macro tồn tại trong dự án VBA của tài liệu.

## Lưu tài liệu và kiểm tra kết quả

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

> **Kết quả mong đợi:** Mở `CommandButton.docx` trong Microsoft Word sẽ hiển thị một nút có nhãn **Click Me** nằm cách lề trái 100 pts và cách lề trên 120 pts. Kích thước nút là **200 pts × 80 pts**. Nhấp nút sẽ kích hoạt chỗ giữ macro (nếu có).

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là chương trình đầy đủ, có thể chạy được, kết hợp mọi thứ lại. Sao chép vào một dự án Console App mới, thêm gói NuGet Aspose.Words, và chạy.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Chạy chương trình, sau đó mở file đã tạo. Bạn sẽ thấy **nút tương tác** sẵn sàng cho việc tùy chỉnh thêm.

## Câu hỏi thường gặp

| Câu hỏi | Trả lời |
|----------|--------|
| **Có hoạt động với .NET Core không?** | Có. Aspose.Words hỗ trợ .NET Standard, vì vậy cùng một đoạn mã chạy trên .NET 5/6/7. |
| **Tôi có thể dùng các điều khiển ActiveX khác (ví dụ, CheckBox) không?** | Chắc chắn. Thay `OleControlType.CommandButton` bằng `OleControlType.CheckBox`, `OleControlType.OptionButton`, v.v. |
| **Nếu tôi cần nút lớn hơn trên trang ngang thì sao?** | Điều chỉnh các thuộc tính `Width`, `Height`, `Left`, và `Top` một cách tỷ lệ. Nhớ rằng đơn vị điểm vẫn giữ nguyên bất kể hướng trang. |
| **Có cần macro để nút có thể nhấp được không?** | Không. Nút đã hoạt động như một thành phần UI; macro chỉ thêm hành vi tùy chỉnh khi nhấp. |

## Kết luận

Bạn đã biết cách **tạo tài liệu Word** với Aspose.Words, **thêm nút lệnh**, **đặt kích thước nút**, và tùy chọn liên kết nút với macro để có hành vi **thêm nút tương tác**. Cách tiếp cận này cho phép bạn tự động hoá việc tạo mẫu, sinh báo cáo động, hoặc xây dựng nguyên mẫu UI dựa trên Word trực tiếp từ C#.

Tiếp theo, bạn có thể khám phá:

* **Cách chèn hộp kiểm ActiveX** cho các mẫu khảo sát.  
* **Cách thêm nội dung văn bản phong phú** quanh nút bằng `DocumentBuilder`.  
* **Cách bảo vệ tài liệu** trong khi vẫn giữ cho nút hoạt động.  

Hãy thoải mái thử nghiệm với các loại điều khiển, kích thước và tên macro khác nhau để phù hợp với kịch bản của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}