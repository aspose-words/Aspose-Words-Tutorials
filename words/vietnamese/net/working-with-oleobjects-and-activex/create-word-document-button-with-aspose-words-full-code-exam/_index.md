---
category: general
date: 2026-07-23
description: tạo nút tài liệu Word bằng Aspose.Words – hướng dẫn chi tiết cách chèn
  một ActiveX CommandButton vào tệp .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: vi
lastmod: 2026-07-23
og_description: 'tạo nút tài liệu Word với Aspose.Words: học cách nhúng một ActiveX
  CommandButton vào tệp Word trong vài phút.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Nút Tạo Tài liệu Word – Hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Tạo nút tạo tài liệu Word với Aspose.Words – Ví dụ mã đầy đủ
url: /vi/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# tạo nút tài liệu word với Aspose.Words – Hướng dẫn lập trình đầy đủ

Bạn đã bao giờ cần **tạo nút tài liệu word** nhưng không chắc API nào nên dùng? Bạn không đơn độc—hầu hết các nhà phát triển gặp khó khăn khi cố gắng nhúng các điều khiển tương tác vào tệp .docx. Tin tốt? Với Aspose.Words for .NET, bạn có thể chèn một ActiveX CommandButton hoạt động đầy đủ vào tài liệu Word chỉ với vài dòng mã.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình: từ việc thiết lập dự án, khởi tạo một `DocumentBuilder`, chèn nút bằng `InsertForms2OleControl`, và cuối cùng lưu tệp để Word nhận ra điều khiển. Khi kết thúc, bạn sẽ có một tệp Word sẵn sàng sử dụng chứa một nút có thể nhấn—không cần các thao tác phức tạp COM interop.

## Những gì bạn cần

- **.NET 6.0** hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+).  
- Gói NuGet **Aspose.Words for .NET** (phiên bản 23.9 hoặc mới hơn).  
- Kiến thức cơ bản về C# (chúng tôi sẽ giữ cú pháp thân thiện với người mới).  
- Visual Studio 2022 hoặc bất kỳ IDE nào bạn thích.

Chỉ vậy—không cần tham chiếu COM bổ sung, không cần Office interop, chỉ mã quản lý thuần túy.

---

## Bước 1: Thiết lập Aspose.Words để **tạo nút tài liệu word**

Đầu tiên, thêm gói Aspose.Words vào dự án của bạn:

```bash
dotnet add package Aspose.Words
```

Hoặc, nếu bạn đang sử dụng giao diện NuGet của Visual Studio, tìm kiếm “Aspose.Words” và nhấn **Install**. Dòng lệnh duy nhất này cho phép bạn truy cập vào các lớp `Document`, `DocumentBuilder`, và phương thức `InsertForms2OleControl` mà chúng ta sẽ cần sau này.

> **Mẹo chuyên nghiệp:** Giữ các gói NuGet của bạn luôn cập nhật; các phiên bản mới thường bao gồm các bản sửa lỗi cho việc xử lý ActiveX.

---

## Bước 2: Khởi tạo **DocumentBuilder** cho một **ActiveX CommandButton**

Bây giờ chúng ta tạo một tài liệu Word mới và khởi động một `DocumentBuilder`. Hãy nghĩ về `DocumentBuilder` như một chiếc cọ vẽ cho phép bạn vẽ nội dung lên canvas.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Chú ý cách chúng ta nhập `System.Drawing`—cấu trúc `Rectangle` xác định vị trí và kích thước của nút. Đây là nơi **ActiveX CommandButton** sẽ được đặt.

---

## Bước 3: Sử dụng **InsertForms2OleControl** để **thêm một CommandButton**

Đây là phần cốt lõi của hướng dẫn: chèn chính nút. Phương thức `InsertForms2OleControl` nhận ba đối số—loại điều khiển, một `Rectangle`, và tùy chọn một tên. Chúng ta sẽ sử dụng `OleControlType.CommandButton` để chỉ định điều khiển cụ thể mà chúng ta muốn.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Lệnh duy nhất này thực hiện rất nhiều:

1. **Tạo** một đối tượng OLE bên trong tệp Word.  
2. **Đăng ký** nó như một ActiveX CommandButton, mà Word sẽ hiển thị như một phần tử UI có thể nhấn.  
3. **Đặt vị trí** theo rectangle mà chúng ta cung cấp.

Nếu bạn cần thay đổi chú thích của nút hoặc các thuộc tính khác, bạn có thể làm điều đó sau khi chèn bằng cách truy cập `OleFormat` nền tảng. Đối với hầu hết các trường hợp, chú thích mặc định (“CommandButton1”) là đủ.

---

## Bước 4: Lưu tài liệu Word chứa **CommandButton**

Lưu trữ rất đơn giản—chỉ cần chỉ đến một thư mục bạn có quyền ghi. Phần mở rộng tệp phải là `.docx` để nút tồn tại qua quá trình lưu.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Khi bạn mở `CommandButton.docx` trong Microsoft Word, bạn sẽ thấy một nút nhỏ ở góc trên‑trái của trang đầu tiên. Nhấn vào nó không làm gì cả (điều đó sẽ cần VBA), nhưng điều khiển này hoàn toàn hoạt động và có thể được kết nối sau.

> **Tại sao cách này hoạt động:** Aspose.Words ghi luồng OLE trực tiếp vào gói DOCX, bỏ qua việc Word phải tạo điều khiển tại thời gian chạy. Điều này đảm bảo nút xuất hiện chính xác ở vị trí bạn đã đặt.

---

## Bước 5: Xác minh nút trong Word

Mở tệp đã tạo:

1. Mở Microsoft Word.  
2. Điều hướng tới **File → Open** và chọn `CommandButton.docx`.  
3. Bạn sẽ thấy một nút hình chữ nhật có nhãn “CommandButton1”.

Nếu bạn không thấy nút, hãy chắc chắn **Design Mode** được bật (Developer → Design Mode). Điều này sẽ bật/tắt hiển thị trực quan của các điều khiển ActiveX.

---

## Bước 6: Tùy chọn nâng cao – Tùy chỉnh **ActiveX CommandButton**

Dưới đây là một vài tùy chỉnh nhanh mà bạn có thể thấy hữu ích:

| Mục tiêu | Đoạn mã |
|------|--------------|
| Thay đổi chú thích | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Đặt tên macro (cần hỗ trợ macro Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Thay đổi kích thước sau khi chèn | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Các đoạn mã này minh họa tính linh hoạt của `InsertForms2OleControl`. Bạn thậm chí có thể nhúng các điều khiển ActiveX khác như `CheckBox` hoặc `ListBox` bằng cách thay đổi enum `OleControlType`.

---

## Ví dụ hoạt động đầy đủ

Dưới đây là chương trình hoàn chỉnh, sẵn sàng sao chép‑dán, **tạo nút tài liệu word** từ đầu:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Kết quả mong đợi khi bạn chạy chương trình:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Mở tệp kết quả và bạn sẽ thấy nút ở đúng vị trí mà mã đã đặt.

---

## Những lỗi thường gặp & Cách tránh

- **Thiếu tham chiếu `System.Drawing`** – Cấu trúc `Rectangle` nằm ở đó; nếu không có, trình biên dịch sẽ báo lỗi.  
- **Sử dụng phiên bản Aspose.Words cũ** – Các bản phát hành sớm không hỗ trợ đầy đủ `InsertForms2OleControl`. Nâng cấp lên gói ổn định mới nhất.  
- **Lưu dưới dạng `.doc` thay vì `.docx`** – Luồng OLE sẽ bị loại bỏ trong định dạng nhị phân cũ, khiến nút biến mất.  
- **Chạy trên máy chủ không có giao diện (headless) mà không cài Word** – Nút vẫn sẽ có trong tệp, nhưng bạn không thể xem trước mà không có Word. Điều này vẫn ổn cho các pipeline tạo tự động.

---

## Các bước tiếp theo – Mở rộng quy trình **tạo nút tài liệu word**

Bây giờ bạn đã nắm vững các kiến thức cơ bản, hãy xem xét những ý tưởng nâng cao sau:

- **Gắn macro VBA** vào nút để thực hiện logic nghiệp vụ tùy chỉnh.  
- **Tạo nhiều nút** trong một vòng lặp cho các biểu mẫu động.  
- **Kết hợp với Aspose.PDF** để xuất cùng tài liệu sang PDF trong khi giữ nguyên bố cục trực quan (nút sẽ trở thành hình ảnh tĩnh trong PDF).  
- **

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ cùng giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Chèn ảnh nội tuyến trong tài liệu Word bằng Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}