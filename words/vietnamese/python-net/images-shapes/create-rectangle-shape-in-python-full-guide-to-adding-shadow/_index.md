---
category: general
date: 2026-05-04
description: Tìm hiểu cách tạo hình chữ nhật, cách thêm hình có bóng, thay đổi màu
  bóng, thiết lập khoảng cách bóng và lưu tài liệu dưới dạng PDF bằng Aspose.Words
  cho Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: vi
og_description: Tạo hình chữ nhật với Aspose.Words cho Python, học cách thêm hình
  dạng, thay đổi màu bóng, thiết lập khoảng cách bóng và lưu tài liệu dưới dạng PDF.
og_title: Tạo hình chữ nhật – Thêm bóng, Thay đổi màu & Lưu dưới dạng PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Tạo hình chữ nhật trong Python – Hướng dẫn đầy đủ về cách thêm bóng và lưu
  dưới dạng PDF
url: /vi/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật – Hướng dẫn đầy đủ cho nhà phát triển Python

Bạn đã bao giờ cần **create rectangle shape** trong một tài liệu Word và tự hỏi làm sao để thêm một bóng mờ tinh tế? Có thể bạn đang xây dựng một trình tạo báo cáo và việc trình bày trực quan rất quan trọng—đặc biệt khi kết quả cuối cùng là PDF. Tin tốt là gì? Với Aspose.Words for Python bạn không chỉ **how to add shape** mà còn có thể tinh chỉnh mọi thuộc tính của bóng, từ màu sắc đến khoảng cách, và sau đó **save document as pdf** trong một quy trình liền mạch.

Trong hướng dẫn này, chúng tôi sẽ đi qua toàn bộ quy trình từng bước một. Bạn sẽ thấy đoạn mã chính xác có thể sao chép‑dán, hiểu *why* mỗi dòng quan trọng, và nắm bắt một vài mẹo để xử lý các trường hợp đặc biệt (như bóng trong suốt hoặc DPI không chuẩn). Khi kết thúc, bạn sẽ có thể **create rectangle shape**, tùy chỉnh bóng của nó, và xuất ra một PDF sắc nét mà không gặp khó khăn.

## Yêu cầu trước

- Python 3.8+ đã được cài đặt trên máy của bạn.  
- Aspose.Words for Python qua `pip install aspose-words`.  
- Kiến thức cơ bản về Python hướng đối tượng (không cần phức tạp).  

Nếu bạn đã có môi trường ảo được thiết lập, chỉ cần chạy lệnh cài đặt và bạn đã sẵn sàng.

## Bước 1: Khởi tạo Document và Builder

Trước khi bạn có thể **how to add shape**, bạn cần một tài liệu trống để làm việc. Lớp `Document` đại diện cho toàn bộ tệp, và `DocumentBuilder` là cây cọ của bạn.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Why this matters:* `Document` chứa tất cả các phần, trang và tài nguyên. `DocumentBuilder` cung cấp cho bạn một API mượt mà để chèn nội dung chính xác nơi bạn cần—hãy nghĩ nó như một con trỏ trong trình xử lý văn bản.

## Bước 2: Chèn hình chữ nhật

Bây giờ chúng ta thực sự **how to add shape**. Phương thức `insert_shape` cần loại hình và kích thước của nó (đơn vị point). Ở đây chúng ta chọn một hình chữ nhật 200 × 100 pt và tô màu xanh nhạt.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tip:* Nếu bạn cần hình căn chỉnh với văn bản hiện có, hãy sử dụng `builder.move_to` trước khi chèn, hoặc điều chỉnh các thuộc tính `left`/`top` sau khi tạo.

## Bước 3: Bật bóng

Một hình không có bóng sẽ trông phẳng. Để **set shadow distance** và làm cho hiệu ứng hiển thị, lấy định dạng bóng và bật nó.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Why this step:* Định dạng bóng là một đối tượng riêng; việc bật `visible` là việc đầu tiên bạn phải làm, nếu không tất cả các thuộc tính bóng khác sẽ bị bỏ qua.

## Bước 4: Định dạng bóng – Màu, Độ mờ, Khoảng cách, Hướng

Đây là nơi phép thuật diễn ra. Chúng ta sẽ **change shadow color**, điều chỉnh bán kính mờ, đặt khoảng cách bóng so với hình chữ nhật, và xoay nó 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Giải thích mỗi thuộc tính:*

| Thuộc tính | Chức năng | Giá trị thường |
|------------|-----------|----------------|
| `style` | Xác định bóng là *inner* hay *outer*. | `OUTER` (phổ biến nhất) |
| `blur_radius` | Kiểm soát độ mềm; giá trị cao hơn = cạnh mờ hơn. | Thông thường 0–20 px |
| `distance` | Khoảng cách bóng so với hình. | 0–10 pt cho nhẹ nhàng, >10 cho nổi bật |
| `direction` | Góc của nguồn sáng, đo theo chiều kim đồng hồ từ trục x. | 0‑360° |
| `color` | Màu của bóng. | Bất kỳ `aw.Color` nào (ví dụ `gray`, `dark_red`) |

*Edge case:* Nếu bạn đặt `distance` thành `0` bóng sẽ nằm ngay dưới hình, thực tế che đi màu nền của hình. Giữ giá trị lớn hơn `0` để có độ dịch chuyển nhìn thấy.

## Bước 5: Lưu tài liệu dưới dạng PDF

Cuối cùng, chúng ta **save document as pdf**. Aspose.Words tự động raster hoá bóng, vì vậy PDF trông giống hệt như trong Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Why PDF?* PDF giữ nguyên bố cục trên mọi nền tảng, làm cho chúng hoàn hảo cho báo cáo, hoá đơn, hoặc bất kỳ tài liệu in nào.

---

![Tạo hình chữ nhật có bóng](https://example.com/images/rectangle-shadow.png){: .align-center alt="ví dụ tạo hình chữ nhật có bóng"}

*Hình ảnh trên hiển thị kết quả PDF cuối cùng – một hình chữ nhật màu xanh nhạt với bóng ngoài màu xám mềm mại, chính xác như chúng ta đã cấu hình.*

## Câu hỏi thường gặp & Biến thể

### Nếu tôi cần một bóng **transparent**?

Đặt kênh alpha trên màu bóng:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Tôi có thể áp dụng cùng một bóng cho nhiều hình không?

Có. Lấy `ShadowFormat` từ một hình và gán nó cho hình khác:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Làm thế nào để thay đổi bóng cho **different shape type**?

Tất cả các loại hình đều chia sẻ cùng các thuộc tính `ShadowFormat`, vì vậy bạn có thể tái sử dụng cùng một khối cấu hình—chỉ cần thay `ShapeType.RECTANGLE` bằng `ShapeType.OVAL`, `ShapeType.TRIANGLE`, v.v.

### Còn **high‑resolution PDFs** cho in ấn thì sao?

Chỉ định `PdfSaveOptions` với DPI cao hơn:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Tóm tắt

Chúng tôi đã bao phủ mọi thứ bạn cần để **create rectangle shape**, **how to add shape**, tùy chỉnh **shadow colour**, **set shadow distance**, và cuối cùng **save document as pdf**. Đoạn script hoàn chỉnh, có thể chạy được như sau:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Chạy script, mở file `ShadowedShape.pdf` tạo ra, và bạn sẽ thấy một hình chữ nhật sắc nét với bóng xám nhẹ – chính xác như bạn mong đợi từ một báo cáo được định dạng chuyên nghiệp.

## Tiếp theo là gì?

- **Explore other shape types** (`ShapeType.OVAL`, `ShapeType.LINE`) để làm phong phú tài liệu của bạn.  
- **Combine multiple shadows** bằng cách xếp lớp các hình; bạn thậm chí có thể tạo hiệu ứng “glow” bằng cách sử dụng bóng trong với màu sáng.  
- **Automate batch processing**: lặp qua một tập hợp các hàng dữ liệu, tạo một hình cho mỗi hàng, và hợp nhất mọi thứ thành một PDF duy nhất.  
- **Integrate with other Aspose libraries** (ví dụ, Aspose.Slides) nếu bạn cần xuất cùng hình ảnh sang PowerPoint.

Hãy thoải mái thử nghiệm—thay đổi `blur_radius`, chơi với `direction`, hoặc thay `gray` bằng màu đặc trưng của thương hiệu. API đủ linh hoạt để một vài điều chỉnh có thể thay đổi đáng kể ảnh hưởng trực quan.

Có câu hỏi hoặc tình huống khó khăn? Để lại bình luận bên dưới hoặc nhắn tin trên diễn đàn cộng đồng Aspose. Chúc lập trình vui vẻ, và tận hưởng những hình chữ nhật có bóng đẹp mắt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}