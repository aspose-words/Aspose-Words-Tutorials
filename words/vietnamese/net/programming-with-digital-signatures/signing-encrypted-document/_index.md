---
"description": "Tìm hiểu cách ký các tài liệu Word được mã hóa bằng Aspose.Words cho .NET với hướng dẫn chi tiết từng bước này. Hoàn hảo cho các nhà phát triển."
"linktitle": "Ký tài liệu Word được mã hóa"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Ký tài liệu Word được mã hóa"
"url": "/vi/net/programming-with-digital-signatures/signing-encrypted-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ký tài liệu Word được mã hóa

## Giới thiệu

Bạn đã bao giờ tự hỏi làm thế nào để ký một tài liệu Word được mã hóa chưa? Hôm nay, chúng ta sẽ hướng dẫn quy trình này bằng Aspose.Words cho .NET. Hãy thắt dây an toàn và sẵn sàng cho một hướng dẫn chi tiết, hấp dẫn và thú vị!

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có mọi thứ cần thiết:

1. Aspose.Words cho .NET: Tải xuống và cài đặt từ [đây](https://releases.aspose.com/words/net/).
2. Visual Studio: Đảm bảo bạn đã cài đặt nó.
3. Chứng chỉ hợp lệ: Bạn sẽ cần tệp chứng chỉ .pfx.
4. Kiến thức cơ bản về C#: Hiểu được những kiến thức cơ bản sẽ giúp hướng dẫn này dễ hiểu hơn.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết. Đây là những không gian tên quan trọng để truy cập các chức năng của Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước đơn giản và dễ quản lý.

## Bước 1: Thiết lập dự án của bạn

Trước tiên, hãy thiết lập dự án Visual Studio của bạn. Mở Visual Studio và tạo một Ứng dụng bảng điều khiển C# mới. Đặt tên cho nó là một cái gì đó mô tả như "SignEncryptedWordDoc".

## Bước 2: Thêm Aspose.Words vào Dự án của bạn

Tiếp theo, chúng ta cần thêm Aspose.Words vào dự án của bạn. Có một số cách để thực hiện việc này, nhưng sử dụng NuGet là cách đơn giản nhất. 

1. Mở Bảng điều khiển Trình quản lý gói NuGet từ Công cụ > Trình quản lý gói NuGet > Bảng điều khiển Trình quản lý gói.
2. Chạy lệnh sau:

```powershell
Install-Package Aspose.Words
```

## Bước 3: Chuẩn bị thư mục tài liệu

Bạn sẽ cần một thư mục để lưu trữ các tài liệu và chứng chỉ Word của mình. Hãy tạo một thư mục.

1. Tạo một thư mục trên máy tính của bạn. Để đơn giản, chúng ta hãy gọi nó là "DocumentDirectory".
2. Đặt tài liệu Word (ví dụ: "Document.docx") và chứng chỉ .pfx (ví dụ: "morzal.pfx") của bạn vào thư mục này.

## Bước 4: Viết mã

Bây giờ, chúng ta hãy đi sâu vào mã. Mở `Program.cs` tập tin và bắt đầu bằng cách thiết lập đường dẫn đến thư mục tài liệu của bạn và khởi tạo `SignOptions` với mật khẩu giải mã.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## Bước 5: Tải chứng chỉ

Tiếp theo, tải chứng chỉ của bạn bằng cách sử dụng `CertificateHolder` lớp. Điều này sẽ yêu cầu đường dẫn đến tệp .pfx và mật khẩu chứng chỉ.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Bước 6: Ký tài liệu

Cuối cùng, sử dụng `DigitalSignatureUtil.Sign` phương pháp ký tài liệu Word được mã hóa của bạn. Phương pháp này yêu cầu tệp đầu vào, tệp đầu ra, chủ sở hữu chứng chỉ và các tùy chọn ký.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## Bước 7: Chạy mã

Lưu tệp của bạn và chạy dự án. Nếu mọi thứ được thiết lập đúng, bạn sẽ thấy tài liệu đã ký của mình trong thư mục đã chỉ định.

## Phần kết luận

Và bạn đã có nó! Bạn đã ký thành công một tài liệu Word được mã hóa bằng Aspose.Words cho .NET. Với thư viện mạnh mẽ này, việc ký kỹ thuật số trở nên dễ dàng, ngay cả đối với các tệp được mã hóa. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể sử dụng loại chứng chỉ khác không?
Có, Aspose.Words hỗ trợ nhiều loại chứng chỉ khác nhau, miễn là chúng có định dạng đúng.

### Có thể ký nhiều tài liệu cùng một lúc không?
Chắc chắn rồi! Bạn có thể lặp qua một tập hợp các tài liệu và ký từng tài liệu theo chương trình.

### Tôi phải làm sao nếu quên mật khẩu giải mã?
Thật không may, nếu không có mật khẩu giải mã, bạn sẽ không thể ký tài liệu.

### Tôi có thể thêm chữ ký trực quan vào tài liệu không?
Có, Aspose.Words cũng cho phép bạn thêm chữ ký số có thể nhìn thấy được.

### Có cách nào để xác minh chữ ký không?
Có, bạn có thể sử dụng `DigitalSignatureUtil.Verify` phương pháp xác minh chữ ký.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}