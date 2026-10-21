---
category: general
date: 2026-02-15
description: Chế độ khôi phục cho phép bạn tải tài liệu với chế độ khôi phục, giúp
  dễ dàng khôi phục tài liệu Word bị hỏng và sửa các lỗi khi khôi phục tài liệu Word.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: vi
og_description: Chế độ khôi phục là chìa khóa để tải tài liệu với khả năng khôi phục,
  cho phép bạn khắc phục các lỗi tài liệu Word bị hỏng trong Java.
og_title: cài đặt chế độ khôi phục – Khôi phục nhanh tài liệu Word bị hỏng
tags:
- Aspose.Words
- Java
- Document Recovery
title: đặt chế độ khôi phục để phục hồi tài liệu Word bị hỏng
url: /vi/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Cách Khôi Phục Tài Liệu Word Bị Hỏng bằng Aspose.Words

Bạn đã bao giờ cố gắng mở một tệp Word mà đột nhiên từ chối tải không? Bạn có thể đang nhìn chằm chằm vào một *.docx* bị hỏng và tự hỏi liệu bạn có cần bắt đầu lại từ đầu không. Tin tốt? **set recovery mode** trong Aspose.Words cung cấp cho bạn một cách nhẹ nhàng để *load document with recovery* và giữ lại hầu hết nội dung.

Trong tutorial này bạn sẽ học chính xác cách **set recovery mode**, tại sao tùy chọn *RELAXED* thường là lựa chọn tốt nhất cho các tệp bị hỏng, và cách xử lý những *recover word document errors* thỉnh thoảng vẫn xuất hiện. Không cần công cụ bên ngoài, chỉ cần Java thuần và vài dòng code.

> **Bạn sẽ nhận được gì:** một ví dụ hoàn chỉnh, có thể chạy được, tải một tệp Word bị hỏng, bỏ qua các phần không đọc được, và cung cấp cho bạn một đối tượng `Document` có thể sử dụng để xử lý tiếp.

---

## Prerequisites

Trước khi bắt đầu, hãy chắc chắn bạn có:

- **Aspose.Words for Java** (v24.9 hoặc mới hơn) được thêm vào dự án của bạn qua Maven hoặc JAR thủ công.
- Một tệp **corrupted .docx** mà bạn muốn thử (chúng tôi sẽ gọi nó là `Corrupted.docx`).
- Kiến thức cơ bản về Java – bạn không cần phải là chuyên gia xử lý Word, chỉ cần thoải mái với một phương thức `main`.

Nếu bạn thiếu bất kỳ mục nào ở trên, hãy tải JAR Aspose.Words mới nhất từ [official site](https://products.aspose.com/words/java) và thêm vào classpath. Đó là tất cả—không cần phụ thuộc thêm.

---

## Step 1: Understand the Recovery Modes

Aspose.Words cung cấp hai chiến lược khôi phục:

| Chế độ | Hành vi | Khi nào sử dụng |
|------|----------|------------|
| **RELAXED** | Bỏ qua các phần không đọc được, giữ lại phần còn lại. | Hầu hết các tệp bị hỏng – bạn muốn **recover broken word document** mà không gặp ngoại lệ. |
| **STRICT** | Ném ngoại lệ khi có bất kỳ lỗi nào. | Khi bạn cần đảm bảo tải hoàn hảo, không lỗi (hiếm khi áp dụng cho nguồn bị hỏng). |

> **Pro tip:** *RELAXED* là mặc định cho các kịch bản “chỉ cần lấy lại một phần gì đó”, trong khi *STRICT* hữu ích trong các pipeline tự động nơi một lỗi phải dừng quá trình.

---

## Step 2: Create a `LoadOptions` Object and **set recovery mode**

Đây là nơi từ khóa chính xuất hiện trong code. Chúng ta **set recovery mode** một cách rõ ràng trên một instance của `LoadOptions` trước khi tải tệp.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Tại sao điều này quan trọng:** Bằng cách gọi `setRecoveryMode`, bạn chỉ định cho Aspose.Words mức độ quyết liệt mà nó sẽ cố gắng cứu vãn tệp. Nếu không có lời gọi này, thư viện sẽ mặc định *STRICT*, sẽ dừng lại ngay khi gặp dấu hiệu lỗi—đánh mất mục đích của quy trình *recover broken word document*.

---

## Step 3: Verify the Load – Did We Really **recover broken word document**?

Sau khi tải, bạn có thể kiểm tra đối tượng `Document`:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Nếu console hiển thị số lượng section hợp lý, bạn đã thành công *load document with recovery*. Trong thực tế, bạn sẽ nhận thấy hầu hết văn bản, bảng và hình ảnh vẫn còn, trong khi các phần bị hỏng sẽ biến mất.

---

## Step 4: Handle Remaining **recover word document errors** Gracefully

Ngay cả với chế độ *RELAXED*, một vài trường hợp biên vẫn có thể gây ra cảnh báo. Bao bọc quá trình tải trong try‑catch để ứng dụng của bạn vẫn hoạt động:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Khi nào điều này xảy ra?** Nếu tệp bị hỏng đến mức ngay cả trình phân tích lỏng lẻo cũng không thể xác định cấu trúc tài liệu hợp lệ, Aspose.Words vẫn sẽ ném ngoại lệ. Trong những trường hợp hiếm hoi này, bạn có thể yêu cầu người dùng cung cấp một bản sao khác.

---

## Step 5: Save the Recovered File (Optional)

Hầu hết các nhà phát triển muốn có một phiên bản sạch để chuyển cho các hệ thống downstream. Lệnh `save` dưới đây sẽ ghi một `.docx` mới không còn chứa các đoạn bị hỏng.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Bây giờ bạn có một **recover broken word document** có thể mở trong Microsoft Word, Google Docs, hoặc bất kỳ trình xem nào khác—không có hộp thoại lỗi.

---

## Visual Overview (Image)

![Sơ đồ mô tả luồng set recovery mode – từ tệp bị hỏng đến tài liệu đã khôi phục](https://example.com/images/recovery-flow.png "sơ đồ luồng set recovery mode")

*Văn bản alt chứa rõ ràng từ khóa chính, giúp cả công cụ tìm kiếm và trình đọc màn hình.*

---

## Common Questions & Edge Cases

| Câu hỏi | Trả lời |
|----------|--------|
| *Nếu tôi cần giữ lại các phần bị hỏng để phân tích pháp y?* | Sử dụng `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` và bắt ngoại lệ. Thông báo ngoại lệ chứa chi tiết về các phần gặp vấn đề. |
| *Tôi có thể chuyển đổi giữa RELAXED và STRICT trong thời gian chạy không?* | Chắc chắn—chỉ cần tạo một đối tượng `LoadOptions` mới với chế độ mong muốn trước mỗi lần tải. |
| *Điều này có hoạt động với các tệp .doc cũ không?* | Có. `LoadOptions` giống nhau áp dụng cho cả định dạng `.doc` và `.docx`. |
| *Có gây giảm hiệu năng không?* | Tối thiểu. Chi phí phân tích thêm là không đáng kể so với chi phí tải toàn bộ tài liệu. |

---

## Full Working Example (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Chạy chương trình, chỉ tới tệp bị hỏng của bạn, và quan sát kết quả. Nếu mọi thứ diễn ra suôn sẻ, bạn sẽ thấy số trang được in ra và một `Recovered.docx` mới xuất hiện bên cạnh nguồn.

---

## Conclusion

Chúng ta đã bao quát mọi thứ bạn cần để **set recovery mode** trong Aspose.Words, từ việc chọn enum `RecoveryMode` phù hợp đến xử lý một vài *recover word document errors* có thể còn xuất hiện. Bằng cách làm theo các bước trên, bạn có thể tin cậy **load document with recovery**, giữ lại các phần tốt của tệp bị hỏng, và xuất ra một phiên bản sạch sàng cho bất kỳ quy trình downstream nào.

Sẵn sàng cho thử thách tiếp theo? Hãy thử kết hợp **set recovery mode** với các API **document cleaning** của Aspose.Words—loại bỏ các đoạn ẩn, sửa các hyperlink bị hỏng, hoặc thậm chí chuyển tệp đã khôi phục sang PDF trong một bước. Khả năng là vô hạn, và giờ bạn đã có nền tảng vững chắc để đối mặt với các tệp Word bị hỏng.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn khỏe mạnh!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}