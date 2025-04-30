---
"description": "Tìm hiểu cách xuất tài liệu Word sang Markdown với các bảng được căn chỉnh bằng Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để có các bảng Markdown hoàn hảo."
"linktitle": "Xuất sang Markdown với căn chỉnh nội dung bảng"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Xuất sang Markdown với căn chỉnh nội dung bảng"
"url": "/vi/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Xuất sang Markdown với căn chỉnh nội dung bảng

## Giới thiệu

Xin chào! Bạn đã bao giờ tự hỏi làm thế nào để xuất tài liệu Word của mình sang định dạng Markdown với các bảng được căn chỉnh hoàn hảo chưa? Cho dù bạn là một nhà phát triển đang làm việc trên tài liệu hay chỉ là một người yêu thích Markdown, hướng dẫn này là dành cho bạn. Chúng tôi sẽ đi sâu vào chi tiết về việc sử dụng Aspose.Words cho .NET để đạt được điều này. Sẵn sàng biến các bảng Word của bạn thành các bảng Markdown được căn chỉnh gọn gàng chưa? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi đi sâu vào mã, bạn cần chuẩn bị một số thứ sau:

1. Aspose.Words cho Thư viện .NET: Đảm bảo bạn có thư viện Aspose.Words cho .NET. Bạn có thể tải xuống từ [Trang phát hành Aspose](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển của bạn. Visual Studio là lựa chọn phổ biến cho phát triển .NET.
3. Kiến thức cơ bản về C#: Hiểu biết về C# là điều cần thiết vì chúng ta sẽ viết mã bằng ngôn ngữ này.
4. Mẫu tài liệu Word: Chuẩn bị một tài liệu Word mà bạn có thể sử dụng để thử nghiệm.

## Nhập không gian tên

Trước khi bắt đầu mã hóa, hãy nhập các không gian tên cần thiết. Chúng sẽ cho phép chúng ta truy cập vào các lớp và phương thức Aspose.Words mà chúng ta sẽ sử dụng.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Khởi tạo Document và DocumentBuilder

Trước tiên, chúng ta cần tạo một tài liệu Word mới và khởi tạo một `DocumentBuilder` đối tượng để bắt đầu xây dựng tài liệu của chúng ta.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Tạo một tài liệu mới.
Document doc = new Document();

// Khởi tạo DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 2: Chèn ô và căn chỉnh nội dung

Tiếp theo, chúng ta sẽ chèn một số ô vào tài liệu và thiết lập căn chỉnh của chúng. Điều này rất quan trọng để đảm bảo rằng bản xuất Markdown giữ nguyên căn chỉnh chính xác.

```csharp
// Chèn một ô và căn chỉnh sang phải.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Chèn một ô khác và căn chỉnh vào giữa.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Bước 3: Thiết lập Căn chỉnh Nội dung Bảng cho Xuất Markdown

Bây giờ, đã đến lúc cấu hình `MarkdownSaveOptions` để kiểm soát sự căn chỉnh của nội dung bảng trong tệp Markdown đã xuất. Chúng tôi sẽ lưu tài liệu với các thiết lập căn chỉnh khác nhau để xem nó hoạt động như thế nào.

```csharp
// Tạo đối tượng MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Lưu tài liệu với căn trái.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Đổi căn chỉnh sang phải và lưu.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Đổi căn chỉnh về giữa và lưu.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Bước 4: Sử dụng Tự động căn chỉnh nội dung bảng

Các `Auto` tùy chọn căn chỉnh lấy căn chỉnh từ đoạn văn đầu tiên trong cột bảng tương ứng. Điều này có thể hữu ích khi bạn có các căn chỉnh hỗn hợp trong một bảng duy nhất.

```csharp
// Đặt căn chỉnh thành Tự động.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Lưu tài liệu với chức năng căn chỉnh tự động.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Phần kết luận

Và bạn đã có nó! Xuất tài liệu Word sang Markdown với các bảng được căn chỉnh bằng Aspose.Words cho .NET thật dễ dàng khi bạn biết cách thực hiện. Thư viện mạnh mẽ này giúp bạn dễ dàng kiểm soát định dạng và căn chỉnh các bảng, đảm bảo rằng các tài liệu Markdown của bạn trông đúng như bạn muốn. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, chỉnh sửa, chuyển đổi và xuất tài liệu Word theo chương trình.

### Tôi có thể thiết lập các căn chỉnh khác nhau cho các cột khác nhau trong cùng một bảng không?
Có, bằng cách sử dụng `Auto` tùy chọn căn chỉnh, bạn có thể căn chỉnh khác nhau dựa trên đoạn văn đầu tiên trong mỗi cột.

### Tôi có cần giấy phép để sử dụng Aspose.Words cho .NET không?
Có, Aspose.Words cho .NET yêu cầu giấy phép để có đầy đủ chức năng. Bạn có thể nhận được [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để đánh giá.

### Có thể xuất các thành phần tài liệu khác sang Markdown bằng Aspose.Words không?
Có, Aspose.Words hỗ trợ xuất nhiều thành phần khác nhau như tiêu đề, danh sách và hình ảnh sang định dạng Markdown.

### Tôi có thể nhận được hỗ trợ ở đâu nếu gặp vấn đề?
Bạn có thể nhận được sự hỗ trợ từ [Diễn đàn hỗ trợ Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}