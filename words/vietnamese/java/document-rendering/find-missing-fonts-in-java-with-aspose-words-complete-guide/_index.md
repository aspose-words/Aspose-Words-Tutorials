---
category: general
date: 2026-06-08
description: Tìm các phông chữ thiếu nhanh chóng bằng Aspose.Words cho Java. Học cách
  chẩn đoán cảnh báo thay thế phông chữ và khắc phục các vấn đề phông chữ thiếu chỉ
  trong vài bước.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: vi
og_description: Tìm các phông chữ thiếu trong tệp DOCX của bạn bằng Aspose.Words for
  Java. Hướng dẫn này chỉ cách bật chẩn đoán, đọc các sự kiện FontSubstitutionWarning
  và xuất tên phông chữ gốc so với phông chữ đã thay thế.
og_title: Tìm phông chữ thiếu trong Java – Hướng dẫn từng bước Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: Tìm các phông chữ thiếu trong Java với Aspose.Words – Hướng dẫn toàn diện
url: /vi/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tìm Kiếm Phông chữ Thiếu trong Java với Aspose.Words – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi làm thế nào để **tìm phông chữ thiếu** trong một tài liệu Word trước khi nó làm hỏng bố cục? Bạn không phải là người duy nhất—các nhà phát triển thường gặp phải việc thay thế phông chữ âm thầm khiến PDF hoặc báo cáo in ra bị hỏng. Tin tốt là Aspose.Words for Java cung cấp cho bạn một API chẩn đoán tích hợp giúp việc phát hiện những phông chữ thiếu trở nên dễ dàng.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ thực tế tải một tệp DOCX, bật việc thu thập cảnh báo, và in ra mọi *FontSubstitutionWarning* mà bạn cần biết. Khi kết thúc, bạn sẽ có thể ghi lại tên phông chữ gốc, phông chữ thay thế mà Aspose chọn, và quyết định có nên nhúng phông chữ thiếu hay không.

## Những gì bạn cần

* **Aspose.Words for Java** (phiên bản mới nhất 23.x) trên classpath của bạn.
* Môi trường phát triển Java 8+ (IDE bạn chọn, Maven/Gradle đều ổn).
* Một tệp DOCX mẫu có cố ý tham chiếu tới một phông chữ không được cài đặt trên máy của bạn—gọi nó là `MissingFonts.docx`.

Đó là tất cả. Không cần thư viện phụ, không cấu hình phức tạp, chỉ cần Java thuần và Aspose.

![Sơ đồ tìm phông chữ thiếu](https://example.com/find-missing-fonts.png "Sơ đồ tìm phông chữ thiếu")

*Hình ảnh trên minh họa quy trình: tải → chẩn đoán → cảnh báo → đầu ra.*

## Bước 1: Chuẩn bị LoadOptions và chỉ định Định dạng Tài liệu

Điều đầu tiên chúng ta làm là tạo một đối tượng **LoadOptions**. Điều này cho Aspose.Words biết cách diễn giải tệp đến và, quan trọng nhất, bật việc thu thập *cảnh báo tài liệu*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*Tại sao lại sử dụng LoadOptions?*  
Nếu không có nó, Aspose vẫn tải tệp nhưng có thể bỏ qua một số dữ liệu chẩn đoán. Bằng cách đặt định dạng một cách rõ ràng, bạn đảm bảo việc tạo cảnh báo nhất quán, đặc biệt khi làm việc với các tệp cũ hoặc bị hỏng.

## Bước 2: Tải Tài liệu với Chẩn đoán Được Bật

Bây giờ chúng ta thực sự đọc tệp. Hàm khởi tạo `Document` tự động bắt đầu thu thập cảnh báo, sau này sẽ bao gồm bất kỳ đối tượng **FontSubstitutionWarning** nào.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng Maven, thêm phụ thuộc Aspose.Words vào `pom.xml` của bạn. Như vậy JAR sẽ được tự động tải về và bạn sẽ không cần quản lý classpath thủ công.

## Bước 3: Quét Cảnh báo Tài liệu để Tìm Các Sự kiện Thay Thế Phông chữ

Aspose lưu mọi cảnh báo trong một bộ sưu tập mà bạn có thể lặp lại. Chúng tôi lọc các đối tượng `FontSubstitutionWarning` vì chúng chỉ ra một phông chữ thiếu đã được thay thế.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*Điều gì đang xảy ra ở đây?*  
`doc.getWarnings()` trả về một `List<WarningInfo>`. Bằng cách kiểm tra `instanceof FontSubstitutionWarning` chúng ta chỉ lấy các mục liên quan đến phông chữ, bỏ qua các cảnh báo khác như “tính năng không hỗ trợ” hoặc “chuyển đổi hình ảnh”.

## Bước 4: Xuất Tên Phông chữ Gốc và Phông chữ Thay Thế

Cuối cùng, chúng ta in ra cả tên phông chữ thiếu (gốc) và phông chữ mà Aspose chọn làm thay thế. Đầu ra này hoàn hảo cho việc ghi log hoặc đưa vào kiểm tra trong pipeline xây dựng.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### Đầu ra Console Dự Kiến

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

Nếu bạn không thấy gì được in, nghĩa là **không phát hiện phông chữ nào bị thiếu**—tài liệu của bạn đã chứa các phông chữ tồn tại trên máy chạy mã.

## Bước 5: Xử lý Các Trường hợp Cạnh và Những Cạm Bẫy Thông thường

### Phông chữ Thiếu nhưng Không Cảnh báo

Đôi khi một phông chữ được nhúng trong DOCX, nhưng việc nhúng bị hỏng. Aspose vẫn sẽ đưa ra `FontSubstitutionWarning` vì không thể hiển thị văn bản. Để phân biệt, kiểm tra `fsWarning.isFontEmbedded()` (có sẵn trong các phiên bản mới hơn).

### Nhiều Lần Thay Thế cho Cùng Một Phông chữ

Một phông chữ thiếu duy nhất có thể được thay thế nhiều lần trong các lần chạy khác nhau nếu thứ tự ưu tiên thay thế thay đổi (ví dụ, đầu tiên thử Arial, sau đó chuyển sang Helvetica). Giữ một `Set<String>` của `getOriginalFontName()` để loại bỏ trùng lặp nếu bạn chỉ cần danh sách các phông chữ thiếu duy nhất.

### Các Yếu tố Hiệu suất

Tải các tệp DOCX rất lớn (hàng trăm MB) trong khi thu thập cảnh báo có thể gây tốn tài nguyên. Nếu bạn chỉ cần chẩn đoán phông chữ, đặt `loadOptions.setValidateStructure(false)` để bỏ qua việc xác thực sâu. Điều này làm tăng tốc quá trình mà không ảnh hưởng đến việc tạo cảnh báo.

## Thêm: Tự động Nhúng Phông chữ

Khi bạn biết phông chữ nào bị thiếu, bạn có thể nhúng chúng một cách lập trình:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

Việc nhúng đảm bảo PDF cuối cùng hoặc DOCX đã lưu hiển thị chính xác như dự định trên bất kỳ máy nào—không còn các trường hợp thay thế bất ngờ.

## Tóm tắt: Cách Tìm Phông chữ Thiếu với Aspose.Words

- **Tạo LoadOptions** và đặt định dạng tải.  
- **Tải tài liệu** trong khi Aspose ghi lại các cảnh báo.  
- **Lặp qua `doc.getWarnings()`**, lọc các `FontSubstitutionWarning`.  
- **In** `getOriginalFontName()` và `getSubstitutedFontName()` để xem phông chữ nào bị thiếu.  
- **Tùy chọn:** loại bỏ trùng lặp, kiểm tra trạng thái nhúng, hoặc tự động nhúng các phông chữ thiếu.

Đó là giải pháp hoàn chỉnh để **tìm phông chữ thiếu** trong một ứng dụng Java sử dụng Aspose.Words. Bây giờ bạn có một cách đáng tin cậy để phát hiện sớm các vấn đề về phông chữ, giữ cho PDF của bạn luôn nhất quán và tránh những bất ngờ khó chịu trong môi trường sản xuất.

## Bạn nên khám phá gì tiếp theo?

* **Nhúng phông chữ** tự động (xem đoạn mã bonus).  
* **Tạo PDF** sau khi sửa phông chữ để xác minh kết quả hiển thị.  
* **Sử dụng FontSettings của Aspose.Words** để định nghĩa chuỗi thay thế tùy chỉnh.  
* **Chạy chẩn đoán tương tự trên các tệp DOC, RTF hoặc HTML**—chỉ cần thay đổi `LoadFormat` cho phù hợp.

Bạn có thể thoải mái thử nghiệm với các loại tài liệu và họa họa phông chữ khác nhau. Nếu gặp khó khăn, hãy để lại bình luận bên dưới hoặc kiểm tra tài liệu API Java chính thức của Aspose để tùy chỉnh sâu hơn.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị với những phông chữ bạn mong muốn!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Sử dụng Phông chữ trong Aspose.Words cho Java](/words/english/java/using-document-elements/using-fonts/)
- [Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng Dẫn Toàn Diện](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Cách Phát hiện Phông chữ trong Aspose.Words – Xử lý Cảnh báo & Cài đặt](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}