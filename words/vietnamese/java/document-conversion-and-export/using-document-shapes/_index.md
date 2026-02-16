---
date: 2026-02-16
description: Tìm hiểu cách tạo hộp văn bản, thêm từ watermark, nhóm nhiều hình dạng,
  đặt tỷ lệ khung hình cho hình dạng và đặt hình dạng vào ô bảng bằng Aspose.Words
  cho Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Cách tạo hộp văn bản và sử dụng Hình dạng Tài liệu trong Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Các Hình Dạng Tài Liệu trong Aspose.Words cho Java

## Giới thiệu về việc Sử dụng Các Hình Dạng Tài Liệu trong Aspose.Words cho Java

Trong hướng dẫn toàn diện này, **bạn sẽ học cách tạo các đối tượng text box** và các hình dạng mạnh mẽ khác với Aspose.Words cho Java. Các hình dạng cho phép bạn làm phong phú tài liệu Word bằng các callout, nút, watermark, SmartArt và hơn thế nữa—giúp chúng trở nên hấp dẫn và tương tác. Chúng tôi sẽ hướng dẫn qua các ví dụ thực tế, từ việc chèn một text box đơn giản đến việc nhóm nhiều hình dạng, thiết lập tỷ lệ khung hình, và đặt hình dạng bên trong các ô bảng.

## Câu trả lời nhanh
- **Cách chính để thêm một text box là gì?** Sử dụng `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Tôi có thể nhóm các hình dạng lại với nhau không?** Có – tạo một `GroupShape` và thêm các hình con.
- **Làm sao để khóa hoặc mở khóa tỷ lệ khung hình của một hình dạng?** Gọi `shape.setAspectRatioLocked(true/false)`.
- **Có thể thêm watermark bằng một hình dạng không?** Chắc chắn – chèn một `Shape` với `TEXT_PLAIN_TEXT` và thiết lập fill/stroke.
- **Các biểu đồ SmartArt có hoạt động với Aspose.Words không?** Có – phát hiện bằng `shape.hasSmartArt()` và cập nhật qua `shape.updateSmartArtDrawing()`.

## Text box là gì và tại sao tạo các hình dạng text box?

Text box là một container có thể chứa văn bản định dạng, hình ảnh hoặc các hình dạng khác. Sử dụng **create text box** trong tự động hoá của bạn cho phép đặt nội dung nổi lên bất kỳ vị trí nào trên trang, rất phù hợp cho chú thích, callout hoặc các yếu tố trang trí mà không làm thay đổi luồng tài liệu chính.

## Cách thêm hình dạng

Trước khi chúng ta đi vào mã, hãy chắc chắn rằng Aspose.Words cho Java đã được tham chiếu trong dự án của bạn. Nếu bạn chưa thêm, tải thư viện từ trang chính thức:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Thêm Hình Dạng vào Tài Liệu

## Cách nhóm nhiều hình dạng

`GroupShape` cho phép bạn xử lý nhiều hình dạng riêng lẻ như một đơn vị duy nhất—hữu ích khi di chuyển hoặc xoay chúng cùng nhau.

### Chèn một GroupShape

Dưới đây là một ví dụ hoàn chỉnh tạo một nhóm, thêm hai hình dạng khác nhau, và chèn nhóm vào tài liệu.

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

## Cách tạo một text box (create text box)

### Chèn Hình Dạng Text Box

Phương thức `insertShape` giúp việc thêm một text box trở nên đơn giản. Ví dụ dưới đây cho thấy hai cách định vị và xoay một text box.

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

## Cách thiết lập tỷ lệ khung hình cho hình dạng

### Quản lý Tỷ lệ Khung hình

Đôi khi bạn cần một hình dạng kéo dài mà không giữ nguyên tỉ lệ ban đầu. Đoạn mã sau minh họa cách mở khóa tỷ lệ khung hình của một hình ảnh.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Cách đặt hình dạng trong một ô bảng

### Đặt Hình Dạng vào Trong Ô Bảng

Dưới đây là ví dụ từng bước xây dựng một bảng, sau đó chèn một hình watermark được định vị tương đối với trang nhưng cũng có thể đặt bên trong một ô.

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

## Làm việc với Các Hình Dạng SmartArt

### Phát hiện Các Hình Dạng SmartArt

Bạn có thể tìm kiếm các đối tượng SmartArt trong tài liệu một cách lập trình bằng phương thức `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Cập nhật Vẽ SmartArt

Sau khi đã xác định được các hình SmartArt, bạn có thể làm mới dữ liệu vẽ nội bộ của chúng bằng `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Kết luận

Trong hướng dẫn này, chúng tôi đã trình bày cách **create text box** các đối tượng, nhóm nhiều hình dạng, điều chỉnh tỷ lệ khung hình, nhúng hình dạng vào các ô bảng, thêm watermark, và làm việc với các biểu đồ SmartArt bằng Aspose.Words cho Java. Những kỹ thuật này cho phép bạn xây dựng các tài liệu Word phong phú, định dạng tốt và tương tác một cách lập trình.

## Câu hỏi thường gặp

### Aspose.Words cho Java là gì?

Aspose.Words cho Java là một thư viện Java cho phép các nhà phát triển tạo, chỉnh sửa và chuyển đổi tài liệu Word một cách lập trình. Nó cung cấp một loạt các tính năng và công cụ để làm việc với tài liệu ở nhiều định dạng khác nhau.

### Làm sao để tải Aspose.Words cho Java?

Bạn có thể tải Aspose.Words cho Java từ trang web Aspose bằng cách theo liên kết này: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Lợi ích của việc sử dụng các hình dạng tài liệu là gì?

Các hình dạng tài liệu thêm các yếu tố trực quan và tính tương tác vào tài liệu của bạn, làm chúng trở nên hấp dẫn và thông tin hơn. Với các hình dạng, bạn có thể tạo callout, nút, hình ảnh, watermark và hơn thế nữa, nâng cao trải nghiệm người dùng tổng thể.

### Tôi có thể tùy chỉnh giao diện của các hình dạng không?

Có, bạn có thể tùy chỉnh giao diện của các hình dạng bằng cách điều chỉnh các thuộc tính như kích thước, vị trí, góc xoay và màu nền. Aspose.Words cho Java cung cấp nhiều tùy chọn để tùy chỉnh hình dạng.

### Aspose.Words cho Java có tương thích với SmartArt không?

Có, Aspose.Words cho Java hỗ trợ các hình dạng SmartArt, cho phép bạn làm việc với các sơ đồ và đồ họa phức tạp trong tài liệu.

## Các Câu Hỏi Thường Gặp

**Q: Tôi có thể kết hợp một text box với hình ảnh bên trong cùng một hình dạng không?**  
A: Có. Chèn một hình ảnh vào hình dạng text box bằng `builder.insertImage()` sau khi tạo hình dạng, sau đó điều chỉnh bố cục theo nhu cầu.

**Q: Làm sao để đảm bảo watermark hiển thị phía sau tất cả nội dung tài liệu?**  
A: Đặt `WrapType` của hình dạng thành `NONE` và điều chỉnh `RelativeHorizontalPosition` và `RelativeVerticalPosition` thành `PAGE`. Điều này sẽ đặt watermark phía sau luồng chính.

**Q: Có thể tạo hoạt ảnh cho một nhóm hình dạng trong Word không?**  
A: Mặc dù Aspose.Words có thể tạo và nhóm các hình dạng, tính năng hoạt ảnh không được hỗ trợ vì chúng dựa vào khả năng UI của Word.

**Q: Phiên bản Aspose.Words nào cần thiết để hỗ trợ SmartArt?**  
A: Phát hiện và cập nhật SmartArt có sẵn bắt đầu từ Aspose.Words 20.9 cho Java và các phiên bản sau.

**Q: Thư viện có xử lý hiệu quả các tài liệu lớn với nhiều hình dạng không?**  
A: Có. Sử dụng `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` hoặc cao hơn để cải thiện hiệu năng trên các tài liệu có nhiều hình dạng.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}