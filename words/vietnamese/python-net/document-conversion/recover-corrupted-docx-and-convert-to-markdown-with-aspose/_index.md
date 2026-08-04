---
category: general
date: 2026-08-04
description: Khôi phục các tệp docx bị hỏng bằng chế độ khôi phục của Aspose.Words
  và chuyển đổi docx sang markdown, xuất các phương trình dưới dạng LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: vi
lastmod: 2026-08-04
og_description: Khôi phục các tệp docx bị hỏng bằng chế độ khôi phục của Aspose.Words,
  sau đó chuyển docx sang markdown đồng thời xuất các phương trình dưới dạng LaTeX.
  Hãy làm theo hướng dẫn từng bước này để tạo thêm các đầu ra PDF và TXT.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Khôi phục tệp docx bị hỏng và chuyển đổi sang markdown – Hướng dẫn của Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: Khôi phục tệp docx bị hỏng và chuyển đổi sang markdown bằng Aspose
url: /vi/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Khôi phục file docx bị hỏng và chuyển đổi sang markdown với Aspose

Nếu bạn cần **khôi phục file docx bị hỏng**, Aspose.Words cung cấp chế độ khôi phục tích hợp có thể tự động sửa các tài liệu Word bị hỏng. Khi file đã được khôi phục, bạn có thể **chuyển đổi docx sang markdown**, và thậm chí **xuất các phương trình latex** để sử dụng liền mạch trong các tài liệu khoa học. Hướng dẫn này sẽ chỉ cho bạn cách thực hiện điều đó trong Python, cùng một vài tùy chọn bổ sung cho đầu ra PDF và văn bản thuần.

Bạn sẽ học cách:

* Tải một file DOCX có thể bị hỏng bằng chế độ khôi phục.  
* Lưu tài liệu đã khôi phục dưới dạng Markdown với các phương trình định dạng LaTeX.  
* Tạo phiên bản văn bản thuần (TXT) cũng chứa các phương trình LaTeX.  
* Xuất ra PDF trong khi gắn thẻ các hình dạng nổi như các phần tử nội tuyến.  
* Điều chỉnh bóng của một hình dạng và tạo PDF cuối cùng.

Không cần công cụ bên ngoài—chỉ cần thư viện Aspose.Words for Python miễn phí.

## Prerequisites

| Yêu cầu | Lý do quan trọng |
|-------------|----------------|
| Python 3.8+ | Yêu cầu bởi Aspose.Words cho Python |
| `aspose-words` package (`pip install aspose-words`) | Cung cấp không gian tên `aw` được sử dụng trong mã |
| A DOCX file that may be damaged (e.g., `corrupted.docx`) | Minh họa quy trình khôi phục |
| Write permission to the output directory | Script sẽ ghi một số file (`.md`, `.txt`, `.pdf`) |

Đảm bảo giấy phép Aspose.Words (bản dùng thử miễn phí hoặc đã mua) được cấu hình đúng nếu bạn vượt quá giới hạn đánh giá.

## Recover corrupted docx using Aspose.Words

Bước đầu tiên là thông báo cho Aspose.Words xem file đầu vào có thể bị hỏng. Điều này được thực hiện bằng `LoadOptions.recovery_mode`.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Tại sao cách này hoạt động:**  
`RecoveryMode.RECOVER` buộc bộ tải bỏ qua các lỗi cấu trúc và cố gắng xây dựng lại cây tài liệu. Nếu file chỉ bị hỏng một phần, hầu hết nội dung—bao gồm văn bản, hình ảnh và phương trình—sẽ được khôi phục.

**Mẹo:** Nếu bạn chỉ muốn xác thực một tài liệu mà không sửa chữa, hãy sử dụng `RecoveryMode.NO_RECOVERY`. Đối với khôi phục đầy đủ, giữ nguyên cài đặt như trên.

## Convert docx to markdown with LaTeX equations

Khi tài liệu đã ở trong bộ nhớ, bạn có thể lưu nó dưới dạng Markdown. Đặt `office_math_export_mode` thành `LATEX` cho Aspose.Words biết cách chuyển đổi mỗi phương trình Word thành chuỗi LaTeX.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

Kết quả `output.md` sẽ trông giống một file Markdown thông thường, nhưng mọi phương trình sẽ xuất hiện dưới dạng `$...$` (nội tuyến) hoặc `$$...$$` (hiển thị) dưới dạng mã LaTeX. Điều này rất quan trọng cho các công cụ downstream như Pandoc hoặc Jupyter notebook hiểu cú pháp LaTeX.

## How to use recovery mode for damaged files

Chế độ khôi phục có thể được tái sử dụng cho bất kỳ thao tác tải nào. Dưới đây là một mẫu ngắn gọn mà bạn có thể sao chép vào các script khác:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

Gọi `load_with_recovery("myfile.docx")` sẽ trả về một đối tượng `Document` mà Aspose.Words đã cố gắng sửa chữa. Hàm này thể hiện **cách sử dụng chế độ khôi phục** một cách an toàn trong các dự án.

## Export equations latex when saving to markdown and txt

Nếu bạn cũng cần một phiên bản văn bản thuần, cờ `office_math_export_mode` tương tự hoạt động với `TxtSaveOptions`.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

File `.txt` chứa văn bản thô của tài liệu Word, và mọi phương trình được biểu diễn dưới dạng mã LaTeX. Định dạng này hữu ích cho việc lập chỉ mục hoặc đưa nội dung vào các công cụ tìm kiếm hiểu LaTeX.

## Additional options: PDF with inline shapes and shape shadow

### Export floating shapes as inline tags

Các hình ảnh hoặc hộp văn bản nổi có thể gây ra vấn đề bố cục khi chuyển đổi sang PDF. Đặt `export_floating_shapes_as_inline_tag` buộc Aspose.Words xử lý những hình dạng này như các phần tử nội tuyến thông thường, giữ nguyên luồng hiển thị.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### Adjust the shadow of the first shape

Bạn có thể muốn cải thiện ngoại hình của một hình dạng cụ thể trước khi lưu PDF cuối cùng. Đoạn mã dưới đây truy cập node `Shape` đầu tiên, bật bóng và điều chỉnh các tham số hiển thị.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Kết quả:** `shadowed.pdf` trông giống hệt `output.pdf` nhưng hình dạng đầu tiên giờ đã có một bóng đen nhẹ, giúp cải thiện khả năng đọc trong các bài thuyết trình.

## Complete runnable script

Dưới đây là script đầy đủ kết hợp tất cả các bước. Sao chép nó vào một file có tên `recover_and_convert.py`, thay `YOUR_DIRECTORY` bằng đường dẫn thực tế, và chạy `python recover_and_convert.py`.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### Expected output

| File | Mô tả |
|------|-------------|
| `output.md` | Phiên bản Markdown của DOCX gốc. Tất cả các phương trình xuất hiện dưới dạng LaTeX (`$...$` hoặc `$$...$$`). |
| `output.txt` | Bản sao văn bản thuần |

## What Should You Learn Next?

Các hướng dẫn sau đây bao phủ các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách Sử Dụng Markdown: Chuyển Đổi DOCX sang Markdown với Các Phương Trình LaTeX](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [cách khôi phục docx với Aspose.Words – từng bước](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Khôi phục DOCX Bị Hỏng & Chuyển Đổi Word sang Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}