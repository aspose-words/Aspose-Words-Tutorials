---
category: general
date: 2026-04-04
description: Ghi lại cảnh báo thay thế phông chữ khi tải tài liệu Word bằng Aspose.Words
  cho Java và tự động phát hiện các phông chữ thiếu. Thực hiện theo hướng dẫn từng
  bước này.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: vi
og_description: Ghi lại cảnh báo thay thế phông chữ khi tải tài liệu Word bằng Aspose.Words
  cho Java và phát hiện các phông chữ thiếu trong vài bước đơn giản.
og_title: Ghi lại Cảnh báo Thay thế Phông chữ – Phát hiện Phông chữ Thiếu
tags:
- Aspose.Words
- Java
- Document Processing
title: Ghi lại Cảnh báo Thay thế Phông chữ – Phát hiện Phông chữ Thiếu
url: /vi/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Thay thế Phông chữ – Phát hiện Phông chữ Thiếu

Bạn đã bao giờ cần **ghi lại cảnh báo thay thế phông chữ** khi mở một tệp Word, chỉ để phát hiện ra rằng một kiểu chữ quan trọng đang thiếu? Bạn không phải là người duy nhất. Trong nhiều quy trình doanh nghiệp, một phông chữ thiếu có thể biến một báo cáo được định dạng hoàn hảo thành một mớ hỗn độn, và manh mối duy nhất bạn nhận được là một cảnh báo im lặng mà hầu hết các nhà phát triển không bao giờ thấy.

Tin tốt là Aspose.Words for Java cho phép bạn gắn vào quá trình tải và **phát hiện phông chữ thiếu** trước khi chúng gây rắc rối sau này. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn qua một ví dụ hoàn chỉnh, có thể chạy được, in mọi cảnh báo thay thế trực tiếp lên console, để bạn có thể quyết định nhúng phông chữ đúng, thay thế nó, hoặc cảnh báo người dùng.

Khi bạn đọc xong hướng dẫn này, bạn sẽ biết cách:

* Thiết lập một đối tượng `LoadOptions` với callback cảnh báo tùy chỉnh.
* Lọc callback sao cho chỉ phản hồi các sự kiện thay thế phông chữ.
* Tải bất kỳ tệp `.docx` nào và xem ngay các cảnh báo.
* Mở rộng giải pháp để ghi log cảnh báo, ném ngoại lệ, hoặc thậm chí tự động cài đặt phông chữ thiếu.

Không cần tài liệu bên ngoài—chỉ cần vài dòng Java và file JAR của Aspose.Words.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn bạn đã có:

* Java 8 hoặc mới hơn được cài đặt (phiên bản LTS mới nhất hoạt động tốt nhất).
* Aspose.Words for Java 23.11 hoặc mới hơn – bạn có thể lấy artifact Maven hoặc file JAR thuần từ trang web Aspose.
* Một tài liệu Word tham chiếu đến một phông chữ mà bạn không có trên máy phát triển (ví dụ: “MyFancyFont”).  
* Một IDE hoặc trình soạn thảo văn bản mà bạn thích – tôi đang dùng IntelliJ IDEA, nhưng Eclipse hoặc VS Code cũng ổn.

Nếu bất kỳ mục nào trên nghe lạ, hãy tạm dừng và cài đặt chúng trước; phần còn lại của hướng dẫn giả định chúng đã sẵn sàng.

---

## Ghi lại Cảnh báo Thay thế Phông chữ bằng Aspose.Words

Cốt lõi của giải pháp nằm trong một thể hiện `LoadOptions`. Bằng cách gán một `IWarningCallback` chúng ta có thể chặn mọi cảnh báo mà thư viện phát ra trong giai đoạn tải.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Tại sao cách này hoạt động:**  
`LoadOptions` chỉ cho Aspose.Words cách xử lý tệp đầu vào. Giao diện `IWarningCallback` là một hook nhận một đối tượng `WarningInfo` cho *mọi* cảnh báo. Bằng cách kiểm tra `info.getWarningType()` chúng ta lọc ra mọi thứ ngoại trừ `SUBSTITUTED_FONT`. Thuộc tính `description` chứa thông điệp dễ đọc như “Font 'MyFancyFont' was substituted with 'Arial'”.

### Kết quả console dự kiến

Nếu tài liệu nguồn tham chiếu một phông chữ chưa được cài đặt, bạn sẽ thấy một thứ gì đó như sau:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Nếu tài liệu chỉ sử dụng các phông chữ đã có trên máy, callback sẽ im lặng và bạn chỉ nhận được dòng cuối cùng “Document loaded successfully.”.

---

## Phát hiện Phông chữ Thiếu trong Tài liệu của Bạn

Bạn có thể tự hỏi, *“Cảnh báo thay thế có giống như phông chữ thiếu không?”* Trong hầu hết các trường hợp, câu trả lời là có—Aspose.Words thay thế phông chữ thiếu bằng một phông chữ dự phòng và báo cáo qua `SUBSTITUTED_FONT`. Tuy nhiên, có những trường hợp ngoại lệ khi phông chữ tồn tại nhưng kiểu chính xác (đậm‑nghiêng, các tính năng OpenType cụ thể) không có, dẫn đến một sự thay thế tinh vi.

Để chắc chắn bạn đã bắt mọi lỗ hổng, bạn có thể kết hợp callback cảnh báo với một bước kiểm tra sau khi tải:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Mẹo chuyên nghiệp:** Nếu bạn phát hiện bất kỳ run nào vẫn tham chiếu đến phông chữ thiếu, bạn có thể thay thế chúng ngay lập tức:

```java
font.setName("Arial"); // fallback
```

Cách này giúp bạn đảm bảo kết quả hiển thị nhất quán, ngay cả khi cảnh báo gốc đã bị ẩn.

---

## Những lỗi thường gặp & Cách tránh chúng

| Lỗi | Nguyên nhân | Cách khắc phục |
|-----|-------------|----------------|
| **Quên thiết lập callback** | `LoadOptions` mặc định có callback không làm gì, vì vậy các cảnh báo biến mất. | Luôn gọi `loadOptions.setWarningCallback(...)` trước khi tải. |
| **Sử dụng loại cảnh báo sai** | `WarningType.SUBSTITUTED_FONT` là enum duy nhất báo hiệu phông chữ thiếu. | Lọc chính xác trên `WarningType.SUBSTITUTED_FONT`; các loại khác (ví dụ: `UNKNOWN_FILE_FORMAT`) không liên quan. |
| **Hard‑coding đường dẫn tệp** | Hoạt động cục bộ nhưng phá vỡ trong các pipeline CI/CD. | Dùng đường dẫn tương đối hoặc truyền vị trí tệp qua tham số dòng lệnh. |
| **Bỏ qua phông chữ Unicode** | Một số phông chữ thiếu chỉ gây vấn đề cho một số ký tự nhất định. | Kiểm tra với tài liệu chứa toàn bộ bộ ký tự bạn dự định hỗ trợ. |
| **Chạy trên server không có cấu hình phông chữ** | Server có thể thiếu bất kỳ phông chữ dự phòng nào, gây ra các thay thế bất ngờ. | Cài đặt một bộ phông chữ cơ bản (Arial, Times New Roman) trên server. |

---

## Mở rộng Giải pháp

Bây giờ bạn đã có thể **ghi lại cảnh báo thay thế phông chữ**, bạn có thể muốn:

* **Ghi log cảnh báo vào file** – thay thế `System.out.println` bằng một logger như SLF4J.
* **Ném ngoại lệ** – hữu ích trong các pipeline tự động khi một phông chữ thiếu nên làm thất bại quá trình build:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Tự động cài đặt phông chữ thiếu** – tải về TTF/OTF cần thiết tại thời gian chạy và thêm vào `GraphicsEnvironment` của Java. Đây là kịch bản nâng cao hơn, nhưng hoàn toàn khả thi.

---

## Diagram (optional)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Sơ đồ luồng ghi lại cảnh báo thay thế phông chữ mô tả cách Aspose.Words chuyển các cảnh báo phông chữ thiếu tới callback tùy chỉnh.”

---

## Kết luận

Chúng ta vừa tìm hiểu cách **ghi lại cảnh báo thay thế phông chữ** và **phát hiện phông chữ thiếu** khi tải tài liệu Word bằng Aspose.Words for Java. Bằng cách cấu hình một đối tượng `LoadOptions` và triển khai một `IWarningCallback` nhỏ, bạn có được khả năng quan sát toàn bộ quá trình fallback phông chữ, cho phép ghi log, thay thế, hoặc dừng lại khi gặp phông chữ thiếu.

Tóm lại: thiết lập callback, lọc `SUBSTITUTED_FONT`, tải tài liệu, và xử lý kết quả theo nhu cầu của ứng dụng. Từ đây bạn có thể mở rộng sang các framework logging, kiểm tra CI, hoặc thậm chí cung cấp phông chữ tự động.

Muốn tiến xa hơn? Hãy thử:

* **Nhúng phông chữ** trực tiếp vào tài liệu đã lưu (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` với `FontEmbeddingMode.EMBED_ALL`).
* **Tạo PDF** sau khi đã khắc phục phông chữ, đảm bảo đầu ra cuối cùng trông chính xác như mong muốn.
* **Quét toàn bộ thư mục** các tài liệu để tìm phông chữ thiếu và tạo báo cáo tóm tắt.

Đó là tất cả trong thời điểm này—chúc bạn lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng kiểu chữ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}