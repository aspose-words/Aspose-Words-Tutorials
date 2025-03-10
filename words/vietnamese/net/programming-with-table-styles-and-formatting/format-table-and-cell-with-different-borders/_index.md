---
title: Định dạng bảng và ô có đường viền khác nhau
linktitle: Định dạng bảng và ô có đường viền khác nhau
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách định dạng bảng và ô với các đường viền khác nhau bằng Aspose.Words cho .NET. Cải thiện tài liệu Word của bạn với các kiểu bảng tùy chỉnh và tô bóng ô.
weight: 10
url: /vi/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng bảng và ô có đường viền khác nhau

## Giới thiệu

Bạn đã bao giờ thử làm cho tài liệu Word của mình trông chuyên nghiệp hơn bằng cách tùy chỉnh đường viền của bảng và ô chưa? Nếu chưa, bạn sẽ được thưởng thức một món quà! Hướng dẫn này sẽ hướng dẫn bạn quy trình định dạng bảng và ô với các đường viền khác nhau bằng Aspose.Words cho .NET. Hãy tưởng tượng bạn có khả năng thay đổi giao diện của bảng chỉ bằng một vài dòng mã. Bạn có tò mò không? Hãy cùng tìm hiểu và khám phá cách bạn có thể dễ dàng thực hiện điều này.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:
- Hiểu biết cơ bản về lập trình C#.
- Đã cài đặt Visual Studio trên máy tính của bạn.
-  Aspose.Words cho thư viện .NET. Nếu bạn chưa cài đặt, bạn có thể tải xuống[đây](https://releases.aspose.com/words/net/).
-  Giấy phép Aspose hợp lệ. Bạn có thể nhận được bản dùng thử miễn phí hoặc giấy phép tạm thời từ[đây](https://purchase.aspose.com/temporary-license/).

## Nhập không gian tên

Để làm việc với Aspose.Words cho .NET, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Thêm các chỉ thị sau vào đầu tệp mã của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Bước 1: Khởi tạo Document và DocumentBuilder

Đầu tiên, bạn cần tạo một tài liệu mới và khởi tạo DocumentBuilder, giúp xây dựng nội dung tài liệu. 

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 2: Bắt đầu tạo bảng

Tiếp theo, sử dụng DocumentBuilder để bắt đầu tạo bảng và chèn ô đầu tiên.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Bước 3: Thiết lập đường viền bảng

Đặt đường viền cho toàn bộ bảng. Bước này đảm bảo rằng tất cả các ô trong bảng đều có kiểu đường viền nhất quán trừ khi có chỉ định khác.

```csharp
// Đặt đường viền cho toàn bộ bảng.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Bước 4: Áp dụng Cell Shading

Áp dụng đổ bóng cho các ô để làm cho chúng khác biệt về mặt thị giác. Trong ví dụ này, chúng ta sẽ đặt màu nền của ô đầu tiên thành màu đỏ.


```csharp
// Thiết lập chế độ tô bóng cho ô này.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Bước 5: Chèn một ô khác có bóng đổ khác

Chèn ô thứ hai và áp dụng màu tô bóng khác. Điều này làm cho bảng nhiều màu sắc hơn và dễ đọc hơn.

```csharp
builder.InsertCell();
// Chỉ định một kiểu tô bóng ô khác cho ô thứ hai.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Bước 6: Xóa định dạng ô

Xóa định dạng ô từ các thao tác trước đó để đảm bảo các ô tiếp theo không kế thừa cùng kiểu.


```csharp
// Xóa định dạng ô từ các thao tác trước đó.
builder.CellFormat.ClearFormatting();
```

## Bước 7: Tùy chỉnh đường viền cho các ô cụ thể

Tùy chỉnh đường viền cho các ô cụ thể để làm nổi bật chúng. Ở đây, chúng ta sẽ thiết lập đường viền lớn hơn cho ô đầu tiên của hàng mới.

```csharp
builder.InsertCell();
// Tạo đường viền lớn hơn cho ô đầu tiên của hàng này. Điều này sẽ khác
// so với đường viền được thiết lập cho bảng.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Bước 8: Chèn ô cuối cùng

Chèn ô cuối cùng và đảm bảo định dạng của ô này đã được xóa để sử dụng kiểu mặc định của bảng.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Bước 9: Lưu tài liệu

Cuối cùng, lưu tài liệu vào thư mục đã chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Phần kết luận

Và bạn đã có nó! Bạn vừa học cách định dạng bảng và ô với các đường viền khác nhau bằng Aspose.Words cho .NET. Bằng cách tùy chỉnh đường viền bảng và tô bóng ô, bạn có thể tăng đáng kể sức hấp dẫn trực quan của tài liệu. Vì vậy, hãy tiếp tục, thử nghiệm với các kiểu khác nhau và làm cho tài liệu của bạn nổi bật!

## Câu hỏi thường gặp

### Tôi có thể sử dụng các kiểu đường viền khác nhau cho mỗi ô không?
 Có, bạn có thể thiết lập các kiểu đường viền khác nhau cho mỗi ô bằng cách sử dụng`CellFormat.Borders` tài sản.

### Làm thế nào để xóa toàn bộ đường viền khỏi bảng?
 Bạn có thể xóa tất cả các đường viền bằng cách thiết lập kiểu đường viền thành`LineStyle.None`.

### Có thể thiết lập màu đường viền khác nhau cho mỗi ô không?
 Chắc chắn rồi! Bạn có thể tùy chỉnh màu đường viền cho mỗi ô bằng cách sử dụng`CellFormat.Borders.Color` tài sản.

### Tôi có thể sử dụng hình ảnh làm hình nền điện thoại không?
Mặc dù Aspose.Words không hỗ trợ trực tiếp hình ảnh làm hình nền ô, bạn vẫn có thể chèn hình ảnh vào ô và điều chỉnh kích thước để phủ kín vùng ô đó.

### Làm thế nào để tôi có thể hợp nhất các ô trong bảng?
 Bạn có thể hợp nhất các ô bằng cách sử dụng`CellFormat.HorizontalMerge` Và`CellFormat.VerticalMerge` của cải.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
