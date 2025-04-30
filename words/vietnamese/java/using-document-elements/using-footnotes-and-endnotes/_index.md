---
"description": "Học cách sử dụng chú thích cuối trang và chú thích cuối văn bản hiệu quả trong Aspose.Words for Java. Nâng cao kỹ năng định dạng tài liệu của bạn ngay hôm nay!"
"linktitle": "Sử dụng chú thích cuối trang và chú thích cuối trang"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng Footnotes và Endnotes trong Aspose.Words cho Java"
"url": "/vi/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Footnotes và Endnotes trong Aspose.Words cho Java


Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình sử dụng chú thích cuối trang và chú thích cuối văn bản trong Aspose.Words for Java. Chú thích cuối trang và chú thích cuối văn bản là những thành phần thiết yếu trong định dạng tài liệu, thường được sử dụng để trích dẫn, tham khảo và thông tin bổ sung. Aspose.Words for Java cung cấp chức năng mạnh mẽ để làm việc với chú thích cuối trang và chú thích cuối văn bản một cách liền mạch.

## 1. Giới thiệu về Chú thích cuối trang và Chú thích cuối văn bản

Chú thích cuối trang và chú thích cuối văn bản là các chú thích cung cấp thông tin bổ sung hoặc trích dẫn trong một tài liệu. Chú thích cuối trang xuất hiện ở cuối trang, trong khi chú thích cuối văn bản được thu thập ở cuối một phần hoặc tài liệu. Chúng thường được sử dụng trong các bài báo học thuật, báo cáo và tài liệu pháp lý để tham khảo nguồn hoặc làm rõ nội dung.

## 2. Thiết lập môi trường của bạn

Trước khi chúng ta bắt đầu làm việc với chú thích cuối trang và chú thích cuối văn bản, bạn cần thiết lập môi trường phát triển của mình. Đảm bảo bạn đã cài đặt và cấu hình Aspose.Words for Java API trong dự án của mình.

## 3. Thêm chú thích vào tài liệu của bạn

Để thêm chú thích vào tài liệu, hãy làm theo các bước sau:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // Chỉ định số cột được định dạng cho vùng chú thích.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. Sửa đổi tùy chọn chú thích

Bạn có thể sửa đổi tùy chọn chú thích để tùy chỉnh giao diện và hành vi của chúng. Sau đây là cách thực hiện:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. Thêm chú thích cuối trang vào tài liệu của bạn

Việc thêm chú thích cuối trang vào tài liệu của bạn rất đơn giản. Sau đây là một ví dụ:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. Tùy chỉnh cài đặt Endnote

Bạn có thể tùy chỉnh thêm cài đặt chú thích cuối trang để đáp ứng yêu cầu của tài liệu.

## Mã nguồn đầy đủ
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // Chỉ định số cột được định dạng cho vùng chú thích.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. Kết luận

Trong hướng dẫn này, chúng tôi đã khám phá cách làm việc với chú thích cuối trang và chú thích cuối văn bản trong Aspose.Words for Java. Các tính năng này vô cùng hữu ích để tạo ra các tài liệu có cấu trúc tốt với trích dẫn và tham chiếu phù hợp.

Bây giờ bạn đã biết cách sử dụng chú thích cuối trang và chú thích cuối văn bản, bạn có thể cải thiện định dạng tài liệu và làm cho nội dung trở nên chuyên nghiệp hơn.

### Những câu hỏi thường gặp

### 1. Sự khác biệt giữa chú thích cuối trang và chú thích cuối văn bản là gì?
Chú thích xuất hiện ở cuối trang, trong khi chú thích cuối trang được thu thập ở cuối phần hoặc cuối tài liệu.

### 2. Làm thế nào để thay đổi vị trí chú thích hoặc chú thích cuối trang?
Bạn có thể sử dụng `setPosition` phương pháp thay đổi vị trí chú thích hoặc chú thích cuối trang.

### 3. Tôi có thể tùy chỉnh định dạng chú thích cuối trang và chú thích cuối văn bản không?
Có, bạn có thể tùy chỉnh định dạng chú thích cuối trang và chú thích cuối văn bản bằng Aspose.Words cho Java.

### 4. Chú thích cuối trang và chú thích cuối trang có quan trọng trong việc định dạng tài liệu không?
Có, chú thích cuối trang và chú thích cuối trang rất cần thiết để cung cấp tài liệu tham khảo và thông tin bổ sung trong tài liệu.

Hãy thoải mái khám phá thêm nhiều tính năng của Aspose.Words for Java và nâng cao khả năng tạo tài liệu của bạn. Chúc bạn viết mã vui vẻ!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}