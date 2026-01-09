---
date: 2026-01-09
description: Tìm hiểu cách tạo danh sách đa cấp, áp dụng kiểu đoạn văn, thiết lập
  căn chỉnh đoạn văn và tạo tài liệu Word bằng Aspose.Words cho Java. Hướng dẫn này
  bao gồm các kỹ thuật định dạng cho tài liệu chuyên nghiệp.
linktitle: Formatting Documents
second_title: Aspose.Words Java Document Processing API
title: Cách tạo danh sách đa cấp và định dạng tài liệu trong Aspose.Words cho Java
url: /vi/java/document-manipulation/formatting-documents/
weight: 29
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng tài liệu trong Aspose.Words cho Java

## Giới thiệu về Định dạng tài liệu trong Aspose.Words cho Java

Trong thế giới xử lý tài liệu Java, Aspose.Words cho Java nổi bật như một công cụ mạnh mẽ và đa năng. Dù bạn đang tạo báo cáo, lập hoá đơn, hay xây dựng bố cục phức tạp, bạn thường cần **create multilevel list** và áp dụng kiểu đoạn văn tinh vi. Trong hướng dẫn toàn diện này, chúng ta sẽ đi qua cách định dạng tài liệu, tạo một tài liệu Word từ đầu, và tinh chỉnh căn chỉnh đoạn, thụt lề trái và các chi tiết kiểu chữ khác. Hãy bắt đầu từng bước.

## Câu trả lời nhanh
- **How do I create a multilevel list?** Sử dụng `DocumentBuilder.getListFormat().applyNumberDefault()` và thêm các mục danh sách theo thứ tự.  
- **Can I set paragraph alignment?** Có, gọi `ParagraphFormat.setAlignment(ParagraphAlignment.CENTER)` hoặc bất kỳ căn chỉnh nào khác.  
- **What method adds left indent?** Sử dụng `ParagraphFormat.setLeftIndent(double)` để xác định lề trái.  
- **How do I generate a Word document programmatically?** Tạo một đối tượng `Document`, thêm nội dung bằng `DocumentBuilder`, sau đó gọi `save("MyDoc.docx")`.  
- **Is there a way to apply a custom paragraph style?** Đặt định danh kiểu bằng `ParagraphFormat.setStyleIdentifier(StyleIdentifier.TITLE)`.

## Cài đặt môi trường của bạn

Trước khi chúng ta đi sâu vào các chi tiết phức tạp của việc định dạng tài liệu, việc thiết lập môi trường là rất quan trọng. Đảm bảo bạn đã cài đặt và cấu hình Aspose.Words cho Java đúng cách trong dự án của mình. Bạn có thể tải xuống từ [here](https://releases.aspose.com/words/java/).

## Tạo tài liệu đơn giản

Hãy bắt đầu bằng cách **generate word document** bằng Aspose.Words cho Java. Đoạn mã Java sau minh họa cách tạo một tài liệu và thêm một số văn bản vào đó:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello, Aspose.Words for Java!");
doc.save("MyDocument.docx");
```

## Điều chỉnh khoảng cách giữa văn bản Asian và Latin

Aspose.Words cho Java cung cấp các tính năng mạnh mẽ để xử lý khoảng cách văn bản. Bạn có thể tự động điều chỉnh khoảng cách giữa văn bản Asian và Latin như dưới đây:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAddSpaceBetweenFarEastAndAlpha(true);
paragraphFormat.setAddSpaceBetweenFarEastAndDigit(true);
builder.writeln("Automatically adjust space between Asian and Latin text");
builder.writeln("Automatically adjust space between Asian text and numbers");
doc.save("SpaceBetweenAsianAndLatinText.docx");
```

## Làm việc với kiểu chữ Asian

Để kiểm soát các cài đặt kiểu chữ Asian, hãy xem đoạn mã sau:

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getParagraphs().get(0).getParagraphFormat();
format.setFarEastLineBreakControl(false);
format.setWordWrap(true);
format.setHangingPunctuation(false);
doc.save("AsianTypographyLineBreakGroup.docx");
```

## Định dạng đoạn văn

Aspose.Words cho Java cho phép bạn **set paragraph alignment**, **set left indent**, và định dạng các đoạn một cách dễ dàng. Xem ví dụ sau:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAlignment(ParagraphAlignment.CENTER);
paragraphFormat.setLeftIndent(50.0);
paragraphFormat.setRightIndent(50.0);
paragraphFormat.setSpaceAfter(25.0);
builder.writeln("I'm a very nice formatted paragraph. I'm intended to demonstrate how the left and right indents affect word wrapping.");
builder.writeln("I'm another nice formatted paragraph. I'm intended to demonstrate how the space after paragraph looks like.");
doc.save("ParagraphFormatting.docx");
```

## Định dạng danh sách đa cấp

Tạo **multilevel list** là một yêu cầu phổ biến trong việc định dạng tài liệu. Aspose.Words cho Java đơn giản hoá công việc này:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().applyNumberDefault();
builder.writeln("Item 1");
// Add more items here...
doc.save("MultilevelListFormatting.docx");
```

## Áp dụng kiểu đoạn văn

Aspose.Words cho Java cho phép bạn **apply paragraph style** một cách dễ dàng:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.TITLE);
builder.write("Hello, Styled Paragraph!");
doc.save("ApplyParagraphStyle.docx");
```

## Thêm viền và tô bóng cho đoạn văn

Nâng cao tính thẩm mỹ của tài liệu bằng cách thêm viền và tô bóng:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
BorderCollection borders = builder.getParagraphFormat().getBorders();
// Customize borders here...
Shading shading = builder.getParagraphFormat().getShading();
// Customize shading here...
builder.write("I'm a formatted paragraph with double border and nice shading.");
doc.save("ApplyBordersAndShadingToParagraph.docx");
```

## Thay đổi khoảng cách và thụt lề đoạn văn Asian

Tinh chỉnh khoảng cách và thụt lề đoạn văn cho văn bản Asian:

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat();
format.setCharacterUnitLeftIndent(10.0);
format.setCharacterUnitRightIndent(10.0);
format.setCharacterUnitFirstLineIndent(20.0);
format.setLineUnitBefore(5.0);
format.setLineUnitAfter(10.0);
doc.save("ChangeAsianParagraphSpacingAndIndents.docx");
```

## Căn lưới (Snapping to the Grid)

Tối ưu bố cục khi làm việc với ký tự Asian bằng cách căn lưới:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Paragraph par = doc.getFirstSection().getBody().getFirstParagraph();
par.getParagraphFormat().setSnapToGrid(true);
builder.writeln("Lorem ipsum dolor sit amet, consectetur adipiscing elit...");
par.getRuns().get(0).getFont().setSnapToGrid(true);
doc.save("SnapToGrid.docx");
```

## Phát hiện bộ tách kiểu đoạn văn

Nếu bạn cần tìm bộ tách kiểu trong tài liệu, bạn có thể sử dụng đoạn mã sau:

```java
Document doc = new Document("Document.docx");
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (paragraph.getBreakIsStyleSeparator())
    {
        System.out.println("Separator Found!");
    }
}
```

## Kết luận

Trong bài viết này, chúng ta đã khám phá nhiều khía cạnh của việc định dạng tài liệu trong Aspose.Words cho Java, bao gồm cách **create multilevel list**, **apply paragraph style**, **set paragraph alignment**, và **set left indent**. Với những kiến thức này, bạn có thể tạo ra các tài liệu Word chuyên nghiệp cho các ứng dụng Java của mình. Hãy nhớ tham khảo [Aspose.Words for Java documentation](https://reference.aspose.com/words/java/) để có hướng dẫn chi tiết hơn.

## Câu hỏi thường gặp

**Q: Làm sao tôi có thể tải xuống Aspose.Words cho Java?**  
A: Bạn có thể tải xuống Aspose.Words cho Java từ [this link](https://releases.aspose.com/words/java/).

**Q: Aspose.Words cho Java có phù hợp để tạo tài liệu phức tạp không?**  
A: Chắc chắn! Aspose.Words cho Java cung cấp khả năng rộng rãi để tạo và định dạng tài liệu phức tạp một cách dễ dàng.

**Q: Tôi có thể áp dụng kiểu tùy chỉnh cho các đoạn văn bằng Aspose.Words cho Java không?**  
A: Có, bạn có thể áp dụng các kiểu tùy chỉnh cho các đoạn văn, mang lại cho tài liệu của bạn một giao diện độc đáo.

**Q: Aspose.Words cho Java có hỗ trợ danh sách đa cấp không?**  
A: Có, Aspose.Words cho Java cung cấp hỗ trợ tuyệt vời cho việc tạo và định dạng danh sách đa cấp.

**Q: Làm sao tôi có thể tối ưu khoảng cách đoạn văn cho văn bản Asian?**  
A: Bạn có thể tinh chỉnh khoảng cách đoạn văn cho văn bản Asian bằng cách điều chỉnh các cài đặt liên quan trong Aspose.Words cho Java.

**Q: Cách dễ nhất để tạo tài liệu Word một cách lập trình là gì?**  
A: Tạo một đối tượng `Document`, sử dụng `DocumentBuilder` để thêm nội dung, và gọi `save("YourFile.docx")`.

**Q: Có mẹo nào về hiệu năng cho tài liệu lớn không?**  
A: Sử dụng API streaming và giải phóng các đối tượng không dùng ngay để giữ mức sử dụng bộ nhớ thấp.

**Cập nhật lần cuối:** 2026-01-09  
**Kiểm tra với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}