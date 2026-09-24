---
category: general
date: 2026-01-11
description: Tìm hiểu cách ghi nhận cảnh báo thay thế phông chữ bằng Aspose.Words
  cho Java. Hướng dẫn từng bước này cũng đề cập đến LoadOptions và các callback cảnh
  báo.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: vi
og_description: Ghi lại cảnh báo thay thế phông chữ với Aspose.Words cho Java. Tham
  khảo hướng dẫn này để thiết lập LoadOptions và callback cảnh báo nhằm tải tài liệu
  một cách đáng tin cậy.
og_title: Ghi lại Cảnh báo Thay thế Phông chữ trong Java – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- Java
- Document Processing
title: Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng dẫn
  đầy đủ
url: /vi/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Thay thế Phông chữ – Hướng dẫn Java đầy đủ

Bạn đã bao giờ cần **ghi lại cảnh báo thay thế phông chữ** khi mở một tài liệu Word thiếu phông chữ chưa? Đó là một rắc rối phổ biến, đặc biệt khi bạn tạo PDF hoặc in trên máy chủ không có mọi kiểu chữ được cài đặt. Tin tốt là gì? Aspose.Words for Java làm cho việc này trở nên dễ dàng—chỉ cần cấu hình một đối tượng `LoadOptions` và gắn một callback cảnh báo. Trong hướng dẫn này, bạn sẽ thấy chính xác cách thực hiện, tại sao nó quan trọng, và những gì sẽ xảy ra khi cảnh báo được kích hoạt.

Chúng tôi cũng sẽ đề cập đến các chủ đề liên quan như **Aspose.Words font substitution**, sử dụng **Java warning callback**, và các thực hành tốt nhất cho **LoadOptions usage**. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy, ghi lại mọi sự kiện phông chữ thiếu, để quá trình xử lý tiếp theo của bạn không bao giờ bị bất ngờ.

## Yêu cầu trước

- Java 17 (hoặc bất kỳ JDK gần đây nào) đã được cài đặt và cấu hình.
- Aspose.Words for Java 23.10 (hoặc mới hơn) trên classpath của bạn.
- Một tài liệu Word tham chiếu một phông chữ mà bạn không có cục bộ (ví dụ, `DocWithMissingFont.docx`).
- Kiến thức cơ bản về các khối try/catch của Java—không có gì phức tạp.

Nếu bất kỳ mục nào trên nghe lạ, hãy tạm dừng một chút và cài đặt thư viện từ Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Bây giờ nền tảng đã sẵn sàng, hãy vào phần mã.

## Bước 1: Thiết lập Callback Cảnh báo để **Ghi lại Cảnh báo Thay thế Phông chữ**

Điều đầu tiên bạn cần là một callback mà Aspose.Words sẽ gọi mỗi khi gặp phông chữ thiếu. Đây là nơi chúng ta **ghi lại cảnh báo thay thế phông chữ**. Callback này triển khai giao diện `IWarningCallback` và kiểm tra `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Tại sao điều này quan trọng:** Nếu không có callback, Aspose.Words sẽ im lặng thay thế phông chữ thiếu bằng một phông mặc định, và bạn sẽ không biết đầu ra hình ảnh đã thay đổi. Bằng cách ghi lại cảnh báo, bạn có thể ghi log, cảnh báo, hoặc thậm chí hủy quá trình tải nếu phông chữ thiếu là quan trọng.

## Bước 2: Cấu hình **LoadOptions** và Đăng ký Callback

Bây giờ chúng ta tạo một thể hiện `LoadOptions` và gắn `FontWarningCallback` của chúng ta. Bước này là thiết yếu cho **LoadOptions usage** và đảm bảo rằng mỗi lần tải tài liệu đều đi qua cùng một bộ lọc cảnh báo.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Mẹo:** Bạn có thể tái sử dụng cùng một đối tượng `LoadOptions` cho nhiều tài liệu, giúp tiết kiệm vài dòng mã lặp lại và đảm bảo việc xử lý **cảnh báo tải tài liệu** nhất quán trong toàn bộ ứng dụng của bạn.

## Bước 3: Tải Tài liệu và Quan sát Kết quả

Với callback đã được kết nối, chỉ cần tải file Word của bạn. Nếu tài liệu tham chiếu một phông chữ chưa được cài đặt, callback sẽ được kích hoạt và in chi tiết ra console.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Kết quả Dự kiến trên Console

Giả sử `DocWithMissingFont.docx` tham chiếu phông chữ thiếu *“Comic Sans MS”*, bạn sẽ thấy một cái gì đó như sau:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Nếu tài liệu **không có phông chữ thiếu**, console sẽ chỉ hiển thị dòng cuối cùng, xác nhận rằng callback của bạn không tạo ra bất kỳ cảnh báo giả nào.

## Bước 4: Xử lý Các Trường hợp Cạnh và Những Cạm bẫy Thông thường

### Nhiều Phông chữ Thiếu

Nếu một tài liệu sử dụng nhiều phông chữ không có sẵn, callback sẽ chạy một lần cho mỗi phông chữ. Bạn sẽ nhận được một loạt tin nhắn, mỗi tin nhắn có `source` và `description` riêng. Không cần mã bổ sung—chỉ cần đảm bảo hệ thống ghi log của bạn có thể xử lý các cuộc gọi liên tiếp nhanh chóng.

### Ẩn Cảnh báo

Trong một số trường hợp hiếm, bạn có thể muốn bỏ qua một số thay thế nhất định (ví dụ, bạn biết một fallback cụ thể là chấp nhận được). Mở rộng logic của callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### An toàn Khi Đa luồng

`LoadOptions` của Aspose.Words không an toàn với đa luồng theo mặc định. Nếu bạn tải tài liệu song song, hãy tạo một thể hiện `LoadOptions` riêng cho mỗi luồng, hoặc đồng bộ hóa callback để tránh các điều kiện tranh chấp.

## Bước 5: Xác minh Phông chữ Được Thay thế trong Tài liệu Kết quả

Sau khi tải, bạn có thể muốn xác nhận rằng việc thay thế thực sự đã diễn ra. API cho phép bạn duyệt qua tất cả các run và kiểm tra tên phông chữ thực tế:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Đoạn mã này in mỗi run văn bản kèm theo phông chữ cuối cùng của nó. Đây là một kiểm tra nhanh hữu ích khi bạn xây dựng các pipeline chuyển đổi PDF tự động.

## Ví dụ Hoạt động Đầy đủ

Kết hợp tất cả lại, đây là chương trình hoàn chỉnh, sẵn sàng chạy:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Lưu lại dưới tên `FontSubstitutionInfo.java`, biên dịch bằng `javac`, và chạy `java FontSubstitutionInfo`. Bạn sẽ thấy các thông báo cảnh báo (nếu có) tiếp theo là danh sách các run và phông chữ cuối cùng của chúng.

## Hình ảnh Hỗ trợ

![Ảnh chụp màn hình đầu ra console hiển thị cảnh báo thay thế phông chữ](/images/font-substitution-warning.png "ví dụ cảnh báo thay thế phông chữ")

*Văn bản thay thế:* **capture font substitution warnings** – đầu ra console sau khi tải tài liệu có phông chữ thiếu.

## Kết luận

Bây giờ bạn đã biết cách **ghi lại cảnh báo thay thế phông chữ** bằng Aspose.Words for Java. Bằng cách cấu hình một đối tượng `LoadOptions` và cung cấp một `IWarningCallback` tùy chỉnh, bạn có được khả năng quan sát đầy đủ mọi sự kiện phông chữ thiếu mà nếu không sẽ ảnh hưởng ẩn lên giao diện tài liệu của bạn. Kỹ thuật này tích hợp trực tiếp vào việc xử lý **Aspose.Words font substitution**, đảm bảo **cảnh báo tải tài liệu** đáng tin cậy, và cung cấp cho bạn tính linh hoạt để ghi log, cảnh báo, hoặc hủy dựa trên quy tắc kinh doanh của mình.

### Tiếp theo là gì?

- Khám phá các mẫu **Java warning callback** cho các loại cảnh báo khác (ví dụ, `DEPRECATED_FEATURE`).
- Kết hợp cách tiếp cận này với **PDF conversion** để đảm bảo rằng các phông chữ được thay thế không làm phá vỡ bố cục.
- Tìm hiểu sâu hơn về **LoadOptions usage**—thử nghiệm với `Password`, `Encoding`, và `ResourceLoadingCallback` cho các kịch bản nâng cao hơn.

Bạn có thể tự do điều chỉnh callback, chuyển cảnh báo tới một framework ghi log, hoặc thậm chí ném một ngoại lệ tùy chỉnh nếu một phông chữ quan trọng bị thiếu. Không có giới hạn, và giờ đây bạn đã có nền tảng vững chắc để phát triển.

Chúc lập trình vui vẻ, và hy vọng tài liệu của bạn luôn hiển thị đúng như mong đợi!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}