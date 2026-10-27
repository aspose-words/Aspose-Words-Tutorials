---
category: general
date: 2026-08-07
description: Cách tách miếng bánh pie trong Java bằng Aspose.Words. Tìm hiểu cách
  thêm đường dẫn tới bánh pie, tạo biểu đồ Word và tùy chỉnh các miếng bánh pie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: vi
lastmod: 2026-08-07
og_description: Cách tách miếng bánh pie trong Java với Aspose.Words. Hướng dẫn này
  chỉ cho bạn cách thêm đường dẫn vào biểu đồ bánh, tạo biểu đồ Word và tùy chỉnh
  các miếng bánh pie để đạt hiệu quả hình ảnh rõ ràng.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Cách tách miếng bánh tròn trong Java – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Cách tách miếng bánh tròn trong Java – Hướng dẫn biểu đồ Aspose.Words
url: /vi/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách làm nổ miếng bánh pie trong Java – Hướng dẫn biểu đồ Aspose.Words

Nếu bạn cần biết **cách làm nổ miếng bánh pie** trong tài liệu Word bằng Java, hướng dẫn này sẽ cung cấp cho bạn mọi thứ. Chúng tôi cũng sẽ chỉ cho bạn **cách thêm các đường dẫn (leader lines) vào biểu đồ pie**, **java create word chart** objects, và **tùy chỉnh các miếng bánh pie** để có kết quả hoàn hảo. Khi kết thúc hướng dẫn, bạn sẽ có một ví dụ đầy đủ, có thể chạy được mà bạn có thể đưa vào bất kỳ dự án Java nào.

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Yêu cầu trước

* Java Development Kit (JDK) 8 hoặc cao hơn.
* Maven hoặc Gradle để quản lý phụ thuộc.
* Giấy phép Aspose.Words cho Java (bản dùng thử miễn phí phù hợp cho mục đích học tập).
* Kiến thức cơ bản về cú pháp Java và các khái niệm hướng đối tượng.

> **Mẹo:** Mặc dù Aspose.Words cung cấp bản dùng thử miễn phí, việc mua giấy phép sẽ loại bỏ dấu watermark đánh giá khỏi các tài liệu được tạo.

## Nội dung hướng dẫn này

* Tạo một tài liệu Word mới từ đầu.  
* Chèn một **biểu đồ pie** bằng cách sử dụng `DocumentBuilder`.  
* **Làm nổ một miếng bánh pie** để làm nổi bật một điểm dữ liệu.  
* **Thêm các đường dẫn (leader lines) vào pie** để nhãn rõ ràng hơn.  
* Tùy chỉnh giao diện của miếng bánh, như màu sắc và viền.  
* Lưu tài liệu vào đĩa và xác minh kết quả.

---

## Cách làm nổ miếng bánh pie với Aspose.Words trong Java

Bước đầu tiên là thiết lập đối tượng biểu đồ và làm nổ miếng bánh mong muốn. Aspose.Words cung cấp biểu đồ thông qua lớp `Shape`, và mỗi miếng bánh là một `ChartPoint`. Bằng cách đặt thuộc tính `Explosion` bạn kiểm soát khoảng cách mà miếng bánh di chuyển ra ngoài.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Tại sao nó hoạt động:**  
`setExplosion(20)` cho phép engine biểu đồ dịch miếng bánh ra 20 điểm so với trung tâm của biểu đồ. Giá trị này là tương đối; số lớn hơn tạo hiệu ứng ấn tượng hơn. Bạn có thể làm nổ bất kỳ miếng bánh nào bằng cách thay đổi chỉ mục (`get(1)`, `get(2)`, …).

## Thêm các đường dẫn (leader lines) vào pie để nhãn rõ ràng hơn

Các đường dẫn (leader lines) kết nối nhãn của một miếng bánh với cạnh của nó, điều này đặc biệt hữu ích khi các miếng bánh bị nổ ra hoặc khi biểu đồ chứa nhiều phần nhỏ. Lệnh `setLeaderLines(true)` bật tính năng này cho toàn bộ series.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Tại sao bạn cần các đường dẫn:**  
Khi một miếng bánh bị nổ, nhãn mặc định có thể chồng lên các yếu tố khác. Các đường dẫn giúp nhãn dễ đọc bằng cách vẽ một đường ngắn từ miếng bánh tới hộp văn bản.

## Java tạo biểu đồ Word – chèn series dữ liệu

Một biểu đồ không có dữ liệu không hữu ích. Bạn phải điền series với các danh mục và giá trị. Dưới đây chúng tôi thêm ba danh mục đại diện cho thị phần.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Giải thích:**  
`ChartSeries` chứa cả các danh mục (tên miếng bánh) và các giá trị số. Bật `ShowCategoryName` và `ShowPercentage` làm cho biểu đồ tự giải thích, kết hợp tốt với các đường dẫn chúng tôi đã thêm ở trên.

## Tùy chỉnh các miếng bánh pie vượt qua việc nổ

Ngoài việc nổ một miếng bánh, bạn thường muốn điều chỉnh màu sắc, viền, hoặc thậm chí ẩn một miếng bánh hoàn toàn. Đoạn mã dưới đây minh họa ba tùy chỉnh phổ biến:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Tại sao tùy chỉnh các miếng bánh:**  
Màu tùy chỉnh giúp biểu đồ phù hợp với thương hiệu công ty, trong khi viền cải thiện khả năng đọc trên trang in. Ẩn một miếng bánh hữu ích khi bạn muốn giữ nguyên mô hình dữ liệu nhưng tạm thời loại bỏ một danh mục khỏi đầu ra trực quan.

## Lưu tài liệu và xác minh kết quả

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể mở file `.docx` đã tạo trong Microsoft Word, LibreOffice, hoặc bất kỳ trình xem nào hỗ trợ định dạng này.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Kết quả mong đợi:**  
Khi bạn mở `PieChartDemo.docx`, bạn sẽ thấy một biểu đồ pie trong đó miếng bánh đầu tiên (Product A) được nổ ra ngoài, các đường dẫn chỉ từ mỗi miếng bánh tới nhãn của nó, và các miếng bánh hiển thị màu xanh lá, xanh dương và cam tùy chỉnh. Miếng bánh bị ẩn (Product C) sẽ không hiển thị, nhưng các phần trăm vẫn cộng lại thành 100 % vì dữ liệu vẫn còn trong series của biểu đồ.

---

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy sau khi thêm phụ thuộc Aspose.Words vào dự án của mình.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Phụ thuộc (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cách tải tài liệu Word với Aspose.Words Java: Hướng dẫn toàn diện](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}