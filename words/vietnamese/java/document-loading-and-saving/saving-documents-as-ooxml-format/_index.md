---
date: 2026-01-09
description: Tìm hiểu cách mã hóa tệp docx bằng mật khẩu và thay đổi mức nén khi lưu
  tài liệu ở định dạng OOXML bằng Aspose.Words cho Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Mã hoá docx bằng mật khẩu – Lưu OOXML bằng Aspose.Words Java
url: /vi/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mã hoá docx bằng mật khẩu – Lưu OOXML với Aspose.Words Java

## Giới thiệu về việc lưu tài liệu dưới định dạng OOXML trong Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ học cách **mã hoá docx bằng mật khẩu** và lưu tài liệu ở định dạng OOXML bằng Aspose.Words cho Java. OOXML (Office Open XML) là định dạng tệp hiện đại được Microsoft Word và nhiều ứng dụng văn phòng khác sử dụng. Chúng tôi sẽ hướng dẫn các tùy chọn phổ biến nhất—bảo vệ bằng mật khẩu, mức độ tuân thủ, cập nhật thuộc tính, xử lý ký tự legacy, và **cách thay đổi mức độ nén**—để bạn có thể tùy chỉnh kết quả theo nhu cầu chính xác.

## Câu trả lời nhanh
- **Làm thế nào để bảo vệ một tệp Word?** Sử dụng `OoxmlSaveOptions.setPassword("yourPassword")` trước khi lưu.  
- **Mức độ tuân thủ OOXML nào tôi nên chọn?** ISO 29500 2008 Strict để đạt khả năng tương thích tối đa với các phiên bản Office hiện đại.  
- **Tôi có thể giữ lại các ký tự điều khiển legacy không?** Có, bật `setKeepLegacyControlChars(true)`.  
- **Làm thế nào để thay đổi mức độ nén?** Đặt `setCompressionLevel(CompressionLevel.SUPER_FAST)` hoặc `MAXIMUM` tùy nhu cầu.  
- **Các tùy chọn này có ảnh hưởng đến kích thước tệp không?** Mức độ nén và việc xử lý ký tự legacy có thể thay đổi đáng kể kích thước .docx cuối cùng.

## “Mã hoá docx bằng mật khẩu” là gì?
Mã hoá một tệp DOCX có nghĩa là tài liệu được lưu với mã hoá AES‑256, yêu cầu mật khẩu để mở trong Word hoặc bất kỳ trình xem tương thích nào. Điều này rất cần thiết để bảo vệ thông tin mật khi tệp được chia sẻ qua email, lưu trữ đám mây hoặc cổng thông tin nội bộ.

## Tại sao nên sử dụng các tùy chọn lưu OOXML?
- **Bảo mật:** Bảo vệ bằng mật khẩu ngăn chặn truy cập trái phép.  
- **Tương thích:** Cài đặt tuân thủ đảm bảo tệp hoạt động trên các phiên bản Word khác nhau.  
- **Hiệu suất:** Điều chỉnh mức độ nén có thể tăng tốc quá trình lưu hoặc giảm kích thước tệp.  
- **Bảo tồn:** Giữ lại các ký tự điều khiển legacy duy trì độ chính xác khi chuyển đổi các tài liệu cũ.

## Yêu cầu trước
- Thư viện Aspose.Words cho Java được thêm vào dự án của bạn (Maven/Gradle hoặc JAR thủ công).  
- Java 8 hoặc cao hơn.  
- Tài liệu nguồn (`.docx` hoặc `.doc`) bạn muốn xử lý.

## Lưu tài liệu với mã hoá mật khẩu

Bạn có thể mã hoá tài liệu của mình bằng mật khẩu khi lưu ở định dạng OOXML. Dưới đây là cách thực hiện:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Mẹo chuyên nghiệp:** Chọn mật khẩu mạnh và lưu trữ an toàn; mật khẩu không thể khôi phục từ tệp đã mã hoá.

## Cài đặt mức độ tuân thủ OOXML

Bạn có thể chỉ định mức độ tuân thủ OOXML khi lưu tài liệu. Ví dụ, bạn có thể đặt nó thành ISO 29500:2008 (Strict). Dưới đây là cách thực hiện:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Cập nhật thuộc tính Thời gian Lưu cuối

Bạn có thể chọn cập nhật thuộc tính “Last Saved Time” của tài liệu khi lưu. Dưới đây là cách thực hiện:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Giữ lại các ký tự điều khiển Legacy

Nếu tài liệu của bạn chứa các ký tự điều khiển legacy, bạn có thể chọn giữ chúng khi lưu. Dưới đây là cách thực hiện:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Cách thay đổi mức độ nén khi lưu OOXML

Bạn có thể điều chỉnh mức độ nén khi lưu tài liệu. Ví dụ, bạn có thể đặt nó thành `SUPER_FAST` để nén tối thiểu hoặc `MAXIMUM` để có kích thước tệp nhỏ nhất. Dưới đây là cách thực hiện:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Đây là một số tùy chọn và cài đặt quan trọng bạn có thể sử dụng khi lưu tài liệu ở định dạng OOXML bằng Aspose.Words cho Java. Hãy tự do khám phá thêm các tùy chọn và tùy chỉnh quy trình lưu tài liệu của bạn theo nhu cầu.

## Mã nguồn hoàn chỉnh để lưu tài liệu dưới định dạng OOXML trong Aspose.Words cho Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Kết luận

Trong hướng dẫn toàn diện này, chúng tôi đã khám phá cách **mã hoá docx bằng mật khẩu** và lưu tài liệu ở định dạng OOXML bằng Aspose.Words cho Java. Dù bạn cần bảo vệ tệp, đảm bảo tuân thủ OOXML nghiêm ngặt, cập nhật thuộc tính tài liệu, bảo tồn các ký tự điều khiển legacy, hay **thay đổi mức độ nén**, Aspose.Words cung cấp một bộ công cụ đa năng để đáp ứng yêu cầu của bạn.

## Câu hỏi thường gặp

**H: Làm thế nào để bỏ bảo vệ mật khẩu khỏi tài liệu đã được bảo vệ bằng mật khẩu?**  
A: Mở tài liệu bằng mật khẩu đúng, sau đó lưu mà không chỉ định mật khẩu trong `OoxmlSaveOptions`. Điều này sẽ tạo ra một bản sao không được bảo vệ.

**H: Tôi có thể đặt các thuộc tính tùy chỉnh khi lưu tài liệu ở định dạng OOXML không?**  
A: Có. Sử dụng `BuiltInDocumentProperties` và `CustomDocumentProperties` trên đối tượng `Document` trước khi gọi `save()`.

**H: Mức độ nén mặc định khi lưu tài liệu ở định dạng OOXML là gì?**  
A: Mặc định là `CompressionLevel.NORMAL`. Bạn có thể chuyển sang `SUPER_FAST` để tăng tốc hoặc `MAXIMUM` để có kích thước tệp nhỏ nhất.

**H: Việc bật `keepLegacyControlChars` có ảnh hưởng đến khả năng tương thích với các phiên bản Word hiện đại không?**  
A: Word hiện đại có thể mở các tệp có ký tự điều khiển legacy, nhưng một số tính năng cũ có thể hiển thị khác nhau. Chỉ sử dụng tùy chọn này khi bạn cần bảo tồn nội dung gốc một cách chính xác.

**H: Có thể kết hợp nhiều tùy chọn lưu (ví dụ: mật khẩu + nén) trong một lần gọi không?**  
A: Chắc chắn. Cấu hình tất cả các thuộc tính mong muốn trên một thể hiện `OoxmlSaveOptions` duy nhất trước khi truyền nó cho `doc.save()`.

---

**Cập nhật lần cuối:** 2026-01-09  
**Kiểm tra với:** Aspose.Words for Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}