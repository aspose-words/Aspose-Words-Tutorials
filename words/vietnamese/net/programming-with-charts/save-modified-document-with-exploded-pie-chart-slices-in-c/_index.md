---
category: general
date: 2026-10-13
description: 'Lưu tài liệu đã chỉnh sửa sau khi tùy chỉnh biểu đồ tròn: tách các phần,
  thay đổi góc của phần đầu tiên và hiển thị nhãn phần trăm trong C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: vi
lastmod: 2026-10-13
og_description: Lưu tài liệu đã chỉnh sửa sau khi tùy chỉnh biểu đồ tròn trong C#.
  Tìm hiểu cách tách các phần của biểu đồ tròn, thay đổi góc của phần đầu tiên và
  hiển thị nhãn phần trăm.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Lưu tài liệu đã chỉnh sửa với các lát bánh biểu đồ tròn tách ra – Hướng
  dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Lưu tài liệu đã chỉnh sửa với các lát biểu đồ tròn nổ ra trong C#
url: /vi/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu đã chỉnh sửa với các lát biểu đồ tròn bị nổ trong C#

Nếu bạn cần **save modified document** sau khi chỉnh sửa một biểu đồ tròn trong Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ học cách nổ các lát biểu đồ tròn, thay đổi góc của lát đầu tiên và hiển thị nhãn phần trăm — chỉ với vài dòng mã C#.

Tùy chỉnh biểu đồ là một yêu cầu phổ biến khi tạo báo cáo, hoá đơn hoặc bảng điều khiển một cách tự động. Khi kết thúc hướng dẫn này, bạn sẽ có thể tải tệp DOCX, chỉnh sửa giao diện biểu đồ và **save modified document** sẵn sàng để phân phối.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 hoặc mới hơn (bản dùng thử miễn phí hoặc bản có giấy phép)
- Tệp Word (`input.docx`) chứa một biểu đồ tròn duy nhất
- Visual Studio 2022 hoặc bất kỳ IDE C# nào

> **Tip:** Gói NuGet Aspose.Words được thêm bằng `dotnet add package Aspose.Words`.

## Bước 1: Tải tài liệu Word chứa biểu đồ

Bước đầu tiên là mở tệp DOCX nguồn. Lớp `Document` đại diện cho toàn bộ tệp Word trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Việc tải tài liệu cho phép bạn truy cập đầy đủ vào mọi nút, bao gồm các hình dạng chứa biểu đồ.

## Bước 2: Lấy hình dạng biểu đồ đầu tiên từ tài liệu

Biểu đồ được lưu trong các nút `Shape`. Bạn có thể tìm biểu đồ đầu tiên bằng `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Nếu tài liệu chứa nhiều biểu đồ, hãy điều chỉnh chỉ mục (`0`) hoặc lặp qua bộ sưu tập. Dòng này đảm bảo bạn có một tham chiếu tới đối tượng `Chart` sẽ được chỉnh sửa.

## Bước 3: Nổ các lát biểu đồ tròn

Việc nổ một lát sẽ tách nó ra khỏi phần còn lại của bánh, giúp biểu đồ dễ đọc hơn. Thuộc tính `Explode` áp dụng cho toàn bộ series.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Đặt `Explode` thành `true` **explodes pie chart slices** cho toàn bộ series, hữu ích khi bạn muốn mọi lát đều nổi bật.

## Bước 4: Thay đổi góc của lát đầu tiên

Đôi khi bạn cần lát đầu tiên bắt đầu ở một góc tùy chỉnh, ví dụ để phù hợp với hướng dẫn thiết kế.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Thuộc tính `FirstSliceAngle` **changes first slice** hướng, xoay toàn bộ bánh sao cho lát đầu tiên bắt đầu ở góc 30 độ.

## Bước 5: Hiển thị nhãn phần trăm trên các lát bánh

Hiển thị đóng góp số liệu của mỗi lát thường được yêu cầu trong báo cáo. Cờ `DataLabel.ShowPercentage` bật giá trị phần trăm.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Bước này **show percentage labels** trực tiếp trên biểu đồ, đồng thời đáp ứng yêu cầu **display percentages pie**.

## Bước 6: Lưu tài liệu đã chỉnh sửa

Sau khi áp dụng tất cả các tùy chỉnh, lưu các thay đổi vào một tệp mới. Phương thức `Save` ghi DOCX đã cập nhật lên đĩa.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Bây giờ bạn có một **save modified document** chứa biểu đồ tròn bị nổ, lát đầu tiên đã xoay và nhãn phần trăm hiển thị.

![Tài liệu đã lưu hiển thị biểu đồ tròn bị nổ](/images/pie-chart-exploded.png "Tài liệu đã lưu với các lát biểu đồ tròn bị nổ và nhãn phần trăm")

*Ảnh chụp màn hình minh họa kết quả cuối cùng sau khi tài liệu được lưu.*

## Ví dụ đầy đủ, có thể chạy

Kết hợp các phần lại, dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một dự án console:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Kết quả mong đợi

Mở `output.docx` sẽ hiển thị một biểu đồ tròn nơi:

- Mỗi lát được tách ra một chút (**exploded pie chart slices**)
- Lát đầu tiên bắt đầu ở góc lệch 30 độ (**change first slice**)
- Mỗi lát hiển thị đóng góp của nó dưới dạng phần trăm (**show percentage labels**, **display percentages pie**)
- Tệp đã được **save modified document** mà không làm thay đổi bản gốc.

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Câu hỏi | Câu trả lời |
|----------|--------|
| **Nếu tài liệu không có biểu đồ thì sao?** | Mã kiểm tra `null` sau `GetChild`. Nếu không có biểu đồ, bạn có thể thêm một biểu đồ bằng chương trình hoặc dừng lại với thông báo rõ ràng. |
| **Tôi có thể nổ chỉ một lát duy nhất không?** | Có. Sử dụng `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` trong đó `i` là chỉ mục của lát. |
| **Làm sao để thay đổi định dạng nhãn (ví dụ: hiển thị giá trị + %)?** | Đặt `chart.PieChart.DataLabel.ShowValue = true;` và tùy chọn `chart.PieChart.DataLabel.ShowPercentage = true;` để kết hợp cả hai. |
| **Kiểu biểu đồ có được giữ nguyên sau khi lưu không?** | Aspose.Words giữ lại mọi kiểu dáng, bao gồm màu sắc và phông chữ, khi bạn **save modified document**. |
| **Tôi có thể xử lý nhiều biểu đồ trong cùng một tệp không?** | Lặp qua tất cả các nút `Shape` bằng `NodeType.Shape` và lọc bằng `shape.HasChart`. Áp dụng các bước tương tự cho mỗi biểu đồ. |

## Kết luận

Bây giờ bạn đã biết cách **save modified document** sau khi tùy chỉnh biểu đồ tròn trong Word bằng chương trình. Hướng dẫn đã đề cập đến việc nổ các lát biểu đồ tròn, thay đổi góc của lát đầu tiên và hiển thị nhãn phần trăm — đáp ứng các yêu cầu **show percentage labels**, **explode pie chart slices**, **display percentages pie**, và **change first slice**.

Tiếp theo, hãy khám phá:

- Thêm series dữ liệu một cách động (`chart.Series.Add(...)`)  
- Tùy chỉnh vị trí chú giải và tiêu đề biểu đồ  
- Chuyển đổi DOCX sang PDF trong khi giữ nguyên kiểu biểu đồ  

Bạn có thể tự do thử nghiệm các góc khác nhau, cài đặt nổ, hoặc định dạng nhãn để phù hợp với nhu cầu báo cáo của mình. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách lưu tài liệu đã chỉnh sửa trong C# với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Cập nhật dữ liệu series biểu đồ trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Chèn biểu đồ cột vào tài liệu Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}