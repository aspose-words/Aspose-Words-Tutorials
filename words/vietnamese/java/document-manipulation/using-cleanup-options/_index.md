---
"description": "Tăng cường độ rõ nét của tài liệu với tùy chọn dọn dẹp Aspose.Words for Java. Tìm hiểu cách xóa các đoạn văn trống, vùng không sử dụng và nhiều hơn nữa."
"linktitle": "Sử dụng Tùy chọn Dọn dẹp"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng tùy chọn dọn dẹp trong Aspose.Words cho Java"
"url": "/vi/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng tùy chọn dọn dẹp trong Aspose.Words cho Java


## Giới thiệu về cách sử dụng tùy chọn Cleanup trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng tùy chọn dọn dẹp trong Aspose.Words for Java để thao tác và dọn dẹp tài liệu trong quá trình trộn thư. Tùy chọn dọn dẹp cho phép bạn kiểm soát nhiều khía cạnh khác nhau của việc dọn dẹp tài liệu, chẳng hạn như xóa các đoạn văn trống, vùng không sử dụng, v.v.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã tích hợp thư viện Aspose.Words for Java vào dự án của mình. Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/java/).

## Bước 1: Xóa đoạn văn trống

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn trường hợp nhập
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Thiết lập tùy chọn dọn dẹp
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Cho phép dọn dẹp đoạn văn bằng dấu chấm câu
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Thực hiện trộn thư
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Lưu tài liệu
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Trong ví dụ này, chúng tôi tạo một tài liệu mới, chèn các trường hợp hợp nhất và thiết lập các tùy chọn dọn dẹp để xóa các đoạn văn trống. Ngoài ra, chúng tôi cho phép xóa các đoạn văn có dấu chấm câu. Sau khi thực hiện hợp nhất thư, tài liệu được lưu với tùy chọn dọn dẹp đã chỉ định được áp dụng.

## Bước 2: Xóa các vùng chưa được hợp nhất

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Đặt tùy chọn dọn dẹp để xóa các vùng không sử dụng
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Thực hiện trộn thư với các vùng
doc.getMailMerge().executeWithRegions(data);

// Lưu tài liệu
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Trong ví dụ này, chúng tôi mở một tài liệu hiện có với các vùng hợp nhất, thiết lập tùy chọn dọn dẹp để xóa các vùng không sử dụng, sau đó thực hiện hợp nhất thư với dữ liệu trống. Quá trình này tự động xóa các vùng không sử dụng khỏi tài liệu.

## Bước 3: Xóa các trường trống

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Đặt tùy chọn dọn dẹp để xóa các trường trống
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Thực hiện trộn thư
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Lưu tài liệu
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Trong ví dụ này, chúng tôi mở một tài liệu có các trường hợp hợp nhất, thiết lập tùy chọn dọn dẹp để xóa các trường trống và thực hiện hợp nhất thư với dữ liệu. Sau khi hợp nhất, mọi trường trống sẽ bị xóa khỏi tài liệu.

## Bước 4: Xóa các trường không sử dụng

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Đặt tùy chọn dọn dẹp để xóa các trường không sử dụng
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Thực hiện trộn thư
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Lưu tài liệu
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Trong ví dụ này, chúng tôi mở một tài liệu có các trường hợp hợp nhất, thiết lập tùy chọn dọn dẹp để xóa các trường không sử dụng và thực hiện hợp nhất thư với dữ liệu. Sau khi hợp nhất, mọi trường không sử dụng sẽ bị xóa khỏi tài liệu.

## Bước 5: Xóa các trường chứa

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Đặt tùy chọn dọn dẹp để xóa các trường chứa
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Thực hiện trộn thư
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Lưu tài liệu
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Trong ví dụ này, chúng tôi mở một tài liệu có các trường hợp hợp nhất, thiết lập tùy chọn dọn dẹp để xóa các trường chứa và thực hiện hợp nhất thư với dữ liệu. Sau khi hợp nhất, các trường sẽ tự động bị xóa khỏi tài liệu.

## Bước 6: Xóa các hàng bảng trống

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Đặt tùy chọn dọn dẹp để xóa các hàng bảng trống
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Thực hiện trộn thư
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Lưu tài liệu
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Trong ví dụ này, chúng tôi mở một tài liệu có bảng và các trường hợp nhất, thiết lập tùy chọn dọn dẹp để xóa các hàng bảng trống và thực hiện hợp nhất thư với dữ liệu. Sau khi hợp nhất, mọi hàng bảng trống sẽ bị xóa khỏi tài liệu.

## Phần kết luận

Trong hướng dẫn này, bạn đã học cách sử dụng các tùy chọn dọn dẹp trong Aspose.Words for Java để thao tác và dọn dẹp tài liệu trong quá trình trộn thư. Các tùy chọn này cung cấp khả năng kiểm soát chi tiết đối với việc dọn dẹp tài liệu, cho phép bạn dễ dàng tạo các tài liệu được đánh bóng và tùy chỉnh.

## Câu hỏi thường gặp

### Tùy chọn dọn dẹp trong Aspose.Words cho Java là gì?

Tùy chọn dọn dẹp trong Aspose.Words for Java là các thiết lập cho phép bạn kiểm soát nhiều khía cạnh khác nhau của việc dọn dẹp tài liệu trong quá trình trộn thư. Chúng cho phép bạn xóa các thành phần không cần thiết như đoạn văn trống, vùng không sử dụng, v.v., đảm bảo tài liệu cuối cùng của bạn có cấu trúc tốt và được trau chuốt.

### Làm thế nào để xóa đoạn văn trống khỏi tài liệu của tôi?

Để xóa các đoạn văn trống khỏi tài liệu của bạn bằng Aspose.Words cho Java, bạn có thể đặt `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` tùy chọn thành đúng. Điều này sẽ tự động loại bỏ các đoạn văn không có nội dung, giúp tài liệu sạch hơn.

### Mục đích của việc này là gì? `REMOVE_UNUSED_REGIONS` tùy chọn dọn dẹp?

Các `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Tùy chọn này được sử dụng để xóa các vùng trong tài liệu không có dữ liệu tương ứng trong quá trình trộn thư. Nó giúp giữ cho tài liệu của bạn gọn gàng bằng cách loại bỏ các chỗ giữ chỗ không sử dụng.

### Tôi có thể xóa các hàng bảng trống khỏi tài liệu bằng Aspose.Words cho Java không?

Có, bạn có thể xóa các hàng bảng trống khỏi tài liệu bằng cách thiết lập `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` tùy chọn dọn dẹp thành đúng. Tùy chọn này sẽ tự động xóa bất kỳ hàng bảng nào không chứa dữ liệu, đảm bảo bảng có cấu trúc tốt trong tài liệu của bạn.

### Điều gì xảy ra khi tôi thiết lập `REMOVE_CONTAINING_FIELDS` lựa chọn?

Thiết lập `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` tùy chọn sẽ xóa toàn bộ trường hợp hợp nhất, bao gồm cả đoạn văn chứa nó, khỏi tài liệu trong quá trình hợp nhất thư. Điều này hữu ích khi bạn muốn xóa các trường hợp hợp nhất và văn bản liên quan của chúng.

### Làm thế nào để xóa các trường trộn không sử dụng khỏi tài liệu của tôi?

Để xóa các trường hợp nhập không sử dụng khỏi tài liệu, bạn có thể đặt `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` tùy chọn thành đúng. Điều này sẽ tự động loại bỏ các trường hợp nhập không được điền trong quá trình trộn thư, giúp tài liệu sạch hơn.

### Sự khác biệt giữa là gì? `REMOVE_EMPTY_FIELDS` Và `REMOVE_UNUSED_FIELDS` tùy chọn dọn dẹp?

Các `REMOVE_EMPTY_FIELDS` tùy chọn xóa các trường hợp nhất không có dữ liệu hoặc trống trong quá trình hợp nhất thư. Mặt khác, `REMOVE_UNUSED_FIELDS` Tùy chọn này xóa các trường hợp hợp nhất không được điền dữ liệu trong quá trình hợp nhất. Lựa chọn giữa chúng phụ thuộc vào việc bạn muốn xóa các trường không có nội dung hay các trường không được sử dụng trong thao tác hợp nhất cụ thể.

### Làm thế nào tôi có thể bật tính năng xóa đoạn văn có dấu chấm câu?

Để cho phép xóa các đoạn văn có dấu chấm câu, bạn có thể thiết lập `cleanupParagraphsWithPunctuationMarks` tùy chọn thành true và chỉ định các dấu câu cần xem xét để dọn dẹp. Điều này cho phép bạn tạo một tài liệu tinh tế hơn bằng cách xóa các đoạn văn chỉ có dấu câu không cần thiết.

### Tôi có thể tùy chỉnh các tùy chọn dọn dẹp trong Aspose.Words cho Java không?

Có, bạn có thể tùy chỉnh các tùy chọn dọn dẹp theo nhu cầu cụ thể của mình. Bạn có thể chọn tùy chọn dọn dẹp nào để áp dụng và cấu hình chúng theo yêu cầu dọn dẹp tài liệu của mình, đảm bảo rằng tài liệu cuối cùng của bạn đáp ứng các tiêu chuẩn mong muốn.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}