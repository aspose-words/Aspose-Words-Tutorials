---
category: general
date: 2026-05-26
description: Mở tài liệu Word bị hỏng trong Java bằng Aspose.Words. Tìm hiểu cách
  thiết lập chế độ khôi phục và phục hồi các tệp Word bị hỏng một cách đáng tin cậy.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: vi
og_description: Mở tài liệu Word bị hỏng trong Java bằng Aspose.Words. Hướng dẫn này
  chỉ cách thiết lập chế độ khôi phục và phục hồi các tệp Word bị hỏng một cách hiệu
  quả.
og_title: Mở tài liệu Word bị hỏng – Đặt chế độ khôi phục trong Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Mở tài liệu Word bị hỏng – Đặt chế độ khôi phục trong Java
url: /vi/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mở Tài Liệu Word Bị Hỏng – Đặt Chế Độ Phục Hồi trong Java

Bạn đã bao giờ cố gắng mở một tài liệu Word bị hỏng và thấy chương trình gặp lỗi ngoại lệ chưa? Bạn không phải là người duy nhất—những tệp .docx hỏng có thể gây đau đầu thực sự. Tin tốt là Aspose.Words for Java cung cấp cho bạn khả năng kiểm soát chi tiết để bạn có thể **open corrupted word document** mà không làm ứng dụng bị sập, và thậm chí quyết định bạn muốn nhận cảnh báo, phục hồi im lặng, hay từ chối hoàn toàn.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình: từ việc tạo `LoadOptions` phù hợp, đến việc chọn giá trị **set recovery mode** thích hợp, và cuối cùng xác nhận tài liệu đã được tải thành công. Khi kết thúc, bạn sẽ biết **how to recover corrupted word file** một cách lập trình, không cần sao chép‑dán thủ công.

> **Bạn sẽ cần**  
> * Java 8 hoặc mới hơn (API cũng hoạt động với Java 11)  
> * Aspose.Words for Java 23.9 (hoặc phiên bản mới nhất)  
> * Một tệp .docx bị hỏng mẫu — chỉ cần đổi tên bất kỳ tệp hợp lệ nào để mô phỏng hỏng nếu bạn không có sẵn  

Hãy bắt đầu.

## Open Corrupted Word Document – Tổng Quan Các Bước

Dưới đây là luồng công việc cấp cao mà chúng ta sẽ thực hiện:

1. **Create `LoadOptions`** – đối tượng này cho Aspose.Words biết cách hành xử khi gặp sự cố.  
2. **Set recovery mode** – chọn `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS`, hoặc `REJECT_CORRUPTED`.  
3. **Load the document** bằng các tùy chọn đã cấu hình.  
4. **Verify** việc tải thành công (ví dụ, in số trang).  

Mỗi bước sẽ được giải thích chi tiết, kèm theo các đoạn mã bạn có thể sao chép‑dán trực tiếp vào IDE.

## Set Recovery Mode cho Các Kịch Bản Khác Nhau

Aspose.Words định nghĩa ba chiến lược phục hồi trong `LoadOptions.RecoveryMode`:

| Mode | Behaviour | When to use |
|------|-----------|-------------|
| `RECOVER_WITH_WARNINGS` | Cố gắng tải tài liệu, nhưng đưa ra bất kỳ vấn đề nào dưới dạng cảnh báo trong console. | Bạn muốn xem *điều gì* đã sai mà không dừng quá trình. |
| `RECOVER_WITHOUT_WARNINGS` | Im lặng sửa những gì có thể và ẩn các cảnh báo. | Môi trường production nơi log cần sạch sẽ. |
| `REJECT_CORRUPTED` | Ném ngoại lệ ngay khi phát hiện hỏng. | Các pipeline kiểm tra nghiêm ngặt cần thất bại nhanh. |

Việc chọn chế độ phù hợp là cốt lõi của **set recovery mode** đúng cách. Trong hầu hết các buổi debug, `RECOVER_WITH_WARNINGS` là lựa chọn tốt nhất vì nó cho bạn biết chính xác phần nào đã được sửa.

## Cách Phục Hồi Tệp Word Bị Hỏng Sử Dụng Aspose.Words

Dưới đây là một **chương trình Java đầy đủ, có thể chạy** minh họa toàn bộ quy trình. Bạn chỉ cần đặt nó vào tệp `RecoveryModeDemo.java`, điều chỉnh đường dẫn, và chạy.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Tại sao mỗi dòng lại quan trọng

* **`LoadOptions loadOptions = new LoadOptions();`** – nếu không có đối tượng này, Aspose.Words sẽ dùng chế độ phục hồi mặc định, tức là *từ chối* các tệp bị hỏng. Tạo nó cho phép bạn thay đổi hành vi đó.  
* **`setRecoveryMode(...)`** – đây là lời gọi **set recovery mode** quyết định liệu cảnh báo có xuất hiện, ẩn đi, hay gây ra ngoại lệ.  
* **`new Document(path, loadOptions);`** – hàm khởi tạo nhận `LoadOptions` mà chúng ta vừa cấu hình, vì vậy thư viện biết cách xử lý tệp hỏng ngay từ đầu.  
* **`doc.getPageCount()`** – kiểm tra nhanh tính hợp lệ. Nếu tài liệu tải và trả về số trang, bạn đã **how to recover corrupted word file** thành công.  
* **`doc.save(...)`** – tùy chọn nhưng hữu ích; bạn có thể ghi lại phiên bản đã được sửa lại lên đĩa để dùng sau.

## Xử Lý Các Trường Hợp Đặc Biệt Thường Gặp

### 1. File Not Found

Nếu đường dẫn sai, `Document` sẽ ném `FileNotFoundException`. Bao bọc việc tải trong khối try‑catch và ghi lại thông báo thân thiện:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Corruption Không Thể Phục Hồi

Ngay cả khi dùng `RECOVER_WITH_WARNINGS`, một số cấu trúc vẫn có thể vượt quá khả năng sửa chữa. Trong trường hợp đó Aspose.Words vẫn sẽ tải những phần có thể, nhưng bạn sẽ thấy các cảnh báo như “Cannot read paragraph properties”. Hãy chú ý tới output console; những cảnh báo này thường chỉ ra các phần thiếu mà bạn có thể cần tái tạo thủ công.

### 3. Tệp Lớn và Hiệu Suất

Quá trình phục hồi thêm một chút overhead vì thư viện phải phân tích tệp hai lần — một lần để phát hiện vấn đề, lần nữa để tái xây dựng. Đối với các tài liệu đa gigabyte, hãy cân nhắc streaming tệp hoặc tăng heap JVM (`-Xmx2g`) để tránh `OutOfMemoryError`.

## Pro Tips – Tăng Cường Độ Bền Khi Phục Hồi

* **Log warnings vào file** – chuyển hướng `System.err` tới một logger để bạn có bản ghi audit về những gì đã được sửa.  
* **Validate sau khi phục hồi** – chạy `doc.updatePageLayout();` rồi kiểm tra lại số trang; đôi khi bố cục thay đổi sau khi sửa các phần bị hỏng.  
* **Tự động phục hồi hàng loạt** – bao bọc demo trong một vòng lặp xử lý một thư mục các tệp bị hỏng, sử dụng cùng một `LoadOptions` mỗi lần.

## Kết Luận

Bây giờ bạn đã biết chính xác **how to recover corrupted word file** bằng Aspose.Words for Java. Bằng cách tạo một thể hiện `LoadOptions`, **set recovery mode** theo chiến lược phù hợp với kịch bản của bạn, và tải tài liệu với các tùy chọn đó, bạn có thể an toàn **open corrupted word document** mà không làm ứng dụng của mình bị sập. Mã mẫu ở trên là một giải pháp hoàn chỉnh, sẵn sàng chạy, in ra số trang và thậm chí lưu một bản sao đã được làm sạch.

Tiếp theo bạn muốn làm gì? Hãy thử chuyển chế độ phục hồi sang `RECOVER_WITHOUT_WARNINGS` và so sánh output console, hoặc thử tải các tài liệu được mã hoá (bạn sẽ cần cung cấp mật khẩu qua

## Related Tutorials

- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}