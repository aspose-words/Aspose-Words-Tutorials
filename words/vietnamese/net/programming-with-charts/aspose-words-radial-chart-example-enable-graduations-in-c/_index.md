---
category: general
date: 2026-10-13
description: Ví dụ biểu đồ tròn của Aspose.Words cho thấy cách bật các đánh dấu chia
  độ trên biểu đồ tròn bằng C# và Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: vi
lastmod: 2026-10-13
og_description: Ví dụ biểu đồ tròn Aspose.Words minh họa cách bật các đánh dấu chia
  độ trên biểu đồ tròn bằng C# và thư viện mới nhất 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Ví dụ biểu đồ dạng tròn Aspose.Words – bật các đánh dấu chia độ trong C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Ví dụ biểu đồ dạng tròn Aspose.Words: bật các chia độ trong C#'
url: /vi/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ví dụ biểu đồ radial Aspose.Words: bật các đánh dấu chia độ trong C#

Nếu bạn đang tìm kiếm một **aspose.words radial chart example**, bạn đã đến đúng nơi. Hướng dẫn này sẽ đưa bạn qua các bước chính xác để bật các đánh dấu chia độ cho biểu đồ radial bằng API Aspose.Words cho .NET.

Biểu đồ radial hữu ích cho việc trực quan hoá dữ liệu chu kỳ như các chỉ số theo thời gian trong ngày hoặc xu hướng theo mùa. Mặc định, các đánh dấu chia độ (các dấu tick quanh trục vòng) bị ẩn, điều này có thể làm cho biểu đồ khó đọc. Việc bật chúng chỉ cần một dòng lệnh, nhưng bạn cần biết mô hình đối tượng đúng và phiên bản hỗ trợ tính năng này.

Trong hướng dẫn này, bạn sẽ học cách:

* Tải tài liệu Word đã chứa một biểu đồ radial.  
* Truy cập hình dạng biểu đồ qua API biểu đồ Aspose.Words.  
* Bật **hiển thị các đánh dấu chia độ** (có sẵn từ **Aspose.Words version 24.9**).  
* Lưu tài liệu đã chỉnh sửa và xác minh kết quả.

Mã nguồn đầy đủ, có thể chạy được đã được bao gồm, vì vậy bạn có thể sao chép‑dán vào một dự án console mới và ngay lập tức thấy hiệu ứng.

![Ví dụ biểu đồ radial Aspose.Words với các đánh dấu chia độ](https://example.com/images/radial-chart-graduations.png "Ví dụ biểu đồ radial Aspose.Words hiển thị các đánh dấu chia độ đã bật")

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

| Yêu cầu | Tại sao quan trọng |
|-------------|----------------|
| .NET 6.0 hoặc mới hơn | Aspose.Words for .NET 24.9+ nhắm tới .NET Standard 2.0 và hoạt động trên .NET 6+. |
| Aspose.Words for .NET **24.9** hoặc mới hơn | Thuộc tính `IsGraduationsVisible` được giới thiệu ở phiên bản 24.9. Các phiên bản cũ sẽ ném `MissingMemberException`. |
| Tài liệu Word (`RadialChart.docx`) chứa một biểu đồ radial | Ví dụ thao tác trên một biểu đồ đã tồn tại; việc tạo mới từ đầu là một chủ đề riêng. |
| IDE C# (Visual Studio, Rider, VS Code) | Bất kỳ IDE nào có thể biên dịch dự án .NET đều hoạt động. |
| Gói NuGet `Aspose.Words` | Cài đặt bằng `dotnet add package Aspose.Words --version 24.9.0` (hoặc mới hơn). |

> **Mẹo chuyên nghiệp:** Nếu bạn không thể nâng cấp lên 24.9, bạn vẫn có thể chỉnh sửa các thuộc tính biểu đồ khác, nhưng các đánh dấu chia độ sẽ vẫn bị ẩn vì API không cung cấp cờ này.

## Ví dụ biểu đồ radial Aspose.Words – hướng dẫn chi tiết từng bước

Các phần sau chia quá trình thành các bước rời rạc, dễ theo dõi. Mỗi bước bao gồm mã chính xác bạn cần và một giải thích ngắn gọn về *lý do* bước đó tồn tại.

### Bước 1: Tải tài liệu chứa một biểu đồ radial

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Tại sao điều này quan trọng:**  
`Document` là điểm vào của **Aspose.Words chart API**. Nó tải tệp DOCX vào bộ nhớ, cho phép bạn truy cập mọi nút—đoạn văn, bảng và hình dạng biểu đồ. Nếu không tìm thấy tệp, `Document` sẽ ném `FileNotFoundException`, bạn nên xử lý lỗi này trong mã sản xuất.

### Bước 2: Lấy hình dạng biểu đồ đầu tiên từ tài liệu

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Tại sao điều này quan trọng:**  
Biểu đồ được lưu dưới dạng nút `Shape`. Phương thức `GetChild` với `NodeType.Shape` duyệt DOM và trả về hình dạng đầu tiên khớp. Ép kiểu sang `Chart` cho phép bạn truy cập các thuộc tính đặc thù của biểu đồ như `RadialChart`. Kiểm tra null đảm bảo bạn nhận được lỗi rõ ràng nếu tài liệu không chứa biểu đồ, một trường hợp thường gặp khi tái sử dụng mẫu.

### Bước 3: Bật các đánh dấu chia độ trên biểu đồ radial

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Tại sao điều này quan trọng:**  
`IsGraduationsVisible` điều khiển các dấu tick quanh trục vòng. Khi đặt `true`, biểu đồ sẽ hiển thị các đánh dấu chia độ, cải thiện khả năng đọc cho người dùng cần đo giá trị một cách chính xác. Thuộc tính này nằm dưới `RadialChart`, một kiểu phụ của `Chart`. Nếu bạn áp dụng trên biểu đồ không phải radial (ví dụ: biểu đồ cột), thuộc tính `RadialChart` sẽ là `null`, vì vậy bạn nên xác minh loại biểu đồ trước trong các kịch bản phức tạp.

#### Xử lý biểu đồ không phải radial (tùy chọn)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Điều kiện này làm cho mã trở nên vững chắc khi tài liệu nguồn có thể chứa các loại biểu đồ khác nhau.

### Bước 4: Lưu tài liệu đã chỉnh sửa

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Tại sao điều này quan trọng:**  
Gọi `Save` ghi lại DOM trong bộ nhớ trở lại tệp .docx, lưu lại thay đổi bạn đã thực hiện trên biểu đồ. Tệp đầu ra có thể mở bằng Microsoft Word, LibreOffice hoặc bất kỳ trình xem nào hỗ trợ DOCX. Bạn sẽ thấy biểu đồ radial với các đánh dấu chia độ hiển thị.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh bạn có thể dán vào `Program.cs` của một dự án console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Kết quả mong đợi

Khi mở `RadialChart_Graduations.docx` trong Word, biểu đồ radial sẽ hiển thị các dấu tick (đánh dấu chia độ) quanh trục vòng, tương tự như ảnh chụp màn hình ở trên. Các thành phần khác của biểu đồ (dòng dữ liệu, chú giải, tiêu đề) vẫn giữ nguyên.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Giải pháp |
|-----------|----------|
| **Phiên bản Aspose.Words cũ (< 24.9)** | Nâng cấp lên gói NuGet mới nhất. Thuộc tính `IsGraduationsVisible` không tồn tại trong các phiên bản trước. |
| **Nhiều biểu đồ trong cùng một tài liệu** | Sử dụng `doc.GetChild(NodeType.Shape, index, true)` với `index` phù hợp hoặc lặp qua `doc.GetChildNodes(NodeType.Shape, true)` và lọc bằng `ChartType.Radial`. |
| **Biểu đồ được tạo lập trình** | Sử dụng `DocumentBuilder` để chèn biểu đồ, sau đó đặt `RadialChart.IsGraduationsVisible` trên biểu đồ |

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cập nhật dữ liệu chuỗi biểu đồ trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Xóa một chuỗi biểu đồ khỏi tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Ẩn viền khu vực vẽ trong biểu đồ cột với Aspose.Words cho .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}