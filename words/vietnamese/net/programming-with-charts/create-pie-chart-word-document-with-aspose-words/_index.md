---
category: general
date: 2026-08-10
description: Tạo tài liệu Word có biểu đồ tròn bằng Aspose.Words. Tìm hiểu cách chèn
  biểu đồ, tùy chỉnh màu sắc biểu đồ tròn và thay đổi màu sắc của từng lát bánh trong
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: vi
lastmod: 2026-08-10
og_description: Tạo tài liệu Word có biểu đồ tròn với Aspose.Words. Hướng dẫn này
  giải thích cách chèn biểu đồ, tùy chỉnh màu sắc biểu đồ tròn và thay đổi màu sắc
  của từng lát bánh trong ứng dụng C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Tạo biểu đồ tròn trong tài liệu Word – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Tạo tài liệu Word có biểu đồ tròn bằng Aspose.Words
url: /vi/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word có biểu đồ tròn với Aspose.Words

Nếu bạn cần **tạo tài liệu Word có biểu đồ tròn** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Chúng ta sẽ đi qua việc chèn biểu đồ, **tùy chỉnh màu sắc biểu đồ tròn**, và **thay đổi màu sắc lát cắt** bằng Aspose.Words cho .NET.

Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy ngay, mà bạn có thể sao chép vào Visual Studio, chạy, và ngay lập tức mở file *.docx* đã tạo để kiểm tra biểu đồ tròn đã được định dạng. Không cần tài liệu bên ngoài—mọi thứ bạn cần đều có trong hướng dẫn này.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 SDK hoặc phiên bản mới hơn được cài đặt  
* Giấy phép hợp lệ của Aspose.Words for .NET (hoặc khóa đánh giá tạm thời)  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  

Mã chỉ sử dụng các namespace `Aspose.Words` và `Aspose.Words.Drawing.Charts`, vì vậy không cần thêm bất kỳ gói NuGet nào ngoài thư viện Aspose.Words.

## Tạo tài liệu Word có biểu đồ tròn – ví dụ đầy đủ

Chương trình C# dưới đây tạo một tài liệu Word mới, chèn một biểu đồ tròn, định dạng hai lát cắt đầu tiên, và lưu file. Mỗi bước được giải thích chi tiết.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Giải thích từng bước

| Bước | Mô tả | Lý do |
|------|------|-------|
| **1** | Tạo một `Document` mới và một `DocumentBuilder`. | `DocumentBuilder` cung cấp các phương thức fluent để chèn nội dung, chẳng hạn như biểu đồ, vào file Word. |
| **2** | Gọi `InsertChart` với `ChartType.Pie` và kích thước cố định. | `InsertChart` là **cách chèn biểu đồ**; việc chỉ định chiều rộng/chiều cao giúp biểu đồ vừa vặn trên trang. |
| **3** | Thêm một series dữ liệu với ba danh mục và các giá trị số. | Một biểu đồ tròn không có dữ liệu sẽ không hiển thị; việc đưa dữ liệu vào cho phép chúng ta thực hiện các bước định dạng. |
| **4** | Đặt `Explosion` cho điểm đầu tiên. | “Nổ” một lát cắt sẽ thu hút sự chú ý đến một phân đoạn cụ thể—hữu ích để làm nổi bật dữ liệu quan trọng. |
| **5** | Đặt `ForeColor` cho hai điểm đầu tiên. | Đây là phần cốt lõi của **tùy chỉnh màu sắc biểu đồ tròn**; bạn có thể dùng bất kỳ `System.Drawing.Color` nào. |
| **6** | Cho thấy cách **thay đổi màu sắc lát cắt** cho các lát cắt khác. | Minh họa rằng việc định dạng không chỉ giới hạn ở hai lát cắt đầu tiên; bạn có thể tô màu từng lát cắt một cách riêng biệt. |
| **7** | Lưu tài liệu dưới tên `PieChartStyled.docx`. | Kết quả cuối cùng có thể mở bằng Microsoft Word, Google Docs, hoặc bất kỳ trình xem tương thích nào. |

#### Kết quả mong đợi

Mở `PieChartStyled.docx` sẽ hiển thị một trang duy nhất với biểu đồ tròn kích thước 400 × 300 pt:

* Lát cắt 1 (màu cam) được “nổ” ra phía ngoài.  
* Lát cắt 2 (màu xanh lá) nằm cạnh lát cắt đã nổ.  
* Lát cắt 3 (màu xanh thép) chiếm phần còn lại.

Biểu đồ phản ánh các giá trị dữ liệu (30, 45, 25) và các màu tùy chỉnh mà bạn đã định nghĩa.

## Cách định dạng biểu đồ tròn – các mẹo bổ sung

* **Sử dụng màu chủ đề** – thay vì mã cứng `Color.Orange`, bạn có thể lấy màu từ theme của tài liệu:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Thêm nhãn dữ liệu** – nếu muốn hiển thị phần trăm trên biểu đồ:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Thay đổi kích thước động** – tính kích thước biểu đồ dựa trên lề trang:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Các biến thể này minh họa tính linh hoạt của **cách định dạng biểu đồ tròn** ngoài ví dụ cơ bản.

## Các câu hỏi thường gặp

**H: Điều này có hoạt động với .NET Core không?**  
Đ: Có. Aspose.Words for .NET tương thích với .NET Core, .NET 5, .NET 6 và các phiên bản sau. Chỉ cần tham chiếu cùng một gói NuGet.

**H: Nếu tôi muốn biểu đồ donut thay vì pie thì sao?**  
Đ: Thay `ChartType.Pie` bằng `ChartType.Doughnut`. Các API định dạng (`Explosion`, `ForeColor`) vẫn áp dụng được.

**H: Tôi có thể chèn biểu đồ vào tài liệu hiện có không?**  
Đ: Mở file hiện có bằng `new Document("Existing.docx")`, tạo một `DocumentBuilder` cho tài liệu đó, và gọi `InsertChart` tại vị trí con trỏ mong muốn.

**H: Làm sao xử lý tập dữ liệu lớn?**  
Đ: Biểu đồ tròn thích hợp cho số lượng danh mục hạn chế (thường < 10). Nếu có nhiều danh mục, hãy cân nhắc sử dụng biểu đồ cột hoặc thanh.

## Tổng hợp mã nguồn đầy đủ

Dưới đây là toàn bộ chương trình trong một khối để bạn có thể sao chép‑dán dễ dàng:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Chạy đoạn mã này sẽ tạo ra tài liệu Word có biểu đồ tròn đã được định dạng như đã mô tả ở trên.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word có biểu đồ tròn** bằng Aspose.Words, **tùy chỉnh màu sắc biểu đồ tròn**, và **thay đổi màu sắc lát cắt** một cách lập trình. Hướng dẫn đã bao gồm việc chèn biểu đồ, đưa dữ liệu vào, “nổ” một lát cắt, áp dụng màu tùy chỉnh, và lưu kết quả.  

Từ đây, bạn có thể khám phá các chủ đề liên quan như **cách chèn các loại biểu đồ** khác ngoài pie, thêm legend, hoặc tạo báo cáo đa trang với nhiều biểu đồ. Hãy thử nghiệm các bảng màu và bộ dữ liệu khác nhau để phù hợp với nhu cầu báo cáo của bạn.

Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}