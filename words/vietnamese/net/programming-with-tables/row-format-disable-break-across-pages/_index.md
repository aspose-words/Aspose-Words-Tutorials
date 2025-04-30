---
"description": "Tìm hiểu cách tắt ngắt hàng giữa các trang trong tài liệu Word bằng Aspose.Words cho .NET để duy trì khả năng đọc và định dạng của bảng."
"linktitle": "Định dạng hàng vô hiệu hóa ngắt trang"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Định dạng hàng vô hiệu hóa ngắt trang"
"url": "/vi/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng hàng vô hiệu hóa ngắt trang

## Giới thiệu

Khi làm việc với các bảng trong tài liệu Word, bạn có thể muốn đảm bảo rằng các hàng không bị ngắt giữa các trang, điều này có thể rất cần thiết để duy trì khả năng đọc và định dạng của tài liệu. Aspose.Words for .NET cung cấp một cách dễ dàng để vô hiệu hóa ngắt hàng giữa các trang.

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình vô hiệu hóa ngắt hàng giữa các trang trong tài liệu Word bằng Aspose.Words cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đáp ứng các điều kiện tiên quyết sau:
- Đã cài đặt thư viện Aspose.Words cho .NET.
- Một tài liệu Word có bảng trải dài trên nhiều trang.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Bước 1: Tải tài liệu

Tải tài liệu có chứa bảng trải dài trên nhiều trang.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Bước 2: Truy cập Bảng

Truy cập bảng đầu tiên trong tài liệu. Điều này giả định rằng bảng bạn muốn sửa đổi là bảng đầu tiên trong tài liệu.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Bước 3: Vô hiệu hóa việc ngắt trang cho tất cả các hàng

Lặp qua từng hàng trong bảng và thiết lập `AllowBreakAcrossPages` tài sản để `false`. Điều này đảm bảo các hàng sẽ không bị ngắt giữa các trang.

```csharp
// Vô hiệu hóa việc ngắt trang cho tất cả các hàng trong bảng.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Bước 4: Lưu tài liệu

Lưu tài liệu đã sửa đổi vào thư mục bạn chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã trình bày cách vô hiệu hóa ngắt hàng giữa các trang trong tài liệu Word bằng Aspose.Words cho .NET. Bằng cách làm theo các bước nêu trên, bạn có thể đảm bảo rằng các hàng trong bảng của mình vẫn nguyên vẹn và không bị chia thành các trang, duy trì khả năng đọc và định dạng của tài liệu.

## Câu hỏi thường gặp

### Tôi có thể tắt ngắt hàng trên các trang cho một hàng cụ thể thay vì tất cả các hàng không?  
Có, bạn có thể vô hiệu hóa ngắt hàng cho các hàng cụ thể bằng cách truy cập vào hàng mong muốn và thiết lập hàng đó. `AllowBreakAcrossPages` tài sản để `false`.

### Phương pháp này có hiệu quả với các bảng có ô được hợp nhất không?  
Có, phương pháp này áp dụng cho các bảng có ô được hợp nhất. Thuộc tính `AllowBreakAcrossPages` áp dụng cho toàn bộ hàng, bất kể có hợp nhất ô hay không.

### Phương pháp này có hiệu quả nếu bảng được lồng bên trong một bảng khác không?  
Có, bạn có thể truy cập và sửa đổi các bảng lồng nhau theo cùng một cách. Đảm bảo bạn tham chiếu đúng bảng lồng nhau theo chỉ mục hoặc các thuộc tính khác của nó.

### Làm thế nào để kiểm tra xem một hàng có được phép ngắt trang hay không?  
Bạn có thể kiểm tra xem một hàng có cho phép ngắt trang hay không bằng cách truy cập `AllowBreakAcrossPages` tài sản của `RowFormat` và kiểm tra giá trị của nó.

### Có cách nào để áp dụng cài đặt này cho tất cả các bảng trong tài liệu không?  
Có, bạn có thể lặp qua tất cả các bảng trong tài liệu và áp dụng cài đặt này cho từng bảng.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}