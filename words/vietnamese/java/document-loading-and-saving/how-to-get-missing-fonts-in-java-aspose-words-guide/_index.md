---
category: general
date: 2026-02-15
description: Tìm hiểu cách lấy các phông chữ bị thiếu khi tải tài liệu Word trong
  Java bằng Aspose.Words. Bao gồm các callback cảnh báo và xử lý thay thế phông chữ.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: vi
og_description: Cách lấy các phông chữ bị thiếu trong Java với Aspose.Words. Khám
  phá các callback cảnh báo, xử lý thay thế phông chữ và các thực tiễn tốt nhất cho
  việc xử lý tài liệu.
og_title: Cách lấy phông chữ bị thiếu trong Java – Hướng dẫn Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Cách lấy các phông chữ bị thiếu trong Java – Hướng dẫn Aspose.Words
url: /vi/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách lấy các phông chữ thiếu trong Java – Hướng dẫn Aspose.Words

Bạn đã bao giờ mở một tài liệu Word trong Java mà thấy các phông chữ bị thay thế lạ và tự hỏi **cách lấy các phông chữ thiếu** chưa? Bạn không phải là người đầu tiên gặp bất ngờ này. Trong nhiều ứng dụng doanh nghiệp, các cảnh báo phông chữ thiếu có thể làm mất đi độ chính xác hình ảnh của báo cáo, hợp đồng hoặc tài liệu marketing.

Tin tốt? Aspose.Words cung cấp cho bạn một cách sạch sẽ để bắt các cảnh báo này thông qua callback, cho phép bạn ghi log, thay thế, hoặc thậm chí thông báo cho người dùng trước khi tài liệu được render. Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được, cho thấy **cách lấy các phông chữ thiếu**, giải thích tại sao callback lại quan trọng, và đề cập một vài mẹo xử lý các trường hợp đặc biệt mà bạn có thể cần trong các dự án thực tế.

> **Mẹo chuyên nghiệp:** Nếu bạn đã sử dụng Aspose.Words 22.12 hoặc mới hơn, API được trình bày dưới đây sẽ hoạt động ngay mà không cần cấu hình thêm.

---

![Sơ đồ minh họa cách lấy các phông chữ thiếu bằng callback cảnh báo của Aspose.Words](how-to-get-missing-fonts-diagram.png "sơ đồ cách lấy các phông chữ thiếu")

## Nội dung hướng dẫn này

- Thiết lập **callback cảnh báo LoadOptions cho Java** để bắt các cảnh báo thay thế phông chữ.  
- Lọc các cảnh báo sao cho bạn chỉ thấy những cảnh báo liên quan đến phông chữ thiếu.  
- In ra một báo cáo rõ ràng, dễ đọc về các phông chữ đã được thay thế và chúng được thay bằng gì.  
- Các mẹo xử lý tài liệu lớn, tùy chỉnh mức độ cảnh báo, và tích hợp giải pháp vào pipeline xử lý lớn hơn.

Khi hoàn thành hướng dẫn này, bạn sẽ có thể trả lời câu hỏi “**cách lấy các phông chữ thiếu**?” bằng một đoạn mã sẵn sàng chạy và hiểu sâu về cơ chế bên trong.

### Yêu cầu trước

- Java 8 hoặc mới hơn đã được cài đặt.  
- Thư viện Aspose.Words for Java (tải từ trang chính thức hoặc thêm qua Maven/Gradle).  
- Một tài liệu Word tham chiếu tới phông chữ không được cài trên máy của bạn (ví dụ, `MissingFont.docx`).  

Nếu bạn còn thiếu bất kỳ thứ nào, hãy tải thư viện ngay—thêm vào Maven rất đơn giản:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Bước 1: Chuẩn bị một bộ sưu tập cho các cảnh báo thay thế phông chữ

Trước khi tải tài liệu, chúng ta cần một nơi để lưu trữ mọi cảnh báo mà Aspose.Words phát sinh. Một `ArrayList<WarningInfo>` hoạt động tốt vì nó giữ thứ tự và cho phép chúng ta duyệt lại sau.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Lý do quan trọng:* Callback cảnh báo có thể được kích hoạt hàng chục lần cho một tệp duy nhất—nghĩ đến mỗi glyph thiếu, mỗi vấn đề ảnh nhúng, v.v. Bằng cách thu thập chúng trước, bạn giữ cho giai đoạn tải nhanh và xử lý sau trong một vòng lặp kiểm soát.

---

## Bước 2: Cấu hình LoadOptions với Callback cảnh báo

Aspose.Words cho phép bạn gắn một `IWarningCallback`. Trong callback, chúng ta sẽ thêm mọi `WarningInfo` vào danh sách từ Bước 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Giải thích:* Phương thức `warning` được gọi **đồng bộ** trong quá trình tải tài liệu. Bằng cách chỉ đưa `WarningInfo` vào `fontWarnings`, chúng ta tránh bất kỳ I/O nặng nào (như ghi log vào file) có thể làm chậm quá trình tải. Mô hình “thu thập‑rồi‑xử lý” này là cách được khuyến nghị để xử lý lượng lớn cảnh báo.

---

## Bước 3: Tải tài liệu bằng các tùy chọn đã cấu hình

Bây giờ chúng ta thực sự đọc tệp Word. Nếu tài liệu chứa các phông chữ không được cài, Aspose.Words sẽ tự động thay thế chúng và kích hoạt callback cảnh báo mà chúng ta vừa thiết lập.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Điều gì xảy ra phía sau?* Aspose.Words phân tích bảng phông chữ của tệp, so sánh với các phông chữ có trên hệ điều hành, và với mỗi mục thiếu nó tạo một `WarningInfo` với `WarningSource.FontSubstitution`. Nguồn này là chìa khóa để chúng ta lọc ra các cảnh báo liên quan đến phông chữ thiếu.

---

## Bước 4: Lọc và hiển thị chỉ các cảnh báo thay thế phông chữ

Sau khi tải, `fontWarnings` có thể chứa hỗn hợp các thông điệp (ví dụ, tính năng lỗi thời, vấn đề ảnh). Chúng ta chỉ quan tâm đến phông chữ thiếu, vì vậy duyệt danh sách và in ra một báo cáo ngắn gọn.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Kết quả mẫu**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Lý do hữu ích:* Trường `description` cho bạn biết tài liệu yêu cầu phông chữ nào, trong khi `additionalInfo` cho biết Aspose.Words thực sự đã dùng phông chữ gì. Với dữ liệu này, bạn có thể:

- Yêu cầu người dùng cài đặt phông chữ thiếu.  
- Chèn một phông chữ thay thế vào tài liệu một cách lập trình (`doc.getFontInfos().add(...)`).  
- Ghi lại sự kiện để kiểm tra tuân thủ.

---

## Xử lý các trường hợp đặc biệt và biến thể phổ biến

### 1. Loại bỏ các cảnh báo không liên quan đến phông chữ

Nếu bạn chỉ muốn các thông điệp liên quan đến phông chữ, có thể thu hẹp callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Điều này giảm tải bộ nhớ khi xử lý các lô dữ liệu khổng lồ.

### 2. Điều chỉnh mức độ nghiêm trọng của cảnh báo

Aspose.Words phân loại cảnh báo bằng `WarningType`. Đối với phông chữ thiếu, bạn thường sẽ thấy `WarningType.FontSubstitution`. Nếu muốn coi chúng là lỗi (ví dụ, dừng tải), ném một ngoại lệ trong callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Làm việc với Streams thay vì Files

Đôi khi tài liệu đến từ cơ sở dữ liệu hoặc yêu cầu HTTP. Cùng một cách tiếp cận vẫn hoạt động với một `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Chỉ cần nhớ đóng stream sau khi tải.

### 4. Sử dụng thư mục phông chữ tùy chỉnh

Nếu bạn có một bộ sưu tập phông chữ công ty lưu trên ổ chia sẻ, chỉ định thư mục đó cho Aspose.Words:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Thư viện sẽ tìm kiếm ở đó *trước* khi quay lại các phông chữ hệ thống, giảm đáng kể số cảnh báo phông chữ thiếu.

---

## Ví dụ hoàn chỉnh

Kết hợp mọi thứ lại, đây là một lớp tự chứa bạn có thể đưa vào bất kỳ dự án Java nào:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Chạy chương trình này, bạn sẽ thấy danh sách gọn gàng của mọi phông chữ mà Aspose.Words đã phải thay thế. Không có thư viện phụ, không có phép thuật ẩn—chỉ Java thuần và sức mạnh của **API phông chữ thiếu của Aspose.Words**.

---

## Kết luận

Chúng ta đã trả lời câu hỏi cốt lõi **cách lấy các phông chữ thiếu** trong môi trường Java bằng Aspose.Words. Bằng cách gắn một callback cảnh báo `LoadOptions`, thu thập các đối tượng `WarningInfo`, và lọc các nguồn `FontSubstitution`, bạn có được khả năng quan sát toàn bộ vấn đề liên quan đến phông chữ trước khi bất kỳ quá trình render nào diễn ra. Cách tiếp cận này mở rộng từ công cụ đơn file tới các bộ xử lý hàng loạt khổng lồ, và đủ linh hoạt để hỗ trợ thư mục phông chữ tùy chỉnh, xử lý mức độ nghiêm trọng, hoặc đầu vào dạng stream.

Bước tiếp theo? Thử chèn các phông chữ đã thay thế trực tiếp vào tài liệu (`doc.getFontInfos().add(...)`) để tệp cuối cùng thực sự tự chứa, hoặc tích hợp báo cáo cảnh báo vào bảng điều khiển giám sát. Bạn cũng có thể khám phá các chủ đề liên quan như **xử lý tài liệu Java**, **cảnh báo thay thế phông chữ Aspose.Words**, và **callback cảnh báo LoadOptions Java** để nâng cao kỹ năng.

Chúc lập trình vui vẻ, và hy vọng tài liệu của bạn luôn hiển thị đúng phông chữ mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}