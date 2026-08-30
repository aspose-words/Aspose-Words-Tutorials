---
category: general
date: 2026-06-05
description: Ví dụ Python tạo tài liệu Word cho thấy cách thêm bóng cho một hình dạng,
  áp dụng hiệu ứng bóng trong Word bằng Aspose.Words.
draft: false
keywords:
- create word document python
- how to add shadow
- add shadow to shape
- apply shadow effect word
- insert shape with shadow
language: vi
og_description: Hướng dẫn tạo tài liệu Word bằng Python sẽ chỉ cho bạn cách thêm bóng
  cho một hình dạng và áp dụng hiệu ứng bóng trong Word bằng Aspose.Words.
og_title: Tạo tài liệu Word bằng Python – Thêm bóng cho hình dạng
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Create Word document Python example shows how to add shadow to a shape,
    applying shadow effect in Word with Aspose.Words.
  headline: Create Word Document Python – Add Shadow to Shape Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Use `builder.insert_image(...)` to place an image, then access
      `image_shape.shadow_format` just like we did with the rectangle.
    question: Can I add a shadow to a picture instead of a shape?
  - answer: Yes. Aspose.Words preserves shape effects during conversion, so the PDF
      will retain the shadow.
    question: Does the shadow survive when I convert the document to PDF?
  - answer: Call `builder.insert_shape` for each shape, then configure each shape’s
      `shadow_format` independently. No shared state.
    question: What if I need multiple shapes with different shadows?
  - answer: 'Minimal for typical documents. If you’re generating thousands of shapes,
      consider batch processing or limiting blur radius to keep rendering fast. ##
      Conclusion We’ve just demonstrated how to **create Word document python** code
      that inserts a rectangle and **adds shadow to shape** using Aspose.Word'
    question: Is there a performance impact when adding many shadows?
  type: FAQPage
tags:
- python
- aspose-words
- document automation
title: Tạo tài liệu Word bằng Python – Hướng dẫn thêm bóng cho hình dạng
url: /vi/python/images-shapes/create-word-document-python-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Tài liệu Word bằng Python – Hướng dẫn Thêm Bóng cho Hình dạng

Bạn đã bao giờ tự hỏi làm thế nào để **tạo tài liệu Word bằng Python** mà không chỉ chèn một hình dạng mà còn cho nó một bóng mờ tinh tế? Bạn không phải là người duy nhất. Trong nhiều báo cáo, hoá đơn hoặc tờ rơi marketing, một bóng mờ nhẹ nhàng có thể khiến một hình chữ nhật như đang nổi lên khỏi trang, tạo độ sâu mà không cần đồ họa bổ sung.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được, cho thấy **cách thêm bóng** vào một hình dạng bằng Aspose.Words cho Python. Khi hoàn thành, bạn sẽ có một tệp `.docx` với một hình chữ nhật có bóng mờ 45 độ — hoàn hảo để làm cho tài liệu của bạn trông chuyên nghiệp và bóng bẩy.

## Những gì Hướng dẫn này Bao gồm

Chúng ta sẽ bắt đầu bằng việc thiết lập môi trường, sau đó tạo một tài liệu Word mới, chèn một hình chữ nhật, cấu hình các thuộc tính bóng, và cuối cùng lưu tệp. Trong suốt quá trình, chúng ta sẽ thảo luận vì sao mỗi thiết lập quan trọng, những lỗi thường gặp, và một vài mẹo bổ sung bạn có thể thử. Không cần tham chiếu bên ngoài; mọi thứ bạn cần đều có ở đây.

**Yêu cầu trước**

- Python 3.8+ đã được cài đặt  
- Gói `aspose-words` (`pip install aspose-words`)  
- Kiến thức cơ bản về cú pháp Python (nếu bạn đã viết “Hello, World!” trước đây, bạn đã sẵn sàng)

Sẵn sàng? Hãy bắt đầu.

## Bước 1: Khởi tạo Tài liệu – Các kiến thức Cơ bản **Create Word Document Python**

Điều đầu tiên bạn cần là một đối tượng tài liệu trống và một `DocumentBuilder` cho phép bạn thêm nội dung. Hãy tưởng tượng builder như một cây bút viết vào file Word.

```python
import aspose.words as aw

# Create a new, empty Word document
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add elements
builder = aw.DocumentBuilder(doc)
```

*Lý do quan trọng:* `aw.Document()` là điểm vào cho mọi thao tác Aspose.Words. Nếu không có nó, bạn không thể chèn hình dạng, văn bản hay bất kỳ yếu tố nào khác. Builder giữ một tham chiếu tới tài liệu, vì vậy bạn không cần phải truyền tài liệu qua lại một cách thủ công.

## Bước 2: Chèn Hình chữ nhật – Sử dụng Logic **Insert Shape With Shadow**

Bây giờ chúng ta sẽ đặt một hình chữ nhật trên trang. Kích thước được tính bằng điểm (1 pt ≈ 1/72 inch), vì vậy 150 × 100 pts tạo ra một hộp có tỷ lệ đẹp mắt.

```python
# Insert a rectangle shape of 150x100 points
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
```

*Mẹo chuyên nghiệp:* Nếu bạn cần một hình dạng khác, chỉ cần thay `ShapeType.RECTANGLE` bằng `ShapeType.ELLIPSE`, `ShapeType.CLOUD`, v.v. Mã cấu hình bóng giống nhau sẽ hoạt động cho bất kỳ hình dạng nào bạn chọn.

## Bước 3: Áp dụng Hiệu ứng Bóng – **How To Add Shadow** Một cách Chính xác

Đây là nơi phép thuật xảy ra. Đối tượng `shadow_format` điều khiển khả năng hiển thị, khoảng cách, độ mờ, góc, màu và độ trong suốt. Điều chỉnh mỗi thuộc tính để có được diện mạo mong muốn.

```python
# Grab the shadow formatting object
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set how far the shadow sits from the shape (in points)
shadow.distance = 5.0

# Blur radius controls softness; higher = fuzzier edges
shadow.blur = 3.0

# Angle determines the light source direction (degrees clockwise from the x‑axis)
shadow.angle = 45

# Choose a color – black works for most professional documents
shadow.color = aw.drawing.Color.black

# Transparency is a float from 0 (opaque) to 1 (fully transparent)
shadow.transparency = 0.4   # 40 % transparent gives a subtle effect
```

**Tại sao mỗi thiết lập lại quan trọng**

| Thuộc tính | Sử dụng thường | Ảnh hưởng trực quan |
|------------|----------------|----------------------|
| `visible` | Bật/tắt hiệu ứng | Không có bóng nếu `False` |
| `distance` | Điều chỉnh độ lệch so với hình | Giá trị lớn hơn đẩy bóng xa hơn |
| `blur` | Làm mềm các cạnh | Blur cao hơn = bóng mờ hơn |
| `angle` | Mô phỏng hướng ánh sáng | 0° = bóng sang phải, 90° = phía dưới |
| `color` | Phù hợp với thương hiệu hoặc chủ đề | Bóng trắng hiếm khi hợp lý |
| `transparency` | Điều chỉnh độ mờ | 0.0 = đặc, 0.8 = hầu như không thấy |

*Nhầm lẫn thường gặp:* Quên đặt `shadow.visible = True` sẽ cho ra một hình dạng hoàn hảo nhưng không có bóng — dễ bỏ qua khi bạn đang tập trung vào màu sắc hoặc kích thước.

## Bước 4: Lưu Tài liệu – Bước Cuối **Create Word Document Python**

Sau khi cấu hình hình dạng, chỉ cần ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, `.html`, v.v.). Trong hướng dẫn này, chúng ta sẽ dùng định dạng cổ điển `.docx`.

```python
# Save the document to the desired location
output_path = "shadowed_shape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Khi bạn mở `shadowed_shape.docx` trong Microsoft Word (hoặc bất kỳ trình xem tương thích nào), bạn sẽ thấy một hình chữ nhật với bóng mờ sắc nét, góc 45 độ — chính xác như mã phía trên mô tả.

### Kết quả mong đợi

- Một tệp Word một trang.  
- Một hình chữ nhật được căn giữa vị trí của builder.  
- Bóng đen bán trong suốt, lệch 5 pts, mờ 3 pts, tạo góc 45°.

Nếu bạn không thấy bóng, hãy kiểm tra lại rằng `shadow.visible` được đặt là `True` và bạn đang sử dụng một trình xem hỗ trợ hiệu ứng hình dạng (hầu hết các phiên bản Word hiện đại đều hỗ trợ).

## Bonus: Tinh chỉnh Bóng cho Các Kiểu Dáng Khác nhau

Bạn có thể muốn một vẻ ngoài mềm mại hơn cho báo cáo doanh nghiệp, hoặc một bóng màu đậm cho tờ rơi marketing. Dưới đây là một vài biến thể nhanh:

```python
# Soft gray shadow for subtle emphasis
shadow.color = aw.drawing.Color.gray
shadow.transparency = 0.6
shadow.blur = 5.0
shadow.distance = 3.0

# Red, dramatic shadow for a creative brochure
shadow.color = aw.drawing.Color.red
shadow.transparency = 0.2
shadow.blur = 2.0
shadow.angle = 120
```

Thử nghiệm các giá trị này là cách tốt nhất để hiểu cách **add shadow to shape** hoạt động trong thực tế.

## Xem Trước Hình Ảnh (Bao gồm Alt Text)

![Hình chữ nhật có bóng trong tài liệu Word – ví dụ tạo tài liệu Word bằng Python](/images/shadowed_rectangle.png)

*Alt text:* *Hình chữ nhật có bóng trong tài liệu Word – ví dụ tạo tài liệu Word bằng Python.*

## Câu hỏi Thường gặp

**Hỏi: Tôi có thể thêm bóng cho một hình ảnh thay vì hình dạng không?**  
Đáp: Chắc chắn. Sử dụng `builder.insert_image(...)` để chèn ảnh, sau đó truy cập `image_shape.shadow_format` giống như chúng ta đã làm với hình chữ nhật.

**Hỏi: Bóng có tồn tại khi tôi chuyển đổi tài liệu sang PDF không?**  
Đáp: Có. Aspose.Words giữ nguyên hiệu ứng hình dạng trong quá trình chuyển đổi, vì vậy PDF sẽ vẫn có bóng.

**Hỏi: Nếu tôi cần nhiều hình dạng với các bóng khác nhau thì sao?**  
Đáp: Gọi `builder.insert_shape` cho mỗi hình dạng, sau đó cấu hình `shadow_format` của từng hình độc lập. Không có trạng thái chia sẻ.

**Hỏi: Việc thêm nhiều bóng có ảnh hưởng đến hiệu năng không?**  
Đáp: Tối thiểu đối với các tài liệu thông thường. Nếu bạn tạo hàng ngàn hình dạng, hãy cân nhắc xử lý theo lô hoặc giới hạn bán kính mờ để giữ tốc độ render nhanh.

## Kết luận

Chúng ta vừa trình diễn cách **tạo tài liệu Word bằng Python** để chèn một hình chữ nhật và **thêm bóng cho hình dạng** bằng Aspose.Words. Bằng cách cấu hình `shadow_format`, bạn có thể **áp dụng hiệu ứng bóng cho tài liệu Word** với kiểm soát chi tiết về khoảng cách, độ mờ, góc, màu và độ trong suốt. Mẫu này hoạt động cho bất kỳ hình dạng, ảnh hoặc thậm chí hộp văn bản nào, cung cấp cho bạn một bộ công cụ đa năng để tạo ra các tài liệu chuyên nghiệp.

Tiếp theo bạn sẽ làm gì? Hãy thử kết hợp nhiều hình dạng, xếp lớp văn bản lên trên, hoặc xuất ra PDF để xem bóng vẫn tồn tại sau khi chuyển đổi. Bạn cũng có thể khám phá các hiệu ứng hình ảnh khác như glow hoặc reflection — chỉ cần thay `shadow_format` bằng `glow_format` hoặc `reflection_format`.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn có chiều sâu thêm!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh cùng giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}