---
category: general
date: 2026-09-18
description: Học cách tạo tài liệu Word và chèn biểu đồ tròn bằng Aspose.Words for
  Java. Bao gồm các bước xoay biểu đồ tròn và tạo file Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: vi
lastmod: 2026-09-18
og_description: Tạo tài liệu Word và chèn biểu đồ tròn bằng Java. Tham khảo hướng
  dẫn này để xoay biểu đồ tròn, tách các phần và tạo tệp Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Tạo tài liệu Word với biểu đồ tròn – hướng dẫn Java từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Cách tạo tài liệu Word có biểu đồ tròn trong Java
url: /vi/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word với biểu đồ tròn trong Java

Nếu bạn cần **tạo một tài liệu Word** để trực quan hoá dữ liệu, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words for Java. Bạn sẽ học cách chèn biểu đồ tròn, tách một lát, xoay biểu đồ, và cuối cùng **tạo một tệp Word** mà bạn có thể mở trong Microsoft Word.

Việc xây dựng báo cáo kết hợp văn bản và biểu đồ không cần một công cụ đồ họa riêng. Khi kết thúc hướng dẫn này, bạn sẽ có một chương trình hoàn chỉnh, có thể chạy được, tạo ra một tệp .docx chứa biểu đồ tròn được cấu hình đầy đủ.

## Yêu cầu trước

- Java 17 hoặc mới hơn (mã cũng biên dịch được với Java 8+)
- Maven hoặc Gradle để quản lý phụ thuộc
- Giấy phép Aspose.Words for Java (bản dùng thử miễn phí hoạt động cho ví dụ này)
- Kiến thức cơ bản về cú pháp Java

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven mới và thêm phụ thuộc Aspose.Words vào `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Mẹo:** Giữ cho số phiên bản luôn cập nhật; các bản phát hành mới hơn bổ sung cải tiến loại biểu đồ và sửa lỗi.

## Bước 2: Tạo một tài liệu Word mới

Hoạt động đầu tiên khi bạn **tạo một tài liệu Word** bằng chương trình là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp .docx trong bộ nhớ.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Lớp `Document` là điểm vào cho tất cả các tính năng xử lý Word. Không có tệp nào được ghi ra đĩa ở thời điểm này; mọi thứ diễn ra trong RAM cho đến khi bạn gọi `save`.

## Bước 3: Cách chèn biểu đồ tròn

Một `DocumentBuilder` cho phép bạn thêm nội dung vào tài liệu. Với `insertChart` bạn có thể **chèn biểu đồ tròn** một cách trực tiếp.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` chỉ cho Aspose.Words tạo một biểu đồ tròn. Kích thước được biểu diễn bằng điểm (1 pt ≈ 1/72 in). Sau lệnh này, biểu đồ xuất hiện trên một đoạn mới.

## Bước 4: Điền dữ liệu vào biểu đồ

Biểu đồ tròn cần một chuỗi các giá trị. Ở đây chúng ta thêm ba danh mục: “Apples”, “Bananas”, và “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Phương thức `add` xây dựng chuỗi và tự động tạo các mục trong chú giải. Bạn có thể tái sử dụng mẫu này cho bất kỳ bộ dữ liệu số nào.

## Bước 5: Nhấn mạnh lát đầu tiên

Việc tách một lát làm nổi bật một giá trị cụ thể. Lát đầu tiên (chỉ số 0) được tách ra 20 điểm.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Cài đặt `explode` trên chuỗi ảnh hưởng tới toàn bộ biểu đồ, vì vậy chỉ điểm dữ liệu đầu tiên được dịch chuyển.

## Bước 6: Cách xoay biểu đồ tròn

Xoay biểu đồ cải thiện cân bằng trực quan, đặc biệt khi lát lớn nhất không ở vị trí trên cùng. Phương thức `setRotationAngle` nhận giá trị theo độ.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Việc xoay 45° di chuyển góc bắt đầu theo chiều kim đồng hồ, làm cho biểu đồ dễ đọc hơn trong nhiều bố cục.

## Bước 7: Lưu tài liệu và tạo tệp Word

Cuối cùng, ghi tài liệu ra đĩa. Bước này **tạo tệp word** có thể mở bằng Microsoft Word, LibreOffice, hoặc bất kỳ trình xem nào tương thích.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Phương thức `save` tự động phát hiện phần mở rộng .docx và ghi một gói tương thích với Word. Thư mục `output` phải tồn tại hoặc bạn có thể tạo nó bằng mã.

### Kết quả mong đợi

Sau khi chạy chương trình, mở `output/PieChart.docx`. Bạn sẽ thấy:

- Một trang duy nhất chứa biểu đồ tròn kích thước 400 × 300 pt.
- Lát “Apples” được tách ra ngoài 20 pt.
- Toàn bộ biểu đồ được xoay 45° theo chiều kim đồng hồ.
- Một chú giải khớp với ba danh mục trái cây.

## Các biến thể phổ biến và trường hợp đặc biệt

### Chèn nhiều biểu đồ

Nếu bạn cần hơn một biểu đồ, gọi lại `builder.insertChart` sau khi di chuyển con trỏ:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Thay đổi màu sắc biểu đồ

Bạn có thể tùy chỉnh màu sắc của các lát thông qua bộ sưu tập `getPoints()` của chuỗi:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Xử lý bộ dữ liệu lớn

Đối với bộ dữ liệu có hơn 10 lát, hãy cân nhắc sử dụng biểu đồ vòng donut (`ChartType.DOUGHNUT`) để giữ cho hình ảnh rõ ràng.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu Word**, **chèn biểu đồ tròn**, **xoay biểu đồ tròn**, và **tạo một tệp Word** bằng Aspose.Words for Java. Giải pháp hoàn chỉnh minh họa quy trình làm việc đầy đủ từ khởi tạo tài liệu đến xuất tệp cuối cùng, bao gồm cả “cách thực hiện” và “lý do” cho mỗi bước.

Tiếp theo, khám phá các chủ đề liên quan như **cách tạo dữ liệu biểu đồ tròn** từ cơ sở dữ liệu, thêm nhãn dữ liệu, hoặc xuất biểu đồ dưới dạng hình ảnh. Thử nghiệm các loại biểu đồ khác nhau (cột, đường, donut) để mở rộng bộ công cụ tự động hoá Word của bạn.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Theo dõi thay đổi trong tài liệu Word bằng Aspose.Words Java: Hướng dẫn đầy đủ về phiên bản tài liệu](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}