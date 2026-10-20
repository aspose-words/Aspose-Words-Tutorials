---
date: 2025-12-14
description: Tìm hiểu cách **chèn hình ảnh dạng shape** bằng Aspose.Words cho Java.
  Hướng dẫn này chỉ cho bạn cách thêm các shape, tạo các shape hộp văn bản, đặt shape
  vào bảng, thiết lập tỷ lệ khung hình của shape và thêm các shape chú thích.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Sử dụng các hình dạng tài liệu trong Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách **chèn hình ảnh dạng shape** với Aspose.Words for Java

Trong hướng dẫn toàn diện này, bạn sẽ khám phá cách **chèn hình ảnh dạng shape** vào tài liệu Word bằng Aspose.Words for Java. Dù bạn đang tạo báo cáo, tài liệu marketing, hay biểu mẫu tương tác, các shape cho phép bạn thêm callout, nút bấm, hộp văn bản, watermark và thậm chí SmartArt. Chúng tôi sẽ hướng dẫn từng bước, giải thích lý do sử dụng mỗi loại shape, và cung cấp các đoạn mã sẵn sàng chạy.

## Trả lời nhanh
- **Cách chính để thêm một shape là gì?** Sử dụng `DocumentBuilder.insertShape` hoặc tạo một thể hiện `Shape` và thêm nó vào cây tài liệu.  
- **Tôi có thể chèn hình ảnh dưới dạng shape không?** Có – gọi `builder.insertImage` rồi xử lý `Shape` trả về như bất kỳ shape nào khác.  
- **Làm sao để giữ tỷ lệ khung hình của shape?** Đặt `shape.setAspectRatioLocked(true)` hoặc `false` tùy nhu cầu.  
- **Có thể nhóm các shape lại với nhau không?** Chắc chắn – bọc chúng trong một `GroupShape` và chèn nhóm như một nút duy nhất.  
- **Các sơ đồ SmartArt có hoạt động với Aspose.Words không?** Có, bạn có thể phát hiện và cập nhật các shape SmartArt bằng chương trình.

## **insert image shape** là gì?
*Image shape* là một thành phần trực quan chứa đồ họa raster hoặc vector trong tài liệu Word. Trong Aspose.Words, hình ảnh được biểu diễn bằng một đối tượng `Shape`, cho phép bạn kiểm soát hoàn toàn kích thước, vị trí, góc quay và cách bọc.

## Tại sao nên sử dụng shape trong tài liệu?
- **Tác động thị giác:** Shape thu hút sự chú ý tới thông tin quan trọng.  
- **Tính tương tác:** Nút bấm và callout có thể liên kết tới URL hoặc bookmark.  
- **Linh hoạt bố cục:** Đặt đồ họa một cách chính xác bằng tọa độ tuyệt đối hoặc tương đối.  
- **Tự động hoá:** Tạo bố cục phức tạp mà không cần chỉnh sửa thủ công.

## Yêu cầu trước
- Java Development Kit (JDK 8 hoặc cao hơn)  
- Thư viện Aspose.Words for Java (tải về từ trang chính thức)  
- Kiến thức cơ bản về Java và lập trình hướng đối tượng  

Bạn có thể tải thư viện tại đây: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Cách **thêm shape** – Chèn một GroupShape
`GroupShape` cho phép bạn xử lý nhiều shape như một đơn vị duy nhất. Điều này hữu ích khi di chuyển hoặc định dạng đồng thời nhiều phần tử.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## Tạo **shape hộp văn bản**
Hộp văn bản là một container có thể chứa văn bản đã định dạng. Bạn cũng có thể xoay nó để tạo hiệu ứng động.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Đặt **tỷ lệ khung hình của shape**
Đôi khi bạn muốn shape tự do kéo dài, đôi khi lại muốn giữ nguyên tỉ lệ gốc. Kiểm soát tỷ lệ khung hình rất đơn giản.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Đặt **shape vào bảng**
Nhúng shape vào ô bảng có thể hữu ích cho bố cục báo cáo. Ví dụ dưới đây tạo một bảng và chèn một shape kiểu watermark phủ toàn trang.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Thêm **shape callout**
Shape callout hoàn hảo để làm nổi bật ghi chú hoặc cảnh báo. Mặc dù đoạn mã trên đã minh họa `ACCENT_BORDER_CALLOUT_1`, bạn có thể thay đổi `ShapeType` sang bất kỳ biến thể callout nào phù hợp với thiết kế.

## Làm việc với Shape SmartArt

### Phát hiện Shape SmartArt
Các sơ đồ SmartArt có thể được xác định bằng chương trình, cho phép bạn xử lý hoặc thay thế chúng khi cần.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Cập nhật bản vẽ SmartArt
Sau khi phát hiện, bạn có thể làm mới đồ họa SmartArt để phản ánh bất kỳ thay đổi dữ liệu nào.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Các vấn đề thường gặp & Mẹo
- **Shape không hiển thị:** Đảm bảo shape được chèn sau nút mục tiêu bằng `builder.insertNode`.  
- **Xoay không mong muốn:** Nhớ rằng việc xoay được thực hiện quanh trung tâm của shape; điều chỉnh `setLeft`/`setTop` nếu cần.  
- **Tỷ lệ khung hình bị khóa:** Mặc định, nhiều shape khóa tỷ lệ; gọi `setAspectRatioLocked(false)` để kéo dài tự do.  
- **Phát hiện SmartArt thất bại:** Kiểm tra bạn đang dùng phiên bản Aspose.Words hỗ trợ SmartArt (v24+).

## Câu hỏi thường gặp

**Hỏi: Aspose.Words for Java là gì?**  
Đáp: Aspose.Words for Java là một thư viện Java cho phép các nhà phát triển tạo, sửa đổi và chuyển đổi tài liệu Word một cách lập trình. Nó cung cấp một loạt các tính năng và công cụ để làm việc với tài liệu ở nhiều định dạng.

**Hỏi: Làm sao để tải Aspose.Words for Java?**  
Đáp: Bạn có thể tải Aspose.Words for Java từ trang web Aspose bằng liên kết này: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Hỏi: Lợi ích của việc sử dụng shape trong tài liệu là gì?**  
Đáp: Shape bổ sung các yếu tố trực quan và tính tương tác cho tài liệu, làm cho chúng hấp dẫn và thông tin hơn. Với shape, bạn có thể tạo callout, nút bấm, hình ảnh, watermark và nhiều hơn nữa, nâng cao trải nghiệm người dùng.

**Hỏi: Tôi có thể tùy chỉnh giao diện của shape không?**  
Đáp: Có, bạn có thể tùy chỉnh giao diện của shape bằng cách điều chỉnh các thuộc tính như kích thước, vị trí, góc quay và màu nền. Aspose.Words for Java cung cấp nhiều tùy chọn để tùy biến shape.

**Hỏi: Aspose.Words for Java có hỗ trợ SmartArt không?**  
Đáp: Có, Aspose.Words for Java hỗ trợ các shape SmartArt, cho phép bạn làm việc với các sơ đồ và đồ họa phức tạp trong tài liệu.

---

**Cập nhật lần cuối:** 2025-12-14  
**Đã kiểm tra với:** Aspose.Words for Java 24.12 (phiên bản mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}