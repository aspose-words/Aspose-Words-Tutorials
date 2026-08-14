---
category: general
date: 2026-08-14
description: Cách thêm bóng cho hình dạng Word bằng Python – học cách áp dụng hiệu
  ứng bóng, tạo hiệu ứng bóng và lưu tài liệu Word một cách hiệu quả.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow
- apply shadow effect
- create shadow effect
- save word document
- add shadow to shape
language: vi
lastmod: 2026-08-14
og_description: Cách thêm bóng cho hình dạng trong Word bằng Python. Theo dõi hướng
  dẫn đầy đủ này để áp dụng hiệu ứng bóng, tạo hiệu ứng bóng và lưu tài liệu Word
  với giao diện chuyên nghiệp.
og_image_alt: Screenshot illustrating how to add shadow to a Word shape using Python
og_title: Cách thêm bóng cho hình dạng Word bằng Python – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  headline: How to add shadow to a Word shape using Python
  type: TechArticle
- description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  name: How to add shadow to a Word shape using Python
  steps:
  - name: Load the Word document
    text: '```python import aspose.words as aw'
  - name: Retrieve the target shape
    text: '```python # Get the first shape in the document tree. shape = doc.get_child(aw.NodeType.SHAPE,
      0, True) ```'
  - name: Create a shadow object for the shape
    text: '```python # Instantiate a Shadow object and assign it to the shape. shape.shadow
      = aw.Shadow() ```'
  - name: Configure the shadow’s appearance
    text: '```python # Adjust the softness of the shadow edges. shape.shadow.blur
      = 5 # Higher values = softer edges'
  - name: Save the document to apply the changes
    text: '```python # Save the modified document. Overwrite or specify a new file
      name. doc.save("YOUR_DIRECTORY/output.docx") ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
- Document styling
title: Cách thêm bóng cho hình dạng Word bằng Python
url: /vi/python/images-shapes/how-to-add-shadow-to-a-word-shape-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm bóng đổ cho hình dạng Word bằng Python

Nếu bạn cần **cách thêm bóng đổ** cho một hình dạng trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn các bước chính xác. Bạn sẽ học cách áp dụng hiệu ứng bóng đổ, tạo hiệu ứng bóng đổ và lưu tài liệu Word mà không rời khỏi IDE.

Thêm bóng đổ trực quan giúp các sơ đồ, chú thích và biểu tượng nổi bật hơn, cải thiện khả năng đọc cho người dùng cuối. Hướng dẫn này giả định bạn đã có kiến thức cơ bản về Python và đã cài đặt phiên bản mới nhất của thư viện Aspose.Words for Python.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Python 3.8 hoặc mới hơn đã được cài đặt.
* Gói `aspose-words` (`pip install aspose-words`) – thư viện thao tác với các tệp DOCX.
* Một tài liệu Word (`input.docx`) chứa ít nhất một hình dạng (ví dụ: AutoShape hoặc hình ảnh).

Các yêu cầu này đảm bảo mã chạy không thay đổi trên Windows, macOS hoặc Linux.

## Cách thêm bóng đổ cho một hình dạng trong tài liệu Word

Các phần sau chia nhiệm vụ thành các bước rõ ràng, được đánh số. Mỗi bước giải thích **tại sao** thao tác quan trọng, không chỉ **cái gì** cần gõ.

### Bước 1: Tải tài liệu Word

```python
import aspose.words as aw

# Load the existing DOCX file. Replace YOUR_DIRECTORY with the actual path.
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters:* *Tại sao điều này quan trọng:* Việc tải tài liệu tạo ra một biểu diễn trong bộ nhớ mà bạn có thể thao tác. Nếu không có đối tượng này, bạn không thể truy cập các hình dạng hoặc áp dụng kiểu dáng.

### Bước 2: Lấy hình dạng mục tiêu

```python
# Get the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*Why this matters:* *Tại sao điều này quan trọng:* `get_child` duyệt qua cây nút của tài liệu và trả về loại nút được yêu cầu. Tham số thứ ba (`True`) báo cho Aspose.Words tìm kiếm đệ quy, đảm bảo bạn tìm thấy hình dạng ngay cả khi nó nằm trong đoạn văn hoặc bảng.

> **Pro tip:** Nếu tài liệu của bạn chứa nhiều hình dạng, hãy lặp qua bằng `doc.get_child_nodes(aw.NodeType.SHAPE, True)` và chọn hình cần thiết bằng chỉ mục hoặc kiểm tra `shape.title` hoặc `shape.alt_text`.

### Bước 3: Tạo đối tượng bóng cho hình dạng

```python
# Instantiate a Shadow object and assign it to the shape.
shape.shadow = aw.Shadow()
```

*Why this matters:* *Tại sao điều này quan trọng:* Một thể hiện `Shadow` chứa tất cả các tham số hình ảnh (blur, distance, color, v.v.). Gán nó cho hình dạng sẽ khiến Word hiển thị bóng khi tài liệu được mở.

### Bước 4: Cấu hình ngoại hình của bóng

```python
# Adjust the softness of the shadow edges.
shape.shadow.blur = 5          # Higher values = softer edges

# Set how far the shadow is offset from the shape.
shape.shadow.distance = 3     # Measured in points

# Optional: change the shadow color to a light gray.
shape.shadow.color = aw.Color.gray

# Optional: set the shadow's transparency (0 = opaque, 255 = fully transparent).
shape.shadow.transparency = 50
```

*Why this matters:* *Tại sao điều này quan trọng:* `blur` kiểm soát mức độ lan tỏa của bóng, trong khi `distance` xác định độ lệch. Điều chỉnh các giá trị này cho phép bạn đạt được một bóng nhẹ nhàng hoặc một hiệu ứng bóng đổ mạnh mẽ. Thay đổi `color` và `transparency` nữa sẽ tùy chỉnh giao diện, điều này rất quan trọng khi tài liệu tuân theo hướng dẫn phong cách công ty.

### Bước 5: Lưu tài liệu để áp dụng thay đổi

```python
# Save the modified document. Overwrite or specify a new file name.
doc.save("YOUR_DIRECTORY/output.docx")
```

*Why this matters:* *Tại sao điều này quan trọng:* Phương thức `save` ghi các thay đổi trong bộ nhớ trở lại tệp DOCX thực tế. Sau khi lưu, mở `output.docx` trong Microsoft Word sẽ hiển thị hình dạng với bóng đổ đã cấu hình.

## Đoạn mã đầy đủ bạn có thể chạy ngay hôm nay

Dưới đây là chương trình Python hoàn chỉnh, sẵn sàng thực thi. Thay `YOUR_DIRECTORY` bằng thư mục chứa các tệp của bạn.

```python
import aspose.words as aw

# 1️⃣ Load the source document.
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Retrieve the first shape (you can loop for multiple shapes).
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Attach a new Shadow object.
shape.shadow = aw.Shadow()

# 4️⃣ Configure shadow properties.
shape.shadow.blur = 5
shape.shadow.distance = 3
shape.shadow.color = aw.Color.gray
shape.shadow.transparency = 50

# 5️⃣ Save the updated document.
doc.save("YOUR_DIRECTORY/output.docx")
```

### Kết quả mong đợi

Khi bạn mở `output.docx` trong Microsoft Word:

* Hình dạng đầu tiên sẽ hiển thị một bóng đổ màu xám nhẹ, lệch ba điểm.
* Các cạnh của bóng sẽ bị mờ, tạo cảm giác hình dạng được nâng lên nhẹ trong không gian ba chiều.
* Nội dung khác trong tài liệu không thay đổi.

Nếu bạn không thấy bóng đổ, hãy kiểm tra xem hình dạng có phải là hình ảnh với độ trong suốt được đặt ở 100 % không hoặc chế độ xem của tài liệu (Print Layout) có đang hoạt động không.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cách điều chỉnh mã |
|-----------|--------------------|
| **Multiple shapes** | Sử dụng `doc.get_child_nodes(aw.NodeType.SHAPE, True)` và lặp qua bộ sưu tập, áp dụng cùng cấu hình bóng cho mỗi hình dạng. |
| **Only certain shapes need a shadow** | Kiểm tra `shape.name` hoặc `shape.title` trong vòng lặp và chỉ áp dụng bóng khi tên khớp với tiêu chí của bạn. |
| **Different shadow colors** | Đặt `shape.shadow.color = aw.Color(255, 0, 0)` để có bóng màu đỏ, hoặc dùng `aw.Color.from_argb(alpha, r, g, b)` cho độ trong suốt tùy chỉnh. |
| **No existing shape** | Bao lấy hình trong khối `try/except`; nếu `shape` là `None`, tạo một `Shape` mới (ví dụ: hình chữ nhật) và thêm vào tài liệu trước khi áp dụng bóng. |
| **Saving to PDF** | Sau khi thêm bóng, gọi `doc.save("output.pdf")` – bóng sẽ được render đúng trong file PDF xuất ra. |

Các biến thể này đảm bảo hướng dẫn vẫn hữu ích dù bạn đang xử lý một mẫu đơn lẻ hay một loạt tài liệu.

## Cách thêm bóng đổ mà không dùng Aspose.Words (thay thế)

Nếu bạn ưu tiên thư viện `python-docx`, không thể thiết lập bóng trực tiếp vì thư viện không cung cấp các phần tử bóng VML/OOXML bên dưới. Trong trường hợp đó, bạn sẽ cần thao tác XML thủ công:

```python
from docx import Document
from lxml import etree

doc = Document("input.docx")
shape = doc.inline_shapes[0]._inline
# Insert <v:shadow> element here (complex XML manipulation)
```

Vì Aspose.Words cung cấp API `Shadow` cấp cao, **cách thêm bóng đổ** trở nên dễ dàng hơn rất nhiều với thư viện này.

## Các bước tiếp theo

Bây giờ bạn đã biết **cách thêm bóng đổ** cho một hình dạng, bạn có thể:

* **áp dụng hiệu ứng bóng đổ** cho bảng hoặc hộp văn bản bằng cùng lớp `Shadow`.
* **tạo hiệu ứng bóng đổ** với các kết hợp blur và distance khác nhau cho mục đích thương hiệu.
* Khám phá **thêm bóng đổ cho hình dạng** cùng các tùy chọn định dạng khác như độ dày đường, màu nền và xoay.
* Tự động hoá xử lý hàng loạt bằng cách đọc một thư mục chứa các tệp DOCX, áp dụng bóng đổ và lưu mỗi tệp với tên có dấu thời gian.

Những mở rộng này cho phép bạn xây dựng một quy trình định dạng tài liệu đầy đủ, đáp ứng tiêu chuẩn thiết kế của công ty.

*Bạn đã học cách thêm bóng đổ cho một hình dạng Word bằng Python, cách áp dụng hiệu ứng bóng đổ, cách tạo hiệu ứng bóng đổ và cách lưu tài liệu Word với kiểu dáng mới.* Hãy thoải mái thử nghiệm các tham số và chia sẻ kết quả của bạn trong phần bình luận!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh cùng giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Tài liệu Word Java – Thêm Hình chữ nhật với Hiệu ứng Bóng đổ](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hướng dẫn Bóng đổ Hình dạng Aspose.Words – Thêm Bóng đổ cho Hình dạng Word trong C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cách Lưu Markdown từ Word – Hướng dẫn Python đầy đủ](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}