---
category: general
date: 2026-10-13
description: Tìm hiểu cách điều chỉnh nhãn biểu đồ trong tài liệu Word một cách lập
  trình bằng C#. Hướng dẫn này bao gồm việc thao tác biểu đồ với Aspose.Words và căn
  chỉnh nhãn.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: vi
lastmod: 2026-10-13
og_description: Điều chỉnh nhãn biểu đồ trong tài liệu Word bằng C# một cách lập trình.
  Theo dõi hướng dẫn chi tiết này để thay đổi vị trí nhãn, căn chỉnh và nhiều hơn
  nữa.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Điều chỉnh nhãn biểu đồ trong Word bằng lập trình – Hướng dẫn từng bước
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Điều chỉnh nhãn biểu đồ trong tài liệu Word bằng C# một cách lập trình
url: /vi/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Điều chỉnh nhãn biểu đồ một cách lập trình trong tài liệu Word bằng C#

Nếu bạn cần **điều chỉnh nhãn biểu đồ một cách lập trình** trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng C#. Dù bạn đang tạo báo cáo, tự động hoá bảng điều khiển, hay tùy chỉnh mẫu, bạn sẽ thấy một ví dụ đầy đủ, có thể chạy được, thay đổi vị trí và căn chỉnh nhãn của biểu đồ trong tệp .docx.

Bạn cũng sẽ học cách sử dụng các kỹ thuật **Aspose.Words chart manipulation**, xử lý nhiều series, và tránh các lỗi phổ biến khi làm việc với các đối tượng **C# chart data label**.

## Yêu cầu trước

* .NET 6.0 (hoặc phiên bản mới hơn) đã được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  
* Gói NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Một tài liệu Word (`input.docx`) chứa ít nhất một biểu đồ  

Các mục này là cần thiết cho **Word document chart example** mà chúng ta sẽ chỉnh sửa.

## Bước 1: Thiết lập dự án và nhập các namespace

Tạo một dự án console mới và thêm các chỉ thị `using` cần thiết. Điều này chuẩn bị môi trường cho **programmatically adjust chart labels**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Tại sao bước này?*  
Việc tải tài liệu cho phép bạn truy cập vào cây nội bộ **Word document chart example**, nơi các biểu đồ được lưu dưới dạng các nút shape.

## Bước 2: Xác định shape biểu đồ đầu tiên

Các biểu đồ được lưu dưới dạng các nút `Shape`. Đoạn mã dưới đây lấy biểu đồ đầu tiên trong tài liệu, là mục tiêu cho việc điều chỉnh nhãn của chúng.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Tại sao bước này?*  
Phương thức `GetChild` tìm kiếm đệ quy (`true`) và trả về nút đầu tiên loại `Shape`. Ép kiểu sang `Chart` cho phép chúng ta làm việc với API đặc thù của biểu đồ.

## Bước 3: Truy cập vào nhãn dữ liệu cần chỉnh sửa

Mỗi series trong một biểu đồ có một bộ sưu tập các nhãn dữ liệu. Đối với biểu đồ đơn giản, nhãn đầu tiên thường là đủ. Đoạn mã dưới đây cho thấy cách truy cập nó.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Tại sao bước này?*  
`ChartSeries` đại diện cho một series các điểm. `DataLabelCollection` chứa các nhãn cho series đó, cho phép kiểm soát chính xác vị trí và căn chỉnh.

## Bước 4: Thay đổi vị trí và căn chỉnh nhãn

Bây giờ chúng ta **programmatically adjust chart labels** bằng cách đặt vị trí, căn chỉnh ngang và căn chỉnh dọc. Các thuộc tính này tương ứng với các tùy chọn bạn thấy trong giao diện Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Tại sao lại dùng các thiết lập này?*  

* `OutsideEnd` đặt nhãn ngay bên ngoài cuối mỗi thanh hoặc cột, cải thiện khả năng đọc.  
* `HorizontalAlignment.Center` giữ văn bản ở giữa điểm, trong khi `VerticalAlignment.Top` căn chỉnh cạnh trên của nhãn với điểm dữ liệu, ngăn chồng lấn với các yếu tố khác.

### Mẹo chuyên nghiệp
Nếu một biểu đồ có nhiều series, hãy lặp qua `chart.Series` và áp dụng cùng một thiết lập cho mỗi `DataLabelCollection`. Điều này đảm bảo giao diện nhất quán trên toàn bộ biểu đồ.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Bước 5: Lưu tài liệu đã chỉnh sửa

Sau khi điều chỉnh các nhãn, lưu các thay đổi vào một tệp mới. Điều này hoàn thành quy trình **modify chart label position**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Khi bạn mở `output.docx`, bạn sẽ thấy mọi nhãn biểu đồ đã di chuyển đến cuối bên ngoài của điểm dữ liệu, được căn giữa theo chiều ngang và căn trên theo chiều dọc.

## Các trường hợp đặc biệt và biến thể

| Tình huống | Điều cần lưu ý | Cách tiếp cận đề xuất |
|-----------|-------------------|----------------------|
| **Multiple charts** trong cùng một tài liệu | `GetChild` chỉ trả về biểu đồ đầu tiên. | Sử dụng `doc.GetChildNodes(NodeType.Shape, true)` để lặp qua tất cả các shape biểu đồ. |
| **Series without data labels** | `DataLabelCollection` có thể rỗng. | Kiểm tra `series.HasDataLabels` trước khi truy cập bộ sưu tập. |
| **Different chart types** (pie, line, scatter) | Không phải tất cả các giá trị `DataLabelPosition` đều hợp lệ. | Sử dụng `DataLabelPosition.Auto` cho các biểu đồ tự quyết định vị trí tốt nhất một cách tự động. |
| **Localization** | Các hằng số căn chỉnh không phụ thuộc ngôn ngữ, nhưng văn bản hiển thị có thể cần hỗ trợ từ phải sang trái. | Đặt `dataLabel.TextDirection` nếu bạn cần ngôn ngữ RTL. |

## Ví dụ đầy đủ, có thể chạy

Dưới đây là toàn bộ chương trình mà bạn có thể sao chép, dán và chạy. Thay thế `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi:** Khi mở `output.docx` sẽ hiển thị mỗi nhãn biểu đồ được đặt ngoài điểm dữ liệu, căn giữa theo chiều ngang và căn trên theo chiều dọc — chính xác như hiệu ứng **programmatically adjust chart labels** mà bạn đã lập trình.

## Kết luận

Bây giờ bạn đã biết cách **programmatically adjust chart labels** trong tài liệu Word bằng C#. Bài hướng dẫn đã bao gồm:

* Tải tài liệu với **Aspose.Words chart manipulation**  
* Truy cập một **C# chart data label**  
* Thay đổi **modify chart label position** và căn chỉnh  
* Lưu tệp và xử lý các trường hợp đặc biệt phổ biến  

Từ đây bạn có thể khám phá các kịch bản nâng cao hơn, chẳng hạn tùy chỉnh phông chữ nhãn, thêm định dạng có điều kiện, hoặc cập nhật nhiều biểu đồ trong một quy trình batch. Thử nghiệm các tùy chọn `DataLabelPosition` khác nhau để tìm phong cách phù hợp nhất với báo cáo của bạn.

---

*Sẵn sàng nâng cao quy trình báo cáo tự động của bạn? Hãy thử thêm định dạng số tùy chỉnh cho các nhãn hoặc xuất biểu đồ dưới dạng hình ảnh để sử dụng trong PDF.*

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}