---
title: Áp dụng đường viền phác thảo
linktitle: Áp dụng đường viền phác thảo
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách áp dụng đường viền phác thảo cho bảng trong Word bằng Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để định dạng bảng hoàn hảo.
weight: 10
url: /vi/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Áp dụng đường viền phác thảo

## Giới thiệu

Trong hướng dẫn hôm nay, chúng ta sẽ đi sâu vào thế giới thao tác tài liệu bằng Aspose.Words cho .NET. Cụ thể, chúng ta sẽ học cách áp dụng đường viền phác thảo cho bảng trong tài liệu Word. Đây là một kỹ năng tuyệt vời cần có trong bộ công cụ của bạn nếu bạn thường xuyên làm việc với chức năng tạo và định dạng tài liệu tự động. Vì vậy, hãy bắt đầu hành trình này để làm cho bảng của bạn không chỉ có chức năng mà còn hấp dẫn về mặt hình ảnh.

## Điều kiện tiên quyết

Trước khi tìm hiểu về mã, bạn cần có một số thứ sau:

1.  Aspose.Words cho .NET: Bạn cần phải cài đặt Aspose.Words cho .NET. Bạn có thể tải xuống[đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Một môi trường phát triển phù hợp như Visual Studio.
3. Kiến thức cơ bản về C#: Hiểu biết cơ bản về C# sẽ giúp bạn theo dõi hướng dẫn.

## Nhập không gian tên

Để bắt đầu, hãy đảm bảo bạn đã nhập các không gian tên cần thiết. Điều này rất quan trọng để truy cập các chức năng của Aspose.Words.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Hãy chia nhỏ quy trình thành các bước đơn giản và dễ quản lý.

## Bước 1: Tải tài liệu

Đầu tiên, chúng ta cần tải tài liệu Word có chứa bảng mà chúng ta muốn định dạng.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 Trong bước này, chúng tôi đang sử dụng`Document` lớp từ Aspose.Words để tải một tài liệu hiện có. Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế nơi tài liệu của bạn được lưu trữ.

## Bước 2: Truy cập Bảng

Tiếp theo, chúng ta cần truy cập vào bảng cụ thể mà chúng ta muốn định dạng. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 Đây,`GetChild` phương pháp lấy bảng đầu tiên trong tài liệu. Các tham số`NodeType.Table, 0, true` đảm bảo chúng ta có được loại nút chính xác.

## Bước 3: Căn chỉnh bảng

Bây giờ, hãy căn giữa bảng trên trang.

```csharp
table.Alignment = TableAlignment.Center;
```

Bước này đảm bảo rằng bảng được căn chỉnh chính giữa, tạo cho bảng vẻ chuyên nghiệp.

## Bước 4: Xóa đường viền hiện có

Trước khi áp dụng đường viền mới, chúng ta cần xóa mọi đường viền hiện có.

```csharp
table.ClearBorders();
```

Việc xóa đường viền đảm bảo đường viền mới của chúng ta được áp dụng sạch sẽ mà không làm ảnh hưởng đến bất kỳ kiểu cũ nào.

## Bước 5: Thiết lập đường viền phác thảo

Bây giờ, chúng ta hãy áp dụng đường viền màu xanh lá cây cho bảng.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 Mỗi loại đường viền (trái, phải, trên, dưới) được thiết lập riêng lẻ. Chúng tôi sử dụng`LineStyle.Single` cho một đường nét liền mạch,`1.5` cho độ rộng của đường kẻ và`Color.Green` cho màu đường viền.

## Bước 6: Áp dụng Cell Shading

Để làm cho bảng hấp dẫn hơn về mặt thị giác, hãy tô các ô bằng màu xanh lá cây nhạt.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 Đây,`SetShading` được sử dụng để áp dụng màu xanh lá cây nhạt cho các ô, làm cho bảng nổi bật.

## Bước 7: Lưu tài liệu

Cuối cùng, lưu tài liệu đã sửa đổi.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Bước này lưu tài liệu của bạn với định dạng được áp dụng. Bạn có thể mở nó để xem bảng được định dạng đẹp mắt.

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn đã áp dụng thành công đường viền phác thảo cho bảng trong tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn này bao gồm việc tải tài liệu, truy cập bảng, căn chỉnh bảng, xóa đường viền hiện có, áp dụng đường viền mới, thêm bóng ô và cuối cùng là lưu tài liệu. 

Với những kỹ năng này, bạn có thể cải thiện cách trình bày trực quan của bảng biểu, giúp tài liệu của bạn chuyên nghiệp và hấp dẫn hơn. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể áp dụng các kiểu khác nhau cho mỗi đường viền của bảng không?  
 Có, bạn có thể áp dụng các kiểu và màu khác nhau cho mỗi đường viền bằng cách điều chỉnh các thông số trong`SetBorder` phương pháp.

### Làm thế nào để thay đổi độ rộng của đường viền?  
 Bạn có thể thay đổi chiều rộng bằng cách sửa đổi tham số thứ ba trong`SetBorder` phương pháp. Ví dụ,`1.5` đặt chiều rộng là 1,5 điểm.

### Có thể áp dụng tô bóng cho từng ô riêng lẻ không?  
 Có, bạn có thể áp dụng đổ bóng cho từng ô bằng cách truy cập vào từng ô và sử dụng`SetShading` phương pháp.

### Tôi có thể sử dụng màu khác cho đường viền và bóng đổ không?  
 Chắc chắn rồi! Bạn có thể sử dụng bất kỳ màu nào có sẵn trong`System.Drawing.Color` lớp học.

### Làm thế nào để căn giữa bảng theo chiều ngang?  
 Các`table.Alignment = TableAlignment.Center;` dòng trong mã sẽ căn giữa bảng theo chiều ngang trên trang.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
