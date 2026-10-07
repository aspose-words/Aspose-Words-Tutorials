---
category: general
date: 2026-10-07
description: Học cách tạo biểu đồ tròn trong Word, thêm chuỗi dữ liệu và lưu biểu
  đồ dưới dạng PNG bằng Java. Thực hiện theo hướng dẫn từng bước để có kết quả nhanh
  chóng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: vi
lastmod: 2026-10-07
og_description: 'Tạo biểu đồ tròn trong Word nhanh chóng: hướng dẫn này chỉ cách thêm
  chuỗi dữ liệu, tạo biểu đồ và lưu biểu đồ Word dưới dạng hình ảnh (PNG). Tham khảo
  ví dụ mã đầy đủ.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Tạo biểu đồ tròn trong Word và xuất dưới dạng PNG – hướng dẫn
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Cách tạo biểu đồ tròn trong Word và lưu dưới dạng PNG
url: /vi/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ tròn trong Word và lưu dưới dạng PNG

Nếu bạn cần **tạo biểu đồ tròn** trong một tệp Microsoft Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Java. Bạn cũng sẽ học cách **thêm chuỗi dữ liệu** vào biểu đồ và **lưu biểu đồ dưới dạng PNG** để hình ảnh có thể được sử dụng lại bên ngoài Word.

Việc tạo biểu đồ trực tiếp trong tài liệu giúp bạn tránh việc xuất dữ liệu sang công cụ đồ họa riêng. Khi kết thúc hướng dẫn này, bạn sẽ có một tệp Word hoạt động đầy đủ chứa biểu đồ tròn và một hình PNG tương ứng trên đĩa.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java 17 hoặc mới hơn đã được cài đặt.
* Thư viện **GroupDocs.Viewer for Java** (hoặc một thư viện tương thích cung cấp các lớp `Document`, `Chart`, `ChartType`, và `ImageSaveOptions`).
* Một dự án Maven hoặc Gradle nơi bạn có thể thêm phụ thuộc thư viện.
* Một tài liệu Word đầu vào (`input.docx`) nằm trong thư mục bạn có thể tham chiếu từ mã.

Nếu bạn đang sử dụng Maven, thêm phụ thuộc (thay `VERSION` bằng phiên bản mới nhất):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Cách tạo biểu đồ tròn trong Word

Cốt lõi của giải pháp xoay quanh ba hành động:

1. Tải tệp `.docx` nguồn.
2. **Thêm chuỗi dữ liệu** vào một đối tượng `Chart` mới loại `PIE`.
3. **Lưu biểu đồ dưới dạng PNG** để bạn có được tệp hình ảnh bên cạnh tài liệu Word.

Mỗi bước sẽ được giải thích chi tiết bên dưới, kèm theo mã Java chính xác mà bạn cần.

### Bước 1: Tải tài liệu nguồn

Bạn phải mở tệp Word sẽ chứa biểu đồ. Lớp `Document` đọc nội dung `.docx` vào bộ nhớ.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters*: *Tại sao điều này quan trọng*: Việc tải tài liệu tạo ra một mô hình có thể thay đổi. Tất cả các thao tác biểu đồ tiếp theo sẽ sửa đổi đại diện trong bộ nhớ này, mà bạn sẽ lưu lại lên đĩa sau.

### Bước 2: Thêm chuỗi dữ liệu vào biểu đồ

Việc tạo **biểu đồ tròn** bắt đầu bằng một thể hiện `Chart`. Hàm khởi tạo nhận đối tượng `Document` cha và loại biểu đồ (`ChartType.PIE`). Khi đối tượng biểu đồ đã tồn tại, bạn sẽ điền vào các giá trị số và nhãn tùy chọn.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Why this matters*: *Tại sao điều này quan trọng*: Phương thức `add` **thêm chuỗi dữ liệu** vào biểu đồ. Mỗi mục trong `values` trở thành một phần của biểu đồ tròn, trong khi `categories` cung cấp nhãn chú giải. Bạn có thể cung cấp bất kỳ số lượng điểm nào; thư viện sẽ tự động tính toán góc của các phần.

### Bước 3: Lưu biểu đồ dưới dạng PNG

Khi biểu đồ đã là một phần của tài liệu, bạn có thể xuất biểu diễn hình ảnh. Phương thức `save` trên đối tượng biểu đồ cơ bản sẽ ghi tệp PNG vào hệ thống tệp.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Why this matters*: *Tại sao điều này quan trọng*: Lưu biểu đồ dưới dạng PNG cung cấp cho bạn một hình ảnh raster có thể nhúng vào trang web, email hoặc báo cáo mà không cần tệp Word gốc. Đối tượng `ImageSaveOptions` cho phép bạn kiểm soát định dạng, độ phân giải và các thiết lập xuất khác.

## Tạo biểu đồ tròn trong Word – tùy chỉnh giao diện

Ngoài các bước cơ bản, bạn có thể muốn tùy chỉnh màu sắc, tiêu đề hoặc nhãn dữ liệu. Hầu hết các thư viện cung cấp một đối tượng `ChartOptions` hoặc tương tự. Dưới đây là một ví dụ nhanh thêm tiêu đề và thay đổi màu các phần:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Các tùy chỉnh này là tùy chọn nhưng minh họa cách bạn có thể **tạo biểu đồ tròn trong Word** phù hợp với thương hiệu của mình.

## Lưu biểu đồ Word dưới dạng hình ảnh – các cách tiếp cận thay thế

Nếu bạn chỉ cần hình ảnh mà không cần biểu đồ trong tài liệu, bạn có thể bỏ qua việc chèn hình dạng biểu đồ vào tệp Word và gọi trực tiếp phương thức `save` sau khi tạo biểu đồ. Mã vẫn giữ nguyên; bạn chỉ cần bỏ qua các bước thêm biểu đồ vào phần thân của tài liệu.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Kỹ thuật này hữu ích khi bạn tạo nhiều biểu đồ trong một quy trình batch và chỉ quan tâm đến đầu ra PNG.

## Ví dụ đầy đủ có thể chạy

Sao chép lớp sau vào dự án của bạn, điều chỉnh đường dẫn tệp và chạy nó. Chương trình sẽ:

1. Tải `input.docx`.
2. **Tạo biểu đồ tròn**, **thêm chuỗi dữ liệu**, và nhúng nó vào tài liệu.
3. **Lưu biểu đồ dưới dạng PNG** (`radial.png`).
4. Lưu tệp Word đã chỉnh sửa thành `output.docx`.



## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo biểu đồ cột bằng Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Tạo biểu đồ Scatter trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Chèn biểu đồ cột trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}