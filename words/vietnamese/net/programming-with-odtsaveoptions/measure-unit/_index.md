---
"description": "Tìm hiểu cách cấu hình tính năng đơn vị đo lường trong Aspose.Words cho .NET để giữ nguyên định dạng tài liệu trong quá trình chuyển đổi ODT."
"linktitle": "Đơn vị đo lường"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Đơn vị đo lường"
"url": "/vi/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Đơn vị đo lường

## Giới thiệu

Bạn đã bao giờ phải chuyển đổi tài liệu Word của mình sang các định dạng khác nhau nhưng cần một đơn vị đo lường cụ thể cho bố cục của mình chưa? Cho dù bạn đang xử lý inch, cm hay điểm, việc đảm bảo tài liệu của bạn duy trì tính toàn vẹn trong quá trình chuyển đổi là rất quan trọng. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn cách cấu hình tính năng đơn vị đo lường trong Aspose.Words cho .NET. Tính năng mạnh mẽ này đảm bảo định dạng tài liệu của bạn được giữ nguyên chính xác như bạn cần khi chuyển đổi sang định dạng ODT (Open Document Text).

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, bạn cần chuẩn bị một số thứ sau:

1. Aspose.Words for .NET: Đảm bảo bạn đã cài đặt phiên bản mới nhất của Aspose.Words for .NET. Nếu bạn chưa có, bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Một IDE như Visual Studio để viết và thực thi mã C# của bạn.
3. Kiến thức cơ bản về C#: Hiểu được những kiến thức cơ bản về C# sẽ giúp bạn theo dõi hướng dẫn.
4. Một tài liệu Word: Chuẩn bị một tài liệu Word mẫu mà bạn có thể sử dụng để chuyển đổi.

## Nhập không gian tên

Trước khi bắt đầu mã hóa, hãy đảm bảo rằng chúng ta đã nhập các không gian tên cần thiết. Thêm các chỉ thị using này vào đầu tệp mã của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

Đầu tiên, bạn cần xác định đường dẫn đến thư mục tài liệu của mình. Đây là nơi tài liệu Word của bạn nằm và nơi tệp đã chuyển đổi sẽ được lưu.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Thay thế `"YOUR DOCUMENTS DIRECTORY"` với đường dẫn thực tế đến thư mục của bạn. Điều này đảm bảo mã của bạn biết tìm tài liệu Word của bạn ở đâu.

## Bước 2: Tải tài liệu Word

Tiếp theo, bạn cần tải tài liệu Word mà bạn muốn chuyển đổi. Điều này được thực hiện bằng cách sử dụng `Document` lớp từ Aspose.Words.

```csharp
// Tải tài liệu Word
Document doc = new Document(dataDir + "Document.docx");
```

Đảm bảo rằng tài liệu Word có tên "Document.docx" của bạn có trong thư mục đã chỉ định.

## Bước 3: Cấu hình Đơn vị đo lường

Bây giờ, hãy cấu hình đơn vị đo lường cho chuyển đổi ODT. Đây là nơi phép thuật xảy ra. Chúng ta sẽ thiết lập `OdtSaveOptions` sử dụng inch làm đơn vị đo lường.

```csharp
// Cấu hình tùy chọn sao lưu với tính năng "Đơn vị đo lường"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

Trong ví dụ này, chúng tôi đang thiết lập đơn vị đo lường thành inch. Bạn cũng có thể chọn các đơn vị khác như `OdtSaveMeasureUnit.Centimeters` hoặc `OdtSaveMeasureUnit.Points` tùy thuộc vào yêu cầu của bạn.

## Bước 4: Chuyển đổi tài liệu sang ODT

Cuối cùng, chúng tôi sẽ chuyển đổi tài liệu Word sang định dạng ODT bằng cách sử dụng cấu hình `OdtSaveOptions`.

```csharp
// Chuyển đổi tài liệu sang ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Dòng mã này lưu tài liệu đã chuyển đổi trong thư mục được chỉ định với đơn vị đo lường mới được áp dụng.

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn có thể dễ dàng cấu hình tính năng đơn vị đo lường trong Aspose.Words cho .NET để đảm bảo bố cục tài liệu của bạn được bảo toàn trong quá trình chuyển đổi. Cho dù bạn đang làm việc với inch, cm hay điểm, hướng dẫn này đã chỉ cho bạn cách kiểm soát định dạng tài liệu của mình một cách dễ dàng.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ để làm việc với các tài liệu Word theo chương trình. Nó cho phép các nhà phát triển tạo, sửa đổi, chuyển đổi và xử lý các tài liệu Word mà không cần Microsoft Word.

### Tôi có thể sử dụng đơn vị đo lường khác ngoài inch không?
Có, Aspose.Words cho .NET hỗ trợ các đơn vị đo lường khác như centimet và điểm. Bạn có thể chỉ định đơn vị mong muốn bằng cách sử dụng `OdtSaveMeasureUnit` sự liệt kê.

### Có bản dùng thử miễn phí Aspose.Words dành cho .NET không?
Có, bạn có thể tải xuống bản dùng thử miễn phí Aspose.Words cho .NET từ [đây](https://releases.aspose.com/).

### Tôi có thể tìm tài liệu về Aspose.Words cho .NET ở đâu?
Bạn có thể truy cập tài liệu toàn diện về Aspose.Words cho .NET tại [liên kết này](https://reference.aspose.com/words/net/).

### Làm thế nào tôi có thể nhận được hỗ trợ cho Aspose.Words dành cho .NET?
Để được hỗ trợ, bạn có thể truy cập diễn đàn Aspose.Words tại [liên kết này](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}