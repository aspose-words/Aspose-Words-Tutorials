---
category: general
date: 2026-06-24
description: Tạo hình chữ nhật trong Python với Aspose.Words, học cách thêm bóng cho
  hình, đặt góc bóng và lưu tài liệu dưới dạng PDF trong vài phút.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: vi
og_description: Tạo hình chữ nhật trong Python, thêm bóng cho hình, đặt góc bóng và
  lưu tài liệu dưới dạng PDF bằng Aspose.Words. Thực hiện theo hướng dẫn từng bước
  này.
og_title: Tạo Hình Chữ Nhật trong Python – Hướng Dẫn Đầy Đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Tạo hình chữ nhật trong Python – Hướng dẫn đầy đủ Aspose.Words
url: /vi/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Hình Chữ Nhật trong Python – Hướng Dẫn Toàn Diện Aspose.Words

Bạn đã bao giờ tự hỏi làm thế nào để **create rectangle shape** trong một tài liệu Word bằng Python chưa? Có thể bạn cần một hộp chú thích đậm, một chỉ dẫn trực quan cho sơ đồ, hoặc chỉ một hình chữ nhật đẹp mắt cho báo cáo. Dù sao, bạn đã đến đúng nơi. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quá trình — từ chèn hình chữ nhật, thêm bóng nhẹ, điều chỉnh góc bóng, và cuối cùng **save document as PDF** để bạn có thể chia sẻ với bất kỳ ai.

Chúng tôi sẽ sử dụng **Aspose.Words for Python via .NET**, một thư viện mạnh mẽ cho phép bạn thao tác các tệp Word mà không cần mở Word. Khi kết thúc hướng dẫn này, bạn sẽ có thể trả lời câu hỏi *“how to add shape shadow”* một cách tự tin, và sẽ có một script sẵn sàng chạy mà bạn có thể đưa vào bất kỳ dự án nào.

---

## Những Gì Bạn Cần

- **Python 3.8+** đã được cài đặt trên máy của bạn.  
- **Aspose.Words for Python via .NET** (`aspose-words` package). Cài đặt bằng:

  ```bash
  pip install aspose-words
  ```

- Một thư mục có quyền ghi nơi PDF được tạo sẽ được lưu.  
- (Tùy chọn) Một IDE hoặc trình soạn thảo văn bản — VS Code hoạt động tốt.

Đó là tất cả. Không cần DLL bổ sung, không cần cài đặt Office, chỉ một gói pip duy nhất.

---

## Bước 1: Thiết Lập Document và Builder

Điều đầu tiên bạn cần làm là tạo các đối tượng thân thiện với **create rectangle shape**: một `Document` và một `DocumentBuilder`. Hãy nghĩ về builder như cây bút của bạn; nó vẽ mọi thứ cho bạn.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Tại sao điều này quan trọng:** Đối tượng `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp các phương thức như `insert_shape` giúp việc vẽ hình trở nên dễ dàng.

---

## Bước 2: Chèn Hình Chữ Nhật

Bây giờ chúng ta đã có builder, cuối cùng chúng ta có thể **create rectangle shape**. Phương thức `insert_shape` cần ba đối số: loại hình, chiều rộng và chiều cao. Chúng ta sẽ sử dụng chiều rộng 200 pt và chiều cao 100 pt để có tỉ lệ đẹp.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Tại thời điểm này, bạn đã thành công **create rectangle shape** trong tài liệu của mình. Nếu bạn mở DOCX đã tạo (chúng ta sẽ làm điều đó sau), bạn sẽ thấy một hình chữ nhật đơn giản nằm ở vị trí con trỏ.

---

## Bước 3: Truy Cập Đối Tượng Shadow Formatting

Để **add shadow to shape**, trước tiên chúng ta cần lấy định dạng bóng của hình. Mỗi hình trong Aspose.Words đều có thuộc tính `shadow_format` cho phép truy cập tất cả các cài đặt liên quan đến bóng.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Có tham chiếu `shadow` cho phép chúng ta bật/tắt hiển thị, độ mờ, khoảng cách, góc, màu và độ trong suốt — tất cả chỉ trong vài dòng code.

---

## Bước 4: Bật Bóng và Cấu Hình Ngoại Hình

Đây là nơi phép thuật diễn ra. Chúng ta sẽ **add shadow to shape**, làm nó hơi mờ, dịch chuyển một chút, đặt hướng (phần **set shadow angle**), và cho nó màu đen bán trong suốt.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần hiệu ứng mạnh hơn, tăng `blur_radius` hoặc giảm `transparency`. Ngược lại, một bóng sắc nét, hoàn toàn không trong suốt có thể đạt được bằng `blur_radius = 0` và `transparency = 0`.

---

## Bước 5: Lưu Document dưới dạng PDF

Chúng ta đã **create rectangle shape**, đã **add shadow to shape**, và bây giờ chúng ta sẽ **save document as PDF** để kết quả hiển thị giống hệt trên mọi thiết bị. Aspose.Words làm cho việc này chỉ cần một dòng lệnh.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Chạy script sẽ tạo ra `shadowed_rectangle.pdf` trong thư mục `output`. Mở nó bằng bất kỳ trình xem PDF nào và bạn sẽ thấy một hình chữ nhật sạch sẽ với bóng mềm, góc 45 độ — chính xác như chúng ta đã cấu hình.

---

## Ví Dụ Hoàn Chỉnh Hoạt Động

Dưới đây là script hoàn chỉnh, sẵn sàng chạy, kết hợp tất cả các bước ở trên. Sao chép‑dán nó vào một tệp có tên `create_rectangle_with_shadow.py` và thực thi `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Kết quả mong đợi:** Một tệp PDF hiển thị một hình chữ nhật duy nhất với bóng nhẹ, chéo. Không có trang thừa, không có hiện tượng ẩn — chỉ hình chúng ta đã tạo.

---

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

### Nếu tôi cần một hình khác thì sao?

Aspose.Words hỗ trợ nhiều giá trị `ShapeType` (ellipse, star, callout, v.v.). Chỉ cần thay thế `aw.drawing.ShapeType.RECTANGLE` bằng enum mong muốn, chẳng hạn `aw.drawing.ShapeType.ELLIPSE`.

### Tôi có thể thêm nhiều bóng không?

API chỉ cho phép một `ShadowFormat` cho mỗi hình, nhưng bạn có thể mô phỏng nhiều bóng bằng cách sao chép hình, dịch chuyển mỗi bản sao và điều chỉnh độ trong suốt.

### Làm sao để thay đổi màu bóng phù hợp với thương hiệu của tôi?

Chỉ cần đặt `shadow.color` thành bất kỳ `aw.drawing.Color` nào. Đối với màu xanh thương hiệu, sử dụng `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Còn việc lưu dưới dạng DOCX thay vì PDF thì sao?

Thay thế `document.save(pdf_path)` bằng `document.save("output/shadowed_rectangle.docx")`. Việc render bóng được giữ nguyên trong cả hai định dạng.

### Bóng có hoạt động trên các trình xem PDF cũ không?

Aspose.Words render bóng dưới dạng hiệu ứng vector, được hỗ trợ rộng rãi. Tuy nhiên, một số trình xem rất cũ có thể làm phẳng hiệu ứng; việc kiểm tra trên thiết bị của đối tượng mục tiêu luôn là thói quen tốt.

---

## Mẹo Để Tinh Chỉnh PDF Của Bạn

- **Thêm viền:** `rectangle.line_format.width = 1.5` và đặt màu cho đường viền sắc nét.  
- **Căn giữa hình chữ nhật:** Sử dụng `builder.move_to_document_start()` trước khi chèn, sau đó `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Kết hợp với văn bản:** Chèn một `TextFragment` sau hình chữ nhật để đặt nhãn, ví dụ, `"Important Section"`.

Những điều chỉnh nhỏ này có thể biến một hình chữ nhật đơn giản thành một hộp chú thích được tinh chỉnh, trông chuyên nghiệp trong báo cáo, đề xuất hoặc sách điện tử.

---

## Kết Luận

Bây giờ bạn đã có một công thức toàn diện, từ đầu đến cuối để **create rectangle shape** trong Python, **add shadow to shape**, **set shadow angle**, và **save document as PDF** bằng Aspose.Words. Các bước đơn giản, code hoàn toàn tự chứa, và bạn đã thấy tại sao mỗi dòng lệnh quan trọng — từ khởi tạo document đến tinh chỉnh PDF cuối cùng.

Tiếp theo, bạn có thể khám phá **how to add shape shadow** cho các bản vẽ phức tạp hơn, thử nghiệm với gradient fill, hoặc tạo bảng bên trong các hình. Thư viện cũng hỗ trợ liên kết các hình với bookmark, rất hữu ích cho PDF tương tác.

Bạn có cách nào khác mà bạn đã thử? Hãy chia sẻ trong phần bình luận, hoặc đặt câu hỏi còn lại. Chúc lập trình vui vẻ, và tận hưởng việc thêm chiều sâu cho tài liệu của bạn! 

![Hình chữ nhật có bóng – ví dụ về create rectangle shape trong Python](/images/rectangle-shadow.png)


## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ code hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Tài Liệu Word Java – Thêm Hình Chữ Nhật với Hiệu Ứng Bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hướng Dẫn Shape Shadow của Aspose.Words – Thêm Bóng cho Shape Word trong C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng Dẫn Từng Bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}