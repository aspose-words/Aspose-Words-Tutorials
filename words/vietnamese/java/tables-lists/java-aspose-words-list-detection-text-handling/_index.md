---
"date": "2025-03-28"
"description": "Tìm hiểu cách làm chủ phát hiện danh sách, xử lý văn bản và nhiều hơn nữa bằng Aspose.Words for Java. Hướng dẫn này bao gồm phát hiện danh sách được phân tách bằng khoảng trắng, cắt khoảng trắng, xác định hướng tài liệu, vô hiệu hóa phát hiện đánh số tự động và quản lý siêu liên kết."
"title": "Phát hiện danh sách chính và xử lý văn bản trong Java với Aspose.Words&#58; Hướng dẫn đầy đủ"
"url": "/vi/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Phát hiện danh sách chính và xử lý văn bản trong Java với Aspose.Words: Hướng dẫn đầy đủ

## Giới thiệu

Làm việc với các tài liệu văn bản thuần túy thường gặp thách thức trong việc xác định dữ liệu có cấu trúc như danh sách do các dấu phân cách không nhất quán và các vấn đề về định dạng. Thư viện Aspose.Words for Java cung cấp các tính năng mạnh mẽ để giải quyết các vấn đề này, bao gồm phát hiện đánh số có khoảng trắng, cắt khoảng trắng, xác định hướng tài liệu, vô hiệu hóa phát hiện đánh số tự động và quản lý siêu liên kết trong tài liệu văn bản. Hướng dẫn này giúp bạn thao tác dữ liệu văn bản hiệu quả bằng Aspose.Words.

**Những gì bạn sẽ học được:**
- Kỹ thuật phát hiện danh sách được phân tách bằng khoảng trắng
- Phương pháp cắt bớt khoảng trống không mong muốn khỏi nội dung tài liệu
- Các phương pháp xác định hướng đọc của tệp văn bản
- Cách vô hiệu hóa tính năng phát hiện đánh số tự động
- Chiến lược phát hiện và quản lý siêu liên kết trong tài liệu văn bản thuần túy

Hãy cùng xem lại những điều kiện tiên quyết cần thiết trước khi triển khai các tính năng này.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo rằng bạn có những điều sau:

### Thư viện bắt buộc:
- **Aspose.Words cho Java**: Phiên bản 25.3 trở lên.

### Thiết lập môi trường:
- Đảm bảo môi trường phát triển của bạn hỗ trợ Maven hoặc Gradle vì chúng là cần thiết để quản lý các phụ thuộc.

### Điều kiện tiên quyết về kiến thức:
- Hiểu biết cơ bản về lập trình Java
- Quen thuộc với hệ thống xây dựng Maven hoặc Gradle

## Thiết lập Aspose.Words

Để bắt đầu sử dụng Aspose.Words for Java trong dự án của bạn, bạn cần bao gồm các dependency cần thiết. Sau đây là cách thực hiện:

**Chuyên gia:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Cấp độ:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Mua lại giấy phép

Để sử dụng Aspose.Words một cách đầy đủ, hãy cân nhắc việc xin giấy phép:
- **Dùng thử miễn phí**: Có sẵn để thử nghiệm các tính năng.
- **Giấy phép tạm thời**: Dành cho mục đích đánh giá mà không có giới hạn.
- **Mua**: Giấy phép đầy đủ để sử dụng lâu dài.

Sau khi có giấy phép, hãy khởi tạo nó trong ứng dụng của bạn để mở khóa mọi chức năng của thư viện.

## Hướng dẫn thực hiện

Hãy cùng phân tích từng tính năng và xem cách triển khai chúng bằng Aspose.Words cho Java.

### Phát hiện đánh số có khoảng trắng

**Tổng quan:** Tính năng này cho phép bạn xác định danh sách trong tài liệu văn bản thuần túy sử dụng khoảng trắng làm dấu phân cách.

#### Bước 1: Tải tài liệu
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Bước 2: Xác thực phát hiện danh sách
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Các tham số và phương pháp:*
- `setDetectNumberingWithWhitespaces(true)`: Cấu hình trình phân tích cú pháp để nhận dạng danh sách có dấu cách phân cách.
- `doc.getLists().getCount()`: Truy xuất số lượng danh sách được phát hiện trong tài liệu.

### Cắt khoảng cách dẫn đầu và khoảng cách theo sau

**Tổng quan:** Tính năng này cắt bớt các khoảng trắng không cần thiết ở đầu hoặc cuối dòng trong tài liệu văn bản thuần túy, đảm bảo định dạng văn bản sạch.

#### Bước 1: Cấu hình Tùy chọn Tải
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Bước 2: Xác minh cắt tỉa
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Cấu hình chính:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Cắt khoảng cách từ đầu dòng.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: Xóa khoảng trắng ở cuối dòng.

### Phát hiện hướng tài liệu

**Tổng quan:** Xác định xem tài liệu có nên được đọc từ phải sang trái (RTL) hay không, chẳng hạn như văn bản tiếng Do Thái hoặc tiếng Ả Rập.

#### Bước 1: Thiết lập Tự động phát hiện
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Tắt chức năng phát hiện số tự động

**Tổng quan:** Ngăn không cho thư viện tự động phát hiện và định dạng các mục danh sách.

#### Bước 1: Cấu hình Tùy chọn Tải
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Phát hiện siêu liên kết trong văn bản

**Tổng quan:** Xác định và quản lý các siêu liên kết trong tài liệu văn bản thuần túy.

#### Bước 1: Thiết lập tùy chọn phát hiện
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Ứng dụng thực tế

1. **Hệ thống quản lý nội dung (CMS):** Tự động định dạng nội dung do người dùng tạo thành danh sách có cấu trúc.
2. **Công cụ trích xuất dữ liệu:** Sử dụng tính năng phát hiện danh sách để sắp xếp dữ liệu phi cấu trúc nhằm mục đích phân tích.
3. **Quy trình xử lý văn bản:** Nâng cao quá trình xử lý trước tài liệu bằng cách cắt khoảng trắng và phát hiện hướng văn bản.

## Cân nhắc về hiệu suất

Để tối ưu hóa hiệu suất:
- Tải tài liệu với thao tác tối thiểu, tập trung vào các tính năng cần thiết.
- Quản lý việc sử dụng bộ nhớ bằng cách xử lý các tài liệu lớn thành nhiều phần khi có thể.

## Phần kết luận

Bằng cách tận dụng Aspose.Words for Java, bạn có thể quản lý hiệu quả dữ liệu văn bản trong các tài liệu văn bản thuần túy. Từ việc phát hiện danh sách được phân tách bằng khoảng trắng đến xử lý hướng văn bản và siêu liên kết, các công cụ mạnh mẽ này cho phép thao tác tài liệu mạnh mẽ. Để khám phá thêm, hãy tham khảo [Tài liệu Aspose.Words](https://reference.aspose.com/words/java/) hoặc dùng thử miễn phí.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}