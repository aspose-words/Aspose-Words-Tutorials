---
category: general
date: 2026-08-07
description: Vẽ hình chữ nhật trong PDF bằng Aspose.Words cho Python và tìm hiểu cách
  thêm bóng cho hình dạng, cấu hình bóng của hình dạng, và lưu tài liệu dưới dạng
  PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: vi
lastmod: 2026-08-07
og_description: Vẽ hình chữ nhật trong PDF bằng Aspose.Words cho Python. Hướng dẫn
  này chỉ cách thêm bóng cho hình dạng, cấu hình bóng của hình dạng và lưu tài liệu
  dưới dạng PDF để tạo tài liệu chuyên nghiệp.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Vẽ hình chữ nhật trong PDF bằng Aspose.Words cho Python – hướng dẫn
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Vẽ hình chữ nhật trong PDF bằng Aspose.Words cho Python
url: /vi/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vẽ hình chữ nhật trong PDF bằng Aspose.Words cho Python

Nếu bạn cần **vẽ hình chữ nhật trong PDF** khi làm việc với Python, hướng dẫn này cung cấp cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ thấy cách **thêm bóng cho hình dạng**, cấu hình bóng đó, và cuối cùng **lưu tài liệu dưới dạng PDF** để phân phối hoặc lưu trữ.

Tạo một hình chữ nhật có bóng là yêu cầu phổ biến cho báo cáo, hoá đơn, hoặc chú thích trực quan. Khi kết thúc tutorial này, bạn sẽ có một script duy nhất tạo ra một PDF chứa hình chữ nhật với bóng thực tế, và bạn sẽ hiểu cách điều chỉnh kích thước, màu sắc, và độ dịch chuyển để phù hợp với bất kỳ thiết kế nào.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Python 3.8+ đã được cài đặt.
* Gói Aspose.Words for Python via .NET (`aspose-words`) – cài đặt bằng:

```bash
pip install aspose-words
```

* Quyền ghi vào thư mục mà bạn dự định lưu PDF.

Không cần thư viện bổ sung nào; Aspose.Words tự xử lý việc tạo hình dạng, cấu hình bóng, và xuất PDF nội bộ.

## Bước 1: Tạo một tài liệu trống mới (vẽ hình chữ nhật trong PDF – khởi tạo)

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp PDF và cung cấp một container cho các section, paragraph, và shape.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Tại sao lại quan trọng:** Aspose.Words xem việc tạo PDF như một quá trình chuyển đổi từ mô hình tài liệu Word, vì vậy chúng ta bắt đầu với một `Document` dù kết quả cuối cùng là PDF.

## Bước 2: Chèn một shape hình chữ nhật vào phần thân tài liệu

Hình chữ nhật là một `ShapeType` cụ thể. Chúng ta thêm nó vào phần thân của section đầu tiên, việc này sẽ tự động tạo một trang mới khi lưu dưới dạng PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Giải thích:** Các thuộc tính `width` và `height` điều khiển kích thước hiển thị của shape trong PDF. Thêm văn bản giúp hình chữ nhật dễ kiểm tra hơn trong quá trình thử nghiệm.

## Bước 3: Thêm bóng cho shape – bật và tùy chỉnh

Bây giờ chúng ta bật hiệu ứng bóng và tinh chỉnh ngoại hình của nó. Đây là nơi từ khóa **add shadow to shape** phát huy tác dụng.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Tại sao cần cấu hình bóng cho shape?** Điều chỉnh `blur`, `distance`, và `angle` cho phép bạn mô phỏng ánh sáng thực tế, cải thiện khả năng đọc và thứ tự trực quan trong các PDF được tạo.

## Bước 4: Lưu tài liệu dưới dạng PDF – kết quả cuối cùng

Với hình chữ nhật và bóng đã được định nghĩa, bước cuối cùng là xuất tài liệu Word ra PDF. Điều này đáp ứng yêu cầu **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Khi bạn mở `shadow_rectangle.pdf`, sẽ thấy một trang duy nhất chứa một hình chữ nhật viền xám có tiêu đề “Shadow demo” với bóng chéo sắc nét.

### Kết quả mong đợi

* Một tệp PDF có tên `shadow_rectangle.pdf`.
* Một trang với hình chữ nhật kích thước 200 pt × 100 pt.
* Bóng hiển thị dịch chuyển 5 pt ở góc 45°, mờ đi 8 pt.

## Bước 5: Khám phá các biến thể và trường hợp đặc biệt (tùy chọn)

Dưới đây là các điều chỉnh thường gặp mà bạn có thể cần trong các dự án thực tế:

| Variation | Code snippet | When to use |
|-----------|--------------|-------------|
| **Kiểu shape khác** (ví dụ: ellipse) | `aw.drawing.ShapeType.OVAL` thay vì `RECTANGLE` | Đối với đồ họa tròn hoặc huy hiệu |
| **Màu bóng tùy chỉnh** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Khi cần bóng màu xám hoặc màu thương hiệu |
| **Nhiều shape** | Lặp lại khối tạo shape và điều chỉnh các thuộc tính `left`/`top` | Để xây dựng sơ đồ phức tạp |
| **Không có văn bản trong shape** | Bỏ qua `rectangle.text = "..."` | Khi shape chỉ dùng để trang trí |
| **Đầu ra DPI cao** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` với `PdfSaveOptions` được thiết lập cho chất lượng hình ảnh | Đối với PDF chuẩn in |

**Mẹo chuyên nghiệp:** Luôn đặt `shadow.visible = True` trước khi điều chỉnh các thuộc tính khác; nếu không các thay đổi sẽ bị bỏ qua một cách im lặng.

## Script đầy đủ – sao chép, dán và chạy

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Chạy script từ terminal hoặc IDE của bạn. Thay `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế, chẳng hạn `"/tmp"` hoặc `"C:\\Users\\Me\\Documents"`.

## Kết luận

Bây giờ bạn đã biết cách **vẽ hình chữ nhật trong PDF** bằng Aspose.Words cho Python, **thêm bóng cho shape**, **cấu hình bóng cho shape**, và **lưu tài liệu dưới dạng PDF**. Ví dụ hoàn chỉnh minh họa mọi bước từ tạo tài liệu đến xuất cuối cùng, và các biến thể tùy chọn cho thấy cách điều chỉnh code cho các kịch bản phức tạp hơn.

Tiếp theo, bạn có thể khám phá:

* Thêm các kiểu shape khác (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Áp dụng gradient fill hoặc border để tăng tính thẩm mỹ.
* Sử dụng `PdfSaveOptions` để nhúng phông chữ hoặc kiểm soát nén hình ảnh.

Hãy thoải mái thử nghiệm các tham số để phù hợp với thương hiệu hoặc hướng dẫn thiết kế của bạn. Chúc bạn scripting PDF vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã nguồn hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}