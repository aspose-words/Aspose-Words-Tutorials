---
"description": "Mở khóa sức mạnh của Aspose.Words cho Java. Học cách tải tài liệu văn bản, quản lý danh sách, xử lý khoảng trắng và kiểm soát hướng văn bản."
"linktitle": "Tải tập tin văn bản với"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Tải tệp văn bản bằng Aspose.Words cho Java"
"url": "/vi/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tải tệp văn bản bằng Aspose.Words cho Java


## Giới thiệu về Tải tệp văn bản bằng Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách tải tệp văn bản bằng Aspose.Words for Java và thao tác chúng dưới dạng tài liệu Word. Chúng ta sẽ đề cập đến nhiều khía cạnh khác nhau như phát hiện danh sách, xử lý khoảng trắng và kiểm soát hướng văn bản.

## Bước 1: Phát hiện danh sách

Để tải tài liệu văn bản và phát hiện danh sách, bạn có thể làm theo các bước sau:

```java
// Tạo một tài liệu dạng văn bản thuần túy dưới dạng chuỗi với các phần có thể được hiểu là danh sách.
// Khi tải, ba danh sách đầu tiên sẽ luôn được Aspose.Words phát hiện,
// và các đối tượng Danh sách sẽ được tạo cho chúng sau khi tải.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// Danh sách thứ tư, có khoảng trắng giữa số danh sách và nội dung mục danh sách,
// sẽ chỉ được phát hiện dưới dạng danh sách nếu "DetectNumberingWithWhitespaces" trong đối tượng LoadOptions được đặt thành true,
// để tránh các đoạn văn bắt đầu bằng số bị phát hiện nhầm là danh sách.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Tải tài liệu trong khi áp dụng LoadOptions làm tham số và xác minh kết quả.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Mã này trình bày cách tải một tài liệu văn bản với nhiều định dạng danh sách khác nhau và sử dụng `DetectNumberingWithWhitespaces` tùy chọn để phát hiện danh sách chính xác.

## Bước 2: Xử lý tùy chọn khoảng trắng

Để kiểm soát khoảng cách mở đầu và kết thúc khi tải tài liệu văn bản, bạn có thể sử dụng đoạn mã sau:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

Trong ví dụ này, chúng tôi tải một tài liệu văn bản và cắt bớt khoảng cách đầu và cuối bằng cách sử dụng `TxtLeadingSpacesOptions.TRIM` Và `TxtTrailingSpacesOptions.TRIM`.

## Bước 3: Kiểm soát hướng văn bản

Để chỉ định hướng văn bản khi tải tài liệu văn bản, bạn có thể sử dụng đoạn mã sau:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Mã này thiết lập hướng tài liệu để tự động phát hiện (`DocumentDirection.AUTO`) và tải một tài liệu văn bản bằng văn bản tiếng Do Thái. Bạn có thể điều chỉnh hướng tài liệu khi cần.

## Mã nguồn đầy đủ để tải tệp văn bản với Aspose.Words cho Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Tạo một tài liệu dạng văn bản thuần túy dưới dạng chuỗi với các phần có thể được hiểu là danh sách.
	// Khi tải, ba danh sách đầu tiên sẽ luôn được Aspose.Words phát hiện,
	// và các đối tượng Danh sách sẽ được tạo cho chúng sau khi tải.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Danh sách thứ tư, có khoảng trắng giữa số danh sách và nội dung mục danh sách,
	// sẽ chỉ được phát hiện dưới dạng danh sách nếu "DetectNumberingWithWhitespaces" trong đối tượng LoadOptions được đặt thành true,
	// để tránh các đoạn văn bắt đầu bằng số bị phát hiện nhầm là danh sách.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Tải tài liệu trong khi áp dụng LoadOptions làm tham số và xác minh kết quả.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã khám phá cách tải tệp văn bản bằng Aspose.Words cho Java, phát hiện danh sách, xử lý khoảng trắng và kiểm soát hướng văn bản. Các kỹ thuật này cho phép bạn thao tác hiệu quả các tài liệu văn bản trong các ứng dụng Java của mình.

## Câu hỏi thường gặp

### Aspose.Words dành cho Java là gì?

Aspose.Words for Java là một thư viện xử lý tài liệu mạnh mẽ cho phép các nhà phát triển tạo, thao tác và chuyển đổi các tài liệu Word theo chương trình trong các ứng dụng Java. Nó cung cấp nhiều tính năng để làm việc với văn bản, bảng, hình ảnh và các thành phần tài liệu khác.

### Tôi có thể bắt đầu sử dụng Aspose.Words cho Java như thế nào?

Để bắt đầu sử dụng Aspose.Words for Java, hãy làm theo các bước sau:
1. Tải xuống và cài đặt thư viện Aspose.Words cho Java.
2. Tham khảo tài liệu tại [Tài liệu tham khảo API Aspose.Words cho Java](https://reference.aspose.com/words/java/) để biết thông tin chi tiết và ví dụ.
3. Khám phá mã mẫu và hướng dẫn để tìm hiểu cách sử dụng thư viện hiệu quả.

### Làm thế nào để tải tài liệu văn bản bằng Aspose.Words cho Java?

Để tải một tài liệu văn bản bằng Aspose.Words cho Java, bạn có thể sử dụng `TxtLoadOptions` lớp và `Document` lớp. Đảm bảo rằng bạn chỉ định các tùy chọn thích hợp để xử lý khoảng trắng và hướng văn bản khi cần. Tham khảo hướng dẫn từng bước trong bài viết này để biết ví dụ chi tiết.

### Tôi có thể chuyển đổi một tài liệu văn bản đã tải sang các định dạng khác không?

Có, Aspose.Words for Java cho phép bạn chuyển đổi tài liệu văn bản đã tải sang nhiều định dạng khác nhau, bao gồm DOCX, PDF, v.v. Bạn có thể sử dụng `Document` lớp để thực hiện chuyển đổi. Kiểm tra tài liệu để biết các ví dụ chuyển đổi cụ thể.

### Tôi phải xử lý khoảng trắng trong tài liệu văn bản đã tải như thế nào?

Bạn có thể kiểm soát cách xử lý khoảng cách đầu và cuối trong các tài liệu văn bản đã tải bằng cách sử dụng `TxtLoadOptions`. Các tùy chọn như `TxtLeadingSpacesOptions` Và `TxtTrailingSpacesOptions` cho phép bạn cắt hoặc giữ nguyên khoảng trống khi cần. Tham khảo phần "Xử lý tùy chọn khoảng trống" trong hướng dẫn này để biết ví dụ.

### Ý nghĩa của hướng văn bản trong Aspose.Words dành cho Java là gì?

Hướng văn bản là điều cần thiết đối với các tài liệu có chứa các tập lệnh hoặc ngôn ngữ hỗn hợp, chẳng hạn như tiếng Do Thái hoặc tiếng Ả Rập. Aspose.Words for Java cung cấp các tùy chọn để chỉ định hướng văn bản, đảm bảo hiển thị và định dạng văn bản đúng cách trong các ngôn ngữ này. Phần "Kiểm soát hướng văn bản" trong hướng dẫn này trình bày cách thiết lập hướng văn bản.

### Tôi có thể tìm thêm tài nguyên và hỗ trợ cho Aspose.Words for Java ở đâu?

Để biết thêm tài nguyên, tài liệu và hỗ trợ, hãy truy cập [Tài liệu Aspose.Words cho Java](https://reference.aspose.com/words/java/). Bạn cũng có thể tham gia diễn đàn cộng đồng Aspose.Words hoặc liên hệ với bộ phận hỗ trợ của Aspose để được trợ giúp về các vấn đề hoặc thắc mắc cụ thể.

### Aspose.Words for Java có phù hợp cho các dự án thương mại không?

Có, Aspose.Words for Java phù hợp cho cả dự án cá nhân và thương mại. Nó cung cấp các tùy chọn cấp phép để phù hợp với nhiều tình huống sử dụng khác nhau. Hãy đảm bảo xem xét các điều khoản cấp phép và giá cả trên trang web Aspose để chọn giấy phép phù hợp cho dự án của bạn.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}