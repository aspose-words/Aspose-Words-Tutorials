---
category: general
date: 2026-08-11
description: Thêm bóng cho hình dạng bằng Aspose.Words cho Python. Tìm hiểu cách thêm
  bóng cho hình dạng, áp dụng hiệu ứng làm mờ cho hình dạng và tùy chỉnh độ lệch và
  màu sắc.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: vi
lastmod: 2026-08-11
og_description: Thêm bóng cho hình dạng với Aspose.Words cho Python. Hướng dẫn này
  cho bạn biết cách áp dụng hiệu ứng làm mờ cho hình dạng, thiết lập độ dịch chuyển
  và chọn màu bóng chỉ trong vài dòng mã.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Thêm bóng cho hình dạng trong Python – hướng dẫn Aspose.Words từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Thêm bóng cho hình dạng trong Python – hướng dẫn đầy đủ Aspose.Words
url: /vi/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm bóng cho hình dạng trong Python – hướng dẫn đầy đủ Aspose.Words

Nếu bạn cần **add shadow to shape** trong một tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác với Aspose.Words for Python. Dù bạn đang xây dựng một trình tạo báo cáo hay một dịch vụ mẫu tài liệu, bạn sẽ học cách add shape shadow, apply blur to shape, và tinh chỉnh ngoại hình của bóng chỉ trong vài dòng mã.

Hướng dẫn bao gồm mọi thứ bạn cần: các import cần thiết, cách tìm hình mục tiêu (kể cả các nút lồng nhau), cấu hình các thuộc tính bóng, xử lý các trường hợp biên thường gặp, và lưu tài liệu đã chỉnh sửa. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng để chèn vào bất kỳ dự án Python nào làm việc với tệp .docx.

## Yêu cầu trước

- **Python 3.8+** đã được cài đặt.
- **Aspose.Words for Python via .NET** (cài đặt bằng `pip install aspose-words`).
- Một tài liệu Word (`input.docx`) chứa ít nhất một hình dạng (ví dụ: hình chữ nhật, ảnh, hoặc SmartArt).
- Kiến thức cơ bản về Python và mô hình đối tượng Aspose.Words.

## Bước 1: Nhập Aspose.Words và mở tài liệu

Bước đầu tiên là import gói `aspose.words` (thường được đặt bí danh là `aw`) và tải tài liệu nguồn.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Why this matters*: Mở tài liệu cho phép bạn truy cập vào cây node nơi các shape tồn tại. Lớp `aw.Document` là điểm khởi đầu cho mọi thao tác tiếp theo.

## Bước 2: Tìm shape đầu tiên (kể cả các node lồng nhau)

Shape có thể là con trực tiếp của một `Paragraph` hoặc nằm bên trong các container khác (như bảng). Sử dụng `get_child` với tham số `is_deep` đặt thành `True` sẽ đảm bảo bạn lấy được shape đầu tiên bất kể mức độ lồng nhau.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Why this matters*: Thao tác **add shape shadow** yêu cầu một đối tượng `Shape`. Việc tìm kiếm sâu giúp bạn không bỏ lỡ các shape ẩn trong bảng hoặc các container nhóm.

## Bước 3: Bật bóng và đặt các thuộc tính cơ bản

Aspose.Words biểu diễn bóng bằng một số thuộc tính. Đầu tiên, bật bóng bằng cách đặt `shadow_visible` thành `True`.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

Bây giờ bạn có thể cấu hình bán kính làm mờ, độ dịch chuyển và màu sắc.

## Bước 4: Áp dụng làm mờ cho shape và định nghĩa giá trị offset

Bán kính làm mờ kiểm soát độ mềm của bóng. Giá trị `5.0` tạo ra hiệu ứng mờ đáng chú ý nhưng không quá mạnh. Các offset di chuyển bóng theo chiều ngang và chiều dọc.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Why this matters*: Điều chỉnh `shadow_blur` và các giá trị offset cho phép bạn tạo ra hiệu ứng độ sâu thực tế phù hợp với phong cách hình ảnh của tài liệu.

## Bước 5: Chọn màu bóng (add shape shadow với màu tùy chỉnh)

Bạn có thể sử dụng bất kỳ `aw.Color` nào. Ở đây chúng tôi chọn màu đen, nhưng bạn có thể thay bằng `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)`, v.v.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Why this matters*: Màu sắc quyết định cách bóng tương tác với nội dung xung quanh. Bóng tối hơn sẽ nổi bật trên nền sáng, trong khi các tông màu nhạt hơn hoạt động tốt hơn trên trang tối.

## Bước 6: Lưu tài liệu đã cập nhật

Cuối cùng, ghi các thay đổi trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo một tệp mới.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

Khi bạn mở `output_with_shadow.docx` trong Microsoft Word, shape đầu tiên sẽ hiển thị một bóng đen mềm với độ mờ và offset đã chỉ định.

## Ví dụ đầy đủ, có thể chạy ngay

Kết hợp tất cả lại, đây là một script tự chứa mà bạn có thể chạy ngay lập tức:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Expected output**: Khi mở `output_with_shadow.docx` sẽ thấy shape đầu tiên có một bóng đen nhẹ, được làm mờ, dịch chuyển 2 pt theo chiều ngang và chiều dọc, khớp với các tham số bạn đã truyền.

## Xử lý nhiều shape và các trường hợp đặc biệt

### Thêm bóng cho một shape cụ thể theo tên

Nếu tài liệu của bạn chứa nhiều shape, bạn có thể muốn nhắm mục tiêu một shape bằng thuộc tính `name` của nó:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### Bỏ qua các node không hiển thị

Đôi khi một node shape có thể là placeholder (ví dụ: canvas vẽ không có nội dung hình ảnh). Hãy kiểm tra `shape.is_image` hoặc `shape.is_picture_frame` trước khi áp dụng bóng để tránh lỗi.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### Làm việc với các shape được nhóm

Khi các shape được nhóm, chính nhóm đó cũng là một node `Shape`. Để áp dụng bóng cho mỗi thành viên, lặp qua `shape.get_child_nodes(aw.NodeType.SHAPE, True)`.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

Các biến thể này đảm bảo mã của bạn hoạt động ổn định trên các bố cục tài liệu khác nhau.

## Mẹo chuyên nghiệp để có bóng hoàn hảo

- **Consistency**: Sử dụng cùng một bán kính làm mờ và offset cho tất cả các shape trong báo cáo để duy trì ngôn ngữ hình ảnh nhất quán.
- **Performance**: Áp dụng bóng cho hàng chục hình ảnh độ phân giải cao có thể làm tăng kích thước tệp. Kiểm tra kích thước đầu ra nếu bạn dự định tạo PDF sau này.
- **Color contrast**: Trên nền trang tối, cân nhắc sử dụng bóng sáng hơn (`aw.Color.gray`) để duy trì khả năng nhìn thấy.
- **Preview**: Giao diện “Shadow” của Word phản ánh các thuộc tính Aspose.Words, vì vậy bạn có thể thử nghiệm thủ công, sau đó sao chép các giá trị thu được vào script của mình.

## Kết luận

Bạn đã biết cách **add shadow to shape** trong một tài liệu Word bằng Aspose.Words for Python. Hướng dẫn đã đề cập đến việc tìm shape, bật bóng, **add shape shadow** với blur, offset và màu tùy chỉnh, và lưu kết quả. Với hàm tái sử dụng ở trên, bạn có thể tích hợp hiệu ứng này vào bất kỳ quy trình tạo tài liệu nào.

### Tiếp theo là gì?

- Khám phá **apply blur to shape** cho các hiệu ứng khác như glow hoặc soft edges.
- Kết hợp bóng với **shape borders** hoặc **reflection** để tạo đồ họa phong phú hơn.
- Chuyển đổi tài liệu đã chỉnh sửa sang PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`) để phân phối.

Hãy tự do thử nghiệm các màu sắc, mức độ làm mờ và giá trị offset khác nhau để phù hợp với hướng dẫn thương hiệu của bạn. Chúc bạn lập trình vui!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}