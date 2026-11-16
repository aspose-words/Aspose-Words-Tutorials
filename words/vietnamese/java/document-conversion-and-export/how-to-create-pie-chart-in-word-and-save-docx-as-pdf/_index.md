---
category: general
date: 2026-11-15
description: Học cách tạo biểu đồ tròn trong tài liệu Word và lưu file docx thành
  PDF bằng Java. Hướng dẫn này cũng đề cập đến việc chuyển đổi Word sang PDF và cách
  thêm biểu đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: vi
lastmod: 2026-11-15
og_description: Tạo biểu đồ tròn trong tệp Word và lưu docx dưới dạng PDF bằng Java.
  Hãy làm theo hướng dẫn từng bước này để chuyển đổi Word sang PDF và thêm biểu đồ.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Tạo biểu đồ tròn trong Word và lưu file docx thành PDF – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Cách tạo biểu đồ tròn trong Word và lưu file docx thành PDF
url: /vi/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ tròn trong Word và lưu docx thành PDF

Nếu bạn cần **create pie chart** trong một tài liệu Word và sau đó **save docx as PDF**, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, chuyển đổi tệp .docx sang PDF trong khi nhúng biểu đồ tròn, để bạn có thể trả lời “how to add chart” mà không phải tìm kiếm các đoạn mã rải rác.

Trong hướng dẫn này, bạn sẽ học:

* Tải một *.docx* hiện có (hoặc bắt đầu từ đầu)  
* Sử dụng Aspose.Words for Java để **create pie chart** và điền dữ liệu  
* **Save docx as PDF** với biểu đồ được hiển thị đúng  
* Hiểu các chi tiết của **convert word to pdf** khi có biểu đồ  

Các bước này hoạt động với Aspose.Words 2024‑x.x và Java 17, nhưng các khái niệm áp dụng cho bất kỳ thư viện nào hỗ trợ thao tác biểu đồ Word.

## Yêu cầu trước

| Yêu cầu | Lý do quan trọng |
|-------------|----------------|
| Java 17 (hoặc mới hơn) | Yêu cầu bởi JAR Aspose.Words mới nhất |
| Công cụ xây dựng Maven hoặc Gradle | Đơn giản hoá việc quản lý phụ thuộc |
| Aspose.Words for Java (phiên bản mới nhất) | Cung cấp các lớp `Document`, `Chart`, và `ChartType` |
| Tệp **.docx** đầu vào (hoặc tài liệu trống) | Biểu đồ sẽ được chèn vào tệp này |

Thêm phụ thuộc Aspose.Words vào `pom.xml` (Maven) hoặc `build.gradle` (Gradle) của bạn. Ví dụ cho Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Bước 1: Tải tài liệu Word (hoặc tạo mới)

Hành động đầu tiên là lấy một thể hiện `Document`. Nếu bạn đã có mẫu, truyền đường dẫn của nó; nếu không, tạo một tài liệu trống.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* Đối tượng `Document` là container cho tất cả nội dung Word, bao gồm cả biểu đồ. Tải một tệp hiện có cho phép bạn giữ lại văn bản và kiểu dáng xung quanh trong khi thêm một phần tử trực quan mới.

## Bước 2: **Create pie chart** – cốt lõi của “how to create chart”

Bây giờ chúng ta khởi tạo một đối tượng `Chart` với `ChartType.PIE`. Điều này tự động tạo một placeholder cho biểu đồ tròn mà bạn có thể điền dữ liệu sau này.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` cho Aspose.Words biết sử dụng mẫu biểu đồ tròn. Biểu đồ được thêm vào phần thân của tài liệu, vì vậy nó xuất hiện ở vị trí bạn cần. Điều này đáp ứng yêu cầu “how to add chart” trong một lần gọi.

## Bước 3: Điền dữ liệu vào biểu đồ – trả lời “how to add chart” bằng dữ liệu

Biểu đồ tròn không có ý nghĩa nếu không có dữ liệu series. Sử dụng bộ sưu tập `Series` để thêm các danh mục và giá trị.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: Mỗi lần gọi `add` tạo một phần của biểu đồ tròn. Đối số đầu tiên là nhãn, đối số thứ hai là giá trị số. Bạn có thể thay thế chúng bằng dữ liệu động từ cơ sở dữ liệu hoặc tệp CSV.

### Tùy chọn: Tùy chỉnh giao diện (không bắt buộc nhưng hữu ích)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Những điều chỉnh này minh họa cách bạn có thể **how to create chart** với giao diện chuyên nghiệp, mà không rời khỏi mã Java.

## Bước 4: **Save docx as PDF** – phần cuối của “convert word to pdf”

Sau khi biểu đồ được nhúng, xuất tài liệu ra PDF. Aspose.Words render biểu đồ dưới dạng đồ họa vector, giữ nguyên chất lượng.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: Phương thức `save` tự động chuyển đổi tệp Word sang PDF, xử lý raster hóa biểu đồ, nhúng phông chữ và bố cục trang. Điều này đáp ứng mục tiêu **save docx as pdf** và minh họa cách đáng tin cậy để **convert word to pdf** khi có biểu đồ.

### Kết quả mong đợi

Chạy chương trình sẽ tạo ra `output.pdf` chứa:

* Nội dung gốc của `input.docx` (nếu có)  
* Một biểu đồ tròn được render đầy đủ với tiêu đề *Sales Distribution Q1*  
* Tỷ lệ phần trăm các lát bánh chính xác khớp với dữ liệu (40 %, 30 %, 30 %)

Mở PDF bằng bất kỳ trình xem nào và bạn sẽ thấy một biểu đồ tròn sắc nét, giống hệt như trong tệp Word.

## Những lỗi thường gặp và cách tránh

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------|-----|
| Biểu đồ hiển thị trống trong PDF | Thiếu cài đặt phông chữ hoặc render biểu đồ | Đảm bảo bạn đang sử dụng phiên bản Aspose.Words mới nhất; nó bao gồm các thư viện render cần thiết. |
| Giá trị dữ liệu bị làm tròn không đúng | Sử dụng giá trị nguyên với số lớn | Cung cấp giá trị `double` hoặc chia tỉ lệ số trước khi thêm vào series. |
| PDF đầu ra quá lớn | Hình ảnh được nhúng ở DPI cao | Đặt `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` nếu bạn cũng nhúng hình ảnh. |
| “convert word to pdf” gây ra lỗi `UnsupportedOperationException` | Sử dụng phiên bản Java cũ (< 11) | Nâng cấp lên Java 17 hoặc mới hơn, mà Aspose.Words 24.x yêu cầu. |

## Mẹo chuyên nghiệp: Tái sử dụng logic tạo biểu đồ

Nếu bạn cần thêm nhiều biểu đồ vào cùng một tài liệu, hãy tách mã tạo biểu đồ ra thành một phương thức trợ giúp:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Bây giờ bạn có thể gọi `doc.getFirstSection().getBody().appendChild(createPieChart(...));` cho mỗi bộ dữ liệu, giữ cho mã của bạn DRY (Don’t Repeat Yourself).

## Kết luận

Bây giờ bạn đã biết cách **create pie chart** trong tài liệu Word, điền dữ liệu vào và **save docx as PDF** bằng Java. Ví dụ toàn diện này bao phủ toàn bộ quy trình **convert word to pdf**, trả lời **how to add chart**, và minh họa **how to create chart** một cách lập trình.

Từ đây bạn có thể khám phá:

* Thêm biểu đồ cột hoặc đường (`ChartType.BAR`, `ChartType.LINE`) – một trường hợp **how to create chart** khác.  
* Xuất ra các định dạng khác như PNG hoặc HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Tạo động tài liệu đầu vào với bảng hoặc placeholder trước khi chèn biểu đồ.

Hãy tự do thử nghiệm với các bộ dữ liệu khác nhau, các tùy chọn kiểu dáng, hoặc thậm chí nhúng nhiều biểu đồ trên một trang. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}