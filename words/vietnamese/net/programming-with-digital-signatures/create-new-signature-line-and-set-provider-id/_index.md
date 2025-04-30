---
"description": "Tìm hiểu cách tạo dòng chữ ký mới và đặt ID nhà cung cấp trong tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn từng bước."
"linktitle": "Tạo Dòng Chữ Ký Mới Và Thiết Lập ID Nhà Cung Cấp"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Tạo Dòng Chữ Ký Mới Và Thiết Lập ID Nhà Cung Cấp"
"url": "/vi/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Dòng Chữ Ký Mới Và Thiết Lập ID Nhà Cung Cấp

## Giới thiệu

Xin chào, những người đam mê công nghệ! Bạn đã bao giờ tự hỏi làm thế nào để thêm dòng chữ ký vào tài liệu Word của mình theo chương trình chưa? Vâng, hôm nay chúng ta sẽ tìm hiểu sâu hơn về điều đó bằng cách sử dụng Aspose.Words cho .NET. Hướng dẫn này sẽ hướng dẫn bạn từng bước, giúp bạn dễ dàng tạo dòng chữ ký mới và đặt ID nhà cung cấp trong tài liệu Word của mình. Cho dù bạn đang tự động hóa quá trình xử lý tài liệu hay chỉ muốn hợp lý hóa quy trình làm việc của mình, hướng dẫn này sẽ giúp bạn.

## Điều kiện tiên quyết

Trước khi bắt tay vào thực hiện, hãy đảm bảo rằng chúng ta đã có mọi thứ cần thiết:

1. Aspose.Words cho .NET: Nếu bạn chưa tải xuống, hãy tải xuống [đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Visual Studio hoặc bất kỳ môi trường phát triển C# nào khác.
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework.
4. Chứng chỉ PFX: Để ký tài liệu, bạn sẽ cần chứng chỉ PFX. Bạn có thể lấy chứng chỉ từ một cơ quan cấp chứng chỉ đáng tin cậy.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết vào dự án C# của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Được rồi, chúng ta hãy đi vào chi tiết. Sau đây là phân tích chi tiết từng bước để tạo dòng chữ ký mới và đặt ID nhà cung cấp.

## Bước 1: Tạo một tài liệu mới

Để bắt đầu, chúng ta cần tạo một tài liệu Word mới. Đây sẽ là khung cho dòng chữ ký của chúng ta.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Trong đoạn mã này, chúng tôi đang khởi tạo một `Document` và một `DocumentBuilder`. Các `DocumentBuilder` giúp chúng ta thêm các thành phần vào tài liệu.

## Bước 2: Xác định các tùy chọn dòng chữ ký

Tiếp theo, chúng ta xác định các tùy chọn cho dòng chữ ký của mình. Bao gồm tên, chức danh, email và các thông tin chi tiết khác của người ký.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Các tùy chọn này cá nhân hóa dòng chữ ký, làm cho nó rõ ràng và chuyên nghiệp.

## Bước 3: Chèn Dòng chữ ký

Sau khi thiết lập các tùy chọn, chúng ta có thể chèn dòng chữ ký vào tài liệu.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Ở đây, `InsertSignatureLine` phương pháp này thêm dòng chữ ký và chúng tôi gán cho nó một ID nhà cung cấp duy nhất.

## Bước 4: Lưu tài liệu

Sau khi chèn dòng chữ ký, chúng ta hãy lưu tài liệu.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Thao tác này sẽ lưu tài liệu của bạn với dòng chữ ký mới được thêm vào.

## Bước 5: Thiết lập tùy chọn ký tên

Bây giờ, chúng ta cần thiết lập các tùy chọn để ký tài liệu. Bao gồm ID dòng chữ ký, ID nhà cung cấp, bình luận và thời gian ký.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Các tùy chọn này đảm bảo tài liệu được ký với thông tin chi tiết chính xác.

## Bước 6: Tạo chủ sở hữu chứng chỉ

Để ký tài liệu, chúng ta sẽ sử dụng chứng chỉ PFX. Hãy tạo người giữ chứng chỉ cho nó.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Hãy chắc chắn thay thế `"morzal.pfx"` với tập tin chứng chỉ thực tế của bạn và `"aw"` bằng mật khẩu chứng chỉ của bạn.

## Bước 7: Ký vào tài liệu

Cuối cùng, chúng ta ký tài liệu bằng tiện ích chữ ký số.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Thao tác này sẽ ký vào tài liệu và lưu thành một tệp mới.

## Phần kết luận

Và bạn đã có nó! Bạn đã tạo thành công một dòng chữ ký mới và đặt ID nhà cung cấp trong tài liệu Word bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này giúp quản lý và tự động hóa các tác vụ xử lý tài liệu cực kỳ dễ dàng. Hãy thử và xem nó có thể hợp lý hóa quy trình làm việc của bạn như thế nào.

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh giao diện của dòng chữ ký không?
Chắc chắn rồi! Bạn có thể điều chỉnh nhiều tùy chọn khác nhau trong `SignatureLineOptions` để phù hợp với nhu cầu của bạn.

### Nếu tôi không có chứng chỉ PFX thì sao?
Bạn sẽ cần phải có được một chứng chỉ từ một cơ quan cấp chứng chỉ đáng tin cậy. Chứng chỉ này rất cần thiết để ký tài liệu kỹ thuật số.

### Tôi có thể thêm nhiều dòng chữ ký vào một tài liệu không?
Có, bạn có thể thêm bao nhiêu dòng chữ ký tùy ý bằng cách lặp lại quy trình chèn với các tùy chọn khác nhau.

### Aspose.Words cho .NET có tương thích với .NET Core không?
Có, Aspose.Words for .NET hỗ trợ .NET Core, khiến nó trở nên linh hoạt cho nhiều môi trường phát triển khác nhau.

### Chữ ký số an toàn đến mức nào?
Chữ ký số được tạo bằng Aspose.Words có tính bảo mật cao, miễn là bạn sử dụng chứng chỉ hợp lệ và đáng tin cậy.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}