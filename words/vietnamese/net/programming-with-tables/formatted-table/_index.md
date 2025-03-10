---
title: Bảng được định dạng
linktitle: Bảng được định dạng
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách tạo và định dạng bảng trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước chi tiết này.
weight: 10
url: /vi/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bảng được định dạng

## Giới thiệu

Việc tạo và định dạng bảng trong tài liệu Word theo chương trình có vẻ là một nhiệm vụ khó khăn, nhưng với Aspose.Words for .NET, nó trở nên đơn giản và dễ quản lý. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn cách tạo bảng được định dạng trong tài liệu Word bằng Aspose.Words for .NET. Chúng tôi sẽ đề cập đến mọi thứ từ thiết lập môi trường của bạn đến lưu tài liệu của bạn với bảng được định dạng đẹp mắt.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

1. Aspose.Words cho Thư viện .NET: Tải xuống từ[đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Một IDE như Visual Studio.
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy của mình.

## Nhập không gian tên

Trước khi viết mã thực tế, bạn cần nhập các không gian tên cần thiết:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

Đầu tiên, bạn cần xác định đường dẫn nơi tài liệu của bạn sẽ được lưu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế mà bạn muốn lưu tài liệu.

## Bước 2: Khởi tạo Document và DocumentBuilder

Bây giờ, hãy khởi tạo một tài liệu mới và một đối tượng DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Các`DocumentBuilder` là lớp trợ giúp giúp đơn giản hóa quá trình xây dựng tài liệu.

## Bước 3: Bắt đầu bảng

 Tiếp theo, bắt đầu tạo bảng bằng cách sử dụng`StartTable` phương pháp.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Cần phải chèn một ô để bắt đầu bảng.

## Bước 4: Áp dụng định dạng toàn bảng

Bạn có thể áp dụng định dạng ảnh hưởng đến toàn bộ bảng. Ví dụ, thiết lập thụt lề trái:

```csharp
table.LeftIndent = 20.0;
```

## Bước 5: Định dạng hàng tiêu đề

Đặt chiều cao, căn chỉnh và các thuộc tính khác cho hàng tiêu đề.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Ở bước này, chúng ta làm nổi bật hàng tiêu đề bằng cách thiết lập màu nền, kích thước phông chữ và căn chỉnh.

## Bước 6: Chèn thêm các ô tiêu đề

Chèn thêm ô cho hàng tiêu đề:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Bước 7: Định dạng các hàng nội dung

Sau khi thiết lập tiêu đề, hãy định dạng phần thân của bảng:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Bước 8: Chèn hàng thân

Chèn các hàng nội dung có nội dung:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Lặp lại cho các hàng tiếp theo:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Bước 9: Lưu tài liệu

Cuối cùng, lưu tài liệu vào thư mục đã chỉ định:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Thao tác này sẽ tạo và lưu một tài liệu Word có bảng đã định dạng.

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn có thể tạo một bảng được định dạng tốt trong tài liệu Word bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này giúp bạn dễ dàng thao tác theo chương trình trên tài liệu Word, giúp bạn tiết kiệm thời gian và công sức.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ để tạo, chỉnh sửa và chuyển đổi tài liệu Word theo cách lập trình.

### Tôi có thể sử dụng màu khác nhau cho các hàng khác nhau không?
Có, bạn có thể áp dụng định dạng khác nhau, bao gồm cả màu sắc, cho các hàng hoặc ô khác nhau.

### Aspose.Words cho .NET có miễn phí không?
 Aspose.Words cho .NET là một thư viện trả phí, nhưng bạn có thể nhận được[dùng thử miễn phí](https://releases.aspose.com/).

### Làm thế nào để tôi nhận được hỗ trợ cho Aspose.Words dành cho .NET?
 Bạn có thể nhận được sự hỗ trợ từ[Diễn đàn cộng đồng Aspose](https://forum.aspose.com/c/words/8).

### Tôi có thể tạo các loại tài liệu khác bằng Aspose.Words cho .NET không?
Có, Aspose.Words for .NET hỗ trợ nhiều định dạng tài liệu khác nhau, bao gồm PDF, HTML và TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
