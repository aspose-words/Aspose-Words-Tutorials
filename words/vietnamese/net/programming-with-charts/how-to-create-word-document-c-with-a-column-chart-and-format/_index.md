---
category: general
date: 2026-09-21
description: Học cách tạo tài liệu Word bằng C# và chèn biểu đồ cột, đặt vị trí nhãn,
  và hiển thị giá trị bằng Aspose.Words trong hướng dẫn từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: vi
lastmod: 2026-09-21
og_description: Tạo tài liệu Word C# với Aspose.Words. Hướng dẫn này cho thấy cách
  chèn biểu đồ cột, đặt vị trí nhãn và hiển thị giá trị.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Tạo tài liệu Word bằng C# – chèn biểu đồ cột, đặt nhãn, hiển thị giá trị
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Cách tạo tài liệu Word bằng C# với biểu đồ cột và nhãn được định dạng
url: /vi/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word bằng C# với biểu đồ cột và nhãn đã định dạng

Nếu bạn cần **tạo tài liệu Word C#** có chứa biểu đồ, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ học cách chèn biểu đồ cột, đặt vị trí nhãn dữ liệu và hiển thị giá trị của nhãn—tất cả đều với Aspose.Words cho .NET.

Trước đây, việc tạo tệp Word có biểu đồ đòi hỏi phải thực hiện thủ công trong Microsoft Word. Với các bước **cách chèn biểu đồ** được mô tả ở đây, bạn có thể tự động hoá toàn bộ quá trình bằng mã, giúp việc tạo báo cáo nhanh chóng và có thể lặp lại. Bài học cũng bao gồm **cách đặt nhãn** và **cách hiển thị giá trị** để biểu đồ sẵn sàng cho người dùng cuối.

Khi đọc xong bài viết này, bạn sẽ có một chương trình C# hoàn chỉnh, có thể chạy được, tạo ra tệp `.docx` chứa biểu đồ cột với nhãn dữ liệu nằm bên trong mỗi cột và hiển thị giá trị số.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 SDK hoặc phiên bản mới hơn được cài đặt  
* Bản quyền **Aspose.Words cho .NET** (bản dùng thử miễn phí cũng đủ để thử nghiệm)  
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Bước 1: Thiết lập dự án và thêm Aspose.Words

Tạo một dự án console mới và thêm gói Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Lệnh `dotnet add package` sẽ tải về phiên bản ổn định mới nhất của **Aspose.Words**, bao gồm API biểu đồ được sử dụng trong ví dụ **chèn biểu đồ cột word**.

## Bước 2: Tạo một tài liệu Word trống mới

Đoạn mã đầu tiên tạo một tài liệu rỗng và một `DocumentBuilder` cho phép bạn chèn nội dung. Đây là nền tảng cho **tạo tài liệu word C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho toàn bộ tệp `.docx`, trong khi `DocumentBuilder` cung cấp các phương thức như `InsertParagraph`, `InsertImage` và, quan trọng nhất cho hướng dẫn này, `InsertChart`.

## Bước 3: Chèn một biểu đồ cột (cách chèn biểu đồ)

Bây giờ chúng ta chèn một **biểu đồ cột**. Phương thức `InsertChart` nhận loại biểu đồ, chiều rộng và chiều cao tính bằng điểm.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

Lúc này biểu đồ chứa một chuỗi dữ liệu mặc định với các giá trị placeholder. Bạn có thể thay thế dữ liệu chuỗi nếu cần số liệu tùy chỉnh, nhưng để minh hoạ **cách đặt nhãn** và **cách hiển thị giá trị**, dữ liệu mặc định đã đủ.

## Bước 4: Đặt nhãn dữ liệu bên trong mỗi cột (cách đặt nhãn)

Nhãn dữ liệu là văn bản xuất hiện trên mỗi cột. Để biểu đồ dễ đọc hơn, chúng ta di chuyển nhãn vào bên trong cột và bật hiển thị giá trị số.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` đặt nhãn ở đầu trên của cột nhưng vẫn nằm trong hình dạng của cột, đây là kiểu hiển thị phổ biến cho báo cáo. Đặt `ShowValue` thành `true` đáp ứng yêu cầu **cách hiển thị giá trị**.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Tệp có thể được mở bằng Microsoft Word, LibreOffice hoặc bất kỳ trình xem nào hỗ trợ định dạng Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Chạy chương trình sẽ tạo ra `output.docx` chứa một biểu đồ cột với nhãn dữ liệu được đặt bên trong mỗi cột và hiển thị giá trị của chúng.

### Kết quả mong đợi

Khi bạn mở `output.docx`, sẽ thấy một biểu đồ cột duy nhất giống như hình dưới đây. Mỗi cột có một nhãn số ở phía trên, bên trong cột, hiển thị giá trị của chuỗi.

![Biểu đồ trong tài liệu Word được tạo bằng C#](/images/word-chart-example.png "Biểu đồ trong tài liệu Word được tạo bằng C# – tạo tài liệu word C#")

*Alt text:* *Biểu đồ trong tài liệu Word được tạo bằng C# thể hiện cách chèn biểu đồ cột word và hiển thị giá trị.*

## Các biến thể phổ biến và trường hợp đặc biệt

### Thêm dữ liệu tùy chỉnh vào biểu đồ

Nếu bạn cần thay thế dữ liệu placeholder, có thể sửa đổi bộ sưu tập `Series` của biểu đồ:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Thay đổi phông chữ và màu sắc của nhãn

Bạn có thể tùy chỉnh thêm giao diện của nhãn:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Chèn nhiều biểu đồ

`DocumentBuilder` có thể chèn bao nhiêu biểu đồ tùy ý. Chỉ cần gọi lại `InsertChart` sau khi di chuyển con trỏ bằng `builder.Writeln()` hoặc `builder.InsertParagraph()`.

## Mẹo chuyên nghiệp

* **Mẹo pro:** Đặt `chart.HasTitle = true` và gán `chart.Title.Text` để thêm tiêu đề mô tả cho biểu đồ. Điều này cải thiện khả năng truy cập cho các trình đọc màn hình.  
* **Cẩn thận:** Khi lưu vào một thư mục chia sẻ trên mạng, đảm bảo ứng dụng có quyền ghi; nếu không `doc.Save` sẽ ném ra `UnauthorizedAccessException`.  
* **Mẹo hiệu năng:** Tái sử dụng một thể hiện `DocumentBuilder` duy nhất cho nhiều lần chèn; tạo một builder mới cho mỗi thao tác sẽ gây tốn tài nguyên không cần thiết.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word C#** chứa biểu đồ cột, cách **chèn biểu đồ**, **đặt vị trí nhãn** và **hiển thị giá trị** bên trong mỗi cột. Mã mẫu đầy đủ ở trên đã sẵn sàng để chạy, và bạn có thể mở rộng nó với dữ liệu tùy chỉnh, kiểu dáng hoặc thêm các biểu đồ khác.

Tiếp theo, hãy khám phá các chủ đề liên quan như **cách chèn hình ảnh**, **cách tạo bảng**, hoặc **cách áp dụng chủ đề tài liệu** để làm cho báo cáo tự động của bạn phong phú hơn. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước, giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn Biểu Đồ Cột trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Chèn Biểu Đồ Cột Đơn Giản trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Chèn Biểu Đồ Khu Vực trong Tài Liệu Word | Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}