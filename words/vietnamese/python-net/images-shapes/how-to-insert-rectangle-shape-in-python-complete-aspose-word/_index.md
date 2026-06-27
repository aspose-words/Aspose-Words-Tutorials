---
category: general
date: 2026-06-27
description: Tìm hiểu cách chèn hình chữ nhật trong Python bằng Aspose.Words, thay
  đổi màu bóng, thêm bóng ngoài và áp dụng hiệu ứng bóng cho hình—tất cả trong một
  hướng dẫn.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: vi
og_description: Nắm vững cách chèn hình chữ nhật trong Python, thay đổi màu bóng,
  thêm bóng ngoài và áp dụng hiệu ứng bóng cho hình dạng bằng Aspose.Words.
og_title: Cách chèn hình chữ nhật trong Python – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Cách chèn hình chữ nhật trong Python – Hướng dẫn đầy đủ Aspose.Words
url: /vi/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn rectangle shape trong Python – Hướng dẫn đầy đủ Aspose.Words

Bạn đã bao giờ tự hỏi **cách chèn rectangle shape** vào tài liệu Word bằng Python chưa? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi tự động hoá báo cáo hoặc tạo mẫu. Tin tốt là Aspose.Words làm cho việc này trở nên đơn giản, và trong hướng dẫn này chúng ta sẽ đi qua toàn bộ quy trình, từ việc vẽ hình chữ nhật đến việc thêm bóng ngoài mượt mà.

Chúng tôi cũng sẽ đề cập đến **cách thay đổi màu bóng**, **cách thêm outer shadow**, và bước cuối cùng **apply shadow effect to shape**. Khi kết thúc, bạn sẽ có một hình chữ nhật đã được định dạng hoàn chỉnh mà bạn có thể chèn vào bất kỳ tệp .docx nào một cách lập trình.

## Prerequisites

- Python 3.8+ đã được cài đặt trên máy của bạn  
- Aspose.Words for Python qua `pip install aspose-words`  
- Kiến thức cơ bản về lập trình Python (không cần hiểu sâu về Word‑API)  

Nếu bạn đã có những thứ này, tuyệt vời—hãy bắt đầu. Nếu chưa, hãy cài thư viện trước; phần còn lại của hướng dẫn giả định việc import hoạt động trơn tru.

## How to Insert Rectangle Shape with Aspose.Words for Python

Bước đầu tiên chính xác như từ khóa chính: **cách chèn rectangle shape**. Chúng ta sẽ tạo một tài liệu mới, khởi tạo một `DocumentBuilder`, và thả một hình chữ nhật lên trang.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Tại sao điều này quan trọng:** Lệnh `insert_shape` là cốt lõi của *cách chèn rectangle shape*. Nó trả về một đối tượng `Shape` mà bạn có thể thao tác sau này—kích thước, vị trí, màu nền, viền, tùy ý. Lưu ý chúng ta cũng đặt `fill_color`; nếu không, bóng có thể hòa vào trang trắng, khiến nó khó nhìn thấy.

### Pro tip
Nếu bạn cần hình chữ nhật ở vị trí cụ thể, hãy dùng `builder.move_to` trước khi chèn, hoặc điều chỉnh `rectangle.left` và `rectangle.top` sau khi tạo.

## Changing the Shadow Color of a Shape

Bây giờ hình chữ nhật đã có trong tài liệu, hãy trả lời **cách thay đổi màu bóng**. Aspose.Words cung cấp một đối tượng `ShadowEffect` cho phép bạn đặt thuộc tính `color` thành bất kỳ giá trị RGB nào.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Tại sao bạn muốn làm điều này:** Bóng đen đậm có thể quá gắt, đặc biệt trên các tài liệu màu sáng. Điều chỉnh màu giúp bạn phù hợp với thương hiệu công ty hoặc chỉ đơn giản là tạo ra hiệu ứng nhẹ nhàng hơn.

### Edge case
Nếu bạn quên đặt `shadow.opacity`, giá trị mặc định là hoàn toàn không trong suốt, khiến bóng trông như một hình dạng rắn. Luôn kết hợp việc thay đổi màu với mức độ trong suốt phù hợp.

## Adding an Outer Shadow Effect

Câu hỏi tiếp theo mà nhiều người đặt là **cách thêm outer shadow**. Cờ `ShadowStyle.OUTER` báo cho Aspose.Words vẽ bóng bên ngoài đường viền của hình thay vì bên trong.

Đoạn mã ở trên đã sử dụng `ShadowStyle.OUTER`, nhưng hãy tách riêng cài đặt này để rõ ràng hơn:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Nếu bạn chuyển sang `ShadowStyle.INNER`, bóng sẽ xuất hiện *bên trong* hình chữ nhật, hữu ích cho các hiệu ứng emboss. Đối với hầu hết các kịch bản thiết kế tài liệu, kiểu outer mang lại vẻ bóng rơi tự nhiên.

## Applying the Shadow Effect to Your Shape

Chúng ta đã **apply shadow effect to shape** bằng cách gán `rectangle.shadow = shadow`. Hãy gói tất cả lại và lưu tài liệu, xác nhận rằng hiệu ứng vẫn tồn tại.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Khi bạn mở `RectangleWithShadow.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xanh nhạt với bóng ngoài màu xám nhẹ được chiếu ở góc 45°. Bóng sẽ hơi mờ và lệch, chính xác như chúng ta đã cấu hình.

### Common pitfalls
- **Missing directory:** `doc.save` sẽ gây lỗi nếu thư mục không tồn tại. Hãy tạo thư mục trước hoặc dùng `os.makedirs`.
- **Version mismatch:** API bóng yêu cầu Aspose.Words 22.9+; các phiên bản cũ hơn sẽ bỏ qua cài đặt bóng mà không báo lỗi.

## Full Working Example

Dưới đây là đoạn script hoàn chỉnh, sẵn sàng chạy, kết hợp tất cả các bước. Sao chép‑dán vào một tệp có tên `rectangle_shadow.py` và thực thi bằng `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Kết quả mong đợi:** Một tài liệu Word (`RectangleWithShadow.docx`) chứa một hình chữ nhật duy nhất với bóng ngoài màu xám. Mở nó trong Word để xác nhận hiệu ứng hình ảnh.

## Frequently Asked Questions

| Question | Answer |
|----------|--------|
| *Can I use a different shape type?* | Chắc chắn—thay `ShapeType.RECTANGLE` bằng `ShapeType.OVAL`, `ShapeType.TRIANGLE`, v.v., và logic bóng vẫn áp dụng. |
| *What if I need a thicker border?* | Đặt `rectangle.line_width = 2.0` (points) trước khi áp dụng bóng. |
| *Is it possible to animate the shadow?* | Không trực tiếp với Aspose.Words; bạn cần xuất ra HTML/CSS để thực hiện animation. |
| *Does this work on macOS?* | Có—Aspose.Words không phụ thuộc vào nền tảng miễn là Python chạy được. |

## Conclusion

Chúng ta đã đi qua **cách chèn rectangle shape**, trình bày **cách thay đổi màu bóng**, giải thích **cách thêm outer shadow**, và cuối cùng cho bạn thấy **apply shadow effect to shape** bằng Aspose.Words cho Python. Đoạn script đầy đủ đã sẵn sàng để tích hợp vào bất kỳ pipeline tự động nào, mang lại một hình chữ nhật chuyên nghiệp với bóng tinh tế trong vài giây.

Sẵn sàng cho bước tiếp theo? Hãy thử thay đổi màu nền, thử các góc `direction` khác nhau, hoặc thêm nhiều hình vào cùng một trang. Bạn cũng có thể khám phá API định dạng văn bản phong phú của Aspose.Words để kết hợp bóng với văn bản được định dạng—hoàn hảo cho các báo cáo bắt mắt.

Nếu bạn thấy hướng dẫn này hữu ích, hãy nhấn thích, chia sẻ với đồng nghiệp, hoặc để lại bình luận với các biến thể của bạn. Chúc lập trình vui vẻ!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## What Should You Learn Next?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}