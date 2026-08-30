---
category: general
date: 2026-08-04
description: Tải gạch chân markdown trong Java và giữ nguyên định dạng markdown khi
  tải markdown vào tài liệu. Thực hiện theo hướng dẫn từng bước này.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: vi
lastmod: 2026-08-04
og_description: Tải markdown có gạch chân trong Java và giữ nguyên định dạng markdown.
  Tìm hiểu cách tải markdown vào tài liệu với hỗ trợ gạch chân đầy đủ.
og_image_alt: Diagram showing load markdown underline process
og_title: Tải gạch chân markdown trong Java – hướng dẫn từng bước
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Tải gạch chân markdown trong Java – hướng dẫn lập trình đầy đủ
url: /vi/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tải gạch chân markdown trong Java – hướng dẫn lập trình đầy đủ

Nếu bạn cần **tải gạch chân markdown** khi chuyển đổi tệp Markdown thành đối tượng `Document`, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Bạn cũng sẽ học cách **tải markdown vào tài liệu** mà không mất bất kỳ kiểu gạch chân nào, đảm bảo định dạng Markdown gốc được bảo toàn hoàn toàn.

Bài học bao gồm mọi thứ bạn cần biết: các thư viện bắt buộc, từng bước cấu hình, và cách xác minh rằng định dạng gạch chân đã tồn tại sau khi nhập. Khi hoàn thành, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ dự án Java nào.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- Java 17 hoặc mới hơn đã được cài đặt (ví dụ sử dụng hệ thống module hiện đại)
- Phiên bản mới nhất của **GroupDocs.Viewer** (hoặc thư viện tương thích cung cấp `LoadOptions` và `Document`)
- Một tệp Markdown (`sample.md`) chứa văn bản có gạch chân, ví dụ `<u>underlined</u>` hoặc cú pháp GitHub‑flavored `__underlined__`
- Một IDE như IntelliJ IDEA hoặc VS Code, mặc dù bất kỳ trình soạn thảo văn bản nào cũng được

Các yêu cầu này đảm bảo mã chạy mà không cần cấu hình bổ sung.

## Tải gạch chân markdown – hướng dẫn chi tiết từng bước

Quá trình gồm ba hành động chính: tạo một thể hiện `LoadOptions`, bật phát hiện gạch chân, và cuối cùng tải tệp Markdown với các tùy chọn đó. Mỗi bước được giải thích dưới đây.

### Bước 1: Tạo `LoadOptions` cho tài liệu

`LoadOptions` cho phép bạn tùy chỉnh cách thư viện phân tích tệp nguồn. Tạo một thể hiện mới sẽ cho bạn một nền tảng sạch sẽ cho các thiết lập sau này.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

Đối tượng `LoadOptions` là điểm vào cho mọi tùy chỉnh liên quan đến nhập khẩu. Bạn sẽ dùng nó ở bước tiếp theo để bật phát hiện gạch chân.

### Bước 2: Bật phát hiện định dạng gạch chân khi tải

Mặc định, viewer có thể bỏ qua các thẻ gạch chân vì chúng ít gặp trong Markdown. Bật cờ này sẽ yêu cầu trình phân tích giữ nguyên các đoạn gạch chân.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Cài đặt `setImportUnderlineFormatting(true)` đảm bảo bất kỳ thẻ HTML `<u>` nào hoặc cú pháp gạch chân kiểu GitHub đều được chuyển thành kiểu gạch chân trong mô hình `Document`. Đây là hành động then chốt giúp **tải gạch chân markdown** hoạt động như mong đợi.

### Bước 3: Tải tệp Markdown bằng các tùy chọn đã cấu hình

Bây giờ bạn có thể tải tệp. Truyền đối tượng `loadOptions` vào hàm khởi tạo `Document` để trình phân tích tôn trọng cờ gạch chân.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Khi hàm khởi tạo hoàn tất, `markdownDoc` sẽ chứa một biểu diễn đầy đủ trong bộ nhớ của nguồn Markdown, bao gồm các đoạn gạch chân.

### Bước 4: Xác minh rằng định dạng gạch chân được bảo toàn

Một kiểm tra nhanh sẽ giúp bạn xác nhận rằng **bảo toàn định dạng markdown** đã thành công. Đoạn mã dưới đây in ra văn bản của mỗi đoạn và đánh dấu các phần gạch chân bằng dấu ngã (`~`) để dễ quan sát.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Kết quả mong đợi** (giả sử `sample.md` chứa `This is __underlined__ text`):

```
This is ~underlined~ text
```

Các dấu ngã cho thấy kiểu gạch chân đã tồn tại sau khi nhập, xác nhận rằng thao tác **tải markdown vào tài liệu** đã bảo toàn định dạng gốc.

## Những lỗi thường gặp và cách tránh

| Triệu chứng | Nguyên nhân | Cách khắc phục |
|---|---|---|
| Gạch chân biến mất sau khi tải | `setImportUnderlineFormatting` để ở mặc định `false` | Đảm bảo gọi `loadOptions.setImportUnderlineFormatting(true)` trước khi tạo `Document`. |
| Chỉ một phần văn bản được gạch chân | Cú pháp Markdown hỗn hợp (ví dụ HTML `<u>` kết hợp với `__underline__`) | Thư viện hỗ trợ cả hai; kiểm tra tệp nguồn sử dụng cùng một kiểu đánh dấu gạch chân. |
| Tài liệu không tải được | Đường dẫn tệp sai hoặc thiếu phụ thuộc thư viện | Dùng đường dẫn tuyệt đối hoặc đặt `sample.md` tương đối với thư mục làm việc; bao gồm các JAR viewer trong classpath. |

**Mẹo:** Nếu bạn cũng cần giữ nguyên kiểu in đậm hoặc in nghiêng, bật chúng bằng `setImportBoldFormatting(true)` và `setImportItalicFormatting(true)` tương ứng. Kết hợp các cờ này sẽ cho bạn một quá trình nhập khẩu trung thực cho hầu hết các kiểu Markdown phổ biến.

## Ví dụ đầy đủ có thể chạy

Dưới đây là một chương trình Java tự chứa, kết hợp tất cả các bước. Sao chép mã vào tệp có tên `LoadMarkdownUnderlineDemo.java`, điều chỉnh đường dẫn tệp, và chạy bằng `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Chạy chương trình sẽ in nội dung tài liệu kèm dấu gạch chân, chứng minh tính năng **tải gạch chân markdown** hoạt động và bạn có thể **bảo toàn định dạng markdown** xuyên suốt quy trình nhập khẩu.

## Kết luận

Bạn đã biết cách **tải gạch chân markdown** trong Java, cách **tải markdown vào tài liệu** mà vẫn giữ nguyên kiểu dáng gốc, và cách xác minh rằng định dạng gạch chân vẫn còn nguyên vẹn. Cách tiếp cận này hoạt động với các phiên bản mới nhất của GroupDocs.Viewer và có thể mở rộng để hỗ trợ các tính năng Markdown bổ sung như in đậm, in nghiêng và bảng.

Tiếp theo, khám phá các chủ đề liên quan như **bảo toàn định dạng markdown cho bảng**, **chuyển đổi Markdown sang PDF**, hoặc **định dạng tùy chỉnh các phần tử Markdown đã nhập**. Điều chỉnh các cờ `LoadOptions` để phù hợp với yêu cầu định dạng chính xác của ứng dụng, và bạn sẽ có quyền kiểm soát chi tiết từng bước nhập khẩu. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong bài viết này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thành thạo tùy chọn tải Markdown với Aspose.Words cho Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Thành thạo tùy chọn tải Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}