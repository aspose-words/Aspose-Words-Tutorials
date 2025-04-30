---
"description": "Tìm hiểu cách tạo dấu trang trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn chi tiết từng bước này. Hoàn hảo cho việc điều hướng và sắp xếp tài liệu."
"linktitle": "Tạo Bookmark Trong Tài Liệu Word"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Tạo Bookmark Trong Tài Liệu Word"
"url": "/vi/net/programming-with-bookmarks/create-bookmark/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Bookmark Trong Tài Liệu Word

## Giới thiệu

Tạo dấu trang trong tài liệu Word có thể là một bước ngoặt, đặc biệt là khi bạn muốn điều hướng qua các tài liệu lớn một cách dễ dàng. Hôm nay, chúng ta sẽ hướng dẫn quy trình tạo dấu trang bằng Aspose.Words cho .NET. Hướng dẫn này sẽ hướng dẫn bạn từng bước, đảm bảo bạn hiểu từng phần của quy trình. Vậy, hãy cùng bắt đầu ngay nhé!

## Điều kiện tiên quyết

Trước khi bắt đầu, bạn cần có những thứ sau:

1. Aspose.Words cho Thư viện .NET: Tải xuống và cài đặt từ [đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Visual Studio hoặc bất kỳ môi trường phát triển .NET nào khác.
3. Kiến thức cơ bản về C#: Hiểu biết về các khái niệm lập trình C# cơ bản.

## Nhập không gian tên

Để làm việc với Aspose.Words cho .NET, bạn cần nhập các không gian tên cần thiết:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Thiết lập Document và DocumentBuilder

Khởi tạo tài liệu

Đầu tiên, chúng ta cần tạo một tài liệu mới và khởi tạo `DocumentBuilder`. Đây là điểm khởi đầu để thêm nội dung và dấu trang vào tài liệu của bạn.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Giải thích: `Document` đối tượng là bức tranh của bạn. `DocumentBuilder` giống như chiếc bút của bạn, cho phép bạn viết nội dung và tạo dấu trang trong tài liệu.

## Bước 2: Tạo Dấu trang Chính

Bắt đầu và kết thúc dấu trang chính

Để tạo dấu trang, bạn cần chỉ định điểm bắt đầu và điểm kết thúc. Ở đây, chúng ta sẽ tạo một dấu trang có tên là "Dấu trang của tôi".

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

Giải thích: `StartBookmark` phương pháp đánh dấu sự bắt đầu của dấu trang và `Writeln` thêm văn bản vào dấu trang.

## Bước 3: Tạo một dấu trang lồng nhau

Thêm dấu trang lồng nhau vào dấu trang chính

Bạn có thể lồng dấu trang vào các dấu trang khác. Ở đây, chúng tôi thêm "Dấu trang lồng nhau" vào "Dấu trang của tôi".

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

Giải thích: Việc lồng các dấu trang cho phép tổ chức nội dung có cấu trúc và phân cấp hơn. `EndBookmark` phương pháp này đóng dấu trang hiện tại.

## Bước 4: Thêm văn bản bên ngoài dấu trang lồng nhau

Tiếp tục thêm nội dung

Sau khi tạo dấu trang lồng nhau, chúng ta có thể tiếp tục thêm nội dung vào dấu trang chính.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

Giải thích: Điều này đảm bảo rằng dấu trang chính bao gồm cả dấu trang lồng nhau và văn bản bổ sung.

## Bước 5: Cấu hình tùy chọn lưu PDF

Thiết lập tùy chọn lưu PDF cho dấu trang

Khi lưu tài liệu dưới dạng PDF, chúng ta có thể cấu hình các tùy chọn để bao gồm dấu trang.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

Giải thích: `PdfSaveOptions` lớp cho phép bạn chỉ định cách tài liệu sẽ được lưu dưới dạng PDF. `BookmarksOutlineLevels` Thuộc tính này xác định thứ bậc của các dấu trang trong PDF.

## Bước 6: Lưu tài liệu

Lưu tài liệu dưới dạng PDF

Cuối cùng, lưu tài liệu với các tùy chọn đã chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

Giải thích: `Save` phương pháp lưu tài liệu theo định dạng và vị trí đã chỉ định. PDF bây giờ sẽ bao gồm các dấu trang chúng ta đã tạo.

## Phần kết luận

Tạo dấu trang trong tài liệu Word bằng Aspose.Words cho .NET rất đơn giản và cực kỳ hữu ích cho việc điều hướng và sắp xếp tài liệu. Cho dù bạn đang tạo báo cáo, tạo sách điện tử hay quản lý tài liệu lớn, dấu trang giúp cuộc sống dễ dàng hơn. Làm theo các bước được nêu trong hướng dẫn này và bạn sẽ có một tệp PDF được đánh dấu sẵn sàng trong thời gian ngắn.

## Câu hỏi thường gặp

### Tôi có thể tạo nhiều dấu trang ở nhiều cấp độ khác nhau không?

Hoàn toàn được! Bạn có thể tạo bao nhiêu dấu trang tùy thích và xác định cấp độ phân cấp của chúng khi lưu tài liệu dưới dạng PDF.

### Làm thế nào để cập nhật văn bản của dấu trang?

Bạn có thể điều hướng đến dấu trang bằng cách sử dụng `DocumentBuilder.MoveToBookmark` và sau đó cập nhật văn bản.

### Có thể xóa dấu trang không?

Có, bạn có thể xóa dấu trang bằng cách sử dụng `Bookmarks.Remove` phương pháp bằng cách chỉ định tên của dấu trang.

### Tôi có thể tạo dấu trang ở các định dạng khác ngoài PDF không?

Có, Aspose.Words hỗ trợ dấu trang ở nhiều định dạng khác nhau, bao gồm DOCX, HTML và EPUB.

### Làm sao để đảm bảo dấu trang xuất hiện chính xác trong PDF?

Hãy chắc chắn để xác định `BookmarksOutlineLevels` đúng cách trong `PdfSaveOptions`. Điều này đảm bảo các dấu trang được bao gồm trong phần phác thảo của PDF.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}