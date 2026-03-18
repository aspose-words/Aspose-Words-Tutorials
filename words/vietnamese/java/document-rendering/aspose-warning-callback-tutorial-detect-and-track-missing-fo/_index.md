---
category: general
date: 2026-03-17
description: Tìm hiểu hướng dẫn callback cảnh báo của Aspose để phát hiện và theo
  dõi phông chữ thiếu trong tài liệu Java với một ví dụ đầy đủ, có thể chạy được.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: vi
og_description: Nắm vững hướng dẫn callback cảnh báo của Aspose để phát hiện và theo
  dõi các phông chữ thiếu trong quy trình xử lý Word bằng Java của bạn.
og_title: Hướng dẫn callback cảnh báo Aspose – Phát hiện phông chữ thiếu
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Hướng dẫn callback cảnh báo Aspose – Phát hiện và theo dõi phông chữ thiếu
url: /vi/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

Check for any other markdown links: none.

Check for images: none.

All good.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hướng dẫn callback cảnh báo aspose – Phát hiện và Theo dõi Phông chữ bị thiếu

Bạn đã bao giờ tự hỏi làm thế nào để **phát hiện phông chữ bị thiếu** khi chuyển đổi hoặc chỉnh sửa tệp Word bằng Aspose.Words? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế, một phông chữ lạc lõng có thể gây ra lỗi bố cục, và bạn cần một cách đáng tin cậy để **theo dõi phông chữ bị thiếu** trước khi chúng gây rắc rối sau này.  

Tin tốt? **hướng dẫn callback cảnh báo aspose** cung cấp cho bạn một hook lập trình sạch sẽ, in ra chính xác các cảnh báo thay thế phông chữ khi chúng xảy ra. Trong hướng dẫn này, chúng ta sẽ đi qua cách thiết lập callback, tải tài liệu, và xem các cảnh báo hoạt động — tất cả bằng Java.

Khi kết thúc bài viết này, bạn sẽ có thể tự động phát hiện phông chữ bị thiếu, ghi lại chúng, và quyết định có nên nhúng phông chữ thay thế hoặc điều chỉnh các tệp nguồn của mình. Không cần công cụ bên ngoài.

## Yêu cầu trước

- **Java 8+** (mã nguồn biên dịch với bất kỳ JDK mới nào)
- **Aspose.Words for Java** phiên bản 23.10 trở lên – tải xuống từ cổng Aspose hoặc thêm phụ thuộc Maven.
- Một tệp DOCX mẫu có cố ý tham chiếu đến một phông chữ bạn không cài đặt (ví dụ, “Comic Sans MS” trên máy Linux).

Chỉ vậy—không cần thư viện bổ sung, không có bước xây dựng phức tạp.

## Bước 1: Đăng ký Callback Cảnh báo – Cốt lõi của hướng dẫn callback cảnh báo aspose

Điều đầu tiên mà hướng dẫn dạy bạn là cách gắn một listener cảnh báo. Aspose.Words tạo ra một đối tượng `WarningInfo` cho mỗi vấn đề nó gặp, và cờ `WarningSource.FONT_SUBSTITUTION` cho chúng ta biết chính xác khi nào một phông chữ đang được thay thế.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Tại sao điều này quan trọng:** Nếu không có callback, Aspose sẽ im lặng thay thế các phông chữ thiếu, và bạn sẽ không bao giờ biết ký tự nào có thể bị sai lệch. Bằng cách ghi lại cảnh báo, bạn có thể **phát hiện phông chữ bị thiếu** sớm và quyết định có nên nhúng phông chữ đúng hay không.

> **Mẹo chuyên nghiệp:** Nếu bạn cần thu thập các cảnh báo để báo cáo sau, hãy lưu chúng trong một `List<WarningInfo>` thay vì in trực tiếp.

## Bước 2: Tải Tài liệu – Nơi phông chữ bị thiếu có thể ẩn nấp

Bây giờ chúng ta tải tệp DOCX có thể tham chiếu đến các phông chữ không có trên máy. Việc tải sẽ kích hoạt callback cảnh báo nếu có bất kỳ phông chữ nào bị thiếu.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Điều gì đang diễn ra phía sau?** Aspose phân tích các định nghĩa kiểu của tài liệu, quét từng đoạn văn bản, và kiểm tra kho phông chữ của hệ thống. Khi không tìm thấy khớp chính xác, nó sẽ dùng phông chữ thay thế và kích hoạt cảnh báo mà chúng ta vừa gắn.

## Bước 3: Lưu Tài liệu – Đẩy các cảnh báo ra

Cuối cùng, chúng ta lưu tài liệu. Thao tác lưu cũng sẽ đánh giá lại các phông chữ, vì vậy bất kỳ cảnh báo nào chưa được phát ra trong quá trình tải sẽ xuất hiện bây giờ.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Khi bạn chạy chương trình, bạn sẽ thấy đầu ra console tương tự như:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Đầu ra đó chứng minh **hướng dẫn callback cảnh báo aspose** hoạt động, và bạn đã **phát hiện phông chữ bị thiếu** thành công và hiện đang **theo dõi phông chữ bị thiếu** qua nhật ký.

## Cách Phát hiện Phông chữ Bị Thiếu trong Tài liệu Word – Ngoài Cơ bản

Cách tiếp cận callback rất tốt cho các lần chạy đơn lẻ, nhưng đôi khi bạn cần một tiện ích tái sử dụng. Dưới đây là một wrapper nhanh mà bạn có thể đưa vào bất kỳ dự án nào:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Gọi nó như sau:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Bây giờ bạn có một phương thức **phát hiện phông chữ bị thiếu** tái sử dụng, trả về một danh sách bạn có thể đưa vào pipeline CI hoặc giao diện người dùng.

## Theo dõi Phông chữ Bị Thiếu với Aspose.Words – Báo cáo cho Nhóm

Trong một đội lớn hơn, bạn có thể muốn tạo báo cáo CSV về tất cả các phông chữ bị thiếu trên nhiều tài liệu. Kết hợp tiện ích trước với việc lặp qua các tệp đơn giản:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Chạy script này sẽ cung cấp cho bạn một CSV **theo dõi phông chữ bị thiếu** mà mọi nhà phát triển có thể xem nhanh trước khi cam kết tài liệu vào môi trường production.

## Những Cạm Bẫy Thường Gặp & Cách Tránh

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback không kích hoạt** | Bạn quên thiết lập callback **trước** khi tải tài liệu. | Đặt `Document.setWarningCallback` ở đầu hàm `main`. |
| **Chỉ cảnh báo đầu tiên xuất hiện** | Aspose lưu cache các cảnh báo cho mỗi đối tượng `Document`. | Sử dụng một đối tượng `Document` mới cho mỗi tệp, hoặc đặt lại callback giữa các lần chạy. |
| **Tên phông chữ sai trong nhật ký** | Mô tả chứa văn bản thừa (“Font … not found”). | Loại bỏ bằng regex như trong ví dụ CSV. |
| **Giảm hiệu năng khi xử lý hàng loạt lớn** | Callback chạy trên mỗi đoạn văn bản, có thể tốn kém. | Giới hạn kiểm tra ở bước pre‑flight; bỏ qua lưu nếu chỉ cần phát hiện. |

## Kết Quả Mong Đợi & Xác Minh

1. **Đầu ra console** – Bạn nên thấy ít nhất một dòng “Font substitution warning” cho mỗi phông chữ bị thiếu.  
2. **Báo cáo CSV** – Sau khi script xử lý hàng loạt hoàn thành, mở `missing-fonts-report.csv` và xác minh mỗi hàng liệt kê tên tài liệu và phông chữ bị thiếu chính xác.  
3. **Tài liệu đã lưu** – Tệp DOCX đầu ra sẽ hiển thị bằng các phông chữ thay thế, nhưng bố cục hình ảnh có thể khác so với bản gốc.

Nếu bất kỳ bước nào không hoạt động như mô tả, hãy kiểm tra lại rằng JAR Aspose.Words đã có trong classpath và `input.docx` thực sự tham chiếu đến một phông chữ không có trên hệ điều hành của bạn.

## Kết Luận

Bạn vừa hoàn thành một **hướng dẫn callback cảnh báo aspose** cho thấy cách **phát hiện phông chữ bị thiếu** và **theo dõi phông chữ bị thiếu** trong các ứng dụng Java. Bằng cách đăng ký listener cảnh báo, tải tài liệu, và tùy chọn xuất kết quả, bạn có được khả năng quan sát đầy đủ các vấn đề liên quan đến phông chữ trước khi chúng xuất hiện trong môi trường production.

Tiếp theo, bạn có thể khám phá:

- Nhúng trực tiếp phông chữ bị thiếu bằng `LoadOptions.setFontSubstitution`.
- Sử dụng lớp `FontSettings` để ánh xạ các phông chữ bị thiếu tới các phông chữ thay thế cụ thể.
- Tích hợp báo cáo CSV vào pipeline CI/CD để làm thất bại các build khi xuất hiện phông chữ chưa được ghi chú.

Hãy thử nghiệm, điều chỉnh các callback cho phù hợp với framework ghi log của bạn, và xem quy trình làm việc với tài liệu của bạn trở nên mạnh mẽ hơn nhiều. Chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}