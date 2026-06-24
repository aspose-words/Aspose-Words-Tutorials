---
category: general
date: 2026-06-20
description: Khôi phục các tệp docx bị hỏng trong Java bằng Aspose.Words. Tìm hiểu
  cách thiết lập chế độ khôi phục và tải tài liệu với chế độ khôi phục để mở một cách
  liền mạch.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- load document with recovery
- open word with recovery
- open corrupted docx
language: vi
og_description: Khôi phục các tệp docx bị hỏng trong Java bằng Aspose.Words. Hướng
  dẫn này chỉ cách thiết lập chế độ khôi phục, tải tài liệu với chế độ khôi phục và
  mở tệp docx bị hỏng một cách an toàn.
og_title: Khôi phục tệp docx bị hỏng trong Java – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  headline: Recover corrupted docx in Java – Complete Guide
  type: TechArticle
- description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  name: Recover corrupted docx in Java – Complete Guide
  steps:
  - name: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
    text: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
  - name: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
    text: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
  - name: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
    text: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
  - name: Open Word → *File* → *Open*.
    text: Open Word → *File* → *Open*.
  - name: Select the corrupted `.docx`.
    text: Select the corrupted `.docx`.
  - name: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
    text: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Recovery
- DOCX
title: Khôi phục file docx bị hỏng trong Java – Hướng dẫn toàn diện
url: /vi/java/document-loading-and-saving/recover-corrupted-docx-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Khôi phục tệp docx bị hỏng trong Java – Hướng dẫn toàn diện

Bạn đã bao giờ **khôi phục tệp docx bị hỏng** và gặp khó khăn chưa? Trong tutorial này, chúng tôi sẽ chỉ cho bạn cách **khôi phục tệp docx bị hỏng** bằng Aspose.Words for Java bằng cách **đặt chế độ khôi phục** và **tải tài liệu với chế độ khôi phục** sao cho tệp mở ra như một tài liệu Word bình thường.  

Nếu bạn từng thắc mắc tại sao một số tệp DOCX lại không mở được trong Word, câu trả lời thường là do hư hỏng ẩn mà bộ tải thông thường không xử lý được. Chúng tôi sẽ hướng dẫn chi tiết các bước cần thiết, từ việc thêm thư viện đến kiểm tra số trang, và bạn sẽ có được một tài liệu sạch, có thể sử dụng—không còn thông báo “tệp bị hỏng” nữa.

## Những gì bạn sẽ học

- Cách **đặt chế độ khôi phục** để chỉ định cho Aspose.Words mức độ sửa chữa tệp hỏng.  
- Mã chính xác để **tải tài liệu với chế độ khôi phục** và xử lý một cách nhẹ nhàng các hư hỏng nghiêm trọng.  
- Mẹo cho các trường hợp **mở Word với chế độ khôi phục** và cách xử lý khi tệp không thể cứu được.  
- Một ví dụ hoàn chỉnh, có thể chạy ngay mà bạn có thể sao chép‑dán vào IDE của mình.  

### Yêu cầu trước

- Java 8 hoặc mới hơn đã được cài đặt.  
- Maven hoặc Gradle để quản lý phụ thuộc (chúng tôi sẽ trình bày Maven).  
- Một tệp `.docx` bị hỏng mà bạn muốn thử (bất kỳ tệp nào không mở được trong Microsoft Word đều được).  

Không cần kiến thức sâu về Aspose API—chỉ cần kỹ năng Java cơ bản. Bắt đầu thôi.

![ví dụ khôi phục docx bị hỏng](recover_corrupted_docx.png "ảnh chụp màn hình khôi phục docx bị hỏng")

## Bước 1: Thêm Aspose.Words for Java vào dự án của bạn

Đầu tiên, dự án của bạn cần JAR Aspose.Words. Nếu bạn dùng Maven, thêm đoạn này vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Người dùng Gradle có thể thêm:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

**Mẹo chuyên nghiệp:** Luôn kiểm tra trang web Aspose để lấy phiên bản mới nhất; các bản phát hành mới thường bao gồm thuật toán khôi phục tốt hơn.

## Bước 2: Đặt chế độ khôi phục – Chìa khóa để sửa các tệp bị hỏng

Bây giờ thư viện đã có, bạn cần chỉ định cho nó **cách** hành xử khi gặp hỏng hóc. Đó là lúc `setRecoveryMode` vào cuộc. Enum `RecoveryMode` cung cấp hai tùy chọn:

| Chế độ | Mô tả |
|------|-------------|
| `RECOVER` | Cố gắng sửa càng nhiều càng tốt, trả về tài liệu đã được sửa một phần. |
| `REJECT` | Ném ngoại lệ khi gặp bất kỳ vấn đề nghiêm trọng nào, hữu ích khi bạn cần một bản sạch. |

Đây là đoạn mã **đặt chế độ khôi phục** thành tùy chọn khoan dung `RECOVER`:

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create LoadOptions and set the desired recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Use RECOVER to attempt fixing,
                                                          // REJECT to fail on severe damage

        // Step 2.2: Load the possibly corrupted document using the configured options
        Document doc = new Document("C:/files/corrupted.docx", loadOptions);

        // Step 2.3: Work with the loaded document (e.g., display page count)
        System.out.println("Loaded with " + doc.getPageCount() + " pages");
    }
}
```

**Tại sao điều này quan trọng:** Nếu không đặt chế độ khôi phục, Aspose.Words mặc định là `REJECT`, nghĩa là chương trình của bạn sẽ ném ngoại lệ ngay khi phát hiện phần hỏng. Bằng cách **đặt chế độ khôi phục** một cách rõ ràng, bạn cho phép thư viện vá các node XML thiếu, khôi phục các mối quan hệ bị mất, và nói chung “dọn dẹp” tệp.

## Bước 3: Tải tài liệu với chế độ khôi phục – Kết hợp mọi thứ lại

Đoạn mã ở trên đã minh họa **tải tài liệu với chế độ khôi phục**, nhưng hãy phân tích chi tiết để dễ hiểu:

1. **Tạo đối tượng `LoadOptions`** – đối tượng này chứa tất cả các cờ bạn muốn bộ tải tuân thủ.  
2. **Gọi `setRecoveryMode`** – chúng tôi chọn `RECOVER` vì muốn có cơ hội tốt nhất để mở tệp.  
3. **Truyền các tùy chọn vào hàm khởi tạo `Document`** – Aspose.Words đọc tệp, áp dụng logic khôi phục, và trả về một đối tượng `Document` có thể sử dụng.

Nếu bạn muốn cách tiếp cận phòng thủ hơn, có thể bọc việc tải trong khối try‑catch và chuyển sang `REJECT` nếu `RECOVER` cho kết quả không đạt yêu cầu:

```java
try {
    Document doc = new Document("C:/files/corrupted.docx", loadOptions);
    System.out.println("Recovered document has " + doc.getPageCount() + " pages.");
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
    // Optional: retry with REJECT mode to see if the file is beyond repair
}
```

## Bước 4: Kiểm tra tài liệu đã được sửa

Sau khi tài liệu được tải, bạn sẽ muốn chắc chắn nội dung trông hợp lý. Các kiểm tra thường gặp bao gồm:

- **Số trang** – kiểm tra nhanh (`doc.getPageCount()`).  
- **Trích xuất văn bản** – `doc.getText()` để xem phần thân chính có còn nguyên không.  
- **Lưu bản sao** – ghi phiên bản đã khôi phục ra đĩa để kiểm tra sau.

```java
// Save the recovered file for manual verification
doc.save("C:/files/recovered.docx");

// Print first 200 characters of text to the console
String preview = doc.getText().substring(0, Math.min(200, doc.getText().length()));
System.out.println("Preview of recovered text:\n" + preview);
```

Nếu bản xem trước bị rối loạn, tệp có thể đã chịu hư hỏng không thể phục hồi. Trong trường hợp đó, hãy cân nhắc sử dụng chế độ `REJECT` để tránh lan truyền dữ liệu bị hỏng.

## Bước 5: Tùy chọn – Mở Word với chế độ khôi phục (cách thủ công)

Đôi khi bạn không muốn viết mã; bạn chỉ cần **mở Word với chế độ khôi phục** một cách thủ công. Microsoft Word tự cung cấp tính năng “Open and Repair”:

1. Mở Word → *File* → *Open*.  
2. Chọn tệp `.docx` bị hỏng.  
3. Nhấp vào mũi tên thả xuống bên cạnh *Open* và chọn **Open and Repair**.

Mặc dù cách này hoạt động cho nhiều người dùng, nhưng nó thiếu khả năng tự động hoá và xử lý hàng loạt như cách Java chúng ta vừa trình bày. Hãy dùng phương pháp thủ công cho những lần sửa chữa hiếm hoi; dựa vào Aspose.Words khi cần xử lý hàng chục hoặc hàng trăm tệp một cách lập trình.

## Trường hợp đặc biệt & Những bẫy thường gặp

- **Hỏng nặng** – Nếu tệp thiếu file cốt lõi `[Content_Types].xml`, ngay cả `RECOVER` cũng không giúp gì. Dự kiến sẽ có ngoại lệ và cần thông báo cho người dùng.  
- **Tệp được bảo vệ bằng mật khẩu** – Chế độ khôi phục không bỏ qua mã hoá. Bạn phải cung cấp mật khẩu qua `LoadOptions.setPassword("yourPwd")` trước khi cố gắng khôi phục.  
- **Tài liệu lớn** – Tải một DOCX khổng lồ với `RECOVER` có thể tiêu tốn nhiều bộ nhớ. Xem xét tăng heap JVM (`-Xmx2g`) nếu gặp `OutOfMemoryError`.  

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là chương trình đầy đủ mà bạn có thể biên dịch và chạy ngay. Thay đổi đường dẫn tệp thành vị trí của DOCX bị hỏng của bạn.

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // Create LoadOptions and set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Attempt to fix

            // Load the corrupted document
            Document doc = new Document("C:/files/corrupted.docx", loadOptions);

            // Verify and display basic info
            System.out.println("Recovered document loaded successfully.");
            System.out.println("Page count: " + doc.getPageCount());

            // Save a clean copy
            doc.save("C:/files/recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");

            // Show a short text preview
            String text = doc.getText();
            System.out.println("Text preview (first 200 chars):");
            System.out.println(text.substring(0, Math.min(200, text.length())));
        } catch (Exception ex) {
            System.err.println("Failed to recover the document: " + ex.getMessage());
        }
    }
}
```

**Kết quả mong đợi (khi khôi phục thành công):**

```
Recovered document loaded successfully.
Page count: 12
Recovered file saved as recovered.docx
Text preview (first 200 chars):
Lorem ipsum dolor sit amet, consectetur adipiscing elit...
```

Nếu tài liệu không thể sửa, bạn sẽ nhận được thông báo lỗi rõ ràng thay vì stack trace, nhờ vào khối `try‑catch` bao quanh.

## Kết luận

Bây giờ bạn đã biết cách **khôi phục tệp docx bị hỏng** trong Java bằng Aspose.Words. Bằng cách **đặt chế độ khôi phục** thành `RECOVER` và sau đó **tải tài liệu với chế độ khôi phục**, bạn có thể tự động sửa nhiều vấn đề thường gặp mà nếu không sẽ ngăn không cho tệp Word mở được. Dù bạn cần **mở Word với chế độ khôi phục** một cách lập trình hay chỉ muốn **mở docx bị hỏng** thủ công, các kỹ thuật ở đây sẽ cung cấp nền tảng vững chắc.

**Bước tiếp theo:**  

- Thử nghiệm  

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với hướng dẫn chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Khôi phục docx bị hỏng – Hướng dẫn toàn diện để sửa và xử lý tài liệu](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [Cách tải HTML và lưu dưới dạng DOCX bằng Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Cách hợp nhất nhiều tệp DOCX bằng Aspose.Words for Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}