---
category: general
date: 2026-09-30
description: Tìm hiểu cách tạo hình chữ nhật, áp dụng bóng đổ cho hình và lưu tài
  liệu Word có hình bằng Aspose.Words cho Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: vi
lastmod: 2026-09-30
og_description: Tạo hình chữ nhật trong tài liệu Word một cách nhanh chóng. Hướng
  dẫn này chỉ cách thêm hình, áp dụng bóng cho hình, thiết lập độ mờ của bóng và lưu
  tài liệu Word có hình.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Tạo hình chữ nhật trong Word bằng Python – hướng dẫn chi tiết từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Cách tạo hình chữ nhật trong tài liệu Word bằng Python
url: /vi/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo hình chữ nhật trong tài liệu Word bằng Python

Nếu bạn cần **tạo hình chữ nhật** trong một tệp Word, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, có thể chạy được. Bạn sẽ thấy cách thêm hình, áp dụng hiệu ứng bóng, điều chỉnh độ mờ, và cuối cùng **lưu Word với hình** để kết quả có thể được mở trong Microsoft Word hoặc bất kỳ trình xem tương thích nào.

Ví dụ sử dụng **Aspose.Words for Python via .NET**, một thư viện cho phép bạn thao tác tài liệu Word mà không cần cài đặt Microsoft Office. Không cần kinh nghiệm trước với API—chỉ cần kiến thức cơ bản về Python.

## Những gì bạn sẽ đạt được

- Chèn một hình chữ nhật vào phần đầu tiên của tài liệu mới.  
- Cấu hình một bóng mềm bằng cách đặt độ mờ, độ dịch và màu sắc.  
- Lưu tài liệu vào đĩa và kiểm tra kết quả hình ảnh.

## Yêu cầu trước

- Python 3.8 hoặc mới hơn.  
- Gói `aspose-words` đã được cài đặt (`pip install aspose-words`).  
- Quyền ghi vào thư mục đầu ra.

## Tạo hình chữ nhật và cấu hình giao diện của nó

Bước đầu tiên là khởi tạo một tài liệu trống và thêm một hình chữ nhật vào đó. Hình sẽ đóng vai trò là nền cho hiệu ứng bóng.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Tại sao điều này quan trọng:**  
Việc tạo hình chữ nhật cung cấp cho bạn một đối tượng cụ thể (`shape`) mà bạn có thể định dạng sau này. Đặt kích thước rõ ràng đảm bảo hình trông giống nhau trên mọi nền tảng.

## Cách thêm hình vào tài liệu Word

Mặc dù đoạn mã trên đã thêm hình chữ nhật, bạn có thể cần thêm các hình khác (ví dụ: vòng tròn, mũi tên) sau này. Mẫu tương tự áp dụng: gọi `append_child` trên phần thân của tài liệu và truyền `ShapeType` mong muốn.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Mẹo:** Sử dụng enumeration `ShapeType` để khám phá tất cả các hình hỗ trợ. Điều này giúp mã của bạn dễ đọc và tránh các số “ma thuật”.

## Áp dụng bóng cho hình và đặt độ mờ của bóng

Bóng tạo độ sâu và thu hút thị giác. Lớp `ShadowEffect` cho phép bạn kiểm soát độ mờ, độ dịch và màu sắc. Dưới đây chúng ta áp dụng một bóng đen mềm cho hình chữ nhật.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Tại sao đặt độ mờ?**  
`blur` quyết định mức độ lan tỏa của bóng. Giá trị thấp (ví dụ: 1.0) tạo cạnh sắc nét, trong khi giá trị cao hơn (ví dụ: 5.0) tạo độ mờ nhẹ, thường thẩm mỹ hơn.

**Trường hợp đặc biệt:** Nếu bạn đặt `blur` bằng 0, bóng sẽ trở thành một hình bóng đặc. Một số trình xem có thể hiển thị nó với các artefact aliasing, vì vậy hãy chọn giá trị lớn hơn 0 để có đầu ra mượt hơn.

## Lưu Word với hình

Lưu tài liệu sẽ hoàn tất mọi thay đổi. Phương thức `save` ghi một tệp `.docx` mà bất kỳ trình xử lý Word hiện đại nào cũng có thể mở.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Khi bạn mở `output.docx`, bạn sẽ thấy một hình chữ nhật được đặt cách góc trên‑trái một inch, với bóng đen mềm dịch sang phải và xuống hai điểm. Độ mờ của bóng làm cho hình trông như được nâng lên khỏi trang.

**Mẹo chuyên nghiệp:** Nếu bạn cần tạo nhiều tài liệu trong một vòng lặp, hãy tái sử dụng cùng một đối tượng `Document` và xóa phần thân của nó giữa các lần lặp để giảm tải bộ nhớ.

## Các biến thể phổ biến và khắc phục sự cố

| Tình huống | Cần thay đổi gì | Lý do |
|-----------|----------------|--------|
| Màu bóng khác | `shadow.color = aw.Color.red` | Sử dụng màu thương hiệu hoặc làm nổi bật các hình quan trọng. |
| Độ dịch bóng lớn hơn | Tăng `shadow.offset_x`/`offset_y` | Nhấn mạnh độ sâu cho các mô hình UI. |
| Không có bóng | Bỏ qua dòng `shape.shadow = shadow` | Hữu ích cho các báo cáo tối giản. |
| Xuất ra PDF thay vì DOCX | `doc.save("output.pdf")` | PDF là lý tưởng cho việc phân phối chỉ đọc. |

Nếu hình không xuất hiện, hãy kiểm tra rằng bạn đang thêm nó vào phần đúng (`get_first_section()`) và tài liệu đã được lưu sau khi chỉnh sửa.

## Ví dụ đầy đủ, có thể chạy

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Chạy script sẽ tạo ra `output.docx` chứa hình chữ nhật với bóng mềm. Mở tệp trong Microsoft Word để xác nhận hiệu ứng hình ảnh khớp với mô tả.

## Kết luận

Bây giờ bạn đã biết cách **tạo hình chữ nhật**, **thêm hình** vào tài liệu Word, **áp dụng bóng cho hình**, **đặt độ mờ bóng**, và cuối cùng **lưu Word với hình** bằng Aspose.Words for Python. Mẫu tương tự có thể mở rộng cho các loại hình khác, màu sắc và hiệu ứng, cho phép bạn kiểm soát hoàn toàn đồ họa tài liệu mà không cần tự động hoá Office.

**Các bước tiếp theo**

- Thử nghiệm `Shape.fill` để thêm nền gradient hoặc hình ảnh.  
- Sử dụng đối tượng `Paragraph` để đặt văn bản bên trong hình chữ nhật.  
- Kết hợp nhiều hình để tạo sơ đồ phức tạp, sau đó xuất ra PDF để phân phối.  

Bạn có thể tự do điều chỉnh mã cho nhu cầu báo cáo hoặc tạo mẫu của mình, và chia sẻ kết quả trong phần bình luận!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo hình chữ nhật, thêm bóng & lưu PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Hướng dẫn bóng cho Shape trong Aspose.Words – Thêm bóng vào Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}