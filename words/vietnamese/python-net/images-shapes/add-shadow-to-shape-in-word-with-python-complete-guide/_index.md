---
category: general
date: 2026-07-29
description: Thêm bóng cho hình dạng trong Word bằng Python và Aspose.Words. Tìm hiểu
  cách áp dụng hiệu ứng bóng cho tài liệu Word một cách nhanh chóng với ví dụ mã đầy
  đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- apply shadow effect word
language: vi
lastmod: 2026-07-29
og_description: Thêm bóng cho hình dạng trong tài liệu Word bằng Python. Hướng dẫn
  này chỉ cách áp dụng hiệu ứng bóng cho các tệp Word bằng Aspose.Words, kèm mã và
  mẹo.
og_image_alt: Word document displaying a rectangle shape with a soft gray shadow applied
og_title: Thêm bóng cho hình dạng trong Word – Hướng dẫn Python
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  headline: Add Shadow to Shape in Word with Python – Complete Guide
  type: TechArticle
- description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  name: Add Shadow to Shape in Word with Python – Complete Guide
  steps:
  - name: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
    text: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
  - name: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
    text: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
  - name: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
    text: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Thêm bóng cho hình dạng trong Word bằng Python – Hướng dẫn đầy đủ
url: /vi/python/images-shapes/add-shadow-to-shape-in-word-with-python-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Bóng Đổ cho Hình Dạng trong Word bằng Python – Hướng Dẫn Toàn Diện

Bạn đã bao giờ cần **add shadow to shape** trong một tài liệu Word nhưng không chắc bắt đầu từ đâu? Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn cách thực tế để **apply shadow effect Word** các tệp bằng thư viện Aspose.Words for Python.  

Nếu bạn từng chơi đùa với giao diện người dùng và nghĩ, “Phải có cách lập trình để làm điều này,” thì bạn đang ở đúng nơi. Khi kết thúc, bạn sẽ có một script có thể chạy được, tạo ra một bóng mềm quanh bất kỳ hình dạng nào bạn chọn.

## Yêu cầu trước

- Python 3.8+ đã được cài đặt (bất kỳ phiên bản mới nào cũng hoạt động)
- Giấy phép Aspose.Words for Python đang hoạt động hoặc bản dùng thử miễn phí (API hoạt động mà không có giấy phép nhưng sẽ thêm watermark)
- Tài liệu Word (`.docx`) đã chứa ít nhất một hình dạng (hình chữ nhật, ảnh hoặc SmartArt)
- Kiến thức cơ bản về import Python và xử lý ngoại lệ

> **Mẹo chuyên nghiệp:** Nếu bạn chưa có hình dạng nào, mở Word, chèn một hình chữ nhật đơn giản, và lưu tệp dưới tên `input.docx` trong một thư mục mà bạn có thể tham chiếu từ script của mình.

## Cài đặt Aspose.Words cho Python

Chạy lệnh pip sau trong terminal của bạn:

```bash
pip install aspose-words
```

Lệnh này sẽ tải phiên bản 23.x mới nhất, hỗ trợ các thuộc tính bóng cho các nút `Shape`.

## Bước 1: Tải tài liệu Word

Điều đầu tiên chúng ta làm là mở file `.docx` hiện có. Đây là nơi bắt đầu thao tác **add shadow to shape**.

```python
import aspose.words as aw

# Load the source document
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

> **Tại sao điều này quan trọng:** `aw.Document` phân tích toàn bộ file Word thành cấu trúc giống DOM, cho phép chúng ta duyệt các nút như shape, paragraph và table.

## Bước 2: Xác định Shape mục tiêu

Aspose.Words cung cấp phương thức tìm kiếm sâu `get_child` có thể lấy shape đầu tiên bất kể mức độ lồng nhau. Nếu bạn có nhiều shape, bạn có thể điều chỉnh chỉ số hoặc lặp qua tất cả chúng.

```python
# Retrieve the first shape (deep search = True)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape and try again.")
```

> **Trường hợp đặc biệt:** Một số tài liệu chỉ chứa các đối tượng vẽ (ví dụ: ảnh). Chúng cũng được biểu diễn dưới dạng nút `Shape`, vì vậy đoạn mã này hoạt động cho cả hình chữ nhật và hình ảnh.

## Bước 3: Cấu hình ngoại hình bóng

Bây giờ là phần cốt lõi của **add shadow to shape** — thiết lập các thuộc tính bóng. Các giá trị sau tạo ra một vẻ ngoài tinh tế, chuyên nghiệp:

```python
# Softness of the shadow edges
shape.shadow_blur = 5.0

# Horizontal and vertical offsets (in points)
shape.shadow_offset_x = 2.0
shape.shadow_offset_y = 2.0

# Transparency – 0 is invisible, 1 is solid
shape.shadow_opacity = 0.7
```

Bạn có thể thử nghiệm với các số này:

- Tăng `shadow_blur` để có cạnh mờ hơn.
- Sử dụng offset âm để di chuyển bóng sang trái hoặc lên trên.
- Điều chỉnh `shadow_opacity` để làm bóng nổi bật hơn.

> **Tại sao lại dùng các giá trị mặc định này?** Độ mờ 5 điểm mô phỏng bóng mặc định của Word, trong khi độ trong suốt 0.7 giữ hiệu ứng dễ nhận thấy mà không làm mất màu nền của shape.

## Bước 4: Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi các thay đổi vào một file mới. Giữ nguyên bản gốc không thay đổi giúp việc gỡ lỗi dễ dàng hơn.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Shadow applied! Saved updated file to {output_path}")
```

Tại thời điểm này, bạn đã thực hiện thành công **add shadow to shape** và có thể mở `output.docx` để xem hiệu ứng.

## Ví dụ Hoạt động Đầy đủ

Kết hợp tất cả lại, đây là một script tự chứa mà bạn có thể sao chép‑dán và chạy ngay lập tức:

```python
import aspose.words as aw
import os

def add_shadow_to_first_shape(input_file: str, output_file: str) -> None:
    """
    Loads a Word document, adds a soft shadow to the first shape,
    and saves the result to a new file.

    Parameters
    ----------
    input_file : str
        Path to the source .docx file.
    output_file : str
        Destination path for the modified document.
    """
    # Verify the input exists
    if not os.path.isfile(input_file):
        raise FileNotFoundError(f"Input file not found: {input_file}")

    # Load the document
    doc = aw.Document(input_file)

    # Find the first shape (deep search)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape and retry.")

    # Apply shadow settings
    shape.shadow_blur = 5.0
    shape.shadow_offset_x = 2.0
    shape.shadow_offset_y = 2.0
    shape.shadow_opacity = 0.7

    # Save the updated document
    doc.save(output_file)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
    print("✅ Shadow added successfully.")
```

### Kết quả Dự kiến

Mở `output.docx` và bạn sẽ thấy shape gốc hiện đang có một bóng xám nhẹ, dịch sang phải và xuống một chút. Hiệu ứng này giống như khi bạn tự tay **apply shadow effect word** qua giao diện người dùng.

![Ví dụ hình có bóng](https://example.com/shadowed_shape.png "Hình Word với bóng mềm"){: .center-image width="600" alt="Ảnh chụp màn hình hiển thị một hình có bóng trong tài liệu Word"}

## Áp dụng Shadow Effect Word – Tùy chọn Nâng cao

Nếu bạn cần kiểm soát nhiều hơn, Aspose.Words cho phép bạn điều chỉnh các thuộc tính bổ sung:

| Thuộc tính | Mô tả | Phạm vi điển hình |
|------------|------|-------------------|
| `shadow_color` | Màu của bóng (mặc định là đen) | Bất kỳ `aw.Color` nào |
| `shadow_type` | Xác định bóng là **outer**, **inner**, hay **perspective** | enum `aw.ShadowType` |
| `shadow_transform` | Áp dụng ma trận biến đổi tùy chỉnh cho bóng lệch | Nâng cao – sử dụng hạn chế |

Ví dụ thiết lập bóng màu xanh:

```python
shape.shadow_color = aw.Color.from_argb(255, 0, 0, 255)  # Opaque blue
shape.shadow_type = aw.ShadowType.OUTER
```

Các cài đặt này cho phép bạn **apply shadow effect Word** tài liệu một cách sáng tạo, chẳng hạn như thêm bóng đổ màu vào logo.

## Những Cạm Bẫy Thường Gặp & Cách Tránh

1. **Không tìm thấy shape** – Nếu tài liệu của bạn chỉ chứa văn bản, script sẽ ném ra một `ValueError`. Thêm một shape trước hoặc mở rộng script để lặp qua tất cả các nút `Shape`.
2. **Watermark giấy phép** – Chạy code mà không có giấy phép hợp lệ sẽ chèn watermark “Aspose.Words Evaluation” trên mỗi trang. Lấy giấy phép dùng thử từ cổng Aspose để giữ đầu ra sạch sẽ.
3. **Đường dẫn tệp không đúng** – Sử dụng đường dẫn tương đối có thể gây `FileNotFoundError` khi thư mục làm việc của script khác. Nên dùng `os.path.abspath` hoặc truyền đường dẫn tuyệt đối.

## Các Bước Tiếp Theo

Bây giờ bạn đã thành thạo **add shadow to shape**, bạn có thể muốn khám phá các chủ đề liên quan:

- **Apply shadow effect Word** cho nhiều shape trong một vòng lặp
- Chuyển đổi tài liệu đã thêm bóng sang PDF (`doc.save("output.pdf")`)
- Thay đổi màu bóng dựa trên màu nền của shape (định dạng động)
- Sử dụng Aspose.Words để chèn programmatically các shape mới trước khi áp dụng bóng

Mỗi phần mở rộng này dựa trên cùng các khái niệm API, vì vậy bạn sẽ thấy đường cong học tập nhẹ nhàng.

## Kết luận

Chúng tôi đã bao phủ mọi thứ bạn cần để **add shadow to shape** trong một file Word bằng Python: tải tài liệu, xác định shape, cấu hình các tham số bóng, và lưu kết quả. Script hoàn chỉnh ở trên sẵn sàng đưa vào bất kỳ pipeline tự động nào, và các mẹo bổ sung giúp bạn **apply shadow effect Word** tài liệu trong các kịch bản phức tạp hơn.

Hãy thử nghiệm, điều chỉnh giá trị blur và opacity, và xem một bóng nhỏ có thể tạo ra sự khác biệt lớn về hình ảnh. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ code hoạt động đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Hướng dẫn Shadow Shape Aspose.Words – Thêm Bóng Đổ cho Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Tạo shape hình chữ nhật trong Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tạo tài liệu Word Java – Thêm Shape Hình Chữ Nhật với Hiệu Ứng Bóng Đổ](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}