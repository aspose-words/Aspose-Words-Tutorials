---
title: gạch ngang
linktitle: gạch ngang
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách áp dụng định dạng gạch ngang cho văn bản bằng Aspose.Words cho .NET với hướng dẫn từng bước của chúng tôi. Nâng cao kỹ năng xử lý tài liệu của bạn.
weight: 10
url: /vi/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# gạch ngang

## Giới thiệu

Chào mừng bạn đến với hướng dẫn chi tiết này về cách áp dụng định dạng gạch ngang cho văn bản bằng Aspose.Words cho .NET. Nếu bạn đang muốn nâng cao kỹ năng xử lý tài liệu và thêm nét độc đáo cho văn bản của mình, bạn đã đến đúng nơi rồi. Hãy cùng tìm hiểu nhé!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Aspose.Words cho .NET: Tải xuống[đây](https://releases.aspose.com/words/net/).
- .NET Framework: Đảm bảo rằng bạn đã cài đặt .NET Framework trên hệ thống của mình.
- Môi trường phát triển: Một IDE như Visual Studio.
- Kiến thức cơ bản về C#: Cần phải quen thuộc với lập trình C#.

## Nhập không gian tên

Để bắt đầu, bạn cần nhập các không gian tên cần thiết. Đây là những không gian tên thiết yếu để truy cập thư viện Aspose.Words và các tính năng của thư viện này.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Khởi tạo DocumentBuilder

 Các`DocumentBuilder` class là một công cụ mạnh mẽ trong Aspose.Words cho phép bạn thêm nội dung vào tài liệu một cách dễ dàng.

```csharp
// Khởi tạo DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Bước 2: Thiết lập thuộc tính gạch ngang

Bây giờ, hãy áp dụng thuộc tính gạch ngang cho văn bản của chúng ta. Điều này liên quan đến việc thiết lập`StrikeThrough` tài sản của`Font` phản đối`true`.

```csharp
// Làm cho văn bản thành gạch ngang.
builder.Font.StrikeThrough = true;
```

## Bước 3: Viết văn bản có gạch ngang

 Với thuộc tính gạch ngang được thiết lập, bây giờ chúng ta có thể thêm văn bản của mình.`Writeln` phương pháp này sẽ thêm văn bản vào tài liệu.

```csharp
// Viết văn bản có gạch ngang.
builder.Writeln("This text will be StrikeThrough");
```

## Phần kết luận

Và bạn đã có nó! Bạn đã thêm thành công định dạng gạch ngang vào văn bản của mình bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này mở ra một thế giới khả năng xử lý và tùy chỉnh tài liệu. Cho dù bạn đang tạo báo cáo, thư hoặc bất kỳ loại tài liệu nào khác, việc thành thạo các tính năng này chắc chắn sẽ nâng cao năng suất và chất lượng đầu ra của bạn.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện xử lý tài liệu mạnh mẽ cho phép các nhà phát triển tạo, thao tác và chuyển đổi tài liệu Word theo cách lập trình.

### Tôi có thể sử dụng Aspose.Words cho .NET trong một dự án thương mại không?
 Có, bạn có thể sử dụng Aspose.Words cho .NET trong các dự án thương mại. Để biết các tùy chọn mua, hãy truy cập[mua trang](https://purchase.aspose.com/buy).

### Có bản dùng thử miễn phí Aspose.Words dành cho .NET không?
 Có, bạn có thể tải xuống bản dùng thử miễn phí[đây](https://releases.aspose.com/).

### Làm thế nào để tôi nhận được hỗ trợ cho Aspose.Words dành cho .NET?
Bạn có thể nhận được sự hỗ trợ từ cộng đồng Aspose và các chuyên gia về[diễn đàn hỗ trợ](https://forum.aspose.com/c/words/8).

### Tôi có thể áp dụng các tùy chọn định dạng văn bản khác bằng Aspose.Words cho .NET không?
Chắc chắn rồi! Aspose.Words for .NET hỗ trợ nhiều tùy chọn định dạng văn bản bao gồm in đậm, in nghiêng, gạch chân, v.v.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
