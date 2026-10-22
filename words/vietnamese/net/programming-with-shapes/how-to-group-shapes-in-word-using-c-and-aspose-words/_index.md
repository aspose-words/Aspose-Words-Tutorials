---
category: general
date: 2026-09-30
description: Nhóm các hình dạng trong Word bằng C# – học cách nhóm các hình dạng,
  thêm hình chữ nhật và hình elip, và chèn hình chữ nhật vào tài liệu Word một cách
  lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: vi
lastmod: 2026-09-30
og_description: Nhóm các hình dạng trong Word bằng C# và Aspose.Words. Theo dõi hướng
  dẫn đầy đủ này để thêm hình chữ nhật, thêm hình elip và học cách nhóm các hình dạng
  một cách hiệu quả.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Nhóm các hình dạng trong Word bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách nhóm các hình dạng trong Word bằng C# và Aspose.Words
url: /vi/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word bằng C# và Aspose.Words

Nếu bạn cần **nhóm các hình dạng trong Word** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy cách thêm một hình chữ nhật, thêm một hình elip, và sau đó kết hợp chúng thành một nhóm hình duy nhất bằng thư viện Aspose.Words cho .NET.

Làm việc với các hình dạng là một yêu cầu phổ biến khi tự động tạo báo cáo, hợp đồng, hoặc tài liệu marketing. Khi kết thúc tutorial này, bạn sẽ có một phương thức C# có thể tái sử dụng để tải một tệp DOCX, chèn một hình chữ nhật và một hình elip, nhóm chúng lại, và lưu kết quả—tất cả mà không cần mở Word thủ công.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Môi trường phát triển như Visual Studio 2022 (bản Community cũng được)  
* Giấy phép Aspose.Words for .NET hoặc bản dùng thử miễn phí (API hoạt động mà không có giấy phép nhưng sẽ thêm watermark)  

Bạn cũng cần một tài liệu Word nguồn (`input.docx`) trong một thư mục mà bạn có thể tham chiếu từ mã. Tài liệu có thể để trống; tutorial tập trung vào việc xử lý hình dạng.

## Bước 1: Tạo dự án console mới và thêm Aspose.Words

Mở terminal hoặc command prompt của Visual Studio và chạy:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Lệnh này tạo một ứng dụng console mới tên **WordShapeDemo** và thêm gói NuGet `Aspose.Words`, chứa các lớp `Document` và `DocumentBuilder` dùng để thao tác với các tệp Word.

## Bước 2: Tải hoặc tạo một tài liệu

Hoạt động đầu tiên khi làm việc với **nhóm các hình dạng trong Word** là lấy một đối tượng `Document`. Bạn có thể tải một tệp DOCX hiện có hoặc bắt đầu từ một tài liệu trống.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Lớp `Document` đại diện cho toàn bộ tệp Word. Việc tải một tệp sẽ cung cấp cho bạn một canvas sẵn sàng để chèn các hình dạng.

## Bước 3: Bắt đầu một nhóm hình dạng

Một *nhóm hình dạng* cho phép bạn xử lý nhiều hình độc lập như một đơn vị duy nhất—rất thích hợp để di chuyển hoặc thay đổi kích thước chúng cùng nhau. Để bắt đầu một nhóm, gọi `StartGroupShape()` trên một `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Gọi `StartGroupShape` thông báo cho Aspose.Words rằng mọi hình dạng chèn tiếp theo sẽ thuộc cùng một nhóm logic cho đến khi bạn gọi `EndGroupShape`.

## Bước 4: Cách thêm hình chữ nhật trong Word

Bây giờ nhóm đã mở, chèn một hình chữ nhật. Phương thức `InsertShape` nhận một enum `ShapeType`, tiếp theo là chiều rộng và chiều cao (đơn vị là point).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Hình chữ nhật trở thành thành viên đầu tiên của nhóm. Bạn có thể tùy chỉnh màu nền, viền, hoặc văn bản sau này nếu cần.

## Bước 5: Cách thêm hình elip trong Word

Tiếp theo, thêm một hình elip (hình tròn khi chiều rộng bằng chiều cao). Điều này minh họa **cách thêm elip** bằng cùng một builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Cả hai hình hiện đang chia sẻ cùng không gian tọa độ bên trong nhóm, giúp việc căn chỉnh chúng trở nên dễ dàng.

## Bước 6: Đóng định nghĩa nhóm hình dạng

Khi bạn đã chèn hết các thành viên mong muốn, hãy đóng nhóm. Điều này hoàn thiện tập hợp các hình dạng để Word xử lý chúng như một đối tượng duy nhất.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Lúc này tài liệu chứa một đối tượng nhóm duy nhất gồm một hình chữ nhật và một hình elip.

## Bước 7: Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi các thay đổi trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo một tệp mới.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Chạy chương trình sẽ tạo ra `output.docx`. Mở tệp trong Microsoft Word, chọn hình dạng và bạn sẽ thấy hình chữ nhật và elip di chuyển cùng nhau—chứng minh rằng thao tác **nhóm các hình dạng trong Word** đã thành công.

### Kết quả mong đợi

* Tệp Word chứa một đối tượng nhóm duy nhất.  
* Khi chọn nhóm, bạn có thể kéo, thay đổi kích thước, hoặc xoay cả hình chữ nhật và elip đồng thời.  
* Không cần tương tác thủ công với Word; mọi thứ được thực hiện qua mã C#.

![Các hình dạng được nhóm trong tài liệu Word](grouped-shapes.png "Ảnh chụp màn hình tài liệu Word hiển thị một hình chữ nhật và một hình elip đã được nhóm")

*Văn bản thay thế ảnh: “Ảnh chụp màn hình tài liệu Word hiển thị một hình chữ nhật và một hình elip đã được nhóm”* (đáp ứng yêu cầu về alt‑text của ảnh).

## Tại sao việc nhóm các hình dạng lại quan trọng

Nhóm các hình dạng không chỉ là một tiện ích về mặt hình ảnh. Nó cho phép bạn:

* **Duy trì tính nhất quán của bố cục** – di chuyển một nhóm giữ nguyên vị trí tương đối giữa các thành phần.  
* **Áp dụng biến đổi một lần** – xoay hoặc thu phóng toàn bộ nhóm thay vì từng hình riêng lẻ.  
* **Đơn giản hoá quá trình xử lý downstream** – khi các công cụ khác đọc DOCX, chúng sẽ thấy một hình dạng tổng hợp duy nhất, giảm độ phức tạp.

Nếu bạn cần thêm các hình dạng khác (ví dụ: một đường thẳng hoặc một textbox) vào cùng một đơn vị logic, chỉ cần gọi `InsertShape` lại trước khi gọi `EndGroupShape`.

## Các biến thể phổ biến và trường hợp góc cạnh

| Tình huống | Cách xử lý |
|-----------|------------|
| **Đơn vị khác nhau** – bạn có đo lường bằng centimet | Chuyển centimet sang point (`1 cm ≈ 28.35 pt`) trước khi gọi `InsertShape`. |
| **Thêm nhãn văn bản** – bạn muốn một chú thích bên trong nhóm | Chèn một `ShapeType.TextBox` sau hình chữ nhật và elip, rồi đặt thuộc tính `Text`. |
| **Áp dụng màu nền** – bạn cần một hình chữ nhật màu xanh | Sau `InsertShape`, lấy hình cuối cùng qua `builder.CurrentParagraph.Runs[0].Font` và đặt `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Sử dụng định dạng tài liệu khác** – bạn muốn `.doc` thay vì `.docx` | Mã giống nhau; chỉ cần thay đổi phần mở rộng khi gọi `Save`. Aspose.Words tự động xử lý định dạng. |

## Mẹo chuyên nghiệp

* **Tái sử dụng builder** – bạn có thể bắt đầu và kết thúc nhiều nhóm trong cùng một tài liệu; chỉ cần gọi `StartGroupShape` lại sau `EndGroupShape`.  
* **Hiệu năng** – chèn hàng loạt hình dạng trong một khối `StartGroupShape/EndGroupShape` nhanh hơn so với chèn từng hình riêng lẻ bên ngoài nhóm.  
* **Giấy phép** – giấy phép dùng thử sẽ thêm watermark ở trang đầu. Cài đặt giấy phép chính thức để loại bỏ watermark trong môi trường production.

## Kết luận

Bây giờ bạn đã biết cách **nhóm các hình dạng trong Word** bằng C#, cách **thêm hình chữ nhật**, cách **thêm elip**, và cách **chèn hình dạng chữ nhật vào tài liệu Word** bằng Aspose.Words. Ví dụ hoàn chỉnh, có thể chạy được, minh họa mọi bước từ thiết lập dự án đến lưu tệp cuối cùng.

Từ đây, bạn có thể khám phá các loại hình dạng khác, áp dụng kiểu dáng, hoặc kết hợp các nhóm hình dạng với bảng và hình ảnh để tạo ra các tài liệu phức tạp, được tạo tự động bằng mã.

---

**Bước tiếp theo**

* Tìm hiểu cách **xoay các nhóm hình dạng**: sử dụng `Shape.RotationAngle` sau khi nhóm đã được đóng.  
* Khám phá **tùy chỉnh màu nền và viền** cho hình chữ nhật và elip.  
* Tích hợp logic này vào một API ASP.NET Core để tạo báo cáo theo yêu cầu.  

Chúc bạn lập trình vui!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã đầy đủ, hoạt động với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}