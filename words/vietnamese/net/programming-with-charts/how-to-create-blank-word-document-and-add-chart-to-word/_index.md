---
category: general
date: 2026-09-08
description: Tạo tài liệu Word trống và thêm biểu đồ vào Word bằng Aspose.Words. Tìm
  hiểu cách chèn biểu đồ radar, bật các chia độ và lưu tệp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: vi
lastmod: 2026-09-08
og_description: Tạo tài liệu Word trống và thêm biểu đồ vào Word bằng Aspose.Words.
  Hướng dẫn này chỉ cách chèn biểu đồ radar, cấu hình các trục và lưu tài liệu.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Tạo tài liệu Word trống và thêm biểu đồ radar – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Cách tạo tài liệu Word trống và chèn biểu đồ vào Word
url: /vi/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và chèn biểu đồ vào Word

Nếu bạn cần **tạo tài liệu Word trống** cho báo cáo, mẫu hoặc mail‑merge tự động, hướng dẫn này sẽ dẫn bạn qua toàn bộ quá trình bằng C# và Aspose.Words. Bạn cũng sẽ học cách **chèn biểu đồ vào Word**, cụ thể là **chèn biểu đồ radar**, bật các graduation và lưu kết quả dưới dạng tệp .docx.

Bài tutorial này bao gồm mọi thứ từ thiết lập dự án đến bước kiểm tra cuối cùng. Khi hoàn thành, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ ứng dụng .NET nào. Không yêu cầu kinh nghiệm trước với Aspose.Words, nhưng bạn nên có kiến thức cơ bản về C# và đã cài đặt .NET SDK mới nhất.

## Yêu cầu trước

- .NET 6.0 SDK trở lên  
- Aspose.Words for .NET (gói NuGet `Aspose.Words`)  
- Một IDE như Visual Studio 2022 hoặc VS Code  
- Quyền ghi vào thư mục sẽ lưu tài liệu  

Bạn có thể cài đặt thư viện bằng lệnh sau:

```bash
dotnet add package Aspose.Words
```

## Bước 1: Tạo tài liệu Word trống

Bước đầu tiên là **tạo tài liệu Word trống** trong bộ nhớ. Lớp `Document` đại diện cho toàn bộ tệp, trong khi `DocumentBuilder` cung cấp API dạng fluent để thêm nội dung.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` bắt đầu rỗng, vì vậy bạn có một canvas sạch để đặt biểu đồ. Giữ tài liệu ở trạng thái trống ở giai đoạn này giúp bạn dễ dàng tái sử dụng cùng một đoạn mã cho các mẫu khác nhau.

## Bước 2: Thêm biểu đồ vào Word

Tiếp theo, chúng ta **thêm biểu đồ vào Word** bằng cách gọi `InsertChart`. Phương thức này yêu cầu loại biểu đồ và kích thước mong muốn tính bằng điểm (1 point = 1/72 inch).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` báo cho Aspose.Words tạo một biểu đồ dạng bán kính, lý tưởng để hiển thị dữ liệu đa biến trong bố cục vòng tròn. Các giá trị kích thước (400 × 300) phù hợp với hầu hết các trang dọc, nhưng bạn có thể điều chỉnh chúng để phù hợp với bố cục của mình.

## Bước 3: Chèn biểu đồ radar và cấu hình graduation

Bây giờ chúng ta **chèn biểu đồ radar** và bật graduation (đánh dấu) trên cả trục danh mục (X) và trục giá trị (Y). Graduation giúp cải thiện khả năng đọc bằng cách hiển thị vị trí chính xác cho mỗi điểm dữ liệu.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Đặt `HasGraduations` thành `true` sẽ vẽ các dấu tick trên các trục. Tham số tùy chọn `GraduationStep` kiểm soát khoảng cách giữa các tick trên trục bán kính; bước 10 nghĩa là một tick mỗi 10 độ.

### Mẹo chuyên nghiệp
Nếu bạn cần hiển thị nhãn dữ liệu, gọi `radarChart.Series[0].HasDataLabel = true;`. Điều này sẽ thêm giá trị số bên cạnh mỗi điểm, rất hữu ích cho các buổi thuyết trình.

## Bước 4: Điền dữ liệu mẫu vào biểu đồ (tùy chọn)

Một biểu đồ radar không có dữ liệu sẽ không hiển thị. Dưới đây là cách nhanh chóng để thêm một loạt giá trị mẫu. Bạn có thể thay thế khối này bằng nguồn dữ liệu của riêng mình.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Mỗi lần gọi `Add` sẽ chèn một điểm vào series. Thứ tự các điểm tương ứng với vị trí góc quanh vòng tròn.

## Bước 5: Lưu tài liệu chứa biểu đồ

Cuối cùng, lưu tài liệu vào đĩa. Phương thức `Save` tự động ghi tệp .docx, bảo toàn biểu đồ và mọi định dạng.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Chạy chương trình sẽ tạo một **tài liệu Word trống** hiện đã chứa một biểu đồ radar hoạt động đầy đủ. Mở tệp trong Microsoft Word để xem kết quả.

![Biểu đồ radar trong tài liệu Word](radar_chart.png){alt="Biểu đồ radar được chèn vào tài liệu Word trống"}

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cần thay đổi |
|-----------|--------------|
| **Kích thước biểu đồ khác** | Điều chỉnh các tham số width/height của `InsertChart`. |
| **Các loại biểu đồ khác** | Thay `ChartType.Radar` bằng `ChartType.Column`, `ChartType.Pie`, v.v., và giữ nguyên logic graduation. |
| **Lưu vào stream** | Sử dụng `document.Save(Stream, SaveFormat.Docx)` |

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}