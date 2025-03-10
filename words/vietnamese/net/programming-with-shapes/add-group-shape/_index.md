---
title: Thêm hình dạng nhóm
linktitle: Thêm hình dạng nhóm
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thêm hình dạng nhóm vào tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn toàn diện, từng bước này.
weight: 10
url: /vi/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm hình dạng nhóm

## Giới thiệu

Việc tạo các tài liệu phức tạp với các thành phần trực quan phong phú đôi khi có thể là một nhiệm vụ khó khăn, đặc biệt là khi xử lý các hình dạng nhóm. Nhưng đừng lo lắng! Aspose.Words for .NET đơn giản hóa quy trình này, giúp việc này trở nên dễ dàng như ăn bánh. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn các bước để thêm các hình dạng nhóm vào tài liệu Word của bạn. Sẵn sàng để bắt đầu chưa? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1.  Aspose.Words cho .NET: Bạn có thể tải xuống từ[Trang phát hành Aspose](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Visual Studio hoặc bất kỳ IDE nào khác tương thích với .NET.
3. Hiểu biết cơ bản về C#: Có kinh nghiệm lập trình C# là một lợi thế.

## Nhập không gian tên

Để bắt đầu, chúng ta cần nhập các không gian tên cần thiết vào dự án của mình. Các không gian tên này cung cấp quyền truy cập vào các lớp và phương thức cần thiết để thao tác các tài liệu Word với Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Bước 1: Khởi tạo Tài liệu

Trước tiên, hãy khởi tạo một tài liệu Word mới. Hãy nghĩ về việc này như việc tạo một khung vẽ trống nơi chúng ta sẽ thêm các hình dạng nhóm của mình.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Đây,`EnsureMinimum()` thêm một tập hợp tối thiểu các nút cần thiết cho tài liệu.

## Bước 2: Tạo đối tượng GroupShape

 Tiếp theo, chúng ta cần tạo một`GroupShape`đối tượng. Đối tượng này sẽ đóng vai trò là nơi chứa các hình dạng khác, cho phép chúng ta nhóm chúng lại với nhau.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Bước 3: Thêm Hình dạng vào GroupShape

 Bây giờ, chúng ta hãy thêm các hình dạng riêng lẻ vào`GroupShape` container. Chúng ta sẽ bắt đầu với hình dạng đường viền nhấn mạnh và sau đó thêm hình dạng nút hành động.

### Thêm Hình dạng Đường viền Nhấn mạnh

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Đoạn mã này tạo ra một hình dạng đường viền nhấn mạnh có chiều rộng và chiều cao là 100 đơn vị và thêm nó vào`GroupShape`.

### Thêm hình dạng nút hành động

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Ở đây, chúng ta tạo một hình dạng nút hành động, định vị nó và thêm nó vào`GroupShape`.

## Bước 4: Xác định kích thước GroupShape

 Để đảm bảo các hình dạng của chúng ta phù hợp với nhóm, chúng ta cần thiết lập các kích thước của`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Điều này xác định chiều rộng và chiều cao của`GroupShape` là 200 đơn vị và thiết lập kích thước tọa độ cho phù hợp.

## Bước 5: Chèn GroupShape vào Tài liệu

 Bây giờ, chúng ta hãy chèn`GroupShape` vào tài liệu bằng cách sử dụng`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` cung cấp một cách dễ dàng để thêm các nút, bao gồm cả hình dạng, vào tài liệu.

## Bước 6: Lưu tài liệu

Cuối cùng, lưu tài liệu vào thư mục bạn chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Và thế là xong! Tài liệu với các hình dạng nhóm của bạn đã sẵn sàng.

## Phần kết luận

Việc thêm hình nhóm vào tài liệu Word của bạn không nhất thiết phải là một quá trình phức tạp. Với Aspose.Words for .NET, bạn có thể tạo và thao tác hình dạng dễ dàng, giúp tài liệu của bạn hấp dẫn và hữu dụng hơn về mặt trực quan. Thực hiện theo các bước được nêu trong hướng dẫn này và bạn sẽ trở thành chuyên gia ngay thôi!

## Câu hỏi thường gặp

### Tôi có thể thêm nhiều hơn hai hình dạng vào một GroupShape không?
 Có, bạn có thể thêm nhiều hình dạng tùy theo nhu cầu của bạn.`GroupShape` . Chỉ cần sử dụng`AppendChild` phương pháp cho từng hình dạng.

### Có thể định dạng các hình dạng trong GroupShape không?
 Chắc chắn rồi! Mỗi hình dạng có thể được tạo kiểu riêng bằng cách sử dụng các thuộc tính có sẵn trong`Shape` lớp học.

### Làm thế nào để định vị GroupShape trong tài liệu?
 Bạn có thể định vị`GroupShape` bằng cách thiết lập nó`Left` Và`Top` của cải.

### Tôi có thể thêm văn bản vào các hình dạng trong GroupShape không?
 Có, bạn có thể thêm văn bản vào hình dạng bằng cách sử dụng`AppendChild` phương pháp để thêm một`Paragraph` chứa đựng`Run` các nút có văn bản.

### Có thể nhóm các hình dạng một cách linh hoạt dựa trên thông tin đầu vào của người dùng không?
Có, bạn có thể tạo và nhóm các hình dạng một cách linh hoạt dựa trên thông tin đầu vào của người dùng bằng cách điều chỉnh các thuộc tính và phương pháp cho phù hợp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
