---
category: general
date: 2026-06-21
description: Tạo hình chữ nhật trong Python bằng Aspose.Words. Tìm hiểu cách thêm
  bóng cho hình, đặt màu nền cho hình và lưu tài liệu dưới dạng PDF trong vài phút.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: vi
og_description: Tạo hình chữ nhật trong Python với Aspose.Words. Hướng dẫn này chỉ
  cách thêm bóng cho hình, đặt màu nền cho hình và lưu tài liệu dưới dạng PDF.
og_title: Tạo hình chữ nhật trong Python – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Tạo hình chữ nhật trong Python – Hướng dẫn Aspose.Words
url: /vi/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Python – Hướng dẫn Aspose.Words

Bạn đã bao giờ tự hỏi **cách tạo hình chữ nhật** trong một tài liệu Word khi bạn đang lập trình bằng Python chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi họ cần một yếu tố trực quan nhanh—như một hộp màu với bóng mờ nhẹ—và sau đó xuất toàn bộ thành PDF.  

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được mà **tạo hình chữ nhật**, **đặt màu nền cho hình**, **thêm bóng cho hình**, và cuối cùng **lưu tài liệu dưới dạng PDF**. Không có các tham chiếu mơ hồ, chỉ có mã cụ thể mà bạn có thể sao chép‑dán và chạy ngay hôm nay.

## Những gì bạn cần

Trước khi bắt đầu, hãy chắc chắn rằng máy của bạn đã có:

- Python 3.8 hoặc mới hơn (cú pháp chúng tôi dùng hoạt động trên bất kỳ phiên bản mới nào).
- Giấy phép Aspose.Words for Python đang hoạt động hoặc bản dùng thử miễn phí (thư viện thuần Python, không cần COM interop).
- Một trình soạn thảo văn bản hoặc IDE mà bạn thoải mái—VS Code hoạt động tốt, nhưng bất kỳ công cụ nào cũng được.

Đó là tất cả. Không có framework nặng, không có phụ thuộc cấp hệ điều hành bổ sung. Hãy bắt đầu.

## Bước 1: Cài đặt Aspose.Words for Python

Đầu tiên, nếu bạn chưa làm, hãy tải gói từ PyPI:

```bash
pip install aspose-words
```

Tại sao bước này quan trọng: Aspose.Words cung cấp các lớp `Document` và `DocumentBuilder` mà chúng ta sẽ dựa vào. Nếu không có thư viện, các lời gọi sau này—như `insert_shape`—sẽ không tồn tại, vì vậy script sẽ bị lỗi ngay trước khi vẽ bất kỳ đường nào.

> **Pro tip:** Giữ môi trường ảo của bạn gọn gàng. Chạy `python -m venv .venv && source .venv/bin/activate` trước khi cài đặt, để thư viện được cô lập khỏi các gói hệ thống.

## Bước 2: Tạo tài liệu mới và DocumentBuilder

Bây giờ chúng ta thực sự **tạo hình chữ nhật** – nhưng trước tiên chúng ta cần một canvas trống.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Đối tượng `Document` đại diện cho toàn bộ file, trong khi `DocumentBuilder` là một trợ giúp tiện lợi biết vị trí con trỏ và có thể chèn các phần tử tại điểm đó. Hãy nghĩ về builder như một cây bút viết lên trang.

## Bước 3: Chèn hình chữ nhật

Đây là nơi hành động chính diễn ra. Chúng ta sẽ **tạo hình chữ nhật** với chiều rộng và chiều cao cố định, sau đó đặt nó trên trang.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Tại sao lại là hình chữ nhật? Đó là hình dạng đơn giản nhất vẫn cho phép chúng ta trình diễn màu nền và bóng. Nếu sau này bạn cần một vòng tròn hoặc một ngôi sao, chỉ cần thay `ShapeType.RECTANGLE` bằng một giá trị enum khác.

## Bước 4: Đặt màu nền cho hình

Một hộp trắng đơn giản không hấp dẫn lắm, vì vậy hãy **đặt màu nền cho hình** thành một màu nhẹ—xanh nhạt hoạt động tốt cho báo cáo.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Bạn có thể sử dụng bất kỳ thành viên `aw.Color` đã định nghĩa sẵn (`red`, `green`, `dark_gray`, v.v.) hoặc truyền một tuple RGB (`aw.Color.from_argb(255, 30, 144, 255)`). Màu nền là những gì người dùng nhìn thấy trước khi bất kỳ bóng hoặc viền nào được áp dụng.

## Bước 5: Thêm bóng cho hình

Bây giờ là phần hoàn thiện hình ảnh: **thêm bóng cho hình**. Bóng tạo độ sâu và làm cho hình chữ nhật nổi bật trên trang.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Cách thêm bóng**? Đoạn mã trên thực hiện đúng điều đó, nhưng hãy phân tích vì sao mỗi thuộc tính lại quan trọng:

- `visible` – bật/tắt hiệu ứng.
- `color` – xác định màu; màu xám đậm mô phỏng ánh sáng tự nhiên.
- `blur` – giá trị cao hơn tạo cạnh mềm hơn.
- `offset_x` / `offset_y` – di chuyển bóng ra xa hình; điều chỉnh chúng để mô phỏng các góc ánh sáng khác nhau.
- `transparency` – 0 là đặc, 1 là vô hình; 0.2 tạo ấn tượng nhẹ nhàng.
- `type` – `OUTER` tạo bóng bên ngoài hình, trong khi `INNER` sẽ tạo bóng bên trong.

Nếu bạn muốn một bóng đổ mạnh hơn, tăng `blur` lên 10‑15 và tăng `offset_x`/`offset_y` lên 6‑8.

## Bước 6: Lưu tài liệu dưới dạng PDF

Tất cả công việc này sẽ vô nghĩa nếu chúng ta không thể **lưu tài liệu dưới dạng PDF** và chia sẻ nó. Aspose.Words làm điều này chỉ với một dòng lệnh:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Tại sao lại là PDF? PDF giữ nguyên bố cục trên mọi nền tảng, rất thích hợp cho báo cáo, hoá đơn hoặc bất kỳ tài liệu in nào. Phương thức `save` tự động phát hiện phần mở rộng file và chọn định dạng phù hợp—chỉ cần đảm bảo đường dẫn kết thúc bằng `.pdf`.

### Kết quả mong đợi

Mở file `ShapeWithShadow.pdf` được tạo và bạn sẽ thấy một hình chữ nhật màu xanh nhạt nằm ở trung tâm gần đầu trang đầu tiên, với một bóng xám đậm mềm mại hơi lệch sang phải và xuống dưới. Các cạnh của hình rõ ràng, bóng nhẹ nhàng, và kích thước file thường dưới 100 KB.

## Bonus: Tinh chỉnh bóng – Trả lời “cách thêm bóng”

Bạn có thể tự hỏi, *“Tôi có thể thay đổi hướng bóng mà không di chuyển hình không?”* Chắc chắn rồi. Vị trí bóng độc lập với tọa độ của hình; chỉ cần điều chỉnh `offset_x` và `offset_y`. Giá trị dương di chuyển bóng sang phải/dưới, giá trị âm di chuyển sang trái/lên trên. Đối với nguồn sáng từ góc trên‑trái, dùng `offset_x = -3` và `offset_y = -3`.

Một câu hỏi thường gặp khác: *“Nếu tôi cần nhiều bóng trên cùng một hình thì sao?”* Aspose.Words chỉ hỗ trợ một bóng duy nhất cho mỗi hình. Nếu bạn cần hiệu ứng lớp, tạo một hình sao chép, dịch chuyển nhẹ và áp dụng bóng khác cho mỗi hình. Đây là một mẹo nhỏ, nhưng vẫn hoạt động.

## Kịch bản đầy đủ – Sẵn sàng chạy

Dưới đây là script hoàn chỉnh, tự chứa. Sao chép nó vào một file có tên `create_rectangle_with_shadow.py` và chạy bằng `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Lưu ý:** Thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối tồn tại trên máy của bạn. Nếu thư mục không tồn tại, Python sẽ phát sinh lỗi `FileNotFoundError`.

## Những lỗi thường gặp & Cách tránh

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|------------|----------------|
| Bóng không hiển thị | `shadow.visible` để mặc định `False` | Đảm bảo `shadow.visible = True` |
| Hình không hiển thị | Màu nền được đặt thành `aw.Color.transparent` hoặc `None` | Sử dụng màu đặc như `aw.Color.light_blue` |
| PDF trống | Quên gọi `doc.save` hoặc lưu với phần mở rộng sai | Gọi `doc.save("output.pdf")` và kiểm tra đường dẫn |
| Lỗi runtime `ImportError` | Aspose.Words chưa được cài đặt hoặc môi trường Python sai | Chạy `pip install aspose-words` trong môi trường ảo đang hoạt động |

## Các bước tiếp theo – Khám phá thêm hình dạng và định dạng

Bây giờ bạn đã thành thạo **tạo hình chữ nhật**, bạn có thể:

- Thay `ShapeType.RECTANGLE` bằng `ShapeType.ELLIPSE` hoặc `ShapeType.PENTAGON` để thử nghiệm các hình học khác.
- Thêm văn bản vào trong hình bằng cách dùng `builder.move_to(rectangle.absolute_position)` rồi `builder.writeln("Hello World")`.
- Kết hợp nhiều hình thành một nhóm với `group = aw.drawing.GroupShape(doc)` cho các sơ đồ phức tạp.
- Xuất ra các định dạng khác như DOCX (`doc.save("output.docx")`) hoặc HTML (`doc.save("output.html")`) để xem cách bóng được chuyển đổi.

Mỗi mở rộng này dựa trên các khái niệm cốt lõi: **thêm bóng cho hình**, **đặt màu nền cho hình**, và **lưu tài liệu dưới dạng PDF** (hoặc định dạng khác).

---

### Xem trước hình ảnh *(tùy chọn)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*Ảnh chụp màn hình cho thấy kết quả PDF cuối cùng với một hình chữ nhật màu xanh nhạt và một bóng ngoài nhẹ nhàng.*

---

## Kết luận

Chúng tôi đã đi qua từng bước cần thiết để **tạo hình chữ nhật** trong Python, áp dụng màu nền tùy chỉnh, **thêm bóng cho hình**, và cuối cùng **lưu tài liệu dưới dạng PDF**. Mã hoàn toàn có thể chạy, các giải thích bao gồm *tại sao* phía sau mỗi thuộc tính, và chúng tôi đã đề cập đến các trường hợp lỗi thường gặp và các bước tiếp theo—

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}