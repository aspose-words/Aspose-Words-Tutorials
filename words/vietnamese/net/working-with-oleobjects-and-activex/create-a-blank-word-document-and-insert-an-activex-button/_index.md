---
category: general
date: 2026-11-18
description: Tạo một tài liệu Word trống và chèn một nút ActiveX bằng C#. Tìm hiểu
  cách thêm điều khiển, đặt chú thích cho nút và lưu tệp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: vi
lastmod: 2026-11-18
og_description: Tạo một tài liệu Word trống và chèn một nút ActiveX bằng C#. Theo
  dõi hướng dẫn đầy đủ này để thêm điều khiển, đặt nhãn cho nút và lưu kết quả.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Tạo tài liệu Word trống và chèn nút ActiveX – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Tạo một tài liệu Word trống và chèn nút ActiveX
url: /vi/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu Word trống và chèn nút ActiveX

Nếu bạn cần **tạo một tài liệu Word trống** và đặt một nút ActiveX tương tác bên trong, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác với Aspose.Words cho .NET. Bạn sẽ xem toàn bộ mã, hiểu tại sao mỗi dòng lại quan trọng, và học cách **đặt chú thích cho nút** để điều khiển trông sẵn sàng cho người dùng tương tác.

Ngoài mục tiêu chính, chúng tôi sẽ đề cập đến **cách chèn ActiveX**, các bước **cách thêm điều khiển** vào tệp Word, và những chi tiết của **chèn nút ActiveX** với chú thích tùy chỉnh. Khi kết thúc, bạn sẽ có một mẫu có thể tái sử dụng cho bất kỳ kịch bản tự động hoá tài liệu nào yêu cầu các phần tử UI nhúng.

## Những gì bạn sẽ học

* Cách **tạo một tài liệu Word trống** một cách lập trình.  
* Các lời gọi API chính xác cần thiết để **chèn nút ActiveX** và cấu hình các thuộc tính của nó.  
* Cách **đặt chú thích cho nút** để điều khiển hiển thị văn bản mong muốn.  
* Mẹo lưu tệp ở vị trí bạn chọn và xử lý các vấn đề thường gặp.

### Yêu cầu trước

* .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.6+).  
* Aspose.Words cho .NET đã được cài đặt (`Install-Package Aspose.Words`).  
* Kiến thức cơ bản về C# và Visual Studio hoặc bất kỳ IDE nào tương thích với .NET.

---

## Tạo một tài liệu Word trống với Aspose.Words

Bước đầu tiên là tạo một đối tượng `Document` trống. Đối tượng này đại diện cho một tệp Word không có nội dung nào cho đến khi chúng ta thêm vào.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Tại sao điều này quan trọng*: Một `Document` trống cung cấp cho bạn một nền sạch. Bạn có thể sau này thêm đoạn văn, bảng hoặc điều khiển mà không lo lắng về định dạng đã tồn tại.

---

## Khởi tạo DocumentBuilder để làm việc với tài liệu

`DocumentBuilder` là một lớp trợ giúp cho phép bạn chèn nội dung tại vị trí con trỏ hiện tại. Nó tự động theo dõi vị trí của bạn trong tài liệu.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Tại sao điều này quan trọng*: Nếu không có `DocumentBuilder` bạn sẽ phải thao tác cây node cấp thấp một cách thủ công. Builder đơn giản hoá việc chèn văn bản, hình ảnh và các điều khiển ActiveX.

---

## Cách chèn một nút ActiveX (insert activex button)

Giờ chúng ta sử dụng `InsertForms2OleControl` để nhúng một điều khiển ActiveX. Phương thức này yêu cầu ba đối số:

1. Loại điều khiển (`OleControlType.CommandButton`).  
2. Tên nội bộ cho điều khiển (được VBA hoặc mã macro sử dụng).  
3. Một `RectangleF` xác định vị trí và kích thước trên trang.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Tại sao điều này quan trọng*: Đây là cốt lõi của **cách chèn activex** vào tài liệu Word. Các tọa độ của hình chữ nhật được biểu diễn bằng điểm (1 point = 1/72 inch). Điều chỉnh chúng để đặt nút ở vị trí bạn cần.

### Mẹo

Nếu bạn cần nút xuất hiện trên một trang cụ thể, hãy di chuyển con trỏ của builder trước:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Cách đặt chú thích cho nút (set button caption)

Sau khi điều khiển được đặt, bạn có thể sửa đổi các thuộc tính của nó. Thuộc tính dễ nhìn nhất là `Caption`, xác định văn bản hiển thị trên nút.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Tại sao điều này quan trọng*: Người dùng nhìn thấy chú thích, không phải tên nội bộ. Thay đổi nó làm cho nút có ý nghĩa trong tài liệu cuối cùng.

---

## Lưu tài liệu chứa nút

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, v.v.). Ở đây chúng tôi lưu dưới dạng tài liệu Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Tại sao điều này quan trọng*: Lưu trữ tệp cho phép bạn mở nó trong Microsoft Word và kiểm tra nút. Khi tài liệu được mở, nút sẽ xuất hiện với chú thích “Press”.

### Kết quả mong đợi

Mở `with_button.docx` trong Word sẽ hiển thị một trang trống với một nút hình chữ nhật có nhãn **Press**. Nhấn nút sẽ không thực hiện gì theo mặc định vì không có macro VBA nào được gắn, nhưng điều khiển này hoàn toàn hoạt động và có thể được kết nối với mã sau này.

---

## Cách thêm điều khiển vào một đoạn văn cụ thể (how to add control)

Đôi khi bạn muốn nút nằm trong một đoạn văn cụ thể, ví dụ sau một đoạn văn hướng dẫn. Sử dụng `MoveTo` để đặt vị trí builder trước khi chèn điều khiển.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Tại sao điều này quan trọng*: Mẫu này minh họa **cách thêm điều khiển** trong ngữ cảnh, đảm bảo bố cục tài liệu vẫn hợp lý.

---

## Những khó khăn thường gặp và cách tránh chúng

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Nút xuất hiện ngoài trang | Tọa độ hình chữ nhật nằm ngoài lề trang | Sử dụng `builder.PageSetup` để lấy kích thước trang và tính toán một `RectangleF` an toàn. |
| Chú thích không hiển thị | `Caption` được đặt trước khi điều khiển được khởi tạo hoàn toàn | Đặt `Caption` **sau** lời gọi `InsertForms2OleControl`, như đã trình bày ở Bước 4. |
| Tài liệu lưu mà không có nút | Con trỏ builder đã được di chuyển sau khi chèn mà không ghi lại thay đổi | Giữ builder trên cùng một trang hoặc gọi `builder.Document.UpdatePageLayout()` trước khi lưu. |

---

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy. Nó tạo một tệp Word trống, chèn một nút ActiveX, đặt chú thích cho nó và lưu kết quả.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả**: Sau khi chạy chương trình, mở `C:\Temp\with_button.docx` trong Microsoft Word. Bạn sẽ thấy một trang duy nhất với văn bản “Below is an ActiveX button created programmatically:” tiếp theo là một nút có nhãn **Press**.

---

## Kết luận

Bạn đã biết cách **tạo một tài liệu Word trống**, **chèn một nút ActiveX**, **đặt chú thích cho nút**, và **lưu** kết quả bằng Aspose.Words cho .NET. Mẫu tương tự có thể mở rộng cho các điều khiển ActiveX khác (checkbox, list box, v.v.) bằng cách thay đổi `OleControlType`.

Tiếp theo, bạn có thể khám phá **cách chèn sự kiện nút ActiveX** bằng VBA, hoặc **cách thêm điều khiển** vào các tài liệu hiện có đã chứa nội dung. Cả hai chủ đề đều dựa trực tiếp trên các khái niệm đã được trình bày ở đây.

Chúc lập trình vui vẻ, và hãy thoải mái thử nghiệm các kích thước, vị trí và chú thích khác nhau để phù hợp với yêu cầu UI của ứng dụng của bạn!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo tài liệu Word C# với nút lệnh ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Cách thêm nút ActiveX vào tài liệu Word với Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}