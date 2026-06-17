---
category: general
date: 2026-04-28
description: Duyệt các cảnh báo tài liệu trong tệp Word để phát hiện phông chữ thiếu,
  lấy tên phông chữ thiếu và in chi tiết phông chữ thiếu bằng Aspose.Words cho Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: vi
og_description: Duyệt các cảnh báo tài liệu để tìm phông chữ thiếu, lấy tên các phông
  chữ thiếu và in chi tiết phông chữ thiếu kèm ví dụ Java đầy đủ.
og_title: 'Duyệt các cảnh báo tài liệu: Phát hiện phông chữ thiếu trong Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Duyệt các cảnh báo tài liệu: Phát hiện phông chữ thiếu trong Java'
url: /vi/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lặp lại cảnh báo tài liệu – Phát hiện phông chữ thiếu trong Java

Bạn đã bao giờ cần **iterate document warnings** khi mở một tệp Word và tự hỏi những phông chữ nào bị thiếu chưa? Bạn không phải là người duy nhất. Các phông chữ thiếu có thể làm hỏng giao diện của báo cáo, và nếu không có cách phát hiện chúng, bạn có thể phát hành một tài liệu trông hoàn toàn khác so với bản gốc.  

Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách **detect missing fonts** bằng cách tải một tài liệu Word, lặp lại các cảnh báo của nó, lấy tên các phông chữ thiếu, và cuối cùng in thông tin phông chữ thiếu—tất cả đều sử dụng Aspose.Words for Java.  

Chúng tôi sẽ bao phủ mọi thứ từ dòng mã đầu tiên cho đến đầu ra console dự kiến, để bạn có thể sao chép‑dán một giải pháp hoạt động vào dự án của mình ngay lập tức. Không cần tài liệu bổ sung.

## Yêu cầu trước

- Java 8 hoặc mới hơn đã được cài đặt.
- Thư viện Aspose.Words for Java (phiên bản mới nhất tính đến ngày 2026‑04‑28).
- Một tệp Word có thể chứa các phông chữ chưa được cài đặt trên máy của bạn (ví dụ, `doc-with-missing-font.docx`).

Nếu bạn đã có những thứ này, tuyệt vời—bạn đã sẵn sàng **load word document** và bắt đầu lặp lại.

## Bước 1 – Tải tài liệu Word với tùy chọn mặc định

Trước khi chúng ta có thể **iterate document warnings**, tệp phải được tải vào bộ nhớ. Aspose.Words cho phép bạn thực hiện điều này bằng một lời gọi constructor duy nhất. Sử dụng `LoadOptions` mặc định thường là đủ, nhưng chúng tôi sẽ hiển thị cách tạo rõ ràng để dễ hiểu.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Tại sao điều này quan trọng:**  
> Việc tải tài liệu sẽ kích hoạt Aspose.Words quét tệp để tìm bất kỳ tài nguyên nào không thể giải quyết, chẳng hạn như các phông chữ chưa được cài đặt trên máy. Những vấn đề này được lưu dưới dạng **warnings**, mà chúng ta sẽ **iterate document warnings** trong bước tiếp theo.

## Bước 2 – Lặp lại cảnh báo tài liệu để tìm vấn đề phông chữ

Bây giờ là phần cốt lõi của giải pháp: chúng ta lặp qua mọi cảnh báo mà thư viện thu thập trong quá trình tải. Các đối tượng `WarningInfo` cho chúng ta biết điều gì đã sai, và chúng ta có thể lọc cho `FontSubstitutionWarning` để **detect missing fonts**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Mẹo chuyên nghiệp:** Kiểm tra `instanceof` đảm bảo chúng ta chỉ xử lý các cảnh báo liên quan đến phông chữ, bỏ qua các cảnh báo khác như vấn đề tải hình ảnh. Điều này làm cho vòng lặp hiệu quả và giữ đầu ra tập trung vào các phông chữ mà bạn thực sự cần **retrieve missing font** thông tin.

### Đầu ra Console dự kiến

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Nếu tài liệu không chứa phông chữ thiếu, vòng lặp sẽ kết thúc một cách im lặng—không có gì để **print missing font**.

## Bước 3 – Tại sao không chỉ bắt một Exception?

Bạn có thể tự hỏi, “Tại sao không bao bọc lời gọi `new Document(...)` trong một khối try‑catch và tìm một exception?” Câu trả lời có hai phần:

1. **Thông tin chi tiết:** Exceptions chỉ cho bạn biết rằng có gì đó đã thất bại. Cảnh báo cung cấp tên phông chữ chính xác và phông thay thế mà Aspose.Words đã chọn.
2. **Vấn đề không gây chết chương trình:** Các phông chữ thiếu thường không gây chết chương trình; tài liệu vẫn tải, nhưng độ chính xác về hình ảnh bị ảnh hưởng. Bằng cách **iterating document warnings**, bạn giữ khả năng xử lý phần còn lại của tệp.

## Bước 4 – Mở rộng ví dụ: Thu thập các phông chữ thiếu vào một List

Đôi khi bạn cần các phông chữ thiếu để xử lý tiếp theo—có thể để nhúng chúng hoặc cảnh báo người dùng qua UI. Dưới đây là một chỉnh sửa nhanh để thu thập các tên vào một `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Bây giờ bạn có một cách sạch sẽ để **retrieve missing font** dữ liệu một cách lập trình, mà bạn có thể đưa vào mô-đun báo cáo hoặc trình hướng dẫn cài đặt phông chữ.

## Bước 5 – Các cân nhắc thực tế

- **Nhiều lần thay thế:** Một phông chữ thiếu duy nhất có thể được thay thế bằng các phông chữ khác nhau ở các phần khác nhau của tài liệu. Danh sách cảnh báo sẽ chứa mỗi lần xuất hiện, vì vậy bạn có thể thấy các mục phông chữ thiếu trùng lặp.
- **Hiệu suất:** Tải các tài liệu rất lớn có thể tạo ra hàng nghìn cảnh báo. Nếu bạn chỉ quan tâm đến phông chữ, hãy lọc sớm như đã chỉ ra để giữ vòng lặp nhanh.
- **Phông chữ đa nền tảng:** Trên Linux, phông chữ thay thế mặc định thường là *Liberation Sans*. Trên Windows, có thể là *Arial*. Biết phông thay thế giúp bạn quyết định có cần đóng gói các phông chữ tùy chỉnh cùng ứng dụng hay không.

## Bước 6 – Hình ảnh hỗ trợ

Dưới đây là ảnh chụp màn hình của đầu ra console (văn bản thay thế alt bao gồm từ khóa chính cho SEO).

![Đầu ra console của iterate document warnings hiển thị các phông chữ thiếu và các phông thay thế](/images/iterate-document-warnings.png)

*Alt text:* *ví dụ iterate document warnings hiển thị tên phông chữ thiếu và chi tiết thay thế.*

## Kết luận

Bạn vừa học cách **iterate document warnings** trong Aspose.Words for Java, **detect missing fonts**, **load word document** một cách an toàn, **retrieve missing font** thông tin, và **print missing font** chi tiết ra console. Đoạn mã hoàn chỉnh chạy ngay như vậy, và bạn có thể điều chỉnh để ghi log vào tệp, hiển thị hộp thoại UI, hoặc thậm chí tự động nhúng các phông chữ thiếu.

Tiếp theo, bạn có thể muốn khám phá cách **load word document** với các nguồn phông chữ tùy chỉnh (ví dụ, thêm một thư mục chứa phông chữ công ty) hoặc cách nhúng các phông chữ thiếu trực tiếp vào tệp để giữ bố cục trên các máy khác nhau. Cả hai chủ đề đều phát triển tự nhiên dựa trên những gì chúng tôi đã trình bày ở đây.

Chúc lập trình vui vẻ, và hy vọng các tệp PDF của bạn luôn hiển thị chính xác như bạn mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}