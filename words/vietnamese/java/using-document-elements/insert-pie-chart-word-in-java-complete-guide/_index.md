---
category: general
date: 2026-09-24
description: Chèn biểu đồ tròn vào tệp DOCX bằng Aspose.Words cho Java. Tìm hiểu cách
  thiết lập kích thước lỗ, tách miếng bánh, làm nổi bật miếng biểu đồ tròn và tạo
  biểu đồ DOCX một cách dễ dàng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: vi
lastmod: 2026-09-24
og_description: Chèn biểu đồ tròn vào tệp DOCX bằng Aspose.Words for Java. Điều chỉnh
  kích thước lỗ, tách miếng bánh, làm nổi bật miếng bánh, và tạo biểu đồ DOCX trong
  vài phút.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Chèn biểu đồ tròn trong Java – hướng dẫn chi tiết từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Chèn từ biểu đồ tròn trong Java – hướng dẫn đầy đủ
url: /vi/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn pie chart word trong Java – hướng dẫn đầy đủ

Nếu bạn cần **insert pie chart word** trong một tệp DOCX, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác bằng Aspose.Words for Java. Bạn sẽ thấy quy trình đầy đủ từ việc tạo tài liệu đến tùy chỉnh biểu đồ sao cho phần lát được nổ ra, kích thước lỗ được đặt thành 0, và phần lát được làm nổi bật.

Việc làm việc với biểu đồ trong tài liệu Word thường cảm thấy như một mối quan tâm riêng biệt so với xử lý văn bản thông thường, nhưng Aspose.Words kết hợp cả hai. Trong các bước dưới đây, bạn cũng sẽ học cách **create docx chart** các tệp sẵn sàng mở trong Microsoft Word, Google Docs, hoặc bất kỳ trình xem DOCX nào khác.

## Những gì bạn sẽ đạt được

* **Insert pie chart word** vào một tài liệu trống  
* **Set hole size** để biến biểu đồ thành một vòng tròn đầy (không phải bánh donut)  
* **Explode pie slice** để làm nổi bật một đoạn cụ thể  
* **Highlight pie chart slice** với định dạng tùy chỉnh  
* **Create docx chart** có thể chia sẻ hoặc chỉnh sửa thêm  

### Yêu cầu trước

* Java 17 hoặc mới hơn (mã cũng biên dịch được với Java 8)  
* Thư viện Aspose.Words for Java (phiên bản 23.9 hoặc mới hơn)  
* Một IDE hoặc công cụ xây dựng (Maven/Gradle) có thể giải quyết phụ thuộc Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Cách chèn pie chart word vào DOCX bằng Aspose.Words

Bước đầu tiên là tạo một tài liệu trống mới và lấy một `DocumentBuilder`. Builder cung cấp cho bạn quyền truy cập trực tiếp vào luồng nội dung của tài liệu, giúp việc **insert pie chart word** trở nên đơn giản.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Tại sao điều này quan trọng
`Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` là API cấp cao cho phép bạn chèn đoạn văn, bảng và biểu đồ mà không cần xử lý XML cấp thấp. Bắt đầu với một tài liệu sạch sẽ đảm bảo rằng biểu đồ bạn thêm là nội dung duy nhất, rất phù hợp cho việc học hoặc tạo báo cáo dựa trên mẫu.

## Đặt kích thước lỗ để tạo vòng tròn đầy

Mặc định, Aspose.Words tạo biểu đồ bánh donut khi bạn yêu cầu một biểu đồ tròn. Để làm cho biểu đồ thành một vòng tròn thực sự, bạn phải **set hole size** thành `0`. Điều này loại bỏ lỗ bên trong và tạo ra giao diện bánh tròn truyền thống.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Mẹo thực tế
Nếu sau này bạn quyết định chuyển sang biểu đồ bánh donut, chỉ cần thay đổi giá trị `holeSize` thành phần trăm (ví dụ, `30`). API này hoạt động cho cả hai loại biểu đồ.

## Nổ phần lát bánh tròn để làm nổi bật một đoạn

Việc nổ một phần lát làm cho nó nổi bật về mặt hình ảnh. Thao tác **explode pie slice** di chuyển phần lát đã chọn ra ngoài một tỷ lệ phần trăm của bán kính biểu đồ.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Tại sao phải nổ?
Một phần lát bị nổ sẽ thu hút mắt người đọc tới điểm dữ liệu quan trọng nhất—hoàn hảo cho bảng điều khiển hoặc tóm tắt cho lãnh đạo. Giá trị `20` có nghĩa là 20 % của bán kính; bạn có thể điều chỉnh nó từ `0` (không nổ) đến `100` (tách hoàn toàn).

## Làm nổi bật phần lát biểu đồ tròn với định dạng tùy chỉnh

Ngoài việc nổ, bạn có thể muốn **highlight pie chart slice** bằng cách thay đổi màu nền hoặc viền. Mặc dù mã demo tập trung vào việc nổ, bạn có thể mở rộng nó như sau:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Ghi chú của chuyên gia
Thay đổi màu nền của một phần lát cụ thể yêu cầu truy cập đối tượng `DataPoint`. Nếu bạn có nhiều series, hãy lặp qua `series.getDataPoints()` và áp dụng kiểu dáng một cách có điều kiện.

## Lưu và xác minh biểu đồ docx đã tạo

Cuối cùng, bạn **create docx chart** bằng cách lưu `Document`. Tệp kết quả có thể mở trong Microsoft Word để xem biểu đồ tròn đã được định dạng.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Kết quả mong đợi
Mở `PieChartFormatted.docx` sẽ hiển thị một biểu đồ tròn duy nhất:

* Biểu đồ chiếm khu vực 400 × 300 pt.  
* Kích thước lỗ là `0`, vì vậy biểu đồ là một vòng tròn đầy.  
* Phần lát đầu tiên được nổ ra 20 % và màu đỏ (nếu bạn đã thêm định dạng tùy chọn).  

Bây giờ bạn đã có một **create docx chart** có thể được phân phối, nhúng trong email, hoặc chỉnh sửa thêm bằng chương trình.

---

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Cách điều chỉnh mã |
|----------|----------------------|
| **Multiple series** | Lặp qua `pieChart.getChart().getSeries()` và đặt `Explosion` hoặc `FillColor` cho mỗi series. |
| **Dynamic data** | Điền dữ liệu cho series bằng các giá trị từ cơ sở dữ liệu hoặc CSV trước khi gọi `setExplosion`. |
| **Different chart size** | Thay đổi các đối số width/height trong `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | Sau khi lưu DOCX, gọi `doc.save("output.pdf")` để tạo phiên bản PDF của cùng biểu đồ. |
| **Localization** | Sử dụng `DocumentBuilder.insertChart` với định dạng số đặc thù cho locale cho các nhãn. |

### Mẹo chuyên nghiệp
Luôn gọi `setHoleSize(0)` **sau** `insertChart`. Nếu bạn đặt nó trước khi chèn, Aspose.Words sẽ quay lại kích thước bánh donut mặc định khi biểu đồ được tạo.

---

## Tổng kết

Bây giờ bạn đã biết cách **insert pie chart word** vào tài liệu Word bằng Java, cách **set hole size** để có giao diện bánh tròn đầy, cách **explode pie slice** để thu hút sự chú ý, và cách **highlight pie chart slice** với màu tùy chỉnh. Ví dụ hoàn chỉnh cũng minh họa cách **create docx chart** các tệp sẵn sàng để phân phối.

---

## Các bước tiếp theo

* Khám phá các loại biểu đồ khác (`BAR`, `LINE`, `SCATTER`) với `ChartType`.  
* Kết hợp việc tạo biểu đồ với mail merge để tạo báo cáo cá nhân hoá.  
* Tích hợp DOCX đã tạo vào một dịch vụ web trả về tệp theo yêu cầu.  

Nếu bạn gặp vấn đề, hãy nhớ kiểm tra rằng bạn đang sử dụng phiên bản Aspose.Words tương thích và thư mục đầu ra tồn tại và có quyền ghi.

Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}