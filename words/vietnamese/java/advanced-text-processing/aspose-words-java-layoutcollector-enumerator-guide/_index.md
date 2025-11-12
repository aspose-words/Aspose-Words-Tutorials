---
date: '2025-11-12'
description: Tìm hiểu cách sử dụng LayoutCollector và LayoutEnumerator của Aspose.Words
  cho Java để phân tích phân trang, duyệt bố cục tài liệu, triển khai các callback
  bố cục và khởi động lại đánh số trang trong các phần liên tục.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: vi
title: Phân tích phân trang Java với Công cụ Bố cục Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Phân tích Phân trang Java với Aspose.Words Layout Tools

## Giới thiệu  

Nếu bạn cần **phân tích phân trang** hoặc **duyệt bố cục tài liệu** trong một ứng dụng Java, Aspose.Words for Java cung cấp cho bạn hai API mạnh mẽ: **`LayoutCollector`** và **`LayoutEnumerator`**. Các lớp này cho phép bạn biết một nút chiếm bao nhiêu trang, duyệt qua mọi thực thể bố cục, phản hồi các sự kiện bố cục, và thậm chí khởi động lại đánh số trang trong các phần liên tục. Trong hướng dẫn này, chúng tôi sẽ đi qua từng tính năng từng bước, trình bày các đoạn mã thực tế, và giải thích kết quả mong đợi để bạn có thể áp dụng ngay lập tức.

Bạn sẽ học cách:

* **sử dụng LayoutCollector** để lấy trang bắt đầu và kết thúc của bất kỳ nút nào (use layoutcollector page span)  
* **duyệt bố cục tài liệu** với LayoutEnumerator (traverse document layout)  
* **triển khai callback bố cục** để phản hồi các sự kiện phân trang (implement layout callback)  
* **khởi động lại đánh số trang** trong các phần liên tục (restart page numbering sections)  

Hãy bắt đầu.

## Yêu cầu trước  

### Thư viện bắt buộc  

| Công cụ xây dựng | Phụ thuộc |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Lưu ý:** Số phiên bản được giữ lại để tương thích; đoạn mã hoạt động với bất kỳ bản phát hành Aspose.Words for Java gần đây nào.

### Môi trường  

* JDK 8 hoặc mới hơn  
* Một IDE như IntelliJ IDEA hoặc Eclipse  

### Kiến thức  

Kiến thức cơ bản về lập trình Java và quen thuộc với Maven/Gradle là đủ để theo dõi các ví dụ.

## Cài đặt Aspose.Words  

Trước khi bạn có thể gọi bất kỳ API bố cục nào, thư viện phải được cấp phép (hoặc sử dụng ở chế độ dùng thử). Đoạn mã dưới đây cho thấy cách khởi tạo tối thiểu:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Đoạn mã không thay đổi bất kỳ tài liệu nào; nó chỉ chuẩn bị môi trường Aspose.*  

Bây giờ chúng ta có thể đi sâu vào các tính năng cốt lõi.

## Tính năng 1: Sử dụng **LayoutCollector** để Phân tích Phân trang  

`LayoutCollector` ánh xạ mỗi nút trong một `Document` tới các trang mà nó chiếm. Đây là cách đáng tin cậy nhất để **use layoutcollector page span** cho việc phân tích phân trang.

### Triển khai từng bước  

1. **Tạo một tài liệu mới và gắn LayoutCollector.**  
2. **Chèn nội dung gây ra phân trang** (ví dụ: ngắt trang, ngắt phần).  
3. **Làm mới bố cục** bằng `updatePageLayout()`.  
4. **Truy vấn collector** để lấy trang bắt đầu, trang kết thúc, và tổng số trang chiếm.

#### 1️⃣ Khởi tạo Document và LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Điền nội dung vào Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Cập nhật Layout và Lấy các chỉ số  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Kết quả mong đợi**

```
Document spans 5 pages.
```

> **Tại sao nó hoạt động:** `updatePageLayout()` buộc Aspose.Words tính lại bố cục, sau đó `LayoutCollector` có thể báo cáo chính xác phạm vi trang.

## Tính năng 2: Duyệt Bố cục Tài liệu với **LayoutEnumerator**  

Khi bạn cần **traverse document layout** (ví dụ: để render tùy chỉnh hoặc phân tích), `LayoutEnumerator` cung cấp một dạng cây của các trang, đoạn văn, dòng và từ.

### Triển khai từng bước  

1. Tải một tài liệu hiện có có chứa các thực thể bố cục.  
2. Tạo một thể hiện `LayoutEnumerator`.  
3. Di chuyển tới thực thể gốc `PAGE`.  
4. Duyệt bố cục theo chiều tiến và lùi bằng các phương thức trợ giúp đệ quy.

#### 1️⃣ Tải Document và Tạo Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Đặt vị trí ở mức Page  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Duyệt Tiến (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Duyệt Lùi  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Các phương thức trợ giúp** (`traverseLayoutForward` / `traverseLayoutBackward`) được triển khai đệ quy để thăm mọi thực thể con và in ra loại và chỉ số trang của chúng. Bạn có thể điều chỉnh chúng để thu thập thống kê, render đồ họa, hoặc thay đổi thuộc tính bố cục.

## Tính năng 3: Triển khai **Layout Callbacks**  

Đôi khi bạn cần phản hồi khi Aspose.Words hoàn thành việc bố trí một phần tài liệu. Việc triển khai `IPageLayoutCallback` cho phép bạn **implement layout callback** logic như lưu mỗi trang dưới dạng hình ảnh.

### Triển khai từng bước  

1. Gán một thể hiện callback cho `LayoutOptions` của tài liệu.  
2. Trong callback, xử lý các sự kiện `PART_REFLOW_FINISHED` và `CONVERSION_FINISHED`.  
3. Render trang hiện tại ra PNG bằng `ImageSaveOptions`.

#### 1️⃣ Đăng ký Callback  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Lớp Callback  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**Điều gì xảy ra:** Mỗi khi một phần bố cục hoàn thành việc reflow, callback sẽ render trang đó ra file PNG, cung cấp cho bạn một dấu vết hình ảnh của quá trình phân trang.

## Tính năng 4: Khởi động lại Đánh số Trang trong **Continuous Sections**  

Khi một tài liệu chứa các phần liên tục, bạn có thể muốn số trang chỉ khởi động lại trên một trang vật lý mới. Điều này được thực hiện bằng cài đặt `ContinuousSectionRestart`.

### Triển khai từng bước  

1. Tải tài liệu mục tiêu.  
2. Thay đổi tùy chọn `ContinuousSectionPageNumberingRestart`.  
3. Chạy lại `updatePageLayout()` để áp dụng thay đổi.

#### 1️⃣ Tải Document  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Cấu hình Hành vi Khởi động lại  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Kết quả:** Số trang bây giờ sẽ chỉ khởi động lại khi một trang vật lý mới bắt đầu, giữ cho báo cáo hoặc sách của bạn trông gọn gàng, chuyên nghiệp.

## Ứng dụng Thực tiễn  

| Kịch bản | API nào hỗ trợ | Lợi ích |
|----------|----------------|---------|
| **Kiểm toán hợp đồng dài** | `LayoutCollector` | Nhanh chóng tìm ra các điều khoản trải dài trên nhiều trang. |
| **Render PDF tùy chỉnh** | `LayoutEnumerator` | Duyệt cây bố cục để xuất mỗi dòng dưới dạng đồ họa vector. |
| **Xem trước tài liệu trực tiếp** | Layout callbacks | Tạo ảnh trang ngay khi người dùng chỉnh sửa nội dung. |
| **Báo cáo đa phần** | Continuous section restart | Giữ số trang hợp lý mà không cần điều chỉnh thủ công. |

## Mẹo Tối ưu Hiệu suất  

* **Cắt bỏ các nút không dùng** trước khi gọi `updatePageLayout()` – ít phần tử hơn đồng nghĩa với phân trang nhanh hơn.  
* **Tái sử dụng một LayoutCollector duy nhất** cho nhiều truy vấn thay vì tạo mới mỗi lần.  
* **Giới hạn độ sâu duyệt** khi dùng LayoutEnumerator nếu bạn chỉ cần dữ liệu ở mức trang.  
* **Giải phóng các stream** (như trong ví dụ callback) để tránh rò rỉ bộ nhớ trên tài liệu lớn.

## Kết luận  

Bằng cách thành thạo `LayoutCollector`, `LayoutEnumerator`, các callback bố cục, và đánh số lại trong các phần liên tục, bạn đã có một bộ công cụ hoàn chỉnh để **analyze pagination java**, **traverse document layout**, và **restart page numbering sections**. Những API này cho phép bạn xây dựng các pipeline xử lý văn bản mạnh mẽ, hiệu suất cao và luôn mang lại kết quả chuyên nghiệp.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}