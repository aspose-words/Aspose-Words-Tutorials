---
category: general
date: 2026-08-04
description: Tạo tài liệu Word bằng cách lập trình sử dụng C#. Tìm hiểu cách thêm
  nút lệnh một cách lập trình với Aspose.Words chỉ trong vài bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: vi
lastmod: 2026-08-04
og_description: Tạo tài liệu Word bằng lập trình với Aspose.Words. Hướng dẫn này cho
  thấy cách thêm nút lệnh bằng lập trình, cấu hình nó và lưu tệp.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Tạo tài liệu Word bằng lập trình – hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word bằng lập trình – hướng dẫn từng bước
url: /vi/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình – hướng dẫn C# đầy đủ

Nếu bạn cần **tạo tài liệu word bằng chương trình**, hướng dẫn này sẽ cho bạn thấy cách thực hiện với Aspose.Words cho .NET. Chỉ trong vài dòng C# bạn có thể tạo một tệp `.docx` trống, **thêm nút lệnh** một cách lập trình, thiết lập các thuộc tính của chúng và lưu kết quả.  

Các bước dưới đây bao gồm mọi thứ từ thiết lập dự án đến xử lý các trường hợp đặc biệt, vì vậy bạn có thể sao chép mã vào ứng dụng của mình và chạy mà không cần chỉnh sửa.

## Những gì bạn sẽ đạt được

* Khởi tạo một tài liệu Word mới hoàn toàn trong bộ nhớ.  
* **Thêm nút lệnh** OLE một cách lập trình tại bất kỳ vị trí và kích thước nào.  
* Cấu hình chú thích của nút, tên nội bộ và các thuộc tính OLE khác.  
* Lưu tài liệu đã tạo vào đĩa hoặc một luồng để xử lý tiếp theo.

### Yêu cầu trước

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+).  
* Giấy phép Aspose.Words cho .NET hợp lệ (hoặc bản dùng thử miễn phí).  
* Kiến thức cơ bản về C# và Visual Studio (hoặc bất kỳ IDE nào bạn chọn).

> **Mẹo:** Nếu bạn chạy mẫu mà không có giấy phép, Aspose.Words sẽ thêm một dấu nước đánh giá nhỏ vào trang đầu tiên.

## Bước 1: Thiết lập dự án và nhập các namespace cần thiết

Tạo một ứng dụng Console mới (hoặc tích hợp vào dịch vụ hiện có) và thêm gói NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Sau đó, bao gồm các namespace cần thiết ở đầu tệp `.cs` của bạn:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Các import này cho phép bạn truy cập `Document`, `DocumentBuilder`, `Forms2OleControl`, và struct `RectangleF` được sử dụng để định vị.

## Bước 2: Khởi tạo một tài liệu Word mới

Hoạt động đầu tiên trong bất kỳ quy trình **tạo tài liệu word bằng chương trình** nào là tạo một đối tượng `Document`. Đối tượng này chỉ tồn tại trong bộ nhớ cho đến khi bạn lưu nó một cách rõ ràng.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` hoạt động như một con trỏ theo dõi vị trí sẽ đặt phần tử tiếp theo. Sử dụng nó giúp mã ngắn gọn và mô phỏng cách bạn gõ trực tiếp trong Word.

## Bước 3: Chèn điều khiển OLE nút lệnh

Aspose.Words cung cấp phương thức `InsertForms2OleControl` để nhúng các đối tượng OLE như nút lệnh, hộp kiểm, hoặc hộp combo. Phương thức này yêu cầu ba đối số:

1. Giá trị enum `ControlType` (ở đây là `CommandButton`).  
2. Một `RectangleF` xác định vị trí X‑Y và chiều rộng‑cao của điều khiển (được đo bằng điểm, trong đó 72 pt = 1 inch).  
3. Tùy chọn, các thuộc tính OLE bổ sung (không cần cho nút cơ bản).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Tại sao điều này hoạt động:** `InsertForms2OleControl` tạo một container OLE trong tài liệu và trả về một wrapper `Forms2OleControl`. Wrapper này cho phép bạn thao tác với đối tượng OLE nền (nút thực tế) mà không cần xử lý COM interop cấp thấp.

## Bước 4: Cấu hình chú thích và tên nội bộ của nút

Sau khi chèn, bạn thường muốn đặt cho nút một nhãn hiển thị cho người dùng và một định danh nội bộ mà macro hoặc add‑in của bạn có thể tham chiếu sau này.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` là văn bản hiển thị trên nút trong giao diện Word.  
* `Name` là định danh lập trình được VBA hoặc các script tự động bên ngoài sử dụng.

### Tùy chọn: Gán macro cho nút

Nếu bạn dự định chạy một macro VBA khi nút được nhấn, bạn có thể gắn tên macro:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Trường hợp đặc biệt:** Khi tài liệu mục tiêu được mở trên máy không có macro, Word sẽ hiển thị cảnh báo bảo mật. Luôn ký các macro của bạn hoặc thông báo cho người dùng về các cài đặt cần thiết.

## Bước 5: Lưu tài liệu

Bạn có thể ghi tệp vào đĩa, một `MemoryStream`, hoặc trực tiếp vào đối tượng phản hồi trong một web API. Cách đơn giản nhất cho demo console là lưu vào thư mục cục bộ:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Tệp `.docx` kết quả sẽ mở trong Microsoft Word với một nút lệnh hoạt động hiển thị “Click Me”. Nhấn nút sẽ kích hoạt macro đã gán (nếu có) hoặc chỉ hiển thị một thông báo mặc định.

## Ví dụ hoàn chỉnh hoạt động

Sao chép chương trình sau vào `Program.cs` và chạy nó. Nó minh họa toàn bộ quy trình **tạo tài liệu word bằng chương trình**, bao gồm xử lý lỗi.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Kết quả mong đợi:** Mở `CommandButton.docx` trong Word sẽ hiển thị một nút có nhãn “Click Me”. Di chuột lên nút sẽ hiển thị tên `cmdClickMe` trong bảng thuộc tính.

## Các câu hỏi thường gặp và khắc phục sự cố

| Câu hỏi | Trả lời |
|----------|--------|
| *Tôi có thể thêm nút vào tài liệu hiện có không?* | Có. Tải tệp bằng `new Document("Existing.docx")`, sau đó sử dụng cùng một lệnh `InsertForms2OleControl`. |
| *`RectangleF` sử dụng đơn vị nào?* | Điểm (1 inch = 72 pt). Điều chỉnh giá trị để đặt vị trí nút một cách chính xác. |
| *Nút có hoạt động trên Word cho Mac không?* | Các điều khiển OLE chỉ được hỗ trợ trên Word Windows. Trên Mac, nút sẽ hiển thị dưới dạng hình ảnh tĩnh. |
| *Tôi có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?* | Giấy phép thương mại loại bỏ dấu nước đánh giá và mở khóa đầy đủ tính năng. |
| *Làm thế nào để thay đổi kích thước của nút sau khi chèn?* | Sửa `commandButton.Width` và `commandButton.Height` hoặc chèn lại với một `RectangleF` mới. |

## Mở rộng giải pháp

Bây giờ bạn đã biết cách **thêm nút lệnh** một cách lập trình, bạn có thể khám phá các chủ đề liên quan sau:

* **Chèn các điều khiển biểu mẫu khác** – sử dụng `ControlType.CheckBox`, `ControlType.OptionButton`, v.v. (bao gồm từ khóa phụ *Aspose.Words InsertForms2OleControl*).  
* **Điền dữ liệu động vào tài liệu** – hợp nhất dữ liệu từ cơ sở dữ liệu vào bảng hoặc trường mail‑merge.  
* **Xuất ra PDF** – sau khi thêm nút, gọi `doc.Save("output.pdf", SaveFormat.Pdf)` để tạo phiên bản PDF (liên quan đến *C# Word automation*).  

## Kết luận

Bạn đã có một mẫu hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **tạo tài liệu word bằng chương trình** và **thêm nút lệnh** một cách lập trình bằng Aspose.Words cho .NET. Hướng dẫn đã bao gồm thiết lập dự án, khởi tạo tài liệu, chèn nút OLE, cấu hình thuộc tính và lưu tệp. Bạn có thể tự do điều chỉnh mã để chèn các điều khiển biểu mẫu khác, gắn macro, hoặc tích hợp logic vào dịch vụ web hoặc công việc nền.

Chúc lập trình vui vẻ và tận hưởng việc tự động hoá tài liệu Word!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Tạo tài liệu Word với bảng bằng Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Tạo hình dạng nhóm trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}