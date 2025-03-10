---
title: Kết xuất hình dạng trong Aspose.Words cho Java
linktitle: Kết xuất hình dạng
second_title: API xử lý tài liệu Java Aspose.Words
description: Học cách kết xuất hình dạng trong Aspose.Words cho Java với hướng dẫn từng bước này. Tạo hình ảnh EMF theo chương trình.
weight: 10
url: /vi/java/rendering-documents/rendering-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kết xuất hình dạng trong Aspose.Words cho Java


Trong thế giới xử lý và thao tác tài liệu, Aspose.Words for Java nổi bật như một công cụ mạnh mẽ. Nó trao quyền cho các nhà phát triển tạo, chỉnh sửa và chuyển đổi tài liệu một cách dễ dàng. Một trong những tính năng chính của nó là khả năng kết xuất hình dạng, có thể cực kỳ hữu ích khi xử lý các tài liệu phức tạp. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước trong quy trình kết xuất hình dạng trong Aspose.Words for Java.

## 1. Giới thiệu về Aspose.Words cho Java

Aspose.Words for Java là một Java API cho phép các nhà phát triển làm việc với các tài liệu Word theo chương trình. Nó cung cấp nhiều tính năng để tạo, chỉnh sửa và chuyển đổi các tài liệu Word.

## 2. Thiết lập môi trường phát triển của bạn

Trước khi đi sâu vào mã, bạn cần thiết lập môi trường phát triển của mình. Đảm bảo bạn đã cài đặt thư viện Aspose.Words for Java và sẵn sàng sử dụng trong dự án của mình.

## 3. Tải một tài liệu

Để bắt đầu, bạn sẽ cần một tài liệu Word để làm việc. Đảm bảo rằng bạn có một tài liệu trong thư mục được chỉ định.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 4. Lấy lại hình dạng mục tiêu

Trong bước này, chúng ta sẽ lấy hình dạng mục tiêu từ tài liệu. Hình dạng này sẽ là hình dạng chúng ta muốn hiển thị.

```java
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
ShapeRenderer render = shape.getShapeRenderer();
```

## 5. Kết xuất hình dạng dưới dạng hình ảnh EMF

 Bây giờ đến phần thú vị - kết xuất hình dạng dưới dạng hình ảnh EMF. Chúng ta sẽ sử dụng`ImageSaveOptions` lớp để chỉ định định dạng đầu ra và tùy chỉnh cách kết xuất.

```java
ImageSaveOptions imageOptions = new ImageSaveOptions(SaveFormat.EMF);
{
    imageOptions.setScale(1.5f);
}
render.save(outPath + "RenderShape.RenderShapeAsEmf.emf", imageOptions);
```

## 6. Tùy chỉnh kết xuất

Bạn có thể tùy chỉnh kết xuất thêm dựa trên yêu cầu cụ thể của mình. Bạn có thể điều chỉnh các thông số như tỷ lệ, chất lượng, v.v.

## 7. Lưu hình ảnh đã kết xuất

Sau khi kết xuất, bước tiếp theo là lưu hình ảnh đã kết xuất vào thư mục đầu ra mong muốn.

## Mã nguồn đầy đủ
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Lấy hình dạng mục tiêu từ tài liệu.
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
ShapeRenderer render = shape.getShapeRenderer();
ImageSaveOptions imageOptions = new ImageSaveOptions(SaveFormat.EMF);
{
	imageOptions.setScale(1.5f);
}
render.save(outPath + "RenderShape.RenderShapeAsEmf.emf", imageOptions);
    
```

## 8. Kết luận

Xin chúc mừng! Bạn đã học thành công cách kết xuất hình dạng trong Aspose.Words cho Java. Khả năng này mở ra một thế giới khả năng khi làm việc với các tài liệu Word theo chương trình.

## 9. Câu hỏi thường gặp

### Câu hỏi 1: Tôi có thể hiển thị nhiều hình dạng trong một tài liệu không?

Có, bạn có thể kết xuất nhiều hình dạng trong một tài liệu. Chỉ cần lặp lại quy trình cho mỗi hình dạng bạn muốn kết xuất.

### Câu hỏi 2: Aspose.Words for Java có tương thích với các định dạng tài liệu khác nhau không?

Có, Aspose.Words for Java hỗ trợ nhiều định dạng tài liệu, bao gồm DOCX, PDF, HTML, v.v.

### Câu hỏi 3: Có tùy chọn cấp phép nào cho Aspose.Words dành cho Java không?

Có, bạn có thể khám phá các tùy chọn cấp phép và mua Aspose.Words cho Java trên[Trang web Aspose](https://purchase.aspose.com/buy).

### Câu hỏi 4: Tôi có thể dùng thử Aspose.Words cho Java trước khi mua không?

 Chắc chắn rồi! Bạn có thể truy cập bản dùng thử miễn phí của Aspose.Words cho Java trên[Aspose.Phát hành](https://releases.aspose.com/).

### Câu hỏi 5: Tôi có thể tìm kiếm sự hỗ trợ hoặc đặt câu hỏi về Aspose.Words cho Java ở đâu?

 Đối với bất kỳ câu hỏi hoặc hỗ trợ nào, hãy truy cập[Diễn đàn Aspose.Words cho Java](https://forum.aspose.com/).

Bây giờ bạn đã thành thạo việc kết xuất hình dạng bằng Aspose.Words for Java, bạn đã sẵn sàng khai thác toàn bộ tiềm năng của API đa năng này trong các dự án xử lý tài liệu của mình. Chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
