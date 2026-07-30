---
date: 2025-12-20
description: Tìm hiểu cách tải HTML và chuyển đổi HTML sang DOCX với Aspose.Words
  cho Java. Hướng dẫn từng bước cho thấy cách lưu tệp DOCX và sử dụng thẻ tài liệu
  có cấu trúc.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Cách tải HTML và lưu dưới dạng DOCX bằng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách tải HTML và lưu dưới dạng DOCX bằng Aspose.Words cho Java

## Giới thiệu về việc tải và lưu tài liệu HTML bằng Aspose.Words cho Java

Trong bài viết này, chúng ta sẽ khám phá **cách tải html** và lưu nó dưới dạng tệp DOCX bằng thư viện Aspose.Words cho Java. Aspose.Words là một API mạnh mẽ cho phép bạn thao tác các tài liệu Word một cách lập trình, và nó bao gồm hỗ trợ mạnh mẽ cho việc nhập/xuất HTML. Chúng tôi sẽ hướng dẫn toàn bộ quy trình, từ việc thiết lập các tùy chọn tải cho đến việc lưu kết quả dưới dạng tài liệu Word.

## Câu trả lời nhanh
- **Lớp chính để tải HTML là gì?** `Document` cùng với `HtmlLoadOptions`.
- **Tùy chọn nào cho phép Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Tôi có thể chuyển đổi HTML sang DOCX trong một bước không?** Có – tải HTML và gọi `doc.save(...".docx")`.
- **Tôi có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.
- **Yêu cầu phiên bản Java nào?** Java 8 hoặc cao hơn được hỗ trợ.

## “cách tải html” là gì trong ngữ cảnh của Aspose.Words?

Tải HTML có nghĩa là đọc một chuỗi hoặc tệp HTML và chuyển đổi nó thành một đối tượng `Document` của Aspose.Words. Đối tượng này sau đó có thể được chỉnh sửa, định dạng, hoặc lưu dưới bất kỳ định dạng nào được API hỗ trợ, chẳng hạn như DOCX, PDF hoặc RTF.

## Tại sao nên sử dụng Aspose.Words cho việc chuyển đổi HTML‑to‑DOCX?

- **Giữ nguyên bố cục** – bảng, danh sách và hình ảnh được giữ nguyên.
- **Hỗ trợ Structured Document Tags** – lý tưởng để tạo các content control trong Word.
- **Không cần Microsoft Office** – hoạt động trên bất kỳ máy chủ hoặc môi trường đám mây nào.
- **Hiệu suất cao** – xử lý các tệp HTML lớn một cách nhanh chóng.

## Yêu cầu trước

1. **Thư viện Aspose.Words cho Java** – tải xuống từ [here](https://releases.aspose.com/words/java/).
2. **Môi trường phát triển Java** – JDK 8+ đã được cài đặt và cấu hình.
3. **Kiến thức cơ bản về Java I/O** – chúng ta sẽ sử dụng `ByteArrayInputStream` để cung cấp chuỗi HTML.

## Cách tải tài liệu HTML

Dưới đây là một ví dụ ngắn gọn minh họa cách tải một đoạn HTML trong khi bật tính năng **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Giải thích**

- Chúng tôi tạo một chuỗi `HTML` chứa một điều khiển `<select>` đơn giản.
- `HtmlLoadOptions` cho phép chúng ta chỉ định cách HTML sẽ được diễn giải. Đặt loại điều khiển ưu tiên thành `STRUCTURED_DOCUMENT_TAG` cho Aspose.Words biết chuyển đổi các điều khiển form HTML thành các content control của Word.
- Hàm khởi tạo `Document` đọc HTML từ một `ByteArrayInputStream` sử dụng mã hoá UTF‑8.

## Cách lưu dưới dạng DOCX (Chuyển đổi HTML sang DOCX)

Khi HTML đã được tải vào một `Document`, việc lưu nó dưới dạng tệp DOCX trở nên đơn giản:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Thay thế `"Your Directory Path"` bằng thư mục thực tế nơi bạn muốn tệp đầu ra được tạo.

## Mã nguồn hoàn chỉnh cho việc tải và lưu tài liệu HTML

Dưới đây là ví dụ đầy đủ, sẵn sàng để chạy, kết hợp các bước tải và lưu. Bạn có thể sao chép và dán vào IDE của mình.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Những lỗi thường gặp & Mẹo

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|----------------|------------|
| **Thiếu phông chữ** | HTML tham chiếu các phông chữ chưa được cài đặt trên máy chủ. | Nhúng phông chữ vào DOCX bằng `FontSettings` hoặc đảm bảo các phông chữ cần thiết có sẵn. |
| **Hình ảnh không hiển thị** | Đường dẫn hình ảnh tương đối không thể được giải quyết. | Sử dụng URL tuyệt đối hoặc tải hình ảnh vào một `MemoryStream` và đặt `HtmlLoadOptions.setImageSavingCallback`. |
| **Loại điều khiển không được chuyển đổi** | `setPreferredControlType` chưa được đặt hoặc được đặt sai enum. | Xác nhận bạn đang sử dụng `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Vấn đề mã hoá** | Chuỗi HTML được mã hoá bằng một charset khác. | Luôn sử dụng `StandardCharsets.UTF_8` khi chuyển đổi chuỗi thành byte. |

## Câu hỏi thường gặp

### Làm thế nào để cài đặt Aspose.Words cho Java?

Aspose.Words cho Java có thể tải xuống từ [here](https://releases.aspose.com/words/java/). Thực hiện theo hướng dẫn cài đặt trên trang tải xuống để thêm các tệp JAR vào classpath của dự án.

### Tôi có thể tải các tài liệu HTML phức tạp bằng Aspose.Words không?

Có, Aspose.Words cho Java có thể xử lý HTML phức tạp, bao gồm các bảng lồng nhau, kiểu CSS và các phần tử tương tác không có JavaScript. Điều chỉnh `HtmlLoadOptions` (ví dụ, `setLoadImages` hoặc `setCssStyleSheetFileName`) để tinh chỉnh quá trình nhập.

### Các định dạng tài liệu khác mà Aspose.Words hỗ trợ là gì?

Aspose.Words hỗ trợ DOC, DOCX, RTF, HTML, PDF, EPUB, XPS và nhiều định dạng khác. API cung cấp việc lưu một dòng duy nhất sang bất kỳ định dạng nào trong số này.

### Aspose.Words có phù hợp cho tự động hoá tài liệu cấp doanh nghiệp không?

Chắc chắn. Nó được các doanh nghiệp lớn sử dụng cho việc tạo báo cáo tự động, chuyển đổi hàng loạt tài liệu, và xử lý tài liệu phía máy chủ mà không cần phụ thuộc vào Microsoft Office.

### Tôi có thể tìm tài liệu và ví dụ bổ sung cho Aspose.Words cho Java ở đâu?

Bạn có thể khám phá toàn bộ tham chiếu API và các hướng dẫn bổ sung trên trang tài liệu Aspose.Words cho Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Cập nhật lần cuối:** 2025-12-20  
**Đã kiểm tra với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất tại thời điểm viết)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}