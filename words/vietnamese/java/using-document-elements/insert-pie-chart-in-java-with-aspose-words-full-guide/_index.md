---
category: general
date: 2026-07-29
description: Chèn biểu đồ tròn bằng Aspose.Words cho Java và tìm hiểu cách tạo biểu
  đồ bánh vòng, định dạng biểu đồ tròn, định dạng biểu đồ trong Word và tùy chỉnh
  kích thước biểu đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: vi
lastmod: 2026-07-29
og_description: Chèn biểu đồ tròn với Aspose.Words cho Java và nhanh chóng học cách
  tạo biểu đồ vòng, định dạng biểu đồ tròn, định dạng biểu đồ Word, và tùy chỉnh kích
  thước biểu đồ cho tài liệu chuyên nghiệp.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Chèn biểu đồ tròn trong Java – Hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Chèn biểu đồ tròn trong Java với Aspose.Words – Hướng dẫn đầy đủ
url: /vi/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn biểu đồ tròn trong Java với Aspose.Words – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi làm thế nào để **insert pie chart** vào tài liệu Word từ mã Java chưa? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi họ cần một cách nhanh chóng, lập trình để trực quan hoá dữ liệu. Tin tốt? Với Aspose.Words cho Java, bạn có thể thực hiện chỉ trong vài dòng, và trong khi làm vậy bạn cũng có thể **generate doughnut chart**, **format pie chart**, **format chart Word**, và **customize chart size** để phù hợp với thương hiệu của mình.

Trong tutorial này, chúng ta sẽ đi qua một ví dụ thực tế bắt đầu bằng việc tạo một tài liệu trống, chèn một biểu đồ tròn, tinh chỉnh một vài thuộc tính hiển thị, và cuối cùng lưu file. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng, có thể dán vào bất kỳ dự án Java nào cần tự động hoá biểu đồ. Không cần thư viện phụ, không cần can thiệp thủ công với Office interop—chỉ cần Java sạch, đã biên dịch.

## Những gì bạn cần

- **Java 17** (hoặc bất kỳ JDK mới nào; API tương thích ngược)
- **Aspose.Words for Java** 22.12 hoặc mới hơn – bạn có thể tải artifact Maven hoặc file .jar từ trang Aspose.
- Một IDE vừa phải (IntelliJ IDEA, Eclipse, VS Code…) – bất kỳ công cụ nào cho phép bạn chạy phương thức `main`.
- Tùy chọn: file giấy phép nếu bạn không muốn dấu watermark đánh giá.

Nếu bạn đã có những thứ trên, chúng ta có thể nhảy thẳng vào mã.

## Bước 1: Chèn biểu đồ tròn với Aspose.Words

Điều đầu tiên chúng ta làm là **insert pie chart** vào một tài liệu mới. Bước này đặt nền tảng cho mọi thứ khác, vì đối tượng biểu đồ cho phép chúng ta truy cập vào series, data points và các tinh chỉnh hiển thị.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` không chỉ tạo biểu đồ mà còn trả về một đối tượng `Chart` mà chúng ta có thể thao tác. Các tham số width và height cho phép bạn **customize chart size** ngay khi tạo, vì vậy không cần phải thay đổi kích thước sau này.

## Bước 2: Tạo biểu đồ donut (tùy chọn)

Nếu thiết kế của bạn yêu cầu một lỗ ở giữa—như biểu đồ donut cổ điển—Aspose làm điều này chỉ trong một dòng. Cùng một instance `Chart` có thể chuyển từ pie thông thường sang donut bằng cách điều chỉnh kích thước lỗ.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** Kích thước lỗ chỉ có hiệu lực với `ChartType.DONUT`. Nếu bạn giữ loại là `PIE`, lệnh sẽ bị bỏ qua, vì vậy bạn có thể thoải mái thử nghiệm.

## Bước 3: Định dạng các lát biểu đồ tròn

Một hình ảnh tốt thường làm nổi bật một lát cụ thể. Ở đây chúng ta **format pie chart** bằng cách “nổ” (explode) lát đầu tiên ra 20 điểm. Điều này thu hút mắt người đọc tới dữ liệu quan trọng nhất.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** Bạn có thể lặp qua `pieChart.getSeries()` nếu có nhiều series và đặt màu, viền hoặc nhãn dữ liệu riêng cho từng series. Đó là cách **format chart Word** tài liệu với kiểu dáng phong phú.

## Bước 4: Thêm dữ liệu vào biểu đồ

Một biểu đồ không có dữ liệu chỉ là một hình dạng trang trí. Hãy cung cấp cho nó một bộ dữ liệu đơn giản—ví dụ, số liệu bán hàng theo quý.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** Bằng cách thêm rõ ràng các đối tượng `ChartPoint` chúng ta đảm bảo biểu đồ phản ánh logic kinh doanh của mình. Các lệnh `setShowCategoryName` và `setShowValue` là một phần của **formatting the pie chart** để hiển thị cả nhãn và số.

## Bước 5: Tinh chỉnh giao diện (customize chart size & style)

Ngoài kích thước ban đầu, bạn có thể muốn điều chỉnh legend, tiêu đề, hoặc thậm chí phông chữ dùng cho nhãn dữ liệu. Tất cả những điều này thuộc về **customize chart size** và định dạng tổng thể.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** Nếu sau này bạn quyết định xuất tài liệu ra PDF, dữ liệu vector của biểu đồ vẫn giữ độ sắc nét vì kích thước được định nghĩa bằng points, không phải pixel. Đây là lợi thế cho **format chart Word** và các định dạng downstream.

## Bước 6: Lưu và xem tài liệu

Bước cuối cùng đơn giản chỉ cần gọi `doc.save`. Lệnh này ghi một file `.docx` mà bạn có thể mở bằng Microsoft Word, LibreOffice, hoặc bất kỳ trình xem nào hỗ trợ định dạng OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** Mở `PieChart.docx` và bạn sẽ thấy một biểu đồ tròn (hoặc donut) có kích thước vừa phải, với một lát bị nổ, tiêu đề và legend—tất cả được tạo mà không cần chạm vào giao diện người dùng.

### Kết quả mong đợi

| Thành phần | Bạn sẽ thấy |
|------------|-------------|
| Loại biểu đồ | Biểu đồ tròn (hoặc donut nếu `holeSize` > 0) |
| Độ nổ lát | Lát đầu tiên dịch ra 20 pts |
| Legend | Đặt ở phía bên phải |
| Tiêu đề | “Quarterly Sales Distribution” in bold 14 pt |
| Nhãn dữ liệu | Tên danh mục và giá trị hiển thị trên mỗi lát |
| Tài liệu | Tệp Word `.docx` tiêu chuẩn, sẵn sàng chia sẻ |

## Câu hỏi thường gặp & Lưu ý

- **Do I need a license?**  
  Phiên bản đánh giá hoạt động tốt cho việc thử nghiệm, nhưng nó sẽ thêm watermark. Đặt file `aspose.words.lic` của bạn vào classpath để có kết quả sạch sẽ.

- **Can I use this with Maven?**  
  Chắc chắn rồi. Thêm dependency sau vào `pom.xml` của bạn:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  Lặp qua `pieChart.getSeries()` và áp dụng `setExplosion`, `setFillColor`, hoặc các định dạng khác cho từng series. Đó là cách **format pie chart** cho dữ liệu đa chiều.

- **Is the chart editable in Word after generation?**  
  Có—sau khi lưu, bạn có thể mở tài liệu và tự điều chỉnh màu sắc, phông chữ, hoặc thậm chí chuyển biểu đồ tròn thành biểu đồ cột nếu cần.

## Tổng kết

Chúng ta vừa **insert pie chart** vào tài liệu Word bằng Aspose.Words cho Java, đã cho thấy cách **generate doughnut chart**, trình bày nhiều cách **format pie chart**, đề cập đến các thực hành tốt nhất của **format chart Word**, và học cách **customize chart size** để có giao diện chuyên nghiệp. Ví dụ hoàn chỉnh, có thể chạy được ở trên có thể được chèn vào bất kỳ dự án Java nào, mang lại tự động hoá biểu đồ ngay lập tức mà không cần COM interop hay cài đặt Office.

Tiếp theo bạn có thể thử thay đổi nguồn dữ liệu thành cơ sở dữ liệu trực tiếp, thêm màu sắc có điều kiện dựa trên ngưỡng, hoặc xuất cùng tài liệu sang PDF để có báo cáo sẵn in. Mỗi bước đều dựa trên nền tảng chúng ta đã xây dựng, vì vậy quá trình chuyển đổi sẽ rất mượt mà.

Nếu gặp bất kỳ khó khăn nào hoặc có ý tưởng cải tiến—có thể là biểu đồ cột chồng hoặc biểu đồ đường—hãy để lại bình luận bên dưới. Chúc bạn vẽ biểu đồ vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây liên quan chặt chẽ và mở rộng các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Định dạng số của nhãn dữ liệu trong biểu đồ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Định dạng số cho trục trong biểu đồ](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}