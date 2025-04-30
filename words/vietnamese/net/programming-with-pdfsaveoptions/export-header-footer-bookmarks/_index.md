---
"description": "Tìm hiểu cách xuất dấu trang đầu trang và chân trang từ tài liệu Word sang PDF bằng Aspose.Words cho .NET với hướng dẫn từng bước của chúng tôi."
"linktitle": "Xuất Tiêu đề, Chân trang, Dấu trang của Tài liệu Word sang Tài liệu PDF"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Xuất Tiêu đề, Chân trang, Dấu trang của Tài liệu Word sang Tài liệu PDF"
"url": "/vi/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Xuất Tiêu đề, Chân trang, Dấu trang của Tài liệu Word sang Tài liệu PDF

## Giới thiệu

Chuyển đổi tài liệu Word sang PDF là một tác vụ phổ biến, đặc biệt là khi bạn muốn chia sẻ hoặc lưu trữ tài liệu trong khi vẫn giữ nguyên định dạng của chúng. Đôi khi, các tài liệu này chứa các dấu trang quan trọng trong phần đầu trang và chân trang. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình xuất các dấu trang này từ tài liệu Word sang PDF bằng Aspose.Words cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

- Aspose.Words cho .NET: Bạn cần phải cài đặt Aspose.Words cho .NET. Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Thiết lập môi trường phát triển của bạn. Bạn có thể sử dụng Visual Studio hoặc bất kỳ IDE tương thích .NET nào khác.
- Kiến thức cơ bản về C#: Cần phải quen thuộc với lập trình C# để theo dõi các ví dụ về mã.

## Nhập không gian tên

Trước tiên, bạn cần nhập các không gian tên cần thiết vào dự án C# của mình. Thêm các dòng này vào đầu tệp mã của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Chúng ta hãy chia nhỏ quy trình thành các bước dễ thực hiện.

## Bước 1: Khởi tạo Tài liệu

Bước đầu tiên là tải tài liệu Word của bạn. Sau đây là cách bạn có thể thực hiện:

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

Ở bước này, bạn chỉ cần chỉ định đường dẫn đến thư mục tài liệu và tải tài liệu Word.

## Bước 2: Cấu hình tùy chọn lưu PDF

Tiếp theo, bạn cần cấu hình các tùy chọn lưu PDF để đảm bảo các dấu trang trong phần đầu trang và chân trang được xuất chính xác.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Ở đây, chúng tôi đang thiết lập `PdfSaveOptions`. Các `DefaultBookmarksOutlineLevel` thuộc tính thiết lập mức phác thảo cho dấu trang và `HeaderFooterBookmarksExportMode` Thuộc tính này đảm bảo rằng chỉ xuất hiện lần đầu tiên của dấu trang trong phần đầu trang và chân trang.

## Bước 3: Lưu tài liệu dưới dạng PDF

Cuối cùng, lưu tài liệu của bạn dưới dạng PDF bằng các tùy chọn đã cấu hình.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Ở bước này, bạn sẽ lưu tài liệu vào đường dẫn đã chỉ định với các tùy chọn bạn đã cấu hình.

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn có thể dễ dàng xuất dấu trang từ tiêu đề và chân trang của tài liệu Word sang PDF bằng Aspose.Words for .NET. Phương pháp này đảm bảo rằng các công cụ hỗ trợ điều hướng quan trọng trong tài liệu của bạn được lưu giữ ở định dạng PDF, giúp người đọc dễ dàng điều hướng qua tài liệu của bạn hơn.

## Câu hỏi thường gặp

### Tôi có thể xuất tất cả dấu trang từ tài liệu Word sang PDF không?

Vâng, bạn có thể. Trong `PdfSaveOptions`, bạn có thể điều chỉnh cài đặt để bao gồm tất cả các dấu trang nếu cần.

### Tôi phải làm sao nếu muốn xuất cả dấu trang từ nội dung tài liệu?

Bạn có thể cấu hình `OutlTRONGeOptions` in `PdfSaveOptions` để bao gồm các dấu trang từ nội dung tài liệu.

### Có thể tùy chỉnh mức độ đánh dấu trong PDF không?

Chắc chắn rồi! Bạn có thể tùy chỉnh `DefaultBookmarksOutlineLevel` thuộc tính để thiết lập các mức phác thảo khác nhau cho dấu trang của bạn.

### Tôi phải xử lý tài liệu không có dấu trang như thế nào?

Nếu tài liệu của bạn không có dấu trang, PDF sẽ được tạo mà không có bất kỳ phác thảo dấu trang nào. Đảm bảo tài liệu của bạn có dấu trang nếu bạn cần chúng trong PDF.

### Tôi có thể sử dụng phương pháp này cho các loại tài liệu khác như DOCX hoặc RTF không?

Có, Aspose.Words for .NET hỗ trợ nhiều loại tài liệu khác nhau, bao gồm DOCX, RTF và nhiều loại khác.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}