---
category: general
date: 2026-05-04
description: Tìm hiểu cách Aspose.Words LoadOptions có thể khôi phục các tệp Word
  bị hỏng, sử dụng chế độ khôi phục, sửa chữa file docx bị lỗi và đếm số trang Word
  trong một hướng dẫn duy nhất.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: vi
og_description: Thành thạo các tùy chọn tải của Aspose.Words để khôi phục tệp Word
  bị hỏng, chọn chế độ phục hồi phù hợp, sửa chữa file docx hỏng và lấy số trang.
og_title: aspose words loadoptions – Khôi phục các tài liệu Word bị hỏng
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Khôi phục tài liệu Word bị hỏng trong Java
url: /vi/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Khôi phục tài liệu Word bị hỏng trong Java

Bạn đã bao giờ cố gắng mở một tệp Word mà đột nhiên từ chối tải không? Đó là cảm giác như bị đấm vào bụng khi một khách hàng gửi cho bạn một **corrupted docx** và bạn không biết liệu có thể cứu được không. Tin tốt? Với **aspose words loadoptions** bạn có thể chỉ định cho Aspose.Words cách hành xử khi tài liệu bị hỏng, dù là ném ngoại lệ hay cố gắng sửa chữa im lặng.  

Trong hướng dẫn này chúng ta sẽ đi qua cách sử dụng `LoadOptions` để **recover corrupted Word** các tệp, khám phá các cài đặt **use recovery mode**, xem cách **repair corrupted docx** tự động, và cuối cùng **get the word page count** của tài liệu đã khôi phục. Không cần công cụ bên ngoài, chỉ cần Java thuần và Aspose.Words.

## Những gì bạn cần

- **Aspose.Words for Java** (v24.12 hoặc mới hơn) – phiên bản mới nhất bổ sung một vài kiểm tra an toàn bổ sung.
- Một **Java IDE** (IntelliJ IDEA, Eclipse, hoặc thậm chí một trình soạn thảo văn bản đơn giản với `javac`).
- **DOCX bị hỏng** mà bạn muốn thử (chúng tôi sẽ gọi nó là `Corrupted.docx`).
- Một **hiểu biết cơ bản** về cú pháp Java – không có gì phức tạp, chỉ cần `public static void main` thông thường.

> **Mẹo chuyên nghiệp:** giữ một bản sao lưu của tệp gốc; các nỗ lực khôi phục đôi khi có thể ghi lại một phần của nhị phân.

## Bước 1: Tạo LoadOptions – Cốt lõi của việc khôi phục

Điều đầu tiên bạn làm là khởi tạo một đối tượng `LoadOptions`. Đối tượng này là bảng điều khiển của bạn; nó cho Aspose.Words biết cách xử lý tệp khi gặp vấn đề.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Tại sao bước này lại quan trọng? Bởi vì nếu không có `LoadOptions` thư viện sẽ quay lại hành vi mặc định, có thể im lặng bỏ qua lỗi hoặc, tệ hơn, trả về một tài liệu được tải một phần gây crash sau này. Bằng cách cấu hình rõ ràng các tùy chọn, bạn sẽ có xử lý lỗi quyết định.

## Bước 2: Chọn Chế độ Khôi phục Phù hợp

Aspose.Words cung cấp hai chiến lược khôi phục:

| Chế độ | Hành vi |
|------|-----------|
| `RecoveryMode.STRICT` | Ném ngoại lệ nếu tài liệu không thể được sửa chữa hoàn toàn. |
| `RecoveryMode.REPAIR` | Cố gắng sửa file và tiếp tục tải, ngay cả khi một số nội dung bị mất. |

Đối với kịch bản **recover corrupted word** mà bạn cần biết việc sửa chữa có thành công hay không, `STRICT` là lựa chọn an toàn nhất. Nếu bạn thích cách tiếp cận nỗ lực tốt nhất, hãy chuyển sang `REPAIR`.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Tại sao chọn một trong hai?**  
> *STRICT* cung cấp tín hiệu rõ ràng—hoặc tài liệu có thể sử dụng được hoặc bạn cần thông báo cho người dùng. *REPAIR* hữu ích trong các công việc batch khi bạn có thể chấp nhận mất một vài hình ảnh lẻ.

## Bước 3: Tải Tài liệu Có Thể Bị Hỏng

Bây giờ bạn thực sự mở tệp, truyền vào `LoadOptions` vừa cấu hình. Nếu tệp vượt quá khả năng sửa chữa và bạn đã chọn `STRICT`, một ngoại lệ sẽ được ném lên; nếu không, bạn sẽ nhận được một đối tượng `Document` sẵn sàng để kiểm tra.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Lưu ý đường dẫn có thể là tuyệt đối hoặc tương đối so với thư mục gốc dự án. Lớp `Document` trừu tượng hoá toàn bộ tệp Word, giúp bạn dễ dàng truy vấn các thông tin như số trang, các phần, hoặc thậm chí chỉnh sửa nội dung sau khi khôi phục.

## Bước 4: Xác Minh Tải – Lấy Số Trang Word

Một kiểm tra nhanh để chắc chắn là hỏi Aspose.Words tài liệu có bao nhiêu trang. Nếu số đếm khác không, bạn hầu như đã **repair corrupted docx** thành công.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Kết quả điển hình:

```
Loaded successfully, page count = 12
```

Nếu tài liệu thực sự không đọc được dưới `STRICT`, đoạn mã sẽ ném ngoại lệ trước khi tới dòng này. Điều này khiến việc kiểm tra `page count` vừa là xác minh vừa là thông tin hữu ích cho logic downstream (ví dụ, phân trang trong trình xem web).

## Ví dụ Hoạt Động Đầy Đủ

Dưới đây là chương trình Java hoàn chỉnh, sẵn sàng chạy, kết hợp tất cả các phần lại với nhau. Sao chép‑dán vào một tệp có tên `RecoveryModeDemo.java`, điều chỉnh đường dẫn, và chạy `javac RecoveryModeDemo.java && java RecoveryModeDemo`.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Kết quả Dự Kiến

- **Nếu tệp có thể khôi phục:** console sẽ in ra số trang, và bạn có thể tiếp tục xử lý đối tượng `Document` một cách an toàn.
- **Nếu tệp vượt quá khả năng sửa chữa (chế độ STRICT):** một `com.aspose.words.UnsupportedFileFormatException` (hoặc tương tự) sẽ được ném, bạn có thể bắt và xử lý một cách nhẹ nhàng.

## Câu hỏi Thường gặp & Trường hợp Cạnh

### Nếu tôi cần ghi lại chi tiết lỗi chính xác thì sao?

Bao bọc đoạn mã tải trong một khối `try‑catch` và ghi log `e.getMessage()`. Điều này cung cấp lý do rõ ràng—đó là một phần bị thiếu, một mối quan hệ bị hỏng, hay một luồng bị hỏng.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Tôi có thể chỉ khôi phục một số phần cụ thể (như văn bản nhưng không phải hình ảnh) không?

Aspose.Words không cung cấp các công tắc khôi phục chi tiết, nhưng sau khi tải bạn có thể duyệt các phần tử `NodeType` và loại bỏ bất kỳ phần nào là `NodeType.SHAPE` (hình ảnh) nếu chúng gây ra vấn đề downstream.

### Điều này có hoạt động với các tệp `.doc` cũ không?

Có. `LoadOptions` hoạt động trên tất cả các định dạng Word (`.doc`, `.docx`, `.dot`, `.dotx`). Logic khôi phục giống nhau.

### Thư viện xử lý các tệp được bảo vệ bằng mật khẩu như thế nào?

Nếu tệp được mã hoá, `LoadOptions` sẽ không bỏ qua mật khẩu. Bạn cần cung cấp mật khẩu qua `loadOptions.setPassword("yourPassword")`. Chế độ khôi phục chỉ được kích hoạt sau khi giải mã thành công.

## Mẹo cho Sử dụng trong Sản xuất

- **Ghi lại chế độ khôi phục đã chọn** – Giúp bạn khi sau này kiểm tra tại sao một tệp cụ thể thành công hoặc thất bại.
- **Không bao giờ ghi đè lên tệp gốc** – Lưu tài liệu đã khôi phục vào vị trí mới (`document.save("Recovered.docx")`).
- **Kết hợp với kiểm tra tính hợp lệ** – Sau khi khôi phục, chạy nhanh kiểm tra chính tả hoặc kiểm tra cấu trúc để đảm bảo tài liệu đáp ứng quy tắc kinh doanh của bạn.
- **Xử lý batch** – Khi làm việc với nhiều tệp, lặp qua chúng, bắt ngoại lệ riêng lẻ, và giữ báo cáo tóm tắt về số lượng thành công vs. thất bại.

## Kết luận

Bạn giờ đã có một công thức toàn diện, đầu‑tới‑cuối để sử dụng **aspose words loadoptions** để **recover corrupted Word** các tài liệu, quyết định có **use recovery mode** một cách nghiêm ngặt hay linh hoạt, tùy chọn **repair corrupted docx**, và cuối cùng **get the word page count** của tệp đã khôi phục. Cách tiếp cận này quyết đoán, dễ tích hợp vào các pipeline Java hiện có, và cho bạn toàn quyền kiểm soát mức độ mạnh mẽ mà thư viện nên áp dụng khi đối mặt với các binary bị hỏng.

Sẵn sàng tiến xa hơn? Hãy thử thay `RecoveryMode.STRICT` bằng `REPAIR` trong một công việc batch, hoặc mở rộng ví dụ để tự động lưu tệp đã sửa vào một thư mục an toàn. Khả năng là vô hạn, và với Aspose.Words bạn đã sẵn sàng xử lý ngay cả những trục trặc Word khó chịu nhất.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn tải sạch sẽ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}