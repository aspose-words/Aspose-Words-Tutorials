---
category: general
date: 2026-08-04
description: Tùy chỉnh vị trí nhãn dữ liệu cho biểu đồ trong C# cho phép bạn căn giữa
  nhãn trên các phần của biểu đồ. Hãy làm theo hướng dẫn từng bước này bằng API biểu
  đồ của Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: vi
lastmod: 2026-08-04
og_description: Đặt vị trí nhãn dữ liệu tùy chỉnh cho biểu đồ trong C# cho bạn biết
  cách căn giữa tất cả các nhãn dữ liệu trên mỗi phần của biểu đồ Word. Thành thạo
  việc định vị nhãn dữ liệu biểu đồ với Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Đặt nhãn dữ liệu tùy chỉnh cho biểu đồ trong C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Định vị nhãn dữ liệu tùy chỉnh cho biểu đồ trong C#
url: /vi/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt vị trí nhãn dữ liệu tùy chỉnh cho biểu đồ trong C#

**Custom Data‑Label Placement for Charts** cho phép bạn kiểm soát chính xác vị trí của mỗi nhãn trên biểu đồ trong tài liệu Word. Trong hướng dẫn này, bạn sẽ học cách căn giữa tất cả các nhãn dữ liệu trên mỗi phần bằng C# và API biểu đồ của Aspose.Words.

Bạn sẽ nhận được một ví dụ đầy đủ, có thể chạy được, tải một tệp `.docx`, truy cập hình dạng biểu đồ đầu tiên, thay đổi `Position` của mọi nhãn thành `Center`, và lưu tài liệu đã cập nhật. Không cần tham chiếu bên ngoài—chỉ cần thư viện Aspose.Words cho .NET và môi trường phát triển C# cơ bản.

**Bạn sẽ học**

* Cách tải tài liệu Word chứa biểu đồ.  
* Cách xác định hình dạng biểu đồ bằng API biểu đồ của Aspose.Words.  
* Cách áp dụng **chart data label positioning** cho mọi series trong biểu đồ.  
* Cách lưu tài liệu để các nhãn được căn giữa hiển thị trong Word.  

**Yêu cầu**

* .NET 6.0 (hoặc phiên bản mới hơn) đã được cài đặt.  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào).  
* Tham chiếu tới gói NuGet `Aspose.Words`.  
* Tệp Word (`Chart.docx`) chứa ít nhất một biểu đồ.

---

## Đặt vị trí nhãn dữ liệu tùy chỉnh cho biểu đồ – bước 1: tải tài liệu

Hành động đầu tiên là mở tệp Word chứa biểu đồ. `Document` là điểm vào cho mọi thao tác với Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Why this step matters*: *Tại sao bước này quan trọng*: Nếu không tải tài liệu, bạn không thể truy cập đối tượng biểu đồ. Việc xác thực đảm bảo bạn nhận được lỗi rõ ràng nếu tệp không có biểu đồ, tránh lỗi tham chiếu null sau này.

---

## Sử dụng API biểu đồ của Aspose.Words để truy cập các hình dạng biểu đồ

Aspose.Words coi một biểu đồ là đối tượng `Chart` nằm bên trong một `Shape`. Bạn lấy nó bằng cách ép kiểu nút con thích hợp.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Why this step matters*: *Tại sao bước này quan trọng*: Truy cập trực tiếp `Chart` cho bạn toàn quyền kiểm soát các series, điểm dữ liệu và thuộc tính nhãn. Nếu hình dạng không phải là biểu đồ, mã sẽ dừng sớm với thông báo chi tiết.

---

## Đặt vị trí nhãn dữ liệu biểu đồ trong C#

Bây giờ lặp qua mọi series và mọi nhãn dữ liệu, đặt `Position` thành `Center`. Đây là phần cốt lõi của **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tip**: **Mẹo chuyên nghiệp**: Nếu bạn cần vị trí khác (ví dụ, `InsideEnd` cho biểu đồ cột), hãy thay đổi giá trị enum tương ứng. Enum `ChartDataLabelPosition` bao gồm tất cả các vị trí tiêu chuẩn được Word hỗ trợ.

*Why this step matters*: *Tại sao bước này quan trọng*: Thay đổi `label.Position` cập nhật biểu diễn OOXML bên dưới, vì vậy nhãn sẽ hiển thị ở giữa khi tài liệu được mở trong Microsoft Word.

---

## Lưu tài liệu Word với các nhãn đã cập nhật

Sau khi chỉnh sửa biểu đồ, lưu các thay đổi trở lại tệp. Bạn có thể ghi đè lên tệp gốc hoặc tạo một bản sao mới.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Why this step matters*: *Tại sao bước này quan trọng*: Lưu sẽ ghi OOXML đã cập nhật lên đĩa. Mở `ChartLabelsCentered.docx` trong Word sẽ hiển thị mỗi nhãn phần được căn giữa, xác nhận rằng **Custom Data‑Label Placement for Charts** đã thành công.

---

## Các trường hợp đặc biệt và biến thể

| Tình huống | Cách xử lý |
|-----------|---------------|
| **Multiple charts** trong cùng một tài liệu | Lặp qua `doc.GetChildNodes(NodeType.Shape, true)` và kiểm tra `shape.HasChart` cho mỗi shape. |
| **Different chart types** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` hoạt động cho biểu đồ dạng bánh. Đối với biểu đồ cột/đường, bạn có thể muốn `InsideEnd` hoặc `OutsideEnd`. |
| **Label text needs formatting** | Truy cập `label.TextProperties` để đặt kích thước phông chữ, màu sắc hoặc in đậm. |
| **Running on .NET Core** | Đảm bảo bạn tham chiếu phiên bản .NET Standard của Aspose.Words; API giống nhau. |

---

## Ví dụ làm việc đầy đủ

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các chỉ thị `using` cần thiết và xử lý lỗi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Expected result**: **Kết quả mong đợi**: Mở `ChartLabelsCentered.docx` trong Microsoft Word. Mỗi phần của biểu đồ bây giờ hiển thị nhãn dữ liệu ngay ở trung tâm của phần, tạo ra giao diện trực quan sạch sẽ hơn.

---

## Kết luận

Bây giờ bạn đã có một giải pháp **Custom Data‑Label Placement for Charts** hoàn chỉnh trong C#. Bằng cách tải tài liệu, truy cập biểu đồ qua API biểu đồ của Aspose.Words, đặt `ChartDataLabelPosition.Center` cho mọi nhãn, và lưu tệp, bạn có thể tự động hoá việc đặt vị trí nhãn cho bất kỳ biểu đồ nào trong Word.

Tiếp theo, khám phá các tùy chọn **chart data label positioning** khác như `InsideEnd` hoặc `OutsideEnd`, hoặc thử nghiệm **C# chart manipulation** để thay đổi màu sắc, thêm chú giải, hoặc tạo biểu đồ từ đầu. Những mở rộng này dựa trực tiếp trên các kỹ thuật đã trình bày ở đây và mở rộng kỹ năng tự động hoá biểu đồ trong tài liệu Word của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}