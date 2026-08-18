---
category: general
date: 2026-06-30
description: Cách đổi tên hình ảnh khi chuyển DOCX sang markdown. Tìm hiểu cách thay
  đổi tên hình ảnh và lưu Word dưới dạng markdown với tên tệp hình ảnh tùy chỉnh.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: vi
og_description: Cách đổi tên hình ảnh khi chuyển DOCX sang markdown. Hướng dẫn này
  chỉ cho bạn cách thay đổi tên hình ảnh, lưu Word dưới dạng markdown và sử dụng tên
  tệp hình ảnh tùy chỉnh.
og_title: Cách Đổi Tên Hình Ảnh Khi Chuyển Đổi DOCX Sang Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Cách Đổi Tên Hình Ảnh Khi Chuyển Đổi DOCX Sang Markdown
url: /vi/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đổi Tên Hình Ảnh Khi Chuyển DOCX Sang Markdown

Bạn đã bao giờ tự hỏi **cách đổi tên hình ảnh** một cách tự động khi chuyển một tệp DOCX sang Markdown chưa? Bạn không phải là người duy nhất. Trong nhiều quy trình tài liệu, các tên hình ảnh mặc định (như `image1.png`) trở thành cơn ác mộng để theo dõi, đặc biệt khi cùng một markdown được kiểm soát phiên bản giữa các nhóm.  

Tin tốt là Aspose.Words for Python giúp việc **đổi tên hình ảnh** trở nên dễ dàng, và bạn có thể giữ Markdown của mình sạch sẽ đồng thời duy trì một thư mục tài nguyên được đặt tên tùy chỉnh gọn gàng.  

Trong tutorial này bạn sẽ học cách:

* Tải một tài liệu Word (`.docx`) trong Python.  
* Gắn vào quá trình lưu Markdown bằng một callback để đặt tên cho mỗi hình ảnh dựa trên GUID.  
* Lưu tài liệu dưới dạng Markdown sao cho tệp tạo ra tham chiếu đến các hình ảnh đã được đổi tên.  

Nếu bạn đã quen với Python cơ bản và đã cài đặt Aspose.Words, bạn sẽ có thể thực hiện trong chưa tới năm phút. Không cần script bên ngoài, không cần đổi tên thủ công—chỉ một chương trình tự chứa duy nhất thực hiện toàn bộ công việc cho bạn.

---

## Yêu Cầu Trước — Những Gì Bạn Cần Trước Khi Bắt Đầu

| Requirement | Why It Matters |
|-------------|----------------|
| **Python 3.7+** | Ví dụ sử dụng f‑strings và type hints được giới thiệu từ 3.6, nhưng 3.7+ cung cấp tiện ích `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Thư viện này cung cấp lớp `aw.Document` và `MarkdownSaveOptions` mà chúng ta dựa vào. |
| **Write permission** to the output folder | Callback sẽ tạo các tệp hình ảnh mới, vì vậy script cần quyền ghi vào thư mục này. |
| **A DOCX file** you want to convert | Bất kỳ tệp nào từ báo cáo đơn giản tới tài liệu hướng dẫn phức tạp đều hoạt động. |

> **Pro tip:** Nếu bạn đang sử dụng môi trường ảo, hãy kích hoạt nó trước khi cài đặt Aspose.Words. Điều này cô lập các phụ thuộc và tránh xung đột phiên bản.

---

## Bước 1: Tải Tài Liệu Word  

Điều đầu tiên bạn làm khi muốn **convert docx to markdown** là mở tệp nguồn. Aspose.Words trừu tượng hoá toàn bộ việc xử lý OPC cấp thấp, vì vậy một dòng lệnh là đủ.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters:* Nếu không tải tài liệu, bạn không thể kiểm tra các tài nguyên của nó, và trình xuất Markdown sẽ không có gì để ghi. Đối tượng `aw.Document` giữ toàn bộ gói Word trong bộ nhớ, cho phép bạn thao tác an toàn trước khi lưu.

---

## Bước 2: Viết Callback Để **Đổi Tên Tài Nguyên Hình Ảnh**  

Aspose.Words cho phép bạn gắn một `resource_saving_callback` vào `MarkdownSaveOptions`. Callback nhận mỗi tài nguyên (hình ảnh, CSS, v.v.) ngay trước khi nó được ghi ra đĩa. Bằng cách thay đổi `resource.file_name` chúng ta có thể áp dụng **tên hình ảnh tùy chỉnh**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Tại Sao Sử Dụng GUID?

* **Uniqueness** – Một GUID (`uuid4`) đảm bảo rằng hai hình ảnh sẽ không bao giờ trùng nhau, ngay cả khi chạy nhiều lần.  
* **Traceability** – Nếu bạn cần debug sau này, GUID có thể được ghi lại cùng với số đoạn Word gốc.  
* **Portability** – Không phụ thuộc vào scheme đặt tên gốc của Word, có thể chứa dấu cách hoặc ký tự đặc biệt gây lỗi liên kết Markdown.

---

## Bước 3: Gắn Callback Vào Markdown Save Options  

Bây giờ chúng ta nói với Aspose sử dụng logic đổi tên của chúng ta mỗi khi nó ghi một hình ảnh vào thư mục đầu ra.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Explanation:* Lớp `MarkdownSaveOptions` điều khiển mọi thứ từ ngắt dòng tới vị trí thư mục hình ảnh. Bằng cách thiết lập `resource_saving_callback`, bạn có một **hook** được kích hoạt cho mỗi tài nguyên nhúng, cho phép bạn **đổi tên hình ảnh** trước khi tệp được ghi ra đĩa.

---

## Bước 4: Lưu Tài Liệu Thành Markdown – Phần Cuối Cùng  

Với callback đã được thiết lập, bước cuối cùng trở nên đơn giản.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Khi script kết thúc, bạn sẽ thấy:

* `CustomResources.md` – bản đại diện Markdown của tệp Word của bạn.  
* Thư mục `images/` (hoặc bất kỳ tên nào bạn đặt) chứa các tệp như `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

Tệp Markdown sẽ tham chiếu đến các tên tệp dựa trên GUID mới, vì vậy bất kỳ bộ xử lý hạ nguồn nào (GitHub, MkDocs, v.v.) sẽ lấy đúng hình ảnh mà không cần bạn đổi tên thủ công.

### Kết Quả Dự Kiến (đoạn trích)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

Các GUID sẽ khác nhau mỗi lần chạy, nhưng mẫu tên vẫn giữ nguyên.

---

## Xử Lý Các Trường Hợp Cạnh và Câu Hỏi Thường Gặp  

### Nếu tài liệu chứa tài nguyên không phải hình ảnh thì sao?

Callback của chúng ta đã kiểm tra phần mở rộng tệp và trả về `True` cho bất kỳ thứ gì không phải hình ảnh. Điều này có nghĩa là các tệp CSS, phông chữ, hoặc đối tượng OLE nhúng sẽ giữ nguyên tên gốc, thường là điều bạn muốn khi **save word as markdown**.

### Tôi có thể dùng scheme đặt tên tùy chỉnh thay vì GUID không?

Chắc chắn. Thay thế lời gọi `uuid.uuid4()` bằng bất kỳ hàm nào trả về một chuỗi. Ví dụ, bạn có thể thêm chỉ mục đoạn gốc vào trước:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Chỉ cần đảm bảo tên tạo ra là duy nhất trong toàn tài liệu.

### Điều này ảnh hưởng như thế nào đến hiệu năng trên tài liệu lớn?

Callback chạy một lần cho mỗi tài nguyên, vì vậy chi phí chỉ là thời gian tạo GUID. Ngay cả báo cáo 200 trang với hàng chục hình ảnh cũng hoàn thành trong chưa tới một giây trên laptop hiện đại.

### Nếu tôi cần tên file hình ảnh phải xác định được (ví dụ: cho CI builds) thì sao?

Thay `uuid.uuid4()` bằng hàm băm của dữ liệu ảnh gốc:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Điều này sẽ tạo ra cùng một tên file mỗi khi bạn chạy script trên cùng một ảnh nguồn.

---

## Script Hoàn Chỉnh – Sao Chép, Dán, Chạy  



## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ code hoàn chỉnh cùng giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [lưu docx thành markdown – Hướng dẫn C# đầy đủ với việc trích xuất hình ảnh](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [Cách Lưu Markdown từ DOCX – Hướng dẫn Từng Bước](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}