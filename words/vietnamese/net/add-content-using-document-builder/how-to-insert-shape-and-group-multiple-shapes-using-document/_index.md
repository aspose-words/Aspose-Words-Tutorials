---
category: general
date: 2026-11-15
description: Học cách chèn hình dạng vào tài liệu Word và nhóm nhiều hình dạng với
  Aspose.Words DocumentBuilder. Bao gồm các ví dụ chèn hình chữ nhật và chèn nhiều
  hình dạng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: vi
lastmod: 2026-11-15
og_description: Cách chèn hình dạng vào tệp Word bằng Aspose.Words. Hướng dẫn này
  bao gồm việc nhóm nhiều hình dạng, chèn hình chữ nhật và thêm nhiều hình dạng một
  cách hiệu quả.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Cách chèn hình và nhóm nhiều hình bằng DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Cách chèn hình và nhóm nhiều hình bằng DocumentBuilder trong C#
url: /vi/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn hình dạng và nhóm nhiều hình dạng bằng DocumentBuilder trong C#

Nếu bạn cần biết **cách chèn hình dạng** vào tài liệu Word bằng Aspose.Words, hướng dẫn này sẽ chỉ cho bạn các bước chính xác. Bạn cũng sẽ học cách **nhóm nhiều hình dạng** để chúng hoạt động như một đối tượng duy nhất, và cách **chèn hình dạng hình chữ nhật** cùng với các đồ họa khác.

Tự động hoá tài liệu thường yêu cầu thêm nhiều đồ họa—biểu đồ, logo, chú thích—trong khi vẫn giữ chúng được tổ chức. Khi kết thúc tutorial này, bạn sẽ có thể **chèn nhiều hình dạng**, đặt chúng vào một nhóm, và lưu một bố cục sạch sẽ, có thể tái sử dụng.

## Yêu cầu trước

* .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  
* Giấy phép Aspose.Words cho .NET hoặc khóa đánh giá miễn phí  
* Kiến thức cơ bản về C# và lớp `DocumentBuilder` của Aspose.Words  

Bạn **không** cần bất kỳ thư viện bên thứ ba nào khác; mọi thứ cần thiết đều có trong Aspose.Words.

## Bước 1: Cài đặt Aspose.Words qua NuGet

Mở dự án của bạn trong Visual Studio và chạy lệnh sau trong Package Manager Console:

```powershell
Install-Package Aspose.Words
```

Gói này bao gồm các lớp `DocumentBuilder`, `Shape` và `GroupShape` được sử dụng xuyên suốt tutorial này.

## Bước 2: Tạo một thể hiện DocumentBuilder – nền tảng cho **cách chèn hình dạng**

Dòng mã đầu tiên cần thực hiện là tạo một `DocumentBuilder`. Đối tượng này cho phép bạn truy cập trực tiếp vào cây tài liệu, giúp bạn đặt các hình dạng chính xác ở vị trí mong muốn.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Why this matters*: `DocumentBuilder` duy trì một con trỏ (điểm “chèn”). Mọi lệnh `Insert...` tiếp theo đều sử dụng con trỏ này, vì vậy sau này chúng ta di chuyển nó vào một `GroupShape` để giữ tất cả các hình dạng cùng nhau.

## Bước 3: **Chèn hình dạng hình chữ nhật** – đồ họa đầu tiên bạn sẽ thêm

Một hình chữ nhật là placeholder phổ biến cho bảng, hình ảnh hoặc chú thích. Sử dụng `InsertShape` với `ShapeType.Rectangle` và chỉ định chiều rộng, chiều cao bằng điểm (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Hình chữ nhật sẽ xuất hiện tại vị trí con trỏ hiện tại. Bạn có thể tùy chỉnh màu nền, kiểu đường viền hoặc văn bản sau này nếu cần.

## Bước 4: Chèn một hình dạng khác – một hình ellipse để tạo đa dạng trực quan

Thêm hơn một hình dạng cho thấy **chèn nhiều hình dạng**. Hình ellipse sẽ nằm sau hình chữ nhật trong luồng tài liệu.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Tại thời điểm này tài liệu chứa hai hình dạng độc lập. Nếu bạn di chuyển con trỏ hoặc thêm văn bản, các hình dạng sẽ vẫn ở vị trí đã chèn.

## Bước 5: **Nhóm nhiều hình dạng** để chúng hoạt động như một đơn vị duy nhất

Nhóm là cần thiết khi bạn muốn di chuyển, xoay hoặc định dạng nhiều đồ họa cùng lúc. Đoạn mã dưới tạo một `GroupShape`, di chuyển con trỏ của builder vào trong nó, và sau đó chèn lại các hình dạng—lần này chúng trở thành các phần tử con của nhóm.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Tại sao nên dùng nhóm?

* **Biến đổi một điểm duy nhất** – xoay hoặc thay đổi kích thước toàn bộ nhóm bằng một lệnh.  
* **Tổ chức logic** – cây tài liệu Word phản ánh việc nhóm, giúp việc chỉnh sửa sau này dễ dàng hơn.  
* **Bố cục nhất quán** – di chuyển nhóm giữ nguyên vị trí tương đối của các phần tử con.

### Thêm nhiều hình dạng – mở rộng **chèn nhiều hình dạng** trong nhóm

Bạn có thể tiếp tục gọi `InsertShape` trong khi con trỏ vẫn ở bên trong `GroupShape`. Ví dụ, để thêm một tam giác:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Mỗi lần gọi sẽ tuân theo ngữ cảnh nhóm, vì vậy tam giác tự động trở thành một phần của cùng một tập hợp đã nhóm.

## Bước 6: Lưu tài liệu và kiểm tra kết quả

Sau khi tất cả các hình dạng đã được đặt, lưu tài liệu thành tệp `.docx`. Mở tệp trong Microsoft Word (hoặc bất kỳ trình xem tương thích nào) sẽ hiển thị hai hình dạng riêng biệt, tiếp theo là một khối nhóm chứa cùng một hình chữ nhật, ellipse và tam giác.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Kết quả mong đợi

* **Hai hình dạng đầu tiên** – một hình chữ nhật và một hình ellipse được đặt độc lập trên trang.  
* **Khối nhóm** – một hình chữ nhật, một hình ellipse và một tam giác di chuyển cùng nhau khi bạn nhấp vào bất kỳ hình nào trong Word.

Bạn có thể kiểm tra việc nhóm bằng cách chọn bất kỳ hình nào bên trong nhóm; Word sẽ làm nổi bật toàn bộ bộ sưu tập, xác nhận rằng thao tác **nhóm nhiều hình dạng** đã thành công.

## Những lỗi thường gặp và mẹo chuyên nghiệp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Hình dạng xuất hiện ngoài trang mong muốn | Con trỏ của builder chưa được di chuyển vào `GroupShape` trước khi chèn. | Luôn gọi `builder.MoveTo(group)` **trước** bất kỳ lệnh `InsertShape` nào thuộc nhóm. |
| Nhóm biến mất sau khi lưu | Nhóm đã được chèn mà không được thêm vào bộ sưu tập node của tài liệu. | Sử dụng `builder.InsertNode(group)` ngay sau khi tạo `GroupShape`. |
| Kích thước không mong muốn do DPI của tài liệu | Aspose.Words sử dụng đơn vị điểm; nếu bạn suy nghĩ bằng pixel có thể dẫn đến kích thước không khớp. | Chuyển đổi pixel sang điểm (`points = pixels * 72 / 96`) hoặc làm việc trực tiếp bằng điểm. |
| Hình dạng chồng lên nhau không mong muốn | Không có vị trí cụ thể được đặt; Word đặt chúng theo thứ tự liên tiếp. | Đặt `Shape.Left` và `Shape.Top` sau khi chèn để kiểm soát vị trí chính xác. |

**Pro tip:** Sau khi nhóm, bạn có thể lấy bộ sưu tập `Shapes` của nhóm (`group.Shapes`) để duyệt, đổi tên hoặc áp dụng định dạng hàng loạt.

## Bước 7: Mở rộng ví dụ – tiếp theo là gì?

Bây giờ bạn đã biết **cách chèn hình dạng**, **chèn hình dạng hình chữ nhật**, và **nhóm nhiều hình dạng**, bạn có thể khám phá:

* **Tạo hoạt ảnh cho các hình dạng nhóm** – đặt thuộc tính xoay hoặc lật cho nhóm.  
* **Áp dụng kiểu** – sử dụng `Shape.FillColor`, `Shape.LineFormat`, hoặc `Shape.TextBox` để thêm nhãn.  
* **Xuất ra PDF** – cùng bố cục nhóm sẽ được hiển thị đúng khi bạn gọi `doc.Save("output.pdf")`.  

Tất cả các mở rộng này đều tái sử dụng quy trình làm việc `DocumentBuilder` giống nhau, giúp mã của bạn sạch sẽ và dễ bảo trì.

## Kết luận

Tutorial này đã trình bày **cách chèn hình dạng** vào tài liệu Word bằng Aspose.Words, cách **chèn hình dạng hình chữ nhật**, và cách **nhóm nhiều hình dạng** để chúng hoạt động như một đối tượng duy nhất. Bằng cách làm theo mã từng bước, bạn có thể tin cậy **chèn nhiều hình dạng**, tổ chức chúng thành nhóm, và tạo ra các tài liệu chất lượng chuyên nghiệp một cách lập trình.

Hãy tự do thử nghiệm với các loại hình dạng, màu sắc và biến đổi nhóm khác nhau. Khi đã sẵn sàng, tích hợp mẫu này vào các giải pháp báo cáo hoặc mẫu tài liệu lớn hơn để tự động hoá các bố cục tài liệu phức tạp. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn các hình dạng trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Cách tạo và chèn các hình ellipse và hình chữ nhật vào trong một nhóm hình trong tài liệu Word bằng Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Cách nhóm các hình dạng trong tài liệu Word bằng Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}