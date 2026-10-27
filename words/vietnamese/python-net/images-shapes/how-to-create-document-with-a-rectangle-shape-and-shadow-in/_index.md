---
category: general
date: 2026-10-04
description: Cách tạo tài liệu trong Python và thêm bóng cho hình dạng bằng Aspose.Words.
  Tìm hiểu cách đặt màu bóng, chèn hình chữ nhật và tùy chỉnh bóng ngoài.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: vi
lastmod: 2026-10-04
og_description: Cách tạo tài liệu trong Python và thêm bóng cho hình dạng. Hướng dẫn
  này chỉ cho bạn cách đặt màu bóng, chèn hình chữ nhật và áp dụng bóng ngoài bằng
  Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Cách tạo tài liệu với hình chữ nhật và bóng trong Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Cách tạo tài liệu với hình chữ nhật và bóng trong Python
url: /vi/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu với hình chữ nhật và bóng trong Python

Nếu bạn cần **how to create document** chứa một hình chữ nhật được định dạng, hướng dẫn này cung cấp giải pháp hoàn chỉnh. Bạn sẽ thấy cách **add shadow to shape**, đặt màu cho bóng, và kiểm soát độ dịch chuyển và độ mờ—tất cả bằng Aspose.Words for Python. Khi kết thúc tutorial, bạn có thể tạo một tệp `.docx` trông chuyên nghiệp và sẵn sàng phân phối.

Các bước dưới đây bao gồm mọi thứ từ cài đặt thư viện đến tùy chỉnh giao diện bóng. Không cần tài liệu bên ngoài; mã đã sẵn sàng để sao chép, chạy và điều chỉnh cho dự án của bạn. Bạn cũng sẽ học cách **insert rectangle shape**, chọn một **outer shadow style**, và xử lý các vấn đề thường gặp như bóng không hiển thị hoặc cài đặt wrap không đúng.

## Yêu cầu trước

* Python 3.8 trở lên đã được cài đặt.
* Giấy phép Aspose.Words for Python đang hoạt động (hoặc khóa dùng thử miễn phí).
* Kiến thức cơ bản về lập trình Python.
* Quyền truy cập vào vị trí hệ thống tập tin nơi tài liệu được tạo sẽ được lưu.

Bạn có thể cài đặt SDK bằng pip:

```bash
pip install aspose-words
```

## Bước 1: Nhập thư viện và tạo tài liệu trống mới

Việc tạo một tài liệu mới là hành động đầu tiên trong bất kỳ kịch bản tự động Word nào. Hàm khởi tạo `aw.Document()` cung cấp cho bạn một tệp rỗng mà bạn có thể điền bằng văn bản, hình ảnh hoặc hình dạng.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Đối tượng `DocumentBuilder` đơn giản hoá việc chèn nội dung. Nó theo dõi vị trí con trỏ hiện tại, vì vậy bạn có thể thêm các phần tử một cách tuần tự mà không cần quản lý các phần thủ công.

## Bước 2: Chèn hình chữ nhật với kích thước mong muốn

Hình chữ nhật hoạt động như một container cho các yếu tố hình ảnh. Bạn có thể xác định chiều rộng và chiều cao của nó bằng điểm (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Ở thời điểm này, hình dạng chưa có kiểu dáng trực quan, vì vậy nó xuất hiện như một đường viền đơn giản. Các bước tiếp theo sẽ thêm độ sâu và màu sắc cho nó.

## Bước 3: Đặt hình dạng để chảy inline cùng văn bản xung quanh

Khi một hình dạng là **inline**, nó hoạt động như một ký tự trong đoạn văn. Điều này đảm bảo hình chữ nhật ở vị trí bạn mong muốn trong bố cục tài liệu.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Nếu bạn muốn hình dạng nổi trên văn bản, bạn có thể dùng `WrapType.SQUARE` hoặc `WrapType.TOP_BOTTOM`, nhưng đối với hầu hết các báo cáo, một hình dạng inline giúp bố cục dự đoán được.

## Bước 4: Làm cho bóng hiển thị và chọn màu

Một bóng không hiển thị không mang lại lợi ích trực quan. Cờ `visible` kích hoạt hiệu ứng, và thuộc tính `color` xác định màu sắc của nó. Sử dụng màu đen tạo độ sâu cổ điển, tinh tế.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Bạn có thể thay thế `aw.drawing.Color.black` bằng bất kỳ màu nào khác, chẳng hạn `aw.drawing.Color.gray` hoặc một giá trị RGB tùy chỉnh (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Bước 5: Định nghĩa offset và blur cho bóng để tạo độ sâu

Offset kiểm soát khoảng cách bóng dịch khỏi hình dạng, trong khi bán kính blur làm mềm các cạnh. Giá trị nhỏ tạo bóng sắc nét; giá trị lớn hơn tạo vẻ mềm mại.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Hãy thử nghiệm các số này để phù hợp với hướng dẫn thiết kế của bạn. Đối với bóng đổ mạnh, bạn có thể tăng cả offset và blur.

## Bước 6: Chọn kiểu bóng outer

Aspose.Words cung cấp một số kiểu bóng, như `INNER`, `OUTER`, và `PERSPECTIVE`. Kiểu **outer** đặt bóng bên ngoài viền của hình dạng, lý tưởng cho giao diện sạch sẽ, chuyên nghiệp.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Nếu bạn cần hiệu ứng ấn tượng hơn, thử `ShadowStyle.PERSPECTIVE`—nó thêm độ nghiêng ba chiều.

## Bước 7: Lưu tài liệu với bóng đã tạo

Lưu hoàn thiện tệp và ghi tất cả định dạng lên đĩa. Chọn thư mục bạn có quyền ghi, và đặt tên tệp mô tả.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Chạy script sẽ tạo ra một tệp Word chứa hình chữ nhật với bóng màu hiển thị. Mở tệp trong Microsoft Word hoặc LibreOffice để kiểm tra kết quả.

## Ví dụ đầy đủ có thể chạy

Dưới đây là script hoàn chỉnh bao gồm mọi bước đã thảo luận. Sao chép mã vào tệp có tên `create_shadowed_shape.py` và chạy bằng `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Kết quả mong đợi**

Khi bạn mở `ShapeWithShadow.docx`, bạn sẽ thấy một hình chữ nhật duy nhất ở trung tâm trang. Hình chữ nhật đi kèm với một bóng đen nhẹ, dịch sang phía dưới‑phải, hơi mờ để tạo độ sâu. Bóng tuân theo kiểu outer, vì vậy không giao nhau với nội thất của hình chữ nhật.

## Các câu hỏi thường gặp và trường hợp đặc biệt

### Tại sao bóng đôi khi lại không hiển thị?

Bóng chỉ được vẽ nếu `shadow.visible` được đặt thành `True` **và** `wrap_type` của hình cho phép hiển thị. Hình dạng inline hoạt động ổn định; các hình dạng nổi có thể cần điều chỉnh bố cục thêm.

### Làm sao để thay đổi màu bóng phù hợp với bảng màu thương hiệu?

Thay thế `aw.drawing.Color.black` bằng một giá trị RGB tùy chỉnh:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Nếu tôi muốn hình dạng xuất hiện phía sau văn bản thì sao?

Đặt `wrap_type` thành `WrapType.BEHIND` và điều chỉnh `z_order_position` nếu cần. Lưu ý rằng một số trình xem có thể hiển thị các hình dạng phía sau văn bản khác nhau.

### Tôi có thể áp dụng cùng một cài đặt bóng cho nhiều hình dạng không?

Có. Tạo một hàm trợ giúp để cấu hình bóng và gọi nó cho mỗi hình dạng bạn chèn. Điều này thúc đẩy việc tái sử dụng mã và đảm bảo kiểu dáng nhất quán.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Kết luận

Bây giờ bạn đã biết **how to create document** chứa hình chữ nhật với bóng tùy chỉnh bằng Aspose.Words for Python. Hướng dẫn đã bao gồm chèn hình chữ nhật, đặt hình dạng inline, bật bóng, thiết lập màu, offset, blur và kiểu, và cuối cùng lưu tệp.

Từ đây bạn có thể khám phá các chủ đề liên quan như **add shadow to shape** cho các loại hình dạng khác, **set shadow color** động dựa trên dữ liệu, hoặc **how to add shadow** cho hình ảnh và hộp văn bản. Thử nghiệm các kích thước, màu sắc và kiểu bóng khác nhau để phù hợp với hướng dẫn thương hiệu hoặc hệ thống thiết kế của bạn.

Sẵn sàng tự động hoá nhiều tài liệu Word hơn? Hãy thử thêm bảng, tiêu đề, hoặc nội dung động tiếp theo—mỗi bước dựa trên các nguyên tắc đã trình bày ở đây. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}