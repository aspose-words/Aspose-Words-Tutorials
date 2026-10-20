---
category: general
date: 2026-09-21
description: Cách định dạng chuỗi trong biểu đồ đường Word bằng C#. Tìm hiểu cách
  tạo tài liệu Word, chèn biểu đồ đường và áp dụng định dạng số tùy chỉnh.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: vi
lastmod: 2026-09-21
og_description: Cách định dạng chuỗi trong biểu đồ đường của Word bằng C#. Hướng dẫn
  này chỉ cho bạn cách tạo tài liệu Word, chèn biểu đồ đường và áp dụng định dạng
  số tùy chỉnh.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Cách định dạng chuỗi trong biểu đồ đường Word bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Cách định dạng chuỗi trong biểu đồ đường Word bằng C#
url: /vi/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách định dạng series trong biểu đồ đường của Word bằng C#

Nếu bạn cần **cách định dạng series** trong biểu đồ đường của Word, hướng dẫn này cung cấp cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ thấy cách **tạo tài liệu Word**, **chèn biểu đồ đường**, và **áp dụng định dạng số tùy chỉnh** cho các giá trị Y — tất cả đều sử dụng Aspose.Words for .NET.

Tự động hoá Word trở nên đơn giản khi bạn hiểu mô hình đối tượng biểu đồ. Khi kết thúc tutorial này, bạn sẽ có một tệp Word chứa biểu đồ đường mà các series dữ liệu được hiển thị dưới dạng phần trăm với hai chữ số thập phân.

## Những gì bạn sẽ đạt được

* Tạo một tệp `.docx` trống bằng mã.  
* Thêm một biểu đồ đường có kích thước 400 × 300 điểm.  
* Truy cập series dữ liệu đầu tiên của biểu đồ.  
* Áp dụng mã định dạng `#,##0.00%` để các giá trị Y hiển thị dưới dạng phần trăm.  

Không cần công cụ bên ngoài nào ngoài gói NuGet Aspose.Words.

## Yêu cầu trước

* .NET 6.0 SDK trở lên.  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào).  
* Aspose.Words for .NET 23.10 hoặc mới hơn – cài đặt qua `dotnet add package Aspose.Words`.  

Mã chạy trên Windows, Linux và macOS vì Aspose.Words không phụ thuộc vào nền tảng.

## Tạo tài liệu Word với Aspose.Words

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp Word trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Lý do quan trọng*: `Document` là điểm vào cho mọi thao tác xử lý Word. Không có nó, bạn không thể thêm đoạn văn, bảng hay biểu đồ.

## Chèn biểu đồ đường vào tài liệu

`DocumentBuilder` ghi nội dung vào `Document`. Gọi `InsertChart` sẽ tạo một hình dạng biểu đồ trên trang hiện tại.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Lý do quan trọng*: `InsertChart` trả về một đối tượng `Chart` cho phép bạn kiểm soát toàn bộ series, trục và định dạng. Các tham số kích thước được tính bằng điểm (1 điểm = 1/72 inch).

## Truy cập series dữ liệu đầu tiên

Mỗi biểu đồ chứa một hoặc nhiều `ChartSeries`. Series đầu tiên có chỉ số 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Lý do quan trọng*: Đối tượng `ChartSeries` chứa các giá trị Y, X và các tùy chọn định dạng cho một đường trong biểu đồ đường. Thay đổi đối tượng này sẽ thay đổi cách dữ liệu được hiển thị.

## Áp dụng định dạng số tùy chỉnh cho series

Thuộc tính `FormatCode` điều khiển cách hiển thị các giá trị số. Đặt nó thành `#,##0.00%` sẽ khiến Word coi các giá trị là phần trăm với hai chữ số thập phân.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Lý do quan trọng*: Nếu không có định dạng tùy chỉnh, Word sẽ hiển thị số thập phân thô (ví dụ, `0.15`). Mã định dạng sẽ chuyển chúng thành `15.00%`, thường là yêu cầu của các báo cáo kinh doanh.

## Lưu tài liệu và kiểm tra kết quả

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Khi bạn mở `FormattedSeriesLineChart.docx` trong Microsoft Word, sẽ thấy một biểu đồ đường mà các nhãn trục Y hiển thị `15.00%`, `30.00%`, `45.00%`, và `60.00%`. Kích thước biểu đồ khớp với các thông số đã truyền vào `InsertChart`.

### Ảnh chụp màn hình kết quả mong đợi

> *Hình ảnh: Một trang tài liệu Word hiển thị biểu đồ đường với các giá trị trục Y được định dạng dưới dạng phần trăm.*  
> *(Văn bản thay thế: Ảnh chụp màn hình tài liệu Word hiển thị biểu đồ đường với các giá trị trục Y được định dạng dưới dạng phần trăm)*

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Điều chỉnh |
|-----------|------------|
| **Nhiều series** | Duyệt qua `chart.Series` và đặt `FormatCode` cho mỗi series. |
| **Loại biểu đồ khác** | Thay `ChartType.Line` bằng `ChartType.Column`, `ChartType.Pie`, v.v. |
| **Dấu phân cách theo locale** | Sử dụng chuỗi định dạng có hỗ trợ `CultureInfo`, ví dụ `"# ##0,00 %"` cho ngôn ngữ Pháp. |
| **Nguồn dữ liệu động** | Điền `series.YValues` từ cơ sở dữ liệu hoặc tệp CSV trước khi áp dụng định dạng. |

**Mẹo chuyên nghiệp:** Luôn áp dụng định dạng **sau** khi bạn đã thêm các giá trị Y. Việc thay đổi định dạng trước rồi mới thêm giá trị cũng được, nhưng áp dụng sau sẽ đảm bảo định dạng được áp dụng cho tập dữ liệu cuối cùng.

## Tóm tắt

Bạn đã biết **cách định dạng series** trong biểu đồ đường của Word bằng C#. Tutorial đã bao gồm:

* Tạo tài liệu Word (`create word document`).  
* Chèn biểu đồ đường (`insert line chart`, `add chart to word`).  
* Truy cập series đầu tiên của biểu đồ.  
* Áp dụng định dạng số tùy chỉnh (`apply custom number format`) để hiển thị phần trăm.

## Bước tiếp theo

* Thử nghiệm các giá trị `ChartType` khác để xem các dạng biểu đồ khác hoạt động như thế nào.  
* Thêm tiêu đề, nhãn trục và chú giải bằng `chart.Title`, `chart.AxisX.Title`, và `chart.AxisY.Title`.  
* Xuất biểu đồ dưới dạng hình ảnh (`chart.Save` với `SaveFormat.Png`) để sử dụng trong báo cáo web.

Hãy tự do điều chỉnh mẫu này để tạo dashboard, báo cáo tài chính, hoặc bất kỳ tài liệu nào cần vẽ biểu đồ tự động. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}