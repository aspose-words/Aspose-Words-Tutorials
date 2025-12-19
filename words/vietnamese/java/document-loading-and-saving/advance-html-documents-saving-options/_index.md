---
date: 2025-12-19
description: Tìm hiểu cách xuất HTML với Aspose.Words Java, bao gồm các tùy chọn nâng
  cao để lưu Word dưới dạng HTML và chuyển đổi Word sang HTML một cách hiệu quả.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Cách xuất HTML với Aspose.Words Java: Các tùy chọn nâng cao'
url: /vi/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách xuất HTML với Aspose.Words Java: Các tùy chọn nâng cao

Trong hướng dẫn này, bạn sẽ khám phá **cách xuất HTML** từ tài liệu Word bằng Aspose.Words cho Java. Dù bạn cần **lưu Word dưới dạng HTML** để xuất bản trên web hay **chuyển đổi Word sang HTML** để xử lý tiếp theo, các tùy chọn lưu nâng cao cho phép bạn kiểm soát chi tiết đầu ra. Chúng tôi sẽ hướng dẫn từng tùy chọn một cách từng bước, giải thích khi nào nên sử dụng và đưa ra các kịch bản thực tế nơi các cài đặt này tạo ra sự khác biệt.

## Trả lời nhanh
- **Lớp chính để xuất HTML là gì?** `HtmlSaveOptions`  
- **Có thể nhúng phông chữ trực tiếp trong HTML không?** Có, đặt `exportFontsAsBase64` thành `true`.  
- **Làm sao để giữ dữ liệu vòng‑đi chuyển Word‑đặc thù?** Bật `exportRoundtripInformation`.  
- **Định dạng nào là tốt nhất cho đồ họa vector?** Sử dụng `convertMetafilesToSvg` để xuất SVG.  
- **Có thể tránh xung đột tên lớp CSS không?** Có, sử dụng `addCssClassNamePrefix`.

## 1. Giới thiệu
Aspose.Words cho Java là một API mạnh mẽ cho phép các nhà phát triển thao tác tài liệu Word một cách lập trình. Hướng dẫn này tập trung vào các tùy chọn lưu tài liệu HTML nâng cao, giúp bạn tùy chỉnh quá trình chuyển đổi để đáp ứng các yêu cầu web hoặc tích hợp cụ thể.

## 2. Xuất thông tin vòng‑đi chuyển (Roundtrip Information)
Việc bảo tồn thông tin vòng‑đi chuyển cho phép bạn chuyển đổi HTML trở lại tài liệu Word mà không mất chi tiết bố cục hoặc định dạng.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Khi nào nên sử dụng
- Khi bạn cần một quy trình chuyển đổi có thể đảo ngược (HTML → Word → HTML).  
- Thích hợp cho các kịch bản chỉnh sửa cộng tác, nơi cấu trúc Word gốc phải được giữ lại.

## 3. Xuất phông chữ dưới dạng Base64
Nhúng phông chữ trực tiếp vào HTML loại bỏ phụ thuộc vào phông chữ bên ngoài và đảm bảo độ chính xác hình ảnh trên mọi trình duyệt.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Mẹo chuyên nghiệp
Sử dụng tùy chọn này khi môi trường đích có hạn chế truy cập tài nguyên bên ngoài (ví dụ: bản tin email).

## 4. Xuất tài nguyên
Kiểm soát cách CSS và tài nguyên phông chữ được phát ra, và chỉ định thư mục hoặc bí danh URL tùy chỉnh cho các tài sản đó.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Tại sao quan trọng
Tách CSS ra thành tệp riêng giảm kích thước HTML và cho phép bộ nhớ đệm, giúp tải trang nhanh hơn.

## 5. Chuyển đổi Metafile sang EMF hoặc WMF
Metafile (ví dụ: EMF/WMF) được chuyển đổi sang định dạng mà trình duyệt có thể hiển thị một cách đáng tin cậy.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Trường hợp sử dụng
Chọn EMF/WMF khi các trình duyệt mục tiêu hỗ trợ các định dạng vector này và bạn cần khả năng phóng to không mất chất lượng.

## 6. Chuyển đổi Metafile sang SVG
SVG cung cấp khả năng mở rộng tốt nhất và được hỗ trợ rộng rãi trên các trình duyệt hiện đại.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### Lợi ích
Tệp SVG nhẹ và giữ độ phân giải độc lập, hoàn hảo cho thiết kế web đáp ứng.

## 7. Thêm tiền tố cho tên lớp CSS
Ngăn ngừa xung đột kiểu bằng cách thêm tiền tố vào tất cả các tên lớp CSS được tạo.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Mẹo thực tiễn
Sử dụng một tiền tố duy nhất (ví dụ: tên dự án của bạn) khi nhúng HTML vào các trang hiện có để tránh xung đột CSS.

## 8. Xuất URL CID cho tài nguyên MHTML
Khi lưu dưới dạng MHTML, bạn có thể xuất tài nguyên bằng URL Content‑ID để tăng khả năng tương thích email.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### Khi nào nên sử dụng
Thích hợp cho việc tạo một tệp HTML duy nhất, tự chứa, có thể đính kèm vào email.

## 9. Giải quyết tên phông chữ
Đảm bảo HTML tham chiếu đúng họ phông chữ, cải thiện tính nhất quán đa nền tảng.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### Tại sao hữu ích
Nếu tài liệu gốc sử dụng phông chữ không được cài đặt trên máy khách, tùy chọn này sẽ thay thế chúng bằng các phông chữ an toàn cho web.

## 10. Xuất trường biểu mẫu nhập văn bản dưới dạng văn bản
Hiển thị trường biểu mẫu dưới dạng văn bản thuần thay vì các phần tử nhập HTML tương tác.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Trường hợp sử dụng
Khi bạn cần một biểu diễn chỉ đọc của biểu mẫu để lưu trữ hoặc in ấn.

## Các lỗi thường gặp & Khắc phục
| Vấn đề | Nguyên nhân thường gặp | Cách khắc phục |
|-------|------------------------|----------------|
| Phông chữ thiếu trong đầu ra | `exportFontsAsBase64` chưa được bật | Đặt `setExportFontsAsBase64(true)` |
| CSS bị hỏng sau khi nhúng | Sử dụng `EXTERNAL` mà không cung cấp tệp CSS | Đảm bảo tệp CSS được triển khai tại `resourceFolderAlias` đã chỉ định |
| Kích thước HTML lớn | Nhúng nhiều hình ảnh dưới dạng Base64 | Chuyển sang tài nguyên ảnh bên ngoài bằng `setExportFontResources(true)` và cấu hình `resourceFolder` |
| SVG không hiển thị trên trình duyệt cũ | Trình duyệt không hỗ trợ SVG | Cung cấp ảnh PNG dự phòng bằng cách cũng xuất dưới dạng EMF/WMF |

## Câu hỏi thường gặp

**H: Tôi có thể vừa nhúng phông chữ dưới dạng Base64 vừa giữ CSS bên ngoài không?**  
Đ: Có. Đặt `exportFontsAsBase64(true)` đồng thời giữ `CssStyleSheetType.EXTERNAL` để tách dữ liệu phông chữ khỏi quy tắc kiểu.

**H: Làm sao chuyển lại HTML hiện có thành tài liệu Word?**  
Đ: Tải HTML bằng `Document doc = new Document("input.html");` rồi `doc.save("output.docx");`. Bảo tồn dữ liệu vòng‑đi chuyển bằng cách bật `exportRoundtripInformation` trong quá trình xuất ban đầu.

**H: Việc chuyển đổi sang SVG có ảnh hưởng tới hiệu năng không?**  
Đ: Chuyển đổi các metafile lớn sang SVG có thể tăng thời gian xử lý, nhưng HTML tạo ra thường nhỏ hơn và render nhanh hơn trên trình duyệt.

**H: Các tùy chọn này có hoạt động với Aspose.Words cho .NET không?**  
Đ: Các khái niệm tương tự tồn tại trong API .NET, mặc dù tên phương thức có thể hơi khác (ví dụ: `HtmlSaveOptions` được chia sẻ giữa các nền tảng).

**H: Tôi nên chọn tùy chọn nào cho HTML thân thiện với email?**  
Đ: Sử dụng `SaveFormat.MHTML` cùng `exportCidUrlsForMhtmlResources` để nhúng tất cả tài nguyên trực tiếp vào phần thân email.

---

**Cập nhật lần cuối:** 2025-12-19  
**Đã kiểm tra với:** Aspose.Words cho Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}