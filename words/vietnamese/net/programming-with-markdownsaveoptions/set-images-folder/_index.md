---
title: Thiết lập thư mục hình ảnh
linktitle: Thiết lập thư mục hình ảnh
second_title: API xử lý tài liệu Aspose.Words
description: Chuyển đổi tài liệu Word sang Markdown với căn chỉnh bảng phù hợp bằng Aspose.Words cho .NET. Làm theo hướng dẫn chi tiết của chúng tôi để có kết quả hoàn hảo.
weight: 10
url: /vi/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thiết lập thư mục hình ảnh

## Giới thiệu

Bạn đã bao giờ muốn xuất tài liệu Word của mình sang định dạng Markdown trong khi vẫn đảm bảo các bảng và nội dung được căn chỉnh hoàn hảo chưa? Aspose.Words cho .NET là giải pháp phù hợp cho nhiệm vụ này. Trong bài viết này, chúng tôi sẽ hướng dẫn bạn quy trình thiết lập Aspose.Words, chuẩn bị tài liệu và xuất sang Markdown với căn chỉnh nội dung bảng phù hợp. Chúng tôi sẽ chia nhỏ từng bước để bạn dễ theo dõi và hiểu. Vậy, hãy cùng tìm hiểu và chuyển đổi tài liệu Word của bạn thành các tệp Markdown được căn chỉnh đẹp mắt!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Aspose.Words cho .NET: Bạn có thể tải xuống[đây](https://releases.aspose.com/words/net/).
-  Giấy phép hợp lệ: Nhận bản dùng thử miễn phí[đây](https://releases.aspose.com/) hoặc giấy phép tạm thời[đây](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Hoặc bất kỳ IDE nào khác hỗ trợ phát triển .NET.
- Kiến thức cơ bản về C#: Hiểu biết về ngôn ngữ lập trình C#.

## Nhập không gian tên

Để bắt đầu, bạn sẽ cần nhập các không gian tên cần thiết vào dự án C# của mình. Các không gian tên này sẽ cho phép bạn truy cập chức năng Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Bước 1: Thiết lập dự án của bạn

Trước tiên, hãy thiết lập dự án .NET của bạn trong IDE. Tạo một ứng dụng bảng điều khiển mới và thêm tham chiếu đến Aspose.Words cho .NET.

### 1.1 Tạo một dự án mới

Mở Visual Studio và tạo một dự án Console Application mới. Đặt tên là "MarkdownExporter" hoặc tên tương tự.

### 1.2 Thêm tham chiếu Aspose.Words

 Để thêm Aspose.Words vào dự án của bạn, bạn có thể tải xuống DLL từ[Trang web Aspose](https://releases.aspose.com/words/net/) và thêm thủ công hoặc sử dụng NuGet Package Manager:

```bash
Install-Package Aspose.Words
```

## Bước 2: Viết mã để xuất dưới dạng Markdown

Bây giờ, chúng ta hãy viết mã để đọc tài liệu Word và lưu nó dưới dạng tệp Markdown với căn chỉnh bảng phù hợp.

### 2.1 Xác định đường dẫn đến tài liệu của bạn

Đặt đường dẫn đến tài liệu Word và thư mục mà bạn muốn lưu hình ảnh.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Tải Tài liệu

Tải tài liệu Word của bạn bằng Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Cấu hình tùy chọn lưu Markdown

 Cấu hình`MarkdownSaveOptions` để chỉ định nơi hình ảnh sẽ được lưu trữ.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Lưu tài liệu dưới dạng Markdown

 Sử dụng một`MemoryStream` để lưu tài liệu ở định dạng Markdown.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Phần kết luận

Xuất tài liệu Word sang Markdown với căn chỉnh nội dung bảng bằng Aspose.Words cho .NET rất đơn giản khi bạn làm theo các bước sau. Chỉ với một vài dòng mã, bạn có thể tự động hóa quy trình chuyển đổi và đảm bảo nội dung của mình được định dạng tốt. Bây giờ, bạn có thể dễ dàng chia sẻ tài liệu của mình ở định dạng Markdown, biết rằng chúng sẽ trông tuyệt vời và duy trì cấu trúc của chúng.

## Câu hỏi thường gặp

### Tôi có thể sử dụng Aspose.Words cho .NET với các ngôn ngữ lập trình khác không?

Có, Aspose.Words cho .NET có thể được sử dụng với bất kỳ ngôn ngữ nào tương thích với .NET như VB.NET, F#, v.v.

### Làm thế nào để tôi có được giấy phép tạm thời cho Aspose.Words?

Bạn có thể xin giấy phép tạm thời[đây](https://purchase.aspose.com/temporary-license/).

### Tôi có thể chuyển đổi những loại tài liệu nào sang Markdown?

Bạn có thể chuyển đổi nhiều loại tài liệu Word bao gồm .doc, .docx, .rtf, v.v.

### Phiên bản dùng thử của Aspose.Words có hạn chế nào không?

Phiên bản dùng thử có một số hạn chế như hình mờ trong các tệp đầu ra. Bạn có thể dùng thử miễn phí[đây](https://releases.aspose.com/).

### Tôi có thể tìm thêm ví dụ và tài liệu về Aspose.Words ở đâu?

 Bạn có thể tìm thấy tài liệu chi tiết và ví dụ trên[Trang web Aspose](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
