---
category: general
date: 2026-06-30
description: Thêm bóng cho hình dạng bằng Aspose.Words cho Python. Tìm hiểu cách đặt
  khoảng cách bóng, tùy chỉnh độ mờ và lưu PDF với bóng cho hình dạng một cách nhanh
  chóng.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: vi
og_description: Thêm bóng cho hình dạng trong tài liệu Word bằng Aspose.Words cho
  Python. Hướng dẫn này cho thấy cách thiết lập khoảng cách bóng, độ mờ và màu sắc,
  sau đó lưu dưới dạng PDF.
og_title: Thêm bóng cho hình dạng trong Python – Hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Thêm bóng cho hình dạng trong Python với Aspose.Words – Hướng dẫn đầy đủ
url: /vi/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Bóng cho Hình dạng trong Python với Aspose.Words – Hướng Dẫn Đầy Đủ

Thêm bóng cho hình dạng trong tài liệu Word bằng Aspose.Words cho Python dễ hơn bạn nghĩ. Nếu bạn từng tự hỏi **cách thiết lập khoảng cách bóng** hoặc **cách thêm bóng cho hình dạng** để có vẻ ngoài hoàn hảo, hướng dẫn này sẽ giúp bạn.

Trong vài phút tới, chúng ta sẽ đi qua mọi thứ bạn cần: từ tạo một tài liệu mới, chèn một hình chữ nhật, điều chỉnh các thuộc tính bóng, cho đến cuối cùng lưu thành PDF để hiển thị hiệu ứng. Khi kết thúc, bạn sẽ có thể áp dụng bóng cho bất kỳ hình dạng nào—hình chữ nhật, hình ellipse, hoặc bản vẽ tùy chỉnh—mà không cần dò tìm trong tài liệu API.

> **Prerequisites** – Bạn nên có Python 3.7+ được cài đặt, giấy phép Aspose.Words for Python (hoặc bản dùng thử miễn phí), và kiến thức cơ bản về lập trình Python. Không cần thư viện bên ngoài nào khác.

---

## Thêm Bóng cho Hình dạng – Tổng Quan Các Bước

Dưới đây là lộ trình nhanh về những gì chúng ta sẽ thực hiện:

1. **Tạo một tài liệu mới** và một `DocumentBuilder` để chỉnh sửa nó.  
2. **Chèn một hình chữ nhật** với kích thước bạn cần.  
3. **Bật và tùy chỉnh bóng** – đây là nơi từ khóa chính tỏa sáng.  
4. **Lưu tài liệu** dưới dạng PDF giữ lại bóng của hình dạng.

Mỗi bước được chia thành một phần riêng, vì vậy bạn có thể sao chép‑dán các đoạn mã trực tiếp vào IDE của mình.

---

## Bước 1: Khởi Tạo Document và Builder

Đầu tiên—không có `Document` thì bạn không có gì để làm việc. `DocumentBuilder` là cây cọ của bạn.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Why this matters*: Đối tượng `Document` đại diện cho toàn bộ tệp, trong khi `DocumentBuilder` đơn giản hoá việc chèn văn bản, bảng và hình dạng. Hãy nghĩ về builder như một con trỏ bạn có thể di chuyển quanh trang.

---

## Bước 2: Chèn Hình Chữ Nhật

Bây giờ chúng ta sẽ thêm một hình chữ nhật—bức tranh nền cho hiệu ứng bóng. Bạn có thể thay `RECTANGLE` bằng `ELLIPSE`, `STAR`, hoặc bất kỳ `ShapeType` nào khác nếu cần hình học khác.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Pro tip*: Các kích thước tính bằng point (1 pt ≈ 1/72 inch). Điều chỉnh chúng cho phù hợp với bố cục; bóng sẽ tự động co giãn.

---

## Cách Thiết Lập Khoảng Cách Bóng

**Khoảng cách** của bóng xác định nó cách hình dạng bao xa. Khoảng cách lớn mô phỏng nguồn sáng ở xa hơn, trong khi giá trị nhỏ tạo cảm giác nâng nhẹ.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Note**: Khoảng cách hoạt động cùng với `angle`. Thay đổi góc sẽ quay bóng quanh hình dạng, trong khi `distance` đẩy nó ra ngoài.

---

## Cách Thêm Bóng cho Hình Dạng – Tùy Chỉnh Độ Mờ, Màu Sắc và Góc

Thêm bóng không chỉ là bật nó lên; bạn thường muốn tinh chỉnh độ mờ, màu sắc và hướng để đạt hiệu ứng thực tế.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Why these settings?*  
- **Blur radius** làm mềm cạnh, ngăn ngừa bóng cứng.  
- **Angle** mô phỏng nguồn sáng; 45° là giá trị mặc định phổ biến và cân bằng.  
- **Color** có thể là bất kỳ đối tượng `Color` nào; thử `Color.gray` để có hiệu ứng nhẹ nhàng hơn.

---

## Bước 4: Lưu Tài Liệu dưới Dạng PDF

Khi hình dạng và bóng đã sẵn sàng, việc lưu lại kết quả trở nên cực kỳ dễ dàng. Aspose.Words tự động xử lý chuyển đổi sang PDF, giữ nguyên độ chính xác hình ảnh.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Expected output*: Mở file `ShadowShape.pdf` đã tạo. Bạn sẽ thấy một trang duy nhất với hình chữ nhật 200 × 100 pt, bóng cách 4 pt với góc 45°, mờ 5 pt. Bóng sẽ xuất hiện như một hào viền xám‑đen nhẹ nhàng bao quanh hình dạng.

---

## Các Câu Hỏi Thường Gặp & Trường Hợp Đặc Biệt

### Nếu tôi cần một hình dạng khác thì sao?

Thay `aw.drawing.ShapeType.RECTANGLE` bằng bất kỳ giá trị enum nào khác, ví dụ `aw.drawing.ShapeType.ELLIPSE`. Các thuộc tính bóng vẫn áp dụng—không cần mã bổ sung.

### Có thể áp dụng bóng cho nhiều hình cùng lúc không?

Có. Lặp qua các hình bạn tạo và cấu hình từng `shadow_format` riêng biệt. Dưới đây là một đoạn mã nhanh:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Làm sao thay đổi độ trong suốt của bóng?

Sử dụng thuộc tính `shadow.transparency` (0 = đông đặc, 1 = hoàn toàn trong suốt):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Ví Dụ Hoàn Chỉnh

Dưới đây là script đầy đủ—sao chép, điều chỉnh thư mục đầu ra, và chạy nó. Không có phần nào bị thiếu.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Chạy script, sau đó mở PDF kết quả. Bạn sẽ thấy hình chữ nhật với bóng sắc nét, lệch vị trí—đúng như **add shadow to shape** hứa hẹn.

---

## Kết Luận

Chúng ta vừa trình diễn cách **add shadow to shape** trong tài liệu Word bằng Aspose.Words for Python, bao gồm các bước quan trọng để **set shadow distance**, tùy chỉnh độ mờ, góc và màu sắc, và cuối cùng xuất PDF giữ lại hiệu ứng. Kỹ thuật này hoạt động với bất kỳ loại hình dạng nào, và bạn có thể mở rộng bằng vòng lặp, điều chỉnh độ trong suốt, hoặc thậm chí bóng gradient.

Sẵn sàng cho thử thách tiếp theo? Hãy thử kết hợp nhiều bóng, xếp lớp các hình, hoặc tạo báo cáo nơi mỗi biểu đồ có bóng riêng. Thử nghiệm sẽ củng cố khái niệm và mở ra những khả năng mới cho tự động hoá tài liệu.

Nếu bạn thấy hướng dẫn này hữu ích, hãy chia sẻ, star repository Aspose.Words, hoặc để lại bình luận với mẹo tùy chỉnh bóng của bạn. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}