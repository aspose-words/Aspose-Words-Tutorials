---
title: Xuất URL Cid cho Tài nguyên Mhtml
linktitle: Xuất URL Cid cho Tài nguyên Mhtml
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách xuất URL Cid cho tài nguyên MHTML bằng Aspose.Words cho .NET trong hướng dẫn từng bước này. Hoàn hảo cho các nhà phát triển ở mọi cấp độ.
weight: 10
url: /vi/net/programming-with-htmlsaveoptions/export-cid-urls-for-mhtml-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xuất URL Cid cho Tài nguyên Mhtml

## Giới thiệu

Bạn đã sẵn sàng để thành thạo nghệ thuật xuất URL Cid cho tài nguyên MHTML bằng Aspose.Words cho .NET chưa? Cho dù bạn là một nhà phát triển dày dạn kinh nghiệm hay chỉ mới bắt đầu, hướng dẫn toàn diện này sẽ hướng dẫn bạn từng bước. Đến cuối bài viết này, bạn sẽ hiểu rõ cách xử lý hiệu quả các tài nguyên MHTML trong tài liệu Word của mình. Hãy cùng bắt đầu!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có mọi thứ cần thiết:

-  Aspose.Words for .NET: Đảm bảo bạn đã cài đặt phiên bản mới nhất của Aspose.Words for .NET. Nếu chưa, bạn có thể tải xuống từ[đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Môi trường phát triển như Visual Studio.
- Kiến thức cơ bản về C#: Mặc dù tôi sẽ hướng dẫn bạn từng bước, nhưng hiểu biết cơ bản về C# sẽ rất có ích.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Bước này thiết lập bối cảnh cho hướng dẫn của chúng ta:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước đơn giản, dễ quản lý. Mỗi bước sẽ bao gồm phần giải thích chi tiết để đảm bảo bạn có thể dễ dàng thực hiện theo.

## Bước 1: Thiết lập dự án của bạn

### Bước 1.1: Tạo một dự án mới
Mở Visual Studio và tạo một dự án C# mới. Chọn mẫu Console App để đơn giản hóa mọi thứ.

### Bước 1.2: Thêm Aspose.Words cho .NET Reference
Để sử dụng Aspose.Words cho .NET, bạn cần thêm tham chiếu đến thư viện Aspose.Words. Bạn có thể thực hiện việc này thông qua NuGet Package Manager:

1. Nhấp chuột phải vào dự án của bạn trong Solution Explorer.
2. Chọn "Quản lý gói NuGet".
3. Tìm kiếm "Aspose.Words" và cài đặt.

## Bước 2: Tải tài liệu Word

### Bước 2.1: Chỉ định thư mục tài liệu
Xác định đường dẫn đến thư mục tài liệu của bạn. Đây là nơi tài liệu Word của bạn nằm.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục của bạn.

### Bước 2.2: Tải Tài liệu
Tải tài liệu Word của bạn vào dự án.

```csharp
Document doc = new Document(dataDir + "Content-ID.docx");
```

## Bước 3: Cấu hình tùy chọn lưu HTML

 Tạo một trường hợp của`HtmlSaveOptions` để tùy chỉnh cách lưu tài liệu của bạn dưới dạng MHTML.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Mhtml)
{
    PrettyFormat = true,
    ExportCidUrlsForMhtmlResources = true
};
```

- `SaveFormat.Mhtml` chỉ rõ định dạng đầu ra là MHTML.
- `PrettyFormat = true` đảm bảo đầu ra được định dạng gọn gàng.
- `ExportCidUrlsForMhtmlResources = true` cho phép xuất URL Cid cho các tài nguyên MHTML.

### Bước 4: Lưu tài liệu dưới dạng MHTML

Bước 4.1: Lưu tài liệu
Lưu tài liệu của bạn dưới dạng tệp MHTML bằng các tùy chọn đã cấu hình.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
```

## Phần kết luận

Xin chúc mừng! Bạn đã xuất thành công URL Cid cho tài nguyên MHTML bằng Aspose.Words cho .NET. Hướng dẫn này hướng dẫn bạn thiết lập dự án, tải tài liệu Word, cấu hình tùy chọn lưu HTML và lưu tài liệu dưới dạng MHTML. Bây giờ bạn có thể áp dụng các bước này vào dự án của riêng mình và cải thiện các tác vụ quản lý tài liệu.

## Câu hỏi thường gặp

### Mục đích của việc xuất URL Cid cho tài nguyên MHTML là gì?
Việc xuất URL Cid cho các tài nguyên MHTML đảm bảo rằng các tài nguyên nhúng trong tệp MHTML của bạn được tham chiếu đúng cách, cải thiện tính di động và tính toàn vẹn của tài liệu.

### Tôi có thể tùy chỉnh định dạng đầu ra thêm không?
 Có, Aspose.Words cho .NET cung cấp các tùy chọn tùy chỉnh mở rộng để lưu tài liệu. Tham khảo[tài liệu](https://reference.aspose.com/words/net/) để biết thêm chi tiết.

### Tôi có cần giấy phép để sử dụng Aspose.Words cho .NET không?
 Có, bạn cần có giấy phép để sử dụng Aspose.Words cho .NET. Bạn có thể dùng thử miễn phí[đây](https://releases.aspose.com/) hoặc mua giấy phép[đây](https://purchase.aspose.com/buy).

### Tôi có thể tự động hóa quy trình này cho nhiều tài liệu không?
Chắc chắn rồi! Bạn có thể tạo một tập lệnh để tự động hóa quy trình cho nhiều tài liệu, tận dụng sức mạnh của Aspose.Words cho .NET để xử lý các hoạt động hàng loạt một cách hiệu quả.

### Tôi có thể nhận được hỗ trợ ở đâu nếu gặp vấn đề?
Nếu bạn cần hỗ trợ, hãy truy cập diễn đàn hỗ trợ Aspose[đây](https://forum.aspose.com/c/words/8) để được hỗ trợ từ cộng đồng và các nhà phát triển Aspose.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
