---
date: 2025-12-27
description: Tìm hiểu cách đặt hướng, tải tệp txt, loại bỏ khoảng trắng và chuyển
  đổi txt sang docx bằng Aspose.Words cho Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Cách Đặt Hướng và Tải Tệp Văn Bản bằng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Hướng và Tải Các Tệp Văn Bản với Aspose.Words cho Java

## Giới thiệu về việc tải các tệp văn bản với Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ khám phá **cách đặt hướng** khi tải các tài liệu văn bản thuần và xem các cách thực tế để **tải txt**, **cắt bỏ khoảng trắng**, và **chuyển đổi txt sang docx** bằng Aspose.Words cho Java. Cho dù bạn đang xây dựng một dịch vụ chuyển đổi tài liệu hay cần kiểm soát chi tiết việc phát hiện danh sách, bài hướng dẫn này sẽ dẫn bạn qua từng bước với các giải thích rõ ràng và mã sẵn sàng chạy.

## Câu trả lời nhanh
- **Làm thế nào để đặt hướng văn bản cho một tệp TXT đã tải?** Sử dụng `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` hoặc chỉ định `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Aspose.Words có thể phát hiện danh sách có số trong văn bản thuần không?** Có – bật `DetectNumberingWithWhitespaces` trong `TxtLoadOptions`.
- **Làm sao để cắt bỏ khoảng trắng ở đầu và cuối?** Đặt `TxtLeadingSpacesOptions.TRIM` và `TxtTrailingSpacesOptions.TRIM`.
- **Có thể chuyển đổi một tệp TXT sang DOCX trong một dòng không?** Tải TXT bằng `TxtLoadOptions` và gọi `Document.save("output.docx")`.
- **Yêu cầu phiên bản Java nào?** Java 8+ là đủ cho Aspose.Words 24.x.

## “Cách đặt hướng” là gì trong Aspose.Words?

Khi một tệp văn bản chứa các script từ phải sang trái (ví dụ: Hebrew hoặc Arabic), thư viện cần biết thứ tự đọc. Enum `DocumentDirection` cho phép bạn **đặt hướng** thủ công hoặc để Aspose tự động phát hiện, đảm bảo bố cục và định dạng bidi chính xác.

## Tại sao nên sử dụng Aspose.Words để tải các tệp TXT?

- **Phát hiện danh sách chính xác** – xử lý danh sách có số, có dấu đầu dòng và danh sách phân tách bằng khoảng trắng.
- **Xử lý khoảng trắng chi tiết** – cắt bỏ hoặc giữ lại khoảng trắng ở đầu/cuối.
- **Tự động phát hiện hướng văn bản** – hoàn hảo cho tài liệu đa ngôn ngữ.
- **Chuyển đổi một bước** – tải một tệp `.txt` và lưu thành `.docx`, `.pdf`, hoặc bất kỳ định dạng nào được hỗ trợ.

## Yêu cầu trước
- Java 8 hoặc mới hơn.
- Thư viện Aspose.Words cho Java (thêm phụ thuộc Maven/Gradle hoặc JAR vào dự án của bạn).
- Kiến thức cơ bản về các luồng I/O của Java.

## Hướng dẫn từng bước

### Bước 1: Phát hiện danh sách (cách tải txt)

Để tải một tài liệu văn bản và tự động phát hiện danh sách, tạo một thể hiện `TxtLoadOptions` và bật tính năng phát hiện danh sách. Đoạn mã dưới đây hiển thị một số kiểu danh sách và bật đánh số có nhận thức khoảng trắng.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Mẹo chuyên nghiệp:** Nếu bạn chỉ cần phát hiện danh sách cơ bản, bạn có thể bỏ qua tùy chọn khoảng trắng – Aspose vẫn sẽ nhận ra các mẫu chuẩn `1.` và `1)`.

### Bước 2: Xử lý tùy chọn khoảng trắng (cách cắt bỏ khoảng trắng)

Khoảng trắng ở đầu và cuối thường gây ra lỗi định dạng. Sử dụng `TxtLeadingSpacesOptions` và `TxtTrailingSpacesOptions` để kiểm soát hành vi này.

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

> **Tại sao lại quan trọng:** Cắt bỏ khoảng trắng ngăn ngừa việc thụt lề không mong muốn trong DOCX kết quả, giúp tài liệu trông sạch sẽ mà không cần xử lý thủ công.

### Bước 3: Kiểm soát hướng văn bản (cách đặt hướng)

Đối với các ngôn ngữ từ phải sang trái, đặt hướng tài liệu trước khi tải. Ví dụ dưới đây tải một tệp văn bản Hebrew và in ra cờ bidi để xác nhận hướng.

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

> **Cạm bẫy thường gặp:** Quên đặt `DocumentDirection` có thể dẫn đến văn bản Arabic/Hebrew bị lộn xộn, các ký tự xuất hiện sai thứ tự.

### Mã nguồn hoàn chỉnh để tải các tệp văn bản với Aspose.Words cho Java

Dưới đây là mã nguồn đầy đủ, sẵn sàng chạy, kết hợp phát hiện danh sách, xử lý khoảng trắng và kiểm soát hướng. Bạn có thể sao chép và dán nó vào một lớp duy nhất và chạy ba phương thức kiểm thử riêng biệt.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Không phát hiện được danh sách | `DetectNumberingWithWhitespaces` để `false` cho các danh sách phân tách bằng khoảng trắng | Bật `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Thụt lề thừa sau khi tải | Khoảng trắng ở đầu được giữ lại | Đặt `TxtLeadingSpacesOptions.TRIM` |
| Văn bản Hebrew hiển thị ngược | Chưa đặt hướng tài liệu hoặc đặt thành `LEFT_TO_RIGHT` | Sử dụng `DocumentDirection.AUTO` hoặc `RIGHT_TO_LEFT` |
| DOCX đầu ra rỗng | Luồng đầu vào không được đặt lại trước lần tải thứ hai | Tạo lại `ByteArrayInputStream` cho mỗi lần gọi tải |

## Câu hỏi thường gặp

### H: Aspose.Words cho Java là gì?
A: Aspose.Words cho Java là một thư viện xử lý tài liệu mạnh mẽ cho phép các nhà phát triển tạo, thao tác và chuyển đổi tài liệu Word một cách lập trình trong các ứng dụng Java. Nó hỗ trợ một loạt các tính năng, từ việc tải văn bản đơn giản đến định dạng và chuyển đổi phức tạp.

### H: Làm thế nào để bắt đầu với Aspose.Words cho Java?
A: 1. Tải xuống và cài đặt thư viện Aspose.Words cho Java. 2. Tham khảo tài liệu tại [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) để có thông tin chi tiết và các ví dụ. 3. Khám phá mã mẫu và các hướng dẫn để học cách sử dụng thư viện một cách hiệu quả.

### H: Làm sao để tải một tài liệu văn bản bằng Aspose.Words cho Java?
A: Sử dụng lớp `TxtLoadOptions` cùng với hàm khởi tạo `Document`. Chỉ định các tùy chọn như phát hiện danh sách, xử lý khoảng trắng hoặc hướng văn bản như đã minh họa trong các phần hướng dẫn từng bước ở trên.

### H: Tôi có thể chuyển đổi tài liệu văn bản đã tải sang các định dạng khác không?
A: Có. Sau khi tải tệp TXT vào đối tượng `Document`, gọi `doc.save("output.pdf")`, `doc.save("output.docx")`, hoặc bất kỳ định dạng nào khác được hỗ trợ.

### H: Làm sao để xử lý khoảng trắng trong các tài liệu văn bản đã tải?
A: Kiểm soát khoảng trắng ở đầu và cuối bằng `TxtLeadingSpacesOptions` và `TxtTrailingSpacesOptions`. Đặt chúng thành `TRIM` để loại bỏ khoảng trắng không mong muốn, hoặc thành `PRESERVE` nếu bạn cần giữ nguyên khoảng cách gốc.

### H: Tầm quan trọng của hướng văn bản trong Aspose.Words cho Java là gì?
A: Hướng văn bản đảm bảo việc hiển thị đúng các script từ phải sang trái (Hebrew, Arabic, v.v.). Bằng cách đặt `DocumentDirection`, bạn đảm bảo rằng văn bản bidi được hiển thị chính xác trong tài liệu kết quả.

### H: Tôi có thể tìm thêm tài nguyên và hỗ trợ cho Aspose.Words cho Java ở đâu?
A: Truy cập [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) để xem tài liệu API, mẫu mã và các hướng dẫn chi tiết. Bạn cũng có thể tham gia diễn đàn cộng đồng Aspose hoặc liên hệ hỗ trợ của Aspose để hỏi các câu hỏi cụ thể.

### H: Aspose.Words cho Java có phù hợp cho các dự án thương mại không?
A: Có. Nó cung cấp các tùy chọn cấp phép cho cả sử dụng cá nhân và thương mại. Xem lại các điều khoản cấp phép trên trang web Aspose để chọn gói phù hợp cho dự án của bạn.

## Kết luận

Bạn giờ đã có một bộ công cụ hoàn chỉnh để **tải các tệp txt**, **phát hiện danh sách**, **cắt bỏ khoảng trắng**, và **đặt hướng** khi chuyển đổi văn bản thuần thành các tài liệu Word phong phú bằng Aspose.Words cho Java. Áp dụng các mẫu này để tự động hoá quy trình tài liệu, cải thiện hỗ trợ đa ngôn ngữ và đảm bảo đầu ra sạch sẽ, chuyên nghiệp mỗi lần.

---

**Cập nhật lần cuối:** 2025-12-27  
**Kiểm tra với:** Aspose.Words for Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}