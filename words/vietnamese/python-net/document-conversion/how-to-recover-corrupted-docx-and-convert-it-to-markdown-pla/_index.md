---
category: general
date: 2026-10-13
description: Tìm hiểu cách khôi phục các tệp docx bị hỏng, chuyển đổi docx sang markdown,
  chuyển đổi docx sang văn bản thuần và lưu tài liệu dưới dạng markdown bằng Aspose.Words
  cho Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to recover corrupted word file
- convert docx to plain text
- how to save document as markdown
language: vi
lastmod: 2026-10-13
og_description: Khôi phục các tệp docx bị hỏng và chuyển đổi docx sang markdown, văn
  bản thuần và PDF bằng Aspose.Words cho Python. Tham khảo hướng dẫn đầy đủ này.
og_image_alt: Diagram showing recover corrupted docx workflow from loading to saving
  in multiple formats
og_title: Khôi phục file docx bị hỏng và chuyển đổi sang markdown, văn bản thuần,
  PDF – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to recover corrupted docx files, convert docx to markdown,
    convert docx to plain text, and save document as markdown using Aspose.Words for
    Python.
  headline: How to recover corrupted docx and convert it to markdown, plain text,
    and PDF with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document conversion
title: Cách khôi phục tệp docx bị hỏng và chuyển đổi sang markdown, văn bản thuần
  và PDF bằng Aspose.Words
url: /vi/python/document-conversion/how-to-recover-corrupted-docx-and-convert-it-to-markdown-pla/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách khôi phục docx bị hỏng và chuyển đổi nó sang markdown, văn bản thuần và PDF với Aspose.Words

Nếu bạn cần **khôi phục docx bị hỏng** , hướng dẫn này cho bạn một cách đáng tin cậy, lập trình để thực hiện. Sử dụng Aspose.Words cho Python, bạn có thể tải một tài liệu Word bị hỏng, trích xuất nội dung và sau đó **chuyển docx sang markdown**, **chuyển docx sang văn bản thuần**, hoặc thậm chí lưu kết quả dưới dạng PDF.

Việc khôi phục một tệp bị hỏng thường cảm giác như không còn lối thoát, nhưng chế độ khôi phục của Aspose.Words làm cho quá trình trở nên quyết định. Sau khi tài liệu được tải, bạn có thể xuất nó sang bất kỳ định dạng nào được thư viện hỗ trợ, bao gồm Markdown với các phương trình LaTeX, tệp văn bản thuần, và PDF nơi các hình dạng nổi trở thành thẻ nội tuyến.

Trong tutorial này bạn sẽ:

* Tải một tệp `.docx` có thể bị hỏng với chế độ khôi phục.
* Xuất tài liệu sang Markdown đồng thời giữ lại Office Math dưới dạng LaTeX.
* Lưu cùng nội dung dưới dạng văn bản thuần với các phương trình định dạng LaTeX.
* Tạo PDF mà các hình dạng nổi được gắn thẻ là phần tử nội tuyến.
* Điều chỉnh hiệu ứng bóng của hình dạng đầu tiên và lưu tệp đã chỉnh sửa.

**Yêu cầu trước:**

* Python 3.8+ đã được cài đặt.
* Gói `aspose-words` (`pip install aspose-words`).
* Một tệp `.docx` có thể bị hỏng (ví dụ: `corrupted.docx`).

---

## Cách khôi phục docx bị hỏng với Aspose.Words

Aspose.Words cung cấp lớp `LoadOptions` cho phép bạn chỉ định chiến lược khôi phục. Đặt `recovery_mode` thành `RECOVER` báo cho thư viện cố gắng sửa các vấn đề cấu trúc và tiếp tục tải.

```python
import aspose.words as aw

# Load the document in recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # RECOVER, SKIP, FAIL
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Tại sao cách này hoạt động:** Khi tệp Word chứa các phần bị hỏng (các nút XML thiếu, luồng bị cắt ngắn), chế độ khôi phục sẽ phân tích những gì có thể và loại bỏ các đoạn không thể khôi phục, ngăn ngừa ngoại lệ mà nếu không sẽ dừng chương trình.

> **Mẹo chuyên nghiệp:** Nếu bạn chỉ muốn bỏ qua các phần bị hỏng mà không cố gắng sửa, hãy dùng `RecoveryMode.SKIP`. Đối với kiểm tra nghiêm ngặt, `RecoveryMode.FAIL` sẽ ném lỗi khi gặp bất kỳ vấn đề nào.

---

## Chuyển docx sang markdown

Sau khi tài liệu được tải, bạn có thể lưu nó dưới dạng Markdown. Lớp `MarkdownSaveOptions` cho phép bạn kiểm soát cách xuất các phương trình Office Math. Đặt `office_math_export_mode` thành `LATEX` đảm bảo các phương trình xuất hiện dưới dạng mã LaTeX, là định dạng di động nhất cho tài liệu khoa học.

```python
# Save as Markdown with LaTeX equations
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
```

**Kết quả:** `output.md` chứa nội dung văn bản của tệp Word gốc, với các tiêu đề, danh sách và bảng được hiển thị bằng cú pháp Markdown. Bất kỳ phương trình nhúng nào cũng xuất hiện dưới dạng khối LaTeX `$…$`.

> **Câu hỏi thường gặp:** *Điều này có hoạt động với các tệp DOC không?*  
> Có. `MarkdownSaveOptions` giống nhau có thể được dùng với đầu vào `.doc` hoặc `.docx` vì quá trình chuyển đổi diễn ra sau khi tài liệu đã được tải hoàn toàn.

---

## Chuyển docx sang văn bản thuần

Xuất ra văn bản thuần hữu ích cho việc lập chỉ mục tìm kiếm hoặc xem nhanh. Lớp `TxtSaveOptions` phản chiếu các tùy chọn Markdown cho Office Math, cho phép bạn giữ các phương trình ở định dạng LaTeX ngay trong tệp `.txt`.

```python
# Save as plain text with LaTeX equations
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)
```

**Kết quả:** `output.txt` chứa văn bản thô của tài liệu, giữ nguyên các ngắt dòng, và các phương trình được biểu diễn dưới dạng chuỗi LaTeX (ví dụ: `\frac{a}{b}`).

---

## Lưu tài liệu dưới dạng PDF với hình dạng nội tuyến

Khi chuyển đổi sang PDF, bạn có thể cần các hình dạng nổi (hộp văn bản, hình ảnh) hoạt động như các phần tử nội tuyến để cải thiện khả năng truy cập hoặc xử lý tiếp theo. Lớp `PdfSaveOptions` cung cấp cờ `export_floating_shapes_as_inline_tag` buộc hành vi này.

```python
# Export to PDF, tagging floating shapes as inline
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)
```

**Kết quả:** `output.pdf` phản ánh bố cục của tệp Word gốc, nhưng bất kỳ hình dạng nổi nào cũng được đánh dấu là thẻ nội tuyến trong cấu trúc PDF, mà nhiều trình phân tích PDF coi là một phần của luồng văn bản.

---

## Điều chỉnh hiệu ứng bóng của hình dạng (tùy chọn)

Nếu bạn cần sửa đổi các khía cạnh hình ảnh của một hình dạng—ví dụ, để nâng cao một bài thuyết trình—bạn có thể truy cập trực tiếp nút hình dạng và thay đổi các thuộc tính bóng.

```python
# Locate the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()

# Adjust shadow parameters
shape.shadow.blur = 5.0          # Blur radius
shape.shadow.offset_x = 2.0     # Horizontal offset
shape.shadow.offset_y = 2.0     # Vertical offset

# Save the modified document
doc.save("YOUR_DIRECTORY/shadowed.docx")
```

**Tại sao cần điều chỉnh bóng:** Thay đổi độ mờ và độ lệch có thể làm cho hình dạng trông như được nâng lên khỏi trang, giúp cải thiện khả năng đọc trên tài liệu in hoặc hiển thị trên màn hình.

---

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là script đầy đủ tích hợp mọi bước đã mô tả ở trên. Lưu lại dưới tên `process_docx.py` và chạy từ dòng lệnh.

```python
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Load the potentially corrupted document using recovery mode.
# ------------------------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# ------------------------------------------------------------------
# 2. Export to Markdown (with LaTeX equations).
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_options)

# ------------------------------------------------------------------
# 3. Export to plain text (also with LaTeX equations).
# ------------------------------------------------------------------
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)

# ------------------------------------------------------------------
# 4. Export to PDF, tagging floating shapes as inline.
# ------------------------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)

# ------------------------------------------------------------------
# 5. Optional: modify the first shape's shadow and save a new DOCX.
# ------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shape.shadow.blur = 5.0
shape.shadow.offset_x = 2.0
shape.shadow.offset_y = 2.0
doc.save("YOUR_DIRECTORY/shadowed.docx")
```

**Các tệp đầu ra dự kiến**

| Tệp                | Mô tả                                                    |
|---------------------|----------------------------------------------------------|
| `output.md`         | Phiên bản Markdown với các phương trình LaTeX.          |
| `output.txt`        | Phiên bản văn bản thuần, các phương trình ở cú pháp LaTeX. |
| `output.pdf`        | PDF trong đó các hình dạng nổi được gắn thẻ là nội tuyến. |
| `shadowed.docx`     | Tài liệu gốc với bóng của hình dạng đầu tiên đã được thay đổi. |

Chạy script và xác nhận mỗi tệp xuất hiện trong `YOUR_DIRECTORY`. Mở tệp Markdown bằng trình xem hỗ trợ LaTeX (ví dụ: VS Code với extension preview Markdown) để xem các phương trình được hiển thị đúng.

---

## Câu hỏi thường gặp

**Làm sao khôi phục tệp Word bị hỏng mà không dùng Aspose?**  
Bạn có thể thử tính năng “Mở và Sửa” tích hợp sẵn của Microsoft Word, nhưng nó cung cấp kiểm soát hạn chế và không có khả năng xuất lập trình. Aspose.Words cung cấp khôi phục quyết định và cho phép tự động hoá các chuyển đổi tiếp theo.

**Có thể chuyển DOCX sang markdown mà không mất hình ảnh không?**  
Khi sử dụng `MarkdownSaveOptions`, hình ảnh được lưu thành các tệp riêng trong một thư mục con bên cạnh tệp `.md`. Markdown tham chiếu các tệp hình ảnh bằng đường dẫn tương đối, giữ nguyên bố cục hình ảnh.

**Nếu tài liệu chứa bảng có các ô được hợp nhất thì sao?**  
Aspose.Words giữ nguyên các ô hợp nhất trong quá trình chuyển đổi sang cả Markdown và văn bản thuần. Trong Markdown, các ô hợp nhất trở thành ô thường với các dấu gạch đứng (`|`) thích hợp; trong văn bản thuần, chúng xuất hiện dưới dạng các cột cách nhau bằng khoảng trắng.

**Chế độ xuất LaTeX có tương thích với các phiên bản cũ hơn của Aspose.Words không?**  
Xuất LaTeX cho Office Math được giới thiệu trong phiên bản 22.10. Nếu bạn dùng phiên bản cũ hơn, thuộc tính này sẽ không khả dụng và các phương trình sẽ quay lại sử dụng MathML.

---

## Các bước tiếp theo

Bây giờ bạn đã biết cách **khôi phục docx bị hỏng**, **chuyển docx sang markdown**, **chuyển docx sang văn bản thuần**, và **lưu tài liệu dưới dạng markdown**, bạn có thể mở rộng quy trình:

* **Xử lý hàng loạt** – lặp qua một thư mục các tệp bị hỏng và tạo tất cả các định dạng mục tiêu trong một lần chạy.
* **Triển khai trên đám mây** – đóng gói script trong Azure Function hoặc AWS Lambda để cung cấp dịch vụ chuyển đổi theo yêu cầu dưới dạng web service.
* **Hỗ trợ định dạng khác** – khám phá `HtmlSaveOptions`, `EpubSaveOptions`, hoặc `MhtmlSaveOptions` để có thêm khả năng xuất.

Thử nghiệm các tùy chọn do Aspose.Words cung cấp để tinh chỉnh việc xử lý hình ảnh, nhúng phông chữ, hoặc cài đặt bảo mật PDF. API phong phú của thư viện cho phép xây dựng một pipeline xử lý tài liệu hoàn chỉnh, bắt đầu từ khôi phục và kết thúc bằng các tài sản sẵn sàng xuất bản.

---


## Bạn nên học gì tiếp theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách xuất LaTeX từ Word – Chuyển DOCX sang Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)
- [Lưu Word dưới dạng Markdown với Aspose.Words – Hướng dẫn đầy đủ để chuyển DOCX và trích xuất hình ảnh](/words/english/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/)
- [cách khôi phục docx – đặt chế độ khôi phục & mở tệp Word bị hỏng](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}