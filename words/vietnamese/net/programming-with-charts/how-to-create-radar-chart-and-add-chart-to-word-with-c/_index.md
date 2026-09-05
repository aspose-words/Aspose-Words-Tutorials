---
category: general
date: 2026-09-05
description: Tạo biểu đồ radar trong Word bằng C#. Học cách tạo tài liệu Word trống,
  chèn biểu đồ radar, thiết lập kích thước biểu đồ và bật các dấu tick một cách nhanh
  chóng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: vi
lastmod: 2026-09-05
og_description: Tạo biểu đồ radar trong Word bằng C#. Hướng dẫn này cho bạn cách tạo
  tài liệu Word trống, thêm biểu đồ radar, thiết lập kích thước biểu đồ và bật các
  dấu tick—tất cả trong vài phút.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Tạo biểu đồ radar trong Word – hướng dẫn C# chi tiết từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Cách tạo biểu đồ radar và chèn biểu đồ vào Word bằng C#
url: /vi/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ radar và chèn biểu đồ vào Word bằng C#

Nếu bạn cần **tạo biểu đồ radar** trong một tệp Word, hướng dẫn này sẽ chỉ cho bạn quy trình đầy đủ. Bạn sẽ học cách **tạo tài liệu word trống**, chèn một biểu đồ radar, **đặt kích thước biểu đồ trong word**, và bật các đánh dấu trục—tất cả chỉ với vài dòng mã C#.

Thêm dữ liệu trực quan vào báo cáo là một yêu cầu phổ biến, và việc sử dụng Aspose.Words giúp thực hiện điều này một cách dễ dàng. Trong các bước dưới đây, chúng tôi cũng sẽ hướng dẫn cách **thêm biểu đồ vào word** một cách lập trình, để bạn có thể tự động hoá các bảng điều khiển, bản tóm tắt tài chính, hoặc bất kỳ nội dung nào dựa trên dữ liệu.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 hoặc phiên bản mới hơn được cài đặt  
* Giấy phép Aspose.Words for .NET (hoặc bản dùng thử miễn phí) – thư viện cung cấp các API `Document`, `DocumentBuilder`, và biểu đồ được sử dụng trong hướng dẫn này  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  

> **Mẹo:** Nếu bạn đang thử nghiệm, đặt file DLL Aspose.Words vào thư mục `bin` của dự án và tham chiếu nó qua NuGet (`Install-Package Aspose.Words`).

## Cách tạo biểu đồ radar trong tài liệu Word

Bước đầu tiên là **tạo tài liệu word trống** để chứa biểu đồ. Điều này cung cấp cho bạn một canvas sạch và cho phép bạn kiểm soát siêu dữ liệu của tài liệu trước khi thêm bất kỳ nội dung nào.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Lý do quan trọng:* Đối tượng `Document` rỗng đảm bảo không có kiểu dáng hoặc phần ẩn can thiệp vào bố cục biểu đồ. Nó cũng cho phép bạn đặt các thuộc tính tài liệu (tác giả, tiêu đề) sau này nếu cần.

## Cách chèn biểu đồ vào Word bằng Aspose.Words

Tiếp theo, tạo một `DocumentBuilder`. Builder là công cụ chính cho phép bạn chèn văn bản, hình ảnh và biểu đồ vào tài liệu.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Bây giờ bạn có thể **thêm biểu đồ radar** ngay tại vị trí con trỏ đang đứng. Phương thức `InsertChart` nhận một enum `ChartType`, chiều rộng và chiều cao tính bằng điểm.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Tại sao 400 × 300?* Kích thước này cho phép biểu đồ rõ ràng, dễ đọc trên một trang A4 tiêu chuẩn. Bạn có thể điều chỉnh kích thước sau này bằng bước **đặt kích thước biểu đồ trong word** nếu bố cục của bạn yêu cầu tỷ lệ khung hình khác.

## Đặt kích thước biểu đồ trong Word

Nếu cần tinh chỉnh kích thước sau khi chèn, bạn có thể sửa các thuộc tính `Width` và `Height` của biểu đồ. Điều này hữu ích khi văn bản xung quanh hoặc lề trang yêu cầu một cân bằng hình ảnh khác.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Lưu ý:** Phương thức `InsertChart` đã thiết lập kích thước, vì vậy đoạn mã trên là tùy chọn và chỉ được đưa ra để hoàn thiện.

## Bật các dấu tick trên trục bán kính

Biểu đồ radar thực sự hữu ích khi trục bán kính hiển thị các đánh dấu rõ ràng. Các thiết lập sau sẽ bật các dấu tick và đặt khoảng cách 30 độ, phù hợp với các hiển thị radar kiểu la bàn thông thường.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Lý do quan trọng:* Các đánh dấu giúp người đọc ước lượng giá trị tại mỗi góc, cải thiện khả năng đọc cho những người không quen thuộc với dữ liệu.

## Lưu tài liệu chứa biểu đồ

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ thư mục nào; chỉ cần đảm bảo đường dẫn tồn tại.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Khi mở `RadialChart.docx` trong Microsoft Word, bạn sẽ thấy một biểu đồ radar được hiển thị đầy đủ, nằm ở giữa trang, có kích thước như đã chỉ định, với các dấu tick mỗi 30 độ.

### Kết quả mong đợi

* Một tệp `.docx` có tên **RadialChart.docx**  
* Trang đầu tiên chứa một biểu đồ radar kích thước 400 × 300 điểm  
* Trục X (trục bán kính) hiển thị các dấu tick tại 0°, 30°, 60°, …, 330°  

Bạn có thể thay thế chuỗi dữ liệu mẫu bằng giá trị của riêng mình bằng cách truy cập `radarChart.Series` – nhưng điều này nằm ngoài phạm vi của hướng dẫn **thêm biểu đồ radar** cơ bản này.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Điều chỉnh |
|----------|------------|
| **Loại biểu đồ khác** | Thay `ChartType.Radar` bằng `ChartType.Column`, `ChartType.Pie`, v.v. |
| **Nhiều biểu đồ** | Gọi `InsertChart` nhiều lần; mỗi lần sẽ đặt biểu đồ mới sau biểu đồ trước. |
| **Bộ dữ liệu lớn** | Sử dụng `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` để thêm nhiều điểm. |
| **Lưu dưới dạng PDF** | Gọi `document.Save("RadialChart.pdf", SaveFormat.Pdf);` sau khi đã chèn biểu đồ. |
| **Chạy trên .NET Core** | Đảm bảo tham chiếu gói `Aspose.Words.NETCore`; cách dùng API không thay đổi. |

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các bước, các tùy chỉnh kích thước tùy chọn, và các chú thích để dễ hiểu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Chạy chương trình, mở tệp kết quả, và bạn sẽ thấy biểu đồ radar đúng như mô tả.

## Kết luận

Bây giờ bạn đã biết cách **tạo biểu đồ radar** và **thêm biểu đồ vào Word** bằng C#. Hướng dẫn đã bao gồm việc tạo **tài liệu word trống**, chèn biểu đồ radar, **đặt kích thước biểu đồ trong word**, và bật các đánh dấu trục. Với nền tảng này, bạn có thể mở rộng giải pháp để tạo nhiều biểu đồ, chuỗi dữ liệu tùy chỉnh, hoặc xuất ra PDF.

### Các bước tiếp theo

* Khám phá các loại biểu đồ khác với `ChartType` (ví dụ: `Bar`, `Line`) – xem từ khóa **add radar chart** để tìm các ví dụ liên quan.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây liên quan chặt chẽ và xây dựng trên các kỹ thuật đã trình bày trong bài viết này. Mỗi tài nguyên đều bao gồm mã nguồn hoàn chỉnh và giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API khác và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}