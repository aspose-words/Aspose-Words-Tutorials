---
category: general
date: 2026-05-30
description: Cách chèn hình chữ nhật và thêm bóng trong Word bằng Aspose – hướng dẫn
  Python từng bước để tạo tài liệu Word với hiệu ứng bóng cho hình dạng.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: vi
og_description: Cách chèn hình chữ nhật và thêm bóng trong Word bằng Aspose – học
  cách tạo tài liệu Word với hiệu ứng bóng cho hình dạng bằng Python.
og_title: Cách chèn hình chữ nhật và thêm bóng trong Word bằng Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Cách chèn hình chữ nhật và thêm bóng trong Word bằng Aspose
url: /vi/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn hình chữ nhật và thêm bóng trong Word bằng Aspose

Bạn đã bao giờ tự hỏi **cách chèn hình chữ nhật** vào tệp Word mà không cần mở giao diện người dùng chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển cần tạo báo cáo, hoá đơn hoặc chứng chỉ một cách nhanh chóng, và việc vẽ một hình chữ nhật đơn giản với bóng đẹp mắt có thể làm cho kết quả trông chuyên nghiệp hơn. Trong hướng dẫn này, chúng ta sẽ đi qua các bước chính xác để tạo tài liệu Word, chèn một hình dạng hình chữ nhật, và áp dụng bóng thực tế bằng Aspose.Words cho Python.

Chúng ta sẽ bao phủ mọi thứ từ việc cài đặt gói Aspose đến việc tinh chỉnh khoảng cách, độ mờ và độ trong suốt của bóng. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ quy trình tự động nào. Không có ma thuật, chỉ có mã rõ ràng và một vài mẹo thực tế.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- Python 3.8+ đã được cài đặt (mã hoạt động trên 3.9, 3.10 và các phiên bản mới hơn)
- Giấy phép Aspose.Words for Python hợp lệ hoặc khóa dùng thử miễn phí
- Gói `aspose-words` đã được cài đặt qua `pip install aspose-words`
- Một thư mục có quyền ghi để lưu **create word document aspose** được tạo ra

Đó là tất cả—không cần DLL bổ sung, không cần COM interop, chỉ thuần Python.

## Bước 1: Khởi tạo Document (How to create word document aspose)

Điều đầu tiên: bạn cần một đối tượng `Document` mới. Hãy nghĩ nó như một bảng trắng. Đoạn mã sau tạo tài liệu và một `DocumentBuilder` cho phép chúng ta chèn các hình dạng.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

**Tại sao điều này quan trọng:** `DocumentBuilder` cung cấp cho bạn một API cấp cao để thêm đoạn văn, bảng và—đúng—các hình dạng mà không phải làm việc với cây node cấp thấp. Nếu bạn bỏ qua builder và thao tác trực tiếp trên các node, bạn sẽ có mã dài dòng và khó bảo trì hơn.

## Bước 2: Chèn hình chữ nhật (how to insert rectangle)

Bây giờ chúng ta thực sự **chèn hình chữ nhật**. Aspose.Words xem một hình chữ nhật như một loại hình dạng chung. Bạn chỉ định chiều rộng và chiều cao bằng điểm (1 point ≈ 1/72 inch). Tự do điều chỉnh các số để phù hợp với bố cục của bạn.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần hình chữ nhật được đặt ở vị trí cụ thể trên trang, hãy đặt `shape.left` và `shape.top` sau khi chèn. Điều này cho phép bạn kiểm soát pixel‑perfect.

## Bước 3: Truy cập ShadowFormat của Shape (add shadow to shape)

Phong cách hình dạng nằm trong `ShadowFormat`. Khi lấy nó, chúng ta có quyền truy cập vào mọi thuộc tính xác định giao diện của bóng.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Ở thời điểm này bóng vẫn ẩn—giống như một lớp ẩn chờ lệnh của bạn.

## Bước 4: Cấu hình bóng (how to add shape shadow, apply shadow effect word)

Đây là nơi phép thuật diễn ra. Chúng ta sẽ bật bóng và tinh chỉnh ngoại hình của nó. Các giá trị dưới đây tạo ra một bóng mềm, chéo, phù hợp với hầu hết các tài liệu, nhưng bạn vẫn có thể thử nghiệm.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Mỗi thuộc tính thực hiện gì

| Thuộc tính | Hiệu ứng | Phạm vi điển hình |
|------------|----------|-------------------|
| `visible` | Bật/tắt bóng | `True` / `False` |
| `distance` | Khoảng cách bóng so với hình | 2 – 10 pts |
| `blur` | Độ mềm của các cạnh bóng | 4 – 12 pts |
| `color` | Màu bóng; xám đậm là mặc định an toàn | Bất kỳ `aw.Color` nào |
| `opacity` | Độ trong suốt; 0 = vô hình, 1 = đặc | 0.3 – 0.8 cho vẻ nhẹ nhàng |
| `angle` | Hướng ánh sáng tới | 0 – 360° |

**Tại sao cần điều chỉnh những điều này?** Một bóng được tinh chỉnh tốt có thể làm cho hình chữ nhật phẳng trông như được nâng lên khỏi trang, tạo độ sâu mà không cần hình ảnh. Nếu bạn đặt `opacity` quá cao, bóng sẽ trông gắt; quá thấp thì bóng sẽ biến mất.

## Bước 5: Lưu Document (create word document aspose)

Cuối cùng, ghi tệp ra đĩa. Bạn có thể sử dụng bất kỳ định dạng nào được Aspose.Words hỗ trợ (`.docx`, `.pdf`, `.html`). Trong hướng dẫn này, chúng ta sẽ dùng `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Mở tệp kết quả trong Microsoft Word, và bạn sẽ thấy một hình chữ nhật sắc nét với bóng nhẹ—đúng như bạn mong đợi từ một mẫu thiết kế chuyên nghiệp.

![cách chèn hình chữ nhật có bóng bằng Aspose.Words](/images/rectangle-shadow.png){alt="cách chèn hình chữ nhật có bóng bằng Aspose.Words"}

*Ảnh chụp màn hình (bên trên) hiển thị hình chữ nhật với bóng đã được áp dụng. Lưu ý độ mờ nhẹ và góc 45°, tạo cảm giác tự nhiên.*

## Các biến thể phổ biến và trường hợp đặc biệt

### Thêm nhiều hình

Nếu bạn cần hơn một hình chữ nhật, chỉ cần lặp lại lệnh `insert_shape`. Nhớ di chuyển con trỏ của builder (`builder.move_to(shape)`) hoặc điều chỉnh `shape.left`/`shape.top` để tránh chồng lấn.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Thay đổi loại hình dạng

Mặc dù hướng dẫn này tập trung vào hình chữ nhật, cùng một mẫu code cũng áp dụng cho hình bầu dục, ngôi sao, hoặc các hình dạng tự do tùy chỉnh. Thay `ShapeType.RECTANGLE` bằng `ShapeType.OVAL`, `ShapeType.CLOUD`, v.v., và các cài đặt bóng vẫn giữ nguyên.

### Lưu sang các định dạng khác

Aspose.Words có thể xuất ra PDF, PNG, hoặc thậm chí XPS chỉ với một dòng lệnh:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Việc render bóng được giữ nguyên qua các định dạng, vì vậy PDF của bạn sẽ trông giống như tệp Word.

### Xử lý tài liệu lớn

Khi tạo các báo cáo khổng lồ, hãy cân nhắc gọi `doc.update_page_layout()` sau khi chèn tất cả các hình dạng. Điều này buộc một lượt layout và có thể cải thiện hiệu năng khi bạn chuyển đổi sang PDF sau này.

## Ví dụ hoạt động đầy đủ (Tất cả các bước được kết hợp)

Dưới đây là đoạn script hoàn chỉnh mà bạn có thể sao chép‑dán vào một tệp có tên `rectangle_shadow.py`. Chạy nó bằng `python rectangle_shadow.py` và kiểm tra thư mục `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Chạy script này sẽ tạo ra tài liệu giống hệt như chúng ta đã thảo luận ở trên. Tự do điều chỉnh các số; mã được viết đơn giản để bạn có thể thử nghiệm mà không lo lắng.

## Câu hỏi thường gặp

**Q: Điều này có hoạt động trên Linux không?**


## Bạn nên học gì tiếp theo?

- [Tạo tài liệu Word Java – Thêm hình chữ nhật có hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo tài liệu Word trống với hình chữ nhật có bóng – Hướng dẫn chi tiết](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Hướng dẫn Shadow cho Shape trong Aspose.Words – Thêm bóng cho Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}