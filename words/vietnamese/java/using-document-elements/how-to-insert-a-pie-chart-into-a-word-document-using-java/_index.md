---
category: general
date: 2026-09-27
description: Tìm hiểu cách chèn biểu đồ tròn vào tài liệu Word bằng Java, tạo biểu
  đồ tròn trong Word và hiển thị phần trăm trên biểu đồ tròn để có cái nhìn dữ liệu
  rõ ràng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: vi
lastmod: 2026-09-27
og_description: Cách chèn biểu đồ tròn vào tài liệu Word bằng Java. Hướng dẫn này
  chỉ cho bạn cách tạo biểu đồ tròn trong Word, hiển thị phần trăm trên biểu đồ và
  thêm các đường dẫn.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Cách chèn biểu đồ tròn vào tài liệu Word bằng Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Cách chèn biểu đồ tròn vào tài liệu Word bằng Java
url: /vi/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn biểu đồ tròn vào tài liệu Word bằng Java

Nếu bạn cần **cách chèn biểu đồ tròn** vào một tệp Word, hướng dẫn này sẽ đưa bạn qua toàn bộ quy trình. Bạn sẽ thấy cách **tạo biểu đồ tròn trong Word**, hiển thị phần trăm trên mỗi miếng bánh, và thêm các đường dẫn (leader lines) để có giao diện chuyên nghiệp.

Tự động hoá Word thường cảm giác nặng nề, nhưng với Aspose.Words for Java bạn có thể tạo các tài liệu được định dạng đầy đủ một cách lập trình. Khi kết thúc tutorial này, bạn sẽ có một đoạn mã Java có thể chạy được, tạo ra một tài liệu Word chứa biểu đồ tròn đã được định dạng.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

- Java 17 hoặc mới hơn được cài đặt
- Maven hoặc Gradle để quản lý phụ thuộc
- Aspose.Words for Java (phiên bản 23.11 hoặc mới hơn) đã được thêm vào dự án
- Kiến thức cơ bản về cú pháp Java

Bạn không cần kinh nghiệm trước với API biểu đồ; các bước dưới đây sẽ bao phủ mọi thứ từ thiết lập dự án đến đầu ra cuối cùng.

## Bước 1: Thiết lập phụ thuộc Maven

Thêm thư viện Aspose.Words vào `pom.xml` của bạn. Phụ thuộc duy nhất này cung cấp quyền truy cập vào `Document`, `DocumentBuilder`, và các lớp biểu đồ.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Nếu bạn dùng Gradle, tương đương là:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Mẹo:** Sử dụng phiên bản ổn định mới nhất để được hưởng các bản sửa lỗi và tính năng biểu đồ mới.

## Bước 2: Tạo tài liệu mới và một builder

Đối tượng `Document` đại diện cho tệp Word, trong khi `DocumentBuilder` cho phép bạn chèn nội dung. Đây là nền tảng cho **thêm biểu đồ vào tài liệu word**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder hiện đã sẵn sàng để đặt các đối tượng ở bất kỳ vị trí nào trong tài liệu.

## Bước 3: Chèn một biểu đồ tròn

Aspose.Words hỗ trợ nhiều loại biểu đồ; chúng ta chọn `ChartType.PIE`. Kích thước được biểu thị bằng điểm (1 point = 1/72 inch).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Ở giai đoạn này, biểu đồ chứa một series dữ liệu mặc định với các giá trị placeholder. Bạn có thể thay thế các giá trị này sau nếu cần.

## Bước 4: Truy cập series của biểu đồ

Biểu đồ tròn có một series duy nhất chứa các giá trị của các miếng bánh. Lấy nó ra để áp dụng định dạng.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Bước 5: Tách (explode) miếng bánh đầu tiên

Tách một miếng bánh sẽ thu hút sự chú ý tới một điểm dữ liệu cụ thể. Đây là một dấu hiệu trực quan phổ biến khi bạn muốn làm nổi bật một chỉ số quan trọng.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Bước 6: Hiển thị phần trăm trên mỗi miếng bánh

Hiển thị phần trăm trực tiếp trên biểu đồ giúp cải thiện khả năng hiểu dữ liệu. Điều này đáp ứng yêu cầu **hiển thị phần trăm trên biểu đồ tròn**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Bước 7: Thêm các đường dẫn (leader lines) cho nhãn rõ ràng hơn

Các đường dẫn kết nối nhãn của miếng bánh với phần tương ứng, loại bỏ sự mơ hồ. Điều này thực hiện **cách thêm các đường dẫn**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Bước 8: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ thư mục nào mà bạn có quyền ghi.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Chạy chương trình sẽ tạo ra `output/PieFormatted.docx`. Mở tệp trong Microsoft Word, bạn sẽ thấy một biểu đồ tròn trong đó:

- Miếng bánh đầu tiên được tách ra.
- Mỗi miếng bánh hiển thị giá trị phần trăm của nó.
- Các đường dẫn chỉ từ phần trăm tới các miếng bánh tương ứng.

### Kết quả mong đợi

![Biểu đồ tròn đã định dạng trong Word](/images/pie-formatted.png){: .center-image alt="Biểu đồ tròn đã định dạng được chèn vào tài liệu Word"}

Ảnh chụp màn hình (văn bản alt sử dụng từ khóa chính) minh họa giao diện cuối cùng: một biểu đồ tròn sạch sẽ, dựa trên dữ liệu, sẵn sàng cho báo cáo, đề xuất hoặc bảng điều khiển.

## Các biến thể phổ biến và trường hợp đặc biệt

### Thay đổi giá trị miếng bánh

Nếu bạn cần dữ liệu tùy chỉnh, thay thế các giá trị series mặc định bằng:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Nhiều series (biểu đồ donut)

Mặc dù biểu đồ tròn đơn giản chỉ có một series, Aspose.Words cũng hỗ trợ biểu đồ donut với nhiều series. Đổi `ChartType.PIE` thành `ChartType.DONUT` và lặp lại các bước cấu hình series.

### Xuất ra PDF

Nếu quy trình downstream của bạn yêu cầu PDF, gọi `doc.save("output/PieFormatted.pdf");` sau khi biểu đồ đã được tạo. Bố cục hình ảnh vẫn giữ nguyên.

## Danh sách mã nguồn đầy đủ

Dưới đây là tệp Java hoàn chỉnh, tự chứa, bạn có thể sao chép‑dán vào IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Biên dịch và chạy chương trình bằng `mvn compile exec:java -Dexec.mainClass=PieChartExample` (hoặc lệnh Gradle tương đương). Tệp Word được tạo sẽ chứa biểu đồ tròn đã được định dạng hoàn chỉnh.

## Kết luận

Bây giờ bạn đã biết **cách chèn biểu đồ tròn** vào tài liệu Word bằng Java, **cách tạo biểu đồ tròn trong Word**, **cách hiển thị phần trăm trên biểu đồ tròn**, và **cách thêm biểu đồ vào tài liệu word** với các đường dẫn. Ví dụ hoàn chỉnh minh họa từng bước, giải thích lý do viết mã như vậy, và cung cấp các mẹo tùy chỉnh.

Tiếp theo, bạn có thể khám phá:

- Thêm nhãn dữ liệu với phông chữ tùy chỉnh (**các biến thể hiển thị phần trăm trên biểu đồ tròn**)
- Kết hợp nhiều biểu đồ trong một tài liệu duy nhất (**thêm biểu đồ vào tài liệu word**)
- Tự động hoá việc tạo báo cáo với bảng và biểu đồ đồng thời

Hãy thoải mái thử nghiệm màu sắc, thứ tự miếng bánh, hoặc xuất ra PDF. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}