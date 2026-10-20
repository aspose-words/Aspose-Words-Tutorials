---
category: general
date: 2026-10-20
description: Cấu hình mã hoá LoadOptions trong Java để đọc tài liệu đúng cách và thay
  đổi mã hoá tài liệu sang UTF-8 với Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: vi
lastmod: 2026-10-20
og_description: Cấu hình mã hóa LoadOptions trong Java để đảm bảo xử lý ký tự đúng
  và tìm hiểu cách thay đổi mã hóa tài liệu sang UTF-8 bằng Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Cấu hình mã hóa LoadOptions trong Java – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Cách cấu hình mã hóa LoadOptions trong Java
url: /vi/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách cấu hình mã hoá LoadOptions trong Java

Nếu bạn cần **cấu hình mã hoá LoadOptions** trong Java, hướng dẫn này sẽ chỉ cho bạn cách đặt bộ ký tự đúng và sau đó **thay đổi mã hoá tài liệu sang UTF-8** bằng Aspose.Words. Mã hoá đúng ngăn ngừa văn bản bị rối khi tải các tệp sử dụng các trang mã cũ như Big5, Shift_JIS hoặc Windows‑1252.

Bạn sẽ học cách:

* tạo một thể hiện `LoadOptions` với một mã hoá cụ thể,
* tải tài liệu nguồn sử dụng mã hoá đó,
* lưu tài liệu ở một mã hoá khác (UTF‑8) mà không mất dữ liệu,
* xác minh rằng việc chuyển đổi đã thành công.

Hướng dẫn giả định bạn đã có môi trường phát triển Java cơ bản và một giấy phép Aspose.Words for Java hợp lệ. Không cần công cụ bên ngoài nào.

## Yêu cầu

| Yêu cầu | Lý do quan trọng |
|-------------|----------------|
| Java 17 hoặc mới hơn | Cung cấp các tính năng ngôn ngữ hiện đại và hỗ trợ lâu dài. |
| Aspose.Words for Java (v23.9 hoặc mới hơn) | Lớp `LoadOptions` nằm trong thư viện này. |
| Một tài liệu nguồn được mã hoá bằng trang mã cũ (ví dụ: Big5) | Minh họa nhu cầu mã hoá tùy chỉnh. |
| Một IDE hoặc công cụ xây dựng (Maven/Gradle) | Giúp biên dịch và chạy ví dụ một cách dễ dàng. |

Thêm phụ thuộc Aspose.Words vào `pom.xml` của bạn nếu bạn dùng Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Cấu hình mã hoá LoadOptions

Bước đầu tiên là cho Aspose.Words biết bộ ký tự nào sẽ được mong đợi khi nó đọc tệp. Điều này được thực hiện bằng cách cấu hình đối tượng `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Tại sao điều này quan trọng:** Khi một tài liệu được lưu với mã hoá cũ, bộ tải mặc định giả định UTF‑8. Bằng cách đặt mã hoá một cách rõ ràng, bạn tránh được mojibake (các ký tự rối) và giữ nguyên văn bản gốc.

### Mẹo chuyên nghiệp
Nếu bạn không chắc tệp sử dụng mã hoá nào, có thể kiểm tra dấu byte‑order (BOM) hoặc hỏi nhà cung cấp tài liệu. Các mã hoá cũ phổ biến bao gồm `Big5`, `Shift_JIS` và `Windows-1252`.

## Tải tài liệu với các tùy chọn đã cấu hình

Bây giờ `LoadOptions` đã sẵn sàng, hãy tải tệp nguồn. Hàm khởi tạo nhận đường dẫn tệp và một thể hiện `LoadOptions` đảm bảo mã hoá tùy chỉnh được áp dụng.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Tại sao điều này quan trọng:** Đối tượng `Document` hiện chứa văn bản chính xác như trong tệp gốc, vì bộ tải đã tôn trọng trang mã Big5 mà bạn cung cấp.

## Thay đổi mã hoá tài liệu sang UTF-8

Aspose.Words lưu trữ văn bản nội bộ dưới dạng Unicode, vì vậy việc lưu tài liệu quyết định mã hoá bên ngoài. Để tạo tệp UTF‑8, chỉ cần lưu mà không chỉ định mã hoá bổ sung — UTF‑8 là mặc định cho các định dạng Office Open XML hiện đại. Tuy nhiên, bạn có thể ép buộc nó một cách rõ ràng để tăng tính minh bạch.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Nếu bạn cần tạo một bản biểu diễn dạng văn bản thuần (ví dụ, `.txt`) với UTF‑8, hãy truyền một đối tượng `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Tại sao điều này quan trọng:** Lưu dưới dạng UTF‑8 đảm bảo bất kỳ hệ thống nào phía sau — dịch vụ web, cơ sở dữ liệu, hoặc trình soạn thảo hiện đại — có thể đọc tệp mà không cần các bước chuyển đổi bổ sung.

## Xác minh việc chuyển đổi

Một cách nhanh để xác nhận rằng việc thay đổi mã hoá đã thành công là đọc lại tệp đã lưu bằng bộ đọc UTF‑8 và in ra một vài ký tự.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Nếu đầu ra hiển thị các ký tự có thể đọc được (không có ký hiệu �), việc chuyển đổi đã hoạt động như mong đợi.

## Ví dụ đầy đủ có thể chạy được

Dưới đây là một chương trình tự chứa đưa tất cả các bước lại với nhau. Thay thế các đường dẫn tệp bằng vị trí của bạn.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Kết quả mong đợi**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Nếu các ký tự hiển thị đúng, bạn đã thành công **cấu hình mã hoá LoadOptions** và **thay đổi mã hoá tài liệu sang UTF-8**.

## Các vấn đề thường gặp và cách tránh chúng

| Triệu chứng | Nguyên nhân | Cách khắc phục |
|---------|-------|-----|
| Ký tự rối sau khi tải | `LoadOptions` chưa được đặt hoặc tên charset sai | Đảm bảo `loadOptions.setEncoding(Charset.forName("Big5"))` khớp với trang mã của tệp nguồn. |
| `UnsupportedEncodingException` | Tên charset bị viết sai | Sử dụng đúng tên được liệt kê trong `Charset.availableCharsets()`. |
| Tệp đầu ra vẫn hiển thị mojibake | Lưu dưới dạng định dạng cũ (ví dụ, `.rtf`) mà không có tùy chọn UTF‑8 | Sử dụng `TxtSaveOptions` với `setEncoding("UTF-8")` hoặc lưu dưới dạng `.docx`. |
| Chậm hiệu suất trên các tệp lớn | Tạo lại `LoadOptions` cho mỗi tài liệu | Tái sử dụng một thể hiện `LoadOptions` duy nhất khi xử lý nhiều tệp có cùng mã hoá nguồn. |

## Kết luận

Bạn giờ đã biết cách **cấu hình mã hoá LoadOptions** trong Java để đọc các tài liệu được mã hoá bằng các trang mã cũ và cách **thay đổi mã hoá tài liệu sang UTF-8** để tiêu thụ an toàn ở các hệ thống phía sau. Cách tiếp cận này hoạt động với bất kỳ trang mã nào được Java `Charset` hỗ trợ, làm cho nó trở thành giải pháp linh hoạt cho các ứng dụng đa ngôn ngữ.

Tiếp theo, bạn có thể khám phá:

* **Chuyển đổi hàng loạt** – lặp qua một thư mục các tài liệu và áp dụng cùng một logic mã hoá.
* **Phát hiện mã hoá** – sử dụng các thư viện như juniversalchardet để tự động phát hiện charset nguồn trước khi cấu hình `LoadOptions`.
* **Bảo tồn định dạng** – thử lưu dưới dạng PDF hoặc HTML trong khi vẫn tuân thủ UTF‑8.

Hãy tự do điều chỉnh mã cho kiến trúc dự án của bạn, và để API mạnh mẽ của Aspose.Words thực hiện phần công việc nặng nhọc trong việc thao tác tài liệu.

![Code snippet showing configuration of LoadOptions encoding and document save](/images/encoding-demo.png){: .align-center alt="Configure LoadOptions encoding in Java code example"}

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách thiết lập LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cách chuyển đổi văn bản RTF với mã hoá UTF-8 trong Java bằng Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Khôi phục tài liệu Word DOCX bị hỏng bằng Aspose.Words LoadOptions – Hướng dẫn Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}