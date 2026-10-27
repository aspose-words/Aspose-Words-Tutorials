---
category: general
date: 2026-10-10
description: Dịch đoạn văn sang tiếng Pháp và tìm hiểu cách thay đổi nhãn dữ liệu
  biểu đồ, tùy chỉnh nhãn dữ liệu biểu đồ, và lưu tệp docx đã chỉnh sửa bằng Aspose.Words
  AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: vi
lastmod: 2026-10-10
og_description: Dịch đoạn văn sang tiếng Pháp và học cách thay đổi nhãn dữ liệu biểu
  đồ, tùy chỉnh nhãn dữ liệu biểu đồ và lưu tệp docx đã chỉnh sửa bằng Aspose.Words
  AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Dịch đoạn văn sang tiếng Pháp và thay đổi nhãn biểu đồ trong Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Dịch đoạn văn sang tiếng Pháp và thay đổi nhãn biểu đồ trong Word
url: /vi/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dịch đoạn văn sang tiếng Pháp và thay đổi nhãn biểu đồ trong Word

Nếu bạn cần **dịch đoạn văn sang tiếng Pháp** đồng thời cập nhật một biểu đồ trong cùng một tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Sử dụng Aspose.Words AI, bạn có thể tự động dịch văn bản, sau đó sửa đổi nhãn dữ liệu của biểu đồ và cuối cùng lưu tệp `.docx` đã chỉnh sửa—tất cả trong một vài bước đơn giản.

Bài hướng dẫn bao gồm mọi thứ từ việc tải tệp nguồn đến việc lưu lại các thay đổi. Khi hoàn thành, bạn sẽ có thể dịch bất kỳ đoạn văn nào, tùy chỉnh nhãn dữ liệu của biểu đồ, và tạo ra một tệp Word mới sẵn sàng phân phối. Không cần bất kỳ script bên ngoài nào; toàn bộ quy trình được thực hiện trong một chương trình C# duy nhất.

## Yêu cầu trước

- .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.7+)
- Giấy phép Aspose.Words cho .NET (hoặc khóa đánh giá miễn phí)
- Kết nối internet để sử dụng trình dịch Google AI (lớp `Translator` sử dụng API của Google phía sau)
- Một tài liệu Word (`input.docx`) chứa ít nhất một đoạn văn và một biểu đồ

## Bước 1: Thiết lập dự án và nhập không gian tên

Tạo một ứng dụng console mới và thêm gói NuGet Aspose.Words:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Bây giờ bao gồm các không gian tên cần thiết ở đầu file `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Các import này cho phép bạn truy cập vào chức năng tải tài liệu, dịch AI và chỉnh sửa biểu đồ.

## Bước 2: Tải tài liệu Word nguồn

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Việc tải tệp tạo ra một biểu diễn trong bộ nhớ mà bạn có thể truy vấn và sửa đổi mà không làm ảnh hưởng tới tệp gốc trên đĩa.

## Bước 3: Dịch đoạn văn đầu tiên sang tiếng Pháp

Đoạn văn đầu tiên thường là tiêu đề hoặc câu giới thiệu, vì vậy nó là một ứng cử viên tốt để dịch. Lớp `Translator` trừu tượng hóa việc gọi mô hình AI của Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Tại sao cách này hoạt động:**  
`paragraph.Runs.Clear()` loại bỏ tất cả các run văn bản hiện có, đảm bảo bản dịch mới không bị nối liền với nội dung cũ. `new Run(document, translatedText)` tạo một run mới kế thừa định dạng của đoạn văn.

## Bước 4: Tìm biểu đồ đầu tiên và tùy chỉnh nhãn dữ liệu của nó

Biểu đồ được lưu dưới dạng các nút `Shape` có kiểu `NodeType.Shape`. Biểu đồ đầu tiên có thể được lấy bằng `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Giải thích các bước chính:**

- `GetChild(NodeType.Shape, 0, true)` thực hiện tìm kiếm theo chiều sâu và trả về shape đầu tiên, trong trường hợp của chúng ta là một biểu đồ.
- `ChartSeries` đại diện cho một tập hợp các điểm dữ liệu; series đầu tiên (`Series[0]`) thường tương ứng với bộ dữ liệu chính.
- `ChartDataLabelPosition.OutsideEnd` di chuyển nhãn ra ngoài cuối thanh, cải thiện khả năng đọc.
- Đặt `dataLabel.Text` thành một chuỗi tiếng Pháp sẽ đồng bộ nhãn với đoạn văn đã dịch.

## Bước 5: Lưu tài liệu với đoạn văn đã dịch

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

Ở thời điểm này, tài liệu đã chứa đoạn văn tiếng Pháp nhưng vẫn giữ cấu hình biểu đồ gốc.

## Bước 6: Lưu tài liệu với biểu đồ đã cập nhật

Bạn có thể tái sử dụng cùng một thể hiện `Document`—không cần tải lại—vì các thay đổi biểu đồ đã có trong bộ nhớ.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Cả hai tệp bây giờ đã sẵn sàng để phân phối:

- **`translated.docx`** – chứa đoạn văn tiếng Pháp.
- **`chart-updated.docx`** – chứa đoạn văn tiếng Pháp *và* nhãn biểu đồ đã tùy chỉnh.

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là toàn bộ chương trình mà bạn có thể sao chép‑dán vào `Program.cs`. Nó biên dịch và chạy ngay lập tức, với điều kiện bạn đã thay thế `YOUR_DIRECTORY` bằng đường dẫn thư mục thực.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tùy chỉnh Nhãn Dữ liệu Biểu đồ](/words/english/net/programming-with-charts/chart-data-label/)
- [Định dạng Số của Nhãn Dữ liệu trong Biểu đồ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Nhãn Dữ liệu Biểu đồ](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}