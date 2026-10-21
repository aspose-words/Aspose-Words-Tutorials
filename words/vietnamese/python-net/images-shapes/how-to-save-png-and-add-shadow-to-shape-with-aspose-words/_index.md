---
category: general
date: 2026-08-17
description: Cách lưu PNG bằng Aspose.Words cho Python. Tìm hiểu cách thêm bóng cho
  hình dạng, lưu tài liệu dưới dạng PDF và xuất Word sang PNG trong một hướng dẫn.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: vi
lastmod: 2026-08-17
og_description: Cách lưu PNG với Aspose.Words. Hướng dẫn này cho thấy cách thêm bóng
  cho một hình dạng, lưu tài liệu dưới dạng PDF và xuất Word sang PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Cách lưu PNG và thêm bóng cho hình dạng bằng Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Cách lưu PNG và thêm bóng cho hình dạng với Aspose.Words
url: /vi/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách lưu PNG và thêm bóng cho hình dạng với Aspose.Words

Nếu bạn cần **cách lưu PNG** từ một tệp Word, hướng dẫn này cung cấp cho bạn một giải pháp hoàn chỉnh, có thể chạy được. Bạn cũng sẽ thấy cách **thêm bóng cho hình dạng**, **lưu tài liệu dưới dạng PDF**, và **xuất Word sang PNG** mà không rời khỏi môi trường Aspose.Words.

Bài hướng dẫn bao gồm mọi thứ cần thiết để chuyển một tài liệu Word trống thành tệp PDF và hình ảnh PNG, đồng thời áp dụng hiệu ứng bóng đơn giản cho một hình chữ nhật. Không cần công cụ bên ngoài, và mã hoạt động với Aspose.Words for Python via .NET 7 hoặc mới hơn.

## Những gì bạn sẽ đạt được

* Tạo một tài liệu Word mới bằng cách lập trình.  
* Chèn một hình chữ nhật và cấu hình hiệu ứng bóng.  
* Lưu cùng một tài liệu dưới dạng tệp PDF.  
* Xuất tài liệu dưới dạng hình ảnh PNG.  

Các bước này trả lời câu hỏi phổ biến **cách lưu PNG** đồng thời xử lý **thêm bóng cho hình dạng** và **lưu tài liệu dưới dạng PDF** trong một quy trình làm việc duy nhất.

## Yêu cầu trước

* Python 3.9 hoặc mới hơn.  
* Aspose.Words for Python via .NET đã được cài đặt (`pip install aspose-words`).  
* Quyền ghi vào thư mục đầu ra mà bạn chỉ định.  

Nếu bạn chưa cài đặt Aspose.Words, hãy chạy:

```bash
pip install aspose-words
```

## Cách lưu PNG với Aspose.Words

Bước quan trọng đầu tiên là tạo một tài liệu và một `DocumentBuilder`. Builder cung cấp cho bạn một API mượt mà để chèn nội dung như hình dạng, bảng hoặc văn bản.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` đại diện cho toàn bộ tệp Word trong bộ nhớ. `aw.DocumentBuilder` chỉ tới vị trí chèn hiện tại, ban đầu là đầu của phần đầu tiên (và duy nhất).

## Thêm bóng cho hình dạng trước khi xuất

Một hình dạng có thể là bất kỳ đối tượng vẽ nào—hình chữ nhật, elip, hoặc đa giác tùy chỉnh. Ở đây chúng ta tạo một hình chữ nhật 100 × 100 point và áp dụng bóng mềm.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Tại sao phải cấu hình bóng trước khi lưu? Aspose.Words render bóng trong quá trình xuất PDF và PNG, vì vậy hiệu ứng hình ảnh được giữ nguyên trong cả hai định dạng đầu ra.

### Mẹo chuyên nghiệp
Nếu bạn cần bóng sắc hơn, giảm `blur`. Để tăng độ lệch rõ ràng hơn, tăng `distance`. Lớp `Shadow` cũng cung cấp `angle` và `transparency` để kiểm soát chi tiết.

## Lưu tài liệu dưới dạng PDF

Lưu một tài liệu Word dưới dạng PDF chỉ cần một dòng lệnh khi nội dung đã sẵn sàng. Hằng số `SaveFormat.PDF` cho Aspose.Words biết thực hiện chuyển đổi.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

PDF kết quả chứa hình chữ nhật với bóng chính xác như bạn đã định nghĩa. Aspose.Words xử lý đồ họa vector, vì vậy kích thước PDF vẫn ở mức vừa phải.

## Xuất Word sang PNG

Xuất sang PNG tạo ra một hình ảnh raster cho mỗi trang. Mặc định Aspose.Words sử dụng 96 DPI; bạn có thể tăng giá trị này để có đầu ra độ phân giải cao hơn bằng cách cung cấp một đối tượng `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Khi bạn **xuất Word sang PNG**, mỗi trang được lưu dưới dạng một tệp PNG riêng. Vì tài liệu mẫu của chúng tôi chỉ có một trang, chỉ có một tệp PNG duy nhất xuất hiện.

### Tùy chọn: PNG độ phân giải cao hơn

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

DPI cao hơn hữu ích khi PNG sẽ được sử dụng trong in ấn hoặc khi bạn cần một hình thu nhỏ sắc nét.

## Kịch bản đầy đủ – sao chép, dán và chạy

Dưới đây là kịch bản hoàn chỉnh, tự chứa, thực hiện mọi bước đã mô tả ở trên. Lưu nó dưới tên `generate_assets.py` và chạy từ dòng lệnh.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Kết quả mong đợi

Chạy kịch bản sẽ tạo ba tệp:

* `output/output.pdf` – một PDF với hình chữ nhật tạo ra bóng đen.  
* `output/output.png` – một PNG 96 DPI hiển thị cùng một trang.  
* `output/high_res_output.png` – một PNG 300 DPI cho chất lượng cao hơn.  

Mở bất kỳ tệp nào trong trình xem yêu thích của bạn để xác nhận rằng bóng xuất hiện chính xác như đã định nghĩa.

## Các câu hỏi thường gặp và các trường hợp đặc biệt

**Nếu thư mục đầu ra không tồn tại thì sao?**  
Kịch bản gọi `os.makedirs(output_dir, exist_ok=True)`, tạo thư mục tự động. Điều này ngăn lỗi `FileNotFoundError` trong quá trình lưu.

**Tôi có thể thêm nhiều hình dạng với các bóng khác nhau không?**  
Có. Tạo các đối tượng `Shape` bổ sung, cấu hình mỗi thuộc tính `shadow` một cách độc lập, và chèn chúng bằng `builder.insert_node(shape)` trước khi lưu.

**Bóng sẽ được giữ lại khi chuyển sang các định dạng raster khác (ví dụ, JPEG) không?**  
Aspose.Words render bóng cho tất cả các định dạng raster được `SaveFormat` hỗ trợ. Bạn có thể thay `aw.SaveFormat.PNG` bằng `aw.SaveFormat.JPEG` và bóng vẫn sẽ xuất hiện.

**Điều này khác gì so với “convert word to pdf”?**  
`convert word to pdf` thực chất là cùng một thao tác được thực hiện ở bước 4. Lệnh `doc.save` với `SaveFormat.PDF` xử lý chuyển đổi nội bộ, giữ nguyên bố cục, phông chữ và đồ họa như bóng.

**Có giới hạn nào về kích thước hình dạng không?**  
Hình dạng được đo bằng point (1 pt ≈ 1/72 inch). Kích thước rất lớn có thể làm tăng kích thước tệp kết quả, nhưng Aspose.Words không đặt giới hạn cứng. Điều chỉnh các đối số `width` và `height` khi tạo `aw.Shape` để phù hợp với bố cục của bạn.

## Kết luận

Bạn đã biết **cách lưu PNG** từ một tài liệu Word đồng thời học cách **thêm bóng cho hình dạng**, **lưu tài liệu dưới dạng PDF**, và **xuất Word sang PNG** bằng Aspose.Words for Python. Kịch bản hoàn chỉnh minh họa một mẫu sạch sẽ, có thể lặp lại mà bạn có thể áp dụng cho tài liệu lớn hơn, nhiều trang, hoặc các hiệu ứng đồ họa phức tạp hơn.

Các bước tiếp theo có thể bao gồm:

* Thử nghiệm các giá trị `ShapeType` khác (ellipse, cloud, v.v.).  
* Using `

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao phủ các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Hướng dẫn Bóng Hình dạng Aspose.Words – Thêm Bóng cho Hình dạng Word trong C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cách Chuyển DOCX sang PNG trong Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Lưu Tài liệu Word dưới dạng PostScript trong Python bằng Aspose.Words: Hướng dẫn Toàn diện](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}