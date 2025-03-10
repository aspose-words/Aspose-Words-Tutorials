---
title: Sử dụng Header và Footer trong Aspose.Words cho Java
linktitle: Sử dụng Header và Footer
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu từng bước cách sử dụng header và footer trong Aspose.Words cho Java. Tạo tài liệu chuyên nghiệp một cách dễ dàng.
weight: 16
url: /vi/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Header và Footer trong Aspose.Words cho Java


Trong hướng dẫn toàn diện này, chúng tôi sẽ hướng dẫn bạn quy trình làm việc với tiêu đề và chân trang trong Aspose.Words for Java. Tiêu đề và chân trang là những thành phần thiết yếu trong định dạng tài liệu và Aspose.Words cung cấp các công cụ mạnh mẽ để tạo và tùy chỉnh chúng theo nhu cầu của bạn.

Bây giờ, chúng ta hãy đi sâu vào từng bước một cách chi tiết.

## 1. Giới thiệu về Aspose.Words

Aspose.Words là một Java API mạnh mẽ cho phép bạn tạo, thao tác và hiển thị các tài liệu Word theo chương trình. Nó cung cấp các tính năng mở rộng để định dạng tài liệu, bao gồm cả tiêu đề và chân trang.

## 2. Thiết lập môi trường Java của bạn

 Trước khi bắt đầu sử dụng Aspose.Words, hãy đảm bảo bạn đã thiết lập đúng môi trường phát triển Java. Bạn có thể tìm thấy hướng dẫn thiết lập cần thiết trên trang tài liệu Aspose.Words:[Tài liệu Java Aspose.Words](https://reference.aspose.com/words/java/).

## 3. Tạo một tài liệu mới

Để làm việc với header và footer, bạn cần tạo một tài liệu mới bằng Aspose.Words. Mã sau đây minh họa cách thực hiện việc này:

```java
// Mã Java để tạo một tài liệu mới
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Hiểu về thiết lập trang

 Thiết lập trang rất quan trọng để kiểm soát bố cục tài liệu của bạn. Bạn có thể chỉ định nhiều thuộc tính liên quan đến tiêu đề và chân trang bằng cách sử dụng`PageSetup` lớp. Ví dụ:

```java
// Thiết lập thuộc tính trang
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Tiêu đề/chân trang đầu tiên khác nhau

Aspose.Words cho phép bạn có nhiều tiêu đề và chân trang khác nhau cho trang đầu tiên của tài liệu. Sử dụng`pageSetup.setDifferentFirstPageHeaderFooter(true);` để kích hoạt tính năng này.

## 6. Làm việc với Tiêu đề

### 6.1. Thêm văn bản vào tiêu đề

 Bạn có thể thêm văn bản vào tiêu đề bằng cách sử dụng`DocumentBuilder`. Đây là một ví dụ:

```java
// Thêm văn bản vào tiêu đề trang đầu tiên
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Chèn hình ảnh vào tiêu đề

 Để chèn hình ảnh vào tiêu đề, bạn có thể sử dụng`insertImage` phương pháp. Đây là một ví dụ:

```java
// Chèn hình ảnh vào tiêu đề
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Tùy chỉnh kiểu tiêu đề

Bạn có thể tùy chỉnh kiểu tiêu đề bằng cách thiết lập nhiều thuộc tính khác nhau như phông chữ, căn chỉnh, v.v., như được hiển thị trong các ví dụ ở trên.

## 7. Làm việc với Footer

### 7.1. Thêm văn bản vào chân trang

 Tương tự như tiêu đề, bạn có thể thêm văn bản vào chân trang bằng cách sử dụng`DocumentBuilder`. Đây là một ví dụ:

```java
// Thêm văn bản vào chân trang chính
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Chèn văn bản và các trường khi cần thiết
```

### 7.2. Chèn hình ảnh vào chân trang

 Để chèn hình ảnh vào chân trang, hãy sử dụng`insertImage` phương pháp giống như trong tiêu đề.

### 7.3. Tùy chỉnh Kiểu Chân trang

 Tùy chỉnh kiểu chân trang bằng cách sử dụng`DocumentBuilder`tương tự như việc tùy chỉnh tiêu đề.

## 8. Đánh số trang

 Bạn có thể bao gồm số trang trong phần đầu trang và chân trang của mình bằng cách sử dụng các trường như`PAGE` Và`NUMPAGES`. Các trường này sẽ tự động cập nhật khi bạn thêm hoặc xóa trang.

## 9. Thông tin bản quyền ở phần chân trang

Để thêm thông tin bản quyền vào chân trang tài liệu, bạn có thể sử dụng bảng có hai ô, căn chỉnh một ô sang trái và một ô sang phải, như minh họa trong đoạn mã.

## 10. Làm việc với nhiều phần

Aspose.Words cho phép bạn làm việc với nhiều phần trong một tài liệu. Bạn có thể thiết lập các thiết lập trang và tiêu đề/chân trang khác nhau cho mỗi phần.

## 11. Định hướng phong cảnh

Bạn có thể thay đổi hướng của các phần cụ thể sang chế độ ngang nếu cần.

## 12. Sao chép Header/Footer từ các phần trước

Sao chép phần đầu trang và phần chân trang từ các phần trước có thể tiết kiệm thời gian khi tạo các tài liệu phức tạp.

## 13. Lưu tài liệu của bạn

Sau khi tạo và tùy chỉnh tài liệu của bạn, đừng quên lưu nó bằng cách sử dụng`doc.save()` phương pháp.

## Mã nguồn đầy đủ
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Chỉ định xem chúng ta có muốn phần đầu trang/chân trang của trang đầu tiên khác với các trang khác không.
        // Bạn cũng có thể sử dụng thuộc tính PageSetup.OddAndEvenPagesHeaderFooter để chỉ định
        // các tiêu đề/chân trang khác nhau cho các trang lẻ và trang chẵn.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Chèn hình ảnh đã định vị vào góc trên cùng/bên trái của tiêu đề.
        // Khoảng cách từ cạnh trên/trái của trang được đặt thành 10 điểm.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Chúng tôi sử dụng bảng có hai ô để tạo một phần văn bản trên dòng (có đánh số trang).
        // Căn trái và phần văn bản còn lại (có bản quyền) căn phải.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Nó sử dụng các trường PAGE và NUMPAGES để tự động tính toán số trang hiện tại và nhiều trang.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Ngắt trang để tạo trang thứ hai mà phần đầu trang/chân trang chính sẽ hiển thị.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Phần này không cần tiêu đề/chân trang đầu tiên khác, chúng ta chỉ cần một trang tiêu đề trong tài liệu,
        //và phần đầu trang/chân trang cho trang này đã được xác định ở phần trước.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Phần này hiển thị tiêu đề/chân trang từ phần trước
        // theo mặc định gọi currentSection.HeadersFooters.LinkToPrevious(false) để hủy chiều rộng trang này
        // khác nhau đối với phần mới và do đó chúng ta cần thiết lập độ rộng ô khác nhau cho bảng chân trang.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Nếu chúng ta muốn sử dụng bộ tiêu đề/chân trang đã có sẵn cho phần này.
        // Nhưng với một số sửa đổi nhỏ, thì có thể sao chép tiêu đề/chân trang là hợp lý
        // từ phần trước và áp dụng những sửa đổi cần thiết vào nơi chúng ta muốn.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Mã nguồn của phương thức copyHeadersFootersFromPreviousSection
```java
    /// <tóm tắt>
    /// Sao chép và tạo bản sao phần đầu trang/chân trang từ phần trước vào phần đã chỉ định.
    /// </tóm tắt>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã đề cập đến những điều cơ bản về cách làm việc với tiêu đề và chân trang trong Aspose.Words for Java. Bạn đã học cách tạo, tùy chỉnh và định dạng tiêu đề và chân trang, cũng như các kỹ thuật định dạng tài liệu thiết yếu khác.

 Để biết thêm chi tiết và các tính năng nâng cao, hãy tham khảo[Tài liệu Java Aspose.Words](https://reference.aspose.com/words/java/).

## Câu hỏi thường gặp

### 1. Làm thế nào để thêm số trang vào chân trang tài liệu của tôi?
 Bạn có thể thêm số trang bằng cách chèn`PAGE` trường vào chân trang bằng Aspose.Words.

### 2. Aspose.Words có tương thích với môi trường phát triển Java không?
Có, Aspose.Words cung cấp hỗ trợ cho phát triển Java. Đảm bảo bạn đã thiết lập cần thiết.

### 3. Tôi có thể tùy chỉnh phông chữ và kiểu dáng của đầu trang và chân trang không?
Hoàn toàn có thể tùy chỉnh phông chữ, căn chỉnh và các kiểu khác để làm cho phần đầu trang và chân trang của bạn hấp dẫn về mặt thị giác.

### 4. Có thể sử dụng các tiêu đề khác nhau cho các trang chẵn và trang lẻ không?
 Có, bạn có thể sử dụng`PageSetup.OddAndEvenPagesHeaderFooter` để chỉ định các tiêu đề khác nhau cho các trang lẻ và trang chẵn.

### 5. Làm thế nào để bắt đầu sử dụng Aspose.Words cho Java?
 Để bắt đầu, hãy truy cập[Tài liệu Java Aspose.Words](https://reference.aspose.com/words/java/) để có hướng dẫn toàn diện về cách sử dụng API.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
