---
category: general
date: 2026-10-20
description: Học cách tạo tài liệu Word trống, nhóm các hình trong Word, đặt màu nền
  cho hình, và sử dụng kiểu bọc nội tuyến với một ví dụ C# hoàn chỉnh.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: vi
lastmod: 2026-10-20
og_description: Tạo một tài liệu Word trống, nhóm các hình dạng trong Word và đặt
  màu nền cho hình dạng với kiểu bao quanh inline bằng Aspose.Words và C#. Thực hiện
  theo hướng dẫn đầy đủ.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Tạo tài liệu Word trống và nhóm các hình dạng trong Word – hướng dẫn từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách tạo tài liệu Word trống và nhóm các hình dạng trong Word bằng Aspose.Words
url: /vi/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và nhóm các hình dạng trong Word

Nếu bạn cần **tạo một tài liệu Word trống** chứa nhiều hình dạng hoạt động như một đơn vị duy nhất, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy cách **nhóm các hình dạng trong Word**, đặt màu nền cho hình dạng, và áp dụng **wrap type inline**—tất cả bằng một chương trình C# ngắn gọn, có thể chạy được.

Bài hướng dẫn sẽ đưa bạn qua từng dòng mã, giải thích lý do mỗi bước quan trọng và nêu bật các lỗi thường gặp. Khi kết thúc, bạn sẽ có một tệp .docx hiển thị một hình chữ nhật và một hộp văn bản được nhóm lại với nhau, sẵn sàng cho các thao tác tự động tiếp theo.

## Những gì bạn sẽ học

* Cách khởi tạo một tệp Word trống bằng Aspose.Words.
* Cách đúng để tạo một **GroupShape** và thêm các hình con.
* Kỹ thuật **set shape fill color** và kiểm soát vị trí.
* Sử dụng **wrap type inline** để nhóm hoạt động như một đối tượng inline duy nhất.
* Cách lưu và xác minh kết quả.

Không cần kinh nghiệm trước với Aspose.Words, nhưng bạn nên quen thuộc với cú pháp C# cơ bản và đã cài đặt Visual Studio (hoặc IDE khác).

## Yêu cầu trước

| Yêu cầu | Lý do |
|-------------|--------|
| .NET 6.0 hoặc mới hơn | Cung cấp môi trường chạy cho dự án C#. |
| Aspose.Words for .NET (phiên bản mới nhất) | Cung cấp các lớp `Document`, `DocumentBuilder` và shape được sử dụng trong ví dụ. |
| Đường dẫn thư mục có thể ghi | Lệnh `doc.Save` cần một thư mục hợp lệ để ghi tệp đầu ra. |
| Kiến thức cơ bản về C# | Giúp bạn theo dõi mã và chỉnh sửa cho các kịch bản của mình. |

Cài đặt Aspose.Words qua NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Bước 1: Tạo tài liệu Word trống

Hoạt động đầu tiên là **tạo một tài liệu Word trống**. Lớp `Document` của Aspose.Words đại diện cho một tệp Word trong bộ nhớ, và `DocumentBuilder` cung cấp một API tiện lợi để chỉnh sửa nó.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Tiêu sao điều này quan trọng*: Bắt đầu với một tài liệu sạch sẽ đảm bảo rằng shape nhóm bạn thêm sẽ là nội dung duy nhất, giúp việc xác minh trở nên đơn giản.

## Bước 2: Định nghĩa một group shape với wrap type inline

Một **GroupShape** hoạt động như một container cho các shape khác. Đặt `WrapType` của nó thành `Inline` đảm bảo nhóm hoạt động như một đối tượng inline duy nhất trong luồng đoạn văn.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Tiêu sao điều này quan trọng*: Sử dụng **wrap type inline** ngăn nhóm trôi ra khỏi văn bản xung quanh, điều này rất cần thiết khi bạn muốn nhóm di chuyển như một đơn vị.

## Bước 3: Thêm một hình chữ nhật và đặt màu nền cho shape

Hình chữ nhật là một yếu tố hình ảnh phổ biến. Hàm khởi tạo `Shape` nhận một `ShapeType`; sau đó chúng ta chỉ định kích thước và màu nền.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Tiêu sao điều này quan trọng*: Thuộc tính `FillColor` minh họa **set shape fill color** trong thực tế, tạo nền màu xanh nhạt cho hình chữ nhật, nổi bật trong tài liệu cuối cùng.

## Bước 4: Thêm một hộp văn bản – cách nhóm các shape một cách hiệu quả

Hộp văn bản cung cấp văn bản có thể chỉnh sửa bên trong nhóm. Đặt vị trí của nó tương đối với hệ tọa độ của nhóm bằng cách điều chỉnh thuộc tính `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Tiêu sao điều này quan trọng*: Bước này trả lời **how to group shapes**—bằng cách thêm mỗi shape con vào cùng một thể hiện `GroupShape`. Độ lệch `Top` đảm bảo hộp văn bản xuất hiện dưới hình chữ nhật, thể hiện kiểm soát bố cục chính xác.

## Bước 5: Chèn group shape đã hoàn thiện vào tài liệu

Bây giờ nhóm đã chứa cả hai shape con, chèn nó vào vị trí hiện tại của builder.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Tiêu sao điều này quan trọng*: Chèn nhóm như một nút duy nhất đảm bảo Word coi hình chữ nhật và hộp văn bản như một đối tượng logic duy nhất, giữ nguyên vị trí tương đối của chúng khi chỉnh sửa.

## Bước 6: Lưu tài liệu và xác minh đầu ra

Cuối cùng, ghi tài liệu ra đĩa. Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Khi bạn mở `GroupShape.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xanh nhạt với một hộp văn bản có nhãn “Grouped text” nằm ngay dưới nó. Chọn bất kỳ shape nào sẽ chọn toàn bộ nhóm, xác nhận rằng **group shapes in Word** hoạt động như mong đợi.

### Kết quả mong đợi

* Một tệp .docx chứa một đoạn văn duy nhất.
* Trong đoạn văn, một nhóm inline trông như một đối tượng hợp thành duy nhất.
* Hình chữ nhật được tô màu xanh nhạt, và hộp văn bản hiển thị “Grouped text”.

![Ảnh chụp màn hình của tài liệu Word đã tạo](grouped_shapes.png){.center width=600 alt="Ảnh chụp màn hình của tài liệu Word trống với hình chữ nhật được nhóm và hộp văn bản được tạo bằng Aspose.Words"}

## Các câu hỏi thường gặp và xử lý các trường hợp đặc biệt

### Nếu tôi cần nhóm nổi thay vì inline thì sao?

Thay `WrapType.Inline` bằng `WrapType.TopBottom` (hoặc bất kỳ giá trị enum `WrapType` nào khác). Các nhóm nổi có thể được đặt vị trí độc lập với luồng đoạn văn, nhưng chúng sẽ mất việc căn chỉnh inline tự động.

### Tôi có thể thêm nhiều shape hơn, chẳng hạn như vòng tròn hoặc hình ảnh không?

Có. Tạo các đối tượng `Shape` bổ sung với `ShapeType.Ellipse` hoặc `ShapeType.Image`, cấu hình các thuộc tính của chúng, và gọi `group.AppendChild(newShape)`. Nhóm sẽ tự động mở rộng để chứa các giới hạn mới nếu bạn cập nhật `group.Bounds` cho phù hợp.

### Làm thế nào để thay đổi kích thước tổng thể của nhóm sau khi đã thêm các shape con?

Điều chỉnh `group.Bounds` sau khi tất cả các shape con đã được thêm, hoặc tính toán hợp nhất các giới hạn của các shape con bằng chương trình. Điều này đảm bảo vùng hit‑test của nhóm khớp với nội dung hình ảnh.

### Nếu thư mục đầu ra không tồn tại thì sao?

Aspose.Words sẽ ném ra một `DirectoryNotFoundException`. Hãy tạo thư mục trước:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Điều này có hoạt động với .NET Framework thay vì .NET Core không?

Tất cả các API được sử dụng (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) đều có sẵn trong phiên bản .NET Framework của Aspose.Words, vì vậy cùng một đoạn mã vẫn hoạt động mà không cần thay đổi.

## Mẹo chuyên nghiệp

* **Mẹo hiệu năng** – Tái sử dụng một thể hiện `DocumentBuilder` duy nhất khi chèn nhiều nhóm; tạo một builder mới cho mỗi nhóm sẽ gây tốn tài nguyên.
* **Nhất quán về hình ảnh** – Đặt `rectangle.StrokeColor` trùng với `FillColor` để có giao diện liền mạch, hoặc đặt `rectangle.LineWidth = 0` để ẩn viền.
* **Gỡ lỗi** – Gọi `doc.UpdatePageLayout()` trước khi lưu nếu bạn thay đổi nhiều shape; điều này buộc Word tính lại bố cục và có thể ngăn ngừa việc cắt xén không mong muốn.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu Word trống**, **nhóm các shape trong Word**, **đặt màu nền cho shape**, và áp dụng **wrap type inline** bằng Aspose.Words cho .NET. Ví dụ đầy đủ minh họa cách tiếp cận tiêu chuẩn để xây dựng đồ họa hợp thành hoạt động như một đối tượng duy nhất trong Word.

Từ đây bạn có thể khám phá:

* Thêm các shape bổ sung như hình ảnh hoặc biểu đồ.
* Thử nghiệm các giá trị `WrapType` khác nhau cho các nhóm nổi.
* Tự động tạo hàng loạt các sơ đồ đã nhóm trên nhiều tài liệu.

Hãy tự do điều chỉnh mã cho các kịch bản tự động của bạn, và chia sẻ kết quả trong phần bình luận!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo tài liệu Word trống với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Cách lưu PDF từ Word với Inline Shapes – Hướng dẫn đầy đủ](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}