---
"description": "Tìm hiểu cách thêm hình mờ văn bản với các tùy chọn cụ thể vào tài liệu Word của bạn bằng Aspose.Words cho .NET. Tùy chỉnh phông chữ, kích thước, màu sắc và bố cục dễ dàng."
"linktitle": "Thêm hình mờ văn bản với các tùy chọn cụ thể"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Thêm hình mờ văn bản với các tùy chọn cụ thể"
"url": "/vi/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm hình mờ văn bản với các tùy chọn cụ thể

## Giới thiệu

Watermark có thể là một bổ sung phong cách và chức năng cho các tài liệu Word của bạn, phục vụ cho các mục đích từ đánh dấu tài liệu là bí mật đến thêm nét cá nhân hóa. Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm watermark văn bản vào tài liệu Word bằng Aspose.Words cho .NET. Chúng ta sẽ đi sâu vào các tùy chọn cụ thể mà bạn có thể cấu hình, chẳng hạn như họ phông chữ, kích thước phông chữ, màu sắc và bố cục. Cuối cùng, bạn sẽ có thể tùy chỉnh watermark của tài liệu để phù hợp với nhu cầu chính xác của mình. Vì vậy, hãy lấy trình soạn thảo mã của bạn và bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã chuẩn bị những thứ sau:

1. Aspose.Words cho Thư viện .NET: Bạn sẽ cần cài đặt thư viện Aspose.Words. Nếu bạn chưa cài đặt, bạn có thể tải xuống từ [Liên kết tải xuống Aspose.Words](https://releases.aspose.com/words/net/).
2. Hiểu biết cơ bản về C#: Hướng dẫn này sẽ sử dụng C# làm ngôn ngữ lập trình. Nắm vững cú pháp C# cơ bản sẽ hữu ích.
3. Môi trường phát triển .NET: Đảm bảo bạn đã thiết lập môi trường phát triển (như Visual Studio) nơi bạn có thể tạo và chạy các ứng dụng .NET của mình.

## Nhập không gian tên

Để làm việc với Aspose.Words, bạn sẽ cần phải bao gồm các không gian tên cần thiết trong dự án của mình. Sau đây là những gì bạn cần nhập:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Bước 1: Thiết lập tài liệu của bạn

Đầu tiên, bạn cần tải tài liệu bạn muốn làm việc. Đối với hướng dẫn này, chúng tôi sẽ sử dụng một tài liệu mẫu có tên `Document.docx`. Đảm bảo tài liệu này tồn tại trong thư mục bạn chỉ định.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Trong bước này, bạn xác định thư mục nơi tài liệu của bạn được lưu trữ và tải nó vào một phiên bản của `Document` lớp học.

## Bước 2: Cấu hình tùy chọn hình mờ

Tiếp theo, cấu hình các tùy chọn cho hình mờ văn bản của bạn. Bạn có thể tùy chỉnh nhiều khía cạnh khác nhau, chẳng hạn như họ phông chữ, kích thước phông chữ, màu sắc và bố cục. Hãy thiết lập các tùy chọn này.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Sau đây là chức năng của từng tùy chọn:
- `FontFamily`: Chỉ định phông chữ của văn bản hình mờ.
- `FontSize`Đặt kích thước của văn bản hình mờ.
- `Color`: Xác định màu của văn bản hình mờ.
- `Layout`: Xác định hướng của hình mờ (ngang hoặc chéo).
- `IsSemitrasparent`: Thiết lập xem hình mờ có trong suốt một phần hay không.

## Bước 3: Thêm Văn bản Hình mờ

Bây giờ, áp dụng hình mờ vào tài liệu của bạn bằng các tùy chọn đã cấu hình trước đó. Trong bước này, bạn sẽ đặt văn bản hình mờ thành "Test" và áp dụng các tùy chọn bạn đã xác định.

```csharp
doc.Watermark.SetText("Test", options);
```

Dòng mã này thêm hình mờ có chữ "Test" vào tài liệu, áp dụng các tùy chọn đã chỉ định.

## Bước 4: Lưu tài liệu

Cuối cùng, lưu tài liệu với hình mờ mới được áp dụng. Bạn có thể lưu với tên mới để tránh ghi đè lên tài liệu gốc.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Đoạn mã này lưu tài liệu đã sửa đổi trong cùng thư mục với tên tệp mới.

## Phần kết luận

Thêm hình mờ văn bản vào tài liệu Word của bạn bằng Aspose.Words cho .NET là một quy trình đơn giản khi bạn chia nhỏ thành các bước dễ quản lý. Bằng cách làm theo hướng dẫn này, bạn đã học cách cấu hình nhiều tùy chọn hình mờ khác nhau, bao gồm phông chữ, kích thước, màu sắc, bố cục và độ trong suốt. Với những kỹ năng này, giờ đây bạn có thể tùy chỉnh tài liệu của mình để đáp ứng tốt hơn nhu cầu của mình hoặc để đưa vào thông tin cần thiết như tính bảo mật hoặc thương hiệu.

Nếu bạn có bất kỳ câu hỏi nào hoặc cần hỗ trợ thêm, vui lòng kiểm tra [Tài liệu Aspose.Words](https://reference.aspose.com/words/net/) hoặc ghé thăm [Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/words/8) để được trợ giúp thêm.

## Câu hỏi thường gặp

### Tôi có thể sử dụng phông chữ khác nhau cho hình mờ không?

Có, bạn có thể chọn bất kỳ phông chữ nào được cài đặt trên hệ thống của mình bằng cách chỉ định `FontFamily` tài sản trong `TextWatermarkOptions`.

### Làm thế nào để thay đổi màu sắc của hình mờ?

Bạn có thể thay đổi màu của hình mờ bằng cách thiết lập `Color` tài sản trong `TextWatermarkOptions` đến bất kỳ `System.Drawing.Color` giá trị.

### Có thể thêm nhiều hình mờ vào một tài liệu không?

Aspose.Words hỗ trợ thêm từng hình mờ một. Để thêm nhiều hình mờ, bạn cần tạo và áp dụng chúng theo trình tự.

### Tôi có thể điều chỉnh vị trí của hình mờ không?

Các `WatermarkLayout` thuộc tính xác định hướng, nhưng các điều chỉnh vị trí chính xác không được hỗ trợ trực tiếp. Bạn có thể cần sử dụng các kỹ thuật khác để định vị chính xác.

### Tôi phải làm sao nếu cần hình mờ bán trong suốt?

Đặt `IsSemitrasparent` tài sản để `true` để làm cho hình mờ của bạn trở nên trong suốt một phần.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}