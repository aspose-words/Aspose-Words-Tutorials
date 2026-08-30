---
category: general
date: 2026-07-20
description: Tạo tài liệu Word trống bằng Aspose.Words và thêm bóng cho hình dạng.
  Tìm hiểu cách thay đổi độ mờ và độ trong suốt của bóng chỉ trong vài bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- add shadow effect
- change shadow transparency
- change shadow opacity
language: vi
lastmod: 2026-07-20
og_description: Tạo tài liệu Word trống bằng Aspose.Words và thêm hiệu ứng bóng cho
  một hình dạng. Thay đổi độ mờ và độ trong suốt của bóng với các ví dụ mã rõ ràng.
og_image_alt: Screenshot showing a Word document with a shape that has a semi‑transparent
  shadow
og_title: Tạo tài liệu Word trống và thêm bóng cho hình dạng – Hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  type: TechArticle
- description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  name: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  steps:
  - name: Expected Output
    text: When you open **ShadowedShape.docx**, you should see a rectangle with a
      gray, semi‑transparent shadow that has a gentle blur. The shadow will be offset
      slightly down and to the right, giving the illusion that the shape is lifted
      off the page.
  - name: What if the document already contains multiple shapes?
    text: 'The current script grabs the *first* shape (`index 0`). To target a specific
      shape, change the index or iterate over all shapes:'
  - name: Can I change the shadow color?
    text: 'Absolutely. Shadow color is another property:'
  - name: How do I make the shadow offset differently?
    text: 'Adjust `distance_x` and `distance_y`:'
  - name: Does this work with older Word versions?
    text: Aspose.Words writes the modern OOXML format (`.docx`). Word 2007+ can open
      it without issues. For legacy `.doc` files, call `doc.save("file.doc", aw.SaveFormat.DOC)`—the
      shadow properties will still be preserved.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
- Word Shapes
title: Tạo tài liệu Word trống và thêm bóng cho hình dạng – Hướng dẫn đầy đủ
url: /vi/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-tuto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Tài liệu Word Trống và Thêm Bóng cho Hình – Hướng Dẫn Toàn Diện

Bạn đã bao giờ cần **create blank Word document** và sau đó làm cho một hình nổi bật với bóng nhẹ? Bạn không phải là người duy nhất. Trong nhiều báo cáo, tờ rơi, hoặc bảng điều khiển nội bộ, một chút độ sâu có thể biến một hình chữ nhật phẳng thành một tín hiệu trực quan thu hút mắt.

Trong hướng dẫn này, chúng tôi sẽ chỉ bạn cách tạo một tệp Word mới hoàn toàn bằng Aspose.Words cho Python, lấy ra hình đầu tiên, và sau đó **add shadow to shape** trong khi điều chỉnh độ trong suốt và độ mờ của nó. Khi kết thúc, bạn sẽ có một tài liệu trông chuyên nghiệp—không cần can thiệp thủ công.

> **Bạn sẽ nhận được** – một script hoàn chỉnh, có thể chạy được, giải thích *tại sao* mỗi dòng lại quan trọng, và các mẹo để xử lý tài liệu mà chưa chứa hình.

## Yêu cầu trước

- Python 3.8+ đã được cài đặt (bất kỳ phiên bản mới nào cũng hoạt động)
- Aspose.Words cho Python qua `pip install aspose-words`
- Kiến thức cơ bản về Python và khái niệm “shape” trong Word (nghĩ tới hộp văn bản, hình ảnh, hoặc auto‑shape)

Không cần thư viện nào khác; mã nguồn tự chứa.

## Bước 1: Tạo Tài liệu Word Trống với Aspose.Words

Đầu tiên, chúng ta cần một nền trắng sạch sẽ. Aspose.Words làm việc này trở nên đơn giản—chỉ cần khởi tạo một đối tượng `Document`.

```python
import aspose.words as aw

# Step 1: Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")
```

*Tại sao điều này quan trọng*: Lớp `Document` là điểm khởi đầu cho mọi thao tác. Bắt đầu với một tài liệu mới đảm bảo không có bất ngờ về định dạng ẩn sau này.

## Bước 2: Chèn một Hình mẫu (để chúng ta có gì để thêm bóng)

Nếu bạn chạy script trên một tệp trống, bạn sẽ gặp khó khăn khi cố gắng lấy một hình—vì thực sự không có hình nào. Hãy thêm một hình chữ nhật đơn giản để các bước tiếp theo có mục tiêu.

```python
# Step 2: Add a rectangle shape to the first page
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")
```

> **Mẹo chuyên nghiệp**: Điều chỉnh giá trị width/height (200, 100) để phù hợp với nhu cầu thiết kế của bạn. Các hình lớn hơn hiển thị bóng rõ ràng hơn.

## Bước 3: Lấy Hình Đầu tiên trong Tài liệu

Bây giờ chúng ta đã có một hình, chúng ta có thể an toàn lấy nó ra. Phương thức `get_child` duyệt cây node và trả về node đầu tiên của loại yêu cầu.

```python
# Step 3: Retrieve the first shape (index 0) – true = deep search
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")
```

*Tại sao chúng ta kiểm tra `None`*: Trong các tình huống thực tế, tài liệu có thể được tạo ở nơi khác, và một hình thiếu sẽ gây ra lỗi `AttributeError` khó hiểu. Ném ra một ngoại lệ rõ ràng giúp tiết kiệm thời gian gỡ lỗi.

## Bước 4: Thêm Hiệu Ứng Bóng – Thay Đổi Độ Trong Suốt của Bóng

Bóng không chỉ là một chi tiết hình ảnh; nó còn có thể truyền tải cấp bậc. Hãy làm nó bán trong suốt bằng cách đặt độ trong suốt (opacity) ở mức 75 %.

```python
# Step 4: Set shadow opacity (0.0 = fully transparent, 1.0 = fully opaque)
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")
```

**Hiểu về độ trong suốt**: Giá trị là một số thực từ 0 đến 1. Số thấp hơn làm bóng mờ dần vào nền, số cao hơn làm bóng nổi bật. Đối với hầu hết các tài liệu kiểu UI, khoảng 0.5–0.8 trông tự nhiên.

## Bước 5: Định Nghĩa Độ Mờ của Bóng – Thay Đổi Độ Trong Suốt của Bóng

Bán kính mờ (blur radius) kiểm soát độ mềm của cạnh bóng. Bán kính lớn hơn tạo ra độ mờ nhẹ nhàng hơn, mô phỏng sự khuếch tán ánh sáng tự nhiên.

```python
# Step 5: Define blur radius (in points) for a softer edge
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")
```

*Tại sao độ mờ quan trọng*: Bóng có cạnh cứng có thể trông rẻ tiền, trong khi độ mờ nhẹ nhàng thêm chiều sâu mà không làm lấn át nội dung.

## Bước 6: Lưu Tài liệu và Xác Nhận Kết Quả

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Mở file `.docx` kết quả trong Word để xem hình chữ nhật với bóng mới.

```python
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

### Kết Quả Dự Kiến

Khi bạn mở **ShadowedShape.docx**, bạn sẽ thấy một hình chữ nhật với bóng màu xám, bán trong suốt và có độ mờ nhẹ. Bóng sẽ được dịch nhẹ xuống dưới và sang phải, tạo ảo giác rằng hình đang nổi lên khỏi trang.

## Các Trường Hợp Ngoại Lệ & Câu Hỏi Thường Gặp

### Nếu tài liệu đã chứa nhiều hình thì sao?

Script hiện tại lấy *hình đầu tiên* (`index 0`). Để nhắm mục tiêu một hình cụ thể, thay đổi chỉ mục hoặc lặp qua tất cả các hình:

```python
for i in range(doc.get_child_nodes(aw.NodeType.SHAPE, True).count):
    shp = doc.get_child(aw.NodeType.SHAPE, i, True)
    # Apply shadow settings to each shape
    shp.shadow.opacity = 0.6
    shp.shadow.blur_radius = 5.0
```

### Tôi có thể thay đổi màu bóng không?

Chắc chắn. Màu bóng là một thuộc tính khác:

```python
shape.shadow.color = aw.drawing.Color.black
```

### Làm sao để thay đổi vị trí offset của bóng?

Điều chỉnh `distance_x` và `distance_y`:

```python
shape.shadow.distance_x = 5   # shift right
shape.shadow.distance_y = 5   # shift down
```

### Điều này có hoạt động với các phiên bản Word cũ không?

Aspose.Words ghi định dạng OOXML hiện đại (`.docx`). Word 2007+ có thể mở mà không gặp vấn đề. Đối với các tệp `.doc` cũ, gọi `doc.save("file.doc", aw.SaveFormat.DOC)`—các thuộc tính bóng vẫn sẽ được giữ lại.

## Tổng Kết Toàn Bộ Script

Kết hợp mọi thứ lại, đây là ví dụ đầy đủ, sẵn sàng chạy:

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")

# Insert a rectangle shape (so we have something to shadow)
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")

# Retrieve the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")

# Add shadow effect – change opacity
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")

# Change shadow transparency – define blur radius
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")

# Optional: tweak color and offset
shape.shadow.color = aw.drawing.Color.gray
shape.shadow.distance_x = 4
shape.shadow.distance_y = 4

# Save the document
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

Chạy script này, mở file đã tạo, và bạn sẽ thấy hình được bao phủ bởi một bóng tinh tế—đúng những gì một báo cáo chuyên nghiệp cần.

## Kết Luận

Bây giờ bạn đã biết **how to create blank Word document** với Aspose.Words, chèn một hình, và **add shadow to shape** trong khi thành thạo *change shadow opacity* và *change shadow transparency*. Các bước đơn giản, nhưng kết quả hình ảnh rất đáng giá.

Tiếp theo, bạn có thể khám phá **add shadow effect** cho hình ảnh, thử nghiệm các giá trị `blur_radius` khác nhau, hoặc kết hợp nhiều hình thành một đồ họa tổng hợp. Để tìm hiểu sâu hơn, hãy xem tài liệu của Aspose về [Shape Formatting](https://docs.aspose.com/words/python-net/shape/) và hướng dẫn rộng hơn về [Document Automation](https://docs.aspose.com/words/python-net/).

Bạn đã thử một cách khác? Để lại bình luận bên dưới—chia sẻ các điều chỉnh thực tế sẽ làm cộng đồng mạnh hơn. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ, hoạt động với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Tài liệu Word Trống với Hình Chữ Nhật Có Bóng – Hướng Dẫn Từng Bước](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Hướng Dẫn Bóng Hình Aspose.Words – Thêm Bóng cho Hình Word trong C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Tạo Hình Chữ Nhật trong Word bằng Aspose.Words – Hướng Dẫn Từng Bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}