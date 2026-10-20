---
category: general
date: 2026-08-01
description: Cách đặt bóng cho hình dạng Word bằng Aspose.Words cho Python. Tìm hiểu
  cách thay đổi độ trong suốt, điều chỉnh độ mờ và thay đổi khoảng cách bóng một cách
  nhanh chóng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: vi
lastmod: 2026-08-01
og_description: Cách đặt bóng cho một hình dạng bằng Aspose.Words cho Python. Thực
  hiện theo hướng dẫn từng bước này để thay đổi độ trong suốt, điều chỉnh độ nhòe
  và thay đổi khoảng cách bóng.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Cách đặt bóng trong Aspose.Words – Hướng dẫn nhanh Python
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Cách thiết lập bóng trong Aspose.Words – Ví dụ Python
url: /vi/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Bóng Đổ trong Aspose.Words – Ví Dụ Python

Bạn đã bao giờ tự hỏi **cách đặt bóng đổ** cho một hình dạng Word mà không cần mở tài liệu thủ công chưa? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi tự động hoá báo cáo hoặc tạo mẫu đồng nhất với thương hiệu. Tin tốt là gì? Với Aspose.Words cho Python, bạn có thể điều chỉnh bóng, độ mờ, độ mờ Gaussian và khoảng cách của một shape chỉ trong vài dòng mã.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được, cho thấy **cách đặt bóng đổ**, **cách thay đổi độ trong suốt**, **cách điều chỉnh độ mờ**, và thậm chí **cách thay đổi khoảng cách bóng**. Khi kết thúc, bạn sẽ nắm vững **cách sử dụng Aspose.Words** để tạo kiểu cho các shape một cách lập trình.

---

![Cách đặt bóng đổ cho một shape bằng Aspose.Words](image-placeholder.png){alt="Cách đặt bóng đổ cho một shape bằng Aspose.Words"}

## Yêu Cầu Trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

| Yêu cầu | Lý do |
|-------------|--------|
| Python 3.8+ | Cú pháp hiện đại, hỗ trợ type hints |
| Gói `aspose-words` (pip install aspose-words) | Thư viện cốt lõi để thao tác Word |
| Một tệp mẫu `input.docx` có ít nhất một shape | Shape mà chúng ta sẽ thêm bóng |
| Quyền ghi vào thư mục sẽ lưu `output.docx` | Để lưu các thay đổi |

Không cần DLL hay COM interop—Aspose.Words là thuần Python, vì vậy bạn có thể chạy trên Windows, macOS hoặc Linux.

---

## Cách Đặt Bóng Đổ cho Shape bằng Aspose.Words

Dưới đây là script **đầy đủ**. Nó tải tài liệu, tìm shape đầu tiên (đệ quy), cấu hình bóng, và lưu kết quả. Mỗi dòng đều có chú thích để bạn hiểu **tại sao** nó có mặt, không chỉ **cái gì** nó làm.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Tại Sao Điều Này Hoạt Động

* **`doc.get_child(..., True)`** – Tham số `True` báo cho Aspose.Words tìm **đệ quy**, vì vậy ngay cả các shape nằm trong header, footer hoặc các đối tượng nhóm cũng được phát hiện. Điều này quan trọng khi bạn không biết chính xác shape nằm ở đâu.
* **`shadow_format`** – Thuộc tính này gom tất cả các cài đặt liên quan đến bóng. Bằng cách đặt `distance`, `blur` và `opacity` bạn kiểm soát độ sâu thị giác của shape. Thay đổi bất kỳ giá trị nào trong số này sẽ minh họa **cách thay đổi độ trong suốt**, **cách điều chỉnh độ mờ**, và **cách thay đổi khoảng cách bóng** trong một lời gọi duy nhất, gọn gàng.
* **Lưu** – `doc.save` ghi ra một file `.docx` mới. File gốc vẫn không bị thay đổi, đây là mẫu an toàn cho việc xử lý hàng loạt.

---

## Cách Thay Đổi Độ Trong Suốt của Bóng Đổ Shape

Độ trong suốt quyết định mức độ trong suốt của bóng. Giá trị nằm trong khoảng 0.0 (hoàn toàn vô hình) đến 1.0 (đậm đặc). Trong đoạn mã trên, bạn chỉ cần sửa đối số `opacity`:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Mẹo chuyên nghiệp:** Khi tạo PDF sau này, độ trong suốt cao hơn thường tạo ra bóng đổ sâu hơn, dễ in hơn. Thử nghiệm các giá trị từ 0.4 đến 0.9 để tìm mức phù hợp với quy chuẩn thương hiệu của bạn.

---

## Cách Điều Chỉnh Độ Mờ Để Có Độ Nhẹ Nhàng Hơn

Độ mờ là bán kính Gaussian được áp dụng cho các cạnh bóng. Số lớn hơn tạo ra hiệu ứng feathered:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Nếu bạn muốn một bóng đổ sắc nét (giống kiểu “Microsoft PowerPoint”), hãy đặt `blur` ở mức thấp như `1.0`.

---

## Thay Đổi Khoảng Cách Bóng Để Tạo Độ Sâu

Khoảng cách được đo bằng điểm (1 pt = 1/72 in). Đẩy bóng ra xa hơn làm cho shape trông như đang nổi lên:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Kết hợp `distance` lớn hơn với `blur` vừa phải để có hiệu ứng “nâng lên” ấn tượng.

---

## Kết Hợp Tất Cả – Dự Án Nhỏ

Hãy tưởng tượng bạn đang xây dựng một công cụ tạo báo cáo tự động, chèn logo công ty vào một textbox. Bạn muốn mọi logo đều có một bóng nhẹ, phù hợp với phong cách công ty. Bằng cách sử dụng hàm `apply_shadow`, bạn có thể:

1. **Tạo tài liệu** (hoặc tải một mẫu).
2. **Chèn shape logo** (qua `DocumentBuilder.insert_image` hoặc `Shape`).
3. **Gọi `apply_shadow`** với các thông số bóng của thương hiệu.
4. **Xuất** ra DOCX, PDF, hoặc HTML chỉ bằng một dòng lệnh.

Vì hàm nhận các tham số, bạn có thể lưu các cài đặt bóng trong file JSON và áp dụng chúng cho hàng chục tài liệu—không cần chỉnh sửa thủ công.

---

## Câu Hỏi Thường Gặp & Các Trường Hợp Đặc Biệt

| Câu hỏi | Trả lời |
|----------|--------|
| **Nếu tài liệu có nhiều shape thì sao?** | Ví dụ chỉ nhắm vào *shape đầu tiên*. Để ảnh hưởng tới tất cả shape, hãy lặp qua `doc.get_child_nodes(aw.NodeType.SHAPE, True)` và áp dụng cùng một cài đặt `shadow_format` cho mỗi node. |
| **Có thể đặt màu bóng khác không?** | Chắc chắn. Dùng `shape.shadow_format.color = aw.Color(255, 0, 0)` để có bóng màu đỏ, hoặc bất kỳ `aw.Color` nào bạn muốn. |
| **Các cài đặt này có được giữ lại khi chuyển sang PDF không?** | Có. Aspose.Words giữ nguyên thuộc tính bóng khi render sang PDF, mặc dù các giá trị blur rất cao có thể được xấp xỉ. |
| **Hiệu năng có bị ảnh hưởng cho tài liệu lớn không?** | API bóng chỉ thao tác trên các đối tượng shape, vì vậy ngay cả báo cáo 500 trang cũng xử lý trong vài mili giây. Điểm nghẽn thường là I/O, không phải cấu hình bóng. |
| **Có thể loại bỏ bóng sau này không?** | Đặt `shape.shadow_format.is_visible = False` hoặc đơn giản đặt lại các thuộc tính về mặc định. |

---

## Tóm Tắt Ví Dụ Hoạt Động Đầy Đủ

Dưới đây là toàn bộ script một lần nữa, đã loại bỏ các chú thích để bạn có thể sao chép nhanh:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Chạy script, mở `output.docx`, và bạn sẽ thấy shape có một bóng đẹp mắt phù hợp với các tham số bạn đã thiết lập.

---

## Kết Luận

Chúng tôi đã bao phủ **

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây liên quan chặt chẽ và mở rộng các kỹ thuật đã trình bày trong bài viết này. Mỗi tài nguyên đều bao gồm mã nguồn đầy đủ và giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API khác và khám phá các cách triển khai thay thế trong dự án của mình.

- [Hướng dẫn Shadow cho Shape trong Aspose.Words – Thêm Shadow vào Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cách triển khai bình luận và trả lời trong tài liệu Word bằng Aspose.Words cho Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Cách quản lý biến tài liệu với Aspose.Words trong Python: Hướng dẫn đầy đủ](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}