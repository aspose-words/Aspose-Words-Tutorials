---
category: general
date: 2026-07-20
description: Cách chèn biểu đồ tròn trong Word bằng Aspose.Words. Tìm hiểu cách thêm
  nhãn dữ liệu phần trăm và hiển thị tỷ lệ phần trăm trên biểu đồ cho tài liệu chuyên
  nghiệp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: vi
lastmod: 2026-07-20
og_description: cách chèn biểu đồ tròn trong Word bằng Aspose.Words. Hướng dẫn này
  cho thấy cách thêm phần trăm nhãn dữ liệu và hiển thị tỷ lệ phần trăm trên biểu
  đồ chỉ trong vài dòng.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: cách chèn biểu đồ tròn trong Word – hướng dẫn nhanh
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Cách chèn biểu đồ tròn trong Word – thêm nhãn dữ liệu phần trăm
url: /vi/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cách chèn biểu đồ tròn trong Word – thêm nhãn dữ liệu phần trăm

Bạn đã bao giờ tự hỏi **cách chèn biểu đồ tròn** vào tài liệu Word mà không phải vật lộn với giao diện người dùng chưa? Bạn không phải là người duy nhất. Trong nhiều tình huống báo cáo, bạn cần *thêm biểu đồ tròn vào Word* và, quan trọng hơn, **hiển thị phần trăm trên biểu đồ tròn** để người đọc ngay lập tức nắm bắt được phân bố dữ liệu.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình bằng cách sử dụng Aspose.Words for Java. Khi kết thúc, bạn sẽ biết chính xác cách **thêm nhãn dữ liệu phần trăm**, **hiển thị phần trăm trên biểu đồ**, và có được một biểu đồ tròn hoàn thiện ngay từ lần đầu. Không cần plugin bổ sung, không cần chỉnh sửa thủ công—chỉ cần đoạn mã sạch sẽ mà bạn có thể đưa vào bất kỳ dự án nào.

---

## Yêu cầu trước

- Java 17 (hoặc mới hơn) – phiên bản LTS hiện tại mà Aspose.Words hỗ trợ.  
- Aspose.Words for Java 24.x (phiên bản mới nhất tại thời điểm viết, tháng 7 2026).  
- Một môi trường Maven hoặc Gradle cơ bản để tải thư viện.  
- Một IDE bạn thích (IntelliJ IDEA, Eclipse, VS Code… bất kỳ đều được).

Nếu bạn đã có những thứ này, tuyệt vời—hãy bắt đầu.

---

## Bước 1: Thiết lập dự án và nhập thư viện

Đầu tiên, thêm phụ thuộc Aspose.Words vào `pom.xml` (Maven) hoặc `build.gradle` (Gradle). Điều này cho phép bạn truy cập các lớp `Document`, `DocumentBuilder` và các lớp biểu đồ.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Giữ phiên bản luôn cập nhật; các bản phát hành mới thường bổ sung các sửa lỗi liên quan đến biểu đồ giúp **hiển thị phần trăm trên biểu đồ** đáng tin cậy hơn.

---

## Bước 2: Tạo tài liệu Word mới và một builder

Builder là công cụ đa năng của bạn để chèn nội dung. Ở đây chúng ta tạo một tài liệu mới và gắn một `DocumentBuilder` vào nó.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Tại sao chúng ta cần một builder? Nó trừu tượng hoá các cấu trúc OpenXML cấp thấp, cho phép chúng ta tập trung vào *điều gì* chúng ta muốn—như **thêm biểu đồ tròn vào word**—thay vì *cách* XML trông như thế nào.

---

## Bước 3: Chèn biểu đồ tròn

Bây giờ là phần cốt lõi của **cách chèn biểu đồ tròn**. Chúng ta yêu cầu builder đặt một biểu đồ tròn với kích thước cụ thể. Các kích thước được tính bằng điểm (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Ở thời điểm này biểu đồ còn trống, nhưng chỗ giữ chỗ đã có trong tài liệu. Bạn vừa **thêm biểu đồ tròn vào word** một cách lập trình.

---

## Bước 4: Đổ dữ liệu vào biểu đồ

Biểu đồ tròn cần ít nhất một chuỗi giá trị. Hãy cung cấp cho nó một số dữ liệu mẫu đại diện cho thị phần.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Nếu bạn cần nhiều chuỗi (biểu đồ tròn chồng, donut, v.v.) bạn có thể gọi `pieChart.getSeries().add()` và lặp lại các bước. Logic tương tự áp dụng khi bạn muốn **hiển thị phần trăm trên biểu đồ** cho mỗi lát.

---

## Bước 5: **add data label percent** – hiển thị phần trăm trên các lát

Đây là phần mà hầu hết các nhà phát triển quên: cấu hình nhãn dữ liệu để hiển thị phần trăm. Nếu không, biểu đồ chỉ hiển thị số thô, có thể gây nhầm lẫn.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

Lệnh `setShowPercent(true)` báo cho Aspose.Words render nhãn dưới dạng “30 %”, “45 %”, v.v. Đó chính là cách bạn **hiển thị phần trăm trên biểu đồ tròn** mà không cần bất kỳ định dạng bổ sung nào.

---

## Bước 6: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn `.docx`, `.pdf`, hoặc thậm chí `.html`. Trong hướng dẫn này chúng ta sẽ giữ định dạng hiện đại `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Chạy chương trình, mở `PieChartDemo.docx`, và bạn sẽ thấy một biểu đồ tròn được render gọn gàng với nhãn phần trăm trên mỗi lát.

---

## Kết quả mong đợi

Dưới đây là ảnh chụp màn hình của tệp Word đã tạo. Lưu ý mỗi lát hiển thị phần chia sẻ của nó dưới dạng phần trăm—đúng như chúng ta mong muốn khi thiết lập **add data label percent**.

![Ảnh chụp màn hình tài liệu Word chứa biểu đồ tròn với nhãn phần trăm](/images/pie-chart-percent.png){.center width=600px alt="Ảnh chụp màn hình cho thấy cách chèn biểu đồ tròn trong Word với nhãn phần trăm"}

*Văn bản thay thế bao gồm từ khóa chính, đáp ứng cả SEO và khả năng truy cập.*

---

## Câu hỏi thường gặp & xử lý các trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Tôi có thể thay đổi phông chữ của nhãn phần trăm không?** | Có. Sau khi bật `setShowPercent(true)`, lấy đối tượng `DataLabel` và điều chỉnh thuộc tính `Font` của nó (`dataLabel.getFont().setSize(10);`). |
| **Nếu tôi cần biểu đồ donut thay vì biểu đồ tròn thì sao?** | Thay `ChartType.PIE` bằng `ChartType.DOUGHNUT` trong lời gọi `insertChart`. Logic **add data label percent** vẫn hoạt động. |
| **Các phiên bản Word cũ hơn (2007‑2010) có hiển thị phần trăm đúng không?** | Aspose.Words ghi XML nền tảng theo cách không phụ thuộc vào phiên bản, vì vậy phần trăm sẽ hiển thị trong bất kỳ Word nào hỗ trợ biểu đồ (2007+). |
| **Làm thế nào để thêm tiêu đề cho biểu đồ?** | Sử dụng `pieChart.getTitle().setText("Market Share");` trước khi lưu. |
| **Tôi có thể chèn biểu đồ vào một đoạn văn hoặc ô bảng cụ thể không?** | Chắc chắn. Di chuyển `DocumentBuilder` đến vị trí mong muốn (`builder.moveToParagraph(index, true);` hoặc `builder.moveToCell(table, row, column, true);`) trước khi gọi `insertChart`. |

---

## Mẹo và thủ thuật thực tế

- **Mẹo:** Nếu bạn dự định tạo nhiều biểu đồ trong một vòng lặp, hãy tái sử dụng một thể hiện `DocumentBuilder` duy nhất; nó giảm việc tiêu tốn bộ nhớ.  
- **Cảnh báo:** Các lát rất nhỏ (< 2 %). Aspose.Words có thể bỏ qua nhãn để tránh lộn xộn; bạn có thể buộc hiển thị bằng `dataLabel.setShowLabel(true);`.  
- **Lưu ý hiệu năng:** Việc render biểu đồ tốn CPU. Đối với việc tạo báo cáo hàng loạt, hãy cân nhắc đa luồng nhưng đảm bảo mỗi luồng làm việc trên một thể hiện `Document` riêng.  
- **Kiểm tra phiên bản:** Phương thức `setShowPercent` được giới thiệu trong Aspose.Words 22.8. Nếu bạn đang dùng phiên bản cũ hơn, hãy nâng cấp hoặc tự tính phần trăm và đặt chúng làm nhãn tùy chỉnh.  

---

## Tóm tắt

Chúng ta đã đề cập **cách chèn biểu đồ tròn** vào tài liệu Word bằng Aspose.Words, chỉ cho bạn cách **add data label percent**, và trình bày cách dễ nhất để **hiển thị phần trăm trên biểu đồ**. Chỉ với vài dòng Java, bạn có thể **thêm biểu đồ tròn vào word** và **hiển thị phần trăm trên biểu đồ tròn**, biến các con số thô thành hình ảnh dễ hiểu ngay lập tức.

---

## Tiếp theo là gì?

- Thử nghiệm các loại biểu đồ khác (`BAR`, `LINE`, `AREA`) và xem cách logic **add data label percent** áp dụng.  
- Kết hợp biểu đồ với bảng để có báo cáo phong phú hơn—Aspose.Words giúp đặt biểu đồ bên cạnh bảng dữ liệu một cách dễ dàng.  
- Khám phá xuất cùng tài liệu sang PDF hoặc HTML để xem cách phần trăm được hiển thị trên các định dạng.

Bạn có thể tự do điều chỉnh kích thước, màu sắc, hoặc nguồn dữ liệu (ví dụ: truy vấn cơ sở dữ liệu) và xem báo cáo Word của bạn trở nên sống động. Nếu gặp khó khăn, hãy để lại bình luận bên dưới—chúc bạn vẽ biểu đồ vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có ví dụ mã hoàn chỉnh và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn biểu đồ cột trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Chèn biểu đồ khu vực trong tài liệu Word \| Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Chèn biểu đồ bong bóng trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}