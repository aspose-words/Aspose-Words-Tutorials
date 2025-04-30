---
"description": "Tìm hiểu cách thêm và tùy chỉnh tiêu đề và chân trang trong tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn từng bước này đảm bảo định dạng tài liệu chuyên nghiệp."
"linktitle": "Tạo Header Footer"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Tạo Header Footer"
"url": "/vi/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Header Footer

## Giới thiệu

Thêm tiêu đề và chân trang vào tài liệu của bạn có thể nâng cao tính chuyên nghiệp và khả năng đọc của chúng. Với Aspose.Words for .NET, bạn có thể dễ dàng tạo và tùy chỉnh tiêu đề và chân trang cho tài liệu Word của mình. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước trong quy trình, đảm bảo bạn có thể triển khai các tính năng này một cách liền mạch.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

- Aspose.Words cho .NET: Tải xuống và cài đặt từ [liên kết tải xuống](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Chẳng hạn như Visual Studio, để viết và chạy mã của bạn.
- Kiến thức cơ bản về C#: Hiểu biết về C# và .NET framework.
- Tài liệu mẫu: Một tài liệu mẫu để áp dụng tiêu đề và chân trang hoặc tạo một tiêu đề và chân trang mới như trong hướng dẫn.

## Nhập không gian tên

Đầu tiên, bạn cần nhập các không gian tên cần thiết để truy cập các lớp và phương thức Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Bước 1: Xác định thư mục tài liệu

Xác định thư mục nơi tài liệu của bạn sẽ được lưu. Điều này giúp quản lý đường dẫn hiệu quả.

```csharp
// Đường dẫn đến thư mục tài liệu
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Bước 2: Tạo một tài liệu mới

Tạo một tài liệu mới và một `DocumentBuilder` để tạo điều kiện thuận lợi cho việc bổ sung nội dung.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 3: Cấu hình Thiết lập Trang

Thiết lập cài đặt trang, bao gồm cả việc trang đầu tiên có phần đầu trang/chân trang khác nhau hay không.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Bước 4: Thêm Tiêu đề vào Trang đầu tiên

Di chuyển đến phần tiêu đề của trang đầu tiên và cấu hình văn bản tiêu đề.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Bước 5: Thêm Tiêu đề chính

Di chuyển đến phần tiêu đề chính và chèn hình ảnh và văn bản.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Chèn hình ảnh vào tiêu đề
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Bước 6: Thêm Chân trang chính

Di chuyển đến phần chân trang chính và tạo bảng để định dạng nội dung chân trang.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Thêm số trang
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Bước 7: Thêm Nội dung và Ngắt trang

Di chuyển đến cuối tài liệu, thêm ngắt trang và tạo phần mới với các thiết lập trang khác nhau.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Bước 8: Sao chép Tiêu đề và Chân trang từ Phần trước

Nếu bạn muốn sử dụng lại phần đầu trang và phần chân trang từ phần trước, hãy sao chép chúng và áp dụng những sửa đổi cần thiết.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Phần kết luận

Bằng cách làm theo các bước này, bạn có thể thêm và tùy chỉnh tiêu đề và chân trang hiệu quả trong tài liệu Word của mình bằng Aspose.Words for .NET. Điều này làm tăng diện mạo và tính chuyên nghiệp của tài liệu, giúp tài liệu dễ đọc và hấp dẫn hơn.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?

Aspose.Words for .NET là thư viện cho phép các nhà phát triển tạo, chỉnh sửa và chuyển đổi các tài liệu Word theo chương trình trong các ứng dụng .NET.

### Tôi có thể thêm hình ảnh vào đầu trang hoặc chân trang không?

Có, bạn có thể dễ dàng thêm hình ảnh vào đầu trang hoặc chân trang bằng cách sử dụng `DocumentBuilder.InsertImage` phương pháp.

### Làm thế nào để thiết lập các tiêu đề và chân trang khác nhau cho trang đầu tiên?

Bạn có thể thiết lập các tiêu đề và chân trang khác nhau cho trang đầu tiên bằng cách sử dụng `DifferentFirstPageHeaderFooter` tài sản của `PageSetup` lớp học.

### Tôi có thể tìm thêm tài liệu về Aspose.Words ở đâu?

Bạn có thể tìm thấy tài liệu toàn diện về [Trang tài liệu API Aspose.Words](https://reference.aspose.com/words/net/).

### Có hỗ trợ cho Aspose.Words không?

Có, Aspose cung cấp hỗ trợ thông qua [diễn đàn hỗ trợ](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}