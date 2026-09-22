---
date: 2026-02-19
description: Tìm hiểu cách tạo tài liệu có watermark bằng Aspose.Words cho Java và
  thêm watermark hình ảnh bằng Java để có các tài liệu chuyên nghiệp.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Tạo tài liệu có dấu watermark bằng Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

Last Updated:", "Tested With:", "Author:" keep as is? Should translate? The content is not part of tutorial but likely should translate. The instruction: translate all text content. So translate these lines.

**Last Updated:** 2026-02-19 -> "Cập nhật lần cuối:".

**Tested With:** Aspose.Words for Java 24.12 (latest) -> "Kiểm tra với:".

**Author:** Aspose -> "Tác giả:".

Make sure to keep bold formatting.

Now produce final content with all translations, preserving markdown.

Let's craft final answer.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu với watermark bằng Aspose.Words cho Java

Trong tutorial này bạn sẽ **tạo tài liệu với watermark** bằng API Aspose.Words cho Java. Watermark—dù là văn bản hay hình ảnh—giúp bạn gắn nhãn cho tệp là bí mật, bản nháp, hoặc đã được phê duyệt, và chúng có thể được áp dụng một cách lập trình cho bất kỳ tài liệu Word nào. Chúng tôi sẽ hướng dẫn cách cài đặt thư viện, thêm cả watermark dạng văn bản và hình ảnh, tùy chỉnh giao diện của chúng, và thậm chí xóa chúng khi không còn cần thiết.

## Câu trả lời nhanh
- **Watermark làm gì?** Nó phủ lên văn bản hoặc hình ảnh trên mỗi trang để truyền tải trạng thái hoặc thương hiệu.  
- **Thư viện nào thêm watermark trong Java?** Aspose.Words cho Java cung cấp hỗ trợ watermark tích hợp.  
- **Tôi có thể thêm watermark hình ảnh không?** Có—sử dụng lớp `Shape` và cách `add image watermark java`.  
- **Watermark có bán trong suốt không?** Bạn có thể điều chỉnh độ trong suốt bằng `setSemitransparent` cho watermark dạng văn bản.  
- **Có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.

## Watermark là gì và tại sao nên sử dụng?

Watermark là một lớp phủ mờ—văn bản hoặc đồ họa—được thêm vào mỗi trang của tài liệu. Nó thường được dùng để chỉ ra **tính bí mật**, **trạng thái bản nháp**, hoặc **thương hiệu** mà không làm thay đổi nội dung gốc. Thêm watermark một cách lập trình giúp duy trì tính nhất quán trên khối lượng lớn tệp và tiết kiệm thời gian so với việc chỉnh sửa thủ công.

## Cài đặt Aspose.Words cho Java

Trước khi bắt đầu thêm watermark, hãy chắc chắn rằng thư viện đã sẵn sàng trong dự án của bạn:

1. Tải Aspose.Words cho Java từ [here](https://releases.aspose.com/words/java/).  
2. Thêm JAR đã tải xuống (hoặc phụ thuộc Maven/Gradle) vào classpath của dự án.  
3. Nhập các lớp cần thiết vào file nguồn Java của bạn:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Bây giờ thư viện đã được cài đặt, chúng ta sẽ đi vào phần mã watermark thực tế.

## Cách thêm watermark dạng văn bản

Watermark dạng văn bản lý tưởng để gắn nhãn tài liệu là “CONFIDENTIAL” hoặc “DRAFT”. Đoạn mã dưới đây cho thấy cách **tạo tài liệu với watermark** bằng `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Tùy chỉnh watermark dạng văn bản
- **Font family & size** – thay đổi `setFontFamily` và `setFontSize`.  
- **Color** – sử dụng bất kỳ `java.awt.Color` nào.  
- **Layout** – chọn `HORIZONTAL`, `DIAGONAL`, v.v.  
- **Transparency** – bật `setSemitransparent(true)` để có vẻ nhẹ hơn.

## Cách thêm watermark dạng hình ảnh (add image watermark java)

Watermark hình ảnh hoàn hảo cho logo hoặc đồ họa tùy chỉnh. Dưới đây là ví dụ **add image watermark java** chèn một file PNG vào trung tâm mỗi trang.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Mẹo cho watermark dạng hình ảnh
- **Resize** sử dụng `setWidth` / `setHeight` để phù hợp với trang.  
- **Position** có thể được căn giữa hoặc căn chỉnh theo bất kỳ lề nào bằng `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparency** có thể áp dụng bằng cách điều chỉnh kênh alpha của hình ảnh trước khi tải.

## Cách xóa watermark

Khi tài liệu không còn cần watermark, bạn có thể xóa chúng một cách lập trình. Đoạn mã dưới đây duyệt qua tất cả các shape và loại bỏ bất kỳ shape nào có chứa “Watermark” trong tên.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Những lỗi thường gặp và cách khắc phục

- **Missing watermark after saving** – đảm bảo bạn gọi `doc.save()` sau khi thiết lập watermark.  
- **Image not appearing** – kiểm tra lại đường dẫn hình ảnh và chắc chắn file ở định dạng được hỗ trợ (PNG, JPEG, BMP).  
- **Transparency not applied** – `setSemitransparent(true)` chỉ hoạt động cho watermark dạng văn bản; đối với hình ảnh, cần chỉnh kênh alpha của PNG.  
- **Multiple sections** – nếu tài liệu có nhiều section, hãy thêm watermark vào body của mỗi section hoặc sử dụng `doc.getWatermark().setText(...)` để áp dụng toàn cục.

## Câu hỏi thường gặp

**Q: Làm thế nào để thay đổi phông chữ của watermark dạng văn bản?**  
A: Sửa thuộc tính `setFontFamily` trong `TextWatermarkOptions`, ví dụ `options.setFontFamily("Times New Roman");`.

**Q: Tôi có thể thêm nhiều watermark vào một tài liệu duy nhất không?**  
A: Có. Tạo nhiều đối tượng `Shape` (cho hình ảnh) hoặc gọi `doc.getWatermark().setText(...)` với các tùy chọn khác nhau cho mỗi watermark.

**Q: Có thể xoay watermark không?**  
A: Đối với watermark hình ảnh, đặt góc xoay trên đối tượng `Shape` bằng `watermark.setRotation(angle)`. Đối với watermark văn bản, sử dụng thuộc tính `setLayout` (ví dụ `WatermarkLayout.DIAGONAL`).

**Q: Làm sao để làm watermark bán trong suốt?**  
A: Đặt `options.setSemitransparent(true)` trong `TextWatermarkOptions`. Đối với hình ảnh, điều chỉnh độ trong suốt của hình trước khi tải.

**Q: Tôi có thể thêm watermark chỉ vào các section cụ thể của tài liệu không?**  
A: Có. Duyệt qua `doc.getSections()` và thêm watermark chỉ vào các section mong muốn.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Cập nhật lần cuối:** 2026-02-19  
**Kiểm tra với:** Aspose.Words cho Java 24.12 (latest)  
**Tác giả:** Aspose