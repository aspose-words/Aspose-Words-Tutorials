---
category: general
date: 2026-10-10
description: Đặt văn bản cho nút và thêm nút ActiveX trong C# bằng Aspose.Words. Tìm
  hiểu cách chèn nút, tạo điều khiển nút và tùy chỉnh chú thích trong tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: vi
lastmod: 2026-10-10
og_description: Đặt văn bản cho nút và thêm nút ActiveX trong C# với Aspose.Words.
  Hãy làm theo hướng dẫn từng bước này để chèn một nút, tạo điều khiển nút và tùy
  chỉnh chú thích của nó.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Đặt văn bản cho nút và thêm nút ActiveX trong C# – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Thiết lập văn bản nút và thêm nút ActiveX trong C#
url: /vi/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt văn bản nút và thêm nút ActiveX trong C#

Nếu bạn cần **đặt văn bản nút** trên một nút ActiveX trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Khi kết thúc bài học, bạn sẽ có thể **chèn nút**, tạo một **điều khiển nút**, và tùy chỉnh tiêu đề của nó chỉ với vài dòng mã C#.

Làm việc với các điều khiển ActiveX thường gặp khi bạn muốn tạo các biểu mẫu tương tác trong Word—cho dù bạn đang xây dựng mẫu hợp đồng, khảo sát, hay công cụ nội bộ. Ví dụ này sử dụng Aspose.Words for .NET, một thư viện cho phép bạn thao tác các tệp Word mà không cần cài đặt Microsoft Office.

## Yêu cầu trước

Trước khi bắt đầu, hãy đảm bảo bạn có:

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#)  
* Giấy phép Aspose.Words for .NET (bản dùng thử miễn phí đủ cho việc học)  

Bạn cũng cần tham chiếu tới gói NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Cách chèn nút vào tài liệu Word

Bước đầu tiên là tạo một `Document` mới và một `DocumentBuilder`. Builder là điểm vào để thêm nội dung, bao gồm cả các điều khiển ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:** `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp các phương thức cấp cao như `InsertParagraph` và `InsertFormField`. Bắt đầu với một tài liệu trống sẽ đảm bảo nút xuất hiện đúng vị trí bạn muốn.

## Tạo điều khiển nút với Forms2OleControl

Bây giờ chúng ta tạo điều khiển nút thực tế. `Forms2OleControl` là lớp mà Aspose.Words dùng cho tất cả các đối tượng ActiveX, và kiểu `COMMANDBUTTON` sẽ hiển thị dưới dạng một nút có thể nhấn trong Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Giải thích:**  
* `InsertForms2OleControl` đặt điều khiển tại tọa độ chính xác mà bạn cung cấp.  
* Kích thước được định nghĩa bằng điểm (1 point = 1/72 inch). Điều chỉnh các số này để phù hợp với bố cục của bạn.

## Thêm điều khiển ActiveX và đặt tên duy nhất

Mỗi đối tượng ActiveX nên có một tên riêng để bạn có thể tham chiếu sau này (ví dụ, khi xử lý sự kiện trong VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Mẹo:** Tránh dùng dấu cách hoặc ký tự đặc biệt trong tên; Word coi tên như một định danh trong mô hình biểu mẫu nội bộ.

## Đặt văn bản nút (caption) trên nút ActiveX

Đây là nơi từ khóa chính **set button text** phát huy tác dụng. Thuộc tính `Caption` xác định nhãn mà người dùng sẽ thấy trên nút.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Bạn có thể thay đổi caption bất kỳ lúc nào trước khi lưu tài liệu. Nếu sau này cần bản địa hoá giao diện, chỉ cần gọi lại `SetCaption` với một chuỗi khác.

## Lưu tài liệu và kiểm tra kết quả

Cuối cùng, ghi tài liệu ra đĩa. Mở tệp trong Microsoft Word sẽ hiển thị nút với caption tùy chỉnh.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Kết quả mong đợi:** Khi bạn mở *ActiveXButton.docx* trong Word, sẽ thấy một nút được đặt ở tọa độ đã chỉ định, nhãn **Click Me**. Nhấn nút sẽ kích hoạt hành vi mặc định của nút lệnh trong Word (bạn có thể tùy chỉnh sau này bằng VBA).

![Set button text example](https://example.com/activex-button.png){alt="Ví dụ đặt văn bản nút"}

## Thêm nút ActiveX và xử lý sự kiện (tùy chọn)

Nếu bạn muốn nút thực hiện một hành động tùy chỉnh, bạn có thể thêm macro VBA phản hồi sự kiện `Click`. Macro có thể được chèn bằng chương trình, nhưng điều đó nằm ngoài phạm vi của hướng dẫn này. Điều quan trọng là nút đã có mặt và caption đã được đặt—sẵn sàng cho bất kỳ xử lý sự kiện nào bạn muốn.

## Những lỗi thường gặp và cách tránh

| Vấn đề | Tại sao xảy ra | Cách khắc phục |
|-------|----------------|----------------|
| Nút hiển thị lệch | Tọa độ tính bằng điểm, không phải pixel | Chuyển đổi giá trị pixel sang điểm (`points = pixels * 72 / DPI`) |
| Caption không thay đổi sau khi lưu | Gọi `SetCaption` sau `Save` | Luôn đặt caption **trước** khi gọi `doc.Save` |
| Điều khiển không hiển thị trong các phiên bản Word cũ | Một số bản Word cũ không hỗ trợ đầy đủ ActiveX | Kiểm tra trên phiên bản Word mục tiêu; cân nhắc dùng `CheckBox` hoặc `DropDownList` làm dự phòng |
| Cảnh báo giấy phép trong đầu ra | Giấy phép dùng thử hết hạn | Áp dụng giấy phép Aspose.Words hợp lệ bằng `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy. Nó bao gồm tất cả các chỉ thị `using` cần thiết và minh họa toàn bộ quy trình từ tạo tài liệu đến lưu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Chạy chương trình bằng `dotnet run`. Sau khi thực thi, mở *ActiveXButton.docx* để xác nhận rằng caption của nút là **Click Me**.

## Tóm tắt những gì bạn đã học

* Bạn đã học cách **set button text** trên một nút ActiveX bằng Aspose.Words.  
* Bạn đã thấy các bước cụ thể để **how to insert button**, **create button control**, và **add activex control** vào tài liệu Word.  
* Giờ đây bạn có một đoạn mã có thể tái sử dụng và điều chỉnh cho bất kỳ dự án tự động hoá Word dựa trên biểu mẫu nào.

## Các bước tiếp theo

* Khám phá các giá trị `Forms2OleControlType` khác như `CHECKBOX` hoặc `LISTBOX` để xây dựng các biểu mẫu phong phú hơn.  
* Kết hợp nút với macro VBA để thực hiện tính toán hoặc kiểm tra dữ liệu.  
* Sử dụng API `FormField` của Aspose.Words để đọc dữ liệu người dùng nhập sau khi tài liệu đã được điền.

Hãy tự do thử nghiệm kích thước, vị trí và caption để phù hợp với yêu cầu thiết kế của bạn. Nếu gặp bất kỳ vấn đề nào, tài liệu Aspose.Words cung cấp các tham chiếu chi tiết cho mọi lớp được sử dụng trong hướng dẫn này.

Chúc lập trình vui vẻ!


## Bạn nên học gì tiếp theo?


Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong bài viết này. Mỗi tài nguyên đều có mã mẫu hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}