---
"description": "Tìm hiểu cách thêm mã và chuỗi thông tin có hàng rào vào tài liệu Word bằng Aspose.Words cho .NET. Có kèm hướng dẫn từng bước. Nâng cao kỹ năng định dạng tài liệu của bạn."
"linktitle": "Mã được rào chắn"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Mã được rào chắn"
"url": "/vi/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mã được rào chắn

## Giới thiệu

Xin chào, các lập trình viên! Hôm nay, chúng ta sẽ khám phá thế giới của Aspose.Words dành cho .NET để thành thạo nghệ thuật thêm mã được rào chắn và mã được rào chắn với chuỗi thông tin vào tài liệu Word của bạn. Hãy tưởng tượng tài liệu Word của bạn như một bức tranh, và bạn, một nghệ sĩ, sắp vẽ với độ chính xác của một nhà phát triển dày dạn kinh nghiệm. Với Aspose.Words, bạn có được sức mạnh để nâng cao tài liệu của mình theo chương trình với các khối mã được định dạng, có cấu trúc, giúp tài liệu kỹ thuật của bạn tỏa sáng với sự chuyên nghiệp và rõ ràng.

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

- Kiến thức cơ bản về C#: Hiểu biết chung về C# sẽ giúp bạn nắm bắt các khái niệm một cách nhanh chóng.
- Aspose.Words for .NET: Bạn cần cài đặt Aspose.Words for .NET. Nếu bạn chưa có, hãy tải về [đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Visual Studio hoặc bất kỳ IDE C# nào khác mà bạn cảm thấy thoải mái.

## Nhập không gian tên

Trước tiên, bạn cần nhập các không gian tên cần thiết. Điều này giống như việc tập hợp tất cả các công cụ của bạn trước khi bắt đầu một dự án.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Bây giờ, chúng ta hãy phân tích quy trình theo từng bước.

## Bước 1: Thiết lập dự án của bạn

Trước khi có thể tạo các khối mã được định dạng đẹp mắt trong tài liệu Word, chúng ta cần thiết lập một dự án mới trong Visual Studio.

1. Tạo một dự án mới: Mở Visual Studio và tạo một ứng dụng bảng điều khiển C# mới.
2. Thêm Aspose.Words Tham khảo: Cài đặt Aspose.Words thông qua NuGet Package Manager. Bạn có thể thực hiện việc này bằng cách nhấp chuột phải vào dự án của mình trong Solution Explorer, chọn "Manage NuGet Packages" và tìm kiếm Aspose.Words.

## Bước 2: Khởi tạo DocumentBuilder

Bây giờ dự án của bạn đã được thiết lập, hãy khởi tạo DocumentBuilder, đây sẽ là công cụ chính để thêm nội dung vào tài liệu Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Bước 3: Tạo kiểu cho mã có hàng rào

Để thêm mã có hàng rào, trước tiên chúng ta cần tạo một kiểu. Hãy nghĩ về điều này như việc thiết lập chủ đề cho khối mã của chúng ta.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Bước 4: Thêm mã được rào chắn vào tài liệu

Khi đã có kiểu dáng như ý, giờ đây chúng ta có thể thêm khối mã được phân cách vào tài liệu.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Bước 5: Tạo kiểu cho mã được rào chắn bằng chuỗi thông tin

Đôi khi, bạn có thể muốn chỉ định ngôn ngữ lập trình hoặc thêm thông tin bổ sung vào khối mã của mình. Hãy tạo một kiểu cho việc đó.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Bước 6: Thêm Mã được Rào chắn với Chuỗi Thông tin vào Tài liệu

Bây giờ, chúng ta hãy thêm một khối mã được phân cách bằng chuỗi thông tin để chỉ ra rằng đó là mã C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Phần kết luận

Xin chúc mừng! Bạn vừa thêm các khối mã được rào chắn và mã được rào chắn với chuỗi thông tin vào tài liệu Word của mình bằng Aspose.Words cho .NET. Đây chỉ là phần nổi của tảng băng chìm. Với Aspose.Words, bạn có thể tự động hóa và nâng cao quá trình xử lý tài liệu của mình lên tầm cao mới. Hãy tiếp tục khám phá và viết mã vui vẻ!

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, thao tác và chuyển đổi các tài liệu Word theo cách lập trình.

### Tôi có thể sử dụng Aspose.Words với các ngôn ngữ lập trình khác không?
Aspose.Words chủ yếu hỗ trợ các ngôn ngữ .NET, nhưng cũng có phiên bản dành cho Java, Python và các ngôn ngữ khác.

### Aspose.Words có miễn phí sử dụng không?
Aspose.Words là một sản phẩm thương mại, nhưng bạn có thể tải xuống bản dùng thử miễn phí [đây](https://releases.aspose.com/) để khám phá các tính năng của nó.

### Tôi có thể nhận được hỗ trợ cho Aspose.Words như thế nào?
Bạn có thể nhận được sự hỗ trợ từ cộng đồng và nhà phát triển Aspose [đây](https://forum.aspose.com/c/words/8).

### Aspose.Words còn cung cấp những tính năng nào khác?
Aspose.Words cung cấp nhiều tính năng bao gồm chuyển đổi tài liệu, tạo tài liệu theo mẫu, báo cáo và nhiều tính năng khác.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}