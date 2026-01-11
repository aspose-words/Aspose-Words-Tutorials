---
date: 2026-01-11
description: Tìm hiểu cách làm sạch tài liệu Word bằng các tùy chọn dọn dẹp của Aspose.Words
  cho Java, bao gồm việc xóa các đoạn trống, các hàng bảng trống và các trường không
  sử dụng.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Dọn dẹp tài liệu Word bằng các tùy chọn dọn dẹp Aspose.Words (Java)
url: /vi/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dọn dẹp tài liệu Word bằng các tùy chọn Cleanup của Aspose.Words (Java)

Trong hướng dẫn này, bạn sẽ khám phá cách **dọn dẹp tài liệu Word** bằng Aspose.Words cho Java. Dù bạn đang tạo hoá đơn, hợp đồng hay các báo cáo mail‑merge hàng loạt, những đoạn văn rỗng không mong muốn, các trường không sử dụng, hoặc các hàng bảng trống đều có thể làm cho kết quả cuối cùng trông không chuyên nghiệp. Chúng tôi sẽ hướng dẫn từng tùy chọn dọn dẹp một cách chi tiết, cung cấp mã nguồn chính xác mà bạn cần, và giải thích *tại sao* mỗi thiết lập quan trọng để bạn có thể tạo ra các tài liệu hoàn hảo mỗi lần.

## Câu trả lời nhanh
- **“Dọn dẹp tài liệu Word” có nghĩa là gì?** Loại bỏ các đoạn văn rỗng, các vùng merge không sử dụng, các hàng bảng trống và các yếu tố thừa khác sau một thao tác mail‑merge.  
- **Tùy chọn dọn dẹp nào loại bỏ các đoạn văn rỗng?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Làm sao để xóa các hàng bảng trống?** Sử dụng `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Có thể loại bỏ các trường chưa bao giờ được điền dữ liệu không?** Có – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` hoặc `REMOVE_EMPTY_FIELDS`.  
- **Có cần giấy phép để chạy các ví dụ này không?** Bản dùng thử miễn phí đủ cho việc đánh giá; cần giấy phép thương mại cho môi trường sản xuất.

## “Dọn dẹp tài liệu Word” trong ngữ cảnh Mail Merge là gì?
Khi bạn thực hiện mail merge, Aspose.Words chèn dữ liệu vào các trường và vùng merge. Nếu một số trường nhận được `null` hoặc chuỗi rỗng, tài liệu có thể xuất hiện các đoạn văn lẻ, bảng trống, hoặc các vùng giữ chỗ. Các **tùy chọn dọn dẹp** tự động loại bỏ những dư thừa này, để lại một tài liệu sạch sẽ, sẵn sàng in ấn.

## Tại sao nên sử dụng các tùy chọn dọn dẹp?
- **Ngoại hình chuyên nghiệp:** Không còn dòng trống hay bảng lẻ.  
- **Kích thước tệp nhỏ hơn:** Loại bỏ các yếu tố không dùng giảm trọng lượng tài liệu.  
- **Xử lý downstream đơn giản hơn:** Tài liệu sạch dễ chuyển đổi sang PDF, HTML hoặc các định dạng khác.  
- **Tiết kiệm thời gian:** Một dòng lệnh thay thế các script xử lý thủ công sau merge.

## Yêu cầu trước
- Môi trường phát triển Java (JDK 8+).  
- Thư viện Aspose.Words cho Java – tải về từ [here](https://releases.aspose.com/words/java/).  
- Kiến thức cơ bản về mail‑merge.

## Hướng dẫn từng bước

### Bước 1: Cách loại bỏ các đoạn văn rỗng (Java)
Đầu tiên, chúng tôi sẽ chỉ cách loại bỏ các đoạn văn không chứa bất kỳ văn bản nào. Điều này đặc biệt hữu ích khi một trường merge trả về `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Điều gì xảy ra ở đây?**  
- `REMOVE_EMPTY_PARAGRAPHS` yêu cầu Aspose.Words loại bỏ bất kỳ đoạn văn nào trở nên rỗng sau khi merge.  
- Bật `cleanupParagraphsWithPunctuationMarks` cũng sẽ xóa các đoạn chỉ gồm dấu câu (ví dụ: “?”).

### Bước 2: Cách loại bỏ các vùng chưa merge
Nếu một vùng mail‑merge không có dữ liệu tương ứng, bạn có thể loại bỏ nó hoàn toàn.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Lý do quan trọng:**  
Các vùng không dùng thường để lại các phần trống hoặc tiêu đề lẻ. Cờ `REMOVE_UNUSED_REGIONS` sẽ tự động dọn dẹp chúng.

### Bước 3: Cách loại bỏ các trường rỗng
Khi một trường nhận được chuỗi rỗng, bạn có thể muốn xóa toàn bộ trường thay vì để lại chỗ trống.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Bước 4: Cách loại bỏ các trường không được sử dụng
Nếu một số trường không bao giờ được tham chiếu trong quá trình merge, bạn có thể gỡ bỏ chúng hoàn toàn.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Bước 5: Cách loại bỏ các trường chứa trong đoạn văn
Đôi khi một trường merge nằm trong một đoạn văn mà bạn cũng muốn loại bỏ.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Bước 6: Cách loại bỏ các hàng bảng trống
Các bảng thường có các hàng chỉ chứa các trường rỗng. Tùy chọn này sẽ cắt bỏ những hàng đó.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Các vấn đề thường gặp & Khắc phục
- **Đoạn văn không bị xóa:** Đảm bảo gọi `setCleanupParagraphsWithPunctuationMarks(true)` *sau* khi thiết lập tùy chọn dọn dẹp.  
- **Các hàng bảng trống vẫn tồn tại:** Kiểm tra các ô bảng thực sự chứa chuỗi rỗng (không phải khoảng trắng).  
- **Các trường không dùng vẫn còn:** Kiểm tra lại bạn đang sử dụng enum đúng (`REMOVE_UNUSED_FIELDS`) và các trường merge không bị điền dữ liệu ở nơi khác.

## Câu hỏi thường gặp

**Q: Sự khác nhau giữa `REMOVE_EMPTY_FIELDS` và `REMOVE_UNUSED_FIELDS` là gì?**  
A: `REMOVE_EMPTY_FIELDS` xóa các trường nhận được chuỗi rỗng hoặc `null` trong quá trình merge, trong khi `REMOVE_UNUSED_FIELDS` loại bỏ các trường chưa bao giờ được tham chiếu bởi thao tác merge.

**Q: Tôi có thể kết hợp nhiều tùy chọn dọn dẹp không?**  
A: Có. Phương thức `setCleanupOptions` chấp nhận phép OR bitwise của các giá trị enum, cho phép bạn dọn dẹp đoạn văn, bảng và vùng trong một lần gọi.

**Q: Bật `cleanupParagraphsWithPunctuationMarks` có ảnh hưởng đến văn bản bình thường không?**  
A: Nó chỉ loại bỏ các đoạn chỉ gồm ký tự dấu câu (ví dụ: “?” hoặc “---”). Các câu thông thường vẫn được giữ nguyên.

**Q: Có thể tùy chỉnh các dấu câu được coi là dấu câu không?**  
A: API hiện tại sử dụng một tập hợp dấu câu được định nghĩa trước. Để có hành vi tùy chỉnh, bạn cần thực hiện xử lý hậu kỳ trên tài liệu sau khi merge.

**Q: Các tùy chọn dọn dẹp này có hoạt động với chuyển đổi PDF không?**  
A: Hoàn toàn có. Khi tài liệu Word đã được dọn dẹp, bạn có thể chuyển đổi sang PDF, HTML hoặc bất kỳ định dạng hỗ trợ nào mà không mang theo các yếu tố không mong muốn.

## Kết luận
Bạn đã có một bộ công cụ hoàn chỉnh để **dọn dẹp tài liệu Word** trong quá trình mail merge bằng Aspose.Words cho Java. Bằng cách chọn `MailMergeCleanupOptions` phù hợp, bạn có thể tự động loại bỏ các đoạn văn rỗng, các hàng bảng trống, các trường không dùng và nhiều hơn nữa — mang lại cho bạn một tài liệu gọn gàng, sẵn sàng cho môi trường sản xuất mỗi lần.

---

**Last Updated:** 2026-01-11  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}