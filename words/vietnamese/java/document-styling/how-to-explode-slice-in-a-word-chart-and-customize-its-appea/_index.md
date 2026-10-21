---
category: general
date: 2026-10-04
description: Tìm hiểu cách tách miếng trong biểu đồ Word, tách miếng biểu đồ tròn
  và thay đổi kích thước biểu đồ bánh donut bằng ví dụ Java từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: vi
lastmod: 2026-10-04
og_description: Cách tách miếng trong biểu đồ Word và tùy chỉnh biểu đồ tròn hoặc
  bánh donut bằng Java. Theo dõi ví dụ đầy đủ để chỉnh sửa biểu đồ trong Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Cách tách phần bánh trong biểu đồ Word – hướng dẫn Java đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Cách tách miếng trong biểu đồ Word và tùy chỉnh giao diện.
url: /vi/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách explode slice trong biểu đồ Word và tùy chỉnh giao diện

Nếu bạn cần **how to explode slice** trong một biểu đồ Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Dù bạn đang chuẩn bị một bài thuyết trình bán hàng hay một báo cáo tài chính, việc explode một lát biểu đồ tròn hoặc điều chỉnh lỗ của biểu đồ doughnut có thể làm nổi bật dữ liệu quan trọng nhất. Trong các phần tiếp theo, bạn cũng sẽ học cách **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, và **customize pie chart word** tài liệu bằng Aspose.Words for Java.

Bạn sẽ hoàn thành tutorial này với một chương trình Java hoàn chỉnh, sẵn sàng chạy, tải một tệp `.docx`, explode lát đầu tiên của biểu đồ pie, thay đổi kích thước lỗ doughnut, và lưu kết quả. Không cần script bên ngoài hay chỉnh sửa thủ công.

## Prerequisites

- Java 17 hoặc mới hơn được cài đặt trên máy phát triển của bạn.  
- Maven 3.6+ (hoặc Gradle) để quản lý các phụ thuộc.  
- Thư viện Aspose.Words for Java (bản dùng thử miễn phí hoạt động cho phát triển).  
- Một tài liệu Word (`input.docx`) chứa ít nhất một biểu đồ (pie hoặc doughnut).

## Step 1: Add Aspose.Words to your project

Nếu bạn dùng Maven, thêm phụ thuộc sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Đối với Gradle, đặt đoạn này vào `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Giữ phiên bản thư viện luôn cập nhật; các bản phát hành mới hơn bổ sung hỗ trợ cho các loại biểu đồ bổ sung và cải thiện hiệu năng.

## Step 2: Load the Word document that contains a chart

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** Tải tài liệu tạo ra một biểu diễn trong bộ nhớ mà Aspose.Words có thể duyệt. Nếu không có đối tượng này, bạn không thể truy cập các nút biểu đồ.

## Step 3: Retrieve the first chart in the document

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` bao phủ tất cả các đối tượng vẽ, bao gồm cả biểu đồ. Tham số `true` yêu cầu Aspose tìm kiếm đệ quy, đảm bảo biểu đồ đầu tiên được tìm thấy ngay cả khi nó nằm trong bảng.

## Step 4: Explode the first slice of a pie chart

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** Phương thức `setExplosion` nhận một giá trị số xác định khoảng cách lát di chuyển ra khỏi trung tâm. Giá trị `20` đủ để nhìn thấy mà không làm hỏng bố cục biểu đồ.

## Step 5: Adjust the doughnut hole size for a doughnut chart

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** Lỗ doughnut lớn hơn có thể cải thiện khả năng đọc khi bạn có nhiều điểm dữ liệu. Phương thức `setDoughnutHoleSize` yêu cầu một phần trăm (0‑100).

## Step 6: Save the modified document

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Expected output

- Lát đầu tiên của biểu đồ pie đầu tiên được dịch ra ngoài, làm nó nổi bật.  
- Nếu biểu đồ là doughnut, lỗ trung tâm mở rộng lên 40 % bán kính của biểu đồ.  
- Tệp kết quả `PieChart.docx` có thể mở trong Microsoft Word, LibreOffice, hoặc bất kỳ trình xem tương thích nào, hiển thị các thay đổi trực quan bạn đã áp dụng bằng chương trình.

## Full, runnable example

Dưới đây là toàn bộ chương trình trong một khối. Sao chép nó vào `ChartExploder.java`, điều chỉnh đường dẫn tệp, và chạy với `mvn compile exec:java` (hoặc cấu hình chạy của IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Running this code will **modify chart in Word**, **explode pie chart slice**, and **change doughnut chart size** automatically.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| *Nếu tài liệu chứa nhiều biểu đồ thì sao?* | Mẫu này nhắm vào biểu đồ **đầu tiên** (`NodeType.SHAPE, 0`). Để làm việc với các biểu đồ khác, thay đổi chỉ mục hoặc lặp qua `doc.getChildNodes(NodeType.SHAPE, true)` và lọc bằng `shape.getChart() != null`. |
| *Tôi có thể explode một lát khác ngoài lát đầu tiên không?* | Có. Truy cập series mong muốn qua `chart.getSeries().get(seriesIndex)` và gọi `setExplosion(value)`. Các chỉ mục bắt đầu từ 0. |
| *Điều này có hoạt động với các tệp Word 2007‑2021 không?* | Aspose.Words hỗ trợ các định dạng `.doc`, `.docx`, `.dot` và `.dotx`. Đoạn mã này hoạt động trên mọi phiên bản vì thư viện trừu tượng hoá định dạng tệp. |
| *Nếu biểu đồ là dạng cột hoặc đường thì sao?* | `setExplosion` và `setDoughnutHoleSize` chỉ áp dụng cho các biểu đồ loại pie. Mã sẽ bỏ qua các thao tác này một cách an toàn khi loại biểu đồ khác. |
| *Tôi có cần giấy phép cho Aspose.Words không?* | Giấy phép dùng thử miễn phí loại bỏ giới hạn 30 ngày nhưng sẽ thêm watermark. Đối với môi trường sản xuất, mua giấy phép để loại bỏ watermark và mở khóa đầy đủ tính năng. |

## Conclusion

Bạn đã biết **how to explode slice** trong một biểu đồ Word, cách **modify chart in Word**, và cách **change doughnut chart size** bằng Aspose.Words for Java. Ví dụ hoàn chỉnh minh họa toàn bộ quy trình—từ tải tài liệu, xác định biểu đồ, áp dụng các chỉnh sửa trực quan, đến lưu kết quả—để bạn có thể tích hợp các bước này vào bất kỳ pipeline báo cáo hoặc tạo tài liệu nào.

**Next steps**

- Khám phá các tùy chỉnh biểu đồ khác như thay đổi màu sắc, thêm nhãn dữ liệu, hoặc chuyển loại biểu đồ (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Kết hợp logic này với Aspose.PDF để tạo phiên bản PDF của cùng báo cáo.  
- Tự động hoá quy trình cho một loạt tài liệu bằng cách lặp qua các tệp trong thư mục.

Hãy thoải mái thử nghiệm với các giá trị explosion hoặc phần trăm lỗ doughnut khác nhau để phù hợp với hướng dẫn thiết kế của bạn. Chúc lập trình vui vẻ!

## What Should You Learn Next?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ẩn trục biểu đồ trong tài liệu Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Chèn biểu đồ bong bóng trong tài liệu Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}