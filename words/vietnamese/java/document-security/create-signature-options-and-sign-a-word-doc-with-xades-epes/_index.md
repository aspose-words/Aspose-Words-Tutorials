---
category: general
date: 2026-10-10
description: Tạo các tùy chọn chữ ký và ký tài liệu Word bằng XAdES EPES trong Java.
  Học cách ký tài liệu Office bằng chứng chỉ trong một vài bước rõ ràng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: vi
lastmod: 2026-10-10
og_description: Tạo các tùy chọn chữ ký và ký tài liệu Word bằng XAdES EPES trong
  Java. Hướng dẫn này chỉ cho bạn cách ký tài liệu Office một cách an toàn bằng chứng
  chỉ.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Tạo các tùy chọn chữ ký và ký tài liệu Word bằng XAdES EPES
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Tạo các tùy chọn chữ ký và ký tài liệu Word bằng XAdES EPES
url: /vi/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo các tùy chọn chữ ký và ký tài liệu Word bằng XAdES EPES

Nếu bạn cần **tạo các tùy chọn chữ ký** cho tệp DOCX, hướng dẫn này sẽ chỉ cho bạn cách ký tài liệu Word bằng mức XAdES‑EPES trong Java. Bạn sẽ nhận được một ví dụ hoàn chỉnh, có thể chạy được, ký một tài liệu Office bằng chứng chỉ PFX chỉ trong vài dòng mã.

Ký tài liệu Office là một yêu cầu phổ biến cho quy trình làm việc pháp lý, xử lý hợp đồng tự động và trao đổi tài liệu an toàn. Trong hướng dẫn này, bạn sẽ học:

* Cách cấu hình `SignatureOptions` cho XAdES‑EPES.  
* Cách gọi `DigitalSignatureUtil.sign` để **ký tài liệu word**.  
* Cách xử lý các vấn đề thường gặp như tải chứng chỉ và lỗi mật khẩu.

> **Prerequisite** – Java 17 trở lên, thư viện GroupDocs.Signature for Java (hoặc một thư viện XAdES tương thích), và một tệp chứng chỉ `.pfx` hợp lệ.

## Những gì bạn sẽ cần

| Item | Reason |
|------|--------|
| Java 17+ | Các tính năng ngôn ngữ hiện đại và API bảo mật tốt hơn |
| GroupDocs.Signature for Java (or equivalent) | Cung cấp `SignatureOptions`, `XmlDsigLevel`, và `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Cung cấp khóa riêng cho chữ ký số |
| Password for the certificate | Cần thiết để mở khóa khóa riêng |
| An unsigned DOCX file (`Unsigned.docx`) | Tài liệu nguồn bạn muốn **ký tài liệu office** |

Make sure the library JAR is on your classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

## Bước 1: Nhập các lớp cần thiết

Bắt đầu bằng cách nhập các lớp xử lý chữ ký và I/O tệp.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Các import này cho phép bạn truy cập API dùng để **tạo các tùy chọn chữ ký** và thực hiện thao tác ký thực tế.

## Bước 2: Tạo các tùy chọn chữ ký

Đối tượng `SignatureOptions` chứa tất cả cấu hình cần thiết cho quá trình ký, chẳng hạn như mức chữ ký, giao diện hiển thị và cài đặt dấu thời gian.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Tạo một thể hiện `SignatureOptions` mới là bước đầu tiên trong **cách ký docx** vì nó tách biệt mỗi yêu cầu ký, ngăn ngừa các ảnh hưởng chéo giữa các tài liệu.

## Bước 3: Chỉ định mức chữ ký XAdES EPES

XAdES‑EPES (Electronic Signature dựa trên Chính sách Rõ ràng) là một chính sách được chấp nhận rộng rãi cho chữ ký tài liệu Office. Đặt mức này cho thư viện biết sẽ sử dụng hồ sơ mật mã nào.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Tại sao XAdES‑EPES? Nó nhúng chính sách ký trực tiếp vào chữ ký, làm cho tài liệu đã ký tự chứa và tuân thủ nhiều quy định về chữ ký điện tử.

## Bước 4: Ký tệp DOCX

Bây giờ gọi `DigitalSignatureUtil.sign`. Phương thức này đọc tệp nguồn, áp dụng chữ ký và ghi ra kết quả đã ký.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**Điều gì xảy ra bên trong?**  
1. Thư viện tải tệp `.pfx` và trích xuất khóa riêng bằng mật khẩu đã cung cấp.  
2. Nó tạo cấu trúc XML‑DSig phù hợp với hồ sơ XAdES‑EPES.  
3. Chữ ký được nhúng vào gói DOCX, giữ nguyên bố cục tài liệu gốc.  

Nếu mật khẩu chứng chỉ sai hoặc không thể đọc tệp, một `IOException` sẽ được ném ra, bạn nên xử lý như đã minh họa.

## Bước 5: Xác minh tài liệu đã ký (tùy chọn)

Sau khi ký, bạn có thể muốn xác nhận chữ ký đã có và hợp lệ. GroupDocs cung cấp API xác minh, nhưng có thể kiểm tra nhanh thủ công bằng Microsoft Word:

1. Mở `SignedXades.docx` trong Word.  
2. Nhấp **File → Info → View signatures**.  
3. Word sẽ hiển thị dấu kiểm màu xanh lá cây cho thấy chữ ký số hợp lệ.

Xác minh tự động bằng thư viện trông như sau:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Chạy bước xác minh sẽ cho bạn sự chắc chắn về mặt lập trình rằng **đã ký tài liệu office** thành công.

## Ví dụ đầy đủ, có thể chạy

Kết hợp tất cả các phần lại, đây là một lớp Java tự chứa mà bạn có thể sao chép, dán và chạy.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Kết quả mong đợi**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Nếu có bất kỳ lỗi nào, console sẽ hiển thị thông báo lỗi rõ ràng, giúp bạn khắc phục vấn đề chứng chỉ hoặc đường dẫn tệp.

## Các câu hỏi thường gặp và xử lý trường hợp biên

| Question | Answer |
|----------|--------|
| **Tôi có thể sử dụng mức chữ ký khác không?** | Có. Thay `XmlDsigLevel.XAdES_EPES` bằng `XAdES_BES`, `XAdES_T`, v.v., tùy theo nhu cầu tuân thủ. |
| **Nếu chứng chỉ của tôi được lưu trong keystore thay vì tệp .pfx thì sao?** | Tải `KeyStore` thủ công, trích xuất `PrivateKey` và `Certificate`, sau đó truyền chúng vào một overload của `sign` chấp nhận đối tượng `KeyStore`. |
| **Làm thế nào để thêm hình ảnh chữ ký hiển thị?** | Sử dụng `signatureOptions.setSignatureImage("path/to/image.png")` trước khi gọi `sign`. |
| **Quá trình ký có an toàn với đa luồng không?** | Phương thức `DigitalSignatureUtil.sign` không giữ trạng thái; bạn có thể gọi nó an toàn từ nhiều luồng miễn là mỗi luồng sử dụng một thể hiện `SignatureOptions` riêng. |
| **Nếu DOCX chứa các chữ ký hiện có thì sao?** | Thư viện sẽ thêm một mục gói chữ ký mới, giữ lại các chữ ký trước. Kiểm tra rằng chính sách ký cho phép nhiều chữ ký nếu cần. |

## Mẹo và thực tiễn tốt nhất (E‑E‑A‑T)

* **Mẹo chuyên nghiệp:** Lưu mật khẩu chứng chỉ của bạn trong một kho bảo mật (ví dụ, Azure Key Vault) thay vì mã cứng trong code.  
* **Cẩn thận với:** Dấu phân cách đường dẫn trên Windows (`\`) so với Unix (`/`). Sử dụng `Paths.get(...)` để xây dựng đường dẫn độc lập nền tảng.  
* **Hiệu năng:** Ký các tệp DOCX lớn có thể bị giới hạn bởi I/O; cân nhắc streaming tệp đầu vào nếu bạn xử lý nhiều tài liệu hàng loạt.  
* **Tuân thủ:** XAdES‑EPES tuân thủ quy định EU eIDAS; hãy kiểm tra yêu cầu pháp lý địa phương trước khi chọn mức chữ ký.

## Kết luận

Trong hướng dẫn này, bạn đã học cách **tạo các tùy chọn chữ ký** và **ký tài liệu Word** bằng mức XAdES‑EPES sử dụng Java. Ví dụ đầy đủ bao gồm tải chứng chỉ, cấu hình tùy chọn, gọi hàm ký và xác minh tùy chọn, cung cấp cho bạn giải pháp sẵn sàng sử dụng cho **cách ký docx** trong môi trường sản xuất.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tùy chọn tải trong Java – Phát hiện phông chữ thiếu & Cách tải DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Sử dụng tùy chọn và cài đặt tài liệu trong Aspose.Words cho Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Cách tạo vùng có thể chỉnh sửa trong tài liệu chỉ đọc bằng Aspose.Words cho Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}