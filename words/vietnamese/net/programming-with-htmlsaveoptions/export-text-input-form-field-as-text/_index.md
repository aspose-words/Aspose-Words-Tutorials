---
"description": "Tìm hiểu cách xuất các trường biểu mẫu nhập văn bản dưới dạng văn bản thuần túy bằng Aspose.Words cho .NET với hướng dẫn từng bước toàn diện này."
"linktitle": "Xuất trường biểu mẫu nhập văn bản dưới dạng văn bản"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Xuất trường biểu mẫu nhập văn bản dưới dạng văn bản"
"url": "/vi/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Xuất trường biểu mẫu nhập văn bản dưới dạng văn bản

## Giới thiệu

Vậy, bạn đang đắm chìm vào thế giới của Aspose.Words cho .NET? Lựa chọn tuyệt vời! Nếu bạn đang muốn tìm hiểu cách xuất trường biểu mẫu nhập văn bản dưới dạng văn bản, bạn đã đến đúng nơi rồi. Cho dù bạn mới bắt đầu hay đang trau dồi kỹ năng, hướng dẫn này sẽ hướng dẫn bạn mọi thứ bạn cần biết. Chúng ta hãy bắt đầu nhé?

## Điều kiện tiên quyết

Trước khi đi sâu vào chi tiết, hãy đảm bảo rằng bạn có mọi thứ cần thiết để theo dõi một cách suôn sẻ:

- Aspose.Words cho .NET: Tải xuống và cài đặt phiên bản mới nhất từ [đây](https://releases.aspose.com/words/net/).
- IDE: Visual Studio hoặc bất kỳ môi trường phát triển C# nào.
- Kiến thức cơ bản về C#: Hiểu biết về cú pháp C# cơ bản và các khái niệm lập trình hướng đối tượng.
- Tài liệu: Một tài liệu Word mẫu (`Rendering.docx`) với các trường nhập văn bản.

## Nhập không gian tên

Trước tiên, bạn cần nhập các không gian tên cần thiết. Chúng giống như các khối xây dựng giúp mọi thứ hoạt động liền mạch.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Được rồi, bây giờ chúng ta đã có không gian tên sẵn sàng, hãy bắt đầu hành động thôi!

## Bước 1: Thiết lập dự án

Trước khi đi sâu vào mã, hãy đảm bảo rằng dự án của chúng ta được thiết lập chính xác.

## Tạo dự án

1. Mở Visual Studio: Bắt đầu bằng cách mở Visual Studio hoặc môi trường phát triển C# mà bạn thích.
2. Tạo một dự án mới: Điều hướng đến `File > New > Project`Lựa chọn `Console App (.NET Core)` hoặc bất kỳ loại dự án có liên quan nào khác.
3. Đặt tên cho dự án của bạn: Đặt cho dự án của bạn một cái tên có ý nghĩa, chẳng hạn như `AsposeWordsExportExample`.

## Thêm Aspose.Words

1. Quản lý các gói NuGet: Nhấp chuột phải vào dự án của bạn trong Solution Explorer và chọn `Manage NuGet Packages`.
2. Tìm kiếm Aspose.Words: Trong NuGet Package Manager, hãy tìm kiếm `Aspose.Words`.
3. Cài đặt Aspose.Words: Nhấp vào `Install` để thêm thư viện Aspose.Words vào dự án của bạn.

## Bước 2: Tải tài liệu Word

Bây giờ dự án của chúng ta đã được thiết lập, hãy tải tài liệu Word có chứa các trường biểu mẫu nhập văn bản.

1. Chỉ định thư mục tài liệu: Xác định đường dẫn đến thư mục lưu trữ tài liệu của bạn.
2. Tải Tài liệu: Sử dụng `Document` lớp để tải tài liệu Word của bạn.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Bước 3: Chuẩn bị thư mục xuất

Trước khi xuất, hãy đảm bảo rằng thư mục xuất của chúng ta đã sẵn sàng. Đây là nơi tệp HTML và hình ảnh của chúng ta sẽ được lưu.

1. Xác định thư mục xuất: Chỉ định đường dẫn nơi các tệp đã xuất sẽ được lưu.
2. Kiểm tra và dọn dẹp thư mục: Đảm bảo thư mục tồn tại và trống.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Bước 4: Cấu hình tùy chọn lưu

Đây chính là nơi phép thuật xảy ra. Chúng ta cần thiết lập tùy chọn lưu để xuất trường biểu mẫu nhập văn bản dưới dạng văn bản thuần túy.

1. Tạo tùy chọn lưu: Khởi tạo một tùy chọn mới `HtmlSaveOptions` sự vật.
2. Đặt tùy chọn xuất văn bản: Cấu hình `ExportTextInputFormFieldAsText` tài sản để `true`.
3. Thiết lập thư mục hình ảnh: Xác định thư mục nơi hình ảnh sẽ được lưu.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Bước 5: Lưu tài liệu dưới dạng HTML

Cuối cùng, hãy lưu tài liệu Word dưới dạng tệp HTML bằng tùy chọn lưu đã cấu hình của chúng tôi.

1. Xác định đường dẫn đầu ra: Chỉ định đường dẫn nơi tệp HTML sẽ được lưu.
2. Lưu tài liệu: Sử dụng `Save` phương pháp của `Document` lớp để xuất tài liệu.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Phần kết luận

Và bạn đã có nó! Bạn đã xuất thành công một trường biểu mẫu nhập văn bản dưới dạng văn bản thuần túy bằng Aspose.Words cho .NET. Hướng dẫn này sẽ cung cấp cho bạn cách tiếp cận từng bước rõ ràng để thực hiện nhiệm vụ này. Hãy nhớ rằng, thực hành tạo nên sự hoàn hảo, vì vậy hãy tiếp tục thử nghiệm với các tùy chọn và cài đặt khác nhau để xem bạn có thể làm gì khác với Aspose.Words.

## Câu hỏi thường gặp

### Tôi có thể xuất các loại trường biểu mẫu khác bằng phương pháp tương tự không?

Có, bạn có thể xuất các loại trường biểu mẫu khác bằng cách cấu hình các thuộc tính khác nhau của `HtmlSaveOptions` lớp học.

### Nếu tài liệu của tôi có hình ảnh thì sao?

Các hình ảnh sẽ được lưu trong thư mục hình ảnh đã chỉ định. Hãy chắc chắn thiết lập `ImagesFolder` tài sản trong `HtmlSaveOptions`.

### Tôi có cần giấy phép sử dụng Aspose.Words không?

Có, bạn có thể dùng thử miễn phí [đây](https://releases.aspose.com/) hoặc mua giấy phép [đây](https://purchase.aspose.com/buy).

### Tôi có thể tùy chỉnh HTML đã xuất không?

Chắc chắn rồi! Aspose.Words cung cấp nhiều tùy chọn khác nhau để tùy chỉnh đầu ra HTML. Tham khảo [tài liệu](https://reference.aspose.com/words/net/) để biết thêm chi tiết.

### Aspose.Words có tương thích với .NET Core không?

Có, Aspose.Words tương thích với .NET Core, .NET Framework và các nền tảng .NET khác.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}