---
category: general
date: 2026-07-16
description: Tạo biểu đồ tròn trong Java bằng Aspose.Words. Tìm hiểu cách thêm các
  đường dẫn, hiển thị chú giải biểu đồ và tách một lát bánh trong một hướng dẫn duy
  nhất.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: vi
lastmod: 2026-07-16
og_description: Tạo biểu đồ tròn trong Java bằng Aspose.Words. Hướng dẫn này chỉ cách
  thêm đường dẫn, hiển thị chú giải biểu đồ và tách một lát bánh, mang lại hình ảnh
  chuyên nghiệp trong vài phút.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Tạo biểu đồ tròn với Aspose.Words Java – Hướng dẫn định dạng toàn diện
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Tạo biểu đồ tròn với Aspose.Words Java – Hướng dẫn chi tiết từng bước
url: /vi/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo biểu đồ tròn với Aspose.Words Java – Hướng dẫn chi tiết từng bước

Bạn đã bao giờ tự hỏi làm thế nào để **tạo biểu đồ tròn** một cách lập trình trong Java mà không phải vật lộn với các API vẽ cấp thấp? Bạn không phải là người duy nhất. Nhiều nhà phát triển cần một hình ảnh nhanh cho báo cáo, bảng điều khiển hoặc tài liệu tự động, và họ chọn Aspose.Words vì nó xử lý phần công việc nặng.  

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, không chỉ **tạo một biểu đồ tròn** mà còn cho bạn thấy cách **thêm các đường dẫn (leader lines)**, **hiển thị chú giải biểu đồ**, và thậm chí **bẻ một phần** để nhấn mạnh. Khi kết thúc, bạn sẽ có một tệp `.docx` trông tinh tế đủ để gây ấn tượng với khách hàng.

> **Quick win:** Đoạn mã dưới đây hoạt động ngay lập tức với Aspose.Words for Java 23.9 (hoặc bất kỳ phiên bản mới hơn nào). Không cần phụ thuộc thêm, chỉ cần JAR.

## Những gì bạn sẽ học

- Thiết lập một tài liệu Word trống bằng `DocumentBuilder`.
- Chèn một **biểu đồ tròn** với kích thước tùy chỉnh.
- Sử dụng tính năng **bẻ phần** để làm nổi bật một điểm dữ liệu.
- Bật **đường dẫn (leader lines)** để phần bẻ vẫn được kết nối với nhãn.
- Bật **chú giải biểu đồ** để người đọc có thể ngay lập tức xác định mỗi phần.
- Lưu kết quả vào tệp `.docx` mà bạn có thể mở trong Microsoft Word hoặc LibreOffice.

**Yêu cầu trước** – Bạn sẽ cần:

1. Java 17 (hoặc mới hơn) đã được cài đặt.
2. JAR Aspose.Words for Java trong classpath của bạn.
3. Một IDE hoặc trình soạn thảo cơ bản—IntelliJ IDEA, Eclipse, VS Code, bất kỳ cái nào bạn thích.

Bây giờ, chúng ta cùng bắt đầu.

## Bước 1: Khởi tạo Document và Builder – Chuẩn bị để **tạo biểu đồ tròn**

Đầu tiên, chúng ta cần một canvas tài liệu sạch sẽ. `Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` là công cụ trợ giúp cho phép chúng ta thêm nội dung.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Tại sao điều này quan trọng:** Bắt đầu với một `Document` mới đảm bảo không có kiểu ẩn hoặc các đối tượng còn lại có thể gây cản trở việc hiển thị biểu đồ.

## Bước 2: Chèn **biểu đồ tròn** – Kích thước quan trọng

Aspose.Words cho phép chèn biểu đồ chỉ bằng một dòng lệnh. Ở đây chúng ta yêu cầu một biểu đồ tròn có kích thước 400 × 300 điểm — khoảng 5.5 × 4.2 inch trên một màn hình tiêu chuẩn.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần kích thước khác, chỉ cần thay đổi hai đối số số. API hoạt động bằng điểm, trong đó 72 điểm = 1 inch.

## Bước 3: **Cách bẻ phần** – Nhấn mạnh một điểm dữ liệu quan trọng

Bẻ một phần sẽ kéo nó ra khỏi phần còn lại của biểu đồ tròn, thu hút ánh nhìn của người đọc. Phương thức `setExplosion` nhận một số nguyên đại diện cho khoảng cách tính bằng điểm.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Nếu bạn có nhiều series?** Bạn có thể gọi `setExplosion` trên bất kỳ chỉ mục series nào (`get(1)`, `get(2)`, …) để bẻ các phần khác nhau.

## Bước 4: **Thêm đường dẫn (leader lines)** và **hiển thị chú giải biểu đồ** – Kết nối các điểm

Khi một phần bị bẻ, nhãn có thể trôi ra xa. Các đường dẫn giữ nhãn gắn kết, duy trì khả năng đọc. Đồng thời, một chú giải cung cấp một khóa nhanh cho tất cả các phần.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Tại sao bật các đường dẫn?** Nếu không có chúng, nhãn có thể xuất hiện lơ lửng, gây nhầm lẫn cho người dùng về phần nào nó thuộc về.  
> **Cần vị trí chú giải tùy chỉnh?** Sử dụng `chart.getLegend().setPosition(LegendPosition.TOP)` hoặc bất kỳ giá trị enum nào khác.

## Bước 5: Lưu tài liệu – Bước cuối cùng của **tạo biểu đồ tròn**

Cuối cùng, chúng ta lưu tài liệu vào đĩa. Điều chỉnh đường dẫn tới thư mục mà bạn có quyền ghi.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Chạy chương trình, mở tệp `PieChartDemo.docx` đã tạo, và bạn sẽ thấy một biểu đồ tròn được định dạng đẹp mắt với phần đầu tiên bị bẻ, các đường dẫn và một chú giải hiển thị.

![Ví dụ biểu đồ tròn hiển thị phần bẻ và chú giải](pie-chart-example.png){: .center-image alt="Ví dụ tạo biểu đồ tròn với phần bẻ, đường dẫn và chú giải"}

### Kết quả mong đợi

Khi bạn mở tệp Word, biểu đồ sẽ trông tương tự như sau:

- Một biểu đồ tròn 400 × 300 pt.
- Phần đầu tiên được dịch chuyển 10 pt.
- Một đường dẫn mỏng nối phần bẻ với nhãn của nó.
- Một chú giải dưới biểu đồ liệt kê tên mỗi series.

Nếu bạn không thấy đường dẫn, hãy kiểm tra lại rằng `setLeaderLines(true)` được gọi *sau* thiết lập bẻ phần — thứ tự quan trọng.

## Các lỗi thường gặp và cách tránh

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|----------------|-----|
| **Không có chú giải xuất hiện** | `setShowLegend(true)` đã bị bỏ qua hoặc được gọi trên đối tượng chart sai. | Đảm bảo bạn gọi `chart.setShowLegend(true)` **sau** khi lấy `Chart` từ shape. |
| **Đường dẫn bị thiếu** | Phần không được bẻ, hoặc loại biểu đồ không hỗ trợ đường dẫn. | Chỉ `ChartType.PIE` (hoặc `PIE_3D`) hỗ trợ đường dẫn. Gọi `setExplosion` trước, sau đó `setLeaderLines(true)`. |
| **Phần không di chuyển** | Giá trị bẻ quá thấp (0‑2 pt). | Tăng giá trị nguyên, ví dụ `setExplosion(10)` hoặc cao hơn để có hiệu ứng mạnh hơn. |
| **Biểu đồ bị biến dạng** | Sử dụng kích thước không vuông (width ≠ height) có thể làm biểu đồ tròn bị ép. | Giữ chiều rộng và chiều cao bằng nhau hoặc gần nhau; 400 × 300 hoạt động nhưng 400 × 400 cho vòng tròn hoàn hảo. |

## Tinh chỉnh nâng cao (Tùy chọn)

Nếu bạn muốn đi xa hơn các kiến thức cơ bản, hãy xem xét:

- **Màu tùy chỉnh**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Nhãn dữ liệu**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Hiệu ứng 3‑D**: Thay `ChartType.PIE` bằng `ChartType.PIE_3D`.

Các tùy chọn này cho phép bạn tinh chỉnh hình ảnh để phù hợp với hướng dẫn thương hiệu của công ty.

## Tóm tắt – Những gì chúng ta đã đạt được

Chúng tôi bắt đầu với một tài liệu Word trống, **tạo một biểu đồ tròn**, **bẻ phần đầu tiên**, **thêm các đường dẫn**, và **hiển thị chú giải biểu đồ**. Toàn bộ quy trình được gói gọn trong một phương thức `main` ngắn gọn, giúp dễ dàng nhúng vào các pipeline báo cáo lớn hơn.

## Các bước tiếp theo

- **Thêm nhiều series**: Điền dữ liệu thực vào biểu đồ từ cơ sở dữ liệu hoặc CSV.
- **Xuất ra PDF**: Sử dụng `doc.save("output.pdf", SaveFormat.PDF);` để tạo phiên bản PDF.
- **Kết hợp với các hình dạng khác**: Chèn bảng, hình ảnh hoặc các biểu đồ bổ sung để có một báo cáo đầy đủ.

Nếu bạn muốn khám phá các loại biểu đồ khác—cột, thanh, đường—chỉ cần thay `ChartType.PIE` bằng enum phù hợp và làm theo các bước định dạng tương tự.

---

*Chúc bạn vẽ biểu đồ vui vẻ!* Hãy thoải mái để lại bình luận nếu có gì không hoạt động như mong đợi, hoặc chia sẻ cách bạn tùy chỉnh vị trí chú giải. Phản hồi của bạn giúp chúng ta cùng xây dựng tài liệu tự động tốt hơn.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cách tạo tài liệu PDF với Aspose.Words for Java | Document Processing API](/words/english/java/)
- [Cách thêm Watermark vào tài liệu bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}