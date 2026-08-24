---
category: general
date: 2026-08-23
description: Tìm hiểu cách nhóm các hình dạng trong C# bằng Aspose.Words. Hướng dẫn
  cũng đề cập đến cách chèn hình chữ nhật và thêm các hình dạng vào Word cho các tài
  liệu phức tạp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: vi
lastmod: 2026-08-23
og_description: Cách nhóm các hình dạng trong C# với Aspose.Words. Theo dõi hướng
  dẫn đầy đủ này để chèn hình chữ nhật, thêm các hình dạng vào Word và nhóm nhiều
  hình dạng một cách hiệu quả.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Cách nhóm các hình dạng trong C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Cách nhóm các hình dạng trong C# với Aspose.Words
url: /vi/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong C# với Aspose.Words

Nếu bạn cần **cách nhóm các hình dạng** trong tài liệu Word một cách lập trình, hướng dẫn này sẽ chỉ cho bạn các bước chính xác bằng cách sử dụng Aspose.Words cho .NET. Dù bạn đang xây dựng một công cụ tạo báo cáo, một engine mẫu, hay một công cụ vẽ sơ đồ, bạn sẽ học cách bắt đầu một nhóm, chèn một hình chữ nhật, và thêm nội dung dạng word‑level vào các hình mà không rời khỏi mã của mình.

Bạn cũng sẽ thấy cách **nhóm nhiều hình dạng** lại với nhau, điều này rất quan trọng khi bạn muốn di chuyển, xoay, hoặc áp dụng kiểu cho một tập hợp các đối tượng như một thực thể duy nhất. Ví dụ dưới đây hoạt động với phiên bản mới nhất Aspose.Words 24.x và chỉ yêu cầu .NET 6 trở lên.

## Yêu cầu trước

- .NET 6 SDK (hoặc bất kỳ phiên bản .NET nào được Aspose.Words hỗ trợ)
- Visual Studio 2022 hoặc VS Code
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Kiến thức cơ bản về C# và mô hình đối tượng Aspose.Words

> **Mẹo chuyên nghiệp:** Sử dụng giấy phép đánh giá miễn phí từ Aspose để tránh giới hạn watermark khi thử nghiệm.

## Cách nhóm các hình dạng với Aspose.Words

Dưới đây là một chương trình hoàn chỉnh, có thể chạy được, minh họa **cách bắt đầu nhóm**, chèn một hình chữ nhật, và hoàn thiện nhóm. Mã nguồn tuân theo luồng logic giống như đoạn mã bạn đã cung cấp, nhưng bổ sung ngữ cảnh, xử lý lỗi, và chú thích để dễ hiểu hơn.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Tại sao mỗi bước lại quan trọng

| Bước | Mục đích | Liên quan đến từ khóa |
|------|----------|------------------------|
| **Tạo một tài liệu trống mới** | Cung cấp một canvas sạch cho các thao tác hình dạng. | Đặt nền cho **add shapes word** sau này. |
| **Khởi tạo DocumentBuilder** | Builder là API chính để chèn các đối tượng. | Cần thiết trước khi bạn có thể **how to start group**. |
| **StartGroupShape** | Bắt đầu một container logic; tất cả các hình tiếp theo sẽ trở thành thành viên của nhóm này. | Trả lời trực tiếp **how to start group**. |
| **InsertShape** (hình chữ nhật, ellipse, text) | Đặt các hình riêng lẻ vào trong nhóm. Lệnh chèn hình chữ nhật đáp ứng **insert rectangle shape**; hình văn bản đáp ứng **add shapes word**. | Minh họa **group multiple shapes**. |
| **EndGroupShape** | Hoàn thiện nhóm để bạn có thể di chuyển hoặc áp dụng kiểu cho nó như một đơn vị. | Hoàn thành quy trình **how to group shapes**. |

## Chèn hình chữ nhật – khám phá sâu hơn

Phương thức `InsertShape` nhận một enum `ShapeType`, chiều rộng và chiều cao. Để **insert rectangle shape** với kiểu dáng tùy chỉnh, bạn có thể mở rộng ví dụ:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Tại sao cần định dạng?** Định dạng giúp hình chữ nhật nổi bật khi nhóm được di chuyển sau này. Nó cũng cho thấy các thuộc tính hình dạng có thể được thiết lập *trước* khi nhóm được đóng.

## Thêm các hình dạng cấp Word (add shapes word)

Nếu bạn cần nhúng văn bản trực tiếp vào một hình—thường gọi là “WordArt” hoặc “text box”—hãy sử dụng `ShapeType.TextPlainText`. Sau khi chèn, bạn có thể ghi văn bản vào hình bằng `DocumentBuilder.Writeln` hoặc bằng cách truy cập thuộc tính `TextBox` của hình:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Điều này đáp ứng từ khóa **add shapes word** và cho thấy cách văn bản có thể đi kèm với nhóm.

## Nhóm nhiều hình dạng – các kịch bản thực tế

Khi bạn **group multiple shapes**, bạn có thể xử lý chúng như một đối tượng duy nhất để định vị, xoay, hoặc thay đổi kích thước. Ví dụ, sau khi nhóm được đóng, bạn có thể di chuyển toàn bộ nhóm:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Hoặc xoay nhóm:

```csharp
group.Rotation = 45; // degrees
```

Các thao tác này chỉ khả thi vì các hình chia sẻ cùng một nhóm cha.

## Xử lý các trường hợp đặc biệt

1. **Nhóm lồng nhau** – Aspose.Words cho phép tạo nhóm trong nhóm. Để tạo một nhóm lồng, gọi `StartGroupShape` một lần nữa trước khi gọi `EndGroupShape` cho nhóm bên trong.
2. **Nhóm rỗng** – Nếu bạn bắt đầu một nhóm nhưng không chèn hình nào, `EndGroupShape` vẫn sẽ tạo một container rỗng. Điều này không gây hại nhưng có thể làm tăng kích thước file hơi lên.
3. **Tương thích** – Tệp DOCX được tạo hoạt động với Word 2010 và các phiên bản sau. Các phiên bản cũ hơn có thể bỏ qua siêu dữ liệu nhóm, vì vậy luôn kiểm tra với phiên bản Word mục tiêu.

## Tệp nguồn đầy đủ để tham khảo

Lưu đoạn mã sau dưới tên `Program.cs` trong một dự án console .NET. Mã sẽ biên dịch và chạy mà không cần chỉnh sửa.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Kết quả mong đợi

Mở `GroupedShapes.docx` trong Microsoft Word sẽ hiển thị:

- Một hình chữ nhật màu coral nhạt, một ellipse, và một hộp văn bản—tất cả đều được ràng buộc trực quan với nhau.
- Khi chọn bất kỳ phần nào của nhóm, toàn bộ nhóm cũng sẽ được chọn (một khung bao duy nhất xuất hiện).
- Di chuyển hoặc xoay nhóm sẽ di chuyển cả ba hình cùng lúc.

## Các câu hỏi thường gặp

**H: Tôi có thể nhóm các hình đã tồn tại trong tài liệu không?**  
Đ: Có. Lấy các đối tượng `Shape` hiện có, gọi `builder.StartGroupShape()`, chèn lại chúng bằng `builder.InsertShape(existingShape)`, rồi gọi `EndGroupShape()`.

**H: Việc nhóm có ảnh hưởng đến XML nền không?**  
Đ: Aspose.Words thêm một phần tử `<w:grpSp>` chứa mỗi nút `<w:sp>` của hình. Điều này hoàn toàn tuân thủ chuẩn Office Open XML.

**H: Nếu tôi cần tách nhóm sau này thì sao?**  
Đ: Không có API “ungroup” trực tiếp, nhưng bạn có thể duyệt qua các hình con của nhóm (`group.GroupShape.Children`) và sao chép chúng ra body tài liệu.

## Bước tiếp theo

Bây giờ bạn đã biết **cách nhóm các hình dạng**, hãy khám phá các chủ đề liên quan sau:

- **Áp dụng định dạng phức tạp cho các hình dạng đã nhóm** – học cách đặt gradient, hiệu ứng bóng, và kiểu đường viền.
- **Xuất các hình dạng đã nhóm dưới dạng hình ảnh** – sử dụng `Shape.GetShapeRenderer().Save(...)` để raster hoá một nhóm.
- **Tạo sơ đồ động** – kết hợp vị trí dựa trên dữ liệu với việc nhóm để tự động tạo flowchart.

Mỗi mục này dựa trên nền tảng đã trình bày ở đây và sẽ giúp bạn tạo ra các tài liệu Word phong phú, tương tác hơn.

---

*Chúc lập trình vui! Nếu bạn thấy hướng dẫn này hữu ích, hãy chia sẻ với đồng nghiệp hoặc đánh dấu sao cho kho lưu trữ chứa dự án mẫu.*

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}