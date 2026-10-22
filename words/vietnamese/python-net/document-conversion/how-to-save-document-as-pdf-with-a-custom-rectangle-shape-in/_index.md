---
category: general
date: 2026-10-07
description: Tìm hiểu cách lưu tài liệu dưới dạng PDF đồng thời thêm hình chữ nhật
  và bóng tùy chỉnh bằng Aspose.Words cho Python. Bao gồm mã từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: vi
lastmod: 2026-10-07
og_description: Lưu tài liệu dưới dạng PDF với hình chữ nhật tùy chỉnh bằng Aspose.Words
  cho Python. Tham khảo ví dụ đầy đủ để vẽ, tạo kiểu và xuất Word sang PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Lưu tài liệu dưới dạng PDF với hình chữ nhật – hướng dẫn Python đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Cách lưu tài liệu dưới dạng PDF với hình chữ nhật tùy chỉnh trong Python
url: /vi/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách lưu tài liệu dưới dạng PDF với hình chữ nhật tùy chỉnh trong Python

Nếu bạn cần **save document as PDF** trong khi thêm đồ họa tùy chỉnh, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Chúng tôi sẽ hướng dẫn tạo một tệp Word trống, **drawing a rectangle shape**, thiết lập kích thước, áp dụng bóng đổ có thể nhìn thấy, và cuối cùng **export Word to PDF** bằng thư viện Aspose.Words for Python.

Bạn sẽ có một tệp PDF chứa một hình chữ nhật được định vị hoàn hảo, sẵn sàng cho báo cáo, hoá đơn, hoặc bất kỳ kịch bản tự động hoá tài liệu nào. Không cần công cụ bên ngoài—chỉ cần Python và gói Aspose.Words.

## Những gì bạn cần

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | API Aspose.Words cho Python nhắm tới các trình thông dịch hiện đại. |
| `aspose-words` package (`pip install aspose-words`) | Cung cấp không gian tên `aw` được sử dụng trong các ví dụ mã. |
| Basic familiarity with Python and object‑oriented programming | Bài hướng dẫn thao tác với các đối tượng như `Document` và `Shape`. |
| Write permission to a folder where the PDF will be saved | Bước `save document as pdf` sẽ ghi tệp lên đĩa. |

> **Pro tip:** Sử dụng môi trường ảo (`python -m venv venv`) để giữ các phụ thuộc được cô lập.

## Cách lưu tài liệu dưới dạng PDF với hình chữ nhật

Dưới đây là một ví dụ đầy đủ, có thể chạy được. Mỗi bước được giải thích để bạn hiểu **why** chúng ta thực hiện hành động, không chỉ **what** mã thực hiện.

### Bước 1: Khởi tạo một tài liệu trống mới

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Tạo một đối tượng `Document` mới cung cấp cho bạn một bộ sưu tập trang sạch sẽ. Bạn cũng có thể tải một tệp *.docx* hiện có nếu muốn **export Word to PDF** sau này, nhưng bắt đầu với tài liệu trống giúp ví dụ tập trung hơn.

### Bước 2: Thêm hình chữ nhật vào tài liệu

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Bước `add rectangle shape` sử dụng `ShapeType.RECTANGLE`. Bằng cách gắn hình vào một đoạn văn, Aspose.Words biết vị trí để render nó trong PDF cuối cùng.

### Bước 3: Đặt kích thước hình chữ nhật

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Việc thiết lập **rectangle dimensions** một cách rõ ràng đảm bảo hình dạng hiển thị đồng nhất trên các nền tảng. Bạn cũng có thể sử dụng các hàm trợ giúp `convert_to_inches` nếu muốn dùng đơn vị imperial.

### Bước 4: (Tùy chọn) Áp dụng bóng tùy chỉnh có thể nhìn thấy

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Bóng giúp hình chữ nhật nổi bật trong PDF. Cờ `shadow.visible` là bắt buộc; nếu không, các thuộc tính khác sẽ không có hiệu lực.

### Bước 5: Lưu tài liệu dưới dạng PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Gọi `document.save` với phần mở rộng **.pdf** sẽ tự động **save document as pdf** bằng bộ render PDF tích hợp của Aspose.Words. Không cần các bước chuyển đổi bổ sung, vì vậy phương pháp này là cách được khuyến nghị để **export Word to PDF**.

> **Why this works:** Aspose.Words ghi bố cục của tài liệu, bao gồm hình chữ nhật và bóng của nó, trực tiếp vào luồng PDF. Quá trình này không mất dữ liệu và giữ nguyên chất lượng vector.

## Toàn bộ mã nguồn (script đơn)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Chạy script này sẽ tạo ra `shadow_rectangle.pdf` trông như sau:

![Sơ đồ PDF đã tạo hiển thị hình chữ nhật sau khi save document as pdf](placeholder-image.png)

*PDF chứa một trang duy nhất với một hình chữ nhật có bóng đen được đặt ở trung tâm tài liệu.*

## Các câu hỏi thường gặp và các trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Tôi có thể đặt hình chữ nhật ở vị trí cụ thể không?** | Có. Đặt `rectangle.left` và `rectangle.top` (theo điểm) trước khi lưu. |
| **Nếu tôi cần nhiều hình dạng?** | Tạo các đối tượng `Shape` bổ sung, cấu hình từng cái, và gắn chúng vào cùng một đoạn hoặc các đoạn khác nhau. |
| **Bóng có ảnh hưởng đến kích thước PDF không?** | Chỉ ảnh hưởng nhẹ; bóng được lưu dưới dạng siêu dữ liệu vector, không phải ảnh raster. |
| **Tôi có thể dùng cách này để chuyển đổi các tệp *.docx* hiện có không?** | Chắc chắn. Thay `aw.Document()` bằng `aw.Document("input.docx")` và các bước còn lại vẫn giữ nguyên. |
| **Có cách nào để thay đổi màu nền của hình chữ nhật không?** | Đặt `rectangle.fill_color = aw.drawing.Color.light_blue` (hoặc bất kỳ `Color` nào bạn muốn). |

## Các bước tiếp theo

Bây giờ bạn đã biết cách **save document as PDF** với hình chữ nhật tùy chỉnh, bạn có thể khám phá:

* **Export Word to PDF** với tiêu đề, chân trang và số trang.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) sử dụng cùng lớp `Shape`.  
* **Batch process** một thư mục các tệp Word, áp dụng cùng lớp phủ hình chữ nhật cho mỗi tệp.  

Các mở rộng này tuân theo cùng mẫu: tạo một hình, cấu hình các thuộc tính, và **save document as pdf**.

---

**Summary:** Bài hướng dẫn này đã chỉ cho bạn cách **save document as PDF** trong khi **add rectangle shape**, **set rectangle dimensions**, và áp dụng bóng tùy chỉnh bằng Aspose.Words cho Python. Script hoàn chỉnh đã sẵn sàng để sao chép, chạy và điều chỉnh cho các quy trình tự động hoá tài liệu của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình chữ nhật, thêm bóng & lưu PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Thêm hình chữ nhật vào PDF với Aspose.Words – Hướng dẫn từng bước](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Lưu tài liệu dưới dạng PDF với Aspose.Words – Hướng dẫn C# đầy đủ](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}