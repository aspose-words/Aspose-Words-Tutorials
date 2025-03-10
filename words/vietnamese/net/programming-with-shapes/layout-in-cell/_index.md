---
title: Bố trí trong ô
linktitle: Bố trí trong ô
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thiết lập bố cục trong ô bằng Aspose.Words cho .NET với hướng dẫn toàn diện này. Hoàn hảo cho các nhà phát triển muốn tùy chỉnh tài liệu Word.
weight: 10
url: /vi/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bố trí trong ô

## Giới thiệu

Nếu bạn từng muốn tinh chỉnh bố cục của các ô trong bảng trong tài liệu Word theo chương trình, bạn đã đến đúng nơi rồi. Hôm nay, chúng ta sẽ tìm hiểu cách thiết lập bố cục trong ô bằng Aspose.Words cho .NET. Chúng ta sẽ hướng dẫn một ví dụ thực tế, chia nhỏ từng bước để bạn có thể dễ dàng theo dõi.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có mọi thứ cần thiết:

1.  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words cho .NET. Nếu chưa, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Bạn sẽ cần một môi trường phát triển được thiết lập bằng .NET. Visual Studio là lựa chọn tuyệt vời nếu bạn đang tìm kiếm các đề xuất.
3. Kiến thức cơ bản về C#: Mặc dù tôi sẽ giải thích từng bước, nhưng hiểu biết cơ bản về C# sẽ giúp bạn theo dõi dễ dàng hơn.
4.  Thư mục tài liệu: Chuẩn bị đường dẫn thư mục nơi bạn sẽ lưu tài liệu của mình. Chúng tôi sẽ gọi đây là`YOUR DOCUMENT DIRECTORY`.

## Nhập không gian tên

Để bắt đầu, hãy đảm bảo bạn đang nhập các không gian tên cần thiết vào dự án của mình:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Hãy chia nhỏ quy trình thành các bước dễ quản lý hơn.

## Bước 1: Tạo một tài liệu mới

 Đầu tiên, chúng ta sẽ tạo một tài liệu Word mới và khởi tạo một`DocumentBuilder` đối tượng giúp chúng ta xây dựng nội dung.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 2: Bắt đầu một bảng và thiết lập định dạng hàng

Chúng ta sẽ bắt đầu xây dựng một bảng và chỉ định chiều cao và quy tắc chiều cao cho các hàng.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Bước 3: Chèn ô và điền nội dung

Tiếp theo, chúng ta lặp để chèn các ô vào bảng. Cứ mỗi 7 ô, chúng ta sẽ kết thúc hàng để tạo một hàng mới.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Bước 4: Thêm Hình mờ

 Bây giờ, chúng ta hãy thêm hình mờ vào tài liệu của mình. Chúng ta sẽ tạo một`Shape` đối tượng và thiết lập thuộc tính của nó.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Hiển thị hình dạng bên ngoài ô của bảng nếu nó sẽ được đặt vào trong ô.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Bước 5: Tùy chỉnh giao diện hình mờ

Chúng ta sẽ tùy chỉnh thêm giao diện của hình mờ bằng cách thiết lập màu sắc và thuộc tính văn bản của nó.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Bước 6: Chèn hình mờ vào tài liệu

Chúng ta sẽ tìm đoạn chạy cuối cùng trong tài liệu và chèn hình mờ vào vị trí đó.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Bước 7: Tối ưu hóa tài liệu cho Word 2010

Để đảm bảo khả năng tương thích, chúng tôi sẽ tối ưu hóa tài liệu cho Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Bước 8: Lưu tài liệu

Cuối cùng, chúng ta sẽ lưu tài liệu vào thư mục đã chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Phần kết luận

Và bạn đã có nó! Bạn đã tạo thành công một tài liệu Word với bố cục bảng tùy chỉnh và thêm hình mờ bằng Aspose.Words cho .NET. Hướng dẫn này nhằm mục đích cung cấp hướng dẫn từng bước rõ ràng để giúp bạn hiểu từng phần của quy trình. Với những kỹ năng này, giờ đây bạn có thể tạo các tài liệu Word tinh vi và tùy chỉnh hơn theo chương trình.

## Câu hỏi thường gặp

### Tôi có thể sử dụng phông chữ khác cho văn bản hình mờ không?
 Có, bạn có thể thay đổi phông chữ bằng cách thiết lập`watermark.TextPath.FontFamily` thuộc tính cho phông chữ bạn mong muốn.

### Làm thế nào để điều chỉnh vị trí của hình mờ?
 Bạn có thể sửa đổi`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , Và`VerticalAlignment` thuộc tính để điều chỉnh vị trí của hình mờ.

### Có thể sử dụng hình ảnh thay vì văn bản để làm hình mờ không?
 Chắc chắn rồi! Bạn có thể tạo ra một`Shape` với loại`ShapeType.Image` và thiết lập hình ảnh của nó bằng cách sử dụng`ImageData.SetImage` phương pháp.

### Tôi có thể tạo bảng với chiều cao hàng khác nhau không?
Có, bạn có thể thiết lập chiều cao khác nhau cho mỗi hàng bằng cách thay đổi`RowFormat.Height` thuộc tính trước khi chèn ô vào hàng đó.

### Làm thế nào để xóa hình mờ khỏi tài liệu?
 Bạn có thể xóa hình mờ bằng cách định vị nó trong bộ sưu tập hình dạng của tài liệu và gọi`Remove` phương pháp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
