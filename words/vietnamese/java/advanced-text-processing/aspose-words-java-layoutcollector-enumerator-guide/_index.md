---
date: '2025-11-12'
description: Tìm hiểu cách sử dụng LayoutCollector và LayoutEnumerator của Aspose.Words
  for Java để xác định phạm vi trang, duyệt các thực thể bố cục và khởi động lại đánh
  số trang trong các phần liên tục.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: vi
title: 'Aspose.Words Java: Hướng dẫn LayoutCollector & LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Hướng dẫn LayoutCollector & LayoutEnumerator

## Giới thiệu  

Bạn có gặp khó khăn trong việc **xác định phạm vi trang**, phân tích phân trang, hoặc khởi động lại đánh số trang trong các tài liệu Java phức tạp không? Với **Aspose.Words for Java**, bạn có thể giải quyết những vấn đề này nhanh chóng bằng cách sử dụng `LayoutCollector` và `LayoutEnumerator`. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn **cách sử dụng LayoutCollector**, **cách duyệt LayoutEnumerator**, và cách kiểm soát đánh số trang trong các section liên tục — tất cả đều được minh họa bằng mã rõ ràng, từng bước mà bạn có thể chạy ngay hôm nay.

Bạn sẽ học được:

1. Sử dụng `LayoutCollector` để **xác định phạm vi trang** của bất kỳ node nào.  
2. **Duyệt các thực thể layout** bằng `LayoutEnumerator`.  
3. Triển khai callback layout cho việc render động.  
4. **Khởi động lại đánh số trang** trong các section liên tục.  

Hãy bắt đầu bằng cách đảm bảo môi trường của bạn đã sẵn sàng.

## Yêu cầu trước  

### Thư viện cần thiết  

> **Lưu ý:** Mã này hoạt động với phiên bản mới nhất của Aspose.Words for Java (không cần chỉ định số phiên bản).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Môi trường  

- JDK 17 trở lên.  
- IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE Java nào bạn ưa thích.  

### Kiến thức  

Bạn nên có kiến thức cơ bản về cú pháp Java và các khái niệm lập trình hướng đối tượng để theo dõi các ví dụ.

## Cài đặt Aspose.Words  

Đầu tiên, thêm thư viện Aspose.Words vào dự án và áp dụng giấy phép (hoặc dùng bản dùng thử). Đoạn mã dưới đây cho thấy cách tải giấy phép và xác nhận thư viện đã sẵn sàng:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Mẹo:** Đặt file giấy phép ra ngoài hệ thống kiểm soát phiên bản để bảo vệ thông tin xác thực của bạn.

Bây giờ chúng ta có thể đi sâu vào hai tính năng cốt lõi.

## 1. Cách sử dụng LayoutCollector để phân tích phạm vi trang  

`LayoutCollector` cho phép bạn **xác định phạm vi trang** cho bất kỳ node nào trong tài liệu, điều này rất quan trọng cho việc phân tích phân trang.

### Triển khai từng bước  

1. **Tạo một Document mới và một thể hiện LayoutCollector.**  
2. **Thêm nội dung trải dài trên nhiều trang.**  
3. **Cập nhật layout và truy vấn các chỉ số phạm vi trang.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Giải thích**

- `DocumentBuilder` chèn văn bản và ngắt trang, tạo ra một tài liệu tự nhiên trải qua nhiều trang.  
- `updatePageLayout()` buộc Aspose.Words tính toán layout, đảm bảo số trang chính xác.  
- `getNumPagesSpanned()` trả về tổng số trang mà node được cung cấp chiếm (ở đây là toàn bộ tài liệu).

## 2. Cách duyệt LayoutEnumerator  

`LayoutEnumerator` cung cấp một **cảnh quan có cấu trúc của các thực thể layout** (trang, đoạn văn, run, v.v.) và cho phép bạn di chuyển lên hoặc xuống qua chúng.

### Triển khai từng bước  

1. Tải một tài liệu hiện có có chứa các thực thể layout.  
2. Tạo một thể hiện `LayoutEnumerator`.  
3. Di chuyển tới mức trang, sau đó duyệt tiến và lùi bằng các phương thức trợ giúp.

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Lưu ý:** Các phương thức `traverseLayoutForward` và `traverseLayoutBackward` là các hàm đệ quy trợ giúp đi qua cây layout. Bạn có thể tùy chỉnh chúng để thu thập thông tin như hộp bao, chi tiết phông chữ, hoặc siêu dữ liệu tùy chỉnh.

## 3. Cách triển khai callback layout trang  

Đôi khi bạn cần phản hồi lại các sự kiện layout — ví dụ, khi một section hoàn thành việc reflow hoặc khi quá trình chuyển đổi sang định dạng khác kết thúc. Triển khai giao diện `IPageLayoutCallback` để nhận các thông báo này.

### Triển khai từng bước  

1. Đặt một instance callback vào tùy chọn layout của tài liệu.  
2. Định nghĩa logic callback để xử lý các sự kiện `PART_REFLOW_FINISHED` và `CONVERSION_FINISHED`.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Giải thích**

- `notify()` nhận mọi sự kiện layout. Chúng ta lọc ra những sự kiện cần quan tâm.  
- Khi một phần hoàn thành reflow, `renderPage()` lưu trang đó dưới dạng ảnh PNG.  

## 4. Cách khởi động lại đánh số trang trong các section liên tục  

Khi một tài liệu chứa các section liên tục, bạn có thể muốn đánh số trang chỉ khởi động lại khi xuất hiện một trang mới. Aspose.Words cho phép bạn kiểm soát điều này bằng `ContinuousSectionRestart`.

### Triển khai từng bước  

1. Tải tài liệu mục tiêu.  
2. Đặt tùy chọn `ContinuousSectionPageNumberingRestart`.  
3. Cập nhật layout để áp dụng thay đổi.

```java
// 1. Load the multi‑section document
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");

// 2. Configure page‑numbering restart behavior
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);

// 3. Update layout to reflect the new numbering scheme
doc.updatePageLayout();
System.out.println("Page numbering restart configured for continuous sections.");
```

**Giải thích**

- `FROM_NEW_PAGE_ONLY` chỉ ra cho Aspose.Words khởi động lại đánh số chỉ khi một trang vật lý mới xuất hiện, giữ cho luồng liên tục qua các section.

## Ứng dụng thực tiễn  

| Kịch bản | Tính năng hỗ trợ | Lợi ích |
|----------|------------------|---------|
| **Kiểm tra phân trang tài liệu** | `LayoutCollector` | Nhanh chóng tìm các section vượt quá trang. |
| **Render PDF với độ chính xác hình ảnh** | `LayoutEnumerator` + callbacks | Truy cập chi tiết layout để render chính xác. |
| **Tự động chèn watermark sau mỗi lần layout trang** | Callback layout trang | Phản hồi ngay khi một trang được layout. |
| **Tạo báo cáo đa section với đánh số tùy chỉnh** | Khởi động lại đánh số section liên tục | Duy trì đánh số trang chuyên nghiệp mà không cần chỉnh sửa thủ công. |

## Mẹo tối ưu hiệu năng  

- **Cắt bỏ các node không dùng** trước khi gọi `updatePageLayout()` để giảm tiêu thụ bộ nhớ.  
- **Tái sử dụng một LayoutCollector duy nhất** cho nhiều truy vấn thay vì tạo mới mỗi lần.  
- **Giới hạn độ sâu đệ quy** trong các hàm duyệt để tránh tràn stack khi xử lý tài liệu rất lớn.  

## Kết luận  

Bằng việc nắm vững **cách sử dụng LayoutCollector**, **cách duyệt LayoutEnumerator**, và **cách khởi động lại đánh số trang**, bạn đã sở hữu một bộ công cụ mạnh mẽ cho việc xử lý văn bản nâng cao với Aspose.Words for Java. Những kỹ thuật này cho phép bạn **xác định phạm vi trang**, **phân tích phân trang tài liệu**, và **kiểm soát hành vi layout** một cách tự tin. Áp dụng chúng vào các báo cáo, e‑book, hoặc bất kỳ quy trình tự động tạo tài liệu nào, bạn sẽ thấy sự cải thiện đáng kể về độ chính xác và năng suất.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}