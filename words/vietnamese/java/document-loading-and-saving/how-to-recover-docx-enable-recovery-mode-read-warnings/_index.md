---
category: general
date: 2026-03-19
description: Cách khôi phục tệp docx bằng Java – học cách bật chế độ khôi phục, đọc
  cảnh báo và khôi phục nhanh tệp docx bị hỏng.
draft: false
keywords:
- how to recover docx
- enable recovery mode
- how to read warnings
- recover corrupted docx
language: vi
og_description: Cách khôi phục tệp docx trong Java. Hướng dẫn này chỉ cho bạn cách
  bật chế độ khôi phục, đọc cảnh báo và sửa các tài liệu docx bị hỏng.
og_title: Cách khôi phục docx – Bật chế độ khôi phục và đọc cảnh báo
tags:
- docx
- recovery
- java
- warnings
title: Cách khôi phục docx – Bật chế độ khôi phục và Đọc cảnh báo
url: /vi/java/document-loading-and-saving/how-to-recover-docx-enable-recovery-mode-read-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách khôi phục file docx – Hướng dẫn Java đầy đủ

Cách khôi phục file docx là một rào cản phổ biến khi bạn tự động hoá quy trình làm việc Office. Trong hướng dẫn này, chúng ta sẽ đi qua **cách bật chế độ khôi phục**, bắt mọi cảnh báo mà API ném ra, và cuối cùng đưa một file docx bị hỏng trở lại trạng thái hoạt động.

Hãy tưởng tượng bạn vừa nhận được một file .docx từ đối tác, nhưng khi mở ra lại gặp lỗi “file bị hỏng”. Thay vì yêu cầu người gửi gửi lại, bạn có thể để Aspose.Words cố gắng cứu những gì còn lại. Khi kết thúc tutorial, bạn sẽ có thể:

* Tải một tài liệu bị hỏng mà không làm ứng dụng của bạn sập.  
* Kiểm tra và ghi lại mỗi cảnh báo để biết những gì đã mất.  
* Chọn chiến lược khôi phục phù hợp nhất với tình huống của bạn.

Không cần công cụ xây dựng phức tạp hay dịch vụ bên ngoài—chỉ cần một phiên bản mới của **Aspose.Words for Java** và một vài dòng code.

## Những gì bạn cần

* Java 17 (hoặc bất kỳ JDK mới nào).  
* Aspose.Words for Java 23.6 trở lên – thư viện cung cấp các tính năng khôi phục.  
* Một file `docx` bị hỏng để thử nghiệm (bạn có thể làm hỏng file bằng cách mở trong trình soạn thảo hex và xóa vài byte).

Đó là tất cả. Nếu bạn đã có những thứ trên, hãy bắt đầu.

![Diagram of recovery workflow for a DOCX file](https://example.com/recovery-diagram.png){: .img-responsive alt="Minh hoạ cách khôi phục docx"}

## Cách khôi phục DOCX – Tổng quan từng bước

Dưới đây là lộ trình cấp cao trước khi chúng ta bắt tay vào thực hiện:

1. **Cấu hình** một đối tượng `LoadOptions` và **bật chế độ khôi phục**.  
2. **Tải** file bị hỏng với các tùy chọn đó.  
3. **Đọc các cảnh báo** mà Aspose.Words tạo ra trong quá trình tải.  
4. **Lưu** tài liệu đã khôi phục (tùy chọn) và kiểm tra kết quả.

Mỗi mục trên sẽ trở thành một phần riêng, kèm code và giải thích chi tiết.

## Bật chế độ khôi phục trong Aspose.Words

Tại sao lại phải dùng đối tượng `LoadOptions`? Mặc định Aspose.Words sẽ ném ra một ngoại lệ ngay khi phát hiện bất thường trong cấu trúc file. Điều này tốt cho việc kiểm tra chặt chẽ, nhưng lại tệ khi bạn chỉ muốn có “phiên bản tốt nhất có thể” của một file bị hỏng.

```java
// Step 1: Prepare load options to recover a corrupted document (with warnings)
import com.aspose.words.*;

LoadOptions recoveryOptions = new LoadOptions();
// Choose the recovery mode you need:
// RECOVER_WITH_WARNINGS – returns a document and fills the warnings collection.
// RECOVER_WITHOUT_WARNINGS – tries to silently fix issues.
recoveryOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
```

*Mẹo:* Nếu bạn chỉ quan tâm tới tài liệu cuối cùng và không cần chi tiết, `RECOVER_WITHOUT_WARNINGS` sẽ nhanh hơn một chút vì thư viện bỏ qua giai đoạn tạo cảnh báo.

## Tải tài liệu bị hỏng

Bây giờ chúng ta đã **bật chế độ khôi phục**, bước tiếp theo là thực sự đưa file vào bộ nhớ. Hàm khởi tạo `Document` chấp nhận `LoadOptions` mà chúng ta vừa cấu hình, vì vậy bất kỳ lỗi nào cũng được xử lý phía sau.

```java
// Step 2: Load the document using the configured recovery options
String pathToCorruptFile = "YOUR_DIRECTORY/corrupted.docx";
Document doc = new Document(pathToCorruptFile, recoveryOptions);
```

Nếu file quá hỏng, `doc` vẫn sẽ được tạo—nhưng danh sách cảnh báo sẽ được lấp đầy bằng các thông điệp mô tả những gì không thể khôi phục (ví dụ: thiếu phần chính của tài liệu, mối quan hệ bị hỏng, v.v.). Vì vậy **cách đọc cảnh báo** trở nên quan trọng.

## Cách đọc cảnh báo từ Document

Aspose.Words lưu mọi vấn đề gặp phải trong một `WarningInfoCollection`. Bạn có thể duyệt qua nó giống như bất kỳ danh sách nào khác. Mỗi `WarningInfo` cung cấp mô tả, nguồn gốc và loại cảnh báo.

```java
// Step 3: Inspect any warnings that were raised during loading
for (WarningInfo warning : doc.getWarnings()) {
    System.out.println("Warning: " + warning.getDescription());
}
```

Kết quả điển hình trông như sau:

```
Warning: The document contains a corrupted image part and has been removed.
Warning: Unknown XML element 'w:ins' encountered – it has been ignored.
```

Những thông điệp này vô giá cho việc ghi log hoặc thông báo cho người dùng rằng một số nội dung có thể đã mất. Nếu bạn cần **khôi phục docx bị hỏng** trong một pipeline sản xuất, bạn có thể muốn ghi các cảnh báo này vào file log thay vì chỉ in ra màn hình.

### Các trường hợp đặc biệt & Biến thể

| Tình huống | Cách xử lý |
|-----------|------------|
| **Không có cảnh báo** | Tài liệu có thể không bị hỏng hoặc thư viện đã tự động sửa mọi thứ một cách im lặng. Bạn có thể an toàn tiếp tục lưu hoặc xử lý file. |
| **Số lượng cảnh báo lớn** | Xem xét dùng `RECOVER_WITHOUT_WARNINGS` nếu bạn chỉ cần một tài liệu có thể sử dụng và không quan tâm tới chi tiết. |
| **Các loại cảnh báo cụ thể** | Bạn có thể lọc bằng `warning.getWarningType()` nếu chỉ muốn xử lý, ví dụ, các hình ảnh bị thiếu. |

## Ví dụ hoàn chỉnh và kết quả mong đợi

Kết hợp mọi thứ lại, dưới đây là một lớp Java tự chứa mà bạn có thể đưa vào bất kỳ dự án nào. Nó minh họa **cách khôi phục docx**, **bật chế độ khôi phục**, và **cách đọc cảnh báo** trong một lần.

```java
import com.aspose.words.*;

public class DocxRecoveryDemo {

    public static void main(String[] args) {
        // ---- 1. Set up recovery options ----
        LoadOptions recoveryOptions = new LoadOptions();
        recoveryOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);

        // ---- 2. Load the corrupted DOCX ----
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        Document doc;
        try {
            doc = new Document(inputPath, recoveryOptions);
        } catch (Exception e) {
            System.err.println("Failed to load the document: " + e.getMessage());
            return;
        }

        // ---- 3. Read and log warnings ----
        if (doc.getWarnings().isEmpty()) {
            System.out.println("No warnings – the document loaded cleanly.");
        } else {
            System.out.println("Warnings encountered during recovery:");
            for (WarningInfo warning : doc.getWarnings()) {
                System.out.println("- " + warning.getDescription());
            }
        }

        // ---- 4. (Optional) Save the recovered document ----
        String outputPath = "YOUR_DIRECTORY/recovered.docx";
        try {
            doc.save(outputPath);
            System.out.println("Recovered document saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Failed to save the recovered document: " + e.getMessage());
        }
    }
}
```

**Kết quả console dự kiến** (khi file nguồn thực sự bị hỏng):

```
Warnings encountered during recovery:
- The document contains a corrupted image part and has been removed.
- Unknown XML element 'w:ins' encountered – it has been ignored.
Recovered document saved to: YOUR_DIRECTORY/recovered.docx
```

Nếu file sạch, bạn sẽ thấy:

```
No warnings – the document loaded cleanly.
Recovered document saved to: YOUR_DIRECTORY/recovered.docx
```

Đó là toàn bộ quy trình **khôi phục docx bị hỏng** trong chưa tới 60 dòng Java.

## Những lỗi thường gặp & Mẹo chuyên nghiệp

* **Quên bật chế độ khôi phục?** Mặc định là `STRICT`, ném ngoại lệ ngay khi gặp vấn đề. Luôn kiểm tra rằng `recoveryOptions.setRecoveryMode(...)` được gọi trước khi khởi tạo `Document`.  
* **Tài liệu lớn có thể sinh ra rất nhiều cảnh báo** – ghi log chi tiết có thể làm ngập nhật log của bạn. Hãy dùng logger có mức độ cấu hình, hoặc chỉ ghi những cảnh báo nghiêm trọng nhất vào file riêng.  
* **Lưu file đã khôi phục vẫn có thể mất dữ liệu** – các cảnh báo cho bạn biết chính xác những gì đã bị loại bỏ (hình ảnh, XML tùy chỉnh, v.v.). Nếu bạn cần những tài nguyên này, phải yêu cầu bản sao sạch từ nguồn.  
* **An toàn đa luồng** – `LoadOptions` không an toàn cho đa luồng. Tạo một thể hiện mới cho mỗi luồng nếu bạn xử lý nhiều file đồng thời.

## Kết luận

Chúng ta đã bao quát **cách khôi phục docx** bằng cách bật chế độ khôi phục, tải file bị hỏng, và đọc mọi cảnh báo mà thư viện phát ra. Với kiến thức này, bạn có thể xây dựng các pipeline xử lý tài liệu mạnh mẽ, xử lý linh hoạt các đầu vào bị hỏng mà không bị sập ngay khi gặp sự cố.

Các bước tiếp theo bạn có thể khám phá:

* **Xử lý hàng loạt** – lặp qua một thư mục các file, khôi phục từng cái và tổng hợp cảnh báo vào báo cáo CSV.  
* **Xử lý cảnh báo tùy chỉnh** – ánh xạ `WarningInfo.getWarningType()` tới các hành động kinh doanh, như thông báo cho người dùng hoặc kích hoạt yêu cầu tải lại.  
* **Thư viện thay thế** – nếu bạn không dùng Aspose.Words, Apache POI cũng cung cấp một số khả năng khôi phục, nhưng không có hệ thống cảnh báo phong phú như chúng ta đã trình bày.

Hãy thử với một file `.docx` cố ý làm hỏng và xem các cảnh báo xuất hiện như thế nào. Bạn càng thực hành, bạn sẽ càng hiểu rõ giới hạn của việc khôi phục tự động và khi nào cần quay lại các phương pháp thủ công.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn nguyên vẹn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}