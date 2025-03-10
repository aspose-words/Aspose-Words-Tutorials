---
title: Phát hiện số có khoảng trắng
linktitle: Phát hiện số có khoảng trắng
second_title: API xử lý tài liệu Aspose.Words
description: Khám phá cách sử dụng Aspose.Words cho .NET để phát hiện việc đánh số có khoảng trắng trong tài liệu văn bản thuần túy và đảm bảo danh sách của bạn được nhận dạng chính xác.
weight: 10
url: /vi/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Phát hiện số có khoảng trắng

## Giới thiệu

Aspose.Words dành cho những người đam mê .NET! Hôm nay, chúng ta sẽ tìm hiểu một tính năng hấp dẫn có thể giúp việc xử lý danh sách trong các tài liệu văn bản thuần túy trở nên dễ dàng. Bạn đã bao giờ xử lý các tệp văn bản trong đó một số dòng được cho là danh sách, nhưng chúng trông không ổn lắm khi được tải vào tài liệu Word chưa? Vâng, chúng tôi có một mẹo hay: phát hiện đánh số bằng khoảng trắng. Hướng dẫn này sẽ hướng dẫn bạn cách sử dụng`DetectNumberingWithWhitespaces` tùy chọn trong Aspose.Words cho .NET để đảm bảo danh sách của bạn được nhận dạng chính xác, ngay cả khi có khoảng trắng giữa các số và văn bản.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Aspose.Words cho .NET: Bạn có thể tải xuống từ[Aspose phát hành](https://releases.aspose.com/words/net/) trang.
- Môi trường phát triển: Visual Studio hoặc bất kỳ IDE C# nào khác.
- .NET Framework được cài đặt trên máy của bạn.
- Kiến thức cơ bản về C#: Hiểu những kiến thức cơ bản sẽ giúp bạn hiểu được các ví dụ.

## Nhập không gian tên

Trước khi bắt đầu code, hãy đảm bảo bạn đã nhập các namespace cần thiết vào dự án của mình. Sau đây là một đoạn mã ngắn để giúp bạn bắt đầu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Hãy chia nhỏ quy trình thành các bước đơn giản, dễ quản lý. Mỗi bước sẽ hướng dẫn bạn qua mã cần thiết và giải thích những gì đang diễn ra.

## Bước 1: Xác định thư mục tài liệu của bạn

Trước tiên, hãy thiết lập đường dẫn đến thư mục tài liệu của bạn. Đây là nơi các tệp đầu vào và đầu ra của bạn sẽ được lưu trữ.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tạo một tài liệu dạng văn bản thuần túy

Tiếp theo, chúng ta sẽ tạo một tài liệu văn bản thuần túy dưới dạng chuỗi. Tài liệu này sẽ chứa các phần có thể được diễn giải như danh sách.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Bước 3: Cấu hình LoadOptions

 Để phát hiện việc đánh số có khoảng trắng, chúng ta cần thiết lập`DetectNumberingWithWhitespaces` tùy chọn để`true` trong một`TxtLoadOptions` sự vật.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Bước 4: Tải tài liệu

 Bây giờ, hãy tải tài liệu bằng cách sử dụng`TxtLoadOptions` như một tham số. Điều này đảm bảo rằng danh sách thứ tư (có khoảng trắng) được phát hiện chính xác.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Bước 5: Lưu tài liệu

Cuối cùng, lưu tài liệu vào thư mục bạn chỉ định. Thao tác này sẽ xuất ra một tài liệu Word với danh sách được phát hiện chính xác.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Phần kết luận

Và bạn đã có nó! Chỉ với một vài dòng mã, bạn đã thành thạo nghệ thuật phát hiện đánh số có khoảng trắng trong các tài liệu văn bản thuần túy bằng Aspose.Words cho .NET. Tính năng này có thể cực kỳ hữu ích khi xử lý nhiều định dạng văn bản khác nhau và đảm bảo danh sách của bạn được thể hiện chính xác trong tài liệu Word. Vì vậy, lần sau khi bạn gặp phải những danh sách khó khăn đó, bạn sẽ biết chính xác phải làm gì.

## Câu hỏi thường gặp

###  Là gì`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` là một lựa chọn trong`TxtLoadOptions` cho phép Aspose.Words nhận dạng danh sách ngay cả khi có khoảng trắng giữa số và văn bản mục danh sách.

### Tôi có thể sử dụng tính năng này cho các dấu phân cách khác như dấu đầu dòng và dấu ngoặc vuông không?
 Có, Aspose.Words tự động phát hiện các danh sách có các dấu phân cách chung như dấu đầu dòng và dấu ngoặc vuông.`DetectNumberingWithWhitespaces` đặc biệt hữu ích với các danh sách có khoảng trắng.

###  Điều gì xảy ra nếu tôi không sử dụng`DetectNumberingWithWhitespaces`?
Nếu không có tùy chọn này, danh sách có khoảng trắng giữa số và văn bản có thể không được nhận dạng là danh sách và các mục có thể xuất hiện dưới dạng đoạn văn bản thuần túy.

### Tính năng này có khả dụng trong các sản phẩm Aspose khác không?
Tính năng cụ thể này được thiết kế riêng cho Aspose.Words dành cho .NET, được thiết kế để xử lý tài liệu Word.

### Làm thế nào tôi có thể nhận được giấy phép tạm thời cho Aspose.Words dành cho .NET?
 Bạn có thể xin giấy phép tạm thời từ[Giấy phép tạm thời Aspose](https://purchase.aspose.com/temporary-license/) trang.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
