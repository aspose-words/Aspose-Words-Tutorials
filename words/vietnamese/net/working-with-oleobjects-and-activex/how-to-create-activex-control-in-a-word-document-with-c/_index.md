---
category: general
date: 2026-09-14
description: Tạo điều khiển ActiveX trong tài liệu Word bằng C#. Tìm hiểu cách chèn
  ActiveX, thêm nút tương tác và tạo file .docx một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: vi
lastmod: 2026-09-14
og_description: Tạo điều khiển ActiveX trong tài liệu Word bằng C#. Tham khảo ví dụ
  đầy đủ này để chèn ActiveX, thêm nút tương tác và lưu tệp.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Tạo điều khiển ActiveX trong Word bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Cách tạo điều khiển ActiveX trong tài liệu Word bằng C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo điều khiển ActiveX trong tài liệu Word bằng C#

Nếu bạn cần **tạo điều khiển ActiveX** trong một tệp Microsoft Word, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ thấy chính xác cách chèn một ActiveX CommandButton, đặt các thuộc tính của nó, và lưu tệp `.docx` kết quả chỉ bằng mã C#.

Thêm một nút tương tác vào tài liệu Word là một yêu cầu phổ biến khi bạn muốn người dùng cuối kích hoạt macro hoặc logic tùy chỉnh trực tiếp từ giao diện người dùng của tài liệu. Ví dụ dưới đây minh họa **cách chèn ActiveX** mà không cần dựa vào công cụ bên thứ ba, và cũng bao gồm **cách tạo tài liệu Word** một cách lập trình.

Khi kết thúc hướng dẫn này, bạn sẽ có thể **tạo nút bằng mã**, tùy chỉnh chú thích của nó, và tạo ra một tệp Word di động giữ nguyên điều khiển ActiveX.

## Yêu cầu trước

- .NET 6.0 hoặc phiên bản mới hơn (thư viện Aspose.Words cho .NET hoạt động với .NET Core và .NET Framework)
- Tham chiếu tới gói NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Kiến thức cơ bản về C# và lập trình hướng đối tượng

## Bước 1: Thiết lập dự án và nhập không gian tên

Tạo một dự án console mới (hoặc tích hợp mã vào bất kỳ ứng dụng C# hiện có nào). Nhập các không gian tên cần thiết để trình biên dịch có thể tìm thấy các lớp xử lý Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Tại sao bước này quan trọng** – API `Aspose.Words` cung cấp các lớp `Document`, `DocumentBuilder` và `Forms2OleControl` cho phép bạn thao tác các tệp Word ở mức độ đối tượng. Nếu không có các tham chiếu này, phần còn lại của mã sẽ không biên dịch được.

## Bước 2: Tạo một tài liệu Word mới và một DocumentBuilder

Đối tượng `Document` đại diện cho toàn bộ gói `.docx`, trong khi `DocumentBuilder` cung cấp một API mượt mà để chèn nội dung.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Giải thích** – Tạo một `Document` mới cung cấp cho bạn một nền trắng sạch sẽ. Con trỏ của builder bắt đầu ở đầu phần đầu tiên, sẵn sàng cho việc chèn tiếp theo.

## Bước 3: Chèn ActiveX CommandButton

Sử dụng `InsertForms2OleControl` để đặt một điều khiển ActiveX tại vị trí cụ thể. Phương thức này yêu cầu loại điều khiển và một `RectangleF` xác định tọa độ X/Y và kích thước (đơn vị point).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Tại sao cách này hoạt động** – `OleControlType.CommandButton` báo cho API tạo một CommandButton Windows tiêu chuẩn. Hình chữ nhật định vị nút so với góc trên‑trái của trang, cho phép bạn **thêm nút tương tác** chính xác ở vị trí mong muốn.

## Bước 4: Cấu hình các thuộc tính của nút

Bây giờ đặt văn bản hiển thị của nút (`Caption`) và tên nội bộ của nó (`Name`). Những thuộc tính này là những gì người dùng nhìn thấy và mã VBA có thể tham chiếu sau này.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Mẹo thực tế** – `Name` phải là duy nhất trong tài liệu; nếu không, macro VBA có thể tham chiếu sai điều khiển.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tệp ra đĩa. Điều khiển ActiveX được lưu trong gói Word, vì vậy tệp đã lưu sẽ giữ đầy đủ chức năng khi mở trong Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Kết quả** – Mở `CommandButton.docx` trong Word sẽ hiển thị một CommandButton có thể nhấp được với nhãn “Click Me”. Điều khiển này có thể được liên kết với một macro thông qua giao diện Word (`Developer → Design Mode → Properties`).

## Danh sách mã nguồn đầy đủ

Kết hợp tất cả các bước lại với nhau tạo ra một chương trình độc lập, bạn có thể sao chép, dán và chạy.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Kết quả mong đợi

Chạy chương trình sẽ in ra một dòng xác nhận:

```
Document saved to C:\Temp\CommandButton.docx
```

Khi bạn mở tệp đã tạo trong Microsoft Word, bạn sẽ thấy một **CommandButton** được đặt tại tọa độ đã chỉ định. Nhấp vào nút trong chế độ thiết kế sẽ làm nổi bật nó; trong chế độ chạy, nó hoạt động như bất kỳ nút ActiveX tiêu chuẩn nào.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Điều chỉnh |
|----------|------------|
| **Loại điều khiển khác** | Thay thế `OleControlType.CommandButton` bằng `OleControlType.CheckBox`, `OleControlType.OptionButton`, v.v. |
| **Nhiều nút** | Gọi `InsertForms2OleControl` nhiều lần, cập nhật tọa độ `RectangleF` cho mỗi nút mới. |
| **Kích thước động** | Tính kích thước hình chữ nhật dựa trên kích thước trang (`builder.PageSetup.PageWidth`). |
| **Lưu vào stream** | Sử dụng `document.Save(stream, SaveFormat.Docx)` khi bạn cần trả về tệp từ một API web. |
| **Định dạng Word 97‑2003** | Thay đổi định dạng lưu thành `SaveFormat.Doc` để tạo tệp `.doc` vẫn nhúng điều khiển ActiveX. |

> **Mẹo chuyên nghiệp:** Luôn kiểm tra tài liệu được tạo trên phiên bản Word mục tiêu, vì các phiên bản cũ hơn có thể áp đặt cài đặt bảo mật khiến điều khiển ActiveX bị tắt mặc định.

## Câu hỏi thường gặp

**Điều này có hoạt động với .NET Core không?**  
Có. Thư viện Aspose.Words là đa nền tảng và hoàn toàn tương thích với .NET Core và .NET 5/6+.

**Tôi có thể gán macro cho nút bằng lập trình không?**  
API không nhúng mã VBA trực tiếp. Sau khi tài liệu được tạo, mở nó trong Word, bật tab Developer, và ghi hoặc viết một macro tham chiếu tới `btnClick`.

**Nếu nút không hiển thị thì sao?**  
Kiểm tra xem tab `Developer` đã được bật trong Word chưa và tài liệu không được mở ở **Protected View**. Cũng hãy xác nhận rằng tọa độ hình chữ nhật nằm trong lề trang.

## Kết luận

Bây giờ bạn đã biết cách **tạo điều khiển ActiveX** trong tệp Word bằng C#. Hướng dẫn đã bao gồm **cách chèn ActiveX**, minh họa **thêm nút tương tác**, trình bày **cách tạo tài liệu Word** từ đầu, và chỉ ra **cách tạo nút bằng mã** mà vẫn tồn tại sau khi lưu.

Từ đây bạn có thể khám phá các loại ActiveX khác, kết nối nút với macro VBA, hoặc nhúng logic vào một dịch vụ tạo tài liệu lớn hơn. Thử nghiệm với các kích thước, vị trí và thuộc tính điều khiển khác nhau để phù hợp với trải nghiệm người dùng mà bạn cần.

---

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Tài liệu Word Mới](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Tạo Dự Án VBA trong Tài liệu Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Tạo và Định dạng Tài liệu Word trong Aspose.Words cho .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}