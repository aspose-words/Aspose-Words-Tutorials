---
category: general
date: 2026-11-22
description: Tạo biểu đồ tròn trong Java và học cách thiết lập kích thước biểu đồ,
  thêm nhãn dữ liệu, hiển thị phần trăm, và xoay lát đầu tiên để tạo hiệu quả hình
  ảnh rõ ràng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: vi
lastmod: 2026-11-22
og_description: Tạo biểu đồ tròn trong Java, sau đó đặt kích thước biểu đồ, hiển thị
  phần trăm trên nhãn dữ liệu và xoay lát cắt đầu tiên — tất cả trong một ví dụ có
  thể chạy được.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Tạo biểu đồ tròn với kích thước tùy chỉnh, nhãn và xoay trong Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Tạo biểu đồ tròn với kích thước tùy chỉnh, nhãn dữ liệu và xoay trong Java
url: /vi/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo biểu đồ tròn với kích thước tùy chỉnh, nhãn dữ liệu và xoay trong Java

Nếu bạn cần **create pie chart** trong Java, hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình. Bạn sẽ học cách **set chart size**, bật **show percentages pie chart**, thêm **data labels pie chart**, và **rotate pie chart slice** để lát cắt đầu tiên bắt đầu ở góc 45 độ.

Ví dụ sử dụng **Aspose.Slides for Java**, một thư viện được sử dụng rộng rãi để thao tác các tệp PowerPoint. Các khái niệm tương tự áp dụng cho các thư viện vẽ biểu đồ khác; chỉ cần thay thế các lời gọi API bằng các tương đương trong bộ công cụ của bạn.

## Yêu cầu trước

* Java 17 hoặc mới hơn đã được cài đặt  
* Maven 3.8+ (hoặc Gradle) để quản lý phụ thuộc  
* Hiểu biết cơ bản về cú pháp Java  
* Truy cập vào binary của Aspose.Slides for Java (bạn có thể lấy bản dùng thử miễn phí từ trang chính thức)

Thêm phụ thuộc vào tệp `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Tạo biểu đồ tròn – ví dụ đầy đủ

Chương trình sau tạo một slide PowerPoint chứa biểu đồ tròn với kích thước tùy chỉnh, nhãn dữ liệu phần trăm, và lát cắt đầu tiên được xoay.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Tại sao mỗi bước lại quan trọng

| Bước | Mục đích | Cách nó liên quan tới các từ khóa |
|------|----------|-----------------------------------|
| **Insert chart** | **Create pie chart** – đối tượng cốt lõi sẽ hiển thị hình ảnh. | Thỏa mãn trực tiếp yêu cầu *create pie chart*. |
| **Set dimensions** | Lệnh `addChart(..., 400, 300)` minh họa **set chart size**. | Kiểm soát chiều rộng (400 px) và chiều cao (300 px). |
| **Show percentages** | `setShowPercentage(true)` làm cho biểu đồ **show percentages pie chart** trên mỗi lát cắt. | Người dùng thường cần phần trăm thay vì giá trị thô. |
| **Add data labels** | Cấu hình `DataLabelFormat` thêm **data labels pie chart** với độ hiển thị mong muốn. | Nhãn cải thiện khả năng đọc và có thể tùy chỉnh. |
| **Rotate slice** | `setFirstSliceAngle(45)` xoay biểu đồ sao cho lát cắt đầu tiên bắt đầu ở góc 45 độ, đáp ứng **rotate pie chart slice**. | Tăng cường nhấn mạnh trực quan cho một lát cắt cụ thể. |

## Phân tích từng bước

### 1. Chèn biểu đồ tròn và đặt kích thước biểu đồ

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Phương thức `addChart` tạo biểu đồ và đồng thời **set chart size** thành 400 × 300 điểm.*  
Nếu bạn cần kích thước khác, hãy điều chỉnh hai đối số cuối cùng.

### 2. Điền dữ liệu vào biểu đồ

Bản demo thêm ba danh mục và một chuỗi duy nhất. Thay thế các số được mã hoá sẵn bằng dữ liệu từ cơ sở dữ liệu, CSV, hoặc đầu vào người dùng khi cần.

### 3. Hiển thị phần trăm trên mỗi lát cắt

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Kích hoạt `setShowPercentage(true)` đảm bảo biểu đồ **show percentages pie chart** tự động tính phần trăm của mỗi lát cắt so với tổng.*

### 4. Thêm nhãn dữ liệu chi tiết

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Bạn có thể bật/tắt các tùy chọn nhãn khác (`setShowValue`, `setShowSeriesName`, v.v.) để tùy chỉnh trải nghiệm **add data labels pie chart**.

### 5. Xoay lát cắt đầu tiên

```java
chart.setFirstSliceAngle(45);
```

*Gọi `setFirstSliceAngle(45)` **rotate pie chart slice** để đoạn đầu tiên bắt đầu ở góc 45 độ, làm cho nó nổi bật.*

### 6. Lưu và xem kết quả

Chạy chương trình sẽ tạo ra `output/PieChartDemo.pptx`. Mở nó trong PowerPoint hoặc bất kỳ trình xem tương thích nào để xem biểu đồ tròn cuối cùng:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Ảnh chụp màn hình của biểu đồ tròn đã tạo với kích thước tùy chỉnh, nhãn phần trăm và lát cắt đầu tiên đã xoay"}

Hình ảnh trên minh họa kết quả **create pie chart**, xác nhận rằng kích thước, nhãn, phần trăm và việc xoay đã được áp dụng đúng.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Điều chỉnh |
|-----------|------------|
| **Kích thước biểu đồ khác nhau** | Thay đổi các tham số chiều rộng/chiều cao trong `addChart`. |
| **Nhiều chuỗi** | Thêm các đối tượng `IChartSeries` bổ sung; mỗi chuỗi có thể có cài đặt nhãn riêng. |
| **Định dạng nhãn tùy chỉnh** | Sử dụng `series.getDataLabelFormat().setNumberFormat("0.0%")` để kiểm soát số chữ số thập phân. |
| **Xoay sang góc khác** | Truyền bất kỳ số nguyên nào (0‑360) vào `setFirstSliceAngle`. |
| **Xuất dưới dạng hình ảnh** | Sau khi lưu, gọi `chart.writeAsSvg(outPath)` hoặc `chart.writeAsPng(outPath)` để có phiên bản raster. |

> **Mẹo chuyên nghiệp:** Nếu bạn dự định tạo nhiều biểu đồ trong một vòng lặp, hãy tái sử dụng cùng một đối tượng `Presentation` và chỉ thay thế dữ liệu biểu đồ. Điều này giảm tải bộ nhớ và tăng tốc xử lý.

## Kết luận

Bây giờ bạn đã biết cách **create pie chart** trong Java, **set chart size**, bật **show percentages pie chart**, **add data labels pie chart**, và **rotate pie chart slice** để nhấn mạnh trực quan tốt hơn. Ví dụ hoàn chỉnh, có thể chạy được minh họa mọi bước từ khởi tạo đến lưu tệp PowerPoint cuối cùng.

### Tiếp theo là gì?

* Khám phá các loại biểu đồ khác (Bar, Line, Area) bằng cách sử dụng cùng enum `ChartType`.  
* Kết hợp nhiều biểu đồ trên một slide để tạo bảng điều khiển.  
* Xuất biểu đồ ra PNG hoặc SVG để sử dụng trong các ứng dụng web.  

Bạn có thể thoải mái thử nghiệm màu sắc, chú giải và hiệu ứng hoạt hình—các biểu đồ dữ liệu của bạn chỉ bị giới hạn bởi trí tưởng tượng. Chúc bạn vẽ biểu đồ vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [cách chèn biểu đồ tròn trong Word – thêm nhãn dữ liệu phần trăm](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Cách tách lát cắt biểu đồ tròn trong Java – hướng dẫn biểu đồ Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Chèn biểu đồ tròn trong Java – Tách, Xoay & Đánh dấu các lát cắt](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}