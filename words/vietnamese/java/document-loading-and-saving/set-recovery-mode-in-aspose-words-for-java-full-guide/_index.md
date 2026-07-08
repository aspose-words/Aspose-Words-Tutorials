---
category: general
date: 2026-07-03
description: Đặt chế độ khôi phục để phục hồi các tệp Word bị hỏng trong Java và hiển
  thị số trang sau khi tải. Học từng bước với Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: vi
og_description: Cài đặt chế độ khôi phục trong Aspose.Words cho Java để phục hồi các
  tệp Word bị hỏng và hiển thị số trang. Xem ví dụ đầy đủ ngay.
og_title: Cài đặt Chế độ Phục hồi trong Aspose.Words cho Java – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Cài đặt Chế độ Khôi phục trong Aspose.Words cho Java – Hướng dẫn đầy đủ
url: /vi/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt Chế Độ Phục Hồi trong Aspose.Words cho Java – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi làm thế nào để **đặt chế độ phục hồi** khi tải một tệp `.docx` bị hỏng bằng Aspose.Words chưa? Bạn không phải là người duy nhất đang bối rối trước các tài liệu Word bị hỏng không mở được. Trong hướng dẫn này, chúng tôi sẽ đi qua chính xác điều đó — cách cấu hình thư viện để **khôi phục các tệp Word bị hỏng** và sau đó **hiển thị số trang** của nội dung đã tải thành công.

Chúng tôi sẽ đề cập đến mọi thứ từ việc tinh chỉnh nhỏ `LoadOptions` đến dòng `System.out.println` cuối cùng cho biết có bao nhiêu trang đã được cứu vãn. Không có phần thừa, chỉ có giải pháp thực tế, sẵn sàng sao chép‑dán, hoạt động với phiên bản mới nhất Aspose.Words 23.12.

## Những Điều Bạn Sẽ Học

- Tại sao chế độ phục hồi quan trọng và những tùy chọn nào mà Aspose.Words cung cấp.  
- Cách **đặt chế độ phục hồi** một cách lập trình bằng Java.  
- Các cách **hiển thị số trang** sau khi tài liệu được tải, xác nhận việc phục hồi thành công.  
- Những cạm bẫy thường gặp khi xử lý các tệp Word bị hỏng và cách tránh chúng.  

Trước khi chúng ta bắt đầu, hãy chắc chắn rằng bạn có:

1. Giấy phép Aspose.Words cho Java hợp lệ (hoặc khóa đánh giá tạm thời).  
2. Java 17 hoặc mới hơn đã được cài đặt trên máy của bạn.  
3. Tệp `Corrupted.docx` bị hỏng mà bạn muốn thử.  

Đã có chưa? Tuyệt—hãy bắt tay vào thực hành.

> **Mẹo chuyên nghiệp:** Ngay cả khi bạn đang sử dụng bản dùng thử, các tính năng phục hồi vẫn hoạt động giống hệt như trong bản có giấy phép.

---

## ## Cách Đặt Chế Độ Phục Hồi với Aspose.Words cho Java

Trọng tâm của giải pháp nằm trong lớp `LoadOptions`. Theo mặc định, Aspose.Words cố gắng tải tài liệu tốt nhất có thể, nhưng khi tệp bị hỏng nghiêm trọng, bạn cần chỉ định cho nó *cách* hành xử. Đó là nơi **đặt chế độ phục hồi** trở nên cần thiết.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Tại sao `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words phân tích bất kỳ đoạn nào nó có thể hiểu, ghép lại thành một tài liệu hoạt động một phần. Lý tưởng khi bạn cần bất kỳ nội dung nào từ tệp bị hỏng.  
- **SKIP** – Thư viện bỏ qua hoàn toàn các phần bị hỏng, có thể nhanh hơn nhưng có thể loại bỏ nhiều dữ liệu hơn.  

Trong hầu hết các kịch bản thực tế, **PARSE** là lựa chọn an toàn hơn vì nó tối đa hoá lượng văn bản, hình ảnh và định dạng có thể khôi phục.

---

## ## Hiển Thị Số Trang Sau Khi Phục Hồi

Sau khi tài liệu được tải, bước tiếp theo hợp lý là xác minh thành công của thao tác. Chỉ số đơn giản nhất, nhưng thông tin nhất, là số trang. Phương thức `Document.getPageCount()` thực hiện đúng điều đó.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Nếu tệp hoàn toàn không đọc được, Aspose.Words sẽ ném ngoại lệ *trước* khi bạn tới dòng này. Khi bạn thấy số trang là `0` hoặc một số rất ít, thường có nghĩa là chế độ phục hồi đã phải loại bỏ các phần lớn của tệp gốc.

**Kết quả mong đợi (ví dụ):**

```
Document loaded, page count = 12
```

Điều đó cho bạn biết thư viện đã tái tạo được mười hai trang từ nguồn bị hỏng — khá ấn tượng cho một `.docx` bị hỏng.

---

## ## Trường Hợp Cạnh & Những Cạm Bẫy Thông Thường

### 1️⃣ Các Phần Header/Footer Bị Hỏng
Đôi khi chỉ phần thân chính được phân tích trong khi header và footer bị mất. Nếu bạn dựa vào chúng cho thương hiệu, có thể cần chèn lại chúng sau khi phục hồi.

### 2️⃣ Hình Ảnh Không Tải Được
Các hình ảnh nhúng thường bị loại bỏ khi container zip (định dạng `.docx` nền) bị hỏng. Bạn có thể phát hiện điều này bằng cách lặp qua `doc.getSections()` và kiểm tra `Section.getBody().getParagraphs()` để tìm các đối tượng `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Nếu vòng lặp không in gì, chế độ phục hồi có khả năng đã bỏ qua các hình ảnh.

### 3️⃣ Tài Liệu Lớn và Bộ Nhớ
Khôi phục một tệp bị hỏng 200 trang có thể tốn nhiều bộ nhớ. Hãy cân nhắc tăng kích thước heap JVM (`-Xmx2g`) khi bạn dự đoán tài liệu lớn.

### 4️⃣ Hạn Chế Giấy Phép
Phiên bản đánh giá giới hạn một số tính năng, nhưng **phục hồi** hoạt động đầy đủ. Tuy nhiên, số trang được in ra có thể bị giới hạn chỉ vài trang trong bản dùng thử. Luôn thử nghiệm với bản có giấy phép cho môi trường sản xuất.

---

## ## Ví Dụ Đầy Đủ Từ Đầu Đến Cuối (Có Thể Chạy)

Dưới đây là một chương trình tự chứa mà bạn có thể đưa vào bất kỳ dự án Maven hoặc Gradle nào. Nó bao gồm khai báo phụ thuộc cần thiết cho Aspose.Words 23.12.

### Đoạn mã Maven `pom.xml`

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Tệp nguồn Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Điều này thực hiện:**

1. Đặt chế độ phục hồi – cốt lõi của hướng dẫn của chúng ta.  
2. Tải tệp bị hỏng bằng `LoadOptions` đã cấu hình.  
3. **Hiển thị số trang**, cung cấp phản hồi ngay lập tức.  
4. Lưu phiên bản đã làm sạch (`Recovered.docx`) để bạn có thể mở trong Word sau này.

Chạy chương trình với:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Bạn sẽ thấy số trang được in ra console, xác nhận việc phục hồi đã thành công.

---

## ## Tổng Quan Hình Ảnh (Hình)

![sơ đồ luồng đặt chế độ phục hồi](https://example.com/images/recovery-mode-flow.png "Sơ đồ minh họa cách chế độ phục hồi hoạt động trong Aspose.Words cho Java")

*Văn bản thay thế bao gồm từ khóa chính **set recovery mode** để đáp ứng SEO.*

---

## ## Câu Hỏi Thường Gặp

**Hỏi: Nếu `RecoveryMode.PARSE` vẫn ném ngoại lệ thì sao?**  
**A:** Điều đó thường có nghĩa là tệp không thể cứu được — có thể container zip đã bị hỏng hoàn toàn. Trong trường hợp này, bạn có thể cần một công cụ sửa chữa của bên thứ ba trước khi đưa cho Aspose.Words.

**Hỏi: Tôi có thể kết hợp `RecoveryMode.PARSE` với các callback tải tài liệu tùy chỉnh không?**  
**A:** Chắc chắn. Triển khai `IWarningCallback` để bắt bất kỳ cảnh báo nào mà Aspose.Words phát ra trong quá trình phân tích. Điều này cung cấp cho bạn thông tin về những phần nào đã bị bỏ qua.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**Hỏi: Việc thay đổi chế độ phục hồi có ảnh hưởng đến tệp gốc không?**  
**A:** Không. Aspose.Words làm việc trên một bản sao trong bộ nhớ; tệp nguồn vẫn không bị thay đổi trừ khi bạn gọi `doc.save()` một cách rõ ràng.

---

## ## Kết Luận

Chúng tôi đã đề cập cách **đặt chế độ phục hồi** trong Aspose.Words cho Java, tại sao `PARSE` thường là lựa chọn tốt nhất để cứu một tài liệu bị hỏng, và cách **hiển thị số trang** để xác nhận kết quả. Bằng cách làm theo ví dụ đầy đủ, bạn đã có một giải pháp sẵn sàng chạy để **khôi phục các tệp Word bị hỏng** và cung cấp phản hồi ngay lập tức về thành công của thao tác.

Bước tiếp theo? Hãy thử chuyển sang `RecoveryMode.SKIP` để xem sự khác biệt, thử nghiệm với các tệp đa phần lớn, hoặc tích hợp logic này vào một dịch vụ web tự động sửa các tài liệu người dùng tải lên. Cùng một mẫu cũng áp dụng cho PDF (sử dụng Aspose.PDF) và thậm chí cho việc khôi phục văn bản thuần với các thư viện khác — chỉ cần nhớ ý tưởng cốt lõi: cấu hình bộ tải, cố gắng phục hồi, sau đó xác thực bằng một chỉ số đơn giản như số trang.

Chúc lập trình vui vẻ, và chúc tài liệu của bạn luôn nguyên vẹn!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao quát các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách Đặt LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Hướng Dẫn Toàn Diện về Xử Lý Tài Liệu Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Kết Hợp Nhiều Tệp Word với Aspose.Words cho Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}