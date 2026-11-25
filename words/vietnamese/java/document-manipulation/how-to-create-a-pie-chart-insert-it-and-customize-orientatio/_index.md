---
category: general
date: 2026-11-25
description: Học cách tạo biểu đồ tròn trong Java, chèn biểu đồ tròn vào tài liệu
  Word, tách miếng bánh và thay đổi hướng biểu đồ với các ví dụ mã rõ ràng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: vi
lastmod: 2026-11-25
og_description: Tạo biểu đồ tròn trong Java, chèn biểu đồ tròn vào tài liệu, tách
  lát bánh và thay đổi hướng biểu đồ bằng mã hướng dẫn từng bước.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Tạo biểu đồ tròn trong Java – chèn, tách phần, và xoay
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Cách tạo biểu đồ tròn, chèn nó và tùy chỉnh hướng trong Java
url: /vi/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ tròn, chèn vào và tùy chỉnh hướng trong Java

Nếu bạn cần **tạo một biểu đồ tròn** trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chi tiết. Bạn sẽ thấy cách **chèn biểu đồ tròn**, làm nổ một lát để nhấn mạnh, và **thay đổi hướng biểu đồ** bằng một phép quay đơn giản.

Bài học bao gồm mọi thứ bạn cần—từ việc thiết lập thư viện Aspose.Words for Java đến việc tạo ra một tệp `.docx` cuối cùng hiển thị biểu đồ tròn đã quay và nổ. Không cần tài liệu bên ngoài; chỉ cần làm theo các bước và chạy mã.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* Java 17 hoặc mới hơn đã được cài đặt.
* Maven hoặc Gradle để quản lý phụ thuộc.
* Giấy phép Aspose.Words for Java hợp lệ (hoặc sử dụng chế độ đánh giá miễn phí).

Thêm phụ thuộc Aspose.Words vào `pom.xml` (Maven) hoặc `build.gradle` (Gradle). Ví dụ cho Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Mẹo:** Giữ phiên bản thư viện luôn cập nhật; bản phát hành mới nhất (24.10 tại thời điểm viết) đã bao gồm các bản sửa lỗi cho việc hiển thị biểu đồ.

## Bước 1: Tạo biểu đồ tròn và chèn vào tài liệu

Bước đầu tiên là **tạo đối tượng biểu đồ tròn** và nhúng chúng vào tệp Word. Đoạn mã dưới đây tạo một tài liệu đơn giản, thêm một chỗ giữ chỗ cho biểu đồ, và chèn một biểu đồ tròn có kích thước 400 × 300 pixel.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Tại sao điều này quan trọng:** `builder.insertChart` tạo một chỗ giữ chỗ cho biểu đồ mà Aspose.Words sẽ tự động chuyển đổi thành biểu đồ OOXML khi tài liệu được lưu. Tham số `ChartType.PIE` báo cho thư viện vẽ một biểu đồ tròn, đáp ứng yêu cầu **chèn biểu đồ tròn**.

## Bước 2: Nổ lát biểu đồ để làm nổi bật một phần

Nổ một lát giúp thu hút sự chú ý đến một điểm dữ liệu cụ thể. Dòng lệnh sau nổ lát đầu tiên (chỉ số 0) ra 10 điểm:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Bạn có thể thay đổi chỉ số để nhắm vào lát khác, hoặc điều chỉnh khoảng cách nổ để tạo hiệu ứng nhẹ hơn. Nổ một lát là cách tiêu chuẩn để **nổ lát biểu đồ tròn** trong Aspose.Words.

## Bước 3: Thay đổi hướng biểu đồ bằng cách quay

Quay biểu đồ mang lại góc nhìn mới. Sử dụng `setRotationAngle` để quay toàn bộ biểu đồ theo chiều kim đồng hồ (góc được đo bằng độ).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Lệnh trên đáp ứng các yêu cầu **quay biểu đồ tròn** và **thay đổi hướng biểu đồ**. Bất kỳ góc nào từ 0 đến 360 độ đều được chấp nhận.

## Ví dụ đầy đủ có thể chạy

Kết hợp tất cả lại, dưới đây là một chương trình hoàn chỉnh, tự chứa, tạo biểu đồ tròn, nổ một lát và quay biểu đồ. Chạy nó từ IDE hoặc từ dòng lệnh với `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Kết quả mong đợi

* Một tệp có tên **CreatePieChartDemo.docx** sẽ xuất hiện trong thư mục làm việc.
* Mở tệp trong Microsoft Word sẽ hiển thị một biểu đồ tròn 400 × 300 pixel.
* Lát đầu tiên (Q1) được dịch ra ngoài 10 điểm, tạo hiệu ứng **nổ lát biểu đồ tròn**.
* Toàn bộ biểu đồ được nghiêng 45 độ, minh họa **thay đổi hướng biểu đồ** và **quay biểu đồ tròn**.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cách điều chỉnh mã |
|-----------|---------------------|
| **Kích thước biểu đồ khác** | Thay đổi các đối số `400, 300` trong `insertChart`. |
| **Nhiều series** | Thêm các đối tượng `ChartSeries` vào `chart.getSeries()`. |
| **Nổ lát khác** | Sử dụng `setExplode(sliceIndex, distance)` với `sliceIndex` mong muốn. |
| **Không cần quay** | Bỏ qua lệnh `setRotationAngle` hoặc đặt góc thành `0`. |
| **Xuất ra PDF thay vì DOCX** | Sau khi xây dựng tài liệu, gọi `doc.save("output.pdf")` với định dạng PDF. |

> **Cảnh báo:** Sử dụng khoảng cách nổ âm sẽ gây ra `IllegalArgumentException`. Luôn cung cấp giá trị không âm.

## Mẹo về hiệu năng

Nếu bạn tạo nhiều biểu đồ trong một vòng lặp, hãy tái sử dụng một đối tượng `DocumentBuilder` duy nhất và chỉ gọi `insertChart` cho mỗi lần lặp. Điều này giảm tải bộ nhớ và tăng tốc xử lý.

## Kết luận

Bây giờ bạn đã biết cách **tạo biểu đồ tròn**, **chèn biểu đồ tròn**, **nổ lát biểu đồ tròn**, và **quay biểu đồ tròn** bằng Aspose.Words for Java. Ví dụ hoàn chỉnh minh họa quy trình đầy đủ—from khởi tạo tài liệu đến lưu tệp hiển thị một biểu đồ tròn đã quay và nổ.

Tiếp theo, bạn có thể khám phá **thay đổi hướng biểu đồ** sâu hơn bằng cách áp dụng hiệu ứng 3‑D, hoặc thử các loại biểu đồ khác như **Bar** hoặc **Line**. Các mẫu API giống nhau, vì vậy việc mở rộng tutorial này là rất đơn giản.

Hãy thoải mái chỉnh sửa dữ liệu, chỉ số lát, hoặc góc quay để phù hợp với nhu cầu báo cáo của bạn, và chia sẻ kết quả với cộng đồng!

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}