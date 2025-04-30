---
"description": "Tìm hiểu cách thêm tiền tố tên lớp CSS khi lưu tài liệu Word dưới dạng HTML bằng Aspose.Words cho .NET. Bao gồm hướng dẫn từng bước, đoạn mã và câu hỏi thường gặp."
"linktitle": "Thêm tiền tố tên lớp Css"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Thêm tiền tố tên lớp Css"
"url": "/vi/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm tiền tố tên lớp Css

## Giới thiệu

Chào mừng! Nếu bạn đang đắm chìm vào thế giới của Aspose.Words for .NET, bạn sẽ được thưởng thức. Hôm nay, chúng ta sẽ khám phá cách thêm tiền tố tên lớp CSS khi lưu tài liệu Word dưới dạng HTML bằng Aspose.Words for .NET. Tính năng này cực kỳ tiện dụng khi bạn muốn tránh xung đột tên lớp trong các tệp HTML của mình.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

- Aspose.Words cho .NET: Nếu bạn chưa cài đặt nó, [tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Visual Studio hoặc bất kỳ IDE C# nào khác.
- Một tài liệu Word: Chúng tôi sẽ sử dụng một tài liệu có tên `Rendering.docx`. Đặt nó vào thư mục dự án của bạn.

## Nhập không gian tên

Đầu tiên, hãy đảm bảo bạn đã nhập các không gian tên cần thiết vào dự án C# của mình. Thêm những không gian tên này vào đầu tệp mã của bạn:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Bây giờ, chúng ta hãy cùng xem hướng dẫn từng bước nhé!

## Bước 1: Thiết lập dự án của bạn

Trước khi chúng ta có thể bắt đầu thêm tiền tố tên lớp CSS, hãy thiết lập dự án của mình.

### Bước 1.1: Tạo một dự án mới

Khởi động Visual Studio của bạn và tạo một dự án Console App mới. Đặt tên cho nó là một cái gì đó hấp dẫn như `AsposeCssPrefixExample`.

### Bước 1.2: Thêm Aspose.Words cho .NET

Nếu bạn chưa thêm Aspose.Words cho .NET vào dự án của bạn thông qua NuGet. Chỉ cần mở NuGet Package Manager Console và chạy:

```bash
Install-Package Aspose.Words
```

Tuyệt! Bây giờ, chúng ta đã sẵn sàng để bắt đầu viết mã.

## Bước 2: Tải tài liệu của bạn

Điều đầu tiên chúng ta cần làm là tải tài liệu Word mà chúng ta muốn chuyển đổi sang HTML.

### Bước 2.1: Xác định Đường dẫn Tài liệu

Thiết lập đường dẫn đến thư mục tài liệu của bạn. Đối với hướng dẫn này, chúng ta hãy giả sử tài liệu của bạn nằm trong một thư mục có tên `Documents` trong thư mục dự án của bạn.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Bước 2.2: Tải Tài liệu

Bây giờ, hãy tải tài liệu bằng Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Bước 3: Cấu hình tùy chọn lưu HTML

Tiếp theo, chúng ta cần cấu hình tùy chọn lưu HTML để bao gồm tiền tố tên lớp CSS.

### Bước 3.1: Tạo tùy chọn lưu HTML

Khởi tạo `HtmlSaveOptions` đối tượng và đặt kiểu bảng định dạng CSS thành `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Bước 3.2: Đặt tiền tố tên lớp CSS

Bây giờ, chúng ta hãy thiết lập `CssClassNamePrefix` thuộc tính thành tiền tố mong muốn của bạn. Đối với ví dụ này, chúng tôi sẽ sử dụng `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Bước 4: Lưu tài liệu dưới dạng HTML

Cuối cùng, hãy lưu tài liệu dưới dạng tệp HTML với các tùy chọn đã cấu hình.


Chỉ định đường dẫn tệp HTML đầu ra và lưu tài liệu.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Bước 5: Xác minh đầu ra

Sau khi chạy dự án của bạn, hãy điều hướng đến `Documents` thư mục. Bạn sẽ tìm thấy một tập tin HTML có tên `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`. Mở tệp này trong trình soạn thảo văn bản hoặc trình duyệt để xác minh rằng các lớp CSS có tiền tố `pfx_`.

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn đã thêm thành công tiền tố tên lớp CSS vào đầu ra HTML của mình bằng Aspose.Words cho .NET. Tính năng đơn giản nhưng mạnh mẽ này có thể giúp bạn duy trì các kiểu sạch và không xung đột trong tài liệu HTML của mình.

## Câu hỏi thường gặp

### Tôi có thể sử dụng tiền tố khác nhau cho mỗi thao tác lưu không?
Có, bạn có thể tùy chỉnh tiền tố mỗi lần bạn lưu tài liệu bằng cách thay đổi `CssClassNamePrefix` tài sản.

### Phương pháp này có hỗ trợ CSS nội tuyến không?
Các `CssClassNamePrefix` thuộc tính này hoạt động với CSS bên ngoài. Đối với CSS nội tuyến, bạn sẽ cần một cách tiếp cận khác.

### Làm thế nào tôi có thể thêm các tùy chọn lưu HTML khác?
Bạn có thể cấu hình các thuộc tính khác nhau của `HtmlSaveOptions` để tùy chỉnh đầu ra HTML của bạn. Kiểm tra [tài liệu](https://reference.aspose.com/words/net/) để biết thêm chi tiết.

### Có thể lưu HTML vào luồng không?
Chắc chắn rồi! Bạn có thể lưu tài liệu vào một luồng bằng cách truyền đối tượng luồng đến `Save` phương pháp.

### Tôi có thể nhận được hỗ trợ như thế nào nếu gặp vấn đề?
Bạn có thể nhận được sự hỗ trợ từ [Diễn đàn Aspose](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}