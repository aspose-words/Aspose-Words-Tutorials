---
"description": "Tìm hiểu cách tạo và tùy chỉnh biểu đồ trong Aspose.Words cho Java. Khám phá các loại biểu đồ, định dạng và thuộc tính trục để trực quan hóa dữ liệu."
"linktitle": "Sử dụng biểu đồ"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng Biểu đồ trong Aspose.Words cho Java"
"url": "/vi/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Biểu đồ trong Aspose.Words cho Java


## Giới thiệu về cách sử dụng biểu đồ trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách làm việc với biểu đồ bằng Aspose.Words for Java. Bạn sẽ học cách tạo nhiều loại biểu đồ khác nhau, tùy chỉnh thuộc tính trục, định dạng nhãn dữ liệu, v.v. Hãy cùng tìm hiểu!

## Tạo biểu đồ đường

Để tạo biểu đồ đường, hãy sử dụng mã sau:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Xóa chuỗi mặc định được tạo.
chart.getSeries().clear();

// Thêm một chuỗi dữ liệu và nhãn dữ liệu.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Hoặc liên kết mã định dạng với ô nguồn.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Tạo các loại biểu đồ khác

Bạn có thể tạo nhiều loại biểu đồ khác nhau như biểu đồ cột, biểu đồ diện tích, biểu đồ bong bóng, biểu đồ phân tán, v.v. bằng các kỹ thuật tương tự. Sau đây là ví dụ về cách chèn biểu đồ cột đơn giản:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Xóa chuỗi mặc định được tạo.
chart.getSeries().clear();

// Tạo danh mục và thêm dữ liệu.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Tùy chỉnh Thuộc tính Trục

Bạn có thể tùy chỉnh các thuộc tính trục, chẳng hạn như thay đổi loại trục, đặt dấu tích, định dạng nhãn, v.v. Sau đây là ví dụ về việc xác định các thuộc tính trục XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Xóa chuỗi mặc định và thêm dữ liệu của bạn.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Thay đổi trục X thành danh mục thay vì ngày tháng.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Được đo theo đơn vị hiển thị của trục Y (hàng trăm).
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

## Định dạng nhãn dữ liệu

Bạn có thể định dạng nhãn dữ liệu với các định dạng số khác nhau. Sau đây là một ví dụ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Xóa chuỗi mặc định và thêm dữ liệu của bạn.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Tùy chỉnh biểu đồ bổ sung

Bạn có thể tùy chỉnh thêm biểu đồ của mình bằng cách điều chỉnh ranh giới, đơn vị khoảng cách giữa các nhãn, ẩn trục biểu đồ, v.v. Khám phá các đoạn mã được cung cấp để tìm hiểu thêm về các tùy chọn này.

## Phần kết luận

Trong hướng dẫn này, chúng ta đã khám phá cách làm việc với biểu đồ bằng Aspose.Words for Java. Bạn đã học cách tạo nhiều loại biểu đồ, tùy chỉnh thuộc tính trục, định dạng nhãn dữ liệu, v.v. Aspose.Words for Java cung cấp các công cụ mạnh mẽ để thêm biểu diễn trực quan của dữ liệu vào tài liệu của bạn, nâng cao cách bạn trình bày thông tin.

## Câu hỏi thường gặp

### Làm thế nào để tôi có thể thêm nhiều chuỗi vào biểu đồ?

Bạn có thể thêm nhiều chuỗi vào biểu đồ bằng cách sử dụng `chart.getSeries().add()` phương pháp. Đảm bảo chỉ định tên sê-ri, danh mục và giá trị dữ liệu.

### Làm thế nào để định dạng nhãn dữ liệu theo định dạng số tùy chỉnh?

Bạn có thể định dạng nhãn dữ liệu bằng cách truy cập `DataLabels` thuộc tính của một chuỗi và thiết lập mã định dạng mong muốn bằng cách sử dụng `getNumberFormat().setFormatCode()`.

### Làm thế nào để tùy chỉnh thuộc tính trục trong biểu đồ?

Bạn có thể tùy chỉnh các thuộc tính trục như loại, dấu tích, nhãn và nhiều hơn nữa bằng cách truy cập `ChartAxis` các thuộc tính như `setCategoryType()`, `setCrosses()`, Và `setMajorTickMark()`.

### Làm thế nào tôi có thể tạo các loại biểu đồ khác như biểu đồ phân tán hoặc biểu đồ diện tích?

Bạn có thể tạo nhiều loại biểu đồ khác nhau bằng cách chỉ định các loại biểu đồ thích hợp. `ChartType` khi chèn biểu đồ bằng cách sử dụng `builder.insertChart(ChartType.TYPE, width, height)`.

### Làm thế nào để ẩn trục biểu đồ?

Bạn có thể ẩn trục biểu đồ bằng cách thiết lập `setHidden(true)` tính chất của trục.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}