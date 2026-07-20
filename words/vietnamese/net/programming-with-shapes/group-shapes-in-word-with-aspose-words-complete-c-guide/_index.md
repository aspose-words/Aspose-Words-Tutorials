---
category: general
date: 2026-07-19
description: Nhóm các hình dạng trong Word bằng Aspose.Words. Tìm hiểu cách thêm hình
  chữ nhật, định nghĩa hình elip và chèn hình vào tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: vi
lastmod: 2026-07-19
og_description: Nhóm các hình dạng trong Word với Aspose.Words. Thêm hình chữ nhật,
  định nghĩa hình elip và chèn hình vào tài liệu Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Nhóm các hình dạng trong Word – Hướng dẫn C# từng bước
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Nhóm hình dạng trong Word với Aspose.Words – Hướng dẫn C# đầy đủ
url: /vi/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhóm Các Hình Dạng trong Word – Hướng Dẫn C# Đầy Đủ

Bạn đã bao giờ tự hỏi làm thế nào để **group shapes in Word** mà không cần bận tâm giao diện người dùng? Bạn không phải là người duy nhất. Dù bạn đang tạo hợp đồng, tờ rơi, hay sơ đồ một cách tự động, khả năng **add rectangle shape**, **define ellipse shape**, và sau đó **group shapes in Word** có thể tiết kiệm cho bạn hàng giờ công việc thủ công.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ thực tế sử dụng **Aspose.Words for .NET**. Khi kết thúc, bạn sẽ biết chính xác cách **insert shape into Word**, kết hợp chúng, và tạo ra một tài liệu hoàn chỉnh mà bạn có thể gửi cho khách hàng hoặc đồng nghiệp.

---

## Những Điều Bạn Cần Có

- **Aspose.Words for .NET** (phiên bản mới nhất, ví dụ: 24.9). Bạn có thể tải về từ NuGet bằng `Install-Package Aspose.Words`.
- Môi trường phát triển .NET (Visual Studio 2022 hoặc VS Code với extension C#) hoạt động tốt.
- Kiến thức cơ bản về cú pháp C#—không cần gì phức tạp, chỉ cần các câu lệnh `using` thông thường và việc tạo đối tượng.

Chỉ vậy thôi. Không cần thư viện bổ sung, không cần COM interop, chỉ là mã quản lý thuần túy.

---

## Cách Nhóm Các Hình Dạng trong Word Sử Dụng Aspose.Words

Dưới đây là bản phân tích từng bước phản ánh mã bạn đã có. Mỗi bước giải thích **why** chúng ta thực hiện, không chỉ **what** dòng lệnh làm, để bạn có thể áp dụng mẫu cho bất kỳ hình nào bạn muốn.

### Bước 1: Thiết Lập Tài Liệu và Builder

Chúng ta bắt đầu bằng việc tạo một `Document` trống và một `DocumentBuilder`. Builder là “bút” của chúng ta cho phép chèn nội dung ở bất kỳ vị trí nào cần thiết.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why?** Đối tượng `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp một API tiện lợi để chèn các node (như shapes) mà không cần xử lý cây node bên dưới.

### Bước 2: Thêm Hình Chữ Nhật (add rectangle shape)

Bây giờ chúng ta **add rectangle shape** vào tài liệu. Chúng ta đặt kích thước, vị trí và màu nền để nó nổi bật.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** Bạn có thể thay đổi `FillColor` thành bất kỳ `System.Drawing.Color` nào bạn muốn. Điều này hữu ích khi bạn cần các phần được mã màu trong báo cáo.

### Bước 3: Định Nghĩa Hình Elip (define ellipse shape)

Tiếp theo, chúng ta **define ellipse shape**. Lưu ý `ShapeType` khác nhau và độ dịch (`Left = 120`) để hình elip nằm bên cạnh hình chữ nhật.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Why this matters:** Bằng cách đặt vị trí các hình một cách rõ ràng, bạn kiểm soát cách chúng xuất hiện trước khi nhóm lại. Nếu bạn dựa vào bố cục tự động, việc nhóm có thể bị lệch trung tâm.

### Bước 4: (Tùy Chọn) Chèn Các Hình Riêng Lẻ Để Xem Trước

Nếu bạn muốn xem từng hình trước khi nhóm, bạn có thể **insert shape into Word** riêng lẻ. Bước này là tùy chọn nhưng hữu ích cho việc gỡ lỗi.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Bạn nên comment hai dòng này khi đã chắc chắn các hình hiển thị đúng; nếu không sẽ có các hình trùng lặp sau khi nhóm.

### Bước 5: Cách Nhóm Các Hình – Tạo GroupShape

Đây là phần cốt lõi của hướng dẫn: **how to group shapes**. Chúng ta tạo một `GroupShape`, gắn hình chữ nhật và elip vào, và quyết định cách nhóm tương tác với văn bản xung quanh.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explanation:** `GroupShape` thực chất là một mini‑canvas chứa các shape khác. Bằng cách đặt `WrapType` thành `Inline`, toàn bộ nhóm di chuyển như một đơn vị duy nhất khi bạn thêm hoặc xóa văn bản.

### Bước 6: Chèn Hình Được Nhóm Vào Tài Liệu (insert shape into word)

Bây giờ chúng ta **insert shape into Word**—nhưng lần này là container đã được nhóm, không phải các phần riêng lẻ.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **What happens under the hood?** Lệnh `InsertNode` thêm `GroupShape` vào bộ sưu tập node của tài liệu. Vì nhóm đã chứa hình chữ nhật và elip, chúng xuất hiện cùng nhau như một đối tượng.

### Bước 7: Lưu Tài Liệu

Cuối cùng, ghi tệp ra đĩa. Bạn có thể thay đổi đường dẫn để phù hợp với cấu trúc dự án.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Result:** Mở `GroupShape.docx` trong Microsoft Word và bạn sẽ thấy một hình chữ nhật màu xanh nhạt và một hình elip màu san hô được khóa cùng nhau. Kéo một hình sẽ di chuyển hình còn lại—đúng như lời hứa của “group shapes in word”.

---

## Xác Nhận Hình Ảnh

Dưới đây là mô phỏng về cách các hình đã nhóm trông như thế nào trong tệp Word.  

![Ảnh chụp màn hình các hình đã nhóm trong tài liệu Word được tạo bằng Aspose.Words](grouped_shapes_placeholder.png "nhóm các hình trong word")

*Văn bản thay thế của hình ảnh chứa từ khóa chính để tăng khả năng truy cập và SEO.*

---

## Câu Hỏi Thường Gặp & Các Trường Hợp Đặc Biệt

### Nếu tôi cần hơn hai hình thì sao?

Chỉ cần tiếp tục gọi `groupShape.AppendChild(yourNewShape);` trước khi chèn nhóm. API không đặt giới hạn số lượng shape con.

### Tôi có thể xoay hoặc thay đổi kích thước toàn bộ nhóm không?

Chắc chắn. `GroupShape` kế thừa từ `Shape`, vì vậy bạn có thể đặt các thuộc tính như `RotationAngle`, `Width`, hoặc `Height` trên chính nhóm, và tất cả các shape con sẽ theo.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Làm sao để thay đổi màu nền của nhóm?

Sử dụng `groupShape.FillColor`. Điều này sẽ tô màu cho hộp bao vô hình; có thể hữu ích để làm nổi bật.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Điều này có hoạt động với các định dạng Word cũ (.doc) không?

`Aspose.Words` cũng có thể lưu thành `.doc`—chỉ cần thay đổi phần mở rộng tệp trong `Save`. Tuy nhiên, một số tính năng shape nâng cao (như grouping) chỉ được hỗ trợ đầy đủ trong định dạng OOXML `.docx`.

---

## Ví Dụ Hoàn Chỉnh Hoạt Động

Sao chép‑dán khối sau vào một ứng dụng console mới để xem toàn bộ quá trình hoạt động. Không có phần nào bị thiếu; đây là một **ví dụ đầy đủ, có thể chạy được**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Expected output:** Khi mở `GroupShape.docx`, bạn sẽ thấy một đối tượng đã nhóm duy nhất bao gồm một hình chữ nhật màu xanh nhạt và một hình elip màu san hô nhạt, được căn chỉnh hoàn hảo bên cạnh nhau.

---

## Tóm Tắt

Chúng ta vừa bao quát mọi thứ bạn cần để **group shapes in Word** với Aspose.Words:

1. Tạo tài liệu và builder.  
2. **Add rectangle shape** và **define ellipse shape** với kích thước rõ ràng.  
3. (Tùy chọn) **insert shape into Word** để xem nhanh trước.  
4. Sử dụng `GroupShape` để **how to group shapes**—thêm mỗi child, đặt wrap, và chèn.  
5. Lưu tệp và xác nhận.

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn Các Hình Vào Tài Liệu Word Sử Dụng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tạo Hình Chữ Nhật trong Word với Aspose.Words – Hướng Dẫn Từng Bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Hướng Dẫn Shadow cho Shape trong Aspose.Words – Thêm Bóng cho Shape Word trong C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}