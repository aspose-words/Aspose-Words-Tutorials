---
"description": "Mở khóa sức mạnh của hình dạng tài liệu trong Aspose.Words cho Java. Học cách tạo tài liệu hấp dẫn trực quan với các ví dụ từng bước."
"linktitle": "Sử dụng hình dạng tài liệu"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng Document Shapes trong Aspose.Words cho Java"
"url": "/vi/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Document Shapes trong Aspose.Words cho Java


## Giới thiệu về cách sử dụng Document Shapes trong Aspose.Words cho Java

Trong hướng dẫn toàn diện này, chúng ta sẽ đi sâu vào thế giới hình dạng tài liệu trong Aspose.Words for Java. Hình dạng là yếu tố thiết yếu khi tạo tài liệu hấp dẫn về mặt thị giác và tương tác. Cho dù bạn cần thêm chú thích, nút, hình ảnh hay hình mờ, Aspose.Words for Java đều cung cấp các công cụ để thực hiện hiệu quả. Hãy cùng khám phá cách sử dụng các hình dạng này từng bước với các ví dụ về mã nguồn.

## Bắt đầu với Hình dạng Tài liệu

Trước khi bắt đầu code, hãy thiết lập môi trường của chúng ta. Đảm bảo bạn đã tích hợp Aspose.Words for Java vào dự án của mình. Nếu bạn chưa có, bạn có thể tải xuống từ trang web Aspose [Tải xuống Aspose.Words cho Java](https://releases.aspose.com/words/java/)

## Thêm hình dạng vào tài liệu

### Chèn GroupShape

MỘT `GroupShape` cho phép bạn nhóm nhiều hình dạng lại với nhau. Sau đây là cách bạn có thể tạo và chèn một `GroupShape`:

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

### Chèn hình hộp văn bản

Để chèn hình hộp văn bản, bạn có thể sử dụng `insertShape` phương pháp như thể hiện trong ví dụ dưới đây:

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

## Thao tác các thuộc tính hình dạng

### Quản lý tỷ lệ khung hình

Bạn có thể kiểm soát tỷ lệ khung hình của một hình dạng có bị khóa hay không. Sau đây là cách mở khóa tỷ lệ khung hình của một hình dạng:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Đặt một hình dạng vào một ô trong bảng

Nếu bạn cần đặt một hình dạng bên trong ô của bảng, bạn có thể thực hiện điều này bằng đoạn mã sau:

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
watermark.isLayoutInCell(true); // Hiển thị hình dạng bên ngoài ô của bảng nếu nó sẽ được đặt vào trong ô.
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

## Làm việc với các hình dạng SmartArt

### Phát hiện hình dạng SmartArt

Bạn có thể phát hiện các hình dạng SmartArt trong tài liệu bằng cách sử dụng mã sau:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Cập nhật bản vẽ SmartArt

Để cập nhật bản vẽ SmartArt trong tài liệu, hãy sử dụng mã sau:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã khám phá thế giới hình dạng tài liệu trong Aspose.Words for Java. Bạn đã học cách thêm nhiều hình dạng khác nhau vào tài liệu của mình, thao tác các thuộc tính của chúng và làm việc với các hình dạng SmartArt. Với kiến thức này, bạn có thể dễ dàng tạo các tài liệu hấp dẫn về mặt thị giác và tương tác.

## Câu hỏi thường gặp

### Aspose.Words dành cho Java là gì?

Aspose.Words for Java là một thư viện Java cho phép các nhà phát triển tạo, sửa đổi và chuyển đổi các tài liệu Word theo chương trình. Nó cung cấp nhiều tính năng và công cụ để làm việc với các tài liệu ở nhiều định dạng khác nhau.

### Làm thế nào tôi có thể tải xuống Aspose.Words cho Java?

Bạn có thể tải xuống Aspose.Words cho Java từ trang web Aspose bằng cách nhấp vào liên kết này: [Tải xuống Aspose.Words cho Java](https://releases.aspose.com/words/java/)

### Lợi ích của việc sử dụng hình dạng tài liệu là gì?

Hình dạng tài liệu thêm các yếu tố trực quan và tính tương tác vào tài liệu của bạn, khiến chúng hấp dẫn và nhiều thông tin hơn. Với hình dạng, bạn có thể tạo chú thích, nút, hình ảnh, hình mờ, v.v., nâng cao trải nghiệm chung của người dùng.

### Tôi có thể tùy chỉnh giao diện của hình dạng không?

Có, bạn có thể tùy chỉnh giao diện của hình dạng bằng cách điều chỉnh các thuộc tính của chúng như kích thước, vị trí, xoay và tô màu. Aspose.Words for Java cung cấp nhiều tùy chọn để tùy chỉnh hình dạng.

### Aspose.Words cho Java có tương thích với SmartArt không?

Có, Aspose.Words for Java hỗ trợ các hình dạng SmartArt, cho phép bạn làm việc với các sơ đồ và đồ họa phức tạp trong tài liệu của mình.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}