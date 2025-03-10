---
title: Danh sách có dấu đầu dòng
linktitle: Danh sách có dấu đầu dòng
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách tạo và tùy chỉnh danh sách có dấu đầu dòng trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước này.
weight: 10
url: /vi/net/working-with-markdown/bulleted-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Danh sách có dấu đầu dòng

## Giới thiệu

Sẵn sàng khám phá thế giới Aspose.Words cho .NET chưa? Hôm nay, chúng ta sẽ cùng tìm hiểu cách tạo danh sách có dấu đầu dòng trong tài liệu Word của bạn. Cho dù bạn đang sắp xếp ý tưởng, liệt kê các mục hay chỉ thêm một chút cấu trúc vào tài liệu của mình, danh sách có dấu đầu dòng đều rất tiện dụng. Vậy, hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

1.  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words. Nếu bạn chưa có, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Môi trường phát triển AC# như Visual Studio.
3. Kiến thức cơ bản về C#: Hiểu biết cơ bản về lập trình C# sẽ giúp bạn theo dõi.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Điều này giống như thiết lập bối cảnh để mã của chúng ta chạy trơn tru.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước dễ thực hiện và dễ quản lý.

## Bước 1: Tạo một tài liệu mới

Được rồi, chúng ta hãy bắt đầu bằng cách tạo một tài liệu mới. Đây là nơi mọi điều kỳ diệu sẽ xảy ra.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Bước 2: Áp dụng định dạng danh sách dấu đầu dòng

Tiếp theo, chúng ta sẽ áp dụng định dạng danh sách dấu đầu dòng. Điều này cho tài liệu biết rằng chúng ta sắp bắt đầu một danh sách dấu đầu dòng.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Bước 3: Tùy chỉnh danh sách dấu đầu dòng

Ở đây, chúng ta sẽ tùy chỉnh danh sách bullet theo ý thích của mình. Đối với ví dụ này, chúng ta sẽ sử dụng dấu gạch ngang (-) làm bullet.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Bước 4: Thêm mục danh sách

Bây giờ, hãy thêm một số mục vào danh sách có dấu đầu dòng. Đây là nơi bạn có thể sáng tạo và thêm bất kỳ nội dung nào bạn cần.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Bước 5: Thêm các mục phụ

Để làm cho mọi thứ thú vị hơn, hãy thêm một số mục phụ vào "Mục 2". Điều này giúp sắp xếp các điểm phụ.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Quay lại cấp độ danh sách chính
```

## Phần kết luận

Và bạn đã có nó! Bạn vừa tạo một danh sách có dấu đầu dòng trong tài liệu Word bằng Aspose.Words cho .NET. Đây là một quy trình đơn giản nhưng cực kỳ mạnh mẽ để sắp xếp tài liệu của bạn. Cho dù bạn đang tạo danh sách đơn giản hay danh sách lồng nhau phức tạp, Aspose.Words đều có thể đáp ứng nhu cầu của bạn.

Hãy thoải mái thử nghiệm các kiểu danh sách và định dạng khác nhau để phù hợp với nhu cầu của bạn. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể sử dụng các ký hiệu dấu đầu dòng khác nhau trong danh sách không?
    Có, bạn có thể tùy chỉnh các ký hiệu dấu đầu dòng bằng cách thay đổi`NumberFormat` tài sản.

### Làm thế nào để thêm nhiều mức thụt lề hơn?
    Sử dụng`ListIndent` phương pháp để thêm nhiều cấp độ hơn và`ListOutdent` để quay lại cấp độ cao hơn.

### Có thể kết hợp danh sách dấu đầu dòng và danh sách số được không?
   Chắc chắn rồi! Bạn có thể chuyển đổi giữa định dạng dấu đầu dòng và số bằng cách sử dụng`ApplyNumberDefault` Và`ApplyBulletDefault` phương pháp.

### Tôi có thể định dạng văn bản trong các mục danh sách không?
    Có, bạn có thể áp dụng các kiểu, phông chữ và định dạng khác nhau cho văn bản trong các mục danh sách bằng cách sử dụng`Font` tài sản của`DocumentBuilder`.

### Làm thế nào để tạo danh sách có nhiều cột dấu đầu dòng?
   Bạn có thể sử dụng định dạng bảng để tạo danh sách nhiều cột, trong đó mỗi ô chứa một danh sách có dấu đầu dòng riêng biệt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
