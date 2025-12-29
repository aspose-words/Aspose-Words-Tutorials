---
date: 2025-12-29
description: Tìm hiểu cách mã hóa tệp docx bằng mật khẩu bằng các tùy chọn lưu của
  Aspose.Words cho Java. Bảo mật, tối ưu và tùy chỉnh các tệp OOXML của bạn một cách
  dễ dàng.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Cách mã hóa DOCX bằng mật khẩu sử dụng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách Mã Hoá DOCX Bằng Mật Khẩu Sử Dụng Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ khám phá **cách mã hoá docx bằng mật khẩu** khi lưu tài liệu ở định dạng OOXML bằng Aspose.Words cho Java. Dù bạn đang bảo vệ các báo cáo mật, hay bảo mật bản thảo hợp đồng, các bước dưới đây sẽ chỉ cho bạn cách áp dụng bảo vệ mật khẩu và tinh chỉnh các tùy chọn lưu OOXML khác.

## Câu Hỏi Nhanh
- **Tôi có thể mã hoá tệp DOCX bằng mật khẩu không?** Có, sử dụng `OoxmlSaveOptions.setPassword()` trước khi lưu.  
- **Lớp nào điều khiển các cài đặt lưu OOXML?** `OoxmlSaveOptions` (thuộc Aspose.Words).  
- **Tôi có cần giấy phép để bảo vệ bằng mật khẩu không?** Cần có giấy phép Aspose.Words hợp lệ cho môi trường sản xuất.  
- **Tôi có thể kết hợp mã hoá với các cài đặt tuân thủ không?** Chắc chắn – đặt cả `setPassword` và `setCompliance` trên cùng một thể hiện `OoxmlSaveOptions`.  
- **Các mức nén nào có sẵn?** `NORMAL`, `SUPER_FAST`, và `MAXIMUM` thông qua `CompressionLevel`.

## “encrypt docx with password” là gì?
Mã hoá một tệp DOCX có nghĩa là nội dung của tệp được lưu dưới dạng đã được mã hoá và chỉ có thể mở được sau khi cung cấp đúng mật khẩu. Điều này bảo vệ thông tin nhạy cảm khỏi truy cập trái phép, đồng thời vẫn cho phép các công cụ Word tiêu chuẩn mở tệp khi mật khẩu được nhập.

## Tại sao sử dụng Aspose.Words save options cho việc mã hoá?
Aspose.Words cung cấp một bộ **aspose words save options** phong phú cho phép bạn kiểm soát không chỉ việc mã hoá mà còn mức độ tuân thủ, nén và xử lý ký tự điều khiển legacy — tất cả đều từ mã Java. Điều này loại bỏ nhu cầu xử lý thủ công sau khi lưu hoặc dùng công cụ của bên thứ ba.

## Yêu Cầu Trước
- Java Development Kit (JDK 8 trở lên)  
- Thư viện Aspose.Words cho Java đã được thêm vào dự án (Maven/Gradle hoặc JAR)  
- Giấy phép Aspose.Words hợp lệ cho môi trường sản xuất (tùy chọn cho bản đánh giá)

## Lưu Tài Liệu Với Mã Hoá Mật Khẩu

Bạn có thể mã hoá tài liệu bằng mật khẩu khi lưu ở định dạng OOXML. Đây là cách thực hiện:

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

## Đặt Mức Tuân Thủ OOXML

Bạn có thể chỉ định mức tuân thủ OOXML khi lưu tài liệu. Ví dụ, bạn có thể đặt nó thành ISO 29500:2008 (Strict). Cách thực hiện:

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

## Cập Nhật Thuộc Tính “Last Saved Time”

Bạn có thể chọn cập nhật thuộc tính “Last Saved Time” của tài liệu khi lưu. Cách thực hiện:

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

## Giữ Các Ký Tự Điều Khiển Legacy

Nếu tài liệu của bạn chứa các ký tự điều khiển legacy, bạn có thể chọn giữ chúng khi lưu. Cách thực hiện:

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

## Đặt Mức Nén

Bạn có thể điều chỉnh mức nén khi lưu tài liệu. Ví dụ, bạn có thể đặt thành **SUPER_FAST** để nén tối thiểu. Cách thực hiện:

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

Đây là một số tùy chọn và cài đặt chính bạn có thể sử dụng khi lưu tài liệu ở định dạng OOXML bằng Aspose.Words cho Java. Hãy tự do khám phá thêm các tùy chọn và tùy biến quy trình lưu tài liệu theo nhu cầu.

## Mã Nguồn Đầy Đủ Để Lưu Tài Liệu Dưới Định Dạng OOXML trong Aspose.Words cho Java

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

## Kết Luận

Trong hướng dẫn toàn diện này, chúng ta đã tìm hiểu cách **encrypt docx with password** và tinh chỉnh một loạt các tùy chọn lưu OOXML bằng Aspose.Words cho Java. Dù bạn cần bảo vệ nội dung mật, đáp ứng tiêu chuẩn ISO nghiêm ngặt, bảo tồn ký tự legacy, hay kiểm soát mức nén, thư viện cung cấp khả năng kiểm soát chi tiết thông qua cùng một API `OoxmlSaveOptions`.

## Câu Hỏi Thường Gặp

**H: Làm sao để bỏ bảo vệ mật khẩu khỏi tài liệu đã được bảo vệ bằng mật khẩu?**  
Đ: Mở tài liệu bằng mật khẩu đúng, sau đó lưu lại mà không gọi `setPassword`. Tệp mới sẽ không còn được bảo vệ.

**H: Tôi có thể đặt các thuộc tính tùy chỉnh khi lưu tài liệu ở định dạng OOXML không?**  
Đ: Có. Sử dụng `BuiltInDocumentProperties` hoặc `CustomDocumentProperties` trên đối tượng `Document` trước khi gọi `save`.

**H: Mức nén mặc định khi lưu tài liệu ở định dạng OOXML là gì?**  
Đ: Mặc định là `NORMAL`. Bạn có thể chuyển sang `SUPER_FAST` để tăng tốc hoặc `MAXIMUM` để giảm kích thước tệp.

**H: Các aspose words save options có hoạt động với các phiên bản Word cũ không?**  
Đ: Có. Bằng cách điều chỉnh `MsWordVersion` và các cài đặt tuân thủ, bạn có thể nhắm tới Word 2007‑2019 và đảm bảo tính tương thích.

**H: Có thể kết hợp nhiều tùy chọn lưu trong một thao tác duy nhất không?**  
Đ: Chắc chắn. Tạo một thể hiện `OoxmlSaveOptions`, thiết lập tất cả các thuộc tính mong muốn (mật khẩu, tuân thủ, nén, v.v.), và truyền nó vào `doc.save()`.

---

**Cập Nhật Lần Cuối:** 2025-12-29  
**Đã Kiểm Tra Với:** Aspose.Words cho Java 24.12  
**Tác Giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}