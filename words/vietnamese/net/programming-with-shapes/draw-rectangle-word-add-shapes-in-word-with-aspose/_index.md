---
category: general
date: 2026-07-29
description: Vẽ hình chữ nhật trong Word bằng Aspose.Words. Tìm hiểu cách thêm hình
  chữ nhật, thêm hình đường thẳng và quản lý nhiều hình trong một tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: vi
lastmod: 2026-07-29
og_description: Vẽ hình chữ nhật trong Word với Aspose.Words. Hãy làm theo hướng dẫn
  từng bước này để thêm hình chữ nhật, thêm hình đường thẳng và làm việc với nhiều
  hình dạng trong Word một cách dễ dàng.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: vẽ hình chữ nhật trong Word – Thành thạo cách thêm các hình dạng trong Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: vẽ hình chữ nhật trong Word – Thêm hình dạng trong Word với Aspose
url: /vi/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Hướng Dẫn Toàn Diện Thêm Hình Dạng trong Word

Bạn đã bao giờ tự hỏi làm thế nào để **draw rectangle word** tài liệu mà không cần mở giao diện người dùng mỗi lần không? Bạn không phải là người duy nhất. Nhiều nhà phát triển cần tạo các tệp Word một cách nhanh chóng, và cách dễ nhất là để một thư viện thực hiện công việc nặng. Trong hướng dẫn này, chúng tôi sẽ cho bạn thấy chính xác **cách thêm các hình dạng**—cụ thể là một hình chữ nhật và một đường thẳng—bằng cách sử dụng Aspose.Words cho .NET, và chúng tôi sẽ tập trung vào cụm từ *draw rectangle word* để bạn không bao giờ bị lạc.

Hãy nghĩ nó như một studio nghệ thuật mini sống bên trong mã của bạn. Khi kết thúc, bạn sẽ có thể **add rectangle shape**, **add line shape**, và thậm chí kết hợp chúng thành các nhóm **multiple shapes word**. Không giao diện, không thao tác thủ công, chỉ C# sạch sẽ, có thể lặp lại.

## Những Điều Bạn Sẽ Học

- Thiết lập một tài liệu Word mới bằng Aspose.Words.  
- Tạo một **GroupShape** có thể chứa nhiều đối tượng.  
- Thêm **add rectangle shape** và **add line shape** vào trong nhóm đó.  
- Chèn các hình đã nhóm vào phần thân tài liệu.  
- Lưu tệp và xem kết quả ngay lập tức.  

Nếu bạn đã quen với C# cơ bản và có bản sao của Aspose.Words, bạn đã sẵn sàng. Không cần gói NuGet bổ sung nào ngoài thư viện cốt lõi.

> **Pro tip:** Aspose.Words hoạt động với .NET 6, .NET 7 và .NET Framework 4.6+. Chọn môi trường chạy phù hợp với dự án của bạn.

![ví dụ vẽ hình chữ nhật trong Word](https://example.com/placeholder-image.png "vẽ hình chữ nhật – các hình đã nhóm trong tệp Word")

## draw rectangle word – Thiết Lập Tài Liệu

Trước khi chúng ta có thể **draw rectangle word**, chúng ta cần một canvas sạch sẽ. Lớp `Document` là canvas đó; `DocumentBuilder` là cọ vẽ của chúng ta.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hai dòng trên tạo ra một `.docx` mới trong bộ nhớ. Chưa có gì được ghi ra đĩa, nghĩa là chúng ta có thể thử nghiệm mà không làm bừa bộn hệ thống tệp.

## Cách Thêm Hình Dạng – Tạo Container GroupShape

Khi bạn muốn **multiple shapes word** hoạt động như một đơn vị duy nhất—di chuyển cùng nhau, xoay cùng nhau—bạn gói chúng trong một `GroupShape`. Hãy nghĩ nhóm như một thư mục chứa các hình dạng khác.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Tại sao lại dùng nhóm? Bởi vì sau này bạn có thể muốn **add rectangle shape** và **add line shape** rồi di chuyển chúng cùng nhau. Nếu không có nhóm, bạn sẽ phải định vị lại từng hình một cách riêng lẻ.

## add rectangle shape – Chèn Hình Chữ Nhật Vào Nhóm

Bây giờ container đã tồn tại, hãy **add rectangle shape**. Một hình chữ nhật là một `Shape` có `ShapeType` là `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Lưu ý các giá trị `Left` và `Top` được tính tương đối so với gốc của nhóm, không phải trang. Điều này giúp bạn căn chỉnh các hình một cách chính xác. Hình chữ nhật sẽ xuất hiện gần góc trên‑trái của nhóm.

## add line shape – Thêm Đường Vào Cùng Nhóm

Một đường chỉ là một `Shape` khác, nhưng `ShapeType` của nó là `Line`. Chúng ta sẽ đặt nó dưới hình chữ nhật.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Vì chiều cao của đường bằng 0, thuộc tính `Top` quyết định vị trí dọc của đường. Thuộc tính `Width` kiểm soát độ dài ngang của đường.

## multiple shapes word – Chèn Nhóm Vào Thân Tài Liệu

Chúng ta có một nhóm hiện đang chứa **add rectangle shape** và **add line shape**. Bước cuối cùng là đưa toàn bộ nhóm vào tài liệu.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` đặt nhóm chính xác tại vị trí hiện tại của `DocumentBuilder`. Nếu bạn cần nó ở một đoạn văn cụ thể, hãy di chuyển builder bằng `builder.MoveToParagraph(index)` trước tiên.

## Saving the Result – Xem Kết Quả draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Mở tệp đã tạo trong Microsoft Word và bạn sẽ thấy một nhóm duy nhất chứa một hình chữ nhật và một đường thẳng. Bạn có thể nhấp vào nhóm, kéo nó quanh, hoặc thậm chí thay đổi kích thước—tất cả các hình di chuyển cùng nhau. Đó là sức mạnh của **multiple shapes word**.

### Kết Quả Dự Kiến

- Một tệp `.docx` có tên `GroupShape.docx`.  
- Một trang với một hình chữ nhật đã nhóm (120 × 80 pt) gần góc trên‑trái.  
- Một đường ngang (dài 150 pt) được đặt ngay dưới hình chữ nhật.  
- Cả hai hình đều có thể chọn như một đối tượng duy nhất.

Nếu bạn nhấp đúp vào nhóm, Word sẽ cho phép bạn chỉnh sửa từng hình riêng lẻ—hoàn hảo cho việc tinh chỉnh.

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

**Nếu tôi cần nhiều hơn hai hình thì sao?**  
Chỉ cần tiếp tục gọi `group.AppendChild(yourShape)` cho mỗi đối tượng bổ sung. Nhóm có thể chứa bất kỳ số lượng hình nào, rất thích hợp cho các sơ đồ phức tạp.

**Tôi có thể thay đổi màu nền của hình chữ nhật không?**  
Chắc chắn. Sau khi tạo hình chữ nhật, đặt `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Điều này áp dụng cho bất kỳ hình nào hỗ trợ tô màu.

**Có phải tôi phải đặt `Height = 0` cho một đường không?**  
Có, đối với một đường ngang thẳng, chiều cao nên bằng 0. Đối với một đường dọc, đặt `Width = 0` và cho `Height` một giá trị dương.

**Điều này có hoạt động với tệp .doc (Word 97‑2003) không?**  
Aspose.Words có thể lưu sang định dạng `.doc` cũ, nhưng một số tính năng hình dạng hiện đại có thể bị giới hạn. Hãy dùng `.docx` để có độ trung thực đầy đủ.

**Làm thế nào để xoay toàn bộ nhóm?**  
Bạn có thể đặt `group.Rotation = 45;` (độ) trước khi chèn. Việc xoay sẽ áp dụng cho mọi hình con.

## Tóm Tắt – Cách Thêm Hình Dạng trong Word Bằng Mã

- **draw rectangle word** bắt đầu bằng việc tạo một `Document` và `DocumentBuilder`.  
- Xây dựng một **GroupShape** để chứa **multiple shapes word**.  
- **add rectangle shape** và **add line shape** được thêm vào nhóm.  
- Chèn nhóm vào phần thân bằng `builder.InsertNode`.  
- Lưu tệp và mở nó để xác nhận kết quả trực quan.

Đó là toàn bộ quy trình, được gói gọn trong một đoạn mã dễ đọc.

## Các Bước Tiếp Theo & Chủ Đề Liên Quan

Bây giờ bạn đã biết **cách thêm các hình dạng**, hãy xem xét khám phá:

- **add rectangle shape** với các góc bo tròn (`ShapeType.Rectangle` + `CornerRadius`).  
- Định dạng đường với các mẫu gạch khác nhau (`line.LineFormat.DashStyle`).  
- Nhúng hình ảnh cùng với các hình để tạo báo cáo phong phú hơn.  
- Sử dụng **multiple shapes word** để xây dựng sơ đồ luồng hoặc các sơ đồ UML đơn giản.  

Mỗi chủ đề này phát triển một cách tự nhiên dựa trên nền tảng chúng ta đã đặt ra ở đây, và tất cả đều tuân theo cùng một mẫu: tạo hình, cấu hình chúng, và nếu cần, nhóm chúng lại.

---

Chúc bạn lập trình vui! Nếu gặp bất kỳ vấn đề nào hoặc có một trường hợp sử dụng thú vị muốn chia sẻ, hãy để lại bình luận bên dưới. Phản hồi của bạn giúp chúng ta cùng nhau làm chủ nghệ thuật **draw rectangle word** và hơn thế nữa.

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có ví dụ mã hoàn chỉnh, kèm theo giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình chữ nhật trong Word bằng C# – Hướng Dẫn Từng Bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng Dẫn Từng Bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Chèn Hình Dạng vào Tài liệu Word Sử dụng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}