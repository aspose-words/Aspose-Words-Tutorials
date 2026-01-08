---
date: 2025-12-13
description: Tìm hiểu cách tạo biểu đồ cột và định dạng nhãn dữ liệu biểu đồ với Aspose.Words
  cho Java. Khám phá việc thêm nhiều chuỗi, thay đổi loại trục và ẩn trục biểu đồ.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Cách tạo biểu đồ cột bằng Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ cột bằng Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ **tạo biểu đồ cột** trực tiếp trong tài liệu Word bằng Aspose.Words cho Java. Chúng ta sẽ đi qua cách tạo các loại biểu đồ khác nhau, thêm nhiều series, định dạng nhãn dữ liệu của biểu đồ, thay đổi loại trục, và thậm chí ẩn một trục biểu đồ khi bạn cần giao diện sạch sẽ hơn. Khi hoàn thành, bạn sẽ có một phương pháp sẵn sàng cho sản xuất để nhúng các biểu đồ phong phú vào tài liệu của mình.

## Câu trả lời nhanh
- **Lớp chính để xây dựng biểu đồ là gì?** `DocumentBuilder` với `insertChart`.
- **Phương thức nào thêm một series mới?** `chart.getSeries().add(...)`.
- **Làm sao để định dạng nhãn dữ liệu của biểu đồ?** Sử dụng `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Có thể ẩn một trục không?** Có, gọi `setHidden(true)` trên đối tượng trục.
- **Có cần giấy phép cho Aspose.Words không?** Giấy phép bắt buộc cho môi trường sản xuất; bản dùng thử miễn phí có sẵn.

## Biểu đồ cột là gì và tại sao nên sử dụng?

Biểu đồ cột hiển thị dữ liệu phân loại dưới dạng các thanh dọc, rất phù hợp để so sánh giá trị giữa các nhóm (doanh số theo khu vực, chi phí hàng tháng, v.v.). Trong các ứng dụng Java, việc tạo biểu đồ cột bằng Aspose.Words cho phép bạn nhúng trực tiếp các hình ảnh này vào các tệp Word / DOCX mà không cần Excel hay công cụ bên ngoài.

## Cách tạo biểu đồ cột

Dưới đây là một ví dụ đơn giản tạo một biểu đồ cột cơ bản. Mã nguồn giống hệt đoạn gốc – chúng tôi chỉ thêm các chú thích giải thích để dễ hiểu hơn.

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

### Thêm nhiều series

Bạn có thể **thêm nhiều series** vào biểu đồ cột bằng cách gọi `chart.getSeries().add(...)` liên tục, như đã minh họa ở trên. Mỗi series có thể có tập hợp danh mục và giá trị riêng, cho phép bạn so sánh nhiều bộ dữ liệu đồng thời.

## Cách tạo biểu đồ đường với nhãn dữ liệu tùy chỉnh

Nếu bạn cần một biểu đồ đường thay vì biểu đồ cột, cùng một mẫu sẽ áp dụng. Ví dụ này cũng minh họa **định dạng nhãn dữ liệu** với các định dạng số khác nhau.

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

### Thêm nhãn dữ liệu

Lệnh `series1.hasDataLabels(true)` **thêm nhãn dữ liệu** vào series, trong khi `setShowValue(true)` hiển thị giá trị thực tế trên biểu đồ.

## Cách thay đổi loại trục và tùy chỉnh thuộc tính trục

Thay đổi loại trục (ví dụ: từ ngày sang danh mục) cho phép bạn kiểm soát cách các điểm dữ liệu được vẽ. Đoạn mã này cũng cho thấy cách **ẩn trục biểu đồ** nếu bạn muốn thiết kế tối giản.

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

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Thay đổi loại trục

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **thay đổi loại trục** từ trục dựa trên ngày sang trục danh mục, giúp bạn kiểm soát hoàn toàn vị trí nhãn.

## Định dạng nhãn dữ liệu của biểu đồ (định dạng số)

Bạn có thể áp dụng định dạng số trực tiếp cho trục hoặc nhãn dữ liệu. Ví dụ này định dạng các số trên trục Y với dấu phân cách hàng nghìn.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Tùy chỉnh biểu đồ bổ sung

Ngoài các chức năng cơ bản, bạn có thể điều chỉnh giới hạn, đặt đơn vị khoảng cách giữa các nhãn, ẩn các trục cụ thể, và nhiều hơn nữa. Tham khảo tài liệu API Aspose.Words cho Java để biết danh sách đầy đủ các thuộc tính.

## Câu hỏi thường gặp

**Q: Làm sao để thêm nhiều series vào một biểu đồ?**  
A: Sử dụng `chart.getSeries().add()` cho mỗi series bạn muốn hiển thị. Mỗi lời gọi có thể cung cấp tên duy nhất, mảng danh mục và mảng giá trị.

**Q: Làm sao để định dạng nhãn dữ liệu của biểu đồ với định dạng số tùy chỉnh?**  
A: Truy cập đối tượng `DataLabels` của một series và gọi `getNumberFormat().setFormatCode("định dạng của bạn")`. Bạn cũng có thể liên kết định dạng với ô nguồn bằng `isLinkedToSource(true)`.

**Q: Làm sao để ẩn một trục biểu đồ?**  
A: Gọi `setHidden(true)` trên `ChartAxis` mà bạn muốn ẩn (ví dụ: `chart.getAxisY().setHidden(true)`).

**Q: Cách tốt nhất để thay đổi loại trục là gì?**  
A: Sử dụng `setCategoryType(AxisCategoryType.CATEGORY)` cho trục danh mục hoặc `AxisCategoryType.DATE` cho trục ngày.

**Q: Làm sao để thêm nhãn dữ liệu vào một series?**  
A: Kích hoạt chúng bằng `series.hasDataLabels(true)` và sau đó cấu hình hiển thị bằng `series.getDataLabels().setShowValue(true)`.

## Kết luận

Chúng tôi đã trình bày mọi thứ bạn cần để **tạo biểu đồ cột** bằng Aspose.Words cho Java — từ việc chèn biểu đồ cơ bản và thêm nhiều series, đến định dạng nhãn dữ liệu, thay đổi loại trục và ẩn trục biểu đồ để có giao diện sạch sẽ. Áp dụng các kỹ thuật này vào quy trình báo cáo hoặc tạo tài liệu của bạn để cung cấp các tài liệu Word chuyên nghiệp, dựa trên dữ liệu.

---

**Cập nhật lần cuối:** 2025-12-13  
**Kiểm tra với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}