---
category: general
date: 2026-06-02
description: Hiển thị chú giải biểu đồ trong tài liệu Word bằng C#. Tìm hiểu cách
  thêm chú giải, áp dụng kiểu biểu đồ có sẵn và tùy chỉnh hình ảnh biểu đồ Word trong
  vài phút.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: vi
og_description: Hiển thị chú giải biểu đồ trong tài liệu Word ngay lập tức. Hướng
  dẫn này sẽ chỉ cho bạn cách thêm chú giải, áp dụng kiểu biểu đồ đã định sẵn và xử
  lý các trường hợp đặc biệt.
og_title: Hiển thị chú giải biểu đồ trong Word – Hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Hiển thị chú giải biểu đồ trong Word bằng C# – Hướng dẫn chi tiết từng bước
url: /vi/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hiển Thị Chú Giải Biểu Đồ trong Word bằng C# – Hướng Dẫn Chi Tiết Từng Bước

Bạn đã bao giờ tự hỏi **cách thêm chú giải** vào một biểu đồ nằm trong tài liệu Word chưa? Bạn không phải là người duy nhất. Trong nhiều báo cáo, việc thiếu chú giải khiến dữ liệu trông khó hiểu, và việc khắc phục không nên là một cơn đau đầu.  

Trong hướng dẫn này, chúng ta sẽ **hiển thị chú giải biểu đồ** trong một tệp Word bằng Aspose.Words cho .NET, áp dụng một kiểu biểu đồ có sẵn, và đảm bảo chú giải xuất hiện đúng vị trí bạn cần. Khi kết thúc, bạn sẽ có một mẫu sẵn sàng chạy mà bạn có thể đưa vào bất kỳ dự án C# nào.

## Những Nội Dung Hướng Dẫn Bao Gồm

Chúng ta sẽ đi qua toàn bộ quy trình:

1. Tải một tệp *.docx* hiện có đã chứa một biểu đồ.  
2. Lấy biểu đồ đầu tiên (hoặc bất kỳ biểu đồ nào bạn muốn).  
3. **Áp dụng kiểu biểu đồ có sẵn** để tạo nên một giao diện chuyên nghiệp.  
4. **Hiển thị chú giải biểu đồ**, đặt nó ở phía bên phải, và xử lý các trường hợp đặc biệt như biểu đồ Waterfall.  
5. Lưu tài liệu đã được chỉnh sửa.

Không cần công cụ bên ngoài, không cần can thiệp thủ công vào giao diện—chỉ cần code. Điều kiện duy nhất là có tham chiếu tới gói NuGet Aspose.Words (phiên bản 23.10 trở lên) và hiểu cơ bản về C#.

---

## Yêu Cầu Trước

- .NET 6.0 hoặc mới hơn (mẫu này cũng hoạt động với .NET Framework 4.7.2).  
- Thư viện Aspose.Words cho .NET đã được cài đặt (`Install-Package Aspose.Words`).  
- Một tệp Word (`input.docx`) đã chứa ít nhất một biểu đồ.  
- Visual Studio, Rider, hoặc bất kỳ IDE nào bạn thích.

---

## Bước 1: Thiết Lập Dự Án và Tải Tài Liệu

Đầu tiên, tạo một ứng dụng console (hoặc tích hợp mã vào dự án hiện có). Thêm các chỉ thị `using` và tải tệp `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Tại sao lại quan trọng:** Việc tải tài liệu là nền tảng. Nếu không có một thể hiện `Document`, bạn không thể truy cập các đối tượng biểu đồ mà Aspose.Words cung cấp.

---

## Bước 2: Lấy Biểu Đồ Mục Tiêu

Biểu đồ được lưu dưới dạng các nút trong cây tài liệu. Phương thức `GetChild` thực hiện tìm kiếm sâu, cho phép chúng ta lấy biểu đồ đầu tiên bất kể nó nằm ở đâu (đầu trang, nội dung, chân trang, v.v.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Mẹo:** Nếu bạn có nhiều biểu đồ, thay đổi chỉ số `0` thành `1`, `2`, … hoặc lặp qua `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Bước 3: Áp Dụng Kiểu Hình Ảnh Có Sẵn

Một biểu đồ đẹp mắt thường bắt đầu với một kiểu. Aspose.Words cung cấp hàng chục kiểu dựng sẵn; `ChartStyle.Style12` là một lựa chọn sạch sẽ, hiện đại.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Cách hoạt động:** Thuộc tính `Style` ánh xạ tới các kiểu biểu đồ Word có sẵn mà bạn thấy trong giao diện người dùng. Chọn một kiểu dựng sẵn giúp bạn không phải tự tay thiết lập màu sắc, phông chữ và ký hiệu.

---

## Bước 4: Bật Chú Giải và Đặt Vị Trí

Bây giờ là phần trọng tâm—**hiển thị chú giải biểu đồ**. Chúng ta bật chú giải, sau đó gắn nó vào phía bên phải của biểu đồ.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Tại sao lại đặt bên phải?** Đặt chú giải ở bên phải giữ cho khu vực dữ liệu rộng rãi, điều này đặc biệt hữu ích cho các biểu đồ cột hoặc thanh.

---

## Bước 5: Xử Lý Biểu Đồ Waterfall (Trường Hợp Đặc Biệt)

Biểu đồ Waterfall hoạt động hơi khác; chú giải có thể bị ẩn mặc định. Đoạn mã kiểm tra sau sẽ đảm bảo chú giải hiển thị khi loại biểu đồ là Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Lưu ý trường hợp biên:** Một số phiên bản Word cũ bỏ qua `HasLegend` đối với biểu đồ Waterfall, vì vậy việc đặt `Legend.Show` một cách rõ ràng sẽ đảm bảo hiển thị.

---

## Bước 6: Lưu Tài Liệu Đã Sửa Đổi

Cuối cùng, ghi các thay đổi trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo một tệp mới.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Chạy chương trình sẽ tạo ra `output.docx` với chú giải hiển thị ở phía bên phải, được định dạng bằng `Style12`. Mở tệp trong Word để kiểm tra kết quả.

---

## Ví Dụ Hoàn Chỉnh (Tất Cả Các Bước Kết Hợp)

Dưới đây là đoạn mã hoàn chỉnh, sẵn sàng chạy. Sao chép‑dán vào `Program.cs` (hoặc bất kỳ tệp C# nào) và điều chỉnh đường dẫn tệp.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Kết quả mong đợi:** Mở `output.docx` sẽ hiển thị biểu đồ gốc với chú giải căn bên phải, được định dạng bằng `Style12`. Tất cả các chuỗi dữ liệu đều được gắn nhãn rõ ràng, giúp biểu đồ ngay lập tức trở nên dễ hiểu.

---

## Các Câu Hỏi Thường Gặp (FAQ)

### Làm sao để thêm chú giải cho một biểu đồ cụ thể (không phải biểu đồ đầu tiên)?

Thay đổi chỉ số `0` trong `GetChild(NodeType.Chart, 0, true)` thành vị trí zero‑based của biểu đồ mục tiêu, hoặc lặp qua tất cả các nút biểu đồ:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Có thể đặt chú giải ở dưới thay vì bên phải không?

Chắc chắn rồi. Chỉ cần thay đổi enum `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Nếu biểu đồ đã có chú giải nhưng tôi muốn ẩn nó thì sao?

Đặt `HasLegend` thành `false`:

```csharp
chart.HasLegend = false;
```

### Điều này có hoạt động với Word 2010, 2016 và các phiên bản sau không?

Có. Aspose.Words trừu tượng hoá phiên bản Word nền tảng, vì vậy cùng một đoạn mã hoạt động trên mọi tệp .docx hiện đại.

---

## Mẹo Chuyên Gia & Những Sai Lầm Thường Gặp

- **Mẹo chuyên gia:** Sau khi áp dụng một kiểu, bạn vẫn có thể tinh chỉnh các thành phần riêng lẻ (màu sắc, nhãn dữ liệu) qua bộ sưu tập `Chart.Series`. Kiểu cung cấp một nền tảng vững chắc.  
- **Cẩn thận:** Nếu biểu đồ nằm trong một ô bảng, chú giải có thể bị chèn chặt. Hãy cân nhắc tăng kích thước biểu đồ (`chart.Width`, `chart.Height`) trước khi đặt chú giải.  
- **Lưu ý hiệu năng:** Tải tài liệu lớn (hàng trăm MB) có thể tốn nhiều bộ nhớ. Sử dụng `LoadOptions` với `LoadFormat.Docx` để giảm tải nếu bạn chỉ cần thao tác với biểu đồ.

---

## Bước Tiếp Theo

Bây giờ bạn đã biết **cách thêm chú giải** và **cách áp dụng kiểu biểu đồ có sẵn** trong Word, bạn có thể khám phá:

- **Màu biểu đồ tùy chỉnh** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Định dạng nhãn dữ liệu** (`chart.Series[i].HasDataLabel = true`).  
- **Xuất biểu đồ dưới dạng hình ảnh** (`chart.ToImage()`), hữu ích cho việc nhúng vào nơi khác.  

Mỗi chủ đề này đều dựa trên cùng một mô hình đối tượng, vì vậy đường cong học tập sẽ nhẹ nhàng.

---

## Kết Luận

Chúng ta vừa trình bày một giải pháp sạch sẽ, từ đầu đến cuối để **hiển thị chú giải biểu đồ** trong tài liệu Word bằng C#. Bằng cách tải tài liệu, lấy biểu đồ, áp dụng kiểu có sẵn, bật chú giải và xử lý các đặc thù của Waterfall, bạn sẽ có một biểu đồ được hoàn thiện, sẵn sàng cho bất kỳ báo cáo kinh doanh nào.  

Hãy tự do thử nghiệm các giá trị `ChartStyle` khác hoặc vị trí chú giải—các biểu đồ của bạn xứng đáng được trình bày tốt nhất. Nếu gặp bất kỳ khó khăn nào, hãy để lại bình luận bên dưới; chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}