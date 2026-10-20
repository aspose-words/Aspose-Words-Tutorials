---
category: general
date: 2026-08-14
description: Học cách ký các tệp docx bằng chứng chỉ PFX. Hướng dẫn này bao gồm cài
  đặt PFX để ký tài liệu, các tùy chọn XAdES‑EPES và mã Java đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign docx
- sign document pfx
language: vi
lastmod: 2026-08-14
og_description: Cách ký tệp docx bằng chứng chỉ PFX. Hãy làm theo hướng dẫn này để
  thiết lập ký tài liệu pfx, áp dụng XAdES‑EPES và tạo tệp DOCX đã ký trong Java.
og_image_alt: Screenshot showing how to sign docx with a PFX certificate in Java
og_title: Cách ký tệp docx bằng chứng chỉ PFX – hướng dẫn đầy đủ
schemas:
- author: GroupDocs
  dateModified: '2026-08-14'
  description: Learn how to sign docx files using a PFX certificate. This tutorial
    covers sign document pfx setup, XAdES‑EPES options, and full Java code.
  headline: How to sign docx files with a PFX certificate – step‑by‑step guide
  type: TechArticle
- description: Learn how to sign docx files using a PFX certificate. This tutorial
    covers sign document pfx setup, XAdES‑EPES options, and full Java code.
  name: How to sign docx files with a PFX certificate – step‑by‑step guide
  steps:
  - name: Load the PFX certificate holder
    text: The signing SDK needs a wrapper that knows where the PFX file lives and
      what password protects it. The `CertificateHolder` class encapsulates this information.
  - name: Sign the document with default XML‑DSIG settings
    text: 'The first signature demonstrates the simplest scenario: a standard XML‑DSIG
      envelope. This is useful when you only need a basic integrity check.'
  - name: Configure XAdES‑EPES signature options
    text: XAdES‑EPES (Extended Advanced Electronic Signature – Explicit Policy‑Based
      Electronic Signature) adds policy information and stronger non‑repudiation guarantees.
      To use it, you must create a `SignatureOptions` instance and set the desired
      level.
  - name: Sign the document with XAdES‑EPES
    text: Now we apply the options created in the previous step. The overload of `sign`
      that accepts a `SignatureOptions` object lets you inject the policy.
  - name: Full runnable example
    text: Combine the pieces into a single `main` method so you can execute the workflow
      with one command.
  type: HowTo
tags:
- docx signing
- pfx certificate
- java
- digital signature
title: Cách ký file docx bằng chứng chỉ PFX – hướng dẫn từng bước
url: /vi/java/document-security/how-to-sign-docx-files-with-a-pfx-certificate-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách ký tệp docx bằng chứng chỉ PFX – hướng dẫn từng bước

Nếu bạn cần **how to sign docx** tệp một cách lập trình, hướng dẫn này sẽ cho bạn các bước chính xác. Bạn sẽ học cách **sign document pfx** tệp, cấu hình XAdES‑EPES, và tạo ra đầu ra DOCX có thể xác minh — tất cả bằng Java thuần.

Ký một tệp DOCX là yêu cầu phổ biến cho tự động hoá hợp đồng, tuân thủ pháp lý và trao đổi tài liệu an toàn. Khi kết thúc tutorial này, bạn sẽ có một ví dụ hoàn chỉnh, có thể chạy được, ký một tài liệu Word đầu vào hai lần — một lần với cài đặt XML‑DSIG mặc định và một lần với mức XAdES‑EPES mạnh hơn.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- Java 17 hoặc mới hơn (mã sử dụng cú pháp `var` hiện đại để ngắn gọn)
- Maven hoặc Gradle để quản lý các phụ thuộc
- Một tệp **PFX** (PKCS #12) hợp lệ chứa khóa riêng và chuỗi chứng chỉ của nó
- Thư viện GroupDocs.Signature cho Java (hoặc bất kỳ SDK ký nào tương thích). Ví dụ sử dụng tọa độ Maven `com.groupdocs:groupdocs-signature:23.5`.

Nếu bạn chưa có tệp PFX, bạn có thể tạo một tệp bằng OpenSSL:

```bash
openssl pkcs12 -export -out mycert.pfx -inkey private.key -in certificate.crt -certfile ca_bundle.crt
```

> **Mẹo chuyên nghiệp:** Bảo vệ PFX bằng mật khẩu mạnh và lưu trữ nó ngoài hệ thống kiểm soát nguồn.

## Cách ký docx bằng chứng chỉ PFX

Quy trình chính bao gồm bốn bước logic:

1. Tải tệp PFX vào một `CertificateHolder`.
2. Ký DOCX với cấu hình XML‑DSIG mặc định.
3. Định nghĩa các tùy chọn chữ ký XAdES‑EPES.
4. Ký lại DOCX bằng các tùy chọn đó.

Mỗi bước sẽ được giải thích dưới đây, và mã nguồn hoàn chỉnh sẽ theo sau các giải thích.

### Bước 1: Tải trình giữ chứng chỉ PFX

SDK ký cần một lớp bao bọc biết vị trí tệp PFX và mật khẩu bảo vệ nó. Lớp `CertificateHolder` đóng gói thông tin này.

```java
import com.groupdocs.signature.options.sign.SignatureOptions;
import com.groupdocs.signature.utils.DigitalSignatureUtil;
import com.groupdocs.signature.options.enumerations.SignatureType;
import com.groupdocs.signature.options.enumerations.XmlDsigLevel;
import com.groupdocs.signature.certificate.CertificateHolder;

public class DocxSigner {
    // Path to the PFX file and its password
    private static final String PFX_PATH = "YOUR_DIRECTORY/mycert.pfx";
    private static final String PFX_PASSWORD = "password";

    // Helper method to create a CertificateHolder
    private static CertificateHolder loadCertificate() {
        // The CertificateHolder reads the PFX file and prepares the private key for signing
        return new CertificateHolder(PFX_PATH, PFX_PASSWORD);
    }
}
```

**Tại sao điều này quan trọng:** SDK không thể truy cập trực tiếp vào khóa riêng; nó phải được tải qua một container an toàn. Sử dụng `CertificateHolder` cũng giúp trừu tượng hoá việc xử lý keystore theo nền tảng.

### Bước 2: Ký tài liệu với cài đặt XML‑DSIG mặc định

Chữ ký đầu tiên minh hoạ kịch bản đơn giản nhất: một phong bì XML‑DSIG tiêu chuẩn. Điều này hữu ích khi bạn chỉ cần kiểm tra tính toàn vẹn cơ bản.

```java
public static void signWithDefaultXmlDsig(CertificateHolder cert) throws Exception {
    String inputPath = "YOUR_DIRECTORY/input.docx";
    String outputPath = "YOUR_DIRECTORY/signed.docx";

    // The static sign method performs the actual signing operation.
    DigitalSignatureUtil.sign(
        inputPath,
        outputPath,
        cert,
        SignatureType.XML_DSIG   // Use the XML‑DSIG profile
    );

    System.out.println("Document signed with default XML‑DSIG: " + outputPath);
}
```

**Giải thích:** `DigitalSignatureUtil.sign` trừu tượng hoá việc thao tác XML mức thấp. Hằng số `SignatureType.XML_DSIG` thông báo cho thư viện tạo một chữ ký số XML tiêu chuẩn tuân thủ đặc tả W3C.

### Bước 3: Cấu hình các tùy chọn chữ ký XAdES‑EPES

XAdES‑EPES (Extended Advanced Electronic Signature – Explicit Policy‑Based Electronic Signature) bổ sung thông tin chính sách và bảo đảm không thể chối bỏ mạnh hơn. Để sử dụng, bạn phải tạo một thể hiện `SignatureOptions` và đặt mức mong muốn.

```java
private static SignatureOptions createXadesEpesOptions() {
    SignatureOptions options = new SignatureOptions();
    // XAdES‑EPES is the most commonly required level for regulated environments
    options.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
    return options;
}
```

**Tại sao chọn XAdES‑EPES?** Nhiều khung pháp lý (ví dụ, eIDAS ở EU) yêu cầu chữ ký nhúng chính sách ký. Mức EPES đáp ứng các yêu cầu này mà không gây tải nặng như chữ ký XAdES‑T (có timestamp) đầy đủ.

### Bước 4: Ký tài liệu với XAdES‑EPES

Bây giờ chúng ta áp dụng các tùy chọn đã tạo ở bước trước. Phương thức overload của `sign` nhận một đối tượng `SignatureOptions` cho phép bạn chèn chính sách.

```java
public static void signWithXadesEpes(CertificateHolder cert, SignatureOptions options) throws Exception {
    String inputPath = "YOUR_DIRECTORY/input.docx";
    String outputPath = "YOUR_DIRECTORY/signed_epes.docx";

    DigitalSignatureUtil.sign(
        inputPath,
        outputPath,
        cert,
        SignatureType.XML_DSIG, // Still XML‑DSIG, but with XAdES‑EPES policy
        options                 // Pass the configured options
    );

    System.out.println("Document signed with XAdES‑EPES: " + outputPath);
}
```

### Ví dụ đầy đủ có thể chạy

Kết hợp các phần lại thành một phương thức `main` duy nhất để bạn có thể thực thi quy trình chỉ bằng một lệnh.

```java
public class DocxSigner {
    private static final String PFX_PATH = "YOUR_DIRECTORY/mycert.pfx";
    private static final String PFX_PASSWORD = "password";

    public static void main(String[] args) {
        try {
            // Load the certificate holder (sign document pfx)
            CertificateHolder cert = new CertificateHolder(PFX_PATH, PFX_PASSWORD);

            // 1️⃣ Default XML‑DSIG signature
            signWithDefaultXmlDsig(cert);

            // 2️⃣ XAdES‑EPES signature
            SignatureOptions xadesOptions = createXadesEpesOptions();
            signWithXadesEpes(cert, xadesOptions);

            System.out.println("Both signatures created successfully.");
        } catch (Exception e) {
            System.err.println("Signing failed: " + e.getMessage());
            e.printStackTrace();
        }
    }

    // --- Methods from previous sections (omitted for brevity) ---
    // signWithDefaultXmlDsig, createXadesEpesOptions, signWithXadesEpes
}
```

**Kết quả mong đợi**

```
Document signed with default XML‑DSIG: YOUR_DIRECTORY/signed.docx
Document signed with XAdES‑EPES: YOUR_DIRECTORY/signed_epes.docx
Both signatures created successfully.
```

Mở `signed.docx` hoặc `signed_epes.docx` trong Microsoft Word → **File → Info → View Signatures** để xác minh rằng chữ ký số xuất hiện và được tin cậy (miễn là chuỗi chứng chỉ đã được cài đặt trên máy).

## Các câu hỏi thường gặp và các trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Nếu mật khẩu PFX sai thì sao?* | SDK ném ra một `InvalidKeyException`. Xác thực mật khẩu trước khi gọi `sign`. |
| *Tôi có thể ký cùng một DOCX nhiều lần không?* | Có. Mỗi lần gọi sẽ thêm một phần tử `<Signature>` mới. Lưu ý rằng kích thước tệp sẽ tăng lên với mỗi chữ ký. |
| *Có cần thêm chứng chỉ vào Windows Trusted Store không?* | Không cần cho việc xác minh trong Word, nhưng các trình xác thực bên ngoài (ví dụ, Adobe Acrobat) có thể yêu cầu chuỗi chứng chỉ được tin cậy. |
| *Cách ký một DOCX đã chứa chữ ký?* | SDK tự động nối thêm một phần tử chữ ký mới; không cần mã bổ sung. |
| *Nếu tôi cần dấu thời gian (XAdES‑T) thì sao?* | Thay `XmlDsigLevel.XADES_EPES` bằng `XmlDsigLevel.XADES_T` và cung cấp URL TSA trong `SignatureOptions`. |

## Các thực hành tốt nhất khi ký DOCX bằng chứng chỉ PFX

- **Lưu trữ PFX một cách an toàn** – sử dụng vault hoặc biến môi trường cho mật khẩu.  
- **Xác thực chuỗi chứng chỉ** trước khi ký để tránh lỗi tin cậy sau này.  
- **Ưu tiên XAdES‑EPES** cho các ngành được quy định; chỉ quay lại XML‑DSIG đơn giản khi tính tương thích là vấn đề.  
- **Ghi lại hoạt động ký** (tên tệp, thời gian, người ký) để tạo nhật ký kiểm toán.  
- **Kiểm tra xác minh** trên nhiều nền tảng (Word, LibreOffice, trình xác thực trực tuyến) để đảm bảo khả năng tương thích.

## Kết luận

Trong tutorial này bạn đã học **how to sign docx** bằng chứng chỉ **sign document pfx**, cách cấu hình XAdES‑EPES, và cách tạo hai chữ ký có thể xác minh với một chương trình Java duy nhất. Ví dụ hoàn chỉnh có thể sao chép vào bất kỳ dự án Maven hoặc Gradle nào, điều chỉnh đường dẫn đầu vào khác nhau, và mở rộng với dấu thời gian hoặc chính sách chữ ký tùy chỉnh.

Tiếp theo, hãy khám phá các chủ đề liên quan như **sign PDF with a PFX certificate**, **embed visible signature images**, hoặc **automate batch signing of multiple Word documents**. Những mở rộng này dựa trên cùng các khái niệm đã trình bày ở đây và sẽ tăng cường hơn nữa quy trình bảo mật tài liệu của bạn. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được minh họa trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Ký tài liệu Word](/words/english/net/programming-with-digital-signatures/sign-document/)
- [Ký tài liệu](/words/hindi/net/programming-with-digital-signatures/sign-document/)
- [Ký tài liệu](/words/spanish/net/programming-with-digital-signatures/sign-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}