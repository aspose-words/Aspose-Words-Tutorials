---
category: general
date: 2026-09-11
description: Lưu tài liệu Word sau khi chỉnh sửa biểu đồ bánh donut bằng Aspose.Words
  for Java. Tìm hiểu cách thay đổi kích thước lỗ bánh donut, xoay biểu đồ bánh donut
  và chỉnh sửa các thuộc tính của biểu đồ bánh donut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: vi
lastmod: 2026-09-11
og_description: Lưu tài liệu Word sau khi chỉnh sửa biểu đồ bánh rán bằng Aspose.Words
  cho Java. Hướng dẫn này cho thấy cách thay đổi kích thước lỗ bánh rán, xoay biểu
  đồ bánh rán và tùy chỉnh giao diện biểu đồ.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Lưu tài liệu Word sau khi chỉnh sửa biểu đồ donut – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Lưu tài liệu Word sau khi chỉnh sửa biểu đồ donut trong Java
url: /vi/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu Word sau khi chỉnh sửa biểu đồ bánh donut trong Java

Nếu bạn cần **lưu tài liệu Word** chứa một biểu đồ bánh donut được tùy chỉnh, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Chỉ trong vài dòng Java, bạn có thể thay đổi lỗ bánh donut, xoay biểu đồ bánh donut, và sau đó ghi kết quả trở lại đĩa.

Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được sử dụng Aspose.Words for Java, cùng với các mẹo để xử lý nhiều biểu đồ, xác minh loại nút, và tránh các bẫy thường gặp. Không cần tham chiếu bên ngoài — mọi thứ bạn cần đều đã được bao gồm.

## Yêu cầu trước

- Java 17 hoặc mới hơn đã được cài đặt
- Maven hoặc Gradle để quản lý các phụ thuộc
- Aspose.Words for Java (phiên bản 23.9 hoặc mới hơn) đã được thêm vào dự án của bạn  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Một tệp Word (`input.docx`) chứa một biểu đồ bánh donut duy nhất

## Bước 1: Tải tài liệu Word

Bước đầu tiên là mở tệp nguồn. Bước này rất quan trọng vì mọi thao tác tiếp theo đều làm việc trên đối tượng `Document` trong bộ nhớ.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Tại sao?** Việc tải tài liệu tạo ra một biểu diễn DOM cho phép bạn duyệt qua các hình dạng, bảng và biểu đồ. Nếu tệp không thể mở, Aspose.Words sẽ ném ra một ngoại lệ, vì vậy bạn sẽ biết ngay rằng đường dẫn sai.

## Bước 2: Xác định hình dạng biểu đồ bánh donut

Một biểu đồ được lưu trong một nút `Shape`. Chúng ta lấy hình dạng đầu tiên chứa biểu đồ và ép kiểu renderer của nó thành `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Tại sao?** Kiểm tra `isChart()` ngăn ngừa `ClassCastException` khi tài liệu chứa hình ảnh hoặc các hình dạng khác trước biểu đồ. Điều này làm cho mã trở nên vững chắc cho các tài liệu có nội dung hỗn hợp.

## Bước 3: Thay đổi kích thước lỗ bánh donut  

Bây giờ chúng ta chỉnh sửa lỗ bánh donut. Phương thức `setHoleSize` yêu cầu một phần trăm của bán kính biểu đồ (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Tại sao?** Thay đổi lỗ bánh donut (`change doughnut hole` / `change chart hole size`) cho phép bạn nhấn mạnh hoặc giảm nhấn mạnh khu vực trung tâm. Các giá trị ngoài khoảng 10‑90 % sẽ bị API bỏ qua.

## Bước 4: Xoay biểu đồ bánh donut  

Để kiểm soát vị trí bắt đầu của lát đầu tiên, đặt góc của lát đầu tiên. Điều này thực sự **xoay biểu đồ bánh donut**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Tại sao?** Xoay biểu đồ hữu ích khi bạn muốn một lát cụ thể xuất hiện ở trên cùng hoặc để phù hợp với yêu cầu thiết kế.

## Bước 5: Lưu tài liệu đã cập nhật  

Cuối cùng, ghi các thay đổi trở lại một tệp mới. Đây là thời điểm bạn **lưu tài liệu Word** với biểu đồ đã chỉnh sửa.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Kết quả mong đợi:** `output.docx` chứa nội dung gốc, nhưng biểu đồ bánh donut hiện có lỗ 30 % và lát đầu tiên bắt đầu ở 45 °. Mở tệp trong Microsoft Word sẽ hiển thị biểu đồ đã được chuyển đổi.

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào IDE của mình. Nó bao gồm tất cả các import và xử lý lỗi cần thiết để **chỉnh sửa biểu đồ bánh donut** và **lưu tài liệu Word** một cách an toàn.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Kết quả mong đợi

Khi bạn mở `output.docx`:

- Lỗ trung tâm của biểu đồ bánh donut chiếm khoảng một phần ba bán kính biểu đồ.  
- Lát đầu tiên bắt đầu ở vị trí 45 độ, làm chuyển toàn bộ biểu đồ theo chiều kim đồng hồ.  

Cả hai thay đổi trực quan đều được phản ánh ngay lập tức trong Word.

## Các biến thể thường gặp và trường hợp đặc biệt

| Tình huống | Cách xử lý |
|-----------|------------|
| **Nhiều biểu đồ** | Duyệt qua `doc.getChildNodes(NodeType.SHAPE, true)` và lọc `shape.isChart()`; áp dụng `setHoleSize` / `setFirstSliceAngle` cho mỗi `Chart`. |
| **Biểu đồ không phải là bánh donut** | Kiểm tra `chart.getType()`; chỉ gọi `setHoleSize` khi `chart.getType() == ChartType.DOUGHNUT`. |
| **Cần thay đổi kích thước lỗ một cách động** | Tính phần trăm mong muốn dựa trên giá trị dữ liệu, sau đó gọi `setHoleSize(computedValue)`. |
| **Lưu vào stream** | Sử dụng 

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cách lưu tài liệu dưới dạng pdf với Aspose.Words cho Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Lưu Word có mật khẩu bằng Aspose.Words cho Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}