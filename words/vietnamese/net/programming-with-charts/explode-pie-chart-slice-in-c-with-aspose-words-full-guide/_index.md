---
category: general
date: 2026-07-19
description: Tách miếng bánh tròn trong biểu đồ bằng Aspose.Words cho C#. Tìm hiểu
  cách tách miếng bánh, điều chỉnh kích thước lỗ bánh donut và nhanh chóng thay đổi
  các điểm dữ liệu của biểu đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: vi
lastmod: 2026-07-19
og_description: Tách phần bánh pie trong biểu đồ bằng Aspose.Words cho C#. Hướng dẫn
  này chỉ cho bạn cách tách phần bánh, điều chỉnh kích thước lỗ bánh donut và thay
  đổi các điểm dữ liệu biểu đồ một cách hiệu quả.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Tách miếng biểu đồ tròn trong C# – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Tách miếng biểu đồ tròn trong C# với Aspose.Words – Hướng dẫn đầy đủ
url: /vi/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bẻ Tách Miếng Bánh Pie trong C# với Aspose.Words – Hướng Dẫn Đầy Đủ

Bạn đã bao giờ tự hỏi cách **bẻ tách miếng bánh pie** trong tài liệu Word bằng C# chưa? Bạn không phải là người duy nhất. Dù bạn đang chuẩn bị một bản thuyết trình bán hàng hay trực quan hoá kết quả khảo sát, một miếng bánh bẻ tách có thể thu hút ánh nhìn đúng nơi bạn muốn. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình — tải tài liệu, lấy biểu đồ, bẻ tách miếng đầu tiên, điều chỉnh lỗ bánh donut, và thậm chí thay đổi các điểm dữ liệu của biểu đồ.

Chúng tôi cũng sẽ đề cập đến các khái niệm phụ mà bạn có thể đang tìm kiếm: **cách bẻ tách miếng bánh pie**, **điều chỉnh kích thước lỗ bánh donut**, và **thay đổi các điểm dữ liệu của biểu đồ**. Không có phần thừa, chỉ có giải pháp sẵn sàng sao chép‑dán.

---

## Những Gì Bạn Cần Chuẩn Bị

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- **Aspose.Words for .NET** (phiên bản mới nhất tính đến ngày 2026‑07‑19). Bạn có thể tải về từ NuGet bằng lệnh `Install-Package Aspose.Words`.
- Dự án **.NET 6+** (hoặc .NET Framework 4.7.2+ nếu bạn vẫn đang dùng phiên bản cũ).
- Một tệp Word (`Chart.docx`) đã chứa sẵn biểu đồ pie hoặc donut. Nếu chưa có, hãy tạo nhanh một biểu đồ trong Word và lưu lại.

Đó là tất cả — không cần thư viện phụ, không cần COM interop, chỉ cần mã quản lý thuần túy.

---

## Bẻ Tách Miếng Bánh Pie – Triển Khai Từng Bước

Dưới đây chúng tôi chia nhiệm vụ thành các bước nhỏ gọn. Mỗi phần có tiêu đề rõ ràng, đoạn mã mẫu, và giải thích ngắn gọn *tại sao* chúng ta làm như vậy.

### Bước 1: Cài Đặt và Tham Chiếu Aspose.Words

Đầu tiên, thêm gói Aspose.Words vào dự án của bạn. Trong Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Mẹo:** Nếu bạn dùng giao diện NuGet tích hợp trong Visual Studio, hãy tìm “Aspose.Words” và nhấn Install. Điều này sẽ giúp bạn nhận được các bản sửa lỗi mới nhất và khả năng làm việc với biểu đồ ngay từ đầu.

### Bước 2: Tải Tài Liệu Word Chứa Biểu Đồ

Chúng ta cần một đối tượng `Document` trỏ tới file `.docx` có biểu đồ bạn muốn chỉnh sửa.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Tại sao lại quan trọng:** `Document` là điểm vào cho mọi thao tác trong Aspose.Words. Kiểm tra sự tồn tại của biểu đồ ngay từ đầu giúp tránh lỗi tham chiếu null khi chúng ta cố gắng bẻ tách miếng.

### Bước 3: Lấy Node Biểu Đồ Đầu Tiên

Hầu hết các ví dụ giả định chỉ có một biểu đồ, vì vậy chúng ta sẽ lấy biểu đồ đầu tiên. Nếu có nhiều biểu đồ, hãy điều chỉnh chỉ số cho phù hợp.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Lưu ý:** Việc ép kiểu sang `Chart` là an toàn sau khi chúng ta đã xác nhận tồn tại biểu đồ. Đối tượng này cho phép truy cập vào series, data points và các thiết lập riêng của loại biểu đồ.

### Bước 4: Bẻ Tách Miếng Đầu Tiên của Biểu Đồ Pie

Bây giờ là phần trọng tâm — **cách bẻ tách miếng bánh pie**. Chúng ta sẽ đặt thuộc tính `Exploded` của data point đầu tiên.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Tại sao lại hoạt động:** `Exploded` báo cho Word kéo miếng đó ra khỏi trung tâm, tạo hiệu ứng “bẻ tách bánh” cổ điển. Thuộc tính này là boolean, nên đặt `true` là đủ.

### Bước 5: Điều Chỉnh Kích Thước Lỗ Bánh Donut (Nếu Là Biểu Đồ Donut)

Nếu biểu đồ của bạn là donut, bạn có thể muốn **điều chỉnh kích thước lỗ bánh donut**. Kích thước lỗ là phần trăm của bán kính biểu đồ.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Giá trị này có nghĩa là gì:** Giá trị `30` đồng nghĩa với việc vòng trong sẽ chiếm 30 % bán kính tổng, để lại một vòng ngoài dày hơn.

### Bước 6: Thay Đổi Các Điểm Dữ Liệu Của Biểu Đồ (Tùy Chọn)

Đôi khi bạn cần **thay đổi các điểm dữ liệu của biểu đồ** — có thể bạn đã cập nhật số liệu và muốn biểu đồ phản ánh chúng.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Lý do thực hiện:** Thay đổi giá trị của một data point sẽ tự động tính lại tỷ lệ phần trăm của các miếng, giữ cho biểu đồ luôn chính xác mà không cần chỉnh sửa thủ công trong Word.

### Bước 7: Lưu Tài Liệu Đã Sửa Đổi

Cuối cùng, ghi các thay đổi ra đĩa. Bạn có thể ghi đè lên file gốc hoặc tạo file mới — tùy bạn.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Mẹo:** Dùng `SaveFormat.Docx` nếu muốn chỉ định rõ ràng, nhưng `Save(string)` sẽ tự động nhận dạng định dạng dựa trên phần mở rộng của file.

---

## Kết Quả Mong Đợi

Khi mở `FormattedChart.docx` trong Microsoft Word, bạn sẽ thấy:

- Miếng đầu tiên của biểu đồ pie **bị bẻ tách** ra phía ngoài.
- Nếu là biểu đồ donut, lỗ trung tâm hiện chiếm **30 %** bán kính.
- Các điểm dữ liệu đã thay đổi hiển thị giá trị mới mà bạn đã đặt.

Dưới đây là mô phỏng miếng bánh bẻ tách (hình chỉ mang tính minh hoạ).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Văn bản thay thế:* **miếng bánh pie bị bẻ tách** hiển thị một phần bị kéo ra trong tài liệu Word.

---

## Câu Hỏi Thường Gặp & Các Trường Hợp Cạnh

**Biểu đồ không phải là pie hoặc donut thì sao?**  
Mã sẽ kiểm tra `ChartType` trước khi áp dụng `Exploded` hoặc `HoleSize`. Đối với biểu đồ cột, đường, hoặc diện tích, các thuộc tính này không tồn tại, vì vậy logic sẽ bỏ qua một cách an toàn.

**Có thể bẻ tách nhiều miếng cùng lúc không?**  
Chắc chắn được. Duyệt qua `chart.PieChartData.Series[0].DataPoints` và đặt `Exploded = true` cho bất kỳ chỉ số nào bạn muốn.

**Có cần lo lắng về định dạng số theo văn hoá không?**  
Aspose.Words lưu giá trị số dưới dạng double, không phụ thuộc vào locale, vì vậy bạn không gặp vấn đề dấu phẩy vs dấu chấm.

**Còn biểu đồ nhúng trong header/footer thì sao?**  
Dùng `doc.GetChildNodes(NodeType.Chart, true)` để lấy tất cả biểu đồ, sau đó kiểm tra `ParentNode` của mỗi node để biết vị trí. Logic bẻ tách vẫn áp dụng tương tự.

---

## Kết Luận

Bây giờ bạn đã có một giải pháp sẵn sàng sao chép‑dán để **bẻ tách miếng bánh pie** bằng Aspose.Words trong C#. Chúng tôi đã bao quát toàn bộ quy trình — từ tải tài liệu, lấy biểu đồ, bẻ tách miếng, **điều chỉnh kích thước lỗ donut**, đến **thay đổi các điểm dữ liệu** và cuối cùng lưu file.

Hãy thử nghiệm: bẻ tách một miếng khác, thay đổi kích thước lỗ lên 45 %, hoặc cập nhật đồng thời nhiều điểm dữ liệu. API của Aspose.Words giúp các thao tác này trở nên nhẹ nhàng, và các thay đổi sẽ hiển thị ngay khi bạn mở file Word.

---

### Tiếp Theo Bạn Nên Làm Gì?

- **Định dạng miếng bẻ tách** (thay đổi màu nền, viền, hoặc thêm nhãn dữ liệu). Tìm kiếm “Aspose.Words chart formatting”.
- **Tự động xử lý hàng loạt** nhiều tài liệu — lặp qua thư mục, bẻ tách miếng, và lưu phiên bản mới.
- **Kết hợp với Aspose.Slides** nếu bạn cần cùng biểu đồ trong bản trình bày PowerPoint.

Nếu còn câu hỏi về thao tác biểu đồ, hoặc muốn khám phá sâu hơn các loại biểu đồ khác, hãy để lại bình luận bên dưới. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây liên quan chặt chẽ tới các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}