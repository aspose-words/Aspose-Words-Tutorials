---
category: general
date: 2026-07-23
description: Tạo tài liệu Word trống và thêm hình chữ nhật trong C#. Tìm hiểu cách
  chèn hình dạng và nhóm các hình dạng trong Word bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: vi
lastmod: 2026-07-23
og_description: Tạo tài liệu Word trống trong C# và học cách chèn hình dạng, thêm
  hình chữ nhật và nhóm các hình dạng trong Word bằng Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Tạo tài liệu Word trống với các hình chữ nhật được nhóm – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word trống với các hình chữ nhật được nhóm – Hướng dẫn C#
url: /vi/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống với các hình chữ nhật được nhóm – Hướng dẫn C#

Bạn đã bao giờ cần **tạo tài liệu Word trống** mà trong đó đã có sẵn một tập hợp các hình dạng, nhưng không chắc cách nhóm chúng một cách gọn gàng? Bạn không phải là người duy nhất. Trong nhiều trường hợp báo cáo hoặc tạo mẫu, bạn muốn có một canvas sạch sẽ với một vài hình chữ nhật làm chỗ giữ chỗ, và muốn chúng di chuyển cùng nhau như một đơn vị duy nhất.

Trong hướng dẫn này, chúng ta sẽ đi qua các bước **tạo tài liệu Word trống**, **thêm hình chữ nhật**, và sau đó **nhóm các hình dạng trong Word** bằng thư viện Aspose.Words. Khi kết thúc, bạn sẽ có một tệp `.docx` sẵn sàng sử dụng, trong đó hai hình chữ nhật là một phần của một nhóm, vì vậy bất kỳ việc định vị hoặc thay đổi kích thước nào sau này sẽ ảnh hưởng đến cả hai cùng một lúc.  

Chúng tôi cũng sẽ trả lời các câu hỏi thường gặp “**cách chèn hình dạng**” và “**cách nhóm hình dạng**” mà thường xuất hiện trên các diễn đàn và Stack Overflow. Không cần tài liệu bên ngoài—mọi thứ bạn cần đều có ở đây.

---

## Yêu cầu trước

- .NET 6 hoặc mới hơn (mã cũng biên dịch được với .NET Core)  
- Aspose.Words for .NET (gói NuGet `Aspose.Words`)  
- Kiến thức cơ bản về cú pháp C# (nếu bạn đã viết “Hello World”, bạn đã sẵn sàng)  

Nếu bạn chưa cài đặt Aspose.Words, chạy:

```bash
dotnet add package Aspose.Words
```

Xong—không cần DLL bổ sung, không cần COM interop, chỉ một tham chiếu NuGet sạch sẽ.

---

## Bước 1: Tạo tài liệu Word trống và khởi tạo builder

Điều đầu tiên chúng ta làm là khởi tạo một đối tượng `Document` rỗng. Hãy tưởng tượng nó như một tờ giấy mới. Sau đó chúng ta gắn một `DocumentBuilder`, công cụ tiện lợi mà Aspose cung cấp để chèn nội dung.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tại sao lại quan trọng:** Nếu không có `DocumentBuilder` bạn sẽ phải thao tác trực tiếp với cây node cấp thấp, điều này dễ gây lỗi. Builder giúp trừu tượng hoá các chi tiết XML của tệp `.docx`.

---

## Bước 2: Cách chèn hình dạng – thêm một container nhóm trước

Aspose cho phép bạn chèn một *group shape* (hình nhóm) mà sau này có thể chứa các hình dạng khác. Đây là nền tảng cho **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Mẹo chuyên nghiệp:** Nhóm bản thân nó vô hình cho tới khi bạn thêm các hình con, vì vậy bạn sẽ không thấy bất kỳ artefact nào trong tài liệu cho tới bước tiếp theo.

---

## Bước 3: Thêm hình chữ nhật – các đối tượng hiển thị thực tế

Bây giờ chúng ta sẽ **thêm hình chữ nhật** hai lần, mỗi lần với kích thước riêng. Phương thức `InsertShape` nhận một `ShapeType` và kích thước tính bằng điểm (1 pt ≈ 1/72 inch).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Tại sao lại là hình chữ nhật?** Chúng là hình học đơn giản nhất, hoàn hảo cho chỗ giữ chỗ, mô phỏng UI dạng nút, hoặc các yếu tố đồ họa cơ bản.

---

## Bước 4: Cách nhóm các hình dạng – gắn các hình chữ nhật vào nhóm

Với các hình chữ nhật đã tạo, chúng ta bây giờ **cách nhóm các hình dạng** bằng cách thêm chúng làm con của shape nhóm mà chúng ta đã chèn ở bước trước.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Bên trong thực tế:** Shape nhóm trở thành node cha trong cây XML của tài liệu. Di chuyển nhóm sẽ di chuyển cả hai hình chữ nhật cùng nhau, giữ nguyên vị trí tương đối của chúng.

---

## Bước 5: Lưu tài liệu – bạn đã có một tệp Word chứa hình dạng được nhóm

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Thay đổi đường dẫn thành vị trí tồn tại trên máy của bạn.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Đó là toàn bộ chương trình. Chạy nó, mở `GroupShape.docx`, và bạn sẽ thấy hai hình chữ nhật nằm cùng nhau. Nếu bạn chọn một hình, toàn bộ nhóm sẽ được đánh dấu—đúng như **group shapes word** mong muốn.

---

## Toàn bộ mã nguồn ở một nơi

Để tiện, dưới đây là ví dụ hoàn chỉnh, sẵn sàng sao chép:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Kết quả mong đợi:** Mở `GroupShape.docx` sẽ hiển thị một trang trống với hai hình chữ nhật được nhóm lại. Khi chọn một hình chữ nhật, hình còn lại sẽ tự động được chọn, xác nhận việc nhóm đã thành công.

---

## Các câu hỏi thường gặp & xử lý trường hợp đặc biệt

### Nếu tôi cần nhiều hơn hai hình dạng thì sao?

Chỉ cần tiếp tục gọi `builder.InsertShape(...)` và `group.AppendChild(...)` cho mỗi hình mới. Nhóm có thể chứa bất kỳ số lượng con nào.

### Tôi có thể đặt màu nền hoặc viền cho các hình chữ nhật không?

Chắc chắn. Sau khi tạo một hình chữ nhật, bạn có thể điều chỉnh `FillColor`, `OutlineColor`, và `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Làm sao di chuyển toàn bộ nhóm sau khi đã tạo?

Sử dụng các thuộc tính `Left` và `Top` của nhóm, tính bằng điểm:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Còn việc thay đổi tỷ lệ của nhóm?

Đặt `group.Width` và `group.Height` hoặc dùng `group.ScaleX` / `group.ScaleY`. Các hình chữ nhật con sẽ giữ tỉ lệ tương đối so với nhóm.

### Điều này có hoạt động với các tệp .doc cũ không?

Aspose.Words trừu tượng hoá định dạng tệp, vì vậy cùng một đoạn mã hoạt động cho `.doc` và `.docx`. Giới hạn duy nhất là một số tính năng hình dạng mới hơn có thể bị giảm cấp khi lưu dưới định dạng nhị phân cũ.

---

## Mẹo cho mã chuẩn sản xuất

- **Giải phóng tài nguyên** – Đặt `Document` trong khối `using` nếu bạn làm việc với tệp lớn để giải phóng bộ nhớ kịp thời.  
- **Xử lý lỗi** – Bắt `Aspose.Words.Fonts.FontSettingsException` nếu bạn dự định nhúng phông chữ tùy chỉnh.  
- **Hiệu năng** – Khi chèn nhiều hình dạng, tạm thời tắt cập nhật bố cục bằng `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` và bật lại sau khi hoàn tất.

---

## Kết luận

Bây giờ bạn đã biết **cách tạo tài liệu Word trống**, **thêm hình chữ nhật**, và **nhóm các hình dạng trong Word** bằng Aspose.Words trong C#. Ví dụ này bao gồm các bước “**cách chèn hình dạng**” và “**cách nhóm hình dạng**” thiết yếu, giải thích lý do mỗi dòng mã tồn tại, và thậm chí đề cập tới tùy chỉnh, các trường hợp đặc biệt, và các thực hành tốt nhất.

Tiếp theo, bạn có thể khám phá **cách chèn hình ảnh**, **thêm văn bản vào trong các hình dạng được nhóm**, hoặc **xuất tài liệu ra PDF**—tất cả đều theo cùng một mẫu sử dụng `DocumentBuilder` và thao tác shape. Hãy tiếp tục thử nghiệm; API của Aspose đủ mạnh để xử lý hầu hết mọi kịch bản tự động hoá Word mà bạn có thể tưởng tượng.

Chúc lập trình vui vẻ, và đừng ngại để lại bình luận nếu gặp bất kỳ khó khăn nào!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn hình dạng trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn chi tiết](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}