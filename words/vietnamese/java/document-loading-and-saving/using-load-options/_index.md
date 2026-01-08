---
date: 2025-12-27
description: Tìm hiểu cách thiết lập LoadOptions trong Aspose.Words cho Java, bao
  gồm cách chỉ định thư mục tạm, đặt phiên bản Word, chuyển đổi metafile sang PNG
  và chuyển đổi hình dạng thành công thức toán học để xử lý tài liệu linh hoạt.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Cách thiết lập LoadOptions trong Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt LoadOptions trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ đi qua **cách đặt LoadOptions** cho nhiều kịch bản thực tế khi làm việc với Aspose.Words cho Java. LoadOptions cho phép bạn kiểm soát chi tiết cách một tài liệu được mở — dù bạn cần cập nhật các trường bẩn, làm việc với tệp được mã hoá, chuyển đổi hình dạng sang Office Math, hay chỉ định thư mục tạm thời để lưu dữ liệu. Khi kết thúc, bạn sẽ có thể tùy chỉnh hành vi tải để phù hợp chính xác với yêu cầu của ứng dụng.

## Trả Lời Nhanh
- **LoadOptions là gì?** Một đối tượng cấu hình ảnh hưởng đến cách Aspose.Words tải tài liệu.  
- **Tôi có thể cập nhật các trường khi tải không?** Có — đặt `setUpdateDirtyFields(true)`.  
- **Làm sao mở tệp được bảo vệ bằng mật khẩu?** Truyền mật khẩu vào hàm khởi tạo `LoadOptions`.  
- **Có thể thay đổi thư mục tạm không?** Sử dụng `setTempFolder("path")`.  
- **Phương thức nào chuyển đổi hình dạng sang Office Math?** `setConvertShapeToOfficeMath(true)`.

## Tại Sao Nên Sử Dụng LoadOptions?
LoadOptions giúp bạn tránh các bước xử lý sau khi tải, giảm mức tiêu thụ bộ nhớ, và đảm bảo tài liệu được diễn giải chính xác như bạn mong muốn. Ví dụ, chuyển đổi metafile sang PNG trong quá trình tải ngăn ngừa các vấn đề raster hoá sau này, và chỉ định phiên bản MS Word giúp duy trì độ chính xác bố cục khi làm việc với các tệp cũ.

## Điều Kiện Tiên Quyết
- Java 17 trở lên  
- Aspose.Words cho Java (phiên bản mới nhất)  
- Giấy phép Aspose hợp lệ cho môi trường sản xuất  

## Hướng Dẫn Từng Bước

### Cập Nhật Các Trường Bẩn

Khi tài liệu chứa các trường đã được chỉnh sửa nhưng chưa được làm mới, bạn có thể yêu cầu Aspose.Words tự động cập nhật chúng trong quá trình tải.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Lệnh `setUpdateDirtyFields(true)` đảm bảo bất kỳ trường bẩn nào sẽ được tính lại ngay khi tài liệu được mở.*

### Tải Tài Liệu Được Mã Hoá

Nếu tệp nguồn của bạn được bảo vệ bằng mật khẩu, cung cấp mật khẩu khi tạo instance `LoadOptions`. Bạn cũng có thể đặt mật khẩu mới khi lưu sang định dạng khác.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Chuyển Đổi Hình Dạng Sang Office Math

Một số tài liệu cũ lưu công thức dưới dạng hình vẽ. Bật tùy chọn này sẽ chuyển các hình dạng đó thành các đối tượng Office Math gốc, dễ chỉnh sửa hơn sau này.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Đặt Phiên Bản MS Word

Xác định phiên bản Word mục tiêu giúp thư viện chọn đúng quy tắc render, đặc biệt khi làm việc với các định dạng tệp cũ.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Sử Dụng Thư Mục Tạm Thời

Các tài liệu lớn có thể tạo ra các tệp tạm thời (ví dụ, khi trích xuất hình ảnh). Bạn có thể chỉ định các tệp này vào một thư mục tùy chọn, rất hữu ích trong môi trường sandbox.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback Cảnh Báo

Trong quá trình tải, Aspose.Words có thể phát sinh các cảnh báo (ví dụ, tính năng không được hỗ trợ). Việc triển khai callback cho phép bạn ghi log hoặc phản hồi lại các sự kiện này.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Chuyển Đổi Metafile Sang PNG

Các metafile như WMF có thể được raster hoá thành PNG trong quá trình tải, đảm bảo việc render nhất quán trên mọi nền tảng.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Mã Nguồn Hoàn Chỉnh Để Làm Việc Với Load Options trong Aspose.Words cho Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Các Trường Hợp Sử Dụng Thông Thường & Mẹo

- **Đường ống chuyển đổi hàng loạt** – Kết hợp `setTempFolder` với một công việc định kỳ để xử lý hàng trăm tệp mà không làm đầy thư mục tạm hệ thống.  
- **Di chuyển tài liệu cũ** – Sử dụng `setMswVersion` cùng với `setConvertShapeToOfficeMath` để đưa các tài liệu kỹ thuật cũ vào định dạng hiện đại mà vẫn giữ nguyên các công thức.  
- **Xử lý tài liệu an toàn** – Kết hợp `loadEncryptedDocument` với `OdtSaveOptions` để mã hoá lại tệp bằng mật khẩu mới trong một định dạng khác.  

## Câu Hỏi Thường Gặp

**H: Làm sao tôi có thể xử lý cảnh báo trong quá trình tải tài liệu?**  
Đ: Triển khai một `IWarningCallback` tùy chỉnh (như trong ví dụ *Callback Cảnh Báo*) và đăng ký nó qua `loadOptions.setWarningCallback(...)`. Điều này cho phép bạn ghi log, bỏ qua, hoặc hủy quá trình dựa trên mức độ nghiêm trọng của cảnh báo.

**H: Tôi có thể chuyển đổi các hình dạng sang đối tượng Office Math khi tải tài liệu không?**  
Đ: Có — gọi `loadOptions.setConvertShapeToOfficeMath(true)` trước khi khởi tạo `Document`. Thư viện sẽ tự động thay thế các hình dạng tương thích bằng các đối tượng Office Math gốc.

**H: Làm sao chỉ định phiên bản MS Word cho quá trình tải tài liệu?**  
Đ: Sử dụng `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (hoặc bất kỳ giá trị enum nào khác) để thông báo cho Aspose.Words quy tắc render của phiên bản Word nào cần áp dụng.

**H: Mục đích của phương thức `setTempFolder` trong LoadOptions là gì?**  
Đ: Nó chỉ định tất cả các tệp tạm thời được tạo ra trong quá trình tải (như hình ảnh được trích xuất) sẽ được lưu vào thư mục bạn kiểm soát, rất quan trọng đối với môi trường có giới hạn thư mục tạm hệ thống.

**H: Có thể chuyển đổi các metafile như WMF sang PNG trong quá trình tải không?**  
Đ: Hoàn toàn có thể — bật tùy chọn này bằng `loadOptions.setConvertMetafilesToPng(true)`. Điều này đảm bảo các ảnh raster được lưu dưới dạng PNG, tăng khả năng tương thích với các trình xem hiện đại.

## Kết Luận

Chúng ta đã khám phá các kỹ thuật thiết yếu để **đặt LoadOptions** trong Aspose.Words cho Java, từ việc cập nhật các trường bẩn đến xử lý tệp được mã hoá, chuyển đổi hình dạng, chỉ định phiên bản Word, chỉ định lưu trữ tạm thời, và hơn thế nữa. Khi tận dụng những tùy chọn này, bạn có thể xây dựng các đường ống xử lý tài liệu mạnh mẽ, hiệu suất cao, thích ứng với đa dạng các kịch bản đầu vào.

---

**Cập Nhật Lần Cuối:** 2025-12-27  
**Đã Kiểm Tra Với:** Aspose.Words cho Java 24.11  
**Tác Giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}