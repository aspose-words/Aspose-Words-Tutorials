---
category: general
date: 2026-07-20
description: Thêm nhãn biểu đồ tròn với Aspose.Words cho .NET. Tìm hiểu cách thay
  đổi nhãn biểu đồ tròn, hiển thị nhãn phần trăm và cập nhật nhanh nhãn chuỗi biểu
  đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: vi
lastmod: 2026-07-20
og_description: Thêm nhãn biểu đồ tròn trong C# với Aspose.Words. Thành thạo việc
  thay đổi nhãn biểu đồ tròn, hiển thị nhãn phần trăm và cập nhật nhãn chuỗi biểu
  đồ chỉ trong vài bước.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Thêm nhãn biểu đồ tròn trong C# – Hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Thêm nhãn biểu đồ tròn trong C# bằng Aspose.Words – Hướng dẫn đầy đủ
url: /vi/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm nhãn biểu đồ tròn trong C# bằng Aspose.Words – Hướng dẫn đầy đủ

Cần **thêm nhãn biểu đồ tròn** vào tài liệu Word bằng C#? Với Aspose.Words bạn có thể dễ dàng **thay đổi nhãn biểu đồ tròn** và **hiển thị phần trăm biểu đồ tròn** ngay trong tệp—không cần chỉnh sửa thủ công trong Word.

Trong hướng dẫn này, chúng ta sẽ đi qua các bước chính xác để **hiển thị nhãn phần trăm**, thay đổi vị trí chúng, và thậm chí **cập nhật nhãn chuỗi biểu đồ** cho dữ liệu động. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ dự án .NET nào.

> **Xem nhanh:** Sau khi làm theo hướng dẫn, mở file `.docx` đã lưu sẽ hiển thị một biểu đồ tròn mà mỗi lát được gắn nhãn phần trăm, đặt ngoài lát để dễ đọc nhất.

---

## Bạn sẽ cần

- **Aspose.Words for .NET** (phiên bản mới nhất tính đến năm 2026). Bạn có thể tải về từ NuGet: `Install-Package Aspose.Words`.
- Một **tài liệu Word** đã chứa sẵn biểu đồ tròn hoặc bánh donut (chúng tôi sẽ gọi nó là `Chart.docx`).
- Kiến thức cơ bản về **C#** và Visual Studio (hoặc IDE yêu thích của bạn).

Vậy là xong—không cần thư viện phụ trợ, không cần COM interop, chỉ là mã quản lý thuần túy.

---

## Thêm nhãn biểu đồ tròn – Triển khai đầy đủ

Dưới đây là một chương trình console C# **đầy đủ, có thể chạy** tải tài liệu, sửa đổi biểu đồ tròn đầu tiên và lưu kết quả. Mỗi dòng đều có chú thích để bạn hiểu **tại sao** chúng ta làm như vậy, không chỉ **cái gì**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Kết quả mong đợi

Mở `ChartWithCustomLabels.docx` trong Microsoft Word. Bạn sẽ thấy biểu đồ tròn **với nhãn phần trăm được đặt ngoài mỗi lát**. Các nhãn trông giống như “35 %”, “20 %”, v.v., giúp biểu đồ ngay lập tức dễ hiểu.

---

## Thay đổi nhãn biểu đồ tròn: vị trí và định dạng

Nếu bạn chỉ cần **thay đổi nhãn biểu đồ tròn** mà không hiển thị phần trăm, bạn có thể điều chỉnh thuộc tính `Position` thành một trong các giá trị sau:

| Enum Vị trí   | Hiệu ứng trực quan |
|---------------|--------------------|
| `InsideEnd`   | Nhãn nằm bên trong lát, ngay tại cạnh. |
| `Center`      | Nhãn xuất hiện ở giữa lát (tốt cho biểu đồ tròn nhỏ). |
| `OutsideEnd`  | Nhãn nằm ngoài lát, được nối bằng đường dẫn (mặc định của chúng tôi). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Mẹo:** `OutsideEnd` hoạt động tốt nhất khi biểu đồ có nhiều lát; nó ngăn chặn việc văn bản chồng lên nhau.

---

## Hiển thị nhãn phần trăm trên biểu đồ tròn

Thuộc tính `ShowPercentage` là một **cờ boolean**. Đặt nó thành `true` sẽ yêu cầu Aspose.Words tính toán đóng góp của mỗi lát dựa trên nguồn dữ liệu gốc.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Bạn cũng có thể kết hợp với `ShowValue` nếu cần cả số nguyên **và** phần trăm:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Khi cả hai cờ đều được bật, nhãn sẽ hiển thị như “45 % (120)”.

---

## Cập nhật nhãn chuỗi biểu đồ cho dữ liệu động

Thường bạn sẽ tạo biểu đồ ngay lập tức—ví dụ doanh thu hàng tháng hoặc kết quả khảo sát. Để **cập nhật nhãn chuỗi biểu đồ** một cách lập trình, hãy sửa đổi bộ sưu tập `Series` trước khi thao tác với nhãn dữ liệu:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Đoạn mã này minh họa cách **cập nhật nhãn chuỗi biểu đồ** cho bất kỳ chuỗi nào, không chỉ chuỗi đầu tiên. Nó hữu ích khi bạn xây dựng báo cáo kết hợp dữ liệu thực tế và dự báo.

---

## Trường hợp đặc biệt & Những bẫy thường gặp

| Tình huống | Điều cần chú ý | Cách khắc phục |
|-----------|----------------|----------------|
| **Biểu đồ không phải dạng tròn/donut** | `Position` có thể không có hiệu ứng trực quan nào. | Xác minh `chart.Type` là `ChartType.Pie` hoặc `ChartType.Doughnut`. |
| **Không tìm thấy biểu đồ** | `GetChild` trả về `null`. | Thêm câu kiểm tra (xem mã) và ghi lại thông báo hữu ích. |
| **Phiên bản Word cũ** | Một số tính năng nhãn bị bỏ qua. | Lưu dưới dạng `.docx` (định dạng hiện đại) để đảm bảo hỗ trợ đầy đủ. |
| **Số lượng lát lớn** | Nhãn có thể chồng lên nhau ngay cả khi dùng `OutsideEnd`. | Xem xét giảm số lượng lát hoặc tăng kích thước biểu đồ. |

---

## Ví dụ hoạt động đầy đủ (Sao chép‑Dán)

Dưới đây là **toàn bộ chương trình** bạn có thể sao chép vào một dự án console mới. Chỉ cần thay thế `YOUR_DIRECTORY` bằng thư mục chứa `Chart.docx`.



## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với hướng dẫn chi tiết từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Đặt tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Tùy chỉnh một chuỗi biểu đồ trong biểu đồ](/words/english/net/programming-with-charts/single-chart-series/)
- [Chèn biểu đồ cột trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}