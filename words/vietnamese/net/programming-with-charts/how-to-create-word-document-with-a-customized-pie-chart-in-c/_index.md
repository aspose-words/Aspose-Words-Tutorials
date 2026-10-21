---
category: general
date: 2026-10-07
description: Tìm hiểu cách tạo tài liệu Word và chèn biểu đồ tròn bằng Aspose.Words
  trong C#. Hướng dẫn cũng chỉ cách tạo file Word với nhãn biểu đồ tùy chỉnh.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: vi
lastmod: 2026-10-07
og_description: Tạo tài liệu Word và chèn biểu đồ tròn trong C#. Hãy làm theo hướng
  dẫn từng bước này để tạo tệp Word với nhãn biểu đồ được tùy chỉnh hoàn toàn.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Tạo tài liệu Word với biểu đồ tròn tùy chỉnh trong C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Cách tạo tài liệu Word có biểu đồ tròn tùy chỉnh trong C#
url: /vi/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word với biểu đồ tròn tùy chỉnh trong C#

Nếu bạn cần **tạo tài liệu word** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách **chèn biểu đồ tròn** và tùy chỉnh nhãn dữ liệu của nó bằng Aspose.Words for .NET. Bạn cũng sẽ học cách **tạo file word** chứa một biểu đồ được định dạng đầy đủ, bao gồm mọi thứ từ thiết lập dự án đến lưu tài liệu cuối cùng.

Hướng dẫn sẽ đi qua từng bước cần thiết để thêm biểu đồ, điều chỉnh vị trí nhãn, bật đường dẫn (leader lines), và cuối cùng lưu kết quả dưới dạng tệp `.docx`. Không cần công cụ bên ngoài nào ngoài thư viện Aspose.Words, và mã nguồn đầy đủ được cung cấp để bạn có thể sao chép, dán và chạy ngay lập tức.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 SDK hoặc phiên bản mới hơn được cài đặt  
* Giấy phép hợp lệ của Aspose.Words for .NET (hoặc khóa dùng thử miễn phí)  
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code  

Bạn cũng cần thêm các gói NuGet sau vào dự án của mình:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Các gói này cung cấp các lớp `Document`, `DocumentBuilder` và các lớp liên quan đến biểu đồ được sử dụng trong các ví dụ dưới đây.

## Tạo tài liệu word và thêm biểu đồ

Bước đầu tiên là **tạo tài liệu word** và lấy một `DocumentBuilder` cho phép bạn chèn nội dung. Builder hoạt động như một con trỏ được đặt bên trong tài liệu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Đối tượng `Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cung cấp các phương thức như `InsertChart` để đặt các đối tượng trực tiếp vào luồng tài liệu.

## Chèn biểu đồ tròn vào tài liệu

Khi builder đã sẵn sàng, bạn có thể **chèn biểu đồ tròn** với kích thước cụ thể. Biểu đồ sẽ được thêm vào vị trí hiện tại của builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` trả về một đối tượng `Chart` mà bạn có thể thao tác thêm. Dữ liệu mẫu tạo ra bốn phần biểu thị doanh thu quý.

## Tùy chỉnh nhãn dữ liệu của biểu đồ tròn

Để biểu đồ dễ đọc hơn, bạn thường cần **tùy chỉnh nhãn biểu đồ tròn** — đặt chúng ở ngoài các phần và hiển thị đường dẫn (leader lines). Đây là nơi `ChartDataLabelCollection` phát huy vai trò.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Đặt `Position` thành `OutsideEnd` sẽ di chuyển mỗi nhãn ra ngoài mép của phần, trong khi `ShowLeaderLines` vẽ một đường nối nhãn với phần tương ứng. Các cờ tùy chọn `ShowValue` và `ShowPercentage` cung cấp cho người đọc cả số nguyên và phần trăm tương đối.

**Mẹo:** Nếu bạn cần định dạng phông chữ của nhãn, hãy sử dụng `dataLabels.Font` để đặt kích thước, màu sắc và kiểu. Điều này đảm bảo biểu đồ phù hợp với bộ nhận diện thương hiệu của công ty.

## Lưu và tạo file word

Sau khi biểu đồ đã được cấu hình đầy đủ, bạn có thể **tạo file word** bằng cách lưu thể hiện `Document` ra đĩa. Chọn định dạng `.docx` để đạt độ tương thích tối đa với các phiên bản Word hiện đại.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Khi mở `CustomPieChart.docx`, bạn sẽ thấy một biểu đồ tròn với bốn phần, mỗi phần có nhãn ở ngoài, được nối bằng đường dẫn, và hiển thị cả giá trị và phần trăm.

![Screenshot of a Word document that contains a customized pie chart created with C#](image-placeholder.png)

*Hình ảnh hiển thị kết quả cuối cùng của hướng dẫn **tạo tài liệu word**.*

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Cách điều chỉnh mã |
|----------|----------------------|
| **Nhiều series** | Thêm các đối tượng `ChartSeries` bổ sung vào `pieChart.Series`. Mỗi series có thể có bộ `DataLabels` riêng để định dạng độc lập. |
| **Kích thước biểu đồ khác** | Thay đổi các tham số chiều rộng và chiều cao trong `InsertChart(width, height)`. Giá trị tính bằng điểm (1 pt ≈ 1/72 in). |
| **Tiêu đề biểu đồ** | Sử dụng `pieChart.Title.Text = "Quarterly Sales"` để thêm tiêu đề mô tả. |
| **Xuất ra PDF** | Gọi `document.Save("Report.pdf", SaveFormat.Pdf);` sau khi biểu đồ đã được tạo. |
| **Xử lý giấy phép** | Đặt tệp giấy phép của bạn (`Aspose.Words.lic`) vào thư mục ứng dụng và tải nó bằng `new License().SetLicense("Aspose.Words.lic");` trước khi tạo tài liệu. |

Các biến thể này cho phép bạn trả lời câu hỏi **cách thêm biểu đồ tròn** trong nhiều tình huống thực tế, từ báo cáo đơn giản đến bảng điều khiển phức tạp.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu word**, **chèn biểu đồ tròn**, và **tùy chỉnh nhãn biểu đồ tròn** bằng Aspose.Words for .NET. Ví dụ đầy đủ minh họa một quy trình làm việc sạch sẽ: khởi tạo tài liệu, thêm biểu đồ, điều chỉnh vị trí nhãn dữ liệu, bật đường dẫn, và cuối cùng **tạo file word** có thể chia sẻ với bất kỳ ai.

Hãy thử mở rộng hướng dẫn này bằng cách thử các loại biểu đồ khác (`ChartType.Column`, `ChartType.Line`) hoặc áp dụng bảng màu tùy chỉnh để phù hợp với thương hiệu của bạn. Nếu gặp vấn đề, hãy tham khảo tài liệu Aspose.Words hoặc khám phá các chủ đề liên quan như “cách thêm biểu đồ tròn” với nhiều series và nguồn dữ liệu động.

Chúc bạn lập trình vui vẻ, và đừng ngại chia sẻ kết quả hoặc đặt câu hỏi tiếp theo trong phần bình luận!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}