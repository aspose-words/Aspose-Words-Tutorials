---
category: general
date: 2026-11-15
description: Tìm hiểu cách thêm biểu đồ tròn vào tài liệu Word bằng Aspose.Words cho
  Java. Bao gồm chuyển đổi sang biểu đồ bánh donut, phần bánh tách ra, và mẫu mã đầy
  đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: vi
lastmod: 2026-11-15
og_description: Thêm biểu đồ tròn vào tài liệu Word bằng Aspose.Words cho Java. Bài
  hướng dẫn này chỉ cách tách một lát và chuyển biểu đồ thành dạng bánh donut.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Thêm biểu đồ tròn vào tài liệu Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Cách thêm biểu đồ tròn vào tài liệu Word bằng Java
url: /vi/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm biểu đồ tròn vào tài liệu Word – hướng dẫn đầy đủ cho Java

Nếu bạn cần **thêm biểu đồ tròn vào tài liệu Word** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Aspose.Words for Java. Bạn sẽ thấy toàn bộ quy trình: tải DOCX, tạo biểu đồ tròn, tách miếng đầu tiên ra, và chuyển biểu đồ thành dạng bánh donut bằng cách đặt kích thước lỗ.

Hướng dẫn cũng bao gồm các biến thể phổ biến — như thêm nhiều series, tùy chỉnh màu sắc, và xử lý tài liệu đã có sẵn biểu đồ — để bạn có thể áp dụng mã vào các dự án thực tế như báo cáo tự động hoặc bài thuyết trình động.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java 17 hoặc mới hơn (mã cũng biên dịch được với JDK 11+)
* Maven 3.6+ hoặc Gradle để quản lý phụ thuộc
* Giấy phép Aspose.Words for Java (bản dùng thử miễn phí đủ cho việc thử nghiệm)
* Kiến thức cơ bản về cú pháp Java và cấu trúc dự án Maven

## Bước 1: Thiết lập dự án Maven và nhập Aspose.Words

Tạo một dự án Maven mới (hoặc thêm vào dự án hiện có) và bao gồm phụ thuộc Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Nếu bạn dùng Gradle, mục tương đương là `implementation 'com.aspose:aspose-words:24.9'`.

Phụ thuộc này sẽ mang lại các lớp `Document`, `Chart`, và `ChartType` mà bạn cần để thao tác với biểu đồ.

## Bước 2: Tải tài liệu mục tiêu

Bạn có thể bắt đầu từ một tệp `.docx` đã có hoặc tạo một tài liệu trống mới. Ví dụ dưới đây tải mẫu có tên `input.docx` nằm trong thư mục `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Nếu tệp không tồn tại, Aspose.Words sẽ tự động tạo một tài liệu rỗng mới khi bạn gọi `new Document()` mà không chỉ định tên tệp.

## Bước 3: Tạo biểu đồ tròn và chèn vào tài liệu

Aspose.Words xem một biểu đồ như một shape có thể đặt ở bất kỳ vị trí nào mà một đoạn văn (paragraph) xuất hiện. Đoạn mã sau tạo một **biểu đồ tròn**, thêm một series dữ liệu duy nhất, và chèn biểu đồ sau đoạn văn đầu tiên.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Tại sao bước này quan trọng:**  
* `ChartType.PIE` báo cho Aspose.Words vẽ một biểu đồ tròn truyền thống.  
* Thêm series có cả nhãn danh mục và giá trị số sẽ tự động tạo các miếng bánh.  
* Chèn biểu đồ như một child của `Paragraph` giúp duy trì luồng tài liệu nguyên vẹn.

## Bước 4: Tách miếng đầu tiên để làm nổi bật

Một *miếng bánh tách ra* sẽ thu hút sự chú ý tới một điểm dữ liệu cụ thể. API cung cấp phương thức `setExplode(boolean)` trên đối tượng `ChartSeries`. Đặt nó cho series đầu tiên (chỉ số 0) sẽ làm miếng bánh đầu tiên bật ra.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Câu hỏi thường gặp:** *Nếu tôi có nhiều series thì sao?*  
> Bạn có thể chỉ định series cụ thể bằng chỉ số của nó, ví dụ `pieChart.getSeries().get(1).setExplode(true)` cho series thứ hai.

## Bước 5: Chuyển biểu đồ tròn thành bánh donut bằng cách đặt kích thước lỗ

Biểu đồ bánh donut thực chất là biểu đồ tròn có trung tâm rỗng. Aspose.Words cho phép bạn định nghĩa kích thước lỗ dưới dạng phần trăm của bán kính biểu đồ.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Phương thức `setHoleSize` chấp nhận giá trị từ **0** (biểu đồ tròn bình thường) đến **100** (hoàn toàn rỗng). Giá trị khoảng **30‑40** sẽ cho ra một bánh donut cân đối về mặt hình ảnh.

## Bước 6: Lưu và kiểm tra kết quả

Sau khi thực hiện tất cả các thay đổi, lưu tài liệu. Dòng lệnh dưới đây ghi tệp vào thư mục `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Kết quả mong đợi

Mở `final-pie-doughnut.docx` trong Microsoft Word:

* Một biểu đồ bánh donut xuất hiện ở vị trí đoạn văn đầu tiên.
* Miếng “Apples” được tách ra (cách một chút so với các miếng còn lại).
* Biểu đồ hiển thị bốn miếng với nhãn *Apples*, *Bananas*, *Cherries*, *Dates* cùng phần trăm bạn đã cung cấp.

Nếu bạn muốn xuất ra PDF, chỉ cần đổi `SaveFormat` thành `SaveFormat.PDF`.

## Xử lý các trường hợp đặc biệt và biến thể

### Thêm nhiều series

Nếu bạn cần nhiều series (ví dụ: bánh donut chồng), hãy thêm chúng tuần tự:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Màu sắc tùy chỉnh

Bạn có thể gán màu cho mỗi miếng bánh qua `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Làm việc với biểu đồ đã tồn tại

Nếu tài liệu đã chứa một biểu đồ và bạn chỉ muốn chỉnh sửa nó, hãy tìm shape biểu đồ:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Xử lý giấy phép

Aspose.Words yêu cầu giấy phép để sử dụng trong môi trường sản xuất. Đặt tệp `Aspose.Words.lic` của bạn vào classpath và tải nó khi ứng dụng khởi động:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Nếu không thiết lập giấy phép, tài liệu sẽ có watermark.

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là lớp Java hoàn chỉnh tích hợp mọi bước đã thảo luận. Sao chép vào `src/main/java/com/example/AddPieChart.java` và chạy `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Chạy chương trình sẽ tạo ra biểu đồ bánh donut như đã mô tả ở trên. Điều chỉnh `categories`, `values`, hoặc `holeSize` cho phù hợp với dữ liệu của bạn.

## Kết luận

Bây giờ bạn đã biết cách **thêm biểu đồ tròn vào tài liệu Word** bằng Java và Aspose.Words. Hướng dẫn đã bao gồm tải tài liệu, tạo biểu đồ tròn, tách miếng, chuyển biểu đồ thành bánh donut, và xử lý các biến thể phổ biến như nhiều series, màu sắc tùy chỉnh, và biểu đồ đã tồn tại. Với nền tảng này, bạn có thể xây dựng công cụ báo cáo tự động, tạo bài thuyết trình động, hoặc nhúng trực quan phong phú ngay trong các tệp Word.

### Những gì bạn có thể khám phá tiếp theo

* **add bar chart to Word document** – các bước tương tự nhưng dùng `ChartType.BAR`.  
* **customize chart legends and titles** – dùng `pieChart.getTitle().setText("...")` và `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **export the Word document as PDF** – đổi `SaveFormat` thành `PDF` để tạo tệp sẵn sàng phân phối.  
* **populate chart data from a database** – thay thế mảng tĩnh bằng kết quả truy vấn JDBC.

Hãy thoải mái thử nghiệm các loại biểu đồ, nguồn dữ liệu và tùy chọn định dạng khác nhau. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây liên quan chặt chẽ tới các kỹ thuật đã trình bày trong bài viết này. Mỗi tài nguyên đều bao gồm mã nguồn đầy đủ và giải thích chi tiết từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}