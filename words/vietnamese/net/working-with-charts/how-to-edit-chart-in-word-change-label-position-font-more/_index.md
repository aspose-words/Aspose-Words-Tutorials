---
category: general
date: 2026-07-29
description: Cách chỉnh sửa biểu đồ trong tài liệu Word—tìm hiểu cách thay đổi vị
  trí nhãn biểu đồ, điều chỉnh nhãn biểu đồ cột, sửa đổi nhãn dữ liệu biểu đồ và thay
  đổi phông chữ nhãn biểu đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: vi
lastmod: 2026-07-29
og_description: Cách chỉnh sửa biểu đồ trong Word nhanh chóng. Nắm vững việc thay
  đổi vị trí nhãn biểu đồ, điều chỉnh nhãn biểu đồ cột, sửa đổi nhãn dữ liệu biểu
  đồ và thay đổi phông chữ nhãn biểu đồ.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Cách chỉnh sửa biểu đồ trong Word – Thay đổi nhãn và phông chữ
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Cách chỉnh sửa biểu đồ trong Word: Thay đổi vị trí nhãn, phông chữ và hơn
  nữa'
url: /vi/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chỉnh sửa biểu đồ trong Word: Thay đổi vị trí nhãn, phông chữ và hơn nữa

Việc chỉnh sửa biểu đồ trong tài liệu Word là nhu cầu phổ biến khi bạn muốn báo cáo của mình trông chuyên nghiệp. Bạn đã bao giờ gặp khó khăn khi **thay đổi vị trí nhãn biểu đồ** hoặc làm cho các nhãn dễ đọc mà không phải lục lọi qua vô số menu chưa? Bạn không đơn độc — hầu hết các nhà phát triển đều gặp phải vấn đề này khi tự động tạo báo cáo. Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được, cho bạn thấy chính xác cách **điều chỉnh nhãn biểu đồ cột**, **sửa đổi nhãn dữ liệu biểu đồ**, và **thay đổi phông chữ nhãn biểu đồ** bằng C# và thư viện Aspose.Words.

## Những gì bạn sẽ học

- Tải một tệp .docx đã chứa biểu đồ cột.  
- Lấy shape biểu đồ đầu tiên và truy cập bộ sưu tập nhãn dữ liệu của nó.  
- **Thay đổi vị trí nhãn biểu đồ** để các cột trông gọn gàng hơn.  
- **Điều chỉnh kích thước phông chữ của nhãn biểu đồ cột** để dễ đọc hơn.  
- Lưu tài liệu đã chỉnh sửa trở lại đĩa.  

Không cần công cụ bên ngoài, không cần các bước giao diện người dùng thủ công — chỉ cần mã thuần túy mà bạn có thể chèn vào bất kỳ dự án .NET nào. Khi kết thúc, bạn sẽ có một giải pháp tự chứa có thể tái sử dụng cho hàng chục tài liệu.

> **Yêu cầu trước**  
> - .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Framework 4.7+).  
> - Aspose.Words cho .NET (có sẵn qua NuGet).  
> - Một tệp Word (`BarChart.docx`) đã chứa biểu đồ cột.  

Nếu bạn thiếu bất kỳ mục nào trong số này, hãy tải gói Aspose.Words mới nhất ngay bây giờ:

```bash
dotnet add package Aspose.Words
```

---

## Cách chỉnh sửa biểu đồ: Lấy biểu đồ từ tài liệu Word

Bước đầu tiên trong việc **cách chỉnh sửa biểu đồ** là tải tài liệu và xác định shape biểu đồ. Aspose.Words coi biểu đồ là các nút `Shape`, vì vậy chúng ta có thể sử dụng `GetChild` với `NodeType.Shape` để lấy biểu đồ đầu tiên mà chúng ta gặp.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Tại sao điều này quan trọng:**  
> Bằng cách truy cập trực tiếp vào đối tượng `Chart`, bạn tránh được chi phí mở tệp trong Word và điều chỉnh từng nhãn một cách thủ công. Đây là nền tảng của bất kỳ tự động hoá **sửa đổi nhãn dữ liệu biểu đồ** nào.

## Điều chỉnh nhãn biểu đồ cột: Thay đổi vị trí nhãn biểu đồ

Bây giờ chúng ta đã có thể hiện `Chart`, hãy lặp qua `DataLabelCollection` của nó. Mục tiêu là **thay đổi vị trí nhãn biểu đồ** sao cho mỗi nhãn nằm gọn trong đáy của cột, thay vì nổi lơ lửng trên nó.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Mẹo chuyên nghiệp:**  
> `InsideBase` hoạt động tốt cho biểu đồ cột dọc. Nếu bạn đang làm việc với biểu đồ cột ngang, hãy thử `InsideEnd` thay thế. Thử nghiệm các vị trí rất đơn giản — chỉ cần chạy lại mã và mở tài liệu đã lưu.

## Thay đổi phông chữ nhãn biểu đồ: Điều chỉnh kích thước phông chữ để dễ đọc

Phông chữ quá nhỏ là kẻ giết chết sự rõ ràng của báo cáo một cách âm thầm. Để **thay đổi phông chữ nhãn biểu đồ**, chỉ cần đặt thuộc tính `Font.Size` trên mỗi `ChartDataLabel`. Chúng ta sẽ tăng lên 9 pt, đây là mức phù hợp cho hầu hết các báo cáo in.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Tại sao chúng ta làm điều này:**  
> Điều chỉnh kích thước phông chữ là một phần của các thực hành tốt **sửa đổi nhãn dữ liệu biểu đồ**. Phông chữ lớn hơn cải thiện khả năng truy cập và giảm nhu cầu xử lý thủ công sau khi tạo.

## Lưu tài liệu đã cập nhật

Sau khi điều chỉnh vị trí và phông chữ, bước cuối cùng trong **cách chỉnh sửa biểu đồ** là lưu các thay đổi. Aspose.Words làm cho việc này chỉ cần một dòng lệnh.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Mở `BarChartCustomLabels.docx` trong Word và bạn sẽ thấy các nhãn gọn gàng bên trong các cột, hiển thị với phông chữ 9 pt rõ ràng. Không còn phải nhìn chằm chằm vào các con số nhỏ nữa.

## Ví dụ hoàn chỉnh (Tất cả các bước trong một tệp)

Dưới đây là một chương trình console đầy đủ, sẵn sàng chạy, minh họa toàn bộ quy trình — từ tải tài liệu đến lưu phiên bản đã cập nhật. Sao chép và dán nó vào một dự án console .NET mới và nhấn **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Kết quả mong đợi** khi bạn chạy chương trình:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Mở tệp kết quả và bạn sẽ thấy **điều chỉnh nhãn biểu đồ cột** được đặt bên trong các cột với kích thước phông chữ thoải mái.

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

### Nếu tài liệu chứa nhiều biểu đồ thì sao?

Mã trên lấy biểu đồ *đầu tiên* (`GetChild(NodeType.Shape, 0, true)`). Để chỉnh sửa tất cả các biểu đồ, thay thế việc lấy duy nhất bằng một vòng lặp:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Cách **thay đổi phông chữ nhãn biểu đồ** cho một series cụ thể chỉ?

Mỗi `ChartSeries` có `DataLabelCollection` riêng. Nhắm mục tiêu một series bằng chỉ số:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Điều này có hoạt động với biểu đồ tròn hoặc đường không?

Có — `ChartDataLabelPosition` hỗ trợ các giá trị như `InsideEnd`, `OutsideEnd`, và `BestFit`. Đối với biểu đồ tròn, bạn có thể muốn dùng `OutsideEnd` để giữ cho nhãn dễ đọc.

### Còn về bản địa hoá (ví dụ: dấu phân cách thập phân khác nhau) thì sao?

Aspose.Words tôn trọng cài đặt ngôn ngữ của tài liệu. Nếu bạn cần ép buộc một định dạng cụ thể, hãy điều chỉnh `label.NumberFormat` trước khi lưu.

## Tóm tắt & Các bước tiếp theo

Chúng tôi đã bao quát việc **cách chỉnh sửa biểu đồ** trong tài liệu Word từ đầu đến cuối: tải tệp, lấy biểu đồ, **thay đổi vị trí nhãn biểu đồ**, **điều chỉnh nhãn biểu đồ cột**, **sửa đổi nhãn dữ liệu biểu đồ**, và cuối cùng **thay đổi phông chữ nhãn biểu đồ** trước khi lưu. Ví dụ đầy đủ đã sẵn sàng cho môi trường sản xuất và có thể chèn vào bất kỳ quy trình tự động nào.

Sẵn sàng nâng cấp? Hãy xem xét các ý tưởng tiếp theo này:

- **Thêm màu cho nhãn dữ liệu** (`dataLabel.Font.Color = Color.Blue;`).  
- **Hiển thị giá trị dưới dạng phần trăm** (`dataLabel.NumberFormat = "0%";`).  
- **Tạo biểu đồ bằng chương trình** thay vì tải các biểu đồ hiện có.  

Tất cả những điều này dựa trên cùng một API mà chúng ta đã sử dụng hôm nay, vì vậy bạn sẽ cảm thấy quen thuộc.

Nếu bạn gặp bất kỳ khó khăn nào, hãy để lại bình luận bên dưới hoặc kiểm tra tài liệu Aspose.Words để biết các tùy chọn tùy chỉnh biểu đồ sâu hơn. Chúc lập trình vui vẻ, và tận hưởng những biểu đồ được gắn nhãn đẹp mắt!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}