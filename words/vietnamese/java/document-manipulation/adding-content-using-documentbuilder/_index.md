---
date: 2026-01-01
description: Học cách tạo các trường biểu mẫu và thêm văn bản, bảng, hình ảnh, siêu
  liên kết và nhiều hơn nữa bằng Aspose.Words for Java DocumentBuilder. Hướng dẫn
  từng bước dành cho các nhà phát triển.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words
  cho Java
url: /vi/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Nội Dung bằng DocumentBuilder trong Aspose.Words cho Java

## Giới thiệu về việc Thêm Nội Dung bằng DocumentBuilder trong Aspose.Words cho Java

Trong hướng dẫn từng bước này, bạn sẽ **tạo các trường biểu mẫu** và thêm nhiều loại nội dung—văn bản, bảng, đường kẻ ngang, HTML, siêu liên kết, hình ảnh và hơn thế nữa—vào tài liệu Word bằng Aspose.Words cho Java. Dù bạn đang xây dựng báo cáo, mẫu hợp đồng hay biểu mẫu tương tác, lớp `DocumentBuilder` cung cấp cho bạn khả năng kiểm soát chi tiết từng thành phần. Hãy cùng khám phá!

## Câu trả lời nhanh
- **Làm thế nào để tạo các trường biểu mẫu?** Sử dụng `insertTextInput`, `insertCheckBox`, hoặc `insertComboBox` trên một `DocumentBuilder`.
- **Phương thức nào để thêm văn bản thuần?** Gọi `builder.write("Your text")` hoặc `builder.writeln("Your text")`.
- **Tôi có thể chèn đường kẻ ngang không?** Có—`builder.insertHorizontalRule()` sẽ thêm một đường ngăn cách.
- **Cách nhúng HTML?** Sử dụng `builder.insertHtml("<p>HTML content</p>")`.
- **Cách thêm hình ảnh nội dòng?** `builder.insertImage("path/to/image.png")` đặt hình ảnh vào trong luồng văn bản.

## DocumentBuilder là gì và tại sao nên sử dụng nó để tạo các trường biểu mẫu?

`DocumentBuilder` là API linh hoạt của Aspose.Words để xây dựng và chỉnh sửa tài liệu Word một cách lập trình. Nó trừu tượng hoá cấu trúc OpenXML cấp thấp, cho phép bạn tập trung vào *điều gì* bạn muốn thêm—như **các trường biểu mẫu**—thay vì *cách* XML trông như thế nào. Điều này làm cho nó trở thành lựa chọn lý tưởng cho việc tạo các biểu mẫu động, hợp đồng, hoặc bất kỳ tài liệu nào cần tương tác của người dùng.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã cài đặt thư viện Aspose.Words cho Java trong dự án của mình. Bạn có thể tải xuống từ [here](https://releases.aspose.com/words/java/).

## Thêm Văn Bản (cách thêm văn bản)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Bảng

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Đường Kẻ Ngang (thêm đường kẻ ngang)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Các Trường Biểu Mẫu (tạo các trường biểu mẫu)

### Trường Nhập Văn Bản

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Trường Hộp Kiểm

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Trường Hộp Kết Hợp

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm HTML (chèn HTML)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Siêu Liên Kết (cách thêm siêu liên kết)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Mục Lục

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Hình Ảnh

### Hình Ảnh Nội Dòng (chèn hình ảnh nội dòng)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Hình Ảnh Nổi

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Thêm Đoạn Văn

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Di chuyển con trỏ (Bước 10)

Bạn có thể điều khiển vị trí con trỏ trong tài liệu bằng các phương thức như `moveToParagraph`, `moveToCell`, v.v.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Đây là một số thao tác phổ biến bạn có thể thực hiện bằng `DocumentBuilder` của Aspose.Words cho Java. Khám phá tài liệu của thư viện để biết các tính năng nâng cao và tùy chỉnh. Chúc bạn tạo tài liệu vui vẻ!

## Kết Luận

Trong hướng dẫn toàn diện này, chúng tôi đã chỉ cách **tạo các trường biểu mẫu** và thêm nhiều loại nội dung—văn bản, bảng, đường kẻ ngang, HTML, siêu liên kết, mục lục, hình ảnh, đoạn văn được định dạng và điều hướng con trỏ—bằng `DocumentBuilder` của Aspose.Words cho Java. Giờ đây bạn đã có nền tảng vững chắc để tạo các tài liệu Word động, tương tác một cách lập trình.

## Câu Hỏi Thường Gặp

### Q: Aspose.Words cho Java là gì?

A: Aspose.Words cho Java là một thư viện Java cho phép các nhà phát triển tạo, sửa đổi và thao tác các tài liệu Microsoft Word một cách lập trình. Nó cung cấp một loạt các tính năng cho việc tạo tài liệu, định dạng và chèn nội dung.

### Q: Làm thế nào để thêm mục lục vào tài liệu của tôi?

A: Để thêm mục lục, sử dụng `DocumentBuilder` để chèn trường TOC và sau đó gọi `doc.updateFields()` sau khi đã thêm nội dung.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Làm thế nào để chèn hình ảnh vào tài liệu bằng Aspose.Words cho Java?

A: Bạn có thể chèn hình ảnh, cả nội dòng và nổi, bằng cách sử dụng `DocumentBuilder`.

#### Hình ảnh nội dòng:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Hình ảnh nổi:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Tôi có thể định dạng văn bản và đoạn văn khi thêm nội dung không?

A: Có, bạn có thể định dạng văn bản và đoạn văn bằng `DocumentBuilder`. Đặt các thuộc tính phông chữ, căn chỉnh đoạn, thụt lề và nhiều hơn nữa trước khi ghi nội dung.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Làm thế nào để di chuyển con trỏ đến vị trí cụ thể trong tài liệu?

A: Sử dụng các phương thức như `moveToParagraph`, `moveToCell`, v.v., để đặt vị trí con trỏ trước khi chèn nội dung mới.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Những câu trả lời này bao quát các kịch bản phổ biến nhất khi làm việc với `DocumentBuilder` của Aspose.Words cho Java. Để biết chi tiết hơn, hãy tham khảo [tài liệu của thư viện](https://reference.aspose.com/words/java/) hoặc tham gia cộng đồng Aspose.Words để được hỗ trợ.

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}