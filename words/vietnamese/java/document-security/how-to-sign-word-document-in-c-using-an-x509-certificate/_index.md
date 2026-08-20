---
category: general
date: 2026-08-20
description: Tìm hiểu cách ký tài liệu Word bằng chữ ký số cho các tệp hợp đồng. Hướng
  dẫn này bao gồm việc tải chứng chỉ x509 từ tệp PFX và tạo chữ ký.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word document
- load x509 certificate
- digital signature for contract
- how to sign document
- load certificate from pfx
language: vi
lastmod: 2026-08-20
og_description: Ký tài liệu Word bằng chữ ký số cho các tệp hợp đồng. Thực hiện theo
  hướng dẫn từng bước này để tải chứng chỉ từ PFX và tạo chữ ký XAdES EPES.
og_image_alt: Diagram showing how to sign word document using an X509 certificate
og_title: Ký tài liệu Word bằng C# – tải chứng chỉ X509 và áp dụng chữ ký số
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to sign word document with a digital signature for contract
    files. This guide covers loading x509 certificate from a PFX and creating the
    signature.
  headline: How to sign word document in C# using an X509 certificate
  type: TechArticle
tags:
- digital signature
- C#
- X509Certificate2
title: Cách ký tài liệu Word trong C# bằng chứng chỉ X509
url: /vi/java/document-security/how-to-sign-word-document-in-c-using-an-x509-certificate/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách ký tài liệu Word trong C# bằng chứng thư X509

Nếu bạn cần **ký tài liệu Word** một cách lập trình, hướng dẫn này sẽ cung cấp cho bạn một giải pháp hoàn chỉnh, có thể chạy ngay. Bạn sẽ học cách **tải chứng thư x509** từ tệp *.pfx*, cấu hình mức ký, và tạo một chữ ký XML tuân chuẩn mà có thể đính kèm vào hợp đồng.  

Các bước dưới đây hoạt động với .NET 6+ và thư viện miễn phí GroupDocs.Signature for .NET, thư viện này trừu tượng hoá các chi tiết XML‑DSig ở mức thấp trong khi vẫn cho bạn kiểm soát toàn bộ quá trình ký.

## Yêu cầu trước

- .NET 6 SDK hoặc phiên bản mới hơn đã được cài đặt  
- Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ .NET)  
- Một chứng thư X509 hợp lệ ở định dạng **PFX** (`certificate.pfx`) với mật khẩu đã biết  
- Gói NuGet `GroupDocs.Signature` (cài đặt bằng `dotnet add package GroupDocs.Signature`)  

> **Tại sao cần những yêu cầu này?**  
> Lớp `X509Certificate2` chỉ có thể đọc PFX khi khóa riêng có thể xuất ra, và GroupDocs.Signature xử lý mức XAdES EPES cần thiết cho nhiều **digital signature for contract**.

## Bước 1: Tải chứng thư ký (load x509 certificate)

```csharp
using System.Security.Cryptography.X509Certificates;

// Replace with the actual path to your PFX file and its password
string certPath = @"C:\Certificates\certificate.pfx";
string certPassword = "yourPassword";

// Load the certificate that contains the private key
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
    X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);
```

**Giải thích**  
`X509Certificate2` đọc **load certificate from pfx** và cung cấp khóa riêng để ký. Các cờ đảm bảo khóa được lưu trong kho máy, tránh các vấn đề quyền trên các dịch vụ Windows.

**Mẹo:** Nếu bạn gặp `CryptographicException` liên quan tới quyền truy cập khóa, hãy kiểm tra tài khoản chạy mã có quyền đọc tệp PFX và khóa đã được đánh dấu là có thể xuất ra.

## Bước 2: Khởi tạo SignatureHelper và gán chứng thư

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

// Create the helper that will perform the signing
SignatureHelper signer = new SignatureHelper();

// Attach the previously loaded certificate
signer.SetCertificate(certificate);
```

**Giải thích**  
`SignatureHelper` là một lớp bọc nhẹ quanh GroupDocs.Signature giúp đơn giản hoá quy trình. Khi gọi `SetCertificate`, bạn thông báo cho thư viện khóa riêng nào sẽ được dùng cho thao tác **how to sign document**.

## Bước 3: Chọn mức ký XAdES (digital signature for contract)

```csharp
// XAdES_EPES is commonly required for contract signing because it embeds
// the signing certificate and timestamp information directly in the XML.
signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

**Giải thích**  
XAdES‑EPES (Explicit Policy‑Based Electronic Signature) đáp ứng hầu hết các yêu cầu pháp lý cho một **digital signature for contract**. Thư viện sẽ tự động tạo các phần tử `<QualifyingProperties>` cần thiết.

## Bước 4: Tải tài liệu Word sẽ được ký

```csharp
using GroupDocs.Signature.Domain;

// The document you want to sign – a .docx contract, for example
string docPath = @"C:\Contracts\contract.docx";
Document document = new Document(docPath);
```

**Giải thích**  
`Document` đại diện cho tệp Word trong bộ nhớ. Nó có thể là bất kỳ tệp `.docx` nào; cùng một đoạn mã cũng hoạt động cho PDF hoặc các định dạng OpenXML khác nếu bạn thay đổi phần mở rộng tệp.

## Bước 5: Tạo tệp chữ ký XML

```csharp
// Destination for the generated XML signature
string signaturePath = @"C:\Contracts\signature.xml";

// Perform the signing operation
signer.SignDocument(document, signaturePath);

// Optional: verify that the file was created
if (System.IO.File.Exists(signaturePath))
{
    Console.WriteLine($"Signature saved to: {signaturePath}");
}
```

**Giải thích**  
`SignDocument` tạo một tệp XML tuân theo hồ sơ XAdES EPES. Tệp `signature.xml` kết quả có thể được gửi cùng với tệp Word gốc hoặc nhúng sau này bằng một phần XML tùy chỉnh.

**Kết quả mong đợi**

```
Signature saved to: C:\Contracts\signature.xml
```

Tệp XML sẽ chứa các phần tử như `<Signature>`, `<SignedInfo>` và `<X509Data>` tham chiếu tới **load x509 certificate** đã tải.

## Ví dụ đầy đủ, có thể chạy

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;

class Program
{
    static void Main()
    {
        // 1. Load the signing certificate (load x509 certificate)
        string certPath = @"C:\Certificates\certificate.pfx";
        string certPassword = "yourPassword";
        X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
            X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);

        // 2. Initialize the SignatureHelper and assign the certificate
        SignatureHelper signer = new SignatureHelper();
        signer.SetCertificate(certificate);

        // 3. Set the XAdES signature level (digital signature for contract)
        signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 4. Load the Word document that will be signed
        string docPath = @"C:\Contracts\contract.docx";
        Document document = new Document(docPath);

        // 5. Generate the XML signature file
        string signaturePath = @"C:\Contracts\signature.xml";
        signer.SignDocument(document, signaturePath);

        // Confirmation
        Console.WriteLine(File.Exists(signaturePath)
            ? $"Signature saved to: {signaturePath}"
            : "Failed to create signature file.");
    }
}
```

Lưu tệp dưới tên `Program.cs`, chạy `dotnet run`, và bạn sẽ nhận được một tệp XML đã ký, sẵn sàng cho việc xác thực pháp lý.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Cần thay đổi | Lý do |
|----------|--------------|-------|
| **Ký PDF thay vì Word** | Thay `Document` bằng `PdfDocument` và điều chỉnh phần mở rộng tệp. | GroupDocs.Signature hỗ trợ nhiều định dạng; quy trình ký vẫn giống nhau. |
| **Sử dụng chứng thư từ Windows Store** | Tải chứng thư qua `X509Store` thay vì tệp PFX. | Hữu ích khi khóa riêng không bao giờ rời máy, đáp ứng yêu cầu tuân thủ. |
| **Thêm dấu thời gian** | Gọi `signer.SetTimestampProvider(new Rfc3161TimestampProvider(url))`. | Nhiều quy trình hợp đồng yêu cầu dấu thời gian tin cậy để chứng minh thời điểm ký. |
| **Nhúng chữ ký vào trong .docx** | Dùng `signer.SignDocument(document, signaturePath, new XmlSignatureOptions { EmbedIntoDocument = true })`. | Nhúng giúp đơn giản hoá việc phân phối vì chỉ cần một tệp duy nhất. |

## Mẹo cho môi trường sản xuất

- **Bảo mật PFX** – lưu trữ trong Azure Key Vault hoặc AWS Secrets Manager thay vì hệ thống tệp.  
- **Xác thực chuỗi chứng thư** trước khi ký để đảm bảo người ký được tin cậy.  
- **Ghi log hoạt động ký** (thumbprint chứng thư, hash tài liệu, dấu thời gian) để tạo chuỗi kiểm tra theo yêu cầu của hầu hết các chính sách **digital signature for contract**.  

## Kết luận

Bây giờ bạn đã biết cách **ký tài liệu Word** một cách lập trình, cách **tải x509 certificate** từ tệp PFX, và cách tạo một **digital signature for contract** tuân chuẩn. Ví dụ bao quát toàn bộ quy trình **how to sign document**, từ tải chứng thư đến tạo chữ ký, và bao gồm các biến thể thường gặp trong các dự án thực tế.

**Bước tiếp theo**

- Khám phá các mức ký khác như XAdES‑T hoặc XAdES‑LT để có thời gian hiệu lực dài hơn.  
- Thử nhúng chữ ký XML trực tiếp vào tệp Word bằng tùy chọn `EmbedIntoDocument`.  
- Tích hợp logic xác thực (`signer.VerifyDocument`) để kiểm tra chữ ký trên các hợp đồng đến.

Hãy tùy chỉnh mã nguồn cho cấu trúc dự án của bạn và chúc bạn ký thành công!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập tới các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}