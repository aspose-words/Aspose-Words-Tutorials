---
category: general
date: 2026-10-26
description: Tìm hiểu cách chỉ định mã hoá trong Java bằng LoadOptions. Hướng dẫn
  này bao gồm mã ký tự, phương thức setEncoding và các tùy chọn tải tài liệu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: vi
lastmod: 2026-10-26
og_description: Cách chỉ định mã hóa trong Java bằng Aspose.Words. Theo dõi hướng
  dẫn đầy đủ này để tải tài liệu với bộ ký tự đúng.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Cách chỉ định mã hoá trong Java với Aspose.Words – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Cách chỉ định mã hóa khi tải tài liệu bằng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chỉ định mã hoá khi tải tài liệu bằng Aspose.Words cho Java

Nếu bạn cần **cách chỉ định mã hoá** cho một tệp nguồn trong Java, hướng dẫn này sẽ cho bạn các bước cụ thể. Cho dù tài liệu sử dụng Big5, UTF‑8, hay một bộ ký tự khác, bạn có thể kiểm soát quá trình đọc bằng `LoadOptions`. Khi kết thúc hướng dẫn, bạn sẽ hiểu tại sao mã hoá ký tự quan trọng, cách áp dụng phương thức `setEncoding`, và cách xác minh tài liệu được tải đúng.

Việc tải tài liệu với mã hoá ký tự đúng ngăn ngừa văn bản bị rối và đảm bảo nội dung đa ngôn ngữ hiển thị như mong muốn. Hướng dẫn này bao gồm:

* Vai trò của **character encoding in Java** khi đọc tệp.
* Cách cấu hình **LoadOptions encoding** cho Aspose.Words.
* Mã thực tế mà bạn có thể sao chép vào dự án.
* Những lỗi thường gặp như mã hoá không khớp và cách khắc phục chúng.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java Development Kit (JDK) 8 trở lên.
* Maven hoặc Gradle để quản lý phụ thuộc.
* Aspose.Words for Java 23.10 hoặc mới hơn (phiên bản được sử dụng trong hướng dẫn này).
* Một tài liệu văn bản mẫu (`input.doc`) được lưu với mã hoá mong muốn (ví dụ: Big5).

Bạn không cần bất kỳ thư viện bổ sung nào; ví dụ chỉ sử dụng core API của Aspose.Words.

## Bước 1: Thêm Aspose.Words vào dự án của bạn

Nếu bạn dùng Maven, thêm phụ thuộc sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Đối với Gradle, đặt dòng này vào `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Việc bao gồm thư viện sẽ làm cho các lớp `LoadOptions`, `Document` và `Encoding` khả dụng.

## Bước 2: Tạo một thể hiện `LoadOptions`

`LoadOptions` cho phép bạn tùy chỉnh cách Aspose.Words mở một tệp. Tạo đối tượng này là phần đầu tiên của **cách chỉ định mã hoá**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

Đối tượng `LoadOptions` ban đầu có các thiết lập mặc định. Bạn sẽ điều chỉnh các thuộc tính của nó trong bước tiếp theo.

## Bước 3: Đặt mã hoá ký tự mong muốn

Phương thức `setEncoding` xác định **character encoding in Java** mà bộ tải sẽ sử dụng. Trong ví dụ này chúng ta chọn trang mã Big5, thường dùng cho các tệp văn bản tiếng Trung truyền thống.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Lý do quan trọng*: Nếu các byte của tệp được giải mã bằng trang mã sai, ký tự sẽ hiển thị dưới dạng dấu hỏi hoặc ký tự rác. Bằng cách gọi `setEncoding` một cách rõ ràng, bạn nói với Aspose.Words giải mã luồng byte bằng bảng ánh xạ Big5.

Bạn có thể thay `"Big5"` bằng bất kỳ tên charset nào mà Java nhận diện, chẳng hạn `"UTF-8"`, `"ISO-8859-1"` hoặc `"Windows-1252"`. Phương thức sẽ ném `UnsupportedEncodingException` nếu tên không hợp lệ, vì vậy bạn nên bắt ngoại lệ này trong mã sản xuất.

## Bước 4: Tải tài liệu với các tùy chọn đã cấu hình

Bây giờ **LoadOptions encoding** đã được đặt, hãy truyền các tùy chọn này vào hàm khởi tạo `Document`. Bước này hoàn thành quy trình **cách chỉ định mã hoá** cốt lõi.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối tới tệp của bạn. Thực thể `Document` hiện chứa nội dung đã được phân tích đầy đủ, tuân theo mã hoá bạn cung cấp.

## Bước 5: Xác minh văn bản được tải đúng

Một bước kiểm tra nhanh giúp bạn chắc chắn rằng mã hoá đã được áp dụng như mong đợi. Bạn có thể trích xuất văn bản của tài liệu và in ra console:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Nếu console hiển thị các ký tự tiếng Trung có thể đọc được (hoặc ngôn ngữ bạn mong đợi), việc mã hoá đã thành công. Nếu vẫn thấy đầu ra rối, hãy kiểm tra lại mã hoá của tệp gốc và xác nhận rằng tên charset khớp chính xác.

## Xử lý các trường hợp đặc biệt thường gặp

### 5.1 Tải từ `InputStream`

Đôi khi bạn nhận được tài liệu dưới dạng luồng (ví dụ, từ một dịch vụ web). Bạn vẫn có thể kiểm soát mã hoá bằng cách truyền luồng cùng với `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Các **document loading options** vẫn áp dụng, và lời gọi `setEncoding` không thay đổi.

### 5.2 Phương án dự phòng khi không biết mã hoá

Nếu bạn không thể xác định charset của tệp nguồn, có thể sử dụng thư viện phát hiện (như ICU4J) trước khi đặt mã hoá. Khi đã có dự đoán, gọi `setEncoding` với giá trị đó. Cách này giảm nguy cơ văn bản bị giải mã sai.

### 5.3 Xử lý các mã hoá không được hỗ trợ

Java hỗ trợ một loạt các trang mã, nhưng một số mã hoá cũ có thể thiếu. Trong trường hợp đó, hãy cân nhắc chuyển đổi tệp sang UTF‑8 bên ngoài (ví dụ, dùng `iconv`) trước khi tải bằng Aspose.Words. Sau khi chuyển đổi, bạn có thể bỏ qua lời gọi `setEncoding` vì UTF‑8 là mặc định cho hầu hết các API hiện đại.

## Mẹo chuyên nghiệp: Tái sử dụng `LoadOptions` cho xử lý hàng loạt

Nếu bạn cần tải nhiều tài liệu có cùng charset, hãy tạo một thể hiện `LoadOptions` duy nhất và tái sử dụng nó:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Việc tái sử dụng đối tượng giảm chi phí tạo đối tượng và đảm bảo mã hoá nhất quán trong toàn bộ batch.

## Ví dụ hoàn chỉnh có thể chạy

Dưới đây là chương trình đầy đủ tích hợp tất cả các bước, bao gồm các import cần thiết và xử lý ngoại lệ tiềm năng.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Kết quả mong đợi** (giả sử tệp nguồn chứa văn bản tiếng Trung được mã hoá bằng Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Nếu đầu ra hiển thị các ký hiệu không đọc được, hãy xem lại tên charset hoặc xác nhận lại mã hoá gốc của tệp.

## Câu hỏi thường gặp

**Liệu cách này có hoạt động với các định dạng tài liệu khác (DOCX, RTF, HTML)?**  
Có. Đối tượng `LoadOptions` giống nhau áp dụng cho bất kỳ định dạng nào được Aspose.Words hỗ trợ. Yêu cầu duy nhất là tệp cơ bản thực sự sử dụng charset đã chỉ định.

**Nếu tôi cần thay đổi mã hoá sau khi tài liệu đã được tải thì sao?**  
Mã hoá chỉ ảnh hưởng đến giai đoạn đọc. Khi đối tượng `Document` đã tồn tại, biểu diễn Unicode nội bộ của nó không phụ thuộc vào charset gốc. Để thay đổi mã hoá khi xuất, hãy điều chỉnh `SaveOptions` khi ghi tệp.

**Tôi có thể dùng cách này với các thư viện khác (ví dụ, Apache POI) không?**  
Apache POI tự xử lý việc phát hiện charset cho các định dạng nhị phân cũ, nhưng khái niệm cung cấp charset cho bộ tải là tương tự. Đối với Aspose.Words, `LoadOptions` là cách chính thức để kiểm soát **cách chỉ định mã hoá**.

## Kết luận

Bây giờ bạn đã biết **cách chỉ định mã hoá** khi tải tài liệu bằng Aspose.Words cho Java. Bằng cách tạo đối tượng `LoadOptions`, gọi phương thức `setEncoding`, và truyền các tùy chọn vào hàm khởi tạo `Document`, bạn đảm bảo các byte của tệp được giải mã đúng. Thực hành này loại bỏ văn bản rối, hỗ trợ nội dung đa ngôn ngữ, và tích hợp mượt mà với xử lý hàng loạt hoặc quy trình dựa trên luồng.

Khám phá các chủ đề liên quan như **document loading options**, **saving with specific encodings**, và **handling Unicode in Java** để nâng cao khả năng xử lý văn bản của bạn. Thử nghiệm với các tên charset khác nhau, kết hợp cách tiếp cận này với chuyển đổi PDF, hoặc tích hợp vào dịch vụ web nhận tải lên ở nhiều mã hoá khác nhau.

Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}