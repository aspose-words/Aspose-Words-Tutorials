---
category: general
date: 2026-10-26
description: Tạo biểu đồ donut và chèn biểu đồ tròn trong Java với mã hướng dẫn từng
  bước. Tìm hiểu quy trình làm việc đầy đủ cho các biểu đồ linh hoạt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: vi
lastmod: 2026-10-26
og_description: Tạo biểu đồ bánh donut trong Java với hướng dẫn này, đồng thời chỉ
  cách chèn biểu đồ tròn để có các biểu đồ linh hoạt.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Tạo biểu đồ bánh donut và chèn biểu đồ tròn – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Cách tạo biểu đồ donut và chèn biểu đồ tròn
url: /vi/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ donut và chèn biểu đồ tròn

Nếu bạn cần **tạo biểu đồ donut** trong Java, hướng dẫn này sẽ dẫn bạn qua các bước chính xác. Chúng tôi cũng sẽ chỉ cách **chèn biểu đồ tròn** bằng cùng một API builder, để bạn có thể chuyển đổi giữa các kiểu hiển thị một cách dễ dàng. Khi hoàn thành, bạn sẽ có một chương trình đầy đủ, có thể chạy được, tạo ra cả hai loại biểu đồ và minh họa các tùy chỉnh phổ biến.

Hướng dẫn bao gồm:

* Khởi tạo builder biểu đồ do thư viện đã chọn cung cấp.  
* Tạo biểu đồ donut và cấu hình kích thước lỗ.  
* Chèn biểu đồ tròn và “nổ” một lát bánh để nhấn mạnh.  
* Mẹo xử lý các trường hợp đặc biệt như thiếu series hoặc loại biểu đồ không được hỗ trợ.

Bạn chỉ cần một JDK mới (8 trở lên) và file JAR của thư viện biểu đồ trong classpath. Không cần dịch vụ bên ngoài.

---

## Yêu cầu trước

| Mục | Lý do |
|------|--------|
| Java Development Kit (JDK) 8+ | Cần thiết để biên dịch và chạy ví dụ. |
| Thư viện biểu đồ (ví dụ: **Aspose.Cells for Java** hoặc **JFreeChart**) | Cung cấp `ChartBuilder`, `ChartType` và các phương thức thao tác series được sử dụng trong mã. |
| Một IDE hoặc trình soạn thảo văn bản | Để viết và thực thi file nguồn Java. |

Đảm bảo file JAR của thư viện đã được thêm vào đường dẫn build của dự án. Nếu bạn dùng Maven, thêm dependency phù hợp; nếu không, đặt JAR vào thư mục `libs` và tham chiếu khi biên dịch.

---

## Bước 1: Thiết lập builder biểu đồ

Bước đầu tiên là tạo một thể hiện `ChartBuilder` (hoặc tương đương) sẽ tạo ra các đối tượng biểu đồ. Đối tượng này hoạt động như một nhà máy và giữ worksheet hoặc canvas nơi biểu đồ sẽ được đặt.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Tại sao lại quan trọng:**  
Builder liên kết biểu đồ với một worksheet cụ thể, đảm bảo rằng tất cả các đối tượng biểu đồ sau này chia sẻ cùng một bề mặt vẽ. Bỏ qua bước này sẽ khiến bạn không có vị trí mục tiêu cho các thành phần hình ảnh.

---

## Bước 2: **Tạo biểu đồ donut**

Bây giờ chúng ta tạo một biểu đồ donut với kích thước lỗ đã định. Kích thước lỗ quyết định phần trung tâm của biểu đồ trống bao nhiêu, biến một biểu đồ tròn thông thường thành donut.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Giải thích:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` tạo đối tượng biểu đồ và dành không gian trên worksheet.  
* `setHoleSize(30)` chuyển biểu đồ tròn thành donut với trung tâm trống 30 %.  
* `add("{10, 20, 30, 40}", true)` cung cấp bốn điểm dữ liệu; cờ `true` báo cho thư viện coi các giá trị là một series duy nhất.

**Trường hợp đặc biệt:** Nếu loại biểu đồ đã chọn không hỗ trợ lỗ (ví dụ: biểu đồ cột), việc gọi `getDoughnutChart()` sẽ ném ra ngoại lệ. Luôn kiểm tra loại biểu đồ trước khi điều chỉnh kích thước lỗ.

---

## Bước 3: **Chèn biểu đồ tròn**

Sau khi donut đã sẵn sàng, chúng ta sẽ minh họa cách **chèn biểu đồ tròn** bằng cùng một builder. Bước này nhấn mạnh sự tương đồng giữa hai loại biểu đồ và cách làm nổi bật một lát bánh.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Giải thích:**  

* `ChartType.PIE` báo cho builder tạo một biểu đồ tròn cổ điển.  
* `setExplode(10)` dịch chuyển lát bánh đầu tiên đi 10 % bán kính, là kỹ thuật thường dùng để làm nổi bật một điểm dữ liệu quan trọng.  

**Mẹo:** Phương thức `setExplode` chỉ hoạt động trên series đầu tiên của biểu đồ tròn. Nếu bạn có nhiều series, cần chỉ định chỉ số phù hợp.

---

## Bước 4: Lưu workbook

Cuối cùng, ghi workbook ra file để bạn có thể xem các biểu đồ trong Excel hoặc bất kỳ trình xem tương thích nào.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Tại sao lưu ở bước này:** Việc lưu workbook hoàn thiện tất cả các thao tác vẽ. Cố gắng mở file trước khi lưu sẽ dẫn đến tài liệu rỗng hoặc không đầy đủ.

**Kết quả:** Mở *DoughnutAndPieChart.xlsx* sẽ hiển thị một biểu đồ donut có lỗ 30 % ở phía trái và một biểu đồ tròn với lát bánh đầu tiên “nổ” ở phía phải.

---

## Bước 5: Các biến thể phổ biến và khắc phục sự cố

| Tình huống | Điều chỉnh |
|-----------|------------|
| **Kích thước biểu đồ khác nhau** | Thay đổi các đối số width và height trong `insertChart`. |
| **Nhiều series dữ liệu** | Gọi `add` nhiều lần hoặc truyền một chuỗi mảng 2‑D. |
| **Kích thước lỗ động** | Tính kích thước lỗ dựa trên phạm vi dữ liệu, sau đó gọi `setHoleSize`. |
| **Nổ nhiều lát bánh** | Dùng vòng lặp `chart.getSeries().get(i).setExplode(percent)` cho mỗi lát bánh muốn dịch chuyển. |
| **Thư viện không hỗ trợ donut** | Dùng biểu đồ tròn và tự vẽ một vòng tròn màu trắng lên trên, dù cách này kém chính xác. |

**Mẹo chuyên nghiệp:** Luôn gọi `builder.flush()` (nếu có) sau khi chèn biểu đồ khi làm việc với workbook lớn. Điều này giải phóng bộ đệm nội bộ và ngăn ngừa rò rỉ bộ nhớ.

---

![Mã Java tạo biểu đồ donut và chèn biểu đồ tròn](https://example.com/images/doughnut-pie-java.png "ví dụ tạo biểu đồ donut trong Java")

*Hình ảnh minh họa bố cục workbook cuối cùng với cả hai biểu đồ đặt cạnh nhau.*

---

## Kết luận

Bây giờ bạn đã biết cách **tạo biểu đồ donut** và **chèn biểu đồ tròn** trong Java bằng một API builder mượt mà. Ví dụ đầy đủ bao gồm khởi tạo, cấu hình kích thước, thiết lập lỗ, “nổ” lát bánh và xuất file. Từ đây, bạn có thể khám phá thêm các tùy chỉnh như màu sắc, chú giải và nhãn dữ liệu để đáp ứng yêu cầu báo cáo của mình.

**Bước tiếp theo**

* Thử nghiệm các tính năng **chart customization Java** như gradient fill và data labels.  
* Tích hợp việc tạo biểu đồ vào một dịch vụ web trả về workbook theo yêu cầu.  
* So sánh cách tiếp cận builder với các thư viện khác (ví dụ: JFreeChart) để chọn giải pháp phù hợp nhất cho dự án của bạn.

Chúc bạn vẽ biểu đồ vui vẻ!


## Bạn nên học gì tiếp theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã nguồn đầy đủ hoạt động cùng các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create doughnut chart in a Word document with Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Save Word document after editing doughnut chart in Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}