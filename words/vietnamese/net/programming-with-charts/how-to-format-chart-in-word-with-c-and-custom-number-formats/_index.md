---
category: general
date: 2026-10-13
description: Cách định dạng biểu đồ trong Word bằng C# bằng cách áp dụng định dạng
  số tùy chỉnh, chẳng hạn như tiền tệ, cho các trục biểu đồ. Bao gồm ví dụ mã từng
  bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: vi
lastmod: 2026-10-13
og_description: Cách định dạng biểu đồ trong Word bằng C# cho phép bạn áp dụng định
  dạng số tùy chỉnh cho các trục biểu đồ, đảm bảo các giá trị hiển thị dưới dạng tiền
  tệ, phần trăm hoặc bất kỳ mẫu nào bạn cần. Hãy làm theo hướng dẫn từng bước.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Cách định dạng biểu đồ trong Word bằng C# – định dạng số tùy chỉnh
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Cách định dạng biểu đồ trong Word bằng C# và định dạng số tùy chỉnh
url: /vi/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách định dạng biểu đồ trong Word bằng C# và định dạng số tùy chỉnh

Cách định dạng biểu đồ trong Word bằng C# là một yêu cầu phổ biến khi bạn cần trình bày dữ liệu một cách chuyên nghiệp. Hướng dẫn này chỉ cho bạn cách áp dụng định dạng số tùy chỉnh cho trục của biểu đồ bằng **Aspose.Words for .NET**, để các giá trị hiển thị chính xác như mong muốn.

Bạn sẽ học cách tải tệp DOCX, xác định biểu đồ đầu tiên, đọc định dạng hiện tại, và sau đó đặt mẫu mới như tiền tệ với hai chữ số thập phân. Hướng dẫn cũng đề cập cách thay đổi định dạng trục biểu đồ cho các chuỗi bổ sung và cách đặt lại định dạng nếu cần.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt  
* Một dự án Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ .NET)  
* Gói NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Một tài liệu Word (`input.docx`) chứa ít nhất một biểu đồ

Bạn có thể thêm gói bằng lệnh sau:

```bash
dotnet add package Aspose.Words
```

## Cách định dạng biểu đồ trong Word bằng Aspose.Words

Chương trình hoàn chỉnh dưới đây minh họa mọi bước cần thiết để **định dạng biểu đồ** các giá trị trục. Lưu tệp dưới dạng `Program.cs` và chạy nó từ dòng lệnh hoặc IDE của bạn.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Giải thích từng bước

| Bước | Lý do quan trọng | Mã chính |
|------|-------------------|----------|
| **Load the document** | Bạn cần một đối tượng `Document` để làm việc với tệp Word. | `new Document("input.docx")` |
| **Retrieve the chart** | `Chart` được lưu dưới dạng nút `Shape`; việc ép kiểu cho phép bạn sử dụng các API đặc thù cho biểu đồ. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Access X‑values** | Định dạng trục được áp dụng cho bộ sưu tập giá trị của một chuỗi dữ liệu. | `chart.ChartData.Series[0].XValues` |
| **Read current format** | Biết `FormatCode` hiện tại giúp bạn quyết định có nên thay thế hoặc bổ sung nó. | `xValues.FormatCode` |
| **Set custom format** | Thuộc tính `FormatCode` chấp nhận bất kỳ mẫu nào tương thích với Excel, cho phép định dạng tiền tệ, phần trăm, ngày tháng, v.v. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Save the document** | Lưu các thay đổi sẽ ghi định dạng trục mới trở lại tệp DOCX. | `doc.Save("output_formatted.docx")` |

Chạy chương trình sẽ tạo ra `output_formatted.docx`. Mở tệp trong Word và bạn sẽ thấy các giá trị trục X của biểu đồ hiển thị dưới dạng **$1,234.00**, **$2,345.00**, … thay vì các số thuần.

## Áp dụng định dạng số tùy chỉnh cho trục biểu đồ

Nếu bạn cần **áp dụng định dạng số tùy chỉnh** cho trục Y hoặc cho các chuỗi bổ sung, quy trình vẫn giống nhau—chỉ cần nhắm vào bộ sưu tập khác:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Mẹo chuyên nghiệp:** Sử dụng dấu ngoặc kép bên trong chuỗi định dạng để chèn các ký tự nguyên (ví dụ, `"$"` cho tiền tệ). Thoát dấu ngoặc kép như đã minh họa ở trên.

## Định dạng số tùy chỉnh trong Word – xử lý ngôn ngữ của Word

Word tôn trọng ngôn ngữ của tài liệu khi diễn giải các định dạng số. Nếu tài liệu sử dụng ngôn ngữ không phải tiếng Mỹ, bạn có thể cần điều chỉnh chuỗi định dạng:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Kiểm tra định dạng trên tài liệu có cài đặt ngôn ngữ tiếng Đức xác nhận rằng các giá trị hiển thị dưới dạng **€ 1.234,00**.

## Cách đặt thuộc tính biểu đồ bằng mã

Ngoài việc định dạng trục, bạn thường muốn **đặt biểu đồ** tiêu đề, chú giải hoặc nhãn dữ liệu. Dưới đây là một đoạn mã nhanh minh họa cách đặt tiêu đề biểu đồ sau khi đã định dạng trục:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Kết hợp đoạn này với định dạng số tùy chỉnh sẽ cho bạn một biểu đồ hoàn thiện, sẵn sàng cho việc báo cáo.

## Thay đổi định dạng trục biểu đồ một cách động dựa trên đầu vào của người dùng

Trong các ứng dụng thực tế, bạn có thể cho phép người dùng chọn định dạng tại thời gian chạy. Phương thức sau gói gọn logic định dạng:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Bạn có thể gọi `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` cho tiền tệ hoặc `SetAxisFormat(chart, 0, "0%")` cho phần trăm. Cách tiếp cận này giữ cho mã chính của bạn sạch sẽ và hỗ trợ các mở rộng trong tương lai.

## Trường hợp đặc biệt và những lỗi thường gặp

| Tình huống | Cần lưu ý | Giải pháp đề xuất |
|-----------|----------|-------------------|
| Tài liệu không chứa **biểu đồ** | `GetChild` trả về `null`, gây ra ngoại lệ khi ép kiểu. | Kiểm tra `null` trước khi ép kiểu (xem ví dụ). |
| Nhiều biểu đồ trong cùng một tài liệu | Mã luôn lấy biểu đồ đầu tiên (`chỉ số 0`). | Lặp qua `doc.GetChildNodes(NodeType.Shape, true)` và lọc theo `ShapeType.Chart`. |
| Chuỗi **không có X‑values** (ví dụ: biểu đồ tròn) | Truy cập `XValues` có thể gây ra `ArgumentOutOfRangeException`. | Kiểm tra `Series[i].XValues` không rỗng trước khi định dạng. |
| Không khớp ngôn ngữ | Ký hiệu tiền tệ có thể hiển thị sai. | Đặt rõ `xValues.FormatCode` với các ký hiệu ngôn ngữ phù hợp. |

## Kết quả mong đợi

Sau khi chạy chương trình mẫu, mở **output_formatted.docx**. Trục X của biểu đồ nên hiển thị các số theo định dạng tùy chỉnh đã chọn. Đối với ví dụ tiền tệ, nhãn trục sẽ trông như sau:

```
$1,000.00
$2,000.00
$3,000.00
```

Nếu bạn áp dụng định dạng phần trăm cho các giá trị Y, nhãn trục Y sẽ xuất hiện như:

```
10%
20%
30%
```

## Kết luận

Bài hướng dẫn này đã chỉ cho bạn **cách định dạng biểu đồ** trong Word bằng C# bằng cách **áp dụng định dạng số tùy chỉnh** cho các giá trị trục. Giờ đây bạn có một mẫu có thể tái sử dụng để đặt tiền tệ, phần trăm hoặc bất kỳ mẫu số nào khác, cùng với hướng dẫn xử lý ngôn ngữ, nhiều chuỗi và đầu vào động của người dùng.

Tiếp theo, bạn có thể khám phá **cách đặt tiêu đề biểu đồ**, nhãn dữ liệu, hoặc thậm chí xuất biểu đồ dưới dạng hình ảnh bằng `ChartRenderer`. Những chủ đề này xây dựng trực tiếp trên các khái niệm đã trình bày ở đây và sẽ giúp bạn tạo ra các giải pháp báo cáo hoàn toàn tự động.

---


## Bạn nên học gì tiếp theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Định dạng số cho trục trong biểu đồ](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Định dạng số của nhãn dữ liệu trong biểu đồ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Định dạng trục X phụ và đặt đơn vị hiển thị thành hàng nghìn trong biểu đồ đường Word bằng Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}