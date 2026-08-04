---
category: general
date: 2026-08-04
description: Cách thêm nhãn dữ liệu trong C# với Aspose.Words. Học cách chỉnh sửa
  biểu đồ, căn giữa nhãn dữ liệu biểu đồ, hiển thị phần trăm trong biểu đồ và tùy
  chỉnh nhãn dữ liệu biểu đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: vi
lastmod: 2026-08-04
og_description: Cách thêm nhãn dữ liệu trong C# bằng Aspose.Words. Hướng dẫn này chỉ
  cho bạn cách chỉnh sửa biểu đồ, căn giữa nhãn dữ liệu của biểu đồ, hiển thị tỷ lệ
  phần trăm trong biểu đồ và tùy chỉnh nhãn dữ liệu của biểu đồ.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Cách thêm nhãn dữ liệu vào biểu đồ Word trong C# – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Cách thêm nhãn dữ liệu vào biểu đồ Word trong C# – hướng dẫn từng bước
url: /vi/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm nhãn dữ liệu vào biểu đồ Word trong C# – hướng dẫn từng bước

Nếu bạn cần **how to add data labels** vào một biểu đồ nằm trong tài liệu Word, hướng dẫn này sẽ cho bạn thấy đoạn mã chính xác cần chạy. Bạn sẽ thấy cách chỉnh sửa thuộc tính biểu đồ, **center chart data labels**, **show percentages in chart**, và **customize chart data labels** cho bất kỳ trường hợp nào.

Hướng dẫn bao gồm mọi thứ cần thiết để sửa đổi một biểu đồ hiện có, từ việc tải tài liệu đến lưu các thay đổi. Không cần tham chiếu bên ngoài—chỉ cần thư viện Aspose.Words for .NET và môi trường phát triển C# cơ bản.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 (hoặc mới hơn) đã được cài đặt.  
* Aspose.Words for .NET phiên bản 23.9 hoặc mới hơn.  
  Bạn có thể cài đặt qua NuGet:

```bash
dotnet add package Aspose.Words
```

* Một tệp Word (`input.docx`) chứa ít nhất một biểu đồ.

## Cách thêm nhãn dữ liệu vào biểu đồ Word trong C#

Các phần sau sẽ hướng dẫn bạn từng bước. Từ khóa chính **how to add data labels** xuất hiện tự nhiên trong nội dung và trong các chú thích mã, duy trì mật độ trong phạm vi đề xuất.

### Bước 1 – Tải tài liệu Word chứa biểu đồ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Lý do bước này quan trọng*: Đối tượng `Document` đại diện cho toàn bộ tệp Word. Khi tải nó, bạn có quyền truy cập vào mọi nút, bao gồm các hình dạng chứa biểu đồ.

### Bước 2 – Lấy biểu đồ đầu tiên từ tài liệu

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Lý do bước này quan trọng*: Các biểu đồ được lưu trong các nút `Shape`. Bằng cách ép kiểu nút đã lấy thành `Shape` và gọi `GetChart()`, bạn nhận được một đối tượng `Chart` cho phép truy cập vào series, trục và bộ sưu tập nhãn.

### Bước 3 – Bật tùy chỉnh nhãn dữ liệu và hiển thị phần trăm trong biểu đồ

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Lý do bước này quan trọng*: Thiết lập `ShowPercentage` cho Aspose.Words tính toán và hiển thị tỷ lệ đóng góp của mỗi phần so với tổng. Điều này đáp ứng trực tiếp từ khóa phụ **show percentages in chart**.

### Bước 4 – Thay đổi vị trí nhãn thành trung tâm của mỗi điểm dữ liệu

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Lý do bước này quan trọng*: Thuộc tính `Position` điều khiển nơi nhãn xuất hiện so với điểm dữ liệu. Sử dụng `Center` đáp ứng từ khóa phụ **center chart data labels** và cải thiện khả năng đọc cho các biểu đồ tròn hoặc vòng donut.

### Bước 5 – Tùy chỉnh thêm nhãn dữ liệu biểu đồ (tùy chọn)

Nếu bạn cần kiểm soát nhiều hơn, có thể điều chỉnh phông chữ, màu sắc hoặc đường dẫn dẫn:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Các thiết lập này minh họa từ khóa phụ **customize chart data labels** và cho thấy cách bạn có thể điều chỉnh giao diện để phù hợp với hướng dẫn thương hiệu.

### Bước 6 – Lưu tài liệu đã chỉnh sửa

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Lý do bước này quan trọng*: Khi lưu, biểu đồ đã cập nhật sẽ được ghi lại vào tệp Word, khiến các nhãn dữ liệu mới hiển thị khi mở tệp trong Microsoft Word.

## Ví dụ đầy đủ, có thể chạy ngay

Dưới đây là một chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy. Nó bao gồm tất cả các chỉ thị `using` cần thiết và các chú thích giải thích từng dòng.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Kết quả mong đợi

Khi bạn mở `output.docx` trong Microsoft Word, biểu đồ sẽ hiển thị:

* Giá trị phần trăm bên cạnh mỗi phần (ví dụ: **25 %**, **40 %**, …).
* Nhãn được đặt ở trung tâm của mỗi điểm dữ liệu.
* Bất kỳ kiểu dáng bổ sung nào bạn đã áp dụng, chẳng hạn như văn bản đỏ in đậm.

Những gợi ý trực quan này giúp biểu đồ dễ hiểu hơn, đặc biệt trong các bài thuyết trình hoặc báo cáo.

## Cách chỉnh sửa thuộc tính biểu đồ ngoài nhãn dữ liệu

Mặc dù trọng tâm của hướng dẫn này là **how to add data labels**, bạn cũng có thể muốn **how to edit chart** các thiết lập như tiêu đề, vị trí chú giải, hoặc định dạng trục. Đối tượng `Chart` cung cấp các thuộc tính như `Title`, `Legend`, và `AxisX/AxisY`. Ví dụ, để thay đổi tiêu đề biểu đồ:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Tất cả các thay đổi biểu đồ đều tuân theo cùng một mẫu: lấy biểu đồ, điều chỉnh thuộc tính, sau đó lưu tài liệu.

## Những lỗi thường gặp và mẹo thực hành tốt

| Vấn đề | Nguyên nhân | Giải pháp đề xuất |
|---|---|---|
| Biểu đồ nằm trong một shape nhóm. | `GetChild(NodeType.Shape, …)` trả về nhóm bên ngoài, không phải biểu đồ bên trong. | Tìm đệ quy một shape có `shape.HasChart`. |
| Nhãn dữ liệu không hiển thị sau khi lưu. | `ShowValue` hoặc `ShowPercentage` chưa được đặt thành `true`. | Đặt rõ ràng cả `ShowValue` và `ShowPercentage` theo nhu cầu. |
| Nhãn chồng lên nhau trên các phần nhỏ. | Vị trí trung tâm có thể gây chật chội. | Sử dụng `ChartDataLabelPosition.OutSideEnd` để đặt ngoài, hoặc bật `LeaderLines`. |

Áp dụng những mẹo này sẽ giúp bạn đạt được kết quả ổn định trên các loại biểu đồ khác nhau.

## Kết luận

Bạn đã biết **how to add data labels** vào biểu đồ Word bằng C#. Hướng dẫn đã trình bày cách lấy biểu đồ, bật hiển thị nhãn, căn giữa nhãn, hiển thị phần trăm và tùy chỉnh giao diện. Với kiến thức này, bạn cũng có thể **how to edit chart**, **center chart data labels**, **show percentages in chart**, và **customize chart data labels** cho bất kỳ kịch bản báo cáo nào.

Sẵn sàng khám phá thêm? Hãy thử thêm nhiều series, áp dụng định dạng có điều kiện, hoặc xuất biểu đồ dưới dạng hình ảnh. API Aspose.Words cung cấp khả năng thao tác biểu đồ phong phú—hãy thử nghiệm để tìm ra cách biểu diễn dữ liệu hoàn hảo nhất.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}