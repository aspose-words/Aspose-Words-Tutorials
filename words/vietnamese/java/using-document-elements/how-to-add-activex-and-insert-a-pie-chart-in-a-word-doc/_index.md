---
category: general
date: 2026-08-17
description: Cách thêm các điều khiển ActiveX và chèn biểu đồ tròn vào tài liệu Word
  bằng Aspose.Words. Bóc một lát và lưu dưới dạng DOCX trong vài bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: vi
lastmod: 2026-08-17
og_description: Cách thêm điều khiển ActiveX, chèn biểu đồ tròn, tách một lát và lưu
  dưới dạng DOCX với Aspose.Words – hướng dẫn chi tiết từng bước.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Cách thêm ActiveX và chèn biểu đồ tròn vào tài liệu Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Cách thêm ActiveX và chèn biểu đồ tròn trong tài liệu Word
url: /vi/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm ActiveX và chèn biểu đồ tròn trong tài liệu Word

Nếu bạn cần **cách thêm ActiveX** và nhúng biểu đồ vào tài liệu Word, hướng dẫn này sẽ cung cấp cho bạn một giải pháp hoàn chỉnh, có thể chạy được. Sử dụng Aspose.Words, bạn có thể đặt một ActiveX CommandButton, tạo biểu đồ tròn, tách một lát để nhấn mạnh, và cuối cùng **lưu dưới dạng DOCX** chỉ trong vài dòng C#.

Trong các phần dưới đây, bạn sẽ thấy mọi import cần thiết, danh sách mã đầy đủ, và giải thích tại sao mỗi bước lại quan trọng. Khi hoàn thành, bạn sẽ có thể tích hợp các điều khiển tương tác và dữ liệu trực quan vào bất kỳ tệp .docx nào bạn tạo bằng chương trình.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
* Gói Aspose.Words for .NET (có sẵn qua NuGet)
* Môi trường phát triển như Visual Studio 2022 hoặc VS Code
* Kiến thức cơ bản về C# và mô hình đối tượng Word

Không cần thư viện biểu đồ bên thứ ba nào—Aspose.Words cung cấp chức năng tạo biểu đồ tích hợp.

## Cách thêm điều khiển ActiveX với Aspose.Words

Điều khiển ActiveX cho phép bạn nhúng các thành phần UI tương tác trực tiếp trong tệp Word. Trong hướng dẫn này, chúng ta sẽ thêm một **CommandButton** mà sau này có thể được gắn với mã VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Tại sao cách này hoạt động:**  
`InsertForms2OleControl` tạo một container OLE mà giao diện Word nhận dạng là một điều khiển ActiveX. Đặt loại điều khiển thành `CommandButton` và cung cấp tiêu đề khiến nó hoạt động như một nút tiêu chuẩn khi người dùng mở tệp trong Word.

## Chèn biểu đồ tròn và tách một lát

Biểu đồ hữu ích cho việc trực quan hoá dữ liệu mà không cần rời khỏi tài liệu. Các bước sau đây minh họa **cách chèn biểu đồ** và cụ thể là **biểu đồ tròn** với lát đầu tiên được tách ra.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Tại sao tách lát:**  
Gọi `SetExplode(0, true)` yêu cầu Aspose.Words dịch chuyển điểm dữ liệu đầu tiên, thu hút ánh nhìn của người xem tới đoạn đó. Đây là kỹ thuật phổ biến trong các bài thuyết trình để làm nổi bật một giá trị quan trọng.

## Lưu dưới dạng DOCX

Sau khi đã thêm nút ActiveX và biểu đồ, lưu tài liệu ra đĩa. Bước này minh họa **lưu dưới dạng DOCX** bằng phương pháp tiêu chuẩn.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Tệp `Output.docx` hiện chứa một nút tương tác, một biểu đồ tròn với lát đã tách, và có thể được mở trong Microsoft Word mà không cần plugin bổ sung.

## Ví dụ đầy đủ có thể chạy

Kết hợp mọi thứ lại, dưới đây là một chương trình tự chứa mà bạn có thể sao chép vào ứng dụng console và chạy ngay lập tức.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Kết quả mong đợi:**  
Mở `Output.docx` trong Word sẽ hiển thị một nút có nhãn *Click Me* và một biểu đồ tròn trong đó lát đầu tiên (January) được dịch ra khỏi phần còn lại. Nút đã sẵn sàng cho việc xử lý sự kiện VBA, và biểu đồ có thể được chỉnh sửa bằng công cụ biểu đồ tích hợp của Word.

## Các câu hỏi thường gặp và trường hợp đặc biệt

* **Tôi có thể thêm các loại ActiveX khác không?**  
  Có. Thay `Forms2OleControlType.CommandButton` bằng bất kỳ giá trị nào từ enum `Forms2OleControlType` (ví dụ, `CheckBox`, `OptionButton`). Mẫu chèn vẫn giống nhau.

* **Nếu tôi cần một loại biểu đồ khác thì sao?**  
  Sử dụng `ChartType.Bar`, `ChartType.Line`, v.v., trong lời gọi `InsertChart`. Bước **cách chèn biểu đồ** vẫn giống, chỉ thay đổi giá trị enum.

* **Làm sao kiểm soát kích thước của lát đã tách?**  
  Aspose.Words hiện chỉ hỗ trợ cờ tách nhị phân (true/false). Để kiểm soát chi tiết hơn (ví dụ, khoảng cách dịch), bạn cần chỉnh sửa OOXML gốc sau khi lưu.

* **Tài liệu có tương thích với các phiên bản Word cũ không?**  
  Lưu dưới dạng DOCX đảm bảo tương thích với Word 2007 trở lên. Đối với Word 2003 bạn có thể đổi sang `SaveFormat.Doc` nhưng hỗ trợ ActiveX trong định dạng đó hạn chế.

* **Có cần tham chiếu `System.Drawing` không?**  
  Không. Tất cả các đối tượng vẽ đều được Aspose.Words cung cấp, vì vậy gói NuGet duy nhất cần thiết là `Aspose.Words`.

## Kết luận

Bây giờ bạn đã biết **cách thêm ActiveX**, **chèn biểu đồ tròn**, **tách lát biểu đồ**, và **lưu dưới dạng DOCX** bằng Aspose.Words for .NET. Ví dụ hoàn chỉnh bao gồm mọi bước từ tạo tài liệu đến lưu cuối cùng, đồng thời giải thích lý do đằng sau mỗi lời gọi API.

Tiếp theo, bạn có thể khám phá:

* Thêm macro VBA phản hồi khi nhấn CommandButton (**cách chèn biểu đồ** và tự động cập nhật dữ liệu)
* Tùy chỉnh giao diện biểu đồ (màu sắc, nhãn dữ liệu) để phù hợp với thương hiệu công ty
* Nhúng các điều khiển ActiveX bổ sung như **ComboBox** hoặc **ListBox** để tạo biểu mẫu phong phú hơn

Hãy thoải mái thử nghiệm với mã, thay đổi dữ liệu mẫu, và tích hợp giải pháp này vào quy trình tạo tài liệu của riêng bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}