---
title: Đặt ID Nhà cung cấp chữ ký trong Tài liệu Word
linktitle: Đặt ID Nhà cung cấp chữ ký trong Tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Thiết lập an toàn ID Nhà cung cấp chữ ký trong tài liệu Word bằng Aspose.Words cho .NET. Làm theo hướng dẫn chi tiết dài 2000 từ của chúng tôi để ký kỹ thuật số cho tài liệu của bạn.
weight: 10
url: /vi/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt ID Nhà cung cấp chữ ký trong Tài liệu Word

## Giới thiệu

Xin chào! Vậy là bạn đã có tài liệu Word tuyệt vời này cần chữ ký số, đúng không? Nhưng không phải bất kỳ chữ ký nào—bạn cần phải thiết lập một ID Nhà cung cấp chữ ký cụ thể. Cho dù bạn đang xử lý các tài liệu pháp lý, hợp đồng hay bất kỳ giấy tờ nào, thì việc thêm chữ ký số an toàn là rất quan trọng. Trong hướng dẫn này, tôi sẽ hướng dẫn bạn toàn bộ quy trình thiết lập ID Nhà cung cấp chữ ký trong tài liệu Word bằng Aspose.Words cho .NET. Sẵn sàng chưa? Hãy cùng bắt đầu nhé!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1. Aspose.Words cho Thư viện .NET: Nếu bạn chưa có,[tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Visual Studio hoặc bất kỳ IDE nào tương thích với C#.
3. Tài liệu Word: Một tài liệu có dòng chữ ký (`Signature line.docx`).
4.  Chứng chỉ số: A`.pfx` tập tin chứng chỉ (ví dụ,`morzal.pfx`).
5. Kiến thức cơ bản về C#: Chỉ cần những điều cơ bản—đừng lo, chúng tôi ở đây để giúp bạn!

Bây giờ, chúng ta hãy cùng bắt tay vào hành động nhé!

## Nhập không gian tên

Trước tiên, hãy đảm bảo bạn bao gồm các không gian tên cần thiết trong dự án của mình. Điều này rất cần thiết để truy cập thư viện Aspose.Words và các lớp liên quan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

Được rồi, chúng ta hãy chia nhỏ vấn đề này thành các bước đơn giản, dễ hiểu.

## Bước 1: Tải tài liệu Word của bạn

Bước đầu tiên là tải tài liệu Word có chứa dòng chữ ký. Tài liệu này sẽ được sửa đổi để bao gồm chữ ký số với ID Nhà cung cấp chữ ký đã chỉ định.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 Ở đây, chúng tôi chỉ định thư mục nơi tài liệu của bạn được lưu trữ. Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến tài liệu của bạn.

## Bước 2: Truy cập vào Dòng chữ ký

Tiếp theo, chúng ta cần truy cập vào dòng chữ ký trong tài liệu. Dòng chữ ký được nhúng dưới dạng đối tượng hình dạng trong tài liệu Word.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 Dòng mã này lấy hình dạng đầu tiên trong phần thân của phần đầu tiên của tài liệu và chuyển nó thành một`SignatureLine` sự vật.

## Bước 3: Thiết lập tùy chọn dấu hiệu

Bây giờ, chúng ta tạo các tùy chọn ký hiệu, bao gồm ID nhà cung cấp và ID dòng chữ ký từ dòng chữ ký đã truy cập.

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

Các tùy chọn này sẽ được sử dụng khi ký tài liệu để đảm bảo ID Nhà cung cấp chữ ký được thiết lập chính xác.

## Bước 4: Tải chứng chỉ

 Để ký tài liệu kỹ thuật số, bạn cần có chứng chỉ. Sau đây là cách bạn tải`.pfx` tài liệu:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Thay thế`"aw"` bằng mật khẩu cho tệp chứng chỉ của bạn nếu có.

## Bước 5: Ký vào tài liệu

 Cuối cùng, đã đến lúc ký tài liệu bằng cách sử dụng`DigitalSignatureUtil.Sign` phương pháp.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 Điều này sẽ ký tài liệu của bạn và lưu nó dưới dạng một tệp mới,`Digitally signed.docx`.

## Phần kết luận

Và bạn đã có nó! Bạn đã thiết lập thành công ID Nhà cung cấp chữ ký trong tài liệu Word bằng Aspose.Words cho .NET. Quy trình này không chỉ bảo mật tài liệu của bạn mà còn đảm bảo chúng tuân thủ các tiêu chuẩn chữ ký số. Bây giờ, hãy tiếp tục và thử nghiệm với tài liệu của bạn. Bạn có thắc mắc nào không? Hãy xem Câu hỏi thường gặp bên dưới hoặc truy cập[Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/words/8).

## Câu hỏi thường gặp

### ID Nhà cung cấp chữ ký là gì?

ID Nhà cung cấp chữ ký xác định duy nhất nhà cung cấp chữ ký số, đảm bảo tính xác thực và bảo mật.

### Tôi có thể sử dụng bất kỳ tệp .pfx nào để ký không?

Có, miễn là đó là chứng chỉ số hợp lệ. Đảm bảo bạn có mật khẩu đúng nếu chứng chỉ được bảo vệ.

### Làm thế nào để có được tệp .pfx?

Bạn có thể lấy tệp .pfx từ Cơ quan cấp chứng chỉ (CA) hoặc tạo tệp này bằng các công cụ như OpenSSL.

### Tôi có thể ký nhiều tài liệu cùng một lúc không?

Có, bạn có thể lặp qua nhiều tài liệu và áp dụng cùng một quy trình ký cho từng tài liệu.

### Tôi phải làm sao nếu tài liệu của tôi không có dòng chữ ký?

Trước tiên, bạn cần chèn dòng chữ ký. Aspose.Words cung cấp các phương pháp để thêm dòng chữ ký theo chương trình.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
