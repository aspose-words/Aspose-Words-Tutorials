---
date: 2025-12-24
description: Tìm hiểu cách chuyển đổi Word sang RTF bằng Aspose.Words cho Java. Hướng
  dẫn từng bước này cho thấy cách tải một tệp DOCX, cấu hình các tùy chọn lưu RTF
  và lưu dưới dạng văn bản phong phú.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: Chuyển đổi Word sang RTF với Hướng dẫn Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển đổi Word sang RTF với Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ học **cách chuyển đổi Word sang RTF** một cách nhanh chóng và đáng tin cậy bằng Aspose.Words cho Java. Việc chuyển đổi một tệp DOCX sang định dạng RTF giàu định dạng là yêu cầu phổ biến khi bạn cần khả năng tương thích rộng rãi với các trình xử lý văn bản cổ điển, khách hàng email hoặc hệ thống lưu trữ tài liệu. Chúng ta sẽ đi qua việc tải tài liệu Word trong Java, tinh chỉnh các tùy chọn lưu RTF (bao gồm lưu hình ảnh dưới dạng WMF), và cuối cùng ghi tệp đầu ra.

## Câu trả lời nhanh
- **“convert word to rtf” có nghĩa là gì?** Nó chuyển đổi tệp DOCX/Word thành Rich Text Format trong khi giữ nguyên văn bản, kiểu dáng và tùy chọn hình ảnh.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt cho phát triển; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Phiên bản Java nào được hỗ trợ?** Aspose.Words cho Java hỗ trợ Java 8 trở lên.  
- **Có thể giữ lại hình ảnh khi chuyển đổi không?** Có – sử dụng tùy chọn `saveImagesAsWmf` để nhúng hình ảnh dưới dạng WMF trong RTF.  
- **Quá trình chuyển đổi mất bao lâu?** Thông thường dưới một giây cho các tài liệu tiêu chuẩn; các tệp lớn hơn có thể mất vài giây.

## “convert word to rtf” là gì?
Việc chuyển đổi một tài liệu Word sang RTF tạo ra một tệp độc lập nền tảng, lưu trữ văn bản, định dạng và tùy chọn hình ảnh trong một markup dạng văn bản thuần. Điều này cho phép tài liệu được xem trong hầu hết mọi trình xử lý văn bản mà không mất bố cục.

## Tại sao nên dùng Aspose.Words cho Java để lưu dưới dạng rich text?
- **Độ trung thực cao** – Tất cả các tính năng Word (kiểu dáng, bảng, header/footer) được giữ nguyên.  
- **Không cần Microsoft Office** – Hoạt động trên bất kỳ máy chủ hoặc môi trường đám mây nào.  
- **Kiểm soát chi tiết** – Các tùy chọn lưu cho phép bạn quyết định cách hình ảnh được lưu, mã hóa nào được dùng, và hơn thế nữa.

## Yêu cầu trước
1. **Thư viện Aspose.Words cho Java** – Tải về và thêm JAR vào dự án của bạn từ [đây](https://releases.aspose.com/words/java/).  
2. **Tệp Word nguồn** – Ví dụ, `Document.docx` mà bạn muốn lưu dưới dạng RTF.  
3. **Môi trường phát triển Java** – JDK 8+ và IDE yêu thích của bạn.

## Bước 1: Tải tài liệu Word (load word document java)
Đầu tiên, tải tệp DOCX hiện có vào một đối tượng `Document`. Đây là nền tảng cho mọi chuyển đổi.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **Mẹo:** Sử dụng đường dẫn tuyệt đối hoặc tài nguyên class‑path để tránh `FileNotFoundException`.

## Bước 2: Cấu hình tùy chọn lưu RTF (save images as wmf)
Aspose.Words cung cấp lớp `RtfSaveOptions` để tinh chỉnh đầu ra. Trong ví dụ này, chúng ta bật **lưu hình ảnh dưới dạng WMF**, định dạng được ưa chuộng cho các tệp RTF.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

Bạn cũng có thể điều chỉnh các cài đặt khác, chẳng hạn `saveOptions.setEncoding(Charset.forName("UTF-8"))` nếu cần một mã ký tự cụ thể.

## Bước 3: Lưu tài liệu dưới dạng RTF (save docx as rtf)
Bây giờ ghi tài liệu ra bằng các tùy chọn đã cấu hình. Bước này **lưu DOCX dưới dạng RTF**, tạo ra một tệp rich‑text sẵn sàng phân phối.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## Mã nguồn hoàn chỉnh để chuyển đổi Word sang RTF
Dưới đây là phiên bản ngắn gọn mà bạn có thể sao chép‑dán vào một lớp Java. Nó minh họa **lưu dưới dạng rich text** với tùy chọn hình ảnh WMF trong một khối duy nhất.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## Các lỗi thường gặp và cách khắc phục
| Vấn đề | Nguyên nhân | Giải pháp |
|-------|------------|-----------|
| RTF đầu ra trống | Không tìm thấy hoặc không tải được tệp nguồn | Kiểm tra lại đường dẫn trong `new Document(...)` |
| Thiếu hình ảnh | `saveImagesAsWmf` được đặt thành `false` | Bật `saveOptions.setSaveImagesAsWmf(true)` |
| Ký tự bị lỗi | Mã ký tự sai | Đặt `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## Câu hỏi thường gặp

**H: Làm sao để thay đổi các tùy chọn lưu RTF khác?**  
Đ: Sử dụng lớp `RtfSaveOptions` – nó cung cấp các thuộc tính cho nén, phông chữ và nhiều hơn nữa. Tham khảo tài liệu API Aspose.Words Java để biết danh sách đầy đủ.

**H: Có thể lưu tài liệu RTF với mã ký tự khác không?**  
Đ: Có. Gọi `saveOptions.setEncoding(Charset.forName("UTF-8"))` (hoặc bất kỳ charset nào được hỗ trợ) trước khi lưu.

**H: Có thể lưu tài liệu RTF mà không có hình ảnh không?**  
Đ: Chắc chắn. Đặt `saveOptions.setSaveImagesAsWmf(false)` để loại bỏ hình ảnh khỏi đầu ra.

**H: Làm sao xử lý ngoại lệ trong quá trình chuyển đổi?**  
Đ: Bao bọc các lệnh tải và lưu trong khối try‑catch bắt `Exception`. Ghi log lỗi và tùy chọn ném lại một ngoại lệ tùy chỉnh cho ứng dụng của bạn.

**H: Điều này có hoạt động với các tệp Word được bảo vệ bằng mật khẩu không?**  
Đ: Tải tài liệu bằng một đối tượng `LoadOptions` bao gồm mật khẩu, sau đó tiếp tục các bước lưu như bình thường.

## Kết luận
Bạn đã có một phương pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **chuyển đổi Word sang RTF** bằng Aspose.Words cho Java. Bằng cách tải DOCX, cấu hình `RtfSaveOptions` (bao gồm **lưu hình ảnh dưới dạng WMF**), và gọi `doc.save(...)`, bạn có thể tạo ra các tệp rich‑text chất lượng cao hoạt động ở mọi nơi. Hãy khám phá thêm các tùy chọn lưu để tùy chỉnh đầu ra theo nhu cầu chính xác của bạn.

---

**Cập nhật lần cuối:** 2025-12-24  
**Đã kiểm thử với:** Aspose.Words cho Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}