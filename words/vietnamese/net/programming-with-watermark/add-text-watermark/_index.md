---
title: Thêm Watermark Văn bản Đỏ Chéo vào Tài liệu Word bằng Aspose.Words cho .NET
weight: 110
limit:
description: Tự động áp dụng watermark văn bản màu đỏ chéo vào mỗi tệp Word được tạo trong một lô bằng Aspose.Words cho .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Tự động áp dụng watermark văn bản màu đỏ chéo vào mỗi tệp Word được
    tạo trong một lô bằng Aspose.Words cho .NET.
  headline: Thêm Watermark Văn bản Đỏ Chéo vào Tài liệu Word bằng Aspose.Words cho
    .NET
  type: TechArticle
- description: Tự động áp dụng watermark văn bản màu đỏ chéo vào mỗi tệp Word được
    tạo trong một lô bằng Aspose.Words cho .NET.
  name: Thêm Watermark Văn bản Đỏ Chéo vào Tài liệu Word bằng Aspose.Words cho .NET
  steps:
  - name: Tạo thư mục "GeneratedReports" nơi các tệp đầu ra sẽ được lưu.
    text: Tạo thư mục "GeneratedReports" nơi các tệp đầu ra sẽ được lưu.
  - name: Bắt đầu một vòng lặp sẽ tạo ba tài liệu riêng biệt.
    text: Bắt đầu một vòng lặp sẽ tạo ba tài liệu riêng biệt.
  - name: Tạo một đối tượng tài liệu Word mới rỗng.
    text: Tạo một đối tượng tài liệu Word mới rỗng.
  - name: Sử dụng DocumentBuilder để ghi một dòng tiêu đề và mô tả vào tài liệu.
    text: Sử dụng DocumentBuilder để ghi một dòng tiêu đề và mô tả vào tài liệu.
  - name: Xác định giao diện của watermark, bao gồm phông chữ, kích thước, màu sắc
      và bố cục chéo.
    text: Xác định giao diện của watermark, bao gồm phông chữ, kích thước, màu sắc
      và bố cục chéo.
  - name: Áp dụng watermark chéo màu đỏ đã cấu hình với văn bản "PROTECTED" vào tài
      liệu.
    text: Áp dụng watermark chéo màu đỏ đã cấu hình với văn bản "PROTECTED" vào tài
      liệu.
  - name: Lưu tài liệu đã có watermark vào thư mục "GeneratedReports" với tên tệp
      duy nhất.
    text: Lưu tài liệu đã có watermark vào thư mục "GeneratedReports" với tên tệp
      duy nhất.
  - name: Đóng vòng lặp sau khi xử lý tài liệu hiện tại.
    text: Đóng vòng lặp sau khi xử lý tài liệu hiện tại.
  type: HowTo
- questions:
  - answer: '**IsSemitrasparent** xác định liệu watermark có được hiển thị với độ
      trong suốt một phần hay không; đặt nó thành **true** làm cho văn bản bán trong
      suốt để nội dung nền vẫn dễ đọc hơn.'
    question: Tùy chọn **IsSemitrasparent** kiểm soát gì và việc đặt nó thành **true**
      có ảnh hưởng gì?
  - answer: Có—đặt thuộc tính **Layout** thành **WatermarkLayout.Horizontal** trong
      **TextWatermarkOptions** trước khi gọi **document.Watermark.SetText**.
    question: Tôi có thể thay đổi hướng của watermark thành ngang thay vì chéo không?
  - answer: Đoạn mã tạo một thể hiện **Document** mới, nhưng bạn có thể mở bất kỳ
      tệp hiện có nào (ví dụ, `new Document(\"Existing.docx\")`) và sau đó gọi **document.Watermark.SetText**
      để áp dụng cùng một watermark.
    question: Đoạn mã này sẽ thêm watermark vào tệp Word hiện có, hay chỉ vào các
      tài liệu mới tạo?
  - answer: Gán một màu tùy chỉnh bằng **Color.FromArgb(red, green, blue)** cho thuộc
      tính **Color** của **TextWatermarkOptions**, ví dụ, `Color = Color.FromArgb(128,
      0, 128)` cho màu tím.
    question: Làm sao tôi có thể sử dụng màu RGB tùy chỉnh cho watermark thay vì **Color.Red**
      đã định sẵn?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Thêm Watermark Văn bản Đỏ Chéo vào Tài liệu Word
og_description: Xem cách tự động áp dụng watermark màu đỏ chéo vào mỗi tài liệu Word trong một lô với Aspose.Words.
og_image_alt: Hướng dẫn cách thêm watermark văn bản màu đỏ chéo vào tài liệu Word bằng Aspose.Words cho .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Watermark Văn bản Đỏ Chéo vào Tài liệu Word bằng Aspose.Words cho .NET
Hướng dẫn này trình bày cách tự động nhúng một watermark văn bản màu đỏ chéo vào mỗi tài liệu Word được tạo trong quá trình tạo báo cáo hàng loạt. Sử dụng các lớp Document và DocumentBuilder của Aspose.Words cho .NET, watermark được áp dụng bằng chương trình khi các tệp được tạo, đảm bảo mỗi tài liệu đều mang cùng một thương hiệu hoặc thông báo bảo mật mà không cần thao tác thủ công.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Tùy chọn **IsSemitrasparent** kiểm soát gì và việc đặt nó thành **true** có ảnh hưởng gì?**  
A: **IsSemitrasparent** xác định liệu watermark có được hiển thị với độ trong suốt một phần hay không; đặt nó thành **true** làm cho văn bản bán trong suốt để nội dung nền vẫn dễ đọc hơn.

**Q: Tôi có thể thay đổi hướng của watermark thành ngang thay vì chéo không?**  
A: Có—đặt thuộc tính **Layout** thành **WatermarkLayout.Horizontal** trong **TextWatermarkOptions** trước khi gọi **document.Watermark.SetText**.

**Q: Đoạn mã này sẽ thêm watermark vào tệp Word hiện có, hay chỉ vào các tài liệu mới tạo?**  
A: Đoạn mã tạo một thể hiện **Document** mới, nhưng bạn có thể mở bất kỳ tệp hiện có nào (ví dụ, `new Document(\"Existing.docx\")`) và sau đó gọi **document.Watermark.SetText** để áp dụng cùng một watermark.

**Q: Làm sao tôi có thể sử dụng màu RGB tùy chỉnh cho watermark thay vì **Color.Red** đã định sẵn?**  
A: Gán một màu tùy chỉnh bằng **Color.FromArgb(red, green, blue)** cho thuộc tính **Color** của **TextWatermarkOptions**, ví dụ, `Color = Color.FromArgb(128, 0, 128)` cho màu tím.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}