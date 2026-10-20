---
category: general
date: 2026-09-18
description: Tìm hiểu cách tạo biểu đồ dạng tròn trong tài liệu Word bằng Java, thêm
  nhãn dữ liệu cho biểu đồ và chèn dữ liệu chuỗi với một ví dụ mã đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: vi
lastmod: 2026-09-18
og_description: Tạo biểu đồ dạng tròn trong tài liệu Word bằng Java, thêm nhãn dữ
  liệu cho biểu đồ và chèn dữ liệu chuỗi trong một hướng dẫn duy nhất.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Tạo biểu đồ dạng tròn trong Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Cách tạo biểu đồ radial trong tài liệu Word bằng Java
url: /vi/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ radial trong tài liệu Word bằng Java

Nếu bạn cần tạo biểu đồ radial trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn các bước cụ thể. Bạn cũng sẽ học cách thêm nhãn dữ liệu cho biểu đồ và chèn dữ liệu series để biểu đồ sẵn sàng cho việc trình bày.

Việc tạo biểu đồ bằng chương trình loại bỏ công việc định dạng thủ công và đảm bảo tính nhất quán trong các báo cáo. Bài hướng dẫn giả định bạn có kiến thức cơ bản về Java và đã cài đặt phiên bản mới của thư viện Aspose.Words for Java.

## Những gì bạn cần

* Java 17 hoặc mới hơn  
* Aspose.Words for Java (phiên bản 23.12 hoặc mới hơn)  
* Một IDE hoặc công cụ xây dựng có thể giải quyết các phụ thuộc Maven/Gradle  

Khi đã cài đặt các yêu cầu trước này, bạn có thể chạy ví dụ mà không cần cấu hình bổ sung.

## Cách tạo biểu đồ radial trong tài liệu Word

Bước đầu tiên là tạo một tệp Word trống sẽ chứa biểu đồ. Tài liệu trống cung cấp một nền sạch và tránh các kiểu không mong muốn.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp các phương thức để chèn các yếu tố như đoạn văn, bảng và biểu đồ.

## Cách chèn biểu đồ

Tiếp theo bạn chèn biểu đồ. Phương thức `insertChart` tạo một đối tượng biểu đồ và đặt nó tại vị trí con trỏ hiện tại của builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Biểu đồ polar hiển thị các điểm dữ liệu xung quanh một trục trung tâm, rất phù hợp để trình bày thông tin tuần hoàn. Kích thước được biểu diễn bằng điểm (1 pt ≈ 1/72 inch).

## Thêm dữ liệu series vào biểu đồ

Một biểu đồ không có dữ liệu series sẽ trống. Bạn có thể thêm series thủ công hoặc liên kết nó với nguồn dữ liệu. Ví dụ dưới đây thêm một series duy nhất với ba điểm dữ liệu.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` nhận một tên series, một danh sách nhãn danh mục và một danh sách các giá trị số tương ứng. Bạn có thể lặp lại khối này để thêm các series khác (`addSeriesData`).

## Thêm nhãn dữ liệu cho series đầu tiên

Nhãn dữ liệu giúp biểu đồ dễ đọc mà không cần di chuột qua các điểm. Dòng sau bật nhãn giá trị cho series đầu tiên.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Cài đặt `showValue` thành `true` sẽ hiển thị giá trị của mỗi điểm trực tiếp trên biểu đồ. Bạn cũng có thể bật tên danh mục, phần trăm hoặc đường dẫn qua cùng một đối tượng `DataLabelFormat`.

## Lưu tệp Word

Sau khi biểu đồ được cấu hình, ghi tài liệu ra đĩa. Chọn một vị trí mà ứng dụng của bạn có thể truy cập.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Tệp `RadialChart.docx` hiện đã chứa một biểu đồ radial hoạt động đầy đủ với nhãn dữ liệu.

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là một chương trình tự chứa mà bạn có thể sao chép, biên dịch và chạy. Nó minh họa quy trình hoàn chỉnh từ việc tạo tài liệu Word trống đến lưu biểu đồ radial với nhãn dữ liệu.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Kết quả mong đợi**

Khi bạn mở `output/RadialChart.docx` trong Microsoft Word, bạn sẽ thấy một biểu đồ radial có tiêu đề *Quarterly Sales*. Mỗi điểm hiển thị giá trị số của nó (ví dụ, “15000”) bên cạnh dấu đánh dấu.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Thay đổi đề xuất |
|-----------|--------------------|
| Bạn cần một loại biểu đồ khác | Thay thế `ChartType.POLAR` bằng bất kỳ giá trị enum `ChartType` nào khác (ví dụ, `ChartType.COLUMN`). |
| Biểu đồ phải sử dụng một phạm vi Excel bên ngoài | Sử dụng `chart.setDataRange("Sheet1!A1:B5")` sau khi tạo biểu đồ và tải workbook. |
| Bạn muốn ẩn chú giải | `chart.getLegend().setVisible(false);` |
| Tài liệu phải được lưu dưới dạng PDF | Gọi `doc.save("RadialChart.pdf");` – Aspose.Words tự động chuyển đổi biểu đồ. |

Những điều chỉnh này giữ nguyên logic cốt lõi trong khi thích nghi đầu ra với các yêu cầu cụ thể.

## Mẹo chuyên nghiệp

* **Reuse the builder** – Bạn có thể chèn nhiều biểu đồ trong cùng một tài liệu bằng cách gọi `builder.insertChart` liên tục.  
* **Performance** – Khi tạo nhiều biểu đồ, tạo một thể hiện `DocumentBuilder` duy nhất và tái sử dụng nó để giảm chi phí cấp phát đối tượng.  
* **Styling** – Ngoại hình biểu đồ (màu sắc, độ dày đường) được điều khiển qua các phương thức của đối tượng `Chart` như `getSeries().get(i).getFormat()`. Thử nghiệm các cài đặt này để phù hợp với thương hiệu công ty.  

## Kết luận

Bây giờ bạn đã biết cách tạo biểu đồ radial trong tài liệu Word bằng Java, thêm dữ liệu series và nhãn dữ liệu cho biểu đồ trước khi lưu tệp. Ví dụ hoàn chỉnh có thể được mở rộng để xử lý các series bổ sung, kiểu tùy chỉnh hoặc các định dạng đầu ra thay thế.

Khám phá các chủ đề liên quan như **cách chèn biểu đồ** từ nguồn dữ liệu bên ngoài, **tạo tài liệu word trống** với mẫu đã định sẵn, và **thêm dữ liệu series** một cách động từ cơ sở dữ liệu. Thử nghiệm các loại biểu đồ khác nhau để tìm ra hình ảnh nào truyền tải dữ liệu của bạn tốt nhất.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Đặt tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}