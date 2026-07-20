---
category: general
date: 2026-07-19
description: Tạo tài liệu Word bằng Aspose.Words C# và tìm hiểu cách thêm nút lệnh
  ActiveX, thiết lập kích thước nút và chèn nút một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: vi
lastmod: 2026-07-19
og_description: Tạo tài liệu Word với Aspose.Words C# và chèn nút lệnh ActiveX trong
  vài giây. Thực hiện theo hướng dẫn chi tiết để đặt kích thước nút và chèn nút một
  cách dễ dàng.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Tạo tài liệu Word với nút ActiveX – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Tạo tài liệu Word với nút ActiveX – Hướng dẫn C#
url: /vi/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Tài liệu Word với Nút ActiveX – Hướng dẫn đầy đủ C# 

Bạn đã bao giờ tự hỏi làm thế nào để **create word document** chứa một nút ActiveX hoạt động? Có thể bạn đang tự động hoá báo cáo và cần một điều khiển “Approve” có thể nhấn ngay trong tệp. Trong hướng dẫn này, chúng tôi sẽ đi qua từng bước—sử dụng Aspose.Words cho .NET để thêm một nút lệnh ActiveX, đặt kích thước và chèn nó vào vị trí bạn muốn.  

Nếu bạn từng tự hỏi *how to add activex* điều khiển mà không cần mở Word thủ công, bạn đang ở đúng chỗ. Khi kết thúc, bạn sẽ có một ví dụ có thể chạy, giải thích rõ ràng từng bước và các mẹo để xử lý những khó khăn thường gặp.

## Những gì bạn sẽ học

- Cách thiết lập Aspose.Words trong dự án C#  
- Mã chính xác để **create word document** và nhúng một nút lệnh ActiveX  
- Cách **set button size** và tùy chỉnh chú thích cũng như tên của nó  
- Phương pháp đúng để **insert command button** và **how to insert button** ở bất kỳ vị trí nào trong tài liệu  
- Các lưu ý trường hợp đặc biệt (phiên bản Word, giới hạn nền tảng, cảnh báo bảo mật)

### Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Framework 4.7+).  
- Giấy phép Aspose.Words cho .NET hợp lệ (hoặc khóa dùng thử miễn phí).  
- Visual Studio 2022 (hoặc bất kỳ IDE nào bạn thích).  
- Kiến thức cơ bản về C# và lập trình hướng đối tượng.

Không cần thư viện bên thứ ba nào khác.

---

## Bước 1: Tạo Tài liệu Word – Cài đặt dự án

Trước khi chúng ta có thể **insert command button**, chúng ta cần một tệp Word trống để làm việc. Bước này cũng trình bày mẫu “create word document” cổ điển sử dụng Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tại sao điều này quan trọng:** `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` theo dõi vị trí con trỏ hiện tại. Tất cả các chèn tiếp theo (bao gồm cả điều khiển ActiveX của chúng ta) diễn ra dựa trên builder này.

---

## Bước 2: Cách Thêm ActiveX – Xây dựng Điều khiển CommandButton

Bây giờ tài liệu đã tồn tại, chúng ta sẽ giải quyết phần **how to add activex**. Aspose.Words cung cấp lớp `Forms2OleControl` cho các đối tượng ActiveX. Ở đây chúng ta sẽ tạo một nút lệnh và cấu hình các thuộc tính của nó, bao gồm yêu cầu **set button size**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Mẹo chuyên nghiệp:** Kích thước được đo bằng điểm (1 point = 1/72 inch). Điều chỉnh các giá trị để phù hợp với bố cục của bạn; đối với một nút thanh công cụ điển hình, 120 × 30 hoạt động tốt.

---

## Bước 3: Chèn Nút Lệnh – Cốt lõi của **Insert Command Button**

Với điều khiển đã sẵn sàng, chúng ta bây giờ **insert command button** vào tài liệu tại vị trí hiện tại của builder. Bạn có thể di chuyển builder đến bất kỳ đâu (ví dụ, sau một đoạn) trước khi gọi phương thức này.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Nếu bạn cần **how to insert button** tại một bookmark cụ thể, chỉ cần di chuyển builder trước:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Điều gì xảy ra phía sau?** Aspose.Words ghi các luồng đối tượng OLE cần thiết vào gói .docx, vì vậy Word có thể hiển thị nút mà không cần macro bổ sung.

---

## Bước 4: Lưu Tài liệu – Hoàn thành chu kỳ **Create Word Document**

Bước cuối cùng rất đơn giản: lưu tệp vào đĩa. Điều này hoàn thành vòng quay của **create word document**, nhúng ActiveX và lưu lại.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Mở tệp kết quả trong Microsoft Word (chỉ Windows). Bạn sẽ thấy một nút có thể nhấn mang nhãn “Click Me”. Khi nhấn, nó sẽ kích hoạt hành động mặc định cho CommandButton—không có gì xảy ra trừ khi bạn gắn mã VBA, nhưng điều khiển này hoàn toàn hoạt động.

> **Kết quả mong đợi:** Một tệp .docx với một trang duy nhất, một nút được căn giữa tại điểm chèn, kích thước 120 × 30 pt, nhãn “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Văn bản thay thế hình ảnh:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## Bước 5: Các Trường hợp Đặc biệt, Bảo mật và Thực hành Tốt

### Giới hạn Nền tảng
- Các điều khiển ActiveX chỉ chạy trên phiên bản Word cho Windows. Nếu người dùng của bạn bao gồm macOS hoặc Word Online, nút sẽ hiển thị dưới dạng hình ảnh tĩnh.
- Một số môi trường doanh nghiệp vô hiệu hoá ActiveX vì lý do bảo mật; bạn có thể cần ký tài liệu hoặc thông báo cho người dùng bật nội dung.

### Tương tác VBA (Tùy chọn)
Nếu bạn muốn nút thực thi macro, bạn sẽ phải thêm dự án VBA vào tài liệu sau khi lưu. Aspose.Words không tự động tạo mã VBA, nhưng bạn có thể sử dụng API `Document.VbaProject` để chèn nó.

### Xung đột Tên
Luôn đặt mỗi điều khiển một `Name` duy nhất. Việc sử dụng lại cùng một tên có thể gây lỗi thời gian chạy khi Word cố gắng giải quyết điều khiển.

### Mẹo Hiệu suất
Khi chèn nhiều điều khiển, hãy tái sử dụng một thể hiện `DocumentBuilder` duy nhất và tránh gọi `doc.Save` trong vòng lặp. Hãy thực hiện chèn hàng loạt và lưu một lần duy nhất ở cuối.

---

## Ví dụ Hoạt động Đầy đủ

Kết hợp tất cả lại, đây là một chương trình hoàn chỉnh, sẵn sàng sao chép‑dán:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Chạy chương trình, mở tệp đã lưu, và bạn sẽ thấy nút đúng tại vị trí mà builder đã đặt.

---

## Kết luận

Chúng tôi vừa **created word document** từ đầu, học **how to add activex** bằng cách cấu hình một `Forms2OleControl`, nắm vững các thuộc tính **set button size**, và trình bày cách đúng để **insert command button** và **how to insert button** ở bất kỳ vị trí nào trong tệp.  

Từ một mẫu mã duy nhất, bạn giờ đã có nền tảng vững chắc cho việc tự động hoá Word phong phú hơn—cho dù bạn đang xây dựng mẫu với các biểu mẫu tương tác, tạo hợp đồng yêu cầu người dùng xác nhận, hoặc chỉ đơn giản là thêm một vài điều khiển tiện lợi vào báo cáo.

### Tiếp theo là gì?

- **Style the button** – thay đổi phông chữ, màu sắc, hoặc thêm nền ảnh.  
- **Attach VBA macros** – làm cho nút thực hiện các phép tính hoặc khởi chạy chương trình bên ngoài.  
- **Combine with other controls** – hộp kiểm, danh sách, hoặc thậm chí các bảng tính Excel nhúng.  

Hãy thoải mái thử nghiệm, và nếu gặp khó khăn, hãy để lại bình luận bên dưới. Chúc lập trình vui vẻ, và tận hưởng việc tự động hoá Word với Aspose.Words!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao phủ các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Tạo Nhóm Hình dạng trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Chèn Hình ảnh Inline trong Tài liệu Word bằng Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}