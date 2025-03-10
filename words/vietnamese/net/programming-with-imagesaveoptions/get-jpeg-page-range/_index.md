---
title: Lấy phạm vi trang Jpeg
linktitle: Lấy phạm vi trang Jpeg
second_title: API xử lý tài liệu Aspose.Words
description: Chuyển đổi các trang cụ thể của tài liệu Word sang JPEG với các thiết lập tùy chỉnh bằng Aspose.Words cho .NET. Tìm hiểu cách điều chỉnh độ sáng, độ tương phản và độ phân giải từng bước.
weight: 10
url: /vi/net/programming-with-imagesaveoptions/get-jpeg-page-range/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lấy phạm vi trang Jpeg

## Giới thiệu

Chuyển đổi tài liệu Word sang hình ảnh có thể cực kỳ hữu ích, cho dù bạn đang tạo hình thu nhỏ, xem trước tài liệu trực tuyến hay chia sẻ nội dung ở định dạng dễ truy cập hơn. Với Aspose.Words for .NET, bạn có thể dễ dàng chuyển đổi các trang cụ thể trong tài liệu Word của mình sang định dạng JPEG trong khi tùy chỉnh nhiều cài đặt khác nhau như độ sáng, độ tương phản và độ phân giải. Hãy cùng tìm hiểu cách thực hiện từng bước này!

## Điều kiện tiên quyết

Trước khi bắt đầu, bạn cần chuẩn bị một số thứ sau:

-  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt Aspose.Words cho .NET. Bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Môi trường phát triển AC# như Visual Studio.
- Tài liệu mẫu: Một tài liệu Word để làm việc. Bạn có thể sử dụng bất kỳ tệp .docx nào cho hướng dẫn này.
- Kiến thức cơ bản về C#: Có kinh nghiệm lập trình C#.

Sau khi đã chuẩn bị xong, chúng ta hãy bắt đầu nhé!

## Nhập không gian tên

Để sử dụng Aspose.Words cho .NET, bạn sẽ cần nhập các không gian tên cần thiết vào đầu mã của mình. Điều này đảm bảo bạn có quyền truy cập vào tất cả các lớp và phương thức cần thiết để thao tác tài liệu.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Tải tài liệu của bạn

Đầu tiên, chúng ta cần tải tài liệu Word mà chúng ta muốn chuyển đổi. Giả sử tài liệu của chúng ta có tên là`Rendering.docx` và nằm trong thư mục được chỉ định bởi trình giữ chỗ`YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Mã này khởi tạo đường dẫn đến tài liệu của bạn và tải nó vào Aspose.Words`Document` sự vật.

## Bước 2: Thiết lập ImageSaveOptions

 Tiếp theo, chúng ta sẽ thiết lập`ImageSaveOptions` để chỉ định cách chúng ta muốn JPEG được tạo ra. Điều này bao gồm thiết lập phạm vi trang, độ sáng, độ tương phản và độ phân giải của hình ảnh.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Chỉ chuyển đổi trang đầu tiên
options.ImageBrightness = 0.3f;   // Thiết lập độ sáng
options.ImageContrast = 0.7f;     // Thiết lập độ tương phản
options.HorizontalResolution = 72f; // Thiết lập độ phân giải
```

## Bước 3: Lưu tài liệu dưới dạng JPEG

Cuối cùng, chúng ta lưu tài liệu dưới dạng tệp JPEG bằng cách sử dụng các thiết lập đã xác định.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

 Mã này lưu trang đầu tiên của`Rendering.docx` dưới dạng ảnh JPEG với các thiết lập độ sáng, độ tương phản và độ phân giải đã chỉ định.

## Phần kết luận

Và bạn đã có nó! Bạn đã chuyển đổi thành công một trang cụ thể của tài liệu Word thành hình ảnh JPEG với các thiết lập tùy chỉnh bằng Aspose.Words cho .NET. Quá trình này có thể được điều chỉnh để phù hợp với nhiều nhu cầu khác nhau, cho dù bạn đang chuẩn bị hình ảnh cho trang web, tạo bản xem trước tài liệu hay nhiều hơn nữa.

## Câu hỏi thường gặp

### Tôi có thể chuyển đổi nhiều trang cùng lúc không?
 Có, bạn có thể chỉ định một phạm vi trang bằng cách sử dụng`PageSet` tài sản trong`ImageSaveOptions`.

### Làm thế nào để điều chỉnh chất lượng hình ảnh?
 Bạn có thể điều chỉnh chất lượng của JPEG bằng cách sử dụng`JpegQuality` tài sản trong`ImageSaveOptions`.

### Tôi có thể lưu ở định dạng hình ảnh khác không?
 Có, Aspose.Words hỗ trợ nhiều định dạng hình ảnh như PNG, BMP và TIFF. Thay đổi`SaveFormat` TRONG`ImageSaveOptions` theo đó.

### Có cách nào để xem trước hình ảnh trước khi lưu không?
Bạn sẽ cần phải triển khai cơ chế xem trước riêng biệt vì Aspose.Words không cung cấp tính năng xem trước tích hợp.

### Làm thế nào để tôi có được giấy phép tạm thời cho Aspose.Words?
 Bạn có thể yêu cầu một[giấy phép tạm thời ở đây](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
