---
"description": "Làm chủ việc tạo tài liệu với Aspose.Words cho Java. Hướng dẫn từng bước để thêm văn bản, bảng, hình ảnh và nhiều nội dung khác. Tạo tài liệu Word tuyệt đẹp một cách dễ dàng."
"linktitle": "Thêm Nội dung bằng DocumentBuilder"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Thêm Nội dung bằng DocumentBuilder trong Aspose.Words cho Java"
"url": "/vi/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Nội dung bằng DocumentBuilder trong Aspose.Words cho Java


## Giới thiệu về Thêm Nội dung bằng DocumentBuilder trong Aspose.Words cho Java

Trong hướng dẫn từng bước này, chúng ta sẽ khám phá cách sử dụng DocumentBuilder của Aspose.Words for Java để thêm nhiều loại nội dung khác nhau vào tài liệu Word. Chúng ta sẽ đề cập đến việc chèn văn bản, bảng, quy tắc ngang, trường biểu mẫu, HTML, siêu liên kết, mục lục, hình ảnh nội tuyến và nổi, đoạn văn, v.v. Hãy bắt đầu nào!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã thiết lập thư viện Aspose.Words for Java trong dự án của mình. Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/java/).

## Thêm văn bản

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một đoạn văn bản đơn giản
builder.write("This is a simple text paragraph.");

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm bảng

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bắt đầu một bảng
Table table = builder.startTable();

// Chèn ô và nội dung
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Kết thúc bảng
builder.endTable();

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm Quy tắc ngang

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một quy tắc ngang
builder.insertHorizontalRule();

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm trường biểu mẫu

### Trường biểu mẫu nhập văn bản

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một trường biểu mẫu nhập văn bản
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

### Trường biểu mẫu hộp kiểm tra

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một trường biểu mẫu hộp kiểm
builder.insertCheckBox("CheckBox", true, true, 0);

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

### Trường biểu mẫu hộp kết hợp

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Xác định các mục cho hộp kết hợp
String[] items = { "Option 1", "Option 2", "Option 3" };

// Chèn một trường biểu mẫu hộp kết hợp
builder.insertComboBox("DropDown", items, 0);

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn nội dung HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm siêu liên kết

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một siêu liên kết
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", sai);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm Mục lục

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn mục lục
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Thêm nội dung tài liệu
// ...

// Cập nhật mục lục
doc.updateFields();

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm hình ảnh

### Hình ảnh nội tuyến

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một hình ảnh nội tuyến
builder.insertImage("path/to/your/image.png");

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

### Hình ảnh nổi

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một hình ảnh nổi
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Thêm đoạn văn

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Thiết lập định dạng đoạn văn
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

// Chèn một đoạn văn
builder.writeln("This is a formatted paragraph.");

// Lưu tài liệu
doc.save("path/to/your/document.docx");
```

## Bước 10: Di chuyển con trỏ

Bạn có thể kiểm soát vị trí con trỏ trong tài liệu bằng nhiều phương pháp khác nhau như `moveToParagraph`, `moveToCell`và nhiều hơn nữa. Sau đây là một ví dụ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Di chuyển con trỏ đến một đoạn văn cụ thể
builder.moveToParagraph(2, 0);

// Thêm nội dung vào vị trí con trỏ mới
builder.writeln("This is the 3rd paragraph.");
```

Đây là một số thao tác phổ biến mà bạn có thể thực hiện bằng cách sử dụng DocumentBuilder của Aspose.Words cho Java. Khám phá tài liệu của thư viện để biết thêm các tính năng nâng cao và tùy chọn tùy chỉnh. Chúc bạn tạo tài liệu vui vẻ!


## Phần kết luận

Trong hướng dẫn toàn diện này, chúng tôi đã khám phá khả năng của DocumentBuilder của Aspose.Words for Java để thêm nhiều loại nội dung khác nhau vào tài liệu Word. Chúng tôi đã đề cập đến văn bản, bảng, quy tắc ngang, trường biểu mẫu, HTML, siêu liên kết, mục lục, hình ảnh, đoạn văn và chuyển động con trỏ.

## Câu hỏi thường gặp

### H: Aspose.Words dành cho Java là gì?

A: Aspose.Words for Java là một thư viện Java cho phép các nhà phát triển tạo, chỉnh sửa và thao tác các tài liệu Microsoft Word theo chương trình. Nó cung cấp nhiều tính năng để tạo tài liệu, định dạng và chèn nội dung.

### H: Làm thế nào để thêm mục lục vào tài liệu của tôi?

A: Để thêm mục lục, hãy sử dụng `DocumentBuilder` để chèn trường mục lục vào tài liệu của bạn. Đảm bảo cập nhật các trường trong tài liệu sau khi thêm nội dung để điền vào mục lục. Sau đây là một ví dụ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một trường mục lục
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Thêm nội dung tài liệu
// ...

// Cập nhật mục lục
doc.updateFields();
```

### H: Làm thế nào để chèn hình ảnh vào tài liệu bằng Aspose.Words cho Java?

A: Bạn có thể chèn hình ảnh, cả nội tuyến và nổi, bằng cách sử dụng `DocumentBuilder`. Sau đây là ví dụ của cả hai:

#### Hình ảnh nội tuyến:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một hình ảnh nội tuyến
builder.insertImage("path/to/your/image.png");
```

#### Hình ảnh nổi:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một hình ảnh nổi
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### H: Tôi có thể định dạng văn bản và đoạn văn khi thêm nội dung không?

A: Có, bạn có thể định dạng văn bản và đoạn văn bằng cách sử dụng `DocumentBuilder`. Bạn có thể thiết lập thuộc tính phông chữ, căn chỉnh đoạn văn, thụt lề và nhiều hơn nữa. Sau đây là một ví dụ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Thiết lập định dạng phông chữ và đoạn văn
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

// Chèn một đoạn văn đã định dạng
builder.writeln("This is a formatted paragraph.");
```

### H: Làm thế nào để di chuyển con trỏ đến một vị trí cụ thể trong tài liệu?

A: Bạn có thể kiểm soát vị trí con trỏ bằng các phương pháp như `moveToParagraph`, `moveToCell`và nhiều hơn nữa. Sau đây là một ví dụ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Di chuyển con trỏ đến một đoạn văn cụ thể
builder.moveToParagraph(2, 0);

// Thêm nội dung vào vị trí con trỏ mới
builder.writeln("This is the 3rd paragraph.");
```

Đây là một số câu hỏi và câu trả lời phổ biến để giúp bạn bắt đầu với DocumentBuilder của Aspose.Words for Java. Nếu bạn có thêm câu hỏi hoặc cần hỗ trợ thêm, hãy tham khảo [tài liệu của thư viện](https://reference.aspose.com/words/java/) hoặc tìm kiếm sự trợ giúp từ cộng đồng Aspose.Words và các nguồn hỗ trợ.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}