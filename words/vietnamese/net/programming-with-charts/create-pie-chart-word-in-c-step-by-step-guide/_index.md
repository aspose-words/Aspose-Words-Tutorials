---
category: general
date: 2026-08-07
description: Tạo biểu đồ tròn trong Word bằng C# nhanh chóng. Học cách chèn biểu đồ
  tròn, thêm nhãn dữ liệu cho biểu đồ tròn, hiển thị phần trăm, và tùy chỉnh nhãn
  dữ liệu của biểu đồ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: vi
lastmod: 2026-08-07
og_description: Tạo biểu đồ tròn trong Word bằng C# với Aspose.Words. Hướng dẫn này
  cho thấy cách chèn biểu đồ tròn, thêm nhãn dữ liệu cho biểu đồ tròn và hiển thị
  phần trăm trên biểu đồ đồng thời tùy chỉnh nhãn dữ liệu của biểu đồ.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Tạo biểu đồ tròn word trong C# – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Tạo biểu đồ tròn trong C# – hướng dẫn từng bước
url: /vi/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo biểu đồ tròn trong Word bằng C# – hướng dẫn chi tiết

Nếu bạn cần **tạo biểu đồ tròn trong Word** bằng C#, hướng dẫn này cung cấp giải pháp hoàn chỉnh, có thể chạy ngay. Bạn sẽ thấy cách **chèn biểu đồ tròn**, **thêm nhãn dữ liệu cho biểu đồ tròn**, và **hiển thị biểu đồ phần trăm** đồng thời **tùy chỉnh nhãn dữ liệu biểu đồ** để có giao diện chuyên nghiệp.

Việc tạo biểu đồ bằng mã giúp bạn tránh việc chỉnh sửa thủ công, đặc biệt khi các báo cáo hoặc bảng điều khiển phải được tạo tự động. Trong các phần dưới đây, bạn sẽ học mọi thứ cần thiết để nhúng một biểu đồ tròn có đầy đủ nhãn vào tệp Word bằng Aspose.Words for .NET.

## Yêu cầu trước và cài đặt

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt.  
* Giấy phép hợp lệ của Aspose.Words for .NET (hoặc khóa đánh giá tạm thời).  
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#).  

Thêm gói NuGet Aspose.Words vào dự án của bạn:

```bash
dotnet add package Aspose.Words
```

> **Mẹo:** Nếu bạn dự định tạo nhiều biểu đồ, hãy bật chế độ **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) để cải thiện hiệu năng.

## Tạo biểu đồ tròn trong Word với Aspose.Words

Bước quan trọng đầu tiên là tạo một tài liệu Word trống và một `DocumentBuilder`. Đối tượng này sẽ điều khiển mọi thao tác chèn tiếp theo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Lý do quan trọng*: `Document` đại diện cho toàn bộ tệp `.docx`, trong khi `DocumentBuilder` cung cấp API dạng fluent để thêm đoạn văn, bảng và biểu đồ. Bắt đầu với tài liệu sạch sẽ giúp tránh các định dạng ẩn can thiệp vào bố cục biểu đồ.

## Chèn biểu đồ tròn vào tài liệu

Bây giờ chúng ta đặt một biểu đồ tròn với kích thước mong muốn. Phương thức `InsertChart` trả về một đối tượng `Chart` mà chúng ta có thể cấu hình thêm.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Lý do quan trọng*: Cờ `ChartType.Pie` báo cho Aspose.Words tạo một biểu đồ dạng vòng tròn. Độ rộng (`400`) và chiều cao (`300`) được tính bằng điểm, cho phép bạn kiểm soát chính xác diện tích hiển thị.

## Điền dữ liệu vào biểu đồ

Biểu đồ tròn cần ít nhất một chuỗi giá trị số. Ở đây chúng ta thêm ba danh mục: “Apples”, “Bananas”, và “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Lý do quan trọng*: Mỗi lời gọi `AddCategory` tạo một lát bánh. Giá trị số quyết định kích thước lát, trong khi nhãn sẽ là tên danh mục hiển thị khi bật nhãn dữ liệu.

## Thêm nhãn dữ liệu cho biểu đồ tròn và hiển thị phần trăm

Để biểu đồ có thông tin, chúng ta bật nhãn dữ liệu, đặt chúng ở ngoài các lát và yêu cầu Aspose.Words hiển thị cả tên danh mục và phần trăm.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Lý do quan trọng*: Đặt `Position` thành `OutsideEnd` cải thiện khả năng đọc, đặc biệt khi các lát nhỏ. Bật `ShowCategoryName` và `ShowPercentage` đáp ứng yêu cầu **hiển thị biểu đồ phần trăm** và mục tiêu **thêm nhãn dữ liệu cho biểu đồ tròn**.

## Tùy chỉnh nhãn dữ liệu biểu đồ thêm (tùy chọn)

Bạn có thể muốn thay đổi phông chữ, thêm đường dẫn (leader line), hoặc ẩn chú giải. Đoạn mã dưới đây minh họa các tùy chỉnh phổ biến:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Lý do quan trọng*: Tùy chỉnh giao diện nhãn giúp biểu đồ phù hợp với quy tắc phong cách của tài liệu. Loại bỏ chú giải giảm bớt sự lộn xộn khi nhãn dữ liệu đã truyền đạt cùng một thông tin.

## Lưu tài liệu với biểu đồ đã tùy chỉnh

Cuối cùng, ghi tài liệu ra đĩa. Chọn một đường dẫn mà bạn có quyền ghi.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Khi mở `ChartWithCustomLabels.docx` trong Microsoft Word, bạn sẽ thấy một biểu đồ tròn mà mỗi lát được gắn nhãn tên danh mục và phần trăm, đặt ở ngoài lát, và được định dạng theo cài đặt phông chữ tùy chỉnh.

### Kết quả mong đợi

| Lát      | Giá trị | Phần trăm | Nhãn hiển thị trong Word |
|----------|---------|-----------|---------------------------|
| Apples   | 40      | 40 %      | Apples – 40 %             |
| Bananas  | 35      | 35 %      | Bananas – 35 %            |
| Cherries | 25      | 25 %      | Cherries – 25 %           |

Biểu đồ sẽ trông tương tự như hình minh họa dưới đây:

![Tài liệu Word hiển thị biểu đồ tròn (pie chart) với nhãn phần trăm ở ngoài mỗi lát](pie-chart-word.png "Create pie chart word example")

*Văn bản thay thế ảnh bao gồm từ khóa chính cho SEO.*

## Xử lý nhiều chuỗi và các trường hợp đặc biệt

Ví dụ cơ bản sử dụng một chuỗi duy nhất, điều này là tiêu chuẩn cho biểu đồ tròn. Nếu bạn cần hiển thị nhiều chuỗi (ví dụ: so sánh hai năm), bạn phải:

1. Gọi `chart.Series.Add()` cho mỗi chuỗi bổ sung.  
2. Đảm bảo mỗi chuỗi sử dụng cùng một danh mục; nếu không, Aspose.Words sẽ ném `ArgumentException`.  
3. Tùy chọn, đặt `labels.ShowSeriesName = true` để phân biệt các lát.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Khi có nhiều chuỗi, biểu đồ tự động hiển thị dưới dạng **pie chart nhóm** (còn gọi là “pie of pies”). Kiểm tra kết quả để xác nhận các nhãn vẫn dễ đọc.

## Những lỗi thường gặp và cách tránh

| Vấn đề                         | Nguyên nhân                                 | Giải pháp |
|--------------------------------|---------------------------------------------|-----------|
| Nhãn chồng lên nhau            | Khu vực biểu đồ quá nhỏ hoặc quá nhiều danh mục | Tăng kích thước biểu đồ (`InsertChart(width, height)`) hoặc chuyển `Position` sang `InsideEnd`. |
| Phần trăm không cộng lại 100 % | Lỗi làm tròn dữ liệu                         | Sử dụng `labels.ShowPercentage = true` (Aspose.Words tự động chuẩn hoá). |
| Biểu đồ hiển thị trống trong Word | Thiếu giấy phép hoặc thời gian dùng thử hết | Đảm bảo tải giấy phép Aspose.Words hợp lệ trước khi tạo tài liệu. |
| Màu phông chữ khác chủ đề Word | Đặt phông chữ tùy chỉnh trong mã             | Xóa cài đặt phông chữ tùy chỉnh hoặc khớp màu chủ đề Word (`System.Drawing.Color.Black`). |

## Toàn bộ mã nguồn (có thể chạy)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Chạy chương trình sẽ tạo ra `ChartWithCustomLabels.docx`, chứa một ví dụ **tạo biểu đồ tròn trong Word** đáp ứng tất cả các yêu cầu được liệt kê trong hướng dẫn.

## Kết luận

Bây giờ bạn đã biết cách **tạo biểu đồ tròn trong Word** bằng C# sử dụng Aspose.Words. Hướng dẫn đã bao gồm việc chèn biểu đồ tròn, **thêm nhãn dữ liệu cho biểu đồ tròn**, **hiển thị biểu đồ phần trăm**, và **tùy chỉnh nhãn dữ liệu biểu đồ** để có một tệp Word chuyên nghiệp, dựa trên dữ liệu.

Từ đây, bạn có thể khám phá các chủ đề liên quan như **chèn biểu đồ tròn** vào các đoạn văn hiện có, tạo biểu đồ **cột** hoặc **đường**, hoặc tự động hoá việc tạo hàng loạt báo cáo với các bộ dữ liệu khác nhau. Thử nghiệm với các vị trí nhãn khác nhau, kiểu phông chữ, và cấu hình đa chuỗi để điều chỉnh đầu ra phù hợp với nhu cầu báo cáo cụ thể của bạn.

Chúc bạn vẽ biểu đồ thành công!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}