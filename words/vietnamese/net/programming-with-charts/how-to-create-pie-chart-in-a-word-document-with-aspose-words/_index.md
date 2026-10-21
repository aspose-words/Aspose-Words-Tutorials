---
category: general
date: 2026-09-21
description: Học cách tạo biểu đồ tròn và chèn biểu đồ vào Word bằng Aspose.Words,
  thêm nhãn dữ liệu vào biểu đồ tròn và hiển thị phần trăm trên biểu đồ tròn chỉ trong
  vài bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: vi
lastmod: 2026-09-21
og_description: Tạo biểu đồ tròn trong Word bằng Aspose.Words, chèn biểu đồ vào Word,
  thêm nhãn dữ liệu vào biểu đồ tròn và hiển thị phần trăm trên biểu đồ tròn — tất
  cả với các ví dụ mã rõ ràng.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Tạo biểu đồ tròn trong Word bằng Aspose.Words – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Cách tạo biểu đồ tròn trong tài liệu Word bằng Aspose.Words
url: /vi/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo pie chart trong tài liệu Word bằng Aspose.Words

Nếu bạn cần **tạo pie chart** một cách lập trình, Aspose.Words làm cho việc này trở nên đơn giản. Trong hướng dẫn này, bạn sẽ thấy cách **chèn chart vào Word**, cấu hình series, **thêm data labels vào pie chart**, và cuối cùng **hiển thị phần trăm trên pie chart** để hình ảnh truyền đạt giá trị chính xác. Khi kết thúc, bạn sẽ có một ví dụ hoàn chỉnh, có thể chạy được mà bạn có thể đưa vào bất kỳ dự án .NET nào.

Hướng dẫn này bao gồm mọi thứ bạn cần biết: các gói NuGet cần thiết, mã nguồn C# đầy đủ, giải thích lý do mỗi lời gọi API quan trọng, và các mẹo để tùy chỉnh chart. Không cần tài liệu bên ngoài—chỉ cần sao chép, chạy và điều chỉnh.

## Yêu cầu trước

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt.  
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ .NET).  
* Giấy phép Aspose.Words for .NET (bản dùng thử miễn phí hoạt động cho việc thử nghiệm).  
* Kiến thức cơ bản về C# và cấu trúc tài liệu Word.

Nếu bạn đã có những thứ này, bạn có thể chuyển thẳng tới mã.

## Bước 1: Thiết lập dự án và nhập Aspose.Words

Tạo một dự án console mới và thêm gói NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Gói này bao gồm namespace `Aspose.Words.Drawing.Charts`, chứa các lớp `Chart` và `ChartSeries` mà chúng ta sẽ sử dụng.

> **Pro tip:** Giữ file giấy phép (`Aspose.Words.lic`) trong thư mục gốc của dự án và tải nó khi khởi động để tránh watermark đánh giá.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Bước 2: Tạo tài liệu trống và DocumentBuilder

`Document` đại diện cho file Word, trong khi `DocumentBuilder` cung cấp một API fluent để chèn nội dung.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:** `DocumentBuilder` duy trì vị trí chèn hiện tại, đảm bảo chart xuất hiện đúng nơi bạn muốn trong luồng tài liệu.

## Bước 3: Chèn một pie chart vào tài liệu Word

Bây giờ chúng ta **chèn chart vào Word**. Phương thức `InsertChart` nhận loại chart, chiều rộng và chiều cao (đơn vị point).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Ở thời điểm này, chart chứa một series dữ liệu mặc định với các giá trị placeholder (25, 25, 25, 25). Bạn có thể thay thế chúng sau nếu cần.

## Bước 4: Truy cập series đầu tiên và tùy chỉnh data labels

Một pie chart thường có một series duy nhất. Để **thêm data labels vào pie chart**, chúng ta lấy nó và bật hiển thị phần trăm.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Tại sao chúng ta đặt `ShowPercentage`:** Cờ này báo cho Aspose.Words tính toán đóng góp của mỗi phần và hiển thị dưới dạng phần trăm. Thuộc tính `Position` đảm bảo nhãn không chồng lên phần, giúp tăng khả năng đọc—đặc biệt khi các phần nhỏ.

## Bước 5: (Tùy chọn) Thay thế dữ liệu placeholder

Nếu bạn muốn các giá trị cụ thể, hãy thay thế các điểm mặc định:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Các phần trăm hiển thị sẽ tự động điều chỉnh để phản ánh các giá trị mới.

## Bước 6: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Phần mở rộng quyết định định dạng; `.docx` tạo một file Word hiện đại.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Chạy chương trình sẽ tạo một file có tên **PieChart.docx** trong thư mục output. Mở nó trong Microsoft Word sẽ hiển thị một pie chart với mỗi phần được gắn nhãn phần trăm, đặt ngoài các phần.

### Kết quả mong đợi

Khi bạn mở tài liệu đã tạo, bạn sẽ thấy:

* Một pie chart duy nhất, kích thước 400 × 300 pt.  
* Bốn phần (hoặc bao nhiêu điểm bạn đã thêm).  
* Các nhãn phần trăm như “40 %”, “30 %”, v.v., hiển thị ngoài mỗi phần.

Nếu các nhãn xuất hiện bên trong các phần, hãy kiểm tra lại rằng `ChartDataLabelPosition.OutsideEnd` đã được đặt đúng.

## Bước 7: Các biến thể phổ biến và trường hợp đặc biệt

### Thêm tiêu đề cho chart

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Thay đổi màu sắc của các phần

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Xử lý series rỗng

Nếu nguồn dữ liệu của bạn có thể rỗng, hãy bảo vệ khỏi `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Xuất ra PDF thay vì Word

Logic render chart vẫn giống; Aspose.Words tự động chuyển đổi bố cục Word sang PDF.

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

## Danh sách mã nguồn đầy đủ

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy. Sao chép nó vào `Program.cs` và thực thi `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Kết luận

Bây giờ bạn đã biết cách **tạo pie chart** trong file Word bằng Aspose.Words, **chèn chart vào Word**, **thêm data labels vào pie chart**, và **hiển thị phần trăm trên pie chart**. Ví dụ minh họa toàn bộ quy trình—từ thiết lập dự án đến tài liệu cuối cùng—để bạn có thể áp dụng cho dashboard, báo cáo, hoặc tạo hoá đơn tự động.  

Tiếp theo, khám phá các chủ đề liên quan như **cách hiển thị phần trăm trong chú giải chart**, tùy chỉnh màu sắc chart, hoặc chuyển đổi tài liệu Word sang PDF để phân phối. Thử nghiệm các loại chart khác nhau (Bar, Line) bằng cùng một phương thức `InsertChart` để mở rộng khả năng tự động hoá của bạn.

Chúc bạn chart vui!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ, hoạt động với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn Column Chart trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Tạo Word Scatter Chart bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Chèn Area Chart trong tài liệu Word | Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}