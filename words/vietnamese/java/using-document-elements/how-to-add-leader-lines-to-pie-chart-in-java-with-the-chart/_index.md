---
category: general
date: 2026-08-20
description: Thêm các đường dẫn vào biểu đồ tròn trong Java một cách nhanh chóng.
  Học cách chèn, tách, thay đổi màu và gắn nhãn cho các phần bằng API Chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: vi
lastmod: 2026-08-20
og_description: Thêm các đường nối vào biểu đồ tròn trong Java với một ví dụ ngắn
  gọn. Hãy làm theo hướng dẫn này để chèn, tách, thay đổi màu và gắn nhãn cho các
  lát cắt bằng API Chart.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Thêm các đường dẫn vào biểu đồ tròn trong Java – hướng dẫn API Chart từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Cách thêm các đường dẫn vào biểu đồ tròn trong Java bằng Chart API
url: /vi/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm leader lines vào biểu đồ tròn trong Java với Chart API

Nếu bạn cần **thêm leader lines vào biểu đồ tròn** trong Java, hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình. Bạn sẽ thấy cách chèn một biểu đồ tròn, nổ tung một lát để nhấn mạnh, thay đổi màu sắc của nó, và cuối cùng bật leader lines để gắn nhãn cho phần đã nổ.

Ví dụ sử dụng Chart API tiêu chuẩn có trong nhiều thư viện báo cáo Java. Không cần công cụ bên ngoài, và mã chạy trên bất kỳ môi trường JDK 8+ nào.

## Những gì bạn sẽ đạt được

* Tạo một `Chart` loại `ChartType.PIE` với kích thước tùy chỉnh.  
* Nổ tung (explode) lát đầu tiên để thu hút sự chú ý.  
* Đặt màu sector của lát đã nổ thành màu xanh dương.  
* **Thêm leader lines vào biểu đồ tròn** để nhãn của lát được kết nối rõ ràng.

Bạn nên đã có một dự án Java với thư viện Chart trong classpath. Nếu bạn đang dùng Maven, thêm phụ thuộc được hiển thị trong phần yêu cầu trước.

## Yêu cầu trước

* JDK 8 hoặc mới hơn đã được cài đặt.  
* Thư viện Chart (ví dụ, `com.example.chart:chart-api:2.5.0`).  
* Kiến thức cơ bản về các lớp Java và các lời gọi phương thức.

---

## Cách thêm leader lines vào biểu đồ tròn

Dưới đây là một chương trình đầy đủ, có thể chạy được, minh họa mọi bước. Mã được viết tự chứa để bạn có thể sao chép, dán và chạy mà không cần sửa đổi.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Giải thích từng bước

| Step | What the code does | Why it matters |
|------|-------------------|----------------|
| **1️⃣ Chèn một biểu đồ tròn** | `builder.insertChart(ChartType.PIE, 400, 300)` tạo một biểu đồ tròn kích thước 400 × 300 pixel. | Thiết lập container cho biểu đồ và xác định kích thước, ảnh hưởng đến vị trí nhãn và độ dài leader line. |
| **2️⃣ Nổ tung lát đầu tiên** | `setExplosion(20)` dịch lát ra 20 % của bán kính. | Lát nổ tung thu hút mắt người xem và làm cho leader line hiển thị. |
| **3️⃣ Đặt màu sector** | `setSectorColor(Color.BLUE)` thay đổi màu nền của lát thành màu xanh dương. | Độ tương phản màu cải thiện khả năng đọc, đặc biệt khi lát được làm nổi bật. |
| **4️⃣ Bật leader lines** | `setLeaderLines(true)` bật các đường kết nối liên kết lát với nhãn của nó. | Leader lines đảm bảo nhãn vẫn đọc được ngay cả khi lát được di chuyển ra ngoài. |

Lệnh `saveAsPng` là tùy chọn nhưng hữu ích để xác minh kết quả hình ảnh. Sau khi chạy chương trình, bạn sẽ thấy một hình ảnh tương tự như dưới đây.

![Thêm leader lines vào biểu đồ tròn](https://example.com/assets/pie-leader-lines.png "Thêm leader lines vào biểu đồ tròn – lát nổ với màu xanh dương và leader lines")

*Hình: Một biểu đồ tròn trong đó lát đầu tiên được nổ, màu xanh dương, và được kết nối với nhãn bằng một leader line.*

## Tùy chỉnh leader lines (nâng cao)

Lệnh `setLeaderLines(true)` cơ bản sử dụng kiểu mặc định của thư viện. Bạn có thể kiểm soát thêm giao diện:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Các tùy chọn này hữu ích khi bạn cần phù hợp với thương hiệu công ty hoặc cải thiện khả năng truy cập.

### Xử lý nhiều series

Nếu biểu đồ tròn của bạn có hơn một series, bạn có thể muốn leader lines chỉ cho một lát cụ thể. Sử dụng chỉ mục series để nhắm mục tiêu phần tử đúng:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Khi một lát không được nổ, leader line thường bị ẩn tự động, nhưng bạn có thể buộc hiển thị bằng `setLeaderLineEnabled(true)`.

## Những lỗi thường gặp và cách tránh

| Pitfall | Symptom | Fix |
|--------|---------|-----|
| **Leader lines không hiển thị** | Biểu đồ hiển thị mà không có các đường kết nối. | Đảm bảo lát được nổ (`setExplosion` > 0) hoặc bật rõ ràng leader lines trên lát. |
| **Nhãn chồng lên nhau** | Các nhãn va chạm nhau. | Tăng kích thước biểu đồ hoặc đặt `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Màu không được áp dụng** | Lát vẫn giữ màu mặc định. | Xác minh bạn đang nhắm đúng chỉ mục series (`getSeries().get(0)`). |
| **Hình ảnh không được lưu** | `saveAsPng` ném ra ngoại lệ. | Kiểm tra quyền ghi cho thư mục đầu ra và thư viện hỗ trợ xuất PNG. |

## Danh sách mã nguồn đầy đủ

Để tiện lợi, dưới đây là toàn bộ tệp nguồn, bao gồm các import và chú thích:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Chạy chương trình này sẽ tạo ra `pie-with-leader-lines.png`, hiển thị một biểu đồ tròn với lát nổ màu xanh dương và các leader line rõ ràng chỉ tới nhãn của lát.

## Kết luận

Bây giờ bạn đã biết cách **thêm leader lines vào biểu đồ tròn** trong Java bằng Chart API. Quy trình gồm chèn một `ChartType.PIE`, nổ tung lát mong muốn, tùy chỉnh màu sắc, và bật leader lines. Với các tùy chọn kiểu dáng tùy chọn, bạn có thể tinh chỉnh màu đường, độ dày và vị trí nhãn để đáp ứng bất kỳ yêu cầu trực quan nào.

Tiếp theo, hãy khám phá các chủ đề liên quan như **pie chart explosion Java**, **set sector color Chart API**, và **builder.insertChart usage** để tạo các biểu đồ phức tạp hơn như donut chart, stacked pie, hoặc bảng điều khiển tương tác.

Bạn có thể tự do thử nghiệm với các chỉ số lát khác nhau, màu sắc và kiểu leader‑line—biểu đồ của bạn sẽ trở nên thông tin hơn và hấp dẫn hơn về mặt hình ảnh với mỗi thay đổi. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ, hoạt động với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Thêm giá trị ngày giờ vào trục của biểu đồ](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Chèn biểu đồ cột trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}