---
title: Định dạng 1Bpp được lập chỉ mục
linktitle: Định dạng 1Bpp được lập chỉ mục
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách chuyển đổi tài liệu Word thành hình ảnh được lập chỉ mục 1Bpp bằng Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để chuyển đổi dễ dàng.
weight: 10
url: /vi/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng 1Bpp được lập chỉ mục

## Giới thiệu

Bạn đã bao giờ tự hỏi làm thế nào để lưu một tài liệu Word dưới dạng hình ảnh đen trắng chỉ bằng một vài dòng mã chưa? Vâng, bạn thật may mắn! Hôm nay, chúng ta sẽ khám phá một mẹo nhỏ gọn sử dụng Aspose.Words cho .NET cho phép bạn chuyển đổi tài liệu của mình thành hình ảnh được lập chỉ mục 1Bpp. Định dạng này hoàn hảo cho một số loại lưu trữ kỹ thuật số, in ấn hoặc khi bạn cần tiết kiệm dung lượng. Chúng tôi sẽ chia nhỏ từng bước để giúp bạn thực hiện dễ như ăn bánh. Sẵn sàng bắt đầu chưa? Hãy cùng bắt đầu nhé!

## Điều kiện tiên quyết

Trước khi bắt tay vào thực hiện, bạn cần chuẩn bị một số thứ sau:

-  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện. Bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển .NET: Visual Studio là một lựa chọn tốt, nhưng bạn có thể sử dụng bất kỳ môi trường nào bạn thấy thoải mái.
- Kiến thức cơ bản về C#: Đừng lo, chúng tôi sẽ giải thích một cách đơn giản, nhưng bạn cần có một chút quen thuộc với C#.
- Một tài liệu Word: Chuẩn bị một tài liệu Word mẫu để chuyển đổi.

## Nhập không gian tên

Trước tiên, chúng ta cần import các namespace cần thiết. Điều này rất quan trọng vì nó cho phép chúng ta truy cập các lớp và phương thức cần thiết từ Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

Bạn sẽ cần chỉ định đường dẫn đến thư mục tài liệu của mình. Đây là nơi lưu trữ tài liệu Word của bạn và nơi hình ảnh đã chuyển đổi sẽ được lưu.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tải tài liệu Word

 Bây giờ, hãy tải tài liệu Word vào Aspose.Words`Document` đối tượng. Đối tượng này đại diện cho tệp Word của bạn và cho phép bạn thao tác trên đó.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Bước 3: Cấu hình tùy chọn lưu hình ảnh

 Tiếp theo, chúng ta cần thiết lập`ImageSaveOptions`Đây là nơi phép thuật xảy ra. Chúng ta sẽ cấu hình nó để lưu hình ảnh ở định dạng PNG với chế độ màu được lập chỉ mục 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Điều này chỉ rõ rằng chúng ta muốn lưu tài liệu dưới dạng hình ảnh PNG.
- PageSet(1): Điều này cho biết chúng ta chỉ chuyển đổi trang đầu tiên.
- ImageColorMode.BlackAndWhite: Thiết lập hình ảnh thành đen trắng.
- ImagePixelFormat.Format1bppIndexed: Thiết lập định dạng hình ảnh thành lập chỉ mục 1Bpp.

## Bước 4: Lưu tài liệu dưới dạng hình ảnh

 Cuối cùng, chúng tôi lưu tài liệu dưới dạng hình ảnh bằng cách sử dụng`Save` phương pháp của`Document` sự vật.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Phần kết luận

Và bạn đã có nó! Chỉ với một vài dòng mã, bạn đã chuyển đổi tài liệu Word của mình thành hình ảnh được lập chỉ mục 1Bpp bằng Aspose.Words cho .NET. Phương pháp này cực kỳ hữu ích để tạo hình ảnh có độ tương phản cao, tiết kiệm không gian từ tài liệu của bạn. Bây giờ, bạn có thể dễ dàng tích hợp điều này vào các dự án và quy trình làm việc của mình. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Hình ảnh được lập chỉ mục 1Bpp là gì?
Hình ảnh được lập chỉ mục 1Bpp (1 Bit cho mỗi Pixel) là định dạng hình ảnh đen trắng trong đó mỗi pixel được biểu diễn bằng một bit duy nhất, hoặc 0 hoặc 1. Định dạng này có hiệu quả cao về mặt không gian.

### Tôi có thể chuyển đổi nhiều trang của một tài liệu Word cùng một lúc không?
 Có, bạn có thể. Sửa đổi`PageSet` tài sản trong`ImageSaveOptions` để bao gồm nhiều trang hoặc toàn bộ tài liệu.

### Tôi có cần giấy phép để sử dụng Aspose.Words cho .NET không?
 Có, Aspose.Words cho .NET yêu cầu giấy phép để có đầy đủ chức năng. Bạn có thể nhận được[giấy phép tạm thời ở đây](https://purchase.aspose.com/temporary-license/).

### Tôi có thể chuyển đổi tài liệu Word của mình sang những định dạng hình ảnh nào khác?
 Aspose.Words hỗ trợ nhiều định dạng hình ảnh bao gồm JPEG, BMP và TIFF. Chỉ cần thay đổi`SaveFormat` trong`ImageSaveOptions`.

### Tôi có thể tìm thêm tài liệu về Aspose.Words cho .NET ở đâu?
 Bạn có thể tìm thấy tài liệu chi tiết về[Trang tài liệu Aspose.Words cho .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
