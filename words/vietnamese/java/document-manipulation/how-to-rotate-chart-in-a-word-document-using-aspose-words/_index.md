---
category: general
date: 2026-10-10
description: Học cách xoay biểu đồ trong tệp Word và chỉnh sửa biểu đồ trong Word
  để thay đổi kích thước biểu đồ bánh donut với một ví dụ Java đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: vi
lastmod: 2026-10-10
og_description: Cách xoay biểu đồ trong tệp Word và chỉnh sửa biểu đồ trong Word để
  thay đổi kích thước biểu đồ bánh vòng bằng Aspose.Words cho Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Cách xoay biểu đồ trong tài liệu Word – hướng dẫn Java từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cách xoay biểu đồ trong tài liệu Word bằng Aspose.Words
url: /vi/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách xoay biểu đồ trong tài liệu Word bằng Aspose.Words

Nếu bạn cần **how to rotate chart** trong một tệp Microsoft Word, hướng dẫn này sẽ cho bạn các bước chính xác. Bạn cũng sẽ học cách **modify chart in Word** để **change doughnut chart size** mà không rời khỏi mã Java của mình.

Word automation thường cảm giác như một loạt các lời gọi API rời rạc, nhưng với Aspose.Words bạn có thể xử lý một biểu đồ như bất kỳ nút tài liệu nào khác. Khi kết thúc tutorial này, bạn sẽ có một chương trình chạy được, tải một `.docx` hiện có, xoay một biểu đồ doughnut 45°, giảm lỗ tròn thành 50 % bán kính, và lưu kết quả thành tệp mới.

## Yêu cầu trước

* Java 17 hoặc mới hơn đã được cài đặt.
* Maven (hoặc Gradle) để quản lý các phụ thuộc.
* Một tài liệu Word đầu vào (`input.docx`) đã chứa sẵn một biểu đồ doughnut.
* Một giấy phép Aspose.Words for Java hợp lệ (hoặc sử dụng chế độ đánh giá).

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven mới hoặc thêm phụ thuộc sau vào `pom.xml` hiện có của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Chạy `mvn clean install` sẽ tải thư viện và đưa các lớp vào classpath của bạn.

## Bước 2: Tải tài liệu Word chứa biểu đồ

Hoạt động đầu tiên là mở tài liệu hiện có. Lớp `Document` đại diện cho toàn bộ tệp.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Tải tệp **không** thay đổi nó; nó chỉ tạo một biểu diễn trong bộ nhớ mà bạn có thể truy vấn và chỉnh sửa.

## Bước 3: Tạo DocumentBuilder để điều hướng

`DocumentBuilder` cung cấp cho bạn một API kiểu con trỏ để duyệt qua cây tài liệu. Chúng ta sẽ dùng nó để tìm hình dạng biểu đồ đầu tiên.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

DocumentBuilder bắt đầu ở đầu tài liệu, nhưng bạn có thể di chuyển nó tới bất kỳ nút nào sau này nếu cần.

## Bước 4: Lấy hình dạng biểu đồ đầu tiên

Biểu đồ được lưu dưới dạng các nút `Shape`. Bằng cách lọc các nút con có kiểu `NodeType.SHAPE` chúng ta có thể trích xuất đối tượng biểu đồ.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Nếu tài liệu chứa nhiều biểu đồ, bạn có thể lặp qua `getChildNodes` và kiểm tra mỗi `Shape` bằng `hasChart()` trước khi ép kiểu.

## Bước 5: Xoay biểu đồ (how to rotate chart)

Biểu đồ doughnut thực chất là một biểu đồ tròn có lỗ ở giữa. Xoay nó sẽ thay đổi góc bắt đầu của lát đầu tiên.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Phương thức `setStartAngle` nhận một giá trị double đại diện cho độ. Giá trị dương xoay theo chiều kim đồng hồ, trong khi giá trị âm xoay ngược chiều kim đồng hồ.

## Bước 6: Thay đổi kích thước lỗ doughnut (change doughnut chart size)

Kích thước lỗ được biểu thị dưới dạng phần tỷ lệ của bán kính biểu đồ. Giá trị `0.5` có nghĩa là lỗ chiếm 50 % bán kính tổng.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Mẹo:** Phạm vi hợp lệ là `0.0` (không có lỗ, tức là biểu đồ tròn thường) đến `0.9` (vòng rất mỏng). Các giá trị ngoài phạm vi này sẽ ném ra `IllegalArgumentException`.

## Bước 7: Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi các thay đổi trở lại đĩa.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Khi bạn mở `DoughnutFormatted.docx` trong Microsoft Word, bạn sẽ thấy biểu đồ doughnut đã được xoay 45° và lỗ giảm còn một nửa kích thước ban đầu.

## Ví dụ đầy đủ, có thể chạy

Kết hợp tất cả các phần lại, đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào IDE của mình:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Kết quả mong đợi

Khi chạy chương trình sẽ in ra:

```
Chart rotated and doughnut size changed successfully.
```

Mở `DoughnutFormatted.docx` sẽ hiển thị một biểu đồ doughnut mà lát đầu tiên bắt đầu ở vị trí 45° và bán kính trong chiếm một nửa bán kính ngoài.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cần điều chỉnh | Lý do quan trọng |
|-----------|----------------|-------------------|
| **Nhiều biểu đồ** | Lặp qua `getChildNodes(NodeType.SHAPE, true)` và kiểm tra `shape.hasChart()` cho mỗi phần tử | Đảm bảo bạn chỉnh sửa biểu đồ mong muốn thay vì biểu đồ đầu tiên |
| **Biểu đồ cột hoặc đường** | `setStartAngle` không áp dụng; sử dụng `chart.getSeries().get(0).setFillFormat(...)` để tinh chỉnh hình ảnh khác | Không phải tất cả các loại biểu đồ đều hỗ trợ xoay; chỉ biểu đồ doughnut/tròn có góc bắt đầu |
| **Biểu đồ không có lỗ doughnut** | Bỏ qua `setDoughnutHoleSize` hoặc trước tiên chuyển loại biểu đồ sang doughnut bằng `chart.setChartType(ChartType.DONUT)` | Thay đổi kích thước lỗ trên biểu đồ không phải doughnut sẽ gây ra ngoại lệ |
| **Tài liệu lớn** | Sử dụng `DocumentBuilder.moveToDocumentStart()` và `builder.moveToNode(chartShape)` để điều hướng mục tiêu | Cải thiện hiệu suất bằng cách tránh duyệt toàn bộ các nút không liên quan |

## Mẹo chuyên nghiệp để thao tác biểu đồ đáng tin cậy

* **Cache the chart reference** – Nếu bạn dự định chỉnh sửa nhiều thuộc tính, hãy giữ một biến `Chart` cục bộ thay vì gọi liên tục `chartShape.getChart()`.
* **Validate input values** – Trước khi gọi `setStartAngle` hoặc `setDoughnutHoleSize`, hãy xác minh phạm vi để tránh lỗi thời gian chạy.
* **Use a license** – Chế độ đánh giá sẽ chèn watermark vào trang đầu. Áp dụng giấy phép (`License license = new License(); license.setLicense("Aspose.Words.lic");`) sẽ loại bỏ nó.

## Bước tiếp theo

Bây giờ bạn đã biết **how to rotate chart** và **change doughnut chart size**, bạn có thể khám phá các kịch bản **modify chart in Word** khác:

* Thay đổi màu sắc các lát bằng `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Thêm nhãn dữ liệu bằng cách gọi `chart.getSeries().get(0).setHasDataLabel(true)`.
* Xuất biểu đồ dưới dạng hình ảnh bằng `chart.toImage(300, 300, ImageType.PNG)`.

Mỗi phần mở rộng này tuân theo cùng một mẫu: lấy đối tượng `Chart`, gọi setter tương ứng, và lưu tài liệu.

---

**Bạn vừa thành thạo việc xoay và thay đổi kích thước biểu đồ doughnut trong Word bằng Java.** Hãy tự do điều chỉnh mã cho các loại biểu đồ khác, tích hợp vào quy trình tạo tài liệu lớn hơn, hoặc kết hợp với Aspose.Slides để tự động PowerPoint. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ẩn trục biểu đồ trong tài liệu Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Chèn biểu đồ bong bóng trong tài liệu Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}