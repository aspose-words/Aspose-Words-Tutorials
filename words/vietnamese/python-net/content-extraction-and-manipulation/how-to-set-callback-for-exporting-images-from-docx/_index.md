---
category: general
date: 2026-06-24
description: Cách thiết lập callback để xuất ảnh từ DOCX khi lưu dưới dạng Markdown.
  Tìm hiểu cách trích xuất ảnh, trích xuất SVG từ Word và lưu DOCX dưới dạng Markdown
  với xử lý tùy chỉnh.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: vi
og_description: Cách thiết lập callback để xuất hình ảnh từ DOCX khi chuyển đổi sang
  Markdown. Hướng dẫn này chỉ cho bạn cách trích xuất hình ảnh và SVG một cách hiệu
  quả.
og_title: Cách thiết lập callback để xuất ảnh từ DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Cách thiết lập callback để xuất ảnh từ DOCX
url: /vi/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Callback Để Xuất Hình Ảnh Từ DOCX

Bạn đã bao giờ tự hỏi **cách đặt callback** để có thể **xuất hình ảnh từ DOCX** khi chuyển đổi sang Markdown chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi quá trình chuyển đổi mặc định đưa tất cả hình ảnh vào một thư mục chung hoặc, tệ hơn, mất hoàn toàn đồ họa SVG.  

Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp hoàn chỉnh, sẵn sàng chạy, trả lời câu hỏi “cách đặt callback”, chỉ ra **cách trích xuất hình ảnh**, và thậm chí đề cập **đến việc trích xuất SVG từ Word**. Khi kết thúc, bạn sẽ có thể **lưu DOCX dưới dạng Markdown** với một quy tắc đặt tên tùy chỉnh cho mỗi tài nguyên hình ảnh—không cần can thiệp thủ công.

## Những Điều Bạn Sẽ Học

- Tại sao một callback là cách sạch nhất để kiểm soát tên tệp hình ảnh trong quá trình chuyển đổi.  
- Cách gắn vào `MarkdownSaveOptions.resource_saving_callback` của Aspose.Words.  
- Mã từng bước để trích xuất **PNG**, **JPG**, **SVG**, và bất kỳ tài nguyên nhúng nào khác.  
- Mẹo xử lý va chạm tên, tệp lớn, và các quirks đường dẫn đa nền tảng.  

> **Mẹo chuyên nghiệp:** Nếu bạn đã sử dụng Aspose.Words trong một pipeline lớn hơn, bạn có thể chèn callback này mà không cần thay đổi phần còn lại của mã.

---

![Sơ đồ cách đặt callback](https://example.com/images/how-to-set-callback.png "cách đặt callback")

## Yêu Cầu Trước

- Python 3.8+ (ví dụ sử dụng f‑strings, vì vậy 3.6+ cũng ổn).  
- Gói `aspose-words` đã được cài đặt (`pip install aspose-words`).  
- Một tệp DOCX chứa cả hình ảnh raster **và** đồ họa vector (SVG).  
- Kiến thức cơ bản về hàm Python và I/O tệp.

Nếu bạn đã có những thứ trên, hãy bắt đầu.

---

## Cách Đặt Callback Để Xuất Hình Ảnh Từ DOCX

Lõi của giải pháp nằm trong một **callback lưu tài nguyên**. Aspose.Words sẽ gọi delegate này cho mỗi hình ảnh hoặc SVG mà nó muốn ghi khi bạn gọi `document.save`. Bằng cách trả về một tuple `(new_name, data)` bạn quyết định cả tên tệp và dữ liệu byte.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Tại Sao Cần Callback?

Nếu không có callback, Aspose.Words sẽ tạo các tệp có tên `image1.png`, `image2.svg`, … và đặt chúng trong một thư mục cạnh tệp Markdown. Điều này có thể chấp nhận được cho các demo nhanh, nhưng trong môi trường sản xuất bạn thường cần:

1. **Tên xác định** – hữu ích cho việc kiểm soát phiên bản hoặc xuất bản trên CDN.  
2. **Tránh va chạm** – hai hình ảnh có cùng tên gốc sẽ không ghi đè lên nhau.  
3. **Cấu trúc thư mục tùy chỉnh** – có thể bạn muốn tất cả tài nguyên nằm dưới `/assets/docs/`.

Callback cho phép bạn kiểm soát hoàn toàn ba yếu tố trên.

---

## Xuất Hình Ảnh Từ DOCX Bằng Callback Tài Nguyên

Dưới đây là triển khai callback. Nó băm dữ liệu nhị phân để tạo hậu tố duy nhất, giữ nguyên phần mở rộng gốc, và trả về tên tệp mới cùng với byte thô.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Xử Lý Các Trường Hợp Cạnh

- **Tệp lớn:** SHA‑256 hoạt động tốt với bất kỳ kích thước nào; hàm băm được tính trong bộ nhớ, vì vậy hãy chú ý đến giới hạn bộ nhớ nếu bạn xử lý các PDF khổng lồ.  
- **Thiếu phần mở rộng:** Một số tệp Word cũ có thể lưu hình ảnh mà không có phần mở rộng rõ ràng. Trong trường hợp đó `extension` sẽ rỗng; bạn có thể mặc định thành `.bin` hoặc kiểm tra vài byte đầu để đoán định dạng.  
- **Tài nguyên không phải hình ảnh:** Callback được gọi cho mọi tài nguyên ngoại vi (ví dụ, đối tượng OLE). Nếu bạn chỉ quan tâm đến hình ảnh/SVG, hãy lọc bằng `resource.type` trước khi tiếp tục.

---

## Cách Trích Xuất Hình Ảnh và SVG Từ Word

Bây giờ chúng ta gắn callback vào pipeline lưu Markdown. Đối tượng `MarkdownSaveOptions` cung cấp thuộc tính `resource_saving_callback` chính xác cho mục đích này.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Việc thiết lập `resource_folder` là tùy chọn nhưng thường rất hữu ích. Nếu bạn bỏ qua, các hình ảnh sẽ nằm cạnh tệp Markdown, có thể làm bừa bộn thư mục gốc dự án.

### Lưu Tài Liệu

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Khi chạy script, bạn sẽ thấy một loạt các tệp như:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

Và tệp `output.md` được tạo sẽ chứa các liên kết hình ảnh trỏ tới đúng những tên tệp đó:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Đó là phần **cách trích xuất hình ảnh** đang hoạt động—mọi bức tranh, raster hay vector, đều trở thành một tài nguyên riêng biệt, có tên duy nhất.

---

## Lưu DOCX Thành Markdown Với Xử Lý Hình Ảnh Tùy Chỉnh

Kết hợp tất cả, dưới đây là script đầy đủ mà bạn có thể sao chép‑dán vào một tệp có tên `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Tại sao cách này hoạt động:**  
- `resource_callback` đảm bảo mỗi hình ảnh nhận được một tên duy nhất, có thể tái tạo.  
- `resource_folder` giữ cho Markdown gọn gàng bằng cách tách các tài nguyên ra.  
- Các lệnh `os.makedirs` bảo vệ bạn khỏi lỗi “thư mục không tồn tại” khi script chạy trên máy mới.

---

## Trích Xuất SVG Từ Word – Còn Đồ Họa Vector?

SVG được xử lý giống như PNG bởi callback vì chúng cũng là một `resource`. Điểm khác biệt duy nhất là một số phiên bản Word cũ nhúng SVG dưới dạng *OfficeArt*, và Aspose.Words sẽ tự động chuyển chúng thành PNG raster trừ khi bạn bật **cờ preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Thêm dòng này trước khi lưu, và callback sẽ nhận được các tài nguyên có phần mở rộng `.svg`, giữ nguyên dữ liệu vector sắc nét—hoàn hảo cho tài liệu web đáp ứng.

---

## Câu Hỏi Thường Gặp & Những Cạm Bẫy

| Câu hỏi | Trả lời |
|----------|--------|
| **Nếu hai hình ảnh hoàn toàn giống nhau thì sao?** | Hàm băm SHA‑256 sẽ giống nhau, dẫn đến va chạm tên tệp. Nếu bạn cần cả hai bản sao, hãy bao gồm `resource.name` gốc trong quá trình tính hash (ví dụ, `hash(resource.name + resource.data)`). |
| **Có thể thay đổi thư mục theo loại tệp không?** | Có. Trong `resource_callback` bạn có thể kiểm tra `extension` và trả về đường dẫn như `f"png/{new_name}"` cho hình raster và `f"svg/{new_name}"` cho vector. |
| **Có hoạt động trên Linux/macOS không?** | Hoàn toàn có. Mã sử dụng `os.path` để trừu tượng hoá dấu phân cách đường dẫn. Chỉ cần đảm bảo bạn có tệp giấy phép Aspose.Words (`aspose.words.lic`) nếu đang dùng phiên bản trả phí. |
| **Về việc sử dụng bộ nhớ cho tài liệu lớn?** | Callback nhận **mảng byte đầy đủ** cho mỗi tài nguyên, nghĩa là hình ảnh sẽ tạm thời tồn tại trong bộ nhớ. Đối với các tệp đa gigabyte, bạn có thể muốn stream dữ liệu ra đĩa trong callback thay vì trả về nó. |

---

## Kết Luận

Bạn đã biết **cách đặt callback** để kiểm soát việc trích xuất hình ảnh khi **lưu DOCX thành Markdown**. Cách tiếp cận này cho phép bạn **xuất hình ảnh từ DOCX**, **trích xuất SVG từ Word**, và giữ cho Markdown của bạn sạch sẽ, có thể dự đoán.  

Trong một script tự chứa, chúng ta đã bao quát việc tải tài liệu, định nghĩa callback lưu tài nguyên, cấu hình `MarkdownSaveOptions`, và xử lý các trường hợp đặc biệt như va chạm tên và đồ họa vector. Kết quả là một tập hợp các tài nguyên có tên duy nhất nằm cạnh tệp Markdown được liên kết hoàn hảo—sẵn sàng cho các trình tạo site tĩnh, pipeline tài liệu, hoặc bất kỳ quy trình nào cần tài nguyên sạch sẽ, tái sử dụng.

**Bước tiếp theo?**  
- Thử kết hợp với một static‑site generator như MkDocs để tự động xuất bản tài liệu dựa trên Word.  
- Thử `markdown_options.export_images_as_base64 = True` nếu bạn muốn nhúng hình ảnh trực tiếp thay vì tạo tệp riêng.  
- Tìm hiểu sâu hơn các callback khác của Aspose.Words (ví dụ, `document_saving_callback`) để kiểm soát đầu ra Markdown ngay từ gốc.

Có câu hỏi thêm về **cách trích xuất hình ảnh** từ các định dạng Office khác, hoặc cần trợ giúp tùy chỉnh callback cho quy tắc đặt tên cụ thể? Hãy để lại bình luận bên dưới, chúc bạn lập trình vui!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong bài viết này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh cùng giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}