---
"description": "Tìm hiểu cách ký tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước này. Bảo mật tài liệu của bạn một cách dễ dàng."
"linktitle": "Ký tên vào tài liệu Word"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Ký tên vào tài liệu Word"
"url": "/vi/net/programming-with-digital-signatures/sign-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ký tên vào tài liệu Word

## Giới thiệu

Trong thế giới kỹ thuật số ngày nay, việc bảo mật tài liệu của bạn trở nên quan trọng hơn bao giờ hết. Chữ ký số cung cấp một cách để đảm bảo tính xác thực và toàn vẹn của tài liệu của bạn. Nếu bạn đang muốn ký một tài liệu Word theo chương trình bằng Aspose.Words cho .NET, bạn đã đến đúng nơi. Hướng dẫn này sẽ hướng dẫn bạn thực hiện toàn bộ quy trình, từng bước một, theo cách đơn giản và hấp dẫn.

## Điều kiện tiên quyết

Trước khi tìm hiểu về mã, bạn cần chuẩn bị một số điều sau:

1. Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt phiên bản mới nhất của Aspose.Words cho .NET. Bạn có thể tải xuống [đây](https://releases.aspose.com/words/net/).
2. Môi trường .NET: Đảm bảo bạn đã thiết lập môi trường phát triển .NET (ví dụ: Visual Studio).
3. Chứng chỉ số: Lấy chứng chỉ số (ví dụ: tệp .pfx) để ký tài liệu.
4. Tài liệu cần ký: Chuẩn bị sẵn một tài liệu Word mà bạn muốn ký.

## Nhập không gian tên

Trước tiên, bạn cần nhập các không gian tên cần thiết. Thêm các chỉ thị sau vào dự án của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Security.Cryptography.X509Certificates;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước dễ quản lý hơn.

## Bước 1: Tải Chứng chỉ số

Bước đầu tiên là tải chứng chỉ số từ tệp. Chứng chỉ này sẽ được sử dụng để ký tài liệu.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Tải chứng chỉ số.
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

### Giải thích

- `dataDir`: Đây là thư mục lưu trữ chứng chỉ và tài liệu của bạn.
- `CertificateHolder.Create`: Phương pháp này tải chứng chỉ từ đường dẫn đã chỉ định. Thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục của bạn và `"morzal.pfx"` với tên tệp chứng chỉ của bạn. `"aw"` là mật khẩu cho chứng chỉ.

## Bước 2: Tải tài liệu Word

Tiếp theo, hãy tải tài liệu Word mà bạn muốn ký.

```csharp
// Tải tài liệu cần ký.
Document doc = new Document(dataDir + "Digitally signed.docx");
```

### Giải thích

- `Document`Lớp này đại diện cho tài liệu Word. Thay thế `"Digitally signed.docx"` với tên tài liệu của bạn.

## Bước 3: Ký vào tài liệu

Bây giờ, sử dụng `DigitalSignatureUtil.Sign` phương pháp ký tài liệu.

```csharp
// Ký vào tài liệu.
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx", dataDir + "Document.Signed.docx", certHolder);
```

### Giải thích

- `DigitalSignatureUtil.Sign`: Phương pháp này ký tài liệu bằng chứng chỉ đã tải. Tham số đầu tiên là đường dẫn đến tài liệu gốc, tham số thứ hai là đường dẫn đến tài liệu đã ký và tham số thứ ba là người giữ chứng chỉ.

## Bước 4: Lưu tài liệu đã ký

Cuối cùng, lưu tài liệu đã ký vào vị trí đã chỉ định.

```csharp
// Lưu tài liệu đã ký.
doc.Save(dataDir + "Document.Signed.docx");
```

### Giải thích

- `doc.Save`: Phương pháp này lưu tài liệu đã ký. Thay thế `"Document.Signed.docx"` với tên mong muốn của tài liệu bạn đã ký.

## Phần kết luận

Và bạn đã có nó! Bạn đã ký thành công một tài liệu Word bằng Aspose.Words cho .NET. Bằng cách làm theo các bước đơn giản này, bạn có thể đảm bảo tài liệu của mình được ký và xác thực an toàn. Hãy nhớ rằng, chữ ký số là một công cụ mạnh mẽ để bảo vệ tính toàn vẹn của tài liệu, vì vậy hãy sử dụng chúng bất cứ khi nào cần thiết.

## Câu hỏi thường gặp

### Chữ ký số là gì?
Chữ ký số là dạng chữ ký điện tử có thể được sử dụng để xác thực danh tính của người ký và đảm bảo rằng tài liệu không bị thay đổi.

### Tại sao tôi cần chứng chỉ số?
Cần có chứng chỉ số để tạo chữ ký số. Chứng chỉ này chứa khóa công khai và danh tính của chủ sở hữu chứng chỉ, cung cấp phương tiện để xác minh chữ ký.

### Tôi có thể sử dụng bất kỳ tệp .pfx nào để ký không?
Có, miễn là tệp .pfx chứa chứng chỉ số hợp lệ và bạn có mật khẩu để truy cập vào tệp đó.

### Aspose.Words cho .NET có miễn phí sử dụng không?
Aspose.Words for .NET là một thư viện thương mại. Bạn có thể tải xuống bản dùng thử miễn phí [đây](https://releases.aspose.com/), nhưng bạn sẽ cần phải mua giấy phép để có đầy đủ chức năng. Bạn có thể mua nó [đây](https://purchase.aspose.com/buy).

### Tôi có thể tìm thêm thông tin về Aspose.Words cho .NET ở đâu?
Bạn có thể tìm thấy tài liệu toàn diện [đây](https://reference.aspose.com/words/net/) và hỗ trợ [đây](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}