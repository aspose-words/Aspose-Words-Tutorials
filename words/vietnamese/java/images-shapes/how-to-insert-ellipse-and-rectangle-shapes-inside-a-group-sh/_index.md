---
category: general
date: 2026-10-23
description: Tìm hiểu cách chèn hình elip và cách thêm hình chữ nhật trong Word bằng
  Aspose.Words. Bao gồm việc di chuyển con trỏ đến hình và cách tạo nhóm hình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: vi
lastmod: 2026-10-23
og_description: Cách chèn hình elip và cách thêm hình chữ nhật trong Word bằng Aspose.Words.
  Thực hiện hướng dẫn từng bước để di chuyển con trỏ đến hình và tạo nhóm hình.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Cách chèn hình elip và hình chữ nhật vào nhóm hình trong Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách chèn hình elip và hình chữ nhật vào trong một nhóm hình bằng Aspose.Words
url: /vi/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn hình ellipse và hình chữ nhật vào trong một nhóm hình (group shape) bằng Aspose.Words

Nếu bạn muốn biết **cách chèn ellipse** vào tài liệu Word một cách lập trình, hướng dẫn này sẽ trình bày quy trình đầy đủ. Bạn cũng sẽ thấy **cách thêm hình chữ nhật**, học **cách di chuyển con trỏ tới hình**, và khám phá **cách tạo group shape** chứa nhiều đối tượng vẽ.

Tự động hoá Word thường đòi hỏi việc định vị chính xác các đối tượng vẽ. Khi kết thúc tutorial này, bạn có thể tạo một tệp `.docx` chứa một hình chữ nhật và một ellipse được nhóm lại, sẵn sàng cho việc định dạng hoặc xuất ra thêm. Không cần công cụ bên ngoài nào ngoài thư viện Aspose.Words cho .NET và môi trường phát triển .NET.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 hoặc phiên bản mới hơn được cài đặt.
* Aspose.Words cho .NET (gói NuGet `Aspose.Words`) đã được thêm vào dự án.
* Kiến thức cơ bản về cú pháp C# và Visual Studio (hoặc bất kỳ IDE nào).

Những yêu cầu này đảm bảo mã của bạn biên dịch mà không cần cấu hình thêm.

## Cách tạo group shape trong Word

Một group shape hoạt động như một container cho phép bạn di chuyển, xoay hoặc định dạng nhiều hình dạng như một đơn vị duy nhất. Đoạn mã dưới đây tạo một nhóm có kích thước cụ thể (300 × 200 points) và chuẩn bị tài liệu cho các thao tác vẽ tiếp theo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Lý do bước này quan trọng*: Group shape xác định một hệ tọa độ cục bộ. Tất cả các hình được thêm sau khi di chuyển con trỏ vào group sẽ được định vị tương đối so với gốc của group, giúp việc tính toán bố cục trở nên đơn giản.

## Cách thêm hình chữ nhật trong Word

Bây giờ group đã tồn tại, bạn có thể **chèn hình chữ nhật** vào bên trong. Hình chữ nhật sẽ đóng vai trò là nền hoặc là một khung hình ảnh cho nội dung khác.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Giải thích*: `MoveTo(group)` thông báo cho builder rằng điểm chèn hiện tại là shape group. Nếu không di chuyển con trỏ, `InsertShape` sẽ thêm hình chữ nhật vào phần thân chính của tài liệu thay vì vào group.

## Cách chèn ellipse

Với hình chữ nhật đã có, bạn có thể **chèn ellipse**. Ellipse sẽ được đặt ở trung tâm cùng một group, chồng lên hình chữ nhật nếu muốn.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Lý do cần di chuyển con trỏ*: Mỗi lần gọi `InsertShape` sẽ dựa trên vị trí con trỏ hiện tại. Gọi lại `MoveTo(group)` đảm bảo ellipse cũng là một phần con của group, giữ nguyên cấu trúc mong muốn.

## Di chuyển con trỏ tới shape trước khi chèn các đối tượng khác

Nếu bạn cần thêm nhiều shape sau này, luôn **di chuyển con trỏ tới shape** trước mỗi lần chèn. Mô hình này tránh việc đặt nhầm ngoài group.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Mẹo*: Việc tái sử dụng `MoveTo(group)` là nhẹ và cải thiện khả năng đọc mã. Nó cũng giúp bảo trì dễ dàng hơn vì ngữ cảnh chèn luôn rõ ràng.

## Lưu tài liệu

Cuối cùng, lưu tài liệu ra đĩa. Ví dụ lưu tệp dưới tên `GroupShape.docx` trong thư mục bạn chỉ định.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Khi mở tệp đã lưu trong Microsoft Word, bạn sẽ thấy một group duy nhất chứa một hình chữ nhật và một ellipse, cả hai đều được đặt đúng vị trí.

### Kết quả mong đợi

* Một tệp `.docx` có tên `GroupShape.docx`.
* Trong tài liệu, một đối tượng vẽ được nhóm có kích thước 300 × 200 points.
* Bên trong group:
  * Một hình chữ nhật (100 × 50 points) nằm ở gốc của group.
  * Một ellipse (80 × 80 points) chồng lên hình chữ nhật.
  * Bất kỳ shape bổ sung nào bạn đã thêm sau khi di chuyển con trỏ.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Phương pháp đề xuất |
|-----------|----------------------|
| **Kích thước đơn vị khác nhau** | Aspose.Words sử dụng points (1 pt = 1/72 in). Chuyển đổi centimet hoặc inch sang points trước khi gọi `InsertShape`. |
| **Xoay các shape bên trong group** | Sau khi chèn shape, lấy đối tượng `ShapeBase` và đặt `ShapeBase.RotationAngle`. |
| **Thêm văn bản vào shape** | Sử dụng `ShapeBase.AppendChild(new Paragraph(document))` rồi thêm một `Run` chứa văn bản mong muốn. |
| **Lưu dưới dạng PDF thay vì DOCX** | Gọi `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – cấu trúc group vẫn được giữ trong file PDF. |

Các biến thể này cho thấy logic **cách chèn ellipse** có thể được điều chỉnh cho nhiều kịch bản thực tế.

## Mẹo chuyên nghiệp

* **Tái sử dụng cùng một instance của `DocumentBuilder`** – giảm tải bộ nhớ và giữ trạng thái tài liệu nhất quán.
* **Kiểm tra kích thước shape** – chiều rộng hoặc chiều cao quá lớn có thể gây lỗi hiển thị trên các phiên bản Word cũ.
* **Nhóm trước khi định dạng** – áp dụng màu nền hoặc kiểu đường viền cho group sau khi đã thêm tất cả các phần tử con sẽ đảm bảo giao diện đồng nhất.

## Kết luận

Bây giờ bạn đã nắm rõ **cách chèn ellipse** và **cách thêm hình chữ nhật** vào một container được nhóm trong tài liệu Word bằng Aspose.Words. Bằng cách luôn **di chuyển con trỏ tới shape** trước mỗi lần chèn, bạn duy trì cấu trúc sạch sẽ và tránh việc đặt nhầm. Ví dụ hoàn chỉnh biên dịch, chạy và tạo ra một group shape có thể tùy chỉnh thêm hoặc xuất ra.

Sẵn sàng khám phá thêm? Hãy thử kết hợp kỹ thuật này với **cách tạo group shape** cho các sơ đồ phức tạp, hoặc thử **chèn hình chữ nhật trong Word** cùng các textbox để tạo báo cáo phong phú. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial dưới đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ và giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API khác và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [How to create blank Word document and add a hidden ellipse shape in C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [How to create group shape docx and add interactive controls in C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}