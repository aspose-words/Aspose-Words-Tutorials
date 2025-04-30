---
"description": "Tìm hiểu cách xuất các tài nguyên như CSS và phông chữ trong khi lưu tài liệu Word dưới dạng HTML bằng Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi."
"linktitle": "Xuất khẩu tài nguyên"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Xuất khẩu tài nguyên"
"url": "/vi/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Xuất khẩu tài nguyên

## Giới thiệu

Xin chào, những người đam mê công nghệ! Nếu bạn từng thấy mình cần chuyển đổi tài liệu Word sang HTML, thì bạn đã đến đúng nơi rồi. Hôm nay, chúng ta sẽ khám phá thế giới tuyệt vời của Aspose.Words for .NET. Thư viện mạnh mẽ này giúp bạn dễ dàng làm việc với các tài liệu Word theo chương trình. Trong hướng dẫn này, chúng ta sẽ hướng dẫn các bước để xuất tài nguyên, chẳng hạn như phông chữ và CSS, khi lưu tài liệu Word dưới dạng HTML bằng Aspose.Words for .NET. Hãy thắt dây an toàn để có một chuyến đi thú vị và bổ ích!

## Điều kiện tiên quyết

Trước khi đi sâu vào mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết để bắt đầu. Sau đây là danh sách kiểm tra nhanh:

1. Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên máy của mình. Bạn có thể tải xuống từ [Trang web Visual Studio](https://visualstudio.microsoft.com/).
2. Aspose.Words cho .NET: Bạn sẽ cần thư viện Aspose.Words cho .NET. Nếu bạn chưa có, hãy tải bản dùng thử miễn phí từ [Aspose phát hành](https://releases.aspose.com/words/net/) hoặc mua nó từ [Cửa hàng Aspose](https://purchase.aspose.com/buy).
3. Kiến thức cơ bản về C#: Hiểu biết cơ bản về C# sẽ giúp bạn theo dõi các ví dụ về mã.

Bạn đã hiểu chưa? Tuyệt! Chúng ta hãy chuyển sang nhập các không gian tên cần thiết.

## Nhập không gian tên

Để sử dụng Aspose.Words cho .NET, bạn cần bao gồm các không gian tên có liên quan trong dự án của mình. Sau đây là cách thực hiện:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Các không gian tên này rất quan trọng để truy cập các lớp và phương thức Aspose.Words mà chúng ta sẽ sử dụng trong hướng dẫn này.

Chúng ta hãy cùng phân tích quy trình xuất tài nguyên khi lưu tài liệu Word dưới dạng HTML. Chúng ta sẽ thực hiện từng bước để dễ theo dõi.

## Bước 1: Thiết lập thư mục tài liệu của bạn

Trước tiên, bạn cần chỉ định đường dẫn đến thư mục tài liệu của mình. Đây là nơi tài liệu Word của bạn nằm và nơi tệp HTML sẽ được lưu.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục của bạn.

## Bước 2: Tải tài liệu Word

Tiếp theo, hãy tải tài liệu Word mà bạn muốn chuyển đổi sang HTML. Đối với hướng dẫn này, chúng tôi sẽ sử dụng một tài liệu có tên `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Dòng mã này tải tài liệu từ thư mục được chỉ định.

## Bước 3: Cấu hình tùy chọn lưu HTML

Để xuất các tài nguyên như CSS và phông chữ, bạn cần cấu hình `HtmlSaveOptions`. Bước này rất quan trọng để đảm bảo đầu ra HTML của bạn có cấu trúc tốt và bao gồm các tài nguyên cần thiết.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

Chúng ta hãy phân tích chức năng của từng tùy chọn:
- `CssStyleSheetType = CssStyleSheetType.External`: Tùy chọn này chỉ định rằng các kiểu CSS sẽ được lưu trong một bảng định kiểu bên ngoài.
- `ExportFontResources = true`: Điều này cho phép xuất các nguồn phông chữ.
- `ResourceFolder = dataDir + "Resources"`: Chỉ định thư mục cục bộ nơi tài nguyên (như phông chữ và tệp CSS) sẽ được lưu.
- `ResourceFolderAlias = "http://example.com/resources"`: Đặt bí danh cho thư mục tài nguyên, sẽ được sử dụng trong tệp HTML.

## Bước 4: Lưu tài liệu dưới dạng HTML

Với các tùy chọn lưu được cấu hình, bước cuối cùng là lưu tài liệu dưới dạng tệp HTML. Sau đây là cách thực hiện:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Dòng mã này lưu tài liệu ở định dạng HTML, cùng với các tài nguyên đã xuất.

## Phần kết luận

Và thế là xong! Bạn đã xuất tài nguyên thành công trong khi lưu tài liệu Word dưới dạng HTML bằng Aspose.Words for .NET. Với thư viện mạnh mẽ này, việc xử lý tài liệu Word theo chương trình trở nên dễ như ăn kẹo. Cho dù bạn đang làm việc trên ứng dụng web hay chỉ cần chuyển đổi tài liệu để sử dụng ngoại tuyến, Aspose.Words đều có thể giúp bạn.

## Câu hỏi thường gặp

### Tôi có thể xuất hình ảnh cùng với phông chữ và CSS không?
Có, bạn có thể! Aspose.Words cho .NET cũng hỗ trợ xuất hình ảnh. Chỉ cần đảm bảo cấu hình `HtmlSaveOptions` theo đó.

### Có cách nào để nhúng CSS thay vì sử dụng bảng định kiểu bên ngoài không?
Chắc chắn rồi. Bạn có thể thiết lập `CssStyleSheetType` ĐẾN `CssStyleSheetType.Embedded` nếu bạn thích kiểu nhúng.

### Làm thế nào để tùy chỉnh tên tệp HTML đầu ra?
Bạn có thể chỉ định bất kỳ tên tệp nào bạn thích trong `doc.Save` phương pháp. Ví dụ, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words có hỗ trợ các định dạng khác ngoài HTML không?
Có, nó hỗ trợ nhiều định dạng khác nhau bao gồm PDF, DOCX, TXT, v.v. Hãy xem [tài liệu](https://reference.aspose.com/words/net/) để biết danh sách đầy đủ.

### Tôi có thể nhận thêm hỗ trợ và tài nguyên ở đâu?
Để được trợ giúp thêm, hãy truy cập [Diễn đàn hỗ trợ Aspose.Words](https://forum.aspose.com/c/words/8). Bạn cũng có thể tìm thấy tài liệu chi tiết và ví dụ trên [Trang web Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}