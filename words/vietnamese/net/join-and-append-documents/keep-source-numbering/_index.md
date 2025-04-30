---
"description": "Tìm hiểu cách nhập tài liệu trong khi vẫn giữ nguyên định dạng bằng Aspose.Words cho .NET. Hướng dẫn từng bước có ví dụ về mã."
"linktitle": "Giữ lại số nguồn"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Giữ lại số nguồn"
"url": "/vi/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Giữ lại số nguồn

## Giới thiệu

Khi làm việc với Aspose.Words cho .NET, việc nhập tài liệu từ nguồn này sang nguồn khác trong khi vẫn giữ nguyên định dạng có thể được xử lý hiệu quả bằng cách sử dụng `NodeImporter` lớp. Hướng dẫn này sẽ hướng dẫn bạn thực hiện từng bước một.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Đã cài đặt Visual Studio trên máy của bạn.
- Aspose.Words cho .NET đã được cài đặt. Nếu chưa, hãy tải xuống từ [đây](https://releases.aspose.com/words/net/).
- Kiến thức cơ bản về lập trình C# và .NET.

## Nhập không gian tên

Đầu tiên, hãy bao gồm các không gian tên cần thiết trong dự án của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Bước 1: Thiết lập dự án của bạn

Bắt đầu bằng cách tạo một dự án C# mới trong Visual Studio và cài đặt Aspose.Words thông qua NuGet Package Manager.

## Bước 2: Khởi tạo tài liệu
Tạo các phiên bản của nguồn (`srcDoc`) và đích đến (`dstDoc`) tài liệu.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Bước 3: Cấu hình Tùy chọn nhập
Thiết lập tùy chọn nhập để duy trì định dạng nguồn, bao gồm cả các đoạn văn được đánh số.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Bước 4: Nhập đoạn văn
Lặp lại các đoạn văn trong tài liệu nguồn và nhập chúng vào tài liệu đích.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Bước 5: Lưu tài liệu
Lưu tài liệu đã hợp nhất vào vị trí bạn mong muốn.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Phần kết luận

Tóm lại, việc sử dụng Aspose.Words cho .NET để nhập tài liệu trong khi vẫn giữ nguyên định dạng rất đơn giản với `NodeImporter` lớp. Phương pháp này đảm bảo rằng tài liệu của bạn duy trì được cấu trúc và giao diện ban đầu một cách liền mạch.

## Câu hỏi thường gặp

### Tôi có thể nhập tài liệu có nhiều định dạng khác nhau không?
Vâng, `NodeImporter` Lớp này hỗ trợ việc nhập tài liệu với nhiều kiểu định dạng khác nhau.

### Nếu tài liệu của tôi chứa nhiều bảng và hình ảnh phức tạp thì sao?
Aspose.Words cho .NET xử lý các cấu trúc phức tạp như bảng và hình ảnh trong quá trình nhập.

### Aspose.Words có tương thích với tất cả các phiên bản .NET không?
Aspose.Words hỗ trợ các phiên bản .NET Framework và .NET Core để tích hợp liền mạch.

### Tôi có thể xử lý lỗi trong quá trình nhập tài liệu như thế nào?
Sử dụng khối try-catch để xử lý các ngoại lệ có thể xảy ra trong quá trình nhập.

### Tôi có thể tìm tài liệu chi tiết hơn về Aspose.Words cho .NET ở đâu?
Ghé thăm [tài liệu](https://reference.aspose.com/words/net/) để có hướng dẫn toàn diện và tài liệu tham khảo API.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}