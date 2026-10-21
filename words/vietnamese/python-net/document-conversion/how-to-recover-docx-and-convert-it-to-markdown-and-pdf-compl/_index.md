---
category: general
date: 2026-05-30
description: Học cách khôi phục tệp docx, đặt bóng, và chuyển đổi docx markdown sang
  cả markdown và PDF bằng Aspose.Words cho Python. Bao gồm mã từng bước.
draft: false
keywords:
- how to recover docx
- convert docx markdown
- save as markdown
- save as pdf
- how to set shadow
language: vi
og_description: Cách khôi phục file docx, đặt bóng và lưu dưới dạng markdown hoặc
  pdf với Aspose.Words. Hướng dẫn đầy đủ cho các nhà phát triển.
og_title: Cách khôi phục DOCX và chuyển sang Markdown & PDF – Hướng dẫn Python
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to recover docx, set shadow, and convert docx markdown to
    both markdown and pdf using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to Recover DOCX and Convert It to Markdown and PDF – Complete Python
    Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Conversion
title: Cách Khôi Phục DOCX và Chuyển Đổi Sang Markdown và PDF – Hướng Dẫn Python Toàn
  Diện
url: /vi/python/document-conversion/how-to-recover-docx-and-convert-it-to-markdown-and-pdf-compl/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Khôi Phục DOCX và Chuyển Đổi Sang Markdown và PDF – Hướng Dẫn Python Đầy Đủ

Bạn đã bao giờ tự hỏi **cách khôi phục docx** khi file không mở được trong Word chưa? Có thể bạn nhận được một báo cáo bị hỏng từ khách hàng, hoặc một công việc batch ban đêm tạo ra một tài liệu chưa hoàn thiện. Trong những lúc như vậy, bạn không chỉ muốn một nút “thử lại”—bạn cần một cách đáng tin cậy để lấy những phần tốt, chỉnh sửa giao diện, và sau đó xuất kết quả ở các định dạng mà các bên liên quan thực sự sử dụng.

Đó chính là những gì chúng ta sẽ làm trong tutorial này. Chúng tôi sẽ chỉ cho bạn cách khôi phục một DOCX, **cách đặt bóng đổ** cho hình dạng đầu tiên, sau đó **chuyển đổi docx sang markdown**, **lưu dưới dạng markdown**, và cuối cùng **lưu dưới dạng pdf**—tất cả đều bằng thư viện mạnh mẽ Aspose.Words for Python. Khi kết thúc, bạn sẽ có một script duy nhất biến một file Word hỏng thành các đầu ra Markdown và PDF sạch sẽ, kèm theo hiệu ứng bóng nhẹ trên bất kỳ đồ họa nào.

> **Mẹo:** Mã này hoạt động với Aspose.Words 22.12 trở lên; các phiên bản cũ hơn có thể thiếu một số cờ tuân thủ PDF/UA mới.

---

## Những Gì Bạn Cần Chuẩn Bị

Trước khi bắt đầu, hãy chắc chắn bạn có những thứ sau:

| Yêu cầu | Lý do |
|---------|-------|
| Python 3.8+ | Cú pháp hiện đại và hỗ trợ type hints |
| Gói `aspose-words` (`pip install aspose-words`) | Thư viện cốt lõi để tải, chỉnh sửa và lưu |
| Một file DOCX (ngay cả file bị hỏng) | Tài liệu nguồn |
| Kiến thức cơ bản về hàm Python | Để dễ dàng theo dõi luồng xử lý |

Đó là tất cả—không cần DLL bổ sung, không cần cài đặt Office, và không cần các lời gọi hệ thống phức tạp. Aspose.Words sẽ thực hiện phần lớn công việc bên trong.

---

## ## Cách Khôi Phục DOCX và Tiếp Tục Làm Việc Với Nó

Điều đầu tiên chúng ta phải làm là tải tài liệu có khả năng bị hỏng trong **chế độ khôi phục**. Aspose.Words cung cấp lớp `DocumentLoadOptions` cho phép bạn bật `RecoveryMode`. Khi đặt thành `RECOVER`, thư viện sẽ cố gắng xây dựng lại cây node nội bộ, chỉ loại bỏ những phần không thể sửa chữa.

```python
import aspose.words as aw

# -------------------------------------------------
# Step 1 – Load the DOCX with recovery enabled
# -------------------------------------------------
load_opts = aw.loading.DocumentLoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

# Replace YOUR_DIRECTORY with the real path to your file
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)

print("Document loaded. Nodes recovered:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())
```

**Tại sao điều này quan trọng:** Nếu bạn bỏ qua việc khôi phục, hàm khởi tạo `Document` sẽ ném ra ngoại lệ ngay khi gặp lỗi, làm dừng toàn bộ pipeline. Bằng cách bật chế độ khôi phục, bạn sẽ nhận được một đối tượng `Document` có thể sử dụng ngay cả khi Word từ chối mở file.

---

## ## Cách Đặt Bóng Đổ cho Hình Dạng Đầu Tiên

Một bóng đổ nhẹ có thể làm cho logo hoặc sơ đồ nổi bật hơn, đặc biệt khi bạn xuất ra PDF/UA nơi các quy tắc truy cập được áp dụng. Đoạn mã dưới đây lấy node `Shape` đầu tiên trong tài liệu và cấu hình `ShadowFormat` cho nó.

```python
# -------------------------------------------------
# Step 2 – Find the first shape and apply a shadow
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shadow = first_shape.shadow_format

# Enable the shadow and tweak its appearance
shadow.visible = True
shadow.distance = 4          # distance of the shadow from the shape (points)
shadow.blur = 6              # blur radius (points)
shadow.color = aw.Color.gray
shadow.opacity = 0.7         # 70% opacity for a soft look

print("Shadow applied to shape:", first_shape.name)
```

**Cạm bẫy thường gặp:** Nếu tài liệu không chứa bất kỳ shape nào, `get_child` sẽ trả về `None` và script sẽ bị crash. Một câu lệnh guard ngắn gọn có thể cứu bạn:

```python
if first_shape is not None:
    # apply shadow (as above)
else:
    print("No shapes found – skipping shadow step.")
```

---

## ## Chuyển Đổi DOCX Sang Markdown (Lưu dưới dạng Markdown)

Bây giờ tài liệu đã ổn định và chỉnh sửa hình ảnh đã hoàn tất, chúng ta **chuyển đổi docx markdown**. Aspose.Words có thể xuất ra Markdown đồng thời xử lý các công thức Office Math, mà chúng tôi sẽ xuất dưới dạng LaTeX để giữ độ chính xác cao nhất.

```python
# -------------------------------------------------
# Step 3 – Export to Markdown, preserving Math as LaTeX
# -------------------------------------------------
md_options = aw.saving.MarkdownSaveOptions()
md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX

# Again, replace the path with your desired output location
md_path = "YOUR_DIRECTORY/Combined.md"
doc.save(md_path, md_options)

print("Markdown file saved to:", md_path)
```

**Bạn sẽ thấy gì:** File `.md` tạo ra chứa cú pháp Markdown thông thường cho đoạn văn, tiêu đề và danh sách, trong khi bất kỳ công thức nhúng nào sẽ xuất hiện dưới dạng khối LaTeX được bao quanh bởi `$$ … $$`. Mở nó trong VS Code hoặc bất kỳ trình xem Markdown nào để kiểm tra.

---

## ## Lưu dưới dạng PDF với Khả năng Truy cập (Lưu dưới dạng PDF)

Cuối cùng, chúng ta sẽ **lưu dưới dạng pdf** đồng thời đảm bảo các shape nổi mà chúng ta đã chỉnh sửa trước đó được xuất dưới dạng phần tử inline‑tag. Điều này giữ cho bố cục nhất quán trên mọi trình xem và đáp ứng tiêu chuẩn PDF/UA 1 cho khả năng truy cập.

```python
# -------------------------------------------------
# Step 4 – Export to PDF/UA with inline‑tagged floating shapes
# -------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1

pdf_path = "YOUR_DIRECTORY/Combined.pdf"
doc.save(pdf_path, pdf_options)

print("PDF file saved to:", pdf_path)
```

**Tại sao lại là PDF/UA?** PDF/UA (Universal Accessibility) thêm các thẻ mà trình đọc màn hình có thể hiểu, làm cho tài liệu của bạn thân thiện hơn với người dùng khuyết tật. Cờ `export_floating_shapes_as_inline_tag` cũng ngăn các shape bị tách rời khỏi văn bản xung quanh, một nguyên nhân phổ biến gây lệch bố cục.

---

## ## Script Đầy Đủ – Giải Pháp Một Cửa

Kết hợp tất cả lại, đây là một script sẵn sàng chạy, bao gồm **cách khôi phục docx**, **cách đặt bóng đổ**, **chuyển đổi docx markdown**, **lưu dưới dạng markdown**, và **lưu dưới dạng pdf**. Sao chép, dán và điều chỉnh đường dẫn file cho phù hợp với môi trường của bạn.

```python
import aspose.words as aw

def recover_and_convert(input_path: str, output_dir: str):
    # ---------- Load with recovery ----------
    load_opts = aw.loading.DocumentLoadOptions()
    load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    doc = aw.Document(input_path, load_opts)
    print(f"Loaded '{input_path}'. Node count:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())

    # ---------- Apply shadow to first shape ----------
    first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if first_shape is not None:
        shape = first_shape.as_shape()
        shadow = shape.shadow_format
        shadow.visible = True
        shadow.distance = 4
        shadow.blur = 6
        shadow.color = aw.Color.gray
        shadow.opacity = 0.7
        print(f"Shadow set on shape '{shape.name}'.")
    else:
        print("No shapes detected – shadow step skipped.")

    # ---------- Save as Markdown ----------
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
    md_path = f"{output_dir}/Combined.md"
    doc.save(md_path, md_options)
    print("Markdown saved at:", md_path)

    # ---------- Save as PDF/UA ----------
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True
    pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1
    pdf_path = f"{output_dir}/Combined.pdf"
    doc.save(pdf_path, pdf_options)
    print("PDF saved at:", pdf_path)

# Example usage – replace with your actual paths
if __name__ == "__main__":
    recover_and_convert("YOUR_DIRECTORY/input.docx", "YOUR_DIRECTORY")
```

Chạy script bằng `python recover_and_convert.py`. Nếu mọi thứ diễn ra suôn sẻ, bạn sẽ có hai file trong `YOUR_DIRECTORY`:

* **Combined.md** – Markdown sạch, LaTeX cho mọi công thức, và hình ảnh đã được thêm bóng đổ nhúng dưới dạng thẻ ảnh thông thường.
* **Combined.pdf** – PDF/UA‑tuân thủ, với bóng đổ của shape được giữ lại và các shape nổi được đặt inline.

---

## ## Kết Quả Mong Đợi & Kiểm Tra

| File | Những Điều Cần Kiểm Tra |
|------|--------------------------|
| `Combined.md` | Các tiêu đề Markdown chuẩn (`#`, `##`), danh sách bullet, và bất kỳ công thức nào hiển thị dưới dạng `$$ … $$`. Mở trong trình xem Markdown để xem định dạng. |
| `Combined.pdf` | Các thẻ truy cập (sử dụng “Read Out Loud” của Adobe Acrobat để kiểm tra), shape đầu tiên phải hiển thị bóng đổ màu xám nhẹ, và bố cục phải gần giống với DOCX gốc nhất có thể. |

Nếu PDF mở mà không có lỗi và Markdown hiển thị đúng, bạn đã **khôi phục thành công DOCX**, áp dụng chỉnh sửa hình ảnh, và xuất ra các định dạng mong muốn.

## Bạn Nên Học Gì Tiếp Theo?

- [how to recover docx with Aspose.Words – step by step](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Save docx as pdf with Aspose.Words – Complete C# Guide](/words/english/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}