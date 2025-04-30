---
"description": "Tìm hiểu cách chèn bảng trực tiếp vào tài liệu Word bằng Aspose.Words cho .NET. Làm theo hướng dẫn chi tiết từng bước của chúng tôi để hợp lý hóa việc tạo tài liệu của bạn."
"linktitle": "Chèn bảng trực tiếp"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Chèn bảng trực tiếp"
"url": "/vi/net/programming-with-tables/insert-table-directly/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn bảng trực tiếp

## Giới thiệu
Việc tạo bảng theo chương trình có thể khá khó khăn, đặc biệt là khi xử lý các cấu trúc tài liệu phức tạp. Nhưng đừng lo, chúng tôi ở đây để giúp bạn! Trong hướng dẫn này, chúng tôi sẽ hướng dẫn các bước chèn bảng trực tiếp vào tài liệu Word bằng Aspose.Words cho .NET. Cho dù bạn là một nhà phát triển dày dạn kinh nghiệm hay chỉ mới bắt đầu, hướng dẫn này sẽ giúp bạn dễ dàng nắm vững quy trình.

## Điều kiện tiên quyết

Trước khi đi sâu vào mã, hãy đảm bảo bạn có mọi thứ cần thiết để bắt đầu. Sau đây là danh sách kiểm tra nhanh:

1. Aspose.Words cho Thư viện .NET: Đảm bảo bạn đã tải xuống và cài đặt thư viện Aspose.Words cho .NET. Bạn có thể lấy nó từ [trang tải xuống](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Môi trường phát triển như Visual Studio.
3. Kiến thức cơ bản về C#: Hiểu những kiến thức cơ bản về lập trình C#.
4. Thư mục tài liệu: Đường dẫn thư mục nơi bạn sẽ lưu tài liệu của mình.

Với những điều kiện tiên quyết này, bạn đã sẵn sàng để bắt đầu viết mã!

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Các không gian tên này sẽ cung cấp cho chúng ta các lớp và phương thức cần thiết để làm việc với các tài liệu Word.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Bây giờ chúng ta đã có không gian tên tại chỗ, hãy chuyển sang phần thú vị—tạo và chèn bảng trực tiếp vào tài liệu Word.

## Bước 1: Thiết lập tài liệu

Chúng ta hãy bắt đầu bằng cách thiết lập một tài liệu Word mới. Đây là nơi bảng của chúng ta sẽ được chèn vào.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Mã này khởi tạo một tài liệu Word mới. Bạn sẽ cần phải thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục tài liệu của bạn.

## Bước 2: Tạo đối tượng bảng

Tiếp theo, chúng ta tạo đối tượng bảng. Đây là nơi chúng ta sẽ xác định cấu trúc của bảng.

```csharp
// Chúng ta bắt đầu bằng cách tạo đối tượng bảng. Lưu ý rằng chúng ta phải truyền đối tượng tài liệu
// đến hàm tạo của mỗi nút. Điều này là do mọi nút chúng ta tạo ra phải thuộc về
// vào một số tài liệu.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

Ở đây, chúng ta tạo một bảng mới và thêm nó vào phần thân của phần đầu tiên trong tài liệu.

## Bước 3: Thêm Hàng và Ô

Bảng được tạo thành từ các hàng và ô. Chúng ta hãy thêm các thành phần này từng bước một.

### Thêm một hàng

```csharp
// Ở đây chúng ta có thể gọi EnsureMinimum để tạo các hàng và ô cho chúng ta. Phương pháp này được sử dụng
// để đảm bảo rằng nút được chỉ định là hợp lệ. Trong trường hợp này, một bảng hợp lệ phải có ít nhất một Hàng và một ô.
// Thay vào đó, chúng ta sẽ tự xử lý việc tạo hàng và bảng.
// Đây sẽ là cách tốt nhất để thực hiện điều này nếu chúng ta đang tạo một bảng bên trong một thuật toán.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

Đoạn mã này tạo một hàng mới và thêm nó vào bảng của chúng ta.

### Thêm ô vào hàng

Bây giờ, hãy thêm một số ô vào hàng của chúng ta. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

Trong đoạn mã này, chúng ta tạo một ô, đặt màu nền của ô thành màu xanh nhạt và xác định chiều rộng của ô. Sau đó, chúng ta thêm một đoạn văn và một dòng vào ô để chứa văn bản của chúng ta.

## Bước 4: Nhân bản tế bào

Để đẩy nhanh quá trình thêm tế bào, chúng ta có thể nhân bản các tế bào hiện có.

```csharp
// Sau đó, chúng ta sẽ lặp lại quy trình này cho các ô và hàng khác trong bảng.
// Chúng ta cũng có thể đẩy nhanh tiến độ bằng cách nhân bản các ô và hàng hiện có.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

Mã này sao chép ô hiện có và thêm nó vào hàng. Sau đó, chúng ta thêm một đoạn văn và một chuỗi vào ô mới.

## Bước 5: Áp dụng Cài đặt Tự động Điều chỉnh

Cuối cùng, hãy áp dụng cài đặt tự động điều chỉnh cho bảng để đảm bảo các cột có chiều rộng cố định.

```csharp
// Bây giờ chúng ta có thể áp dụng bất kỳ cài đặt tự động điều chỉnh nào.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## Bước 6: Lưu tài liệu

Sau khi bảng đã được thiết lập đầy đủ, đã đến lúc lưu tài liệu.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

Mã này lưu tài liệu có chèn bảng.

## Phần kết luận

Xin chúc mừng! Bạn đã chèn thành công một bảng trực tiếp vào tài liệu Word bằng Aspose.Words cho .NET. Quá trình này có thể được sử dụng để tạo các bảng phức tạp theo chương trình, giúp các tác vụ tự động hóa tài liệu của bạn dễ dàng hơn nhiều. Cho dù bạn đang tạo báo cáo, hóa đơn hay bất kỳ loại tài liệu nào khác, hiểu cách thao tác bảng là một kỹ năng quan trọng.

## Câu hỏi thường gặp

### Làm thế nào tôi có thể tải xuống Aspose.Words cho .NET?
Bạn có thể tải xuống Aspose.Words cho .NET từ [trang tải xuống](https://releases.aspose.com/words/net/).

### Tôi có thể dùng thử Aspose.Words cho .NET trước khi mua không?
Có, bạn có thể yêu cầu một [dùng thử miễn phí](https://releases.aspose.com/) để đánh giá thư viện trước khi mua.

### Làm thế nào để mua Aspose.Words cho .NET?
Bạn có thể mua Aspose.Words cho .NET từ [trang mua hàng](https://purchase.aspose.com/buy).

### Tôi có thể tìm tài liệu về Aspose.Words cho .NET ở đâu?
Tài liệu có sẵn [đây](https://reference.aspose.com/words/net/).

### Tôi phải làm sao nếu cần hỗ trợ khi sử dụng Aspose.Words cho .NET?
Để được hỗ trợ, bạn có thể truy cập [Diễn đàn Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}