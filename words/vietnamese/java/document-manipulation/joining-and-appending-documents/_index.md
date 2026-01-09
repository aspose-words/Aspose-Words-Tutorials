---
date: 2026-01-09
description: Tìm hiểu cách hợp nhất tài liệu với Aspose.Words cho Java đồng thời giữ
  nguyên định dạng, liên kết phần đầu và chân trang, và nhiều hơn nữa.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Cách hợp nhất tài liệu bằng Aspose.Words cho Java
url: /vi/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách hợp nhất tài liệu với Aspose.Words cho Java

Việc hợp nhất các tệp Word bằng chương trình có thể gây đau đầu—đặc biệt khi bạn cần giữ nguyên kiểu dáng, số trang và phần đầu/trang chân. Trong hướng dẫn này, bạn sẽ khám phá **cách hợp nhất tài liệu** bằng thư viện Aspose.Words for Java, từng bước một. Chúng tôi sẽ đề cập đến việc nối đơn giản, các tùy chọn nhập nâng cao, xử lý các bố cục trang khác nhau, và các mẹo bạn cần để **giữ nguyên định dạng khi hợp nhất** kết quả trong nhiều kịch bản thực tế.

## Câu trả lời nhanh
- **Cách dễ nhất để hợp nhất các tài liệu Word là gì?** Sử dụng `Document.appendDocument` với `ImportFormatMode.KEEP_SOURCE_FORMATTING`.  
- **Tôi có thể giữ nguyên kiểu dáng gốc của mỗi tệp nguồn không?** Có—đặt `ImportFormatMode.USE_DESTINATION_STYLES` hoặc bật Smart Style Behavior.  
- **Làm sao để giữ số trang đúng sau khi hợp nhất?** Chuyển đổi các trường `NUMPAGES` thành tham chiếu trang và gọi `updatePageLayout()`.  
- **Các phần đầu/trang chân có tự động liên kết không?** Bạn có thể liên kết hoặc hủy liên kết chúng bằng `linkToPrevious(true/false)`.  
- **Tôi cần gì trước khi bắt đầu?** Thêm Aspose.Words for Java vào dự án của bạn và chuẩn bị các tệp nguồn `.docx` sẵn sàng.

## Giới thiệu về việc ghép và nối tài liệu trong Aspose.Words for Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách ghép và nối tài liệu bằng thư viện Aspose.Words for Java. Bạn sẽ học cách hợp nhất nhiều tài liệu một cách liền mạch trong khi giữ nguyên định dạng và cấu trúc.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã cài đặt Aspose.Words for Java API trong dự án Java của mình.

## Các tùy chọn ghép tài liệu

### Nối đơn giản

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Nối với các tùy chọn Import Format

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Nối vào tài liệu trống

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Nối với chuyển đổi số trang

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Xử lý các bố cục trang khác nhau

Khi nối các tài liệu có bố cục trang khác nhau:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Ghép tài liệu với các kiểu dáng khác nhau

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Hành vi Smart Style

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Chèn tài liệu bằng DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Giữ đánh số nguồn

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Xử lý các Text Box

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Quản lý phần đầu và phần chân

### Liên kết phần đầu và phần chân

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Hủy liên kết phần đầu và phần chân

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Tại sao điều này quan trọng đối với các dự án “merge word documents java”

Khi bạn cần **merge word documents java**‑style, việc giữ nguyên giao diện và cảm giác của mỗi tệp là rất quan trọng đối với các quy trình pháp lý, xuất bản hoặc báo cáo. Sử dụng các kỹ thuật trên đảm bảo rằng:
* Kiểu dáng từ mỗi nguồn vẫn nguyên vẹn (hoặc được thống nhất, tùy thuộc vào lựa chọn của bạn).  
* Số trang và ngắt đoạn hoạt động một cách dự đoán được.  
* Phần đầu và phần chân có thể được liên kết hoặc giữ độc lập chỉ bằng một dòng lệnh.  

## Những khó khăn thường gặp & Mẹo

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|----------------|------------|
| Mất đánh số sau khi hợp nhất | `NUMPAGES` vẫn trỏ tới các phần gốc | Gọi `convertNumPageFieldsToPageRef` và `updatePageLayout()` |
| Xung đột kiểu dáng | Sử dụng `KEEP_SOURCE_FORMATTING` với các kiểu xung đột | Chuyển sang `USE_DESTINATION_STYLES` hoặc bật Smart Style Behavior |
| Xuất hiện các trang trắng | Giá trị `SectionStart` khác nhau | Đặt `SectionStart.CONTINUOUS` cho các phần nguồn trước khi nối |

## Câu hỏi thường gặp

**Q: Làm sao tôi có thể ghép các tài liệu có kiểu dáng khác nhau một cách liền mạch?**  
A: Sử dụng `ImportFormatMode.USE_DESTINATION_STYLES` khi nối, hoặc bật `SmartStyleBehavior` để hợp nhất thông minh hơn.

**Q: Tôi có thể giữ số trang khi nối các tài liệu không?**  
A: Có, chuyển đổi các trường `NUMPAGES` thành tham chiếu trang bằng `convertNumPageFieldsToPageRef` và sau đó gọi `updatePageLayout()`.

**Q: Smart Style Behavior là gì?**  
A: Nó tự động ánh xạ các kiểu nguồn sang kiểu đích khi có thể, giúp duy trì giao diện nhất quán trên nội dung đã hợp nhất.

**Q: Làm sao tôi xử lý các text box khi nối tài liệu?**  
A: Đặt `importFormatOptions.setIgnoreTextBoxes(false)` để các text box được giữ lại trong quá trình hợp nhất.

**Q: Nếu tôi muốn liên kết hoặc hủy liên kết phần đầu và phần chân giữa các tài liệu thì sao?**  
A: Sử dụng `linkToPrevious(true)` để liên kết, hoặc `linkToPrevious(false)` để giữ chúng riêng biệt trước khi gọi `appendDocument`.

## Kết luận

Aspose.Words for Java cung cấp các công cụ linh hoạt và mạnh mẽ cho **cách hợp nhất tài liệu**, dù bạn cần duy trì định dạng chính xác, xử lý các bố cục trang đa dạng, hoặc kiểm soát việc liên kết phần đầu/phần chân. Hãy thử nghiệm các đoạn mã trên để phù hợp với quy trình xử lý tài liệu của bạn, và bạn sẽ có thể **hợp nhất tài liệu Word kiểu java** một cách tự tin.

---

**Cập nhật lần cuối:** 2026-01-09  
**Kiểm tra với:** Aspose.Words for Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}