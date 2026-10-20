---
category: general
date: 2026-10-20
description: Tạo biểu đồ tròn trong tài liệu Word bằng Aspose.Words – hướng dẫn từng
  bước cho thấy cách đặt màu, tách miếng (explode slice) và lưu tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: vi
lastmod: 2026-10-20
og_description: Tạo biểu đồ tròn trong tài liệu Word bằng Aspose.Words. Tìm hiểu cách
  đặt màu, tách miếng và lưu tài liệu Word trong một ví dụ duy nhất, có thể chạy được.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Tạo biểu đồ tròn trong tài liệu Word – hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Cách tạo biểu đồ tròn trong tài liệu Word bằng Aspose.Words
url: /vi/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo biểu đồ tròn trong tài liệu Word bằng Aspose.Words

Nếu bạn cần **tạo biểu đồ tròn** trong một tệp Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chi tiết. Bạn sẽ thấy cách đặt màu tùy chỉnh, làm nổ một lát bánh để nhấn mạnh, và cuối cùng **lưu tài liệu Word** với biểu đồ được nhúng.

Việc tạo biểu đồ bằng mã tự động loại bỏ các bước thủ công như mở Word, chèn biểu đồ và điều chỉnh giao diện. Khi kết thúc tutorial này, bạn sẽ có một ứng dụng console C# hoàn chỉnh, có thể chạy được, tạo biểu đồ tròn, tùy chỉnh nó và ghi kết quả ra đĩa.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Giấy phép Aspose.Words for .NET hợp lệ (hoặc khóa dùng thử miễn phí)  
* Một IDE như Visual Studio 2022 hoặc VS Code  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Cách tạo biểu đồ tròn trong tài liệu Word

Bước đầu tiên là khởi tạo một đối tượng `Document` và một `DocumentBuilder`. Builder cho phép bạn truy cập các tính năng cấp cao của Word, bao gồm chèn biểu đồ.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Tại thời điểm này tài liệu đã chứa một biểu đồ tròn cơ bản. Các phần tiếp theo sẽ giải thích **cách làm nổ lát bánh**, **cách đặt màu**, và **cách lưu tài liệu Word**.

## Cách làm nổ lát bánh để nhấn mạnh

Làm nổ một lát bánh tách nó ra khỏi phần còn lại của biểu đồ, thu hút ánh nhìn của người đọc. API Aspose.Words cho phép bạn chỉ định khoảng cách nổ tính bằng điểm.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Tại sao lại làm nổ lát bánh? Trong các báo cáo làm nổi bật một danh mục cụ thể—ví dụ “Sản phẩm bán chạy nhất”—việc tách trực quan giúp dữ liệu đó ngay lập tức được nhận diện.

## Cách đặt màu cho một lát bánh

Màu tùy chỉnh giúp tăng tính nhất quán thương hiệu và độ dễ đọc. Bạn có thể gán bất kỳ `System.Drawing.Color` nào cho một điểm dữ liệu cụ thể.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Bạn không bị giới hạn ở các màu đã định nghĩa trước; bạn có thể tạo giá trị `Color.FromArgb` cho các sắc thái chính xác.

## Cách lưu tài liệu Word với biểu đồ

Khi biểu đồ đã trông như mong muốn, việc lưu file trở nên đơn giản. Phương thức `Document.Save` ghi tài liệu ở định dạng bạn chỉ định—ở đây chúng ta dùng định dạng mặc định `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Chạy chương trình sẽ tạo ra `PieChart.docx`. Mở file này trong Microsoft Word sẽ hiển thị một biểu đồ tròn trong đó lát bánh đầu tiên đã được nổ và tô màu đỏ, chính xác như mã đã chỉ định.

### Kết quả mong đợi

* Một tệp Word có tên **PieChart.docx** trong `C:\Temp`.  
* Tài liệu chứa một biểu đồ tròn duy nhất, kích thước 400 × 300 điểm.  
* Lát bánh 0 được dịch ra 20 điểm và tô màu đỏ, trong khi các lát bánh còn lại giữ màu mặc định.  

Bạn có thể kiểm tra việc nổ và màu sắc bằng cách chọn biểu đồ trong Word và xem thuộc tính của lát bánh.

## Mẹo chuyên nghiệp và các lỗi thường gặp

* **Mẹo chuyên nghiệp:** Nếu cần thay đổi tiêu đề biểu đồ hoặc chú giải, hãy sử dụng các thuộc tính `pieChart.Title.Text` và `pieChart.Legend` trước khi lưu.  
* **Cảnh báo:** Quên xóa các điểm dữ liệu mặc định có thể dẫn đến các lát bánh thừa, không mong muốn. Luôn gọi `Series[0].DataPoints.Clear()` trước khi thêm dữ liệu của bạn.  
* **Mẹo hiệu năng:** Đối với tài liệu lớn, tái sử dụng một thể hiện `DocumentBuilder` duy nhất thay vì tạo nhiều builder; cách này giảm tải bộ nhớ.

## Cách tạo biểu đồ bằng Aspose.Words (ngữ cảnh bổ sung)

Phương thức `InsertChart` hỗ trợ nhiều loại biểu đồ ngoài biểu đồ tròn, chẳng hạn như cột, đường và khu vực. Để chuyển sang loại khác, thay thế `ChartType.Pie` bằng giá trị enum mong muốn, ví dụ `ChartType.Column`. Các bước tùy chỉnh còn lại (nổ lát bánh, đặt màu) vẫn áp dụng tương tự, mặc dù không phải tất cả các loại biểu đồ đều có thuộc tính “explosion”.

## Cách làm nổ lát bánh trong các loại biểu đồ khác

Chỉ các biểu đồ dạng tròn mới có phương thức `SetExplosion`. Nếu bạn gọi nó trên biểu đồ cột, API sẽ ném ra một `ArgumentException`. Trong những trường hợp đó, hãy cân nhắc sử dụng nhãn dữ liệu hoặc callout để làm nổi bật một cột cụ thể.

## Cách đặt màu cho toàn bộ series thay vì một lát bánh riêng lẻ

Nếu bạn muốn mọi lát bánh trong một series cùng màu, hãy lặp qua các điểm dữ liệu:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Cách này hữu ích khi bạn cần một bảng màu đồng nhất cho nhiều biểu đồ.

## Cách lưu tài liệu Word ở các định dạng khác

Aspose.Words có thể xuất ra PDF, HTML và nhiều định dạng khác. Thay đổi phần mở rộng tệp trong `Save` và tùy chọn truyền một đối tượng `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Engine render biểu đồ sẽ tự động chuyển đổi biểu đồ sang định dạng đích, giữ nguyên màu sắc và thiết lập nổ.

## Kết luận

Bây giờ bạn đã biết cách **tạo biểu đồ tròn** trong tài liệu Word, tùy chỉnh giao diện bằng **việc nổ một lát bánh** và **đặt màu**, và cuối cùng **lưu tài liệu Word** với biểu đồ được nhúng. Ví dụ toàn diện này cung cấp nền tảng vững chắc để tự động hoá việc tạo báo cáo, dashboard, hoặc bất kỳ kịch bản nào cần chèn dữ liệu trực quan bằng mã.

### Các bước tiếp theo

* Khám phá các loại biểu đồ khác (`ChartType.Column`, `ChartType.Line`) để mở rộng bộ công cụ báo cáo của bạn.  
* Kết hợp nhiều biểu đồ trong một tài liệu để xây dựng dashboard toàn diện.  
* Thử nghiệm với `ChartDataLabel` để hiển thị phần trăm hoặc giá trị trực tiếp trên các lát bánh.  

Hãy tự do điều chỉnh mã cho nguồn dữ liệu của riêng bạn—cho dù bạn lấy giá trị từ cơ sở dữ liệu, API, hay tệp CSV, quy trình làm việc Aspose.Words vẫn áp dụng. Chúc bạn vẽ biểu đồ thành công!

### Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}