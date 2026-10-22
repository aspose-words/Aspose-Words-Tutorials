---
category: general
date: 2026-09-27
description: Tìm hiểu cách đặt bóng cho một hình dạng với Aspose.Words cho Python.
  Hướng dẫn này bao gồm thêm bóng vào hình dạng, áp dụng hiệu ứng bóng và thiết lập
  màu bóng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: vi
lastmod: 2026-09-27
og_description: Cách đặt bóng cho một hình dạng bằng Aspose.Words cho Python. Thực
  hiện theo hướng dẫn từng bước để thêm bóng cho hình dạng, áp dụng hiệu ứng bóng
  và đặt màu bóng.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Cách thiết lập bóng cho hình dạng trong Aspose.Words cho Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Cách thiết lập bóng cho hình dạng trong Aspose.Words cho Python
url: /vi/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách đặt bóng cho một hình dạng trong Aspose.Words cho Python

Nếu bạn cần **cách đặt bóng** cho một đối tượng vẽ, hướng dẫn này sẽ trình bày toàn bộ quy trình. Bạn sẽ thấy cách thêm bóng vào shape, cấu hình độ mờ, độ dịch và màu của bóng, và lưu tài liệu đã cập nhật mà không rời khỏi mã.

Hướng dẫn giả định rằng bạn đã có môi trường Aspose.Words cho Python cơ bản. Khi kết thúc bài viết, bạn sẽ có thể áp dụng hiệu ứng bóng chuyên nghiệp cho bất kỳ shape nào trong tệp DOCX.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Python 3.8+ đã được cài đặt.  
* Aspose.Words cho Python qua .NET (`pip install aspose-words`) đã được cài đặt.  
* Một tài liệu Word (`input.docx`) chứa ít nhất một shape (ví dụ: hình chữ nhật hoặc ảnh).  
  Nếu tài liệu rỗng, mã sẽ tạo một shape mới để minh họa.

Những mục này đảm bảo các bước tiếp theo chạy mà không gặp lỗi import.

## Bước 1: Tải hoặc tạo tài liệu Word

Hoạt động đầu tiên là lấy một đối tượng `Document`. Bạn có thể tải một tệp hiện có hoặc tạo một tệp mới.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Lý do bước này quan trọng*: Đối tượng `Document` là điểm vào cho mọi thao tác xử lý Word. Không có nó, bạn không thể truy cập các shape hoặc áp dụng hiệu ứng hình ảnh.

## Bước 2: Lấy shape mục tiêu

Để thao tác giao diện của một shape, bạn cần một tham chiếu tới node shape. Ví dụ dưới đây lấy shape đầu tiên được tìm thấy trong cấu trúc tài liệu.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Lý do bước này quan trọng*: `add shadow to shape` yêu cầu một đối tượng shape cụ thể. Mã xử lý an toàn trường hợp tài liệu không chứa shape, đảm bảo hướng dẫn hoạt động cho mọi người đọc.

## Bước 3: Cấu hình giao diện bóng

Bây giờ bạn có thể **apply shadow effect** bằng cách điều chỉnh thuộc tính `shadow` của shape. Các thiết lập sau tạo ra một bóng tối nhẹ nhàng.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Lý do mỗi thuộc tính quan trọng*:

| Thuộc tính | Hiệu ứng |
|------------|----------|
| `blur`   | Kiểm soát mức độ mờ của bóng. |
| `offset_x` / `offset_y` | Xác định hướng và khoảng cách dịch so với shape. |
| `color`  | Định nghĩa màu sắc của bóng; bạn có thể dùng bất kỳ `aw.Color` nào. |
| `visible`| Đảm bảo bóng được hiển thị trong tệp đầu ra. |

Bạn có thể thay `aw.Color.black` bằng `aw.Color.from_argb(255, 0, 0, 0)` để sử dụng giá trị RGBA tùy chỉnh, hoặc bất kỳ màu đã định nghĩa sẵn nào khác.

## Bước 4: Lưu tài liệu đã chỉnh sửa

Sau khi cấu hình bóng, lưu các thay đổi vào một tệp mới.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Khi bạn mở `output.docx` trong Microsoft Word, shape đã chọn sẽ hiển thị một bóng đen mềm dịch 2 pt sang phải và 2 pt xuống dưới.

## Ví dụ làm việc đầy đủ

Kết hợp tất cả các bước lại với nhau tạo thành một script tự chứa mà bạn có thể sao chép‑dán vào IDE.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Chạy script sẽ tạo ra `output.docx` trong đó shape đầu tiên có bóng đã được cấu hình.

## Các lỗi thường gặp và cách tránh

| Vấn đề | Lý do | Cách khắc phục |
|--------|-------|----------------|
| `shape` is `None` even after loading a document | Tài liệu không chứa đối tượng vẽ. | Sử dụng khối tạo shape dự phòng được hiển thị trong Bước 2. |
| Shadow does not appear in Word | `shape.shadow.visible` để `False` hoặc tài liệu được lưu ở định dạng cũ (ví dụ: `.doc`). | Đảm bảo `visible = True` và lưu dưới định dạng `.docx`. |
| Color looks different than expected | Chủ đề của tài liệu ghi đè màu được chỉ định rõ. | Đặt `shape.shadow.color` sau khi tắt ghi đè chủ đề, hoặc dùng `aw.Color.from_argb`. |

Xử lý các trường hợp này giúp giải pháp trở nên vững chắc cho mã sản xuất.

## Mở rộng hiệu ứng (bước tiếp theo)

Bây giờ bạn đã biết **cách thêm bóng**, có thể khám phá các cải tiến liên quan:

* **apply shadow effect** với gradient hoặc nhiều bóng bằng cách điều chỉnh các thuộc tính con của `shape.shadow`.  
* Sử dụng **set shadow color** một cách động dựa trên đầu vào của người dùng hoặc màu chủ đề.  
* Kết hợp **add shadow to shape** với các hành động định dạng khác như quay, kiểu đường viền, hoặc hiệu ứng 3‑D.  
* Tự động thêm bóng cho mọi shape trong tài liệu bằng cách lặp qua `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

Các mở rộng này cho phép bạn xây dựng các pipeline tạo tài liệu phức tạp, tạo ra đầu ra tinh tế và nhất quán về mặt hình ảnh.

## Kết luận

Bạn đã có một giải pháp hoàn chỉnh, có thể chạy được cho **cách đặt bóng** trên một shape bằng Aspose.Words cho Python. Hướng dẫn đã bao gồm tải tài liệu, lấy hoặc tạo shape, cấu hình blur, offset và **set shadow color**, và cuối cùng lưu tệp. Áp dụng mẫu này cho bất kỳ shape nào trong dự án tự động hoá của bạn và thử nghiệm các tinh chỉnh hình ảnh bổ sung để đáp ứng yêu cầu thiết kế.

--- 

*Bạn có thể tùy chỉnh mã cho các loại shape, màu sắc hoặc giá trị offset khác. Nếu gặp vấn đề, việc xem lại bảng “Các lỗi thường gặp” là bước đầu tiên hữu ích.*

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thêm bóng vào shape trong C# – Hướng dẫn đầy đủ để áp dụng hiệu ứng bóng](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Thêm bóng vào shape trong Word – Hướng dẫn Aspose.Words đầy đủ](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Tạo shape hình chữ nhật, thêm bóng & lưu PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}