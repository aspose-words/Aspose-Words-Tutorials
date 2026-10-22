---
category: general
date: 2026-10-16
description: Tạo một tài liệu Word trống, chèn hình dạng vào Word, thêm bóng đổ bên
  ngoài và lưu dưới dạng PDF bằng Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: vi
lastmod: 2026-10-16
og_description: Tạo một tài liệu Word trống với hình dạng bóng ngoài bằng Aspose.Words
  cho Python. Hướng dẫn này chỉ cách chèn hình dạng, áp dụng bóng và lưu tệp dưới
  dạng PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Tạo tài liệu Word trống với bóng hình – Hướng dẫn Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Tạo tài liệu Word trống với hình dạng có bóng trong Python
url: /vi/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống với hình dạng có bóng trong Python

Nếu bạn cần **tạo tài liệu Word trống** và thêm một đồ họa tùy chỉnh, hướng dẫn này sẽ giúp bạn. Chúng tôi sẽ hướng dẫn cách **chèn hình dạng trong Word**, áp dụng **hình dạng bóng ngoài**, và cuối cùng **lưu dưới dạng PDF bằng Python**.

Bạn sẽ học cách thiết lập Aspose.Words for Python, tạo một hình chữ nhật, tạo kiểu cho bóng của nó, và tạo một PDF giữ nguyên hiệu ứng hình ảnh. Không cần kinh nghiệm trước với Aspose API, nhưng bạn nên có kiến thức cơ bản về Python và cài đặt Python 3.10 hoặc mới hơn.

## Yêu cầu trước

* Python 3.10 hoặc mới hơn đã được cài đặt.
* Giấy phép Aspose.Words for Python đang hoạt động (bản dùng thử miễn phí đủ cho việc đánh giá).
* `pip` để cài đặt gói `aspose-words`.
* Quyền ghi vào thư mục nơi PDF sẽ được lưu.

Bạn có thể cài đặt thư viện bằng một lệnh duy nhất:

```bash
pip install aspose-words
```

## Tạo tài liệu Word trống – thiết lập môi trường

Bước đầu tiên là tạo một tệp Word trống sẽ đóng vai trò làm nền cho hình dạng.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` đại diện cho một tệp Word hoàn toàn trống. Bằng cách sử dụng `DocumentBuilder` bạn sẽ có quyền truy cập vào các phương thức như `insert_shape`, mà chúng ta sẽ dùng ở bước tiếp theo.

## Chèn hình dạng trong Word và đặt kích thước

Bây giờ chúng ta thêm một hình chữ nhật sẽ sau này nhận bóng ngoài. Kích thước được biểu thị bằng điểm (1 pt ≈ 1/72 inch).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Lệnh `insert_shape` trả về một đối tượng `Shape` mà bạn có thể tùy chỉnh thêm. Tại thời điểm này tài liệu đã chứa một hình chữ nhật có thể nhìn thấy khi mở trong Microsoft Word.

## Thêm bóng ngoài cho hình dạng – tùy chỉnh hiệu ứng

Aspose.Words cung cấp lớp `ShadowEffect` để định nghĩa các thuộc tính bóng như kiểu, độ mờ, khoảng cách và màu sắc.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Đặt `style` thành `OUTER` đảm bảo bóng xuất hiện bên ngoài viền của hình chữ nhật, tạo nên vẻ ngoài 3‑D nhẹ nhàng. Bạn có thể thử nghiệm với `blur` và `distance` để đạt được bóng chặt hơn hoặc lan tỏa hơn.

## Lưu dưới dạng PDF bằng Python – hoàn thiện tài liệu

Sau khi tạo kiểu cho hình dạng, tài liệu có thể được lưu trực tiếp dưới dạng PDF. Aspose.Words xử lý việc chuyển đổi nội bộ, giữ nguyên hiệu ứng bóng.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Khi bạn mở `shape_with_shadow.pdf` trong bất kỳ trình xem PDF nào, bạn sẽ thấy hình chữ nhật với bóng ngoài chính xác như khi nó xuất hiện trong Word.

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là đoạn script đầy đủ kết hợp tất cả các bước. Sao chép nó vào một tệp có tên `create_word_with_shadow.py` và chạy.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Kết quả mong đợi**

Chạy script sẽ in ra một dòng xác nhận, ví dụ:

```
PDF generated at: output/shape_with_shadow.pdf
```

Mở PDF kết quả sẽ hiển thị một trang duy nhất chứa hình chữ nhật 200 pt × 100 pt với bóng ngoài màu đen mềm.

## Các biến thể thường gặp và trường hợp đặc biệt

* **Thay đổi màu bóng** – Thay `aw.Color.black` bằng bất kỳ giá trị `aw.Color` nào khác, chẳng hạn `aw.Color.red` hoặc `aw.Color.from_argb(255, 0, 120, 215)`.
* **Sử dụng hình dạng khác** – Thay `aw.drawing.ShapeType.RECTANGLE` bằng `OVAL`, `DIAMOND`, hoặc bất kỳ giá trị enum nào được hỗ trợ.
* **Lưu dưới dạng DOCX thay vì PDF** – Gọi `doc.save("output/shape.docx")` để giữ định dạng Word.
* **Nhiều hình dạng** – Tạo các hình dạng bổ sung bằng cách gọi lại `builder.insert_shape`; mỗi hình dạng có thể có `ShadowEffect` riêng.

**Mẹo chuyên nghiệp:** Nếu bạn cần đặt hình dạng ở vị trí cụ thể, hãy thiết lập `rectangle.left` và `rectangle.top` sau khi chèn. Điều này cho phép bạn kiểm soát vị trí một cách chính xác đến pixel.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word trống**, **chèn hình dạng trong Word**, **thêm bóng ngoài cho hình dạng**, và **lưu dưới dạng PDF bằng Python**. Mẫu mã đầy đủ minh họa quy trình từ đầu đến cuối, và các giải thích làm rõ lý do mỗi lời gọi API là cần thiết.

Từ đây bạn có thể khám phá các tùy chọn tạo kiểu nâng cao hơn, thêm văn bản vào bên trong hình dạng, hoặc kết hợp nhiều hình dạng để xây dựng các sơ đồ phức tạp. Thử nghiệm các tham số bóng khác nhau để phù hợp với ngôn ngữ hình ảnh của thương hiệu, và tích hợp cách tiếp cận này vào các quy trình tạo tài liệu quy mô lớn.

Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình chữ nhật, thêm bóng & lưu PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Tạo PDF từ Word – Hướng dẫn Python đầy đủ với Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Thêm bóng cho hình dạng trong Word với Aspose.Words – Bước‑bước](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}