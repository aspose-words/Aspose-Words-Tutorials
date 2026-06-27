---
category: general
date: 2026-06-27
description: Chuyển đổi docx sang markdown bằng Python. Tìm hiểu cách trích xuất hình
  ảnh từ Word và lưu đầu ra markdown với một callback tùy chỉnh.
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: vi
og_description: Chuyển đổi file docx sang markdown bằng Python, trích xuất hình ảnh
  từ Word và lưu kết quả markdown bằng callback tài nguyên tùy chỉnh.
og_title: Chuyển đổi docx sang markdown – Hướng dẫn Python với trích xuất hình ảnh
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: Chuyển đổi docx sang markdown – Hướng dẫn Python toàn diện với trích xuất hình
  ảnh
url: /vi/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển đổi docx sang markdown – Hướng dẫn Python đầy đủ với việc trích xuất hình ảnh

Bạn đã bao giờ tự hỏi làm thế nào để **convert docx to markdown** mà không mất các hình ảnh được nhúng trong tệp Word của mình? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi quá trình chuyển đổi bỏ qua hình ảnh, khiến markdown có các liên kết bị hỏng hoặc tệ hơn, không có hình ảnh nào cả.  

Tin tốt? Chỉ với vài dòng Python và Aspose.Words, bạn có thể chuyển đổi một `.docx` thành markdown sạch sẽ **và** trích xuất mọi hình ảnh vào một thư mục bạn chọn. Trong hướng dẫn này, chúng tôi sẽ đi qua toàn bộ quy trình, từ cài đặt thư viện đến thiết lập callback lưu mỗi hình ảnh ở nơi bạn muốn.

Khi kết thúc hướng dẫn này, bạn sẽ có thể **convert word to markdown**, trích xuất mọi đồ họa, và **save markdown output** sẵn sàng cho các công cụ tạo trang tĩnh, quy trình tài liệu, hoặc bất kỳ quy trình làm việc nào ưu tiên markdown.

## Những gì bạn cần

- Python 3.8 hoặc mới hơn (mã chạy trên 3.9+ cũng được)  
- Truy cập `pip` để cài đặt các gói bên thứ ba  
- Giấy phép Aspose.Words for Python hợp lệ (bản dùng thử miễn phí đủ cho việc đánh giá)  
- Một tệp mẫu `input.docx` chứa văn bản và ít nhất một hình ảnh  

Chỉ vậy—không cần cài đặt Office nặng, không cần COM interop, chỉ Python thuần.

## Bước 1: Cài đặt Aspose.Words cho Python

Đầu tiên, hãy lấy thư viện. Mở terminal và chạy:

```bash
pip install aspose-words
```

Nếu gặp lỗi quyền, hãy thêm `--user` hoặc sử dụng môi trường ảo. Khi cài đặt hoàn tất, bạn sẽ có quyền truy cập vào gói `aspose.words` (được nhập dưới tên `aw` trong các ví dụ).

> **Mẹo chuyên nghiệp:** Giữ file `requirements.txt` gọn gàng; thêm `aspose-words==<latest-version>` để các cộng tác viên có thể tái tạo môi trường một cách chính xác.

## Bước 2: Thiết lập Callback lưu ảnh tùy chỉnh

Aspose.Words cho phép bạn gắn vào quy trình lưu với một *resource‑saving callback*. Hãy nghĩ nó như một trung gian nhận luồng byte của mỗi hình ảnh và chỉ cho thư viện biết nơi tham chiếu trong tệp markdown được tạo.

Here’s the core of the callback:

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**Tại sao điều này quan trọng:**  
- **Kiểm soát** – Bạn quyết định cấu trúc thư mục, quy tắc đặt tên, hoặc thậm chí chuyển đổi định dạng ảnh nếu cần.  
- **Tính di động** – Đường dẫn tương đối trả về giúp markdown di động giữa các máy tính miễn là thư mục `images` đi cùng.  
- **Hiệu suất** – Callback chạy cho mỗi ảnh chỉ một lần, tránh ghi trùng lặp.

## Bước 3: Cấu hình Markdown Save Options

Bây giờ chúng ta gắn callback vào đối tượng `MarkdownSaveOptions`. Điều này cho Aspose.Words biết sử dụng `image_saver` của chúng ta mỗi khi gặp tài nguyên ảnh.

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

Bạn cũng có thể điều chỉnh một vài cài đặt tùy chọn ở đây, như `export_images_as_base64` (đặt `False` vì chúng ta muốn các tệp riêng) hoặc `add_table_of_contents` nếu cần mục lục. Trong hướng dẫn này, chúng tôi sẽ giữ nguyên các giá trị mặc định.

## Bước 4: Tải tài liệu Word nguồn

Loading a `.docx` is straightforward. Just point Aspose.Words at the file path:

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

Nếu tài liệu lớn, bạn có thể cân nhắc stream nó bằng `aw.LoadOptions`, nhưng trong hầu hết các trường hợp, hàm khởi tạo đơn giản đã đủ.

## Bước 5: Lưu dưới dạng Markdown – Để Callback thực hiện công việc nặng

Cuối cùng, chúng ta yêu cầu Aspose.Words ghi tệp markdown. Thư viện sẽ gọi `image_saver` cho mỗi ảnh được nhúng, lưu các tệp và chèn các liên kết ảnh markdown thích hợp.

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

Khi quá trình hoàn tất, bạn sẽ thấy hai điều:

1. `output.md` chứa văn bản markdown với các dòng như `![](images/image1.png)`  
2. Một thư mục con `images` chứa mỗi hình ảnh đã được trích xuất.

### Kết quả mong đợi

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

Mở `output.md` trong bất kỳ trình xem markdown nào (VS Code, GitHub, MkDocs) và bạn sẽ thấy hình ảnh được hiển thị chính xác như trong tệp Word gốc.

## Bước 6: Xác minh kết quả và xử lý các trường hợp đặc biệt

### Kiểm tra nhanh

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

Đảm bảo tên tệp ảnh khớp với các đường dẫn trong markdown. Nếu bạn thấy thiếu ảnh, hãy kiểm tra lại callback đã trả về **đường dẫn tương đối** (không phải tuyệt đối) và thư mục `images` được tham chiếu đúng.

### Xử lý tên ảnh trùng lặp

Word sometimes reuses the same internal name for different pictures. To avoid overwriting, you can tweak `image_saver`:

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### Chuyển đổi tài liệu lớn

For multi‑megabyte documents, consider streaming the output to avoid memory spikes:

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

Aspose.Words xử lý streaming nội bộ, vì vậy bạn không cần tải toàn bộ markdown vào RAM.

## Bước 7: Tự động hoá quy trình (Tùy chọn)

If you need to batch‑process a folder of Word files, wrap the logic in a loop:

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

Bây giờ bạn có thể đặt một trăm tệp `.docx` vào thư mục và để script xử lý chúng, mỗi tệp sẽ có thư mục con `images` riêng.

## Kết luận

Chúng tôi đã trình bày mọi thứ bạn cần để **convert docx to markdown** đồng thời giữ lại mọi hình ảnh, bằng cách sử dụng script Python sạch sẽ và cơ chế callback mạnh mẽ của Aspose.Words. Bây giờ bạn đã biết cách:

- **Trích xuất hình ảnh từ Word** qua một `resource_saving_callback` tùy chỉnh  
- **Convert word to markdown** với cấu hình tối thiểu  
- **Save markdown output** cùng với một thư mục ảnh được tổ chức gọn gàng  

Từ đây, bạn có thể thử nghiệm các phần mở rộng markdown bổ sung (bảng, chú thích) hoặc tích hợp script vào pipeline CI để tự động xây dựng tài liệu. Không gì là không thể—chỉ cần nhớ giữ logic lưu ảnh linh hoạt, markdown của bạn sẽ luôn gọn gàng.

Có câu hỏi về các trường hợp đặc biệt hoặc giấy phép? Hãy để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách lưu Markdown từ Word – Hướng dẫn Python đầy đủ](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Chuyển đổi tệp Docx sang Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [Chuyển đổi Word sang Markdown – Nhúng hình ảnh dưới dạng Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}