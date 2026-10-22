---
category: general
date: 2026-10-07
description: Tìm hiểu cách chèn nút lệnh OLE vào tài liệu Word bằng Aspose.Words C#.
  Hướng dẫn từng bước bao gồm DocumentBuilder, các thuộc tính và lưu tệp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: vi
lastmod: 2026-10-07
og_description: Chèn nút lệnh OLE vào tài liệu Word bằng C#. Hãy làm theo hướng dẫn
  ngắn gọn này để thêm, cấu hình và lưu một CommandButton hoạt động với Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Chèn nút lệnh OLE vào Word bằng C# – hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Cách chèn nút lệnh OLE vào tài liệu Word bằng C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn nút lệnh OLE vào tài liệu Word bằng C#

Nếu bạn cần **chèn nút lệnh OLE** vào tệp Word một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác bằng Aspose.Words cho .NET. Cho dù bạn đang xây dựng báo cáo có biểu mẫu điền sẵn hoặc tự động hoá mẫu cần tương tác người dùng, các bước dưới đây sẽ cung cấp cho bạn một giải pháp hoàn chỉnh, có thể chạy được.

Bạn sẽ học cách tạo một tài liệu trống, sử dụng `DocumentBuilder` để đặt một `Forms2OleControl`, thiết lập chú thích và tên của nút, và cuối cùng lưu thành `.docx`. Không cần công cụ bên ngoài nào ngoài thư viện Aspose.Words.

## Yêu cầu trước

* .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.7+)
* Giấy phép Aspose.Words for .NET hợp lệ hoặc khóa dùng thử miễn phí
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào bạn thích)
* Kiến thức cơ bản về cú pháp C# và các khái niệm OLE trong Word

> **Mẹo:** Nếu bạn đang sử dụng bản dùng thử miễn phí, tài liệu được tạo sẽ chứa một watermark nhỏ. Phiên bản có giấy phép sẽ tự động loại bỏ nó.

## Bước 1: Cài đặt Aspose.Words

Thêm gói Aspose.Words vào dự án của bạn qua NuGet:

```bash
dotnet add package Aspose.Words
```

Gói này bao gồm các không gian tên `Aspose.Words.Drawing` và `Aspose.Words.Drawing.Ole` cần thiết cho các điều khiển OLE.

## Bước 2: Chèn nút lệnh OLE bằng DocumentBuilder

Phần cốt lõi của hướng dẫn là phương thức `InsertForms2OleControl`. Nó tạo một **Forms2 OLE CommandButton** tại một vị trí và kích thước cụ thể.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Tại sao cách này hoạt động

* `DocumentBuilder` là API chính để xây dựng tài liệu Word một cách lập trình.  
* `InsertForms2OleControl` yêu cầu Aspose.Words nhúng một **Forms2 OLE control**, đây là công nghệ biểu mẫu Word cũ hỗ trợ các nút lệnh, hộp kiểm, v.v.  
* Giá trị enum `OleControlType.CommandButton` chỉ định rằng điều khiển được chèn là một **command button** — đúng loại bạn muốn khi **chèn nút lệnh OLE**.  
* `Rectangle` xác định vị trí hiển thị. Điều chỉnh tọa độ X/Y hoặc chiều rộng/chiều cao để phù hợp với bố cục của bạn.

## Bước 3: Lưu tài liệu

Sau khi cấu hình nút, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được Aspose.Words hỗ trợ (`.docx`, `.pdf`, `.odt`, …). Trong hướng dẫn này chúng ta sẽ lưu dưới dạng tài liệu Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Khi bạn mở `CommandButton.docx` trong Microsoft Word, bạn sẽ thấy một nút có thể nhấp được với nhãn **Click Me**. Nhấn nó trong Word sẽ kích hoạt hộp thoại “Run Macro” mặc định vì nút này là một điều khiển biểu mẫu OLE; bạn có thể gắn macro hoặc mã VBA sau này nếu cần.

## Bước 4: Xác minh kết quả (đầu ra mong đợi)

Mở tệp đã tạo:

1. Nút xuất hiện ở tọa độ bạn đã chỉ định (khoảng 1.4 inch từ phía trái và trên của trang).  
2. Chú thích hiển thị **Click Me**.  
3. Thuộc tính name (`cmdSubmit`) hiển thị trong bảng **Developer → Properties** của Word, hữu ích khi bạn cần tham chiếu đến điều khiển từ VBA.

![Ví dụ chèn nút lệnh OLE trong tài liệu Word](insert-ole-button.png)

*Văn bản thay thế hình ảnh*: **Ví dụ chèn nút lệnh OLE trong tài liệu Word** (bao gồm từ khóa chính cho khả năng truy cập và SEO).

## Các trường hợp đặc biệt & Câu hỏi thường gặp

### 1. Nếu nút không xuất hiện ở vị trí tôi mong đợi thì sao?

* Word sử dụng đơn vị point, không phải pixel. Chuyển đổi pixel màn hình sang point (`points = pixels * 72 / DPI`).  
* Đảm bảo `Rectangle` không giao với lề trang; nếu không Word có thể di chuyển điều khiển.

### 2. Tôi có thể chèn nút vào tài liệu hiện có không?

Có. Tải tài liệu bằng `new Document("Existing.docx")` và sử dụng cùng quy trình `DocumentBuilder`. Chỉ cần nhớ di chuyển con trỏ của builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, v.v.) trước khi gọi `InsertForms2OleControl`.

### 3. Làm thế nào để gắn macro vào nút?

Aspose.Words không tạo mã VBA, nhưng bạn có thể nhúng macro sau khi tài liệu đã được tạo:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Điều này có hoạt động với .NET Core trên Linux không?

Điều khiển OLE là tính năng chỉ dành cho Windows vì nó dựa trên COM. Trên Linux nút sẽ được chèn, nhưng sẽ hiển thị như một hình ảnh tĩnh không có hành vi tương tác. Đối với các biểu mẫu tương tác đa nền tảng, hãy xem xét sử dụng content controls (`StructuredDocumentTag`) thay thế.

### 5. Nếu tôi cần kích thước khác hoặc nhiều nút thì sao?

Tạo các đối tượng `Rectangle` bổ sung với tọa độ duy nhất và lặp lại lời gọi `InsertForms2OleControl`. Mỗi nút có thể có `Caption` và `Name` riêng.

## Ví dụ đầy đủ hoạt động

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các chỉ thị `using` cần thiết, xử lý lỗi và chú thích.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Chạy chương trình, mở `CommandButton.docx` đã tạo, và bạn sẽ thấy nút **Click Me** sẵn sàng để tùy chỉnh thêm.

## Kết luận

Bây giờ bạn đã biết cách **chèn nút lệnh OLE** vào tài liệu Word bằng C# và Aspose.Words. Hướng dẫn đã bao gồm:

* Cài đặt gói Aspose.Words  
* Sử dụng `DocumentBuilder.InsertForms2OleControl` với `OleControlType.CommandButton`  
* Thiết lập các thuộc tính của nút (`Caption`, `Name`)  
* Lưu và xác minh đầu ra  

Từ đây bạn có thể khám phá các chủ đề liên quan như **Aspose.Words OLE control** cho hộp kiểm, hộp combo, hoặc nhúng toàn bộ bảng tính Excel. Bạn cũng có thể thử nghiệm tự động hoá **Word OLE command button** trong các mẫu lớn hơn, hoặc thay thế các điều khiển OLE bằng **content controls** hiện đại để hỗ trợ đa nền tảng tốt hơn.

Hãy tự do điều chỉnh các giá trị rectangle, thêm nhiều nút, hoặc gắn macro VBA để đáp ứng nhu cầu của ứng dụng của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}