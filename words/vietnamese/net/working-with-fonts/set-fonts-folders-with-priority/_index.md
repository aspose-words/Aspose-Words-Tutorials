---
title: Đặt thư mục phông chữ có mức độ ưu tiên
linktitle: Đặt thư mục phông chữ có mức độ ưu tiên
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thiết lập thư mục phông chữ theo thứ tự ưu tiên trong tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn của chúng tôi đảm bảo tài liệu của bạn luôn hiển thị hoàn hảo.
weight: 10
url: /vi/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt thư mục phông chữ có mức độ ưu tiên

## Giới thiệu

Trong thế giới thao tác tài liệu, việc thiết lập các thư mục phông chữ tùy chỉnh có thể tạo ra sự khác biệt lớn trong việc đảm bảo tài liệu của bạn hiển thị hoàn hảo, bất kể chúng được xem ở đâu. Hôm nay, chúng ta sẽ tìm hiểu cách bạn có thể thiết lập các thư mục phông chữ theo thứ tự ưu tiên trong tài liệu Word của mình bằng Aspose.Words cho .NET. Hướng dẫn toàn diện này sẽ hướng dẫn bạn từng bước, giúp quá trình này diễn ra suôn sẻ nhất có thể.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo rằng chúng ta có mọi thứ cần thiết. Sau đây là danh sách kiểm tra nhanh:

-  Aspose.Words cho .NET: Bạn cần cài đặt thư viện này. Nếu bạn chưa có, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Đảm bảo bạn có môi trường phát triển .NET đang hoạt động, như Visual Studio.
-  Thư mục tài liệu: Đảm bảo bạn có một thư mục cho các tài liệu của mình. Đối với các ví dụ của chúng tôi, chúng tôi sẽ sử dụng`"YOUR DOCUMENT DIRECTORY"` để giữ chỗ cho đường dẫn này.

## Nhập không gian tên

Trước tiên, chúng ta cần import các namespace cần thiết. Các namespace này rất cần thiết để truy cập các lớp và phương thức do Aspose.Words cung cấp.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bây giờ, chúng ta hãy phân tích từng bước để thiết lập thư mục phông chữ theo thứ tự ưu tiên.

## Bước 1: Thiết lập nguồn phông chữ của bạn

Để bắt đầu, bạn sẽ muốn xác định nguồn phông chữ. Đây là nơi bạn cho Aspose.Words biết nơi tìm phông chữ. Bạn có thể chỉ định nhiều thư mục phông chữ và thậm chí đặt mức độ ưu tiên của chúng.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

Trong ví dụ này, chúng tôi đang thiết lập hai nguồn phông chữ:
- SystemFontSource: Đây là nguồn phông chữ mặc định bao gồm tất cả các phông chữ được cài đặt trên hệ thống của bạn.
-  FolderFontSource: Đây là một thư mục phông chữ tùy chỉnh nằm tại`C:\\MyFonts\\` . Các`true` tham số chỉ định rằng thư mục này sẽ được quét đệ quy và`1` đặt mức độ ưu tiên của nó.

## Bước 2: Tải tài liệu của bạn

Tiếp theo, tải tài liệu bạn muốn làm việc. Đảm bảo tài liệu nằm trong thư mục bạn chỉ định.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Dòng mã này tải một tài liệu có tên`Rendering.docx` từ thư mục tài liệu của bạn.

## Bước 3: Lưu tài liệu của bạn với cài đặt phông chữ mới

Cuối cùng, hãy lưu tài liệu của bạn. Khi bạn lưu tài liệu, Aspose.Words sẽ sử dụng cài đặt phông chữ bạn đã chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 Thao tác này sẽ lưu tài liệu dưới dạng PDF trong thư mục tài liệu của bạn với tên`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Phần kết luận

Và bạn đã có nó! Bạn đã thiết lập thành công các thư mục phông chữ có mức độ ưu tiên bằng Aspose.Words cho .NET. Bằng cách chỉ định các thư mục phông chữ và mức độ ưu tiên tùy chỉnh, bạn có thể đảm bảo tài liệu của mình được hiển thị nhất quán, bất kể chúng được xem ở đâu. Điều này đặc biệt hữu ích trong các môi trường mà các phông chữ cụ thể không được cài đặt theo mặc định.

## Câu hỏi thường gặp

### Tại sao tôi cần phải thiết lập thư mục phông chữ tùy chỉnh?
Việc thiết lập thư mục phông chữ tùy chỉnh đảm bảo tài liệu của bạn hiển thị chính xác, ngay cả khi chúng sử dụng phông chữ không được cài đặt trên hệ thống đang xem.

### Tôi có thể thiết lập nhiều thư mục phông chữ tùy chỉnh không?
Có, bạn có thể chỉ định nhiều thư mục phông chữ. Aspose.Words cho phép bạn đặt mức độ ưu tiên cho từng thư mục, đảm bảo rằng các phông chữ quan trọng nhất sẽ được tìm thấy trước.

### Điều gì xảy ra nếu một phông chữ bị thiếu trong tất cả các nguồn được chỉ định?
Nếu thiếu phông chữ trong tất cả các nguồn được chỉ định, Aspose.Words sẽ sử dụng phông chữ dự phòng để đảm bảo tài liệu vẫn có thể đọc được.

### Tôi có thể thay đổi thứ tự ưu tiên của phông chữ hệ thống không?
Phông chữ hệ thống luôn được bao gồm theo mặc định, nhưng bạn có thể đặt mức độ ưu tiên của chúng theo thư mục phông chữ tùy chỉnh của mình.

### Có thể sử dụng đường dẫn mạng cho thư mục phông chữ tùy chỉnh không?
Có, bạn có thể chỉ định đường dẫn mạng dưới dạng thư mục phông chữ tùy chỉnh, cho phép bạn tập trung tài nguyên phông chữ vào một vị trí mạng.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
