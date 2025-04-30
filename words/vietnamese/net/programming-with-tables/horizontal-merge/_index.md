---
"description": "Tìm hiểu cách gộp ô theo chiều ngang trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn chi tiết từng bước này."
"linktitle": "Hợp nhất theo chiều ngang"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Hợp nhất theo chiều ngang"
"url": "/vi/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hợp nhất theo chiều ngang

## Giới thiệu

Xin chào! Bạn đã sẵn sàng khám phá thế giới của Aspose.Words cho .NET chưa? Hôm nay, chúng ta sẽ giải quyết một tính năng cực kỳ hữu ích: hợp nhất theo chiều ngang trong các bảng. Nghe có vẻ hơi kỹ thuật, nhưng đừng lo, tôi sẽ hỗ trợ bạn. Đến cuối hướng dẫn này, bạn sẽ trở thành chuyên gia trong việc hợp nhất các ô trong tài liệu Word theo chương trình. Vậy, hãy xắn tay áo lên và bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi đi sâu vào vấn đề chính, bạn cần chuẩn bị một số điều sau:

1. Aspose.Words cho Thư viện .NET: Nếu bạn chưa có, hãy tải xuống thư viện Aspose.Words cho .NET. Bạn có thể lấy nó [đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Đảm bảo bạn đã thiết lập môi trường phát triển phù hợp, chẳng hạn như Visual Studio.
3. Kiến thức cơ bản về C#: Hiểu biết cơ bản về lập trình C# sẽ rất có lợi.

Khi đã sắp xếp xong những thứ này, bạn đã sẵn sàng rồi!

## Nhập không gian tên

Trước khi đi sâu vào mã, hãy đảm bảo rằng chúng ta đã nhập các không gian tên cần thiết. Trong dự án C# của bạn, hãy đảm bảo bao gồm:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Được rồi, chúng ta hãy phân tích quy trình hợp nhất các ô trong bảng theo chiều ngang trong tài liệu Word bằng Aspose.Words cho .NET.

## Bước 1: Thiết lập tài liệu của bạn

Trước tiên, chúng ta cần tạo một tài liệu Word mới và khởi tạo `DocumentBuilder`:

```csharp
// Đường dẫn đến thư mục tài liệu của bạn 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Đoạn mã này thiết lập một tài liệu mới và chuẩn bị `DocumentBuilder` để hành động.

## Bước 2: Chèn ô đầu tiên

Tiếp theo, chúng ta bắt đầu bằng cách chèn ô đầu tiên và đánh dấu nó để hợp nhất theo chiều ngang:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Ở đây, chúng ta chèn một ô mới và thiết lập nó `HorizontalMerge` tài sản để `CellMerge.First`, cho biết rằng ô này là điểm bắt đầu của một chuỗi ô đã hợp nhất.

## Bước 3: Chèn ô đã hợp nhất

Bây giờ, chúng ta chèn ô sẽ được hợp nhất với ô trước đó:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Ô này được thiết lập để hợp nhất với ô trước đó bằng cách sử dụng `CellMerge.Previous`. Lưu ý cách chúng ta kết thúc hàng với `builder.EndRow()`.

## Bước 4: Chèn các ô chưa được hợp nhất

Để minh họa sự khác biệt, chúng ta hãy chèn một vài ô chưa được hợp nhất:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Ở đây, chúng tôi chèn hai ô không có sự hợp nhất theo chiều ngang. Điều này cho thấy cách các ô hoạt động khi chúng không phải là một phần của chuỗi được hợp nhất.

## Bước 5: Hoàn thiện bảng

Cuối cùng, chúng ta kết thúc bảng và lưu tài liệu:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Đoạn mã này hoàn thiện bảng và lưu tài liệu vào thư mục đã chỉ định.

## Phần kết luận

Và bạn đã có nó! Bạn vừa thành thạo nghệ thuật hợp nhất các ô theo chiều ngang trong tài liệu Word bằng Aspose.Words cho .NET. Bằng cách làm theo các bước này, bạn có thể dễ dàng tạo các cấu trúc bảng phức tạp. Tiếp tục thử nghiệm và khám phá các khả năng của Aspose.Words để làm cho tài liệu của bạn trở nên năng động và linh hoạt như bạn cần. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, chỉnh sửa và thao tác các tài liệu Word theo chương trình trong các ứng dụng .NET.

### Tôi có thể nhập các ô theo chiều dọc bằng Aspose.Words cho .NET không?
Có, bạn cũng có thể hợp nhất các ô theo chiều dọc bằng cách sử dụng `CellFormat.VerticalMerge` tài sản.

### Aspose.Words cho .NET có miễn phí sử dụng không?
Aspose.Words cho .NET cung cấp bản dùng thử miễn phí, nhưng để có đầy đủ chức năng, bạn sẽ cần mua giấy phép. Bạn có thể nhận được giấy phép tạm thời [đây](https://purchase.aspose.com/temporary-license/).

### Làm thế nào tôi có thể tìm hiểu thêm về Aspose.Words cho .NET?
Bạn có thể khám phá tài liệu chi tiết [đây](https://reference.aspose.com/words/net/).

### Tôi có thể nhận hỗ trợ cho Aspose.Words dành cho .NET ở đâu?
Đối với bất kỳ thắc mắc hoặc vấn đề nào, bạn có thể truy cập diễn đàn hỗ trợ Aspose [đây](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}