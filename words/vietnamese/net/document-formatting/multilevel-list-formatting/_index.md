---
title: Định dạng danh sách đa cấp trong tài liệu Word
linktitle: Định dạng danh sách đa cấp trong tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách làm chủ định dạng danh sách đa cấp trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước của chúng tôi. Cải thiện cấu trúc tài liệu một cách dễ dàng.
weight: 10
url: /vi/net/document-formatting/multilevel-list-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng danh sách đa cấp trong tài liệu Word

## Giới thiệu

Nếu bạn là một nhà phát triển muốn tự động hóa việc tạo và định dạng tài liệu Word, Aspose.Words for .NET là một công cụ thay đổi cuộc chơi. Hôm nay, chúng ta sẽ tìm hiểu cách bạn có thể làm chủ định dạng danh sách nhiều cấp bằng cách sử dụng thư viện mạnh mẽ này. Cho dù bạn đang tạo tài liệu có cấu trúc, phác thảo báo cáo hay tạo tài liệu kỹ thuật, danh sách nhiều cấp có thể nâng cao khả năng đọc và tổ chức nội dung của bạn.

## Điều kiện tiên quyết

Trước khi đi sâu vào chi tiết, hãy đảm bảo rằng bạn có mọi thứ cần thiết để làm theo hướng dẫn này.

1. Môi trường phát triển: Đảm bảo bạn đã thiết lập môi trường phát triển. Visual Studio là lựa chọn tuyệt vời.
2.  Aspose.Words cho .NET: Tải xuống và cài đặt thư viện Aspose.Words cho .NET. Bạn có thể tải xuống[đây](https://releases.aspose.com/words/net/).
3.  Giấy phép: Xin giấy phép tạm thời nếu bạn không có giấy phép đầy đủ. Nhận nó[đây](https://purchase.aspose.com/temporary-license/).
4. Kiến thức cơ bản về C#: Có kiến thức về C# và .NET framework sẽ rất có lợi.

## Nhập không gian tên

Để sử dụng Aspose.Words cho .NET trong dự án của bạn, bạn sẽ cần nhập các không gian tên cần thiết. Sau đây là cách thực hiện:

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

## Bước 1: Khởi tạo Tài liệu và Trình xây dựng của bạn

Trước tiên, hãy tạo một tài liệu Word mới và khởi tạo DocumentBuilder. Lớp DocumentBuilder cung cấp các phương thức để chèn nội dung vào tài liệu.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 2: Áp dụng đánh số mặc định

 Để bắt đầu với một danh sách được đánh số, bạn sử dụng`ApplyNumberDefault` phương pháp. Điều này thiết lập định dạng danh sách đánh số mặc định.

```csharp
builder.ListFormat.ApplyNumberDefault();
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

 Trong những dòng này,`ApplyNumberDefault` bắt đầu danh sách được đánh số và`Writeln` thêm mục vào danh sách.

## Bước 3: Thụt lề cho các cấp độ phụ

 Tiếp theo, để tạo các cấp độ phụ trong danh sách của bạn, bạn sử dụng`ListIndent` phương pháp. Phương pháp này thụt lề mục danh sách, biến nó thành cấp con của mục trước đó.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.1");
builder.Writeln("Item 2.2");
```

Đoạn mã này thụt lề các mục, tạo ra danh sách cấp hai.

## Bước 4: Thụt lề sâu hơn cho các cấp độ sâu hơn

Bạn có thể tiếp tục thụt lề để tạo các cấp độ sâu hơn trong danh sách của mình. Ở đây, chúng ta sẽ tạo cấp độ thứ ba.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.2.1");
builder.Writeln("Item 2.2.2");
```

Bây giờ bạn có danh sách cấp ba trong "Mục 2.2".

## Bước 5: Đẩy ra ngoài để trở về mức cao hơn

 Để trở lại cấp độ cao hơn, hãy sử dụng`ListOutdent` phương pháp. Thao tác này sẽ di chuyển mục trở lại cấp danh sách trước đó.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 2.3");
```

Thao tác này đưa "Mục 2.3" trở lại cấp độ thứ hai.

## Bước 6: Xóa số

Khi hoàn tất danh sách, bạn có thể xóa số để tiếp tục sử dụng văn bản thông thường hoặc định dạng khác.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 3");
builder.ListFormat.RemoveNumbers();
```

Đoạn mã này hoàn thiện danh sách và dừng đánh số.

## Bước 7: Lưu tài liệu của bạn

Cuối cùng, lưu tài liệu vào thư mục bạn mong muốn.

```csharp
doc.Save(dataDir + "DocumentFormatting.MultilevelListFormatting.docx");
```

Tính năng này sẽ lưu tài liệu được định dạng đẹp mắt của bạn bằng danh sách nhiều cấp.

## Phần kết luận

Và bạn đã có nó! Bạn đã tạo thành công danh sách nhiều cấp trong tài liệu Word bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này cho phép bạn tự động hóa các tác vụ định dạng tài liệu phức tạp một cách dễ dàng. Hãy nhớ rằng, việc thành thạo các công cụ này không chỉ tiết kiệm thời gian mà còn đảm bảo tính nhất quán và tính chuyên nghiệp trong quy trình tạo tài liệu của bạn.

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh kiểu đánh số danh sách không?
 Có, Aspose.Words cho .NET cho phép bạn tùy chỉnh kiểu đánh số danh sách bằng cách sử dụng`ListTemplate` lớp học.

### Làm thế nào để thêm dấu đầu dòng thay vì số?
 Bạn có thể áp dụng dấu đầu dòng bằng cách sử dụng`ApplyBulletDefault` phương pháp thay thế`ApplyNumberDefault`.

### Có thể tiếp tục đánh số từ danh sách trước đó không?
 Có, bạn có thể tiếp tục đánh số bằng cách sử dụng`ListFormat.List` thuộc tính để liên kết đến danh sách hiện có.

### Làm thế nào để thay đổi mức thụt lề một cách linh hoạt?
 Bạn có thể thay đổi mức thụt lề một cách động bằng cách sử dụng`ListIndent` Và`ListOutdent` phương pháp khi cần thiết.

### Tôi có thể tạo danh sách đa cấp ở các định dạng tài liệu khác như PDF không?
Có, Aspose.Words hỗ trợ lưu tài liệu ở nhiều định dạng khác nhau bao gồm PDF, mà vẫn giữ nguyên định dạng.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
