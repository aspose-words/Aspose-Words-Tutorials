---
category: general
date: 2026-06-17
description: Học cách lưu tài liệu trong khi thêm bóng tùy chỉnh vào hình chữ nhật
  trong Python bằng Aspose.Words. Bao gồm cách thêm bóng, tạo hình chữ nhật, áp dụng
  bóng và đặt độ trong suốt.
draft: false
keywords:
- how to save document
- how to add shadow
- how to create rectangle
- how to apply shadow
- how to set opacity
language: vi
og_description: Hướng dẫn từng bước cách lưu tài liệu, thêm bóng, tạo hình chữ nhật,
  áp dụng bóng và đặt độ trong suốt bằng Aspose.Words cho Python.
og_title: Cách Lưu Tài Liệu với Hình Chữ Nhật Có Bóng – Hướng Dẫn Python Đầy Đủ
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Learn how to save document while adding a custom shadow to a rectangle
    shape in Python using Aspose.Words. Includes how to add shadow, create rectangle,
    apply shadow, and set opacity.
  headline: How to Save Document with a Shadowed Rectangle – Full Python Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Automation
title: Cách Lưu Tài Liệu với Hình Chữ Nhật Có Bóng – Hướng Dẫn Python Toàn Diện
url: /vi/python/images-shapes/how-to-save-document-with-a-shadowed-rectangle-full-python-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Lưu Tài Liệu với Hình Chữ Nhật Có Bóng – Hướng Dẫn Python Đầy Đủ

Bạn đã bao giờ tự hỏi **cách lưu tài liệu** có chứa một hình chữ nhật được tạo bóng đẹp mắt chưa? Có thể bạn đang xây dựng một trình tạo báo cáo và cần một chút sức mạnh trực quan—bạn không phải là người duy nhất. Trong tutorial này chúng ta sẽ đi qua **cách thêm bóng** vào một hình dạng, **cách tạo hình chữ nhật**, **cách áp dụng bóng**, và cuối cùng **cách đặt độ trong suốt** trước khi thực sự **lưu tài liệu**.

Chúng ta sẽ sử dụng Aspose.Words for Python via .NET, một thư viện mạnh mẽ cho phép bạn thao tác các file Word mà không cần cài Office. Khi kết thúc hướng dẫn, bạn sẽ có một script sẵn sàng chạy, tạo ra một *.docx* với hình chữ nhật trông như đang nổi lên khỏi trang. Không có phần thừa, chỉ có giải pháp thực tế, từ đầu đến cuối.

## Những Điều Bạn Sẽ Học

- Mã chính xác để **tạo một hình chữ nhật** một cách lập trình.  
- Cách kích hoạt **hiệu ứng bóng tùy chỉnh** và điều chỉnh độ mờ, khoảng cách, hướng, màu và **độ trong suốt**.  
- Lệnh chính xác để **lưu tài liệu** vào đĩa, bao gồm các lưu ý về đường dẫn thư mục.  
- Mẹo điều chỉnh các tham số bóng cho các phong cách trực quan khác nhau.  

**Yêu cầu trước:** Python 3.8+, Aspose.Words for Python via .NET (cài đặt bằng `pip install aspose-words`), và một thư mục có quyền ghi trên máy của bạn. Đó là tất cả—không cần phụ thuộc bổ sung.

![Screenshot showing how to save document with a shadowed rectangle](shadowed_rectangle.png "how to save document with a shadowed rectangle")

## Bước 1: Thiết Lập Dự Án và Nhập Aspose.Words

Trước khi chúng ta bắt đầu với các hình dạng, hãy chắc chắn rằng thư viện đã sẵn sàng.

```python
# Install Aspose.Words if you haven’t already:
# pip install aspose-words

import aspose.words as aw
```

> **Pro tip:** Sử dụng môi trường ảo để cài đặt Python toàn cục của bạn luôn sạch sẽ. Điều này cũng giúp bạn dễ dàng khóa phiên bản Aspose.Words mà bạn đã thử nghiệm.

## Bước 2: Cách Tạo Hình Chữ Nhật

Tạo một hình chữ nhật là nền tảng—​không có hình dạng thì không có bóng. Lớp `DocumentBuilder` cung cấp cho chúng ta cách fluent để chèn các hình dạng trực tiếp vào tài liệu.

```python
# Step 2: Create a new blank document and a builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert a rectangle of 200x100 points (about 2.78 x 1.39 inches)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

**Tại sao điều này quan trọng:** Phương thức `insert_shape` trả về một đối tượng `Shape` mà chúng ta có thể sửa đổi sau này. Các kích thước được biểu thị bằng điểm (1 pt = 1/72 in), cho phép bạn kiểm soát chi tiết kích thước cuối cùng.

### Tùy Chỉnh Hình Chữ Nhật (Tùy Chọn)

Bạn có thể muốn thay đổi màu nền hoặc viền:

```python
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0  # points
rectangle.line_format.color = aw.drawing.Color.dark_blue
```

Các dòng này là tùy chọn nhưng minh họa cách bạn có thể tạo kiểu cho hình chữ nhật trước khi thêm bóng.

## Bước 3: Cách Thêm Bóng – Kích Hoạt Hiệu Ứng

Bây giờ là phần thú vị: thêm bóng. Aspose.Words cung cấp thuộc tính `shadow_effect` chứa tất cả các cài đặt bóng.

```python
# Step 3: Enable and configure a custom shadow for the rectangle
shadow = rectangle.shadow_effect
shadow.enabled = True               # Turn the shadow on
shadow.blur_radius = 5.0            # Softness of the shadow edge (points)
shadow.distance = 3.0               # How far the shadow is offset (points)
shadow.direction = 45               # Angle in degrees (0 = left, 90 = down)
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6                # 60% opaque – this is where we **how to set opacity**
```

**Tại sao chúng ta thiết lập từng thuộc tính:**

- **`blur_radius`** làm mềm cạnh, giúp bóng trông tự nhiên hơn.  
- **`distance`** di chuyển bóng ra xa hình dạng; giá trị lớn hơn tạo hiệu ứng “nổi”.  
- **`direction`** quyết định nguồn sáng đến từ đâu—​45° tạo độ rơi chéo.  
- **`color`** và **`opacity`** kiểm soát trọng lượng trực quan; một màu đen bán trong suốt thường hoạt động tốt trên hầu hết tài liệu.

### Các Trường Hợp Đặc Biệt & Biến Thể

- **Bóng rất lớn:** Nếu bạn đặt `blur_radius` trên 20, bóng có thể trở nên không phân biệt được với hình dạng—​sử dụng một cách tiết chế.  
- **Độ trong suốt đầy đủ:** Đặt `opacity = 1.0` tạo bóng đen đặc; phù hợp cho tiêu đề nổi bật.  
- **Không mờ:** `blur_radius = 0` tạo bóng sắc nét, góc cứng, giống như đồ họa vector.

## Bước 4: Cách Áp Dụng Cài Đặt Bóng và Lưu Tài Liệu

Với hình chữ nhật và bóng đã được cấu hình, bước cuối cùng là ghi file. Đây là lúc chúng ta trả lời **cách lưu tài liệu**.

```python
# Step 4: Save the document with the shadowed rectangle
output_path = "output/shadowed_rectangle.docx"
document.save(output_path)

print(f"Document saved successfully at: {output_path}")
```

**Lưu ý quan trọng khi lưu:**

- Thư mục (`output/` trong ví dụ) phải tồn tại; nếu không `document.save` sẽ ném `FileNotFoundError`. Hãy dùng `os.makedirs('output', exist_ok=True)` trước nếu cần tạo thư mục một cách lập trình.  
- Aspose.Words tự động xác định định dạng file từ phần mở rộng, vì vậy `.docx` sẽ cho bạn một tài liệu Word hiện đại. Bạn cũng có thể lưu dưới dạng `.pdf` bằng cách thay đổi phần mở rộng.

## Kịch Bản Đầy Đủ – Tất Cả Các Bước Trong Một Nơi

Kết hợp mọi thứ lại, đây là script hoàn chỉnh, sẵn sàng chạy:

```python
import os
import aspose.words as aw

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# 1️⃣ Create a blank document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle (200x100 points)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional styling (feel free to comment out)
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0
rectangle.line_format.color = aw.drawing.Color.dark_blue

# 3️⃣ Configure shadow effect
shadow = rectangle.shadow_effect
shadow.enabled = True
shadow.blur_radius = 5.0
shadow.distance = 3.0
shadow.direction = 45
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6  # How to set opacity

# 4️⃣ Save the document (how to save document)
output_file = "output/shadowed_rectangle.docx"
document.save(output_file)

print(f"Document saved successfully at: {output_file}")
```

Chạy script này sẽ tạo ra `output/shadowed_rectangle.docx`. Mở nó trong Microsoft Word, và bạn sẽ thấy một hình chữ nhật màu xanh nhạt với bóng đen bán trong suốt nhẹ nhàng trôi xuống‑phải.

## Các Câu Hỏi Thường Gặp & Lưu Ý

- **“Có thể dùng loại hình dạng khác không?”** Chắc chắn. Thay `aw.drawing.ShapeType.RECTANGLE` bằng `CIRCLE`, `ELLIPSE`, hoặc bất kỳ giá trị enum nào được hỗ trợ. API bóng hoạt động tương tự.  
- **“Nếu muốn màu bóng khác thì sao?”** Chỉ cần đặt `shadow.color` thành bất kỳ `aw.drawing.Color` nào bạn muốn, ví dụ `aw.drawing.Color.gray`.  
- **“Giá trị độ trong suốt luôn nằm trong khoảng 0‑1 phải không?”** Đúng. Các giá trị ngoài khoảng này sẽ bị cắt, nhưng tốt nhất nên giữ trong khoảng 0‑1 để có kết quả dự đoán được.  
- **“Có cần gọi `document.update_page_layout()` trước khi lưu không?”** Không. Aspose.Words tự động xử lý bố cục khi lưu, mặc dù bạn có thể gọi thủ công nếu thực hiện nhiều thay đổi nặng và cần dữ liệu bố cục trung gian.

## Các Bước Tiếp Theo – Bạn Có Thể Đi Đâu

Bây giờ bạn đã biết **cách lưu tài liệu** với hình chữ nhật có bóng, bạn có thể khám phá:

- **Cách thêm bóng** vào các yếu tố khác như hình ảnh hoặc hộp văn bản.  
- **Cách tạo hình chữ nhật** với nền gradient để có hình ảnh sinh động hơn.  
- **Cách áp dụng bóng** một cách động dựa trên đầu vào của người dùng (ví dụ, cho phép UI điều chỉnh độ mờ).  
- **Cách đặt độ trong suốt** cho nhiều hình dạng chồng lên nhau để tạo hiệu ứng độ sâu.

Mỗi chủ đề trên đều dựa trên các khái niệm cốt lõi mà chúng ta đã đề cập, vì vậy bạn đã sẵn sàng mở rộng giải pháp.

---

**Kết luận:** Bạn vừa thành thạo quy trình đầy đủ—from tạo hình chữ nhật, cấu hình bóng, điều chỉnh độ trong suốt, đến cuối cùng **cách lưu tài liệu** với tất cả các cài đặt này. Hãy thử, tinh chỉnh các tham số, và xem các file Word của bạn trở nên chuyên nghiệp, có chiều sâu ba‑chiều.

Chúc bạn lập trình vui vẻ, và đừng ngại để lại bình luận nếu gặp bất kỳ khó khăn nào!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ code hoàn chỉnh và giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [How to Add Shadow in C# – Complete Programming Guide](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}