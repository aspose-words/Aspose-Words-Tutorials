---
date: 2026-02-16
description: Tìm hiểu cách thêm nhiều chuỗi vào biểu đồ trong Aspose.Words for Java,
  thay đổi dấu tick của trục, áp dụng định dạng số tùy chỉnh và tạo tài liệu Word
  có biểu đồ với biểu đồ đường và cột.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Thêm Nhiều Dãy vào Biểu Đồ trong Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/using-charts/
weight: 12
---

  

Then closing shortcodes.

Let's craft translation.

Be careful to keep markdown formatting.

Proceed to final answer.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Nhiều Dãy Dữ Liệu vào Biểu Đồ trong Aspose.Words for Java

## Giới thiệu về việc sử dụng biểu đồ trong Aspose.Words for Java

Trong hướng dẫn này bạn sẽ học **cách thêm nhiều dãy dữ liệu** vào một biểu đồ bằng Aspose.Words for Java, tại sao việc tùy chỉnh dấu tick của trục và áp dụng định dạng số tùy chỉnh lại quan trọng, và cách tạo một tài liệu Word giàu biểu đồ. Dù bạn cần biểu đồ đường cho dữ liệu tài chính hay biểu đồ cột cho số liệu bán hàng, các bước dưới đây sẽ hướng dẫn bạn tạo, tạo kiểu và tinh chỉnh biểu đồ một cách lập trình.

## Câu trả lời nhanh
- **Làm thế nào để tôi thêm nhiều dãy dữ liệu?** Sử dụng `chart.getSeries().add(...)` cho mỗi dãy mà bạn muốn hiển thị.  
- **Tôi có thể thay đổi dấu tick của trục không?** Có – sử dụng `setMajorTickMark()` và `setMinorTickMark()` trên các đối tượng trục.  
- **Định dạng nào tôi có thể áp dụng cho nhãn dữ liệu?** Bất kỳ định dạng số nào tương thích với Excel, ví dụ `"$"#,##0.00` hoặc `0.00%`.  
- **Các loại biểu đồ nào được hỗ trợ?** Đường, cột, khu vực, bong bóng, phân tán, và nhiều loại khác thông qua `ChartType`.  
- **Có cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép Aspose.Words for Java hợp lệ để sử dụng đầy đủ các chức năng.

## “Thêm nhiều dãy dữ liệu” trong một biểu đồ là gì?
Thêm nhiều dãy dữ liệu có nghĩa là chèn hơn một bộ dữ liệu vào cùng một khu vực biểu đồ, cho phép bạn so sánh các danh mục hoặc khoảng thời gian khác nhau cạnh nhau. Mỗi dãy xuất hiện dưới dạng một đường, cột hoặc bộ dấu chấm riêng, mang lại cho người đọc một câu chuyện trực quan phong phú hơn.

## Tại sao nên dùng Aspose.Words for Java để tạo tài liệu Word có biểu đồ?
- **Kiểm soát toàn diện** loại biểu đồ, bố cục và kiểu dáng mà không cần mở Word thủ công.  
- **Tạo tự động** phù hợp với các quy trình báo cáo tự động.  
- **Đa nền tảng** – hoạt động trên bất kỳ môi trường Java nào tương thích.  
- **API phong phú** để tùy chỉnh trục, nhãn dữ liệu và định dạng số.

## Yêu cầu trước
- Java Development Kit (JDK) 8 hoặc cao hơn.  
- Thư viện Aspose.Words for Java đã được thêm vào dự án của bạn (Maven/Gradle hoặc JAR).  
- Giấy phép Aspose hợp lệ cho môi trường sản xuất (tùy chọn cho việc đánh giá).

## Hướng dẫn chi tiết

### Bước 1: Tạo biểu đồ đường và **thêm nhiều dãy dữ liệu**
Dưới đây là đoạn mã cốt lõi tạo một biểu đồ đường, xóa các dãy mặc định, và sau đó thêm ba dãy riêng biệt với nhãn dữ liệu tùy chỉnh.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

> **Mẹo chuyên nghiệp:** Gọi `chart.getSeries().add(...)` bao nhiêu lần tùy thích để **thêm nhiều dãy dữ liệu** – mỗi lần gọi sẽ tạo một đường (hoặc cột, v.v.) mới trên cùng một biểu đồ.

### Bước 2: **Tạo biểu đồ cột** (create column chart java)
Đoạn mã tiếp theo cho thấy cách chèn một biểu đồ cột đơn giản, hữu ích cho việc so sánh các danh mục cạnh nhau.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Bước 3: **Thay đổi dấu tick của trục** (change axis tick marks)
Tùy chỉnh trục X và Y giúp cải thiện khả năng đọc. Đoạn mã dưới đây minh họa cách thay đổi dấu tick, đảo ngược thứ tự và đặt điểm giao cắt tùy chỉnh.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Bước 4: **Áp dụng định dạng số tùy chỉnh** (apply custom number format)
Bạn có thể định dạng số trên trục hoặc nhãn dữ liệu bằng bất kỳ mẫu nào được Excel hỗ trợ. Dưới đây là ví dụ ngắn gọn định dạng trục Y với mẫu phân cách hàng nghìn.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Bước 5: Tạo tài liệu Word cuối cùng (generate chart word document)
Sau khi cấu hình dãy, trục và nhãn, chỉ cần gọi `doc.save(...)` như trong các đoạn mã trên. Tệp `.docx` kết quả sẽ chứa các biểu đồ hoạt động đầy đủ, có thể mở và chỉnh sửa trong Microsoft Word.

## Các trường hợp sử dụng phổ biến
- **Bảng điều khiển tài chính** – biểu đồ đường với nhiều dãy cho doanh thu, chi phí và lợi nhuận.  
- **Báo cáo bán hàng** – biểu đồ cột so sánh doanh số quý theo khu vực.  
- **Theo dõi dự án** – biểu đồ khu vực hoặc phân tán hiển thị tiến độ theo thời gian.  

## Tùy chỉnh biểu đồ bổ sung
Ngoài những điều cơ bản, bạn có thể điều chỉnh giới hạn, ẩn trục (`axis.setHidden(true)`), thay đổi màu sắc, thêm chú giải, và nhiều hơn nữa. Tham khảo tài liệu API Aspose.Words for Java để biết danh sách đầy đủ các tùy chọn.

## Kết luận
Trong hướng dẫn này chúng tôi đã trình bày cách **thêm nhiều dãy dữ liệu** vào biểu đồ, tạo cả biểu đồ đường và biểu đồ cột, **thay đổi dấu tick của trục**, **áp dụng định dạng số tùy chỉnh**, và cuối cùng **tạo tài liệu Word giàu biểu đồ**. Với Aspose.Words for Java, bạn có một cách mạnh mẽ, lập trình‑đầu tiên để nhúng các hình ảnh dữ liệu chuyên nghiệp trực tiếp vào tài liệu của mình.

## Câu hỏi thường gặp

**H: Làm thế nào để tôi thêm nhiều dãy dữ liệu vào một biểu đồ?**  
Đ: Gọi `chart.getSeries().add()` cho mỗi dãy mà bạn muốn hiển thị. Mỗi lần gọi sẽ tạo một bộ dữ liệu mới xuất hiện dưới dạng một đường, cột hoặc nhóm dấu chấm riêng.

**H: Làm sao tôi định dạng nhãn dữ liệu bằng định dạng số tùy chỉnh?**  
Đ: Truy cập đối tượng `DataLabels` của dãy và sử dụng `getNumberFormat().setFormatCode("mẫu của bạn")`. Bạn cũng có thể liên kết định dạng với ô nguồn bằng `isLinkedToSource(true)`.

**H: Làm thế nào để thay đổi dấu tick của trục?**  
Đ: Sử dụng `setMajorTickMark()` và `setMinorTickMark()` trên `ChartAxis`. Các tùy chọn bao gồm `CROSS`, `INSIDE`, `OUTSIDE`, và `NONE`.

**H: Tôi có thể tạo các loại biểu đồ khác như biểu đồ phân tán hoặc khu vực không?**  
Đ: Có – chỉ định `ChartType` mong muốn (ví dụ `ChartType.SCATTER`, `ChartType.AREA`) khi gọi `builder.insertChart(...)`.

**H: Làm sao để ẩn một trục mà tôi không cần?**  
Đ: Gọi `axis.setHidden(true)` trên `ChartAxis` mà bạn muốn ẩn.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}