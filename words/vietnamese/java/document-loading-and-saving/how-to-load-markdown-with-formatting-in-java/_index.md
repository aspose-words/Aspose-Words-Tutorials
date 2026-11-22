---
category: general
date: 2026-11-22
description: Tìm hiểu cách tải markdown có định dạng trong Java. Hướng dẫn này chỉ
  cho bạn cách đọc markdown có định dạng bằng LoadOptions và Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: vi
lastmod: 2026-11-22
og_description: Cách tải markdown có định dạng trong Java. Hãy theo dõi hướng dẫn
  đầy đủ này để đọc markdown có định dạng, giữ nguyên kiểu gạch chân và làm việc với
  các đối tượng Document.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Cách tải markdown có định dạng trong Java – hướng dẫn từng bước
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Cách tải markdown với định dạng trong Java
url: /vi/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tải markdown có định dạng trong Java

Nếu bạn cần **cách tải markdown** đồng thời giữ nguyên các kiểu hiển thị, hướng dẫn này cung cấp cho bạn một giải pháp sẵn sàng chạy. Bạn sẽ thấy chính xác cách **đọc markdown có định dạng** như văn bản gạch chân, để tài liệu được hiển thị giống như nguồn gốc.

Hướng dẫn bao gồm mọi bước từ cấu hình bộ tải đến việc xác minh rằng định dạng vẫn còn sau khi nhập. Không cần công cụ bên ngoài nào ngoài thư viện GroupDocs.Viewer tiêu chuẩn (hoặc bất kỳ API tương thích nào cung cấp `LoadOptions` và `Document`). Khi hoàn thành, bạn có thể tích hợp việc tải markdown vào bất kỳ backend Java, dịch vụ web, hay ứng dụng desktop nào.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* Java 17 hoặc mới hơn.
* Maven hoặc Gradle để quản lý phụ thuộc.
* Truy cập vào file JAR GroupDocs.Viewer (hoặc tương đương) chứa `LoadOptions` và `Document`.
* Một file markdown mẫu (`sample.md`) có chứa markup gạch chân (ví dụ: `<u>underlined text</u>` hoặc `_underlined_` tùy theo parser).

## Bước 1: Thêm phụ thuộc cần thiết

Nếu bạn dùng Maven, thêm đoạn sau vào `pom.xml`. Điều chỉnh phiên bản về bản ổn định mới nhất.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Người dùng Gradle có thể thêm:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Việc đưa thư viện vào sẽ làm cho các lớp `LoadOptions` và `Document` có sẵn ở thời điểm biên dịch.

## Bước 2: Cấu hình LoadOptions để nhập định dạng gạch chân

Đối tượng `LoadOptions` cho parser biết những tính năng markdown nào cần bảo tồn. Bật định dạng gạch chân sẽ đảm bảo kiểu hiển thị xuất hiện trong `Document` kết quả.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Tại sao điều này quan trọng:**  
Nếu không gọi `setImportUnderlineFormatting(true)`, parser sẽ loại bỏ các thẻ gạch chân, để lại văn bản thuần. Bật cờ này giữ nguyên kiểu dáng, điều này rất cần thiết khi người tiêu dùng phía sau (ví dụ: trình tạo PDF) dựa vào các dấu hiệu trực quan.

## Bước 3: Tải tài liệu markdown bằng các tùy chọn đã cấu hình

Bây giờ bạn có thể đọc file markdown. Hàm khởi tạo `Document` nhận đường dẫn file và `LoadOptions` bạn vừa chuẩn bị.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Tại sao điều này quan trọng:**  
Việc truyền `LoadOptions` vào hàm khởi tạo `Document` đảm bảo parser tôn trọng cờ gạch chân trong suốt quá trình nhập. Đối tượng `Document` kết quả có thể được render, chuyển đổi, hoặc kiểm tra với đầy đủ định dạng.

## Bước 4: Xác minh định dạng gạch chân đã được giữ lại

Một cách nhanh để xác nhận rằng gạch chân vẫn tồn tại là render tài liệu ra HTML và in kết quả. HTML sẽ chứa thẻ `<u>` nếu việc nhập thành công.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Chạy toàn bộ chương trình sẽ hiển thị một đoạn HTML bao gồm `<u>underlined text</u>`. Nếu thẻ này thiếu, hãy kiểm tra lại rằng `setImportUnderlineFormatting(true)` đã được gọi trước khi tải file.

## Ví dụ hoàn chỉnh có thể chạy được

Kết hợp mọi thứ lại, dưới đây là một lớp Java tự chứa mà bạn có thể biên dịch và thực thi:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Kết quả mong đợi (rút gọn để ngắn gọn):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Nếu thẻ `<u>` xuất hiện, markdown đã được tải với định dạng nguyên vẹn.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống                              | Cần thay đổi gì                                                |
|----------------------------------------|--------------------------------------------------------------|
| **Các phần mở rộng markdown khác**      | Dùng `loadOptions.setImportBoldFormatting(true)` cho **đậm**. |
| **File lớn (> 10 MB)**                  | Dòng dữ liệu file bằng `FileInputStream` và truyền stream cho `Document`. |
| **Cần xuất PDF**                        | Sau khi tải, dùng `PdfViewOptions` với `Viewer` để tạo PDF giữ lại kiểu gạch chân. |
| **Chạy trong servlet container**       | Lưu `Document` trong phạm vi request và render ra HTML ngay lập tức. |

**Mẹo:** Luôn tạo một thể hiện `LoadOptions` mới cho mỗi lần tải. Việc tái sử dụng cùng một đối tượng trên nhiều luồng có thể gây rò rỉ trạng thái không mong muốn.

## Kết luận

Bây giờ bạn đã biết **cách tải markdown có định dạng trong Java** và **cách đọc markdown có định dạng** bằng `LoadOptions`. Ví dụ đầy đủ cho thấy cách cấu hình, tải và xác minh, để bạn có thể nhúng mẫu này vào bất kỳ dự án Java nào xử lý file markdown.  

Tiếp theo, khám phá các chủ đề liên quan như **đọc markdown có hình ảnh**, **chuyển markdown sang PDF**, hoặc **tùy chỉnh nhập các kiểu khác** (đậm, nghiêng, gạch ngang). Mỗi phần mở rộng này đều tuân theo cùng một mẫu: điều chỉnh các cờ trong `LoadOptions`, tải `Document`, và render ở định dạng mong muốn.

Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã nguồn hoàn chỉnh với các ví dụ hoạt động và giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to load markdown document in Java with custom import options](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [How to read and load a Markdown file in Java with Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [How to Load Markdown in Java – Complete Guide](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}