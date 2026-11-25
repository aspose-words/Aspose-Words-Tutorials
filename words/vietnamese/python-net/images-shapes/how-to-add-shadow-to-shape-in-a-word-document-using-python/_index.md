---
category: general
date: 2026-11-25
description: Thêm bóng cho hình dạng trong tài liệu Word bằng Python. Tìm hiểu cách
  chèn hình chữ nhật trong Word và áp dụng bóng trong suốt bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: vi
lastmod: 2026-11-25
og_description: Thêm bóng cho hình dạng trong tài liệu Word bằng Python. Hướng dẫn
  này cho thấy cách chèn một hình chữ nhật trong Word và đặt bóng trong suốt 30 %
  bằng Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Thêm bóng cho hình dạng trong tài liệu Word bằng Python – hướng dẫn từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Cách thêm bóng cho hình dạng trong tài liệu Word bằng Python
url: /vi/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm bóng cho hình dạng trong tài liệu Word bằng Python

Nếu bạn cần **add shadow to shape** trong một tài liệu Word, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, có thể chạy được. Bạn sẽ thấy cách tạo tệp Word, chèn một hình chữ nhật, và áp dụng bóng trong suốt 30 % — tất cả đều bằng thư viện Aspose.Words for Python.

Làm việc với tài liệu Word một cách lập trình giúp bạn tránh việc định dạng thủ công và cho phép tạo báo cáo, hợp đồng, hoặc tờ rơi marketing ở quy mô lớn. Khi kết thúc hướng dẫn này, bạn sẽ có thể trả lời “**how to create Word document python**” bằng một mẫu mã sẵn sàng chạy.

## Yêu cầu trước

* Python 3.8 hoặc mới hơn đã được cài đặt.
* Giấy phép Aspose.Words for Python đang hoạt động (bản dùng thử miễn phí dùng cho đánh giá).
* Gói `aspose-words` được cài đặt qua `pip install aspose-words`.
* Thư mục nơi có thể ghi tệp đầu ra (thay thế `YOUR_DIRECTORY` trong mã).

Không cần phụ thuộc bổ sung nào.

## Bước 1: Tạo tài liệu Word mới

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp .docx trong bộ nhớ.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` hoạt động như một con trỏ ảo. Khi bạn gọi các phương thức của nó, thư viện sẽ chèn các phần tử tương ứng tại vị trí con trỏ hiện tại.

## Bước 2: Chèn hình chữ nhật vào Word

Tiếp theo bạn **insert rectangle shape word** bằng cách sử dụng phương thức `insert_shape` của builder. Phương thức này yêu cầu loại hình dạng và kích thước của nó tính bằng điểm (1 point = 1/72 inch).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Bạn có thể thay đổi kích thước để phù hợp với thiết kế của mình. Hình chữ nhật sẽ trở thành một phần của lớp vẽ trong tài liệu, có nghĩa là bạn có thể chỉnh sửa màu nền, viền, hoặc bóng sau này.

## Bước 3: Truy cập định dạng bóng của hình dạng

Mỗi đối tượng vẽ đều cung cấp thuộc tính `shadow_format` để điều khiển cách hiển thị bóng. Lấy nó để bạn có thể điều chỉnh độ trong suốt, độ lệch, độ mờ và màu sắc.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Tại thời điểm này, hình dạng có bóng mặc định (không có bóng). Đối tượng `ShadowFormat` chứa tất cả các tham số bạn cần để tạo hiệu ứng thực tế.

## Bước 4: Đặt bóng trong suốt 30 %

Độ trong suốt được biểu thị bằng giá trị từ `0` (độ mờ hoàn toàn) đến `1` (độ trong suốt hoàn toàn). Đặt nó thành `0.3` sẽ tạo ra bóng trong suốt 30 %, thường đủ để tạo độ sâu mà không làm lấn át văn bản.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Các thuộc tính bổ sung này không bắt buộc, nhưng chúng minh họa cách bạn có thể tinh chỉnh hiệu ứng. Cờ `visible` là cần thiết; nếu bạn quên, bóng sẽ không hiển thị dù các thiết lập khác đã được cấu hình.

## Bước 5: Lưu tài liệu để xem kết quả

Cuối cùng, ghi tài liệu ra đĩa. Mở tệp `.docx` kết quả trong Microsoft Word hoặc bất kỳ trình xem tương thích nào sẽ hiển thị hình chữ nhật với bóng trong suốt đã được áp dụng.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Khi bạn mở `output.docx`, bạn sẽ thấy một hình chữ nhật đơn giản với bóng xám nhẹ lệch về phía dưới‑phải. Độ trong suốt 30 % của bóng khiến hình dạng trông như được nâng lên khỏi trang.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Ví dụ thêm bóng cho hình dạng trong tài liệu Word được tạo bằng Python"}

## Đoạn mã đầy đủ, có thể chạy

Kết hợp tất cả các phần lại với nhau sẽ cho bạn một đoạn mã tự chứa mà bạn có thể sao chép, dán và chạy ngay lập tức.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Kết quả mong đợi:** Khi mở `output.docx` đã tạo, sẽ hiển thị một trang duy nhất với một hình chữ nhật tạo ra bóng nhẹ, bán trong suốt. Không cần định dạng bổ sung nào.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cách điều chỉnh mã |
|-----------|--------------------|
| **Kiểu hình dạng khác** (ví dụ: ellipse) | Thay `aw.drawing.ShapeType.RECTANGLE` bằng `aw.drawing.ShapeType.ELLIPSE`. |
| **Màu bóng tùy chỉnh** | Đặt `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` để có bóng màu đỏ. |
| **Nhiều hình dạng** | Gọi `builder.insert_shape` nhiều lần; mỗi lần gọi trả về một đối tượng `Shape` riêng mà bạn có thể định dạng độc lập. |
| **Lưu dưới dạng PDF** | Thay `doc.save(output_path)` bằng `doc.save(output_path.replace('.docx', '.pdf'))` và sử dụng phần mở rộng `.pdf`. |
| **Chạy mà không có giấy phép** | Bản dùng thử miễn phí sẽ thêm watermark vào trang đầu. Mua giấy phép để loại bỏ nó trong môi trường sản xuất. |

## Mẹo và thực hành tốt nhất

* **Reuse the builder**: Giữ một thể hiện `DocumentBuilder` duy nhất cho toàn bộ tài liệu để tránh tạo đối tượng không cần thiết.
* **Dispose resources**: Trong các dịch vụ chạy lâu, gọi `doc.dispose()` sau khi lưu để giải phóng bộ nhớ gốc.
* **Validate output**: Sử dụng `doc.validate(aw.ValidationType.FULL_VALIDATION)` trước khi lưu nếu bạn cần đảm bảo tuân thủ tiêu chuẩn Open XML.
* **Version compatibility**: Đoạn mã hoạt động với Aspose.Words for Python ≥ 22.9. Đảm bảo gói của bạn được cập nhật bằng `pip install --upgrade aspose-words`.

## Kết luận

Bây giờ bạn đã biết cách **add shadow to shape** trong tài liệu Word bằng Python. Bằng cách thực hiện năm bước—tạo tài liệu, **insert rectangle shape word**, cấu hình bóng, và lưu—bạn có thể tự động tạo tài liệu chuyên nghiệp cho báo cáo, hoá đơn, hoặc tài liệu marketing.

Từ đây bạn có thể khám phá các tùy chọn định dạng khác như màu nền gradient, bọc văn bản, hoặc chuyển đổi tài liệu sang PDF. Mỗi chủ đề đó dựa trên cùng các khái niệm `DocumentBuilder` và định dạng hình dạng đã được giới thiệu trong hướng dẫn này.

Chúc lập trình vui vẻ, và tận hưởng độ sâu trực quan mà một bóng đơn giản có thể mang lại cho các tài liệu Word tự động của bạn!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo hình chữ nhật trong tài liệu Word bằng Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Thêm Bóng cho Hình trong Python – Hướng dẫn đầy đủ Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Tạo Tài liệu Word Trống và Thêm Bóng cho Hình – Hướng dẫn Python đầy đủ](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}