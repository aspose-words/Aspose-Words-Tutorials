---
category: general
date: 2026-09-27
description: Tạo biểu đồ dạng radial trong Java và chèn biểu đồ vào Word. Tìm hiểu
  cách đặt kích thước biểu đồ, thêm chuỗi dữ liệu và tạo tài liệu Word trống.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: vi
lastmod: 2026-09-27
og_description: Tạo biểu đồ dạng tròn trong Java, sau đó chèn biểu đồ vào Word. Hướng
  dẫn này chỉ cách thiết lập kích thước biểu đồ, thêm chuỗi dữ liệu và tạo một tài
  liệu Word trống.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Tạo biểu đồ dạng tròn và chèn biểu đồ vào Word bằng Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Tạo biểu đồ tròn và chèn biểu đồ vào Word bằng Java
url: /vi/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo biểu đồ radial và chèn biểu đồ vào Word bằng Java

Nếu bạn cần **create radial chart** trong một tệp Word bằng Java, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy cách **insert chart into Word**, thiết lập kích thước biểu đồ, và tạo một **blank Word document** từ đầu.

Chúng tôi sẽ hướng dẫn qua từng bước cần thiết, từ việc khởi tạo tài liệu đến việc thêm một series dữ liệu và lưu file `.docx` cuối cùng. Khi hoàn thành, bạn sẽ có một tệp Word hoạt động đầy đủ chứa biểu đồ radial, và bạn sẽ hiểu **how to set chart size** và **add data series chart** cho các tùy chỉnh trong tương lai.

## Yêu cầu trước

* Java 17 hoặc mới hơn (mã sẽ biên dịch với bất kỳ JDK hiện đại nào)
* Aspose.Words for Java 24.9 hoặc mới hơn – phương thức `setShowGraduations` chỉ có từ phiên bản này
* Một IDE hoặc công cụ xây dựng (Maven/Gradle) có thể bao gồm JAR Aspose.Words
* Kiến thức cơ bản về cú pháp Java và quản lý phụ thuộc Maven/Gradle

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng Maven, thêm đoạn sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Bước 1: Tạo một tài liệu Word trống

Một tài liệu trống là nền mà biểu đồ sẽ được đặt. Lớp `Document` đại diện cho toàn bộ tệp `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Tạo một tài liệu trống đảm bảo không có nội dung đã tồn tại gây cản trở bố cục biểu đồ.

## Bước 2: Khởi tạo DocumentBuilder

`DocumentBuilder` cung cấp các phương thức tiện lợi để chèn đối tượng, văn bản và các yếu tố khác vào tài liệu.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder sẽ được sử dụng sau này để **insert chart into Word**.

## Bước 3: Xây dựng biểu đồ radial

Aspose.Words hỗ trợ nhiều loại biểu đồ; `ChartType.RADIAL` tạo một biểu đồ radial (polar).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Tại thời điểm này, biểu đồ đã tồn tại nhưng chưa có dữ liệu, kích thước hoặc tùy chọn hiển thị.

## Bước 4: Thêm series dữ liệu vào biểu đồ

Một biểu đồ không có series dữ liệu sẽ trống. Phương thức `add` nhận tên series và một mảng các giá trị.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Bạn có thể thêm nhiều series bằng cách gọi `add` liên tục. Điều này đáp ứng yêu cầu **add data series chart**.

## Bước 5: Bật graduations (tùy chọn)

Graduations là các đường lưới radial giúp cải thiện khả năng đọc. Chúng chỉ có từ phiên bản 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Nếu bạn sử dụng phiên bản Aspose.Words cũ hơn, dòng này sẽ gây ra ngoại lệ—vì vậy hãy kiểm tra phiên bản thư viện của bạn trước.

## Bước 6: Đặt kích thước biểu đồ

Kiểm soát kích thước biểu đồ cho phép bạn đặt nó vừa vặn trong lề trang. Điều này đáp ứng **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Bạn có thể điều chỉnh giá trị chiều rộng và chiều cao để phù hợp với nhu cầu bố cục. Hãy nhớ rằng 1 point ≈ 1/72 inch.

## Bước 7: Chèn biểu đồ vào tài liệu Word

Bây giờ biểu đồ đã sẵn sàng để được đặt. Phương thức `insertChart` của `DocumentBuilder` xử lý việc chèn.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Đây là phần cốt lõi của thao tác **insert chart into word**.

## Bước 8: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Tệp sẽ chứa biểu đồ radial bạn vừa tạo.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Chạy chương trình sẽ tạo ra `RadialChart.docx` trong thư mục làm việc của dự án. Mở tệp trong Microsoft Word sẽ hiển thị một biểu đồ radial với ba điểm dữ liệu và các graduations hiển thị.

### Kết quả mong đợi

* Một tệp Word có tên `RadialChart.docx`
* Trong tệp, một trang duy nhất chứa biểu đồ radial có kích thước 400 × 300 points
* Biểu đồ hiển thị một series có tiêu đề **Series 1** với các giá trị **10, 20, 30**
* Graduations (đường lưới radial) hiển thị xung quanh biểu đồ

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cần thay đổi gì | Lý do |
|-----------|----------------|--------|
| **Multiple series** | Gọi `chart.getSeries().add(...)` cho mỗi series | Cho phép trực quan hoá dữ liệu so sánh |
| **Different chart type** | Thay thế `ChartType.RADIAL` bằng `ChartType.COLUMN` (hoặc bất kỳ loại nào khác) | Sử dụng loại biểu đồ phù hợp nhất với dữ liệu của bạn |
| **Custom colors** | Truy cập `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Cải thiện thương hiệu trực quan |
| **Older Aspose.Words version** | Bỏ qua dòng `setShowGraduations` hoặc nâng cấp thư viện | Ngăn ngừa `NoSuchMethodError` |
| **Saving to a different format** | Sử dụng `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Tạo PDF thay vì DOCX |

## Ví dụ đầy đủ có thể chạy

Dưới đây là chương trình Java hoàn chỉnh, tự chứa. Sao chép nó vào tệp có tên `RadialChartExample.java`, thêm phụ thuộc Aspose.Words, và chạy nó.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Kết luận

Bây giờ bạn đã biết cách **create radial chart** bằng chương trình, **add data series chart**, kiểm soát **how to set chart size**, và **insert chart into Word** trong khi bắt đầu từ một **blank Word document**. Ví dụ này sử dụng Aspose.Words for Java 24.9, nhưng các khái niệm tương tự áp dụng cho các thư viện biểu đồ khác có API tương tự.

### Các bước tiếp theo

* Khám phá các loại biểu đồ khác (`ChartType.PIE`, `ChartType.LINE`, v.v.) – điều này liên quan tới từ khóa phụ **insert chart into word**.
* Tùy chỉnh nhãn trục, chú giải và màu sắc để phù hợp với hướng dẫn thương hiệu của bạn.
* Tạo biểu đồ động từ truy vấn cơ sở dữ liệu hoặc tệp CSV.
* Chuyển đổi `.docx` kết quả sang PDF để phân phối (`doc.save("output.pdf", SaveFormat.PDF)`).

Bạn có thể tự do thử nghiệm với kích thước, dữ liệu series và các tùy chọn kiểu dáng để tạo ra hình ảnh chính xác mà bạn cần. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Chèn biểu đồ khu vực vào tài liệu Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}