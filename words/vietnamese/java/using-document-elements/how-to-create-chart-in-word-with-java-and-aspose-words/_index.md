---
category: general
date: 2026-09-24
description: Tìm hiểu cách tạo biểu đồ trong Word bằng Java, chèn biểu đồ dạng tròn
  và lưu tài liệu dưới dạng docx với Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: vi
lastmod: 2026-09-24
og_description: Tạo biểu đồ trong Word bằng Java và Aspose.Words. Hướng dẫn này cho
  bạn cách thêm biểu đồ dạng tròn, tùy chỉnh dữ liệu và lưu tài liệu dưới dạng docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Tạo biểu đồ trong Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Cách tạo biểu đồ trong Word bằng Java và Aspose.Words
url: /vi/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ trong Word bằng Java và Aspose.Words

Nếu bạn cần **create chart in Word** từ một ứng dụng Java, hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình. Bạn sẽ thấy cách thêm một biểu đồ radial, tùy chọn điền dữ liệu cho các series, và cuối cùng **save document as docx** bằng thư viện Aspose.Words for Java.

Việc tạo dữ liệu trực quan trong tệp Word là một yêu cầu phổ biến cho báo cáo, lập hoá đơn, hoặc tạo tài liệu tự động. Khi kết thúc tutorial này, bạn sẽ có thể thực hiện các dự án **create word document java** có khả năng **add chart to Word** mà không cần chỉnh sửa thủ công.

## Yêu cầu trước

* Java Development Kit (JDK) 8 hoặc mới hơn.  
* Maven hoặc Gradle để quản lý phụ thuộc.  
* Một IDE như IntelliJ IDEA, Eclipse, hoặc VS Code.  
* Giấy phép Aspose.Words for Java hợp lệ (bản dùng thử miễn phí hoạt động cho phát triển).

Những công cụ này cung cấp nền tảng cho các ví dụ mã sẽ được trình bày tiếp theo.

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven mới (hoặc cập nhật dự án hiện có) và thêm phụ thuộc Aspose.Words vào file `pom.xml` của bạn:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Chạy `mvn clean install` sẽ tải thư viện và đưa các lớp như `Document`, `DocumentBuilder`, và `ChartType` có sẵn trên classpath.

> **Mẹo:** Giữ phiên bản thư viện luôn cập nhật. Các bản phát hành mới bổ sung các loại biểu đồ và cải thiện hiệu suất render.

## Bước 2: Tạo tài liệu Word mới

Bước lập trình đầu tiên để **create chart in Word** là khởi tạo một `Document` trống. Đối tượng này đại diện cho toàn bộ gói `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` hoạt động như một con trỏ; nó biết vị trí chèn hiện tại và cung cấp các phương thức cho văn bản, bảng và biểu đồ. Tại thời điểm này, bạn đã **created word document java** – một canvas sạch sẵn sàng cho nội dung.

## Bước 3: Chèn biểu đồ radial

Aspose.Words hỗ trợ nhiều loại biểu đồ. Để **insert radial chart**, gọi `insertChart` với `ChartType.RADIAL`. Phương thức này cũng yêu cầu chiều rộng và chiều cao tính bằng điểm (1 point ≈ 1/72 inch).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Đối tượng `Shape` trả về chứa đối tượng biểu đồ bên dưới. Biểu đồ tự động vẽ các chia độ cho bố cục 24.9°, đây là mặc định cho các biểu đồ radial trong Word.

### Tại sao nên sử dụng biểu đồ radial?

Biểu đồ radial hiển thị dữ liệu vòng quanh một vòng tròn, rất phù hợp để thể hiện các mẫu chu kỳ (ví dụ: doanh thu hàng tháng, các chỉ số dạng đồng hồ). API tương tự có thể chèn biểu đồ cột, bánh hoặc đường, nhưng loại radial mang lại vẻ ngoài đặc trưng mà không cần mã định dạng thêm.

## Bước 4: (Tùy chọn) Điền dữ liệu cho series của biểu đồ

Nếu bạn muốn biểu đồ hiển thị giá trị thực, cần thêm series và các điểm dữ liệu. Đoạn mã dưới đây thêm một series duy nhất với ba điểm dữ liệu:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Bạn có thể lặp lại các lời gọi `add` cho bao nhiêu điểm dữ liệu tùy ý. Aspose.Words tự động cập nhật biểu diễn trực quan, vì vậy bạn sẽ thấy các lát radial điều chỉnh theo giá trị mới.

> **Câu hỏi thường gặp:** *Nếu tôi cần liên kết dữ liệu từ cơ sở dữ liệu thì sao?*  
> Lấy các hàng, lặp qua chúng, và gọi `series.getDataPoints().add(value, label)` trong vòng lặp. API này an toàn với đa luồng và hoạt động với bất kỳ `ResultSet` nào bạn cung cấp.

## Bước 5: Lưu tài liệu dưới dạng DOCX

Khi biểu đồ đã sẵn sàng, bước cuối cùng là **save document as docx**. Phương thức `save` xác định định dạng đầu ra dựa trên phần mở rộng tệp.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Tệp được tạo chứa một biểu đồ radial hoạt động đầy đủ có thể mở trong Microsoft Word, LibreOffice, hoặc bất kỳ trình xem nào hỗ trợ định dạng DOCX. Vì chúng ta sử dụng phần mở rộng `.docx`, Word sẽ lưu tệp ở định dạng Open XML, tiêu chuẩn hiện đại cho tài liệu Word.

### Xác minh kết quả

Mở `RadialChartDemo.docx` trong Word:

1. Bạn sẽ thấy một trang duy nhất với biểu đồ radial được căn giữa.  
2. Nếu bạn đã thêm dữ liệu series, biểu đồ sẽ hiển thị bốn lát được gắn nhãn Q1‑Q4.  
3. Nhấp chuột phải vào biểu đồ → **Edit Data** để xác nhận bảng dữ liệu bên dưới.

Nếu biểu đồ hiển thị trống, hãy kiểm tra lại rằng bạn đã gọi `chart.getChart()` trước khi thêm series, và đảm bảo con trỏ của DocumentBuilder được đặt ở vị trí mong muốn cho biểu đồ.

## Bước 6: Mẹo nâng cao khi làm việc với biểu đồ

| Tip | Why it matters |
|-----|----------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Cải thiện tính nhất quán về hình ảnh mà không cần định dạng thủ công từng yếu tố. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Cho phép bạn tinh chỉnh kích thước biểu đồ dựa trên bố cục trang. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Cung cấp ngữ cảnh cho người đọc khi xem tài liệu mà không có văn bản bao quanh. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Hữu ích khi bạn cần một phiên bản không thể chỉnh sửa để phân phối. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Ngăn chặn watermark đánh giá trong các bản dựng sản phẩm. |

Những cải tiến này là tùy chọn nhưng minh họa cách bạn có thể tùy chỉnh biểu đồ hơn nữa sau khi đã học cách **add chart to Word**.

## Kết luận

Bây giờ bạn có một ví dụ hoàn chỉnh, tự chứa, cho thấy cách **create chart in Word** bằng Java, **insert radial chart**, tùy chọn điền dữ liệu, và **save document as docx**. Mẫu tương tự áp dụng cho các loại biểu đồ khác, vì vậy bạn có thể mở rộng tutorial này sang biểu đồ cột, đường, hoặc bánh tùy nhu cầu.

Tiếp theo bạn có thể khám phá:

* Các dự án **create word document java** kết hợp bảng, hình ảnh và nhiều biểu đồ.  
* Sử dụng **save document as docx** cùng với **save document as pdf** cho báo cáo đa định dạng.  
* Thêm dữ liệu động từ REST APIs hoặc cơ sở dữ liệu vào biểu đồ của bạn.

Hãy tự do thử nghiệm các tùy chọn định dạng, kích thước biểu đồ và nguồn dữ liệu. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}