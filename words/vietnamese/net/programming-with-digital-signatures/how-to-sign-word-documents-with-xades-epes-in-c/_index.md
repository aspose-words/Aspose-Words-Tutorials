---
category: general
date: 2026-09-08
description: Cách ký tài liệu Word bằng quy trình chữ ký số docx, tải chứng chỉ pfx
  và tạo chữ ký XAdES trong C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: vi
lastmod: 2026-09-08
og_description: Cách ký tài liệu Word bằng quy trình chữ ký số docx, tải chứng chỉ
  pfx và tạo chữ ký XAdES trong C#. Tham khảo ví dụ đầy đủ.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Cách ký tài liệu Word bằng XAdES EPES trong C# – hướng dẫn từng bước
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: Cách ký tài liệu Word bằng XAdES EPES trong C#
url: /vi/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách ký tài liệu Word bằng XAdES EPES trong C#

Nếu bạn cần **how to sign word** các tệp một cách lập trình, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất. Bạn sẽ học cách tải chứng chỉ PFX, cấu hình một digital signature docx, và tạo một chữ ký XAdES‑EPES có thể được Microsoft Word và các công cụ xác thực bên thứ ba kiểm tra.

Ví dụ sử dụng thư viện GroupDocs.Signature cho .NET, nhưng các khái niệm áp dụng cho bất kỳ API nào hỗ trợ XAdES. Khi kết thúc tutorial, bạn sẽ có một tệp `Signed_XAdES_EPES.docx` đã ký sẵn, sẵn sàng để phân phối.

## Những gì bạn cần

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Tệp chứng chỉ PFX hợp lệ (`.pfx`) chứa khóa riêng
- Mật khẩu cho tệp PFX
- Tài liệu Word (`.docx`) mà bạn muốn ký
- Gói NuGet **GroupDocs.Signature** (cài đặt bằng `dotnet add package GroupDocs.Signature`)

## Bước 1: Cài đặt gói NuGet cần thiết

```bash
dotnet add package GroupDocs.Signature
```

Gói này cung cấp lớp `Document`, `XadesSignatureOptions`, và các kiểu trợ giúp để tạo một tệp **digitally sign word**.

## Bước 2: Tải tài liệu Word chưa ký

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Việc tải tài liệu sẽ cung cấp cho bạn một mô hình đối tượng mà bạn có thể thao tác trước khi áp dụng chữ ký.

## Bước 3: Tải chứng chỉ PFX (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Pro tip:** Nếu chứng chỉ được lưu trong Windows certificate store, bạn có thể lấy nó bằng `X509Store` thay vì tải tệp. Cách `load pfx certificate` hoạt động trên mọi nền tảng, bao gồm cả container Linux.

## Bước 4: (Tùy chọn) Thêm dòng chữ ký trực quan

Một chỉ dẫn trực quan giúp người nhận thấy vị trí chữ ký xuất hiện trong Word.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Nếu bạn muốn chữ ký ẩn, có thể bỏ qua bước này. **digital signature docx** vẫn sẽ hợp lệ về mặt mật mã.

## Bước 5: Cấu hình tùy chọn XAdES‑EPES (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

Cờ `XadesSignatureType.XAdES_EPES` chỉ cho thư viện nhúng chữ ký theo hồ sơ EPES (Explicit Policy-based Electronic Signature), được chấp nhận rộng rãi trong các quy định EU e‑IDAS.

## Bước 6: Áp dụng chữ ký số

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

Phương thức `Sign` thực hiện toàn bộ công việc mật mã: tính hàm băm cho các phần của tài liệu, tạo cấu trúc XML‑DSig, và chèn phong bì XAdES vào tệp Word.

## Bước 7: Lưu tài liệu đã ký

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Sau khi lưu, mở `Signed_XAdES_EPES.docx` trong Microsoft Word. Bạn sẽ thấy một dòng chữ ký (nếu bạn đã thêm) và thanh trạng thái **digitally sign word** cho biết tệp đã được ký và chữ ký hợp lệ.

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Kết quả mong đợi

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Mở tệp trong Word sẽ hiển thị biểu ngữ màu xanh lá “Signed” và, nếu bạn đã thêm dòng trực quan, dòng chữ ký sẽ xuất hiện ở vị trí bạn đã chỉ định.

## Xử lý các vấn đề thường gặp

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Certificate password is wrong** | Constructor `X509Certificate2` ném ra `CryptographicException`. | Xác minh mật khẩu, hoặc sử dụng trình quản lý bí mật an toàn (Azure Key Vault, AWS Secrets Manager). |
| **Word shows “Signature is invalid”** | Tài liệu đã bị thay đổi sau khi ký, hoặc chính sách ký không có. | Đảm bảo tệp được lưu **sau** khi ký và không chỉnh sửa lại. Nhúng chính sách XAdES đúng nếu yêu cầu của cơ quan quản lý. |
| **Signature line not visible** | Tài liệu sử dụng bố cục phần khác. | Thêm `SignatureLine` vào đoạn văn đúng hoặc tạo một đoạn mới trước khi thêm. |
| **Performance slowdown on large docs** | Chữ ký XAdES băm mọi phần của gói. | Sử dụng API streaming (`SignAsync`) hoặc tăng tài nguyên máy cho các tệp rất lớn (>50 MB). |

## Mở rộng giải pháp

- **Multiple signers** – gọi `Sign` nhiều lần với các chứng chỉ khác nhau và đặt `SignatureId` để phân biệt mỗi người ký.
- **Timestamping** – thêm đối tượng `TimestampOptions` vào `XadesSignatureOptions` để nhúng dấu thời gian tin cậy.
- **Custom policies** – cung cấp tệp chính sách XML qua `XadesSignatureOptions.PolicyFilePath` để tuân thủ các tiêu chuẩn cụ thể.

## Kết luận

Bạn giờ đã biết **how to sign word** tài liệu một cách lập trình, cách **load pfx certificate**, và cách **create xades signature** bằng GroupDocs.Signature. Tutorial đã bao phủ mọi bước từ tải tài liệu đến lưu kết quả đã ký, kèm theo các mẹo thực tế cho các trường hợp thường gặp.  

Tiếp theo, khám phá các chủ đề liên quan như PDF **digitally sign word**, tích hợp xác thực **digital signature docx**, hoặc thêm hỗ trợ **timestamp** để đáp ứng các yêu cầu tuân thủ nâng cao. Chúc bạn ký thành công!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}