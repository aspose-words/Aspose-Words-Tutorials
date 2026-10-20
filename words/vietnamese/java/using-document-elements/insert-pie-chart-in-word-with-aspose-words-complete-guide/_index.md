---
category: general
date: 2026-07-26
description: Chèn biểu đồ tròn vào tài liệu Word bằng Aspose.Words. Tìm hiểu cách
  thêm biểu đồ, tách miếng và hiển thị phần trăm chỉ trong vài bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: vi
lastmod: 2026-07-26
og_description: Chèn biểu đồ tròn vào tệp Word bằng Aspose.Words. Hãy làm theo hướng
  dẫn này để biết cách thêm biểu đồ, tách miếng và hiển thị phần trăm nhanh chóng.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Chèn biểu đồ tròn trong Word – Hướng dẫn chi tiết Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Chèn biểu đồ tròn trong Word bằng Aspose.Words – Hướng dẫn đầy đủ
url: /vi/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Biểu Đồ Tròn vào Word với Aspose.Words – Hướng Dẫn Toàn Diện

Bạn đã bao giờ cần **chèn biểu đồ tròn** vào một báo cáo Word nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất. Trong nhiều ứng dụng kinh doanh, sức mạnh trực quan của biểu đồ tròn giúp dữ liệu trở nên dễ hiểu ngay lập tức, và Aspose.Words cho phép điều đó chỉ với vài dòng mã.

Trong tutorial này, chúng ta sẽ đi qua các bước chính xác để **thêm biểu đồ vào Word**, làm nổ một lát cắt để nhấn mạnh, và hiển thị phần trăm trên nhãn dữ liệu. Khi kết thúc, bạn sẽ có một ví dụ sẵn sàng chạy mà bạn có thể đưa vào bất kỳ dự án .NET nào.

---

## Các Yêu Cầu Trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- .NET 6.0 hoặc mới hơn (mã hoạt động với .NET Core và .NET Framework đều được)
- Gói NuGet Aspose.Words for .NET đã được cài đặt  
  ```bash
  dotnet add package Aspose.Words
  ```
- Kiến thức cơ bản về cú pháp C#—không cần gì phức tạp
- Một IDE mà bạn thích (Visual Studio, Rider, hoặc VS Code)

Đó là tất cả. Hãy bắt tay vào thực hành.

---

## Chèn Biểu Đồ Tròn vào Tài Liệu Word

Điều đầu tiên chúng ta cần là một đối tượng `Document` mới và một `DocumentBuilder`. Hãy nghĩ tới builder như một cây bút viết trực tiếp lên canvas của Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tại sao điều này quan trọng:** `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp một API tiện lợi để chèn các yếu tố như biểu đồ, bảng và văn bản. Đây là nền tảng cho mọi thao tác **cách thêm biểu đồ**.

---

## Cách Thêm Biểu Đồ vào Word

Bây giờ chúng ta đã có builder, chúng ta có thể thực sự **chèn biểu đồ tròn**. Phương thức `insertChart` nhận loại biểu đồ và kích thước mong muốn tính bằng điểm (1 point = 1/72 inch).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Mẹo:** Nếu bạn cần kích thước khác, chỉ cần điều chỉnh giá trị chiều rộng và chiều cao. Biểu đồ sẽ tự động thu phóng để phù hợp với lề trang.

---

## Cách Nổ Lát Cắt Để Nhấn Mạnh

Một thủ thuật trực quan phổ biến là “nổ” một lát cắt để nó bật ra khỏi vòng tròn. Điều này thu hút mắt người đọc tới phần quan trọng nhất.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Tại sao nổ một lát cắt?** Khi bạn muốn làm nổi bật một danh mục cụ thể—ví dụ, “Doanh thu Q1” trong báo cáo tài chính—việc nổ lát cắt khiến nó ngay lập tức được chú ý mà không cần thêm văn bản.

---

## Cách Hiển Thị Phần Trăm Trên Nhãn Dữ Liệu

Hầu hết các biểu đồ tròn trông đẹp hơn khi mỗi lát cắt hiển thị phần trăm của nó. Aspose.Words cho phép chúng ta bật tính năng này chỉ bằng một thuộc tính duy nhất.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Lưu ý nhanh:** Cờ `ShowPercentage` hoạt động cho tất cả các điểm trong series, vì vậy bạn không cần đặt riêng cho từng lát cắt.

---

## Lưu Tài Liệu Chứa Biểu Đồ

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Chọn bất kỳ thư mục nào bạn muốn; chỉ cần chắc chắn rằng đường dẫn tồn tại.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Khi bạn mở `PieChart.docx` trong Microsoft Word, bạn sẽ thấy một biểu đồ tròn được render hoàn hảo với lát cắt đầu tiên đã nổ và phần trăm được hiển thị—đúng như mong đợi từ một báo cáo kinh doanh được chăm chút.

---

## Ví Dụ Hoàn Chỉnh

Dưới đây là chương trình đầy đủ, sẵn sàng sao chép‑dán. Chạy nó như một ứng dụng console và kiểm tra tệp đầu ra.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi:** Mở `PieChart.docx` đã tạo. Bạn sẽ thấy một biểu đồ tròn ba lát cắt có tiêu đề “Sales Q1”, với lát cắt đầu tiên được kéo ra và mỗi lát cắt được gắn nhãn “30 %”, “45 %”, và “25 %”. Hình ảnh trực quan khớp với dữ liệu chúng ta đã cung cấp.

---

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

- **Nếu tôi cần hơn một series thì sao?**  
  Chỉ cần thêm các đối tượng `ChartSeries` vào `chart.Series`. Mỗi series có thể có bộ dữ liệu, màu sắc và cài đặt nổ riêng.

- **Tôi có thể thay đổi màu sắc của biểu đồ không?**  
  Có. Mỗi `ChartPoint` có thuộc tính `Format.Fill.ForeColor` mà bạn có thể đặt thành bất kỳ `System.Drawing.Color` nào.

- **Còn các loại biểu đồ khác thì sao?**  
  Enum `ChartType` bao gồm bar, line, doughnut và nhiều loại khác. Thay `ChartType.Pie` bằng loại bạn cần.

- **Biểu đồ có thể chỉnh sửa trong Word sau khi chèn không?**  
  Hoàn toàn có thể. Word xem biểu đồ như một biểu đồ Office gốc, vì vậy người dùng có thể nhấp đúp để mở trình chỉnh sửa biểu đồ tích hợp.

---

## Kết Luận

Bây giờ bạn đã biết chính xác cách **chèn biểu đồ tròn** vào tài liệu Word bằng Aspose.Words, **cách thêm biểu đồ vào Word**, **cách nổ lát cắt**, và **cách hiển thị phần trăm** trên nhãn dữ liệu. Ví dụ đầy đủ ở trên đã sẵn sàng chạy, và bạn có thể mở rộng nó với dữ liệu tùy chỉnh, kiểu dáng, hoặc các series bổ sung.

Sẵn sàng cho bước tiếp theo? Hãy thử thay đổi biểu đồ tròn thành biểu đồ vòng donut, hoặc tạo hàng loạt báo cáo với các bộ dữ liệu khác nhau một cách tự động. Nếu bạn tò mò về các biểu đồ khác, hãy xem các hướng dẫn của chúng tôi về **cách thêm biểu đồ** cho biểu đồ cột và đường, hoặc khám phá tài liệu tham khảo **add chart to word** API để tùy chỉnh sâu hơn.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn rõ ràng như một miếng bánh tròn hoàn hảo!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial dưới đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ cùng các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}