---
category: general
date: 2026-08-14
description: Tạo biểu đồ tròn trong Word bằng Java sử dụng Aspose.Words. Tìm hiểu
  cách thêm dữ liệu series vào biểu đồ và xoay một lát biểu đồ tròn chỉ trong vài
  dòng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: vi
lastmod: 2026-08-14
og_description: Tạo biểu đồ tròn trong Word bằng Java sử dụng Aspose.Words. Hướng
  dẫn này cho thấy cách thêm dữ liệu chuỗi vào biểu đồ và xoay nhanh lát biểu đồ tròn.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Tạo biểu đồ tròn trong Word bằng Java – hướng dẫn lập trình đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Tạo biểu đồ tròn trong Word bằng Java – hướng dẫn từng bước
url: /vi/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo biểu đồ tròn trong Word bằng Java – hướng dẫn từng bước

Nếu bạn cần **tạo biểu đồ tròn trong Word** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Java và Aspose.Words. Bạn sẽ học toàn bộ quy trình, từ việc chèn biểu đồ đến thêm các điểm dữ liệu và xoay lát đầu tiên.

Việc tạo biểu đồ trực tiếp trong tệp `.docx` loại bỏ bước sao chép‑dán thủ công và cho phép bạn tự động hoá báo cáo, hoá đơn hoặc bảng điều khiển. Trong quá trình này, chúng ta cũng sẽ đề cập tới **cách thêm dữ liệu series vào biểu đồ** và **cách xoay lát biểu đồ tròn** để nhấn mạnh trực quan hơn.

## Tạo biểu đồ tròn trong Word – tổng quan

Aspose.Words for Java cung cấp API `DocumentBuilder` dạng fluent, cho phép chèn một đối tượng biểu đồ vào tài liệu Word. Loại biểu đồ bạn chọn sẽ quyết định bố cục mặc định, và bạn có thể tùy chỉnh series, màu sắc, góc, thậm chí chuyển sang dạng bánh donut chỉ bằng một lời gọi phương thức.

### Tại sao nên dùng Aspose.Words?

* **Không cần Microsoft Office** – thư viện hoạt động trên bất kỳ máy chủ hoặc môi trường CI nào.  
* **Độ chính xác .docx đầy đủ** – biểu đồ được tạo ra trông giống hệt biểu đồ tạo thủ công trong Word.  
* **Phụ thuộc một tệp duy nhất** – chỉ cần thêm JAR là đã sẵn sàng sử dụng.

## Cách thêm dữ liệu series vào biểu đồ

Một biểu đồ không có dữ liệu chỉ là một khung trống. Đối tượng `Chart` cung cấp một collection `Series`; mỗi series chứa danh sách các giá trị số tương ứng với các lát (đối với biểu đồ tròn) hoặc các điểm (đối với biểu đồ đường). Thêm dữ liệu rất đơn giản:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Giải thích mã:**  
* `chart.getSeries()` trả về một `List<ChartSeries>`.  
* `get(0)` chọn series đầu tiên vì biểu đồ tròn chỉ có một series theo định nghĩa.  
* `add(double)` thêm một điểm dữ liệu. Các giá trị sẽ tự động được chuyển đổi thành phần trăm sao cho tổng bằng 100 % khi biểu đồ được render.

> **Mẹo chuyên nghiệp:** Nếu nguồn dữ liệu của bạn có hơn ba danh mục, cứ tiếp tục thêm giá trị theo cùng cách. Aspose.Words sẽ tự động tạo các lát bổ sung.

## Xoay lát biểu đồ tròn

Đôi khi bạn muốn một lát cụ thể bắt đầu ở một góc nhất định để phần quan trọng nhất hướng về phía người xem. Phương thức `setFirstSliceAngle(double)` xoay toàn bộ biểu đồ, thực chất di chuyển vị trí bắt đầu của lát đầu tiên:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Góc được đo bằng độ, theo chiều kim đồng hồ từ trục dọc. Đặt giá trị `0` (mặc định) sẽ đặt lát đầu tiên ở vị trí trên cùng. Điều chỉnh giá trị để làm nổi bật một lát hoặc để phù hợp với quy chuẩn thiết kế.

> **Câu hỏi thường gặp:** *Việc xoay có ảnh hưởng tới thứ tự dữ liệu không?*  
> Không. Thứ tự dữ liệu vẫn giữ nguyên; chỉ vị trí bắt đầu hiển thị thay đổi.

## Ví dụ Java đầy đủ

Dưới đây là một chương trình hoàn chỉnh, sẵn sàng chạy, tạo tài liệu Word có biểu đồ tròn, thêm dữ liệu series, xoay lát và lưu tệp. Tất cả các import cần thiết đã được liệt kê, vì vậy bạn có thể sao chép mã vào bất kỳ IDE nào.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Kết quả mong đợi

* Một tệp có tên **PieChart.docx** sẽ xuất hiện trong thư mục `output`.  
* Mở tệp trong Microsoft Word sẽ hiển thị một biểu đồ tròn màu sắc với ba lát (40 %, 30 %, 30 %).  
* Biểu đồ được xoay 45° theo chiều kim đồng hồ, vì vậy lát đầu tiên bắt đầu hơi sang phải so với trục dọc.

## Những lỗi thường gặp và cách khắc phục

| Vấn đề | Nguyên nhân | Giải pháp |
|-------|------------|----------|
| **Biểu đồ hiển thị trống** | Tài liệu được lưu trước khi biểu đồ được render hoàn toàn. | Gọi `doc.save()` **sau** khi đã thực hiện mọi thay đổi trên biểu đồ. |
| **Giá trị lát không cộng lại 100 %** | Thêm các số thô không phải là phần trăm có thể gây tỷ lệ không mong muốn. | Cung cấp các giá trị đại diện cho tỉ lệ của một tổng thể, hoặc để Aspose.Words tự tính phần trăm. |
| **Xoay không có hiệu lực** | Sử dụng `ChartType.DOUGHNUT` mà không đặt `holeSize` có thể ẩn hiệu ứng xoay. | Giữ biểu đồ ở dạng `PIE` hoặc điều chỉnh `holeSize` sau khi đặt góc. |
| **Lỗi đường dẫn tệp** | Đường dẫn tương đối có thể được giải quyết khác nhau trên Windows và Linux. | Sử dụng `Paths.get("output", "PieChart.docx").toString()` hoặc đường dẫn tuyệt đối cho mã sản xuất. |

### Mẹo cho môi trường production

* **Tái sử dụng `DocumentBuilder`** – bạn có thể chèn nhiều biểu đồ trong cùng một tài liệu bằng cách gọi `insertChart` nhiều lần.  
* **Định dạng** – dùng `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` để hiển thị phần trăm trực tiếp trên biểu đồ.  
* **Hiệu năng** – tạo biểu đồ một lần và sao chép nó (`chart.deepClone()`) nếu cần các biểu đồ giống hệt ở nhiều vị trí.

## Xoay lát biểu đồ tròn – các kịch bản nâng cao

* **Góc động** – tính góc dựa trên dữ liệu (ví dụ, làm lát lớn nhất bắt đầu ở trên cùng).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Nhiều series** – mặc dù biểu đồ tròn thường chỉ có một series, Aspose.Words cho phép bạn thêm nhiều series để tạo biểu đồ tròn chồng. Việc xoay vẫn chỉ áp dụng cho series đầu tiên.

## Kết luận

Bây giờ bạn đã biết cách **tạo biểu đồ tròn trong Word** bằng Java, cách **thêm dữ liệu series vào biểu đồ**, và cách **xoay lát biểu đồ tròn** để nhấn mạnh trực quan. Ví dụ đầy đủ minh họa toàn bộ quy trình—from khởi tạo tài liệu đến lưu tệp `.docx` cuối cùng—giúp bạn tích hợp việc tạo biểu đồ vào bất kỳ pipeline báo cáo tự động nào.

### Tiếp theo bạn nên làm gì?

* Khám phá các loại biểu đồ khác (`ChartType.BAR`, `ChartType.LINE`) để mở rộng bộ công cụ tự động hoá.  
* Kết hợp tạo biểu đồ với **mail merge** để tạo báo cáo cá nhân hoá cho từng người nhận.  
* Tìm hiểu sâu hơn **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) để phù hợp với bộ nhận diện thương hiệu của công ty.

Hãy thoải mái thử nghiệm với các bộ dữ liệu, góc và kiểu biểu đồ khác nhau. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}