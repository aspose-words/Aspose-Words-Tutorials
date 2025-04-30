---
"description": "Tìm hiểu cách tạo và ký số dòng chữ ký trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước này. Hoàn hảo cho việc tự động hóa tài liệu."
"linktitle": "Tạo và ký dòng chữ ký mới"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Tạo và ký dòng chữ ký mới"
"url": "/vi/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo và ký dòng chữ ký mới

## Giới thiệu

Xin chào! Vậy là bạn có một tài liệu Word và bạn cần thêm một dòng chữ ký rồi ký số vào đó. Nghe có vẻ khó khăn phải không? Không hề! Nhờ Aspose.Words dành cho .NET, bạn có thể thực hiện việc này một cách liền mạch chỉ với một vài dòng mã. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn toàn bộ quy trình từ thiết lập môi trường đến lưu tài liệu của bạn với một chữ ký mới sáng bóng. Sẵn sàng chưa? Hãy cùng bắt đầu nào!

## Điều kiện tiên quyết

Trước khi tìm hiểu về mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết:
1. Aspose.Words cho .NET - Bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển .NET - Visual Studio được khuyến khích sử dụng.
3. Tài liệu để ký - Tạo một tài liệu Word đơn giản hoặc sử dụng một tài liệu hiện có.
4. Tệp chứng chỉ - Tệp này cần thiết cho chữ ký số. Bạn có thể sử dụng `.pfx` tài liệu.
5. Hình ảnh cho Dòng chữ ký - Tùy chọn, một tệp hình ảnh cho chữ ký.

## Nhập không gian tên

Đầu tiên, chúng ta cần nhập các không gian tên cần thiết. Bước này rất quan trọng vì nó thiết lập môi trường để sử dụng các chức năng của Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Bước 1: Thiết lập thư mục tài liệu

Mỗi dự án đều cần có khởi đầu tốt. Hãy thiết lập đường dẫn đến thư mục tài liệu của bạn. Đây là nơi tài liệu của bạn sẽ được lưu và truy xuất.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tạo một tài liệu mới

Bây giờ, hãy tạo một tài liệu Word mới bằng Aspose.Words. Đây sẽ là khung vẽ nơi chúng ta thêm dòng chữ ký.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 3: Chèn dòng chữ ký

Đây là nơi phép thuật xảy ra. Chúng tôi chèn một dòng chữ ký vào tài liệu của chúng tôi bằng cách sử dụng `DocumentBuilder` lớp học.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Bước 4: Lưu tài liệu có dòng chữ ký

Sau khi dòng chữ ký được đặt vào, chúng ta cần lưu tài liệu. Đây là bước trung gian trước khi chúng ta tiến hành ký.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Bước 5: Thiết lập tùy chọn ký tên

Bây giờ, hãy thiết lập các tùy chọn để ký tài liệu. Điều này bao gồm chỉ định ID dòng chữ ký và hình ảnh sẽ được sử dụng.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Bước 6: Tải chứng chỉ

Chữ ký số yêu cầu phải có chứng chỉ. Ở đây, chúng tôi tải tệp chứng chỉ sẽ được sử dụng để ký tài liệu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Bước 7: Ký tài liệu

Đây là bước cuối cùng. Chúng tôi sử dụng `DigitalSignatureUtil` lớp để ký tài liệu. Tài liệu đã ký sẽ được lưu với tên mới.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Phần kết luận

Và bạn đã có nó! Với các bước này, bạn đã tạo thành công một tài liệu Word mới, thêm dòng chữ ký và ký số bằng Aspose.Words cho .NET. Đây là một công cụ mạnh mẽ giúp tự động hóa tài liệu trở nên dễ dàng. Cho dù bạn đang xử lý hợp đồng, thỏa thuận hay bất kỳ tài liệu chính thức nào, phương pháp này đảm bảo chúng được ký và xác thực an toàn.

## Câu hỏi thường gặp

### Tôi có thể sử dụng định dạng hình ảnh khác cho dòng chữ ký không?
Có, bạn có thể sử dụng nhiều định dạng hình ảnh khác nhau như PNG, JPG, BMP, v.v.

### Có cần thiết phải sử dụng một `.pfx` nộp hồ sơ xin cấp giấy chứng nhận?
Vâng, một `.pfx` tệp là định dạng phổ biến để lưu trữ thông tin mật mã bao gồm chứng chỉ và khóa riêng.

### Tôi có thể thêm nhiều dòng chữ ký vào một tài liệu không?
Hoàn toàn có thể! Bạn có thể chèn nhiều dòng chữ ký bằng cách lặp lại bước chèn cho mỗi chữ ký.

### Nếu tôi không có chứng chỉ số thì sao?
Bạn sẽ cần phải xin chứng chỉ số từ một cơ quan cấp chứng chỉ đáng tin cậy hoặc tạo chứng chỉ bằng các công cụ như OpenSSL.

### Làm thế nào để xác minh chữ ký số trong tài liệu?
Bạn có thể mở tài liệu đã ký trong Word và đi tới chi tiết chữ ký để xác minh tính xác thực và toàn vẹn của chữ ký.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}