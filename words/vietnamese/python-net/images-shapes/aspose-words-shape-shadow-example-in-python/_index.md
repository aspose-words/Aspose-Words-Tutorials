---
category: general
date: 2026-11-18
description: Ví dụ bóng đổ hình dạng Aspose.Words cho thấy cách thêm bóng đổ vào một
  hình dạng Word bằng Python. Hãy làm theo hướng dẫn từng bước này để chỉnh sửa và
  lưu tài liệu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: vi
lastmod: 2026-11-18
og_description: Ví dụ bóng đổ hình dạng Aspose.Words trình bày cách thêm bóng đổ vào
  một hình dạng Word bằng Python. Tìm hiểu mã đầy đủ, lý do mỗi bước quan trọng và
  cách điều chỉnh nó.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Ví dụ bóng cho hình dạng Aspose.Words – Hướng dẫn Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Ví dụ bóng hình dạng Aspose.Words trong Python
url: /vi/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ví dụ bóng đổ cho shape trong Aspose.Words bằng Python

Ví dụ bóng đổ cho shape trong Aspose.Words minh họa cách thêm hiệu ứng bóng đổ vào một shape trong tài liệu Word bằng Python. Trong hướng dẫn này, bạn sẽ nhận được một script hoàn chỉnh, có thể chạy được, tải tài liệu, cấu hình bóng đổ và lưu kết quả.

Áp dụng bóng đổ cho một shape là cách phổ biến để cải thiện thứ tự trực quan trong báo cáo, brochure hoặc hoá đơn. Đoạn mã dưới đây hoạt động với Aspose.Words for Python via .NET và không yêu cầu thư viện bên thứ ba nào.

## Những gì bạn sẽ học

* Cách tải một tệp `.docx` bằng **Aspose.Words for Python**.  
* Cách xác định shape đầu tiên (bao gồm các shape trong bảng hoặc nhóm).  
* Cách cấu hình độ mờ, độ dịch chuyển ngang và độ dịch chuyển dọc của bóng đổ.  
* Cách lưu tài liệu đã chỉnh sửa trong khi giữ nguyên tất cả nội dung khác.  

**Yêu cầu trước**

* Python 3.8 trở lên.  
* Aspose.Words for Python via .NET đã được cài đặt (`pip install aspose-words`).  
* Một tài liệu Word (`input.docx`) chứa ít nhất một shape (ví dụ: hình ảnh, AutoShape hoặc hộp văn bản).  

Nếu bạn cần cài đặt thư viện, chạy:

```bash
pip install aspose-words
```

## Tổng quan ví dụ bóng đổ cho shape trong Aspose.Words

Script dưới đây là giải pháp đầy đủ. Nó tuân theo bốn bước logic của quy trình **document manipulation Aspose** điển hình: tải, xác định, chỉnh sửa và lưu.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Kết quả mong đợi

Mở `output.docx` trong Microsoft Word. Shape đầu tiên bạn đã thêm bây giờ sẽ hiển thị một bóng đổ mềm, dịch chuyển 2 pt theo chiều ngang và dọc, với bán kính mờ 5 pt. Tất cả nội dung khác vẫn không thay đổi.

## Bước 1: Tải tài liệu Word

Việc tải tài liệu là thao tác đầu tiên trong bất kỳ quy trình **Aspose.Words for Python** nào. Lớp `Document` phân tích tệp và xây dựng mô hình đối tượng trong bộ nhớ. Vì thư viện chạy trên nền tảng .NET, nó có thể xử lý các tệp lớn một cách hiệu quả.

*​Tại sao điều này quan trọng:* Tải tài liệu một lần và giữ tham chiếu (`doc`) tránh việc I/O lặp lại, giúp cải thiện hiệu suất khi bạn cần áp dụng nhiều thay đổi.

## Bước 2: Truy cập shape

Các shape có thể là con trực tiếp của thân tài liệu, hoặc được lồng trong bảng, nhóm hoặc canvas vẽ. Sử dụng `get_child(NodeType.SHAPE, 0, True)` sẽ tìm kiếm đệ quy và trả về shape đầu tiên phù hợp.

*​Tại sao điều này quan trọng:* Cờ `True` đảm bảo bạn không bỏ lỡ các shape ẩn bên trong các node khác. Nếu bỏ qua, chỉ các shape cấp cao nhất sẽ được xét, và nhiều tài liệu thực tế sẽ trả về `None`.

### Thay thế: Tìm shape theo tên

Nếu tài liệu của bạn chứa nhiều shape, bạn có thể muốn xác định một shape cụ thể:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Đoạn mã này minh họa một biến thể **python shape shadow** lọc theo thuộc tính `name` của shape.

## Bước 3: Cấu hình bóng đổ cho shape

Thuộc tính `shadow` của đối tượng `Shape` cho phép bạn kiểm soát chi tiết hiệu ứng hình ảnh. Ba thuộc tính thường được điều chỉnh nhất là:

| Thuộc tính | Phạm vi điển hình | Ảnh hưởng trực quan |
|------------|-------------------|----------------------|
| `blur`   | 0 – 15        | Giá trị cao tạo cạnh mềm hơn. |
| `offset_x` | –10 – 10   | Giá trị dương di chuyển bóng sang phải. |
| `offset_y` | –10 – 10   | Giá trị dương di chuyển bóng xuống dưới. |

Bạn cũng có thể sửa đổi `color`, `transparency`, `visible` và `style`. Ví dụ này đặt mức mờ vừa phải và độ dịch chuyển nhẹ để bóng đổ không quá nổi.

**Mẹo:** Khi một shape đã có bóng đổ, các thuộc tính trên sẽ ghi đè lên cài đặt hiện có. Nếu bạn cần giữ nguyên kiểu gốc, hãy đọc các giá trị hiện tại trước khi thay đổi.

## Bước 4: Lưu tài liệu đã chỉnh sửa

Gọi `doc.save()` sẽ ghi lại mô hình trong bộ nhớ thành tệp `.docx`. Aspose.Words tự động cập nhật tất cả các quan hệ nội bộ, vì vậy tệp đầu ra vẫn hoàn toàn tương thích với Microsoft Word.

*​Tại sao điều này quan trọng:* Lưu chỉ một lần vào cuối quá trình giảm nguy cơ hỏng tệp và cải thiện tốc độ tổng thể, đặc biệt khi xử lý nhiều tài liệu trong một công việc batch.

## Các biến thể phổ biến và trường hợp đặc biệt

### Làm việc với nhiều shape

Nếu bạn cần áp dụng cùng một bóng đổ cho mọi shape, hãy lặp qua bộ sưu tập node:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Áp dụng bóng đổ cho một loại shape cụ thể

Bạn có thể lọc theo `ShapeType` (ví dụ: `aw.ShapeType.IMAGE`). Điều này hữu ích khi bạn chỉ muốn ảnh hưởng đến hình ảnh, không phải AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Xử lý tài liệu không có shape

Script đã đưa ra lỗi `ValueError` rõ ràng nếu không tìm thấy shape. Trong mã sản xuất, bạn có thể ghi log vấn đề và tiếp tục xử lý các tệp khác.

### Lưu ý về tính tương thích

- Mã hoạt động với **Aspose.Words for Python via .NET** phiên bản 23.10 trở lên.  
- Hiệu ứng bóng đổ được hỗ trợ trong Word 2007+ (`.docx`). Các định dạng cũ hơn (`.doc`) sẽ mất hiệu ứng sau khi chuyển đổi.

## Kết luận

Ví dụ **aspose.words shape shadow** này hướng dẫn bạn qua các bước tải tệp Word, xác định shape, cấu hình bóng đổ và lưu kết quả bằng **Aspose.Words for Python**. Bây giờ bạn có một mẫu có thể tái sử dụng cho bất kỳ kịch bản **document manipulation Aspose** nào liên quan đến cải tiến hình ảnh.

Tiếp theo, bạn có thể khám phá:

- Thêm màu gradient hoặc kiểu đường cho shape (`modify shape shadow` và các thuộc tính hình ảnh khác).  
- Kết hợp cấu hình bóng đổ với định dạng văn bản để tạo mẫu hoàn chỉnh.  
- Tự động hoá quy trình cho một loạt tài liệu bằng `os.listdir` và mẫu đã trình bày ở trên.

Bạn có thể tự do thử nghiệm các mức mờ, độ dịch chuyển và màu sắc khác nhau để phù hợp với hướng dẫn thương hiệu của mình. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thêm bóng đổ cho Shape trong Python – Hướng dẫn Aspose.Words đầy đủ](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Cách đặt bóng đổ cho shape trong Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [Cách lưu PNG và thêm bóng đổ cho shape với Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}