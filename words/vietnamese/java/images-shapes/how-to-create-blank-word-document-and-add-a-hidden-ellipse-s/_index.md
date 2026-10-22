---
category: general
date: 2026-09-21
description: Tạo tài liệu Word trống có một hình ellipse ẩn bằng C#. Tìm hiểu cách
  ẩn hình trong Word và tạo hình ẩn một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: vi
lastmod: 2026-09-21
og_description: Tạo tài liệu Word trống với một hình elip ẩn bằng C#. Hướng dẫn này
  chỉ cách ẩn hình trong Word và xây dựng các hình ẩn một cách lập trình.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Tạo tài liệu Word trống có hình ellipse ẩn trong C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Cách tạo tài liệu Word trống và thêm hình ellipse ẩn trong C#
url: /vi/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và thêm hình ellipse ẩn trong C#

Nếu bạn cần **tạo tài liệu Word trống** có chứa một đồ họa vô hình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Khi kết thúc tutorial, bạn sẽ có một tệp .docx trông như rỗng nhưng thực tế lưu trữ một hình ellipse đã được ẩn khỏi bố cục.

Chúng ta sẽ sử dụng Aspose.Words for .NET để xây dựng tài liệu, chèn một ellipse, ẩn nó và lưu tệp. Các bước cũng bao gồm **cách tạo đối tượng ellipse**, cách **ẩn shape trong Word** đúng cách, và cách **tạo shape ẩn** bằng mã hoạt động với bất kỳ dự án .NET nào.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 SDK hoặc phiên bản mới hơn được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ trình soạn thảo C# nào)  
* Giấy phép Aspose.Words for .NET hoặc bản dùng thử miễn phí  
* Kiến thức cơ bản về cú pháp C#  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Tạo tài liệu Word trống với Aspose.Words

Bước đầu tiên là tạo một tệp Word rỗng. Điều này cung cấp cho chúng ta một canvas sạch sẽ để sau này chèn các đồ họa ẩn.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Tại sao chúng ta bắt đầu với tài liệu trống** – Bắt đầu từ một tệp rỗng đảm bảo không có nội dung không mong muốn can thiệp vào shape ẩn. Nó cũng giữ kích thước tệp tối thiểu, hữu ích khi tài liệu sau này được dùng làm mẫu.

## Cách tạo ellipse trong tài liệu trống

Tiếp theo chúng ta cần một `DocumentBuilder` để thêm nội dung. Builder cho phép chúng ta đặt shape chính xác ở vị trí mong muốn.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Giải thích** – `ShapeType.Ellipse` báo cho Aspose.Words vẽ một hình tròn‑giống. Chiều rộng và chiều cao được đo bằng điểm (1 pt ≈ 1/72 inch). Bạn có thể điều chỉnh các giá trị này để phù hợp với nhu cầu thiết kế.

## Ẩn shape trong Word để không hiển thị trên bố cục

Một shape bị ẩn vẫn tồn tại trong XML của tài liệu, điều này có thể hữu ích cho metadata, định dạng có điều kiện, hoặc các sửa đổi chương trình sau này. Để ẩn nó, chúng ta đặt thuộc tính `Hidden` thành `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Tại sao phải ẩn shape** – Các shape ẩn bị bộ xử lý bố cục bỏ qua, vì vậy trang trông hoàn toàn trống. Tuy nhiên, dữ liệu shape vẫn tồn tại, có thể dùng để lưu các dấu hiệu, bookmark, hoặc XML tùy chỉnh mà các quy trình downstream có thể đọc.

## Lưu tài liệu với shape ẩn

Cuối cùng chúng ta ghi tệp ra đĩa. Tệp `.docx` đã lưu sẽ mở trong Microsoft Word mà không có nội dung hiển thị, nhưng ellipse ẩn vẫn còn.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Xác minh** – Mở tệp đã tạo trong Word, sau đó nhấn `Alt+F9` để chuyển đổi hiển thị mã trường và `Ctrl+A` → `Ctrl+Shift+F9` để xem các đối tượng ẩn. Bạn sẽ thấy ellipse trong XML của tài liệu (`word/document.xml`) nhưng không có gì trên trang.

---

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một dự án console mới. Nó bao gồm tất cả các chỉ thị `using` và phương thức `Main` để bạn có thể chạy mà không cần scaffolding thêm.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Kết quả mong đợi** – Khi chạy chương trình, console sẽ in ra đường dẫn tệp, và tệp Word tạo ra sẽ không có đối tượng hiển thị. Nếu bạn kiểm tra tài liệu bằng công cụ zip (`.docx` là một archive zip), bạn sẽ thấy phần tử `<w:pict>` mô tả ellipse bên trong `word/document.xml`.

---

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Cần thay đổi | Lý do |
|----------|--------------|-------|
| **Shape khác** | Thay `ShapeType.Ellipse` bằng `ShapeType.Rectangle`, `ShapeType.Line`, v.v. | Cho phép bạn ẩn các đồ họa khác trong cùng quy trình. |
| **Nhiều shape ẩn** | Gọi `InsertShape` nhiều lần và đặt `Hidden = true` cho mỗi shape. | Hữu ích để nhúng một bộ dấu hiệu hoặc placeholder. |
| **Hiển thị có điều kiện** | Dùng `shape.Visible = false` cùng với `shape.Hidden = true` để tăng độ an toàn. | Một số phiên bản Word cũ xử lý `Visible` khác; đặt cả hai sẽ bao phủ mọi trường hợp. |
| **Lưu vào stream** | Thay `doc.Save(path)` bằng `doc.Save(stream, SaveFormat.Docx)`. | Cho phép gửi tài liệu trực tiếp qua HTTP hoặc lưu vào cơ sở dữ liệu. |
| **Áp dụng style** | Sau khi chèn, chỉnh `ellipse.FillColor`, `ellipse.LineWeight`, … trước khi ẩn. | Style của shape được giữ trong XML, có thể hữu ích khi muốn hiện lại sau. |

**Mẹo chuyên nghiệp:** Luôn kiểm tra shape ẩn trên phiên bản Word mục tiêu (ví dụ: Word 2019, Word 365) vì đôi khi có những quirks về render khi các đối tượng ẩn tương tác với bố cục trang phức tạp.

---

## Câu hỏi thường gặp

**H: Ẩn shape có ảnh hưởng đến kích thước tài liệu không?**  
Đ: XML của shape chỉ thêm vài trăm byte, hầu như không đáng kể đối với hầu hết các trường hợp. Tệp vẫn gần như có cùng kích thước với tài liệu thực sự rỗng.

**H: Tôi có thể hiện lại shape sau này bằng mã không?**  
Đ: Có. Tải tài liệu, tìm shape (`doc.GetChildNodes(NodeType.Shape, true)`), và đặt `shape.Hidden = false`.

**H: Shape ẩn có xuất hiện khi in không?**  
Đ: Không. Các đối tượng ẩn bị loại bỏ khỏi bố cục in, vì vậy trang in vẫn trống.

**H: Phương pháp này chỉ tương thích với Office Open XML (OOXML) phải không?**  
Đ: Thuộc tính `Hidden` là một phần của chuẩn OOXML, vì vậy bất kỳ trình xử lý Word nào thực thi đầy đủ OOXML (Word, LibreOffice, Google Docs) sẽ tôn trọng cờ ẩn này.

---

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word trống**, **tạo ellipse**, **ẩn shape trong Word**, và **tạo shape ẩn** bằng Aspose.Words for .NET. Tutorial đã bao phủ toàn bộ vòng đời — từ khởi tạo tệp rỗng, chèn, ẩn và lưu shape — cùng các bước xác minh và các biến thể thường gặp.

Tiếp theo, bạn có thể khám phá:

* Thêm textbox ẩn để lưu metadata (kỹ thuật `hide shape in word` áp dụng cho text)  
* Sử dụng custom XML parts để lưu dữ liệu có cấu trúc bên cạnh các shape ẩn  
* Chuyển đổi tài liệu có shape ẩn sang PDF trong khi giữ nguyên các phần tử ẩn  

Hãy thử nghiệm với các shape và cài đặt hiển thị khác nhau để xem nội dung ẩn có thể phục vụ như một kho dữ liệu nhẹ trong các file Word như thế nào.

Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ và giải thích chi tiết từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}