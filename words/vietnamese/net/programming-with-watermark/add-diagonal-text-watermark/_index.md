---
title: Tạo Watermark Văn bản Chéo với Phông Tùy chỉnh trong Tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Mã từng bước để thêm watermark văn bản chéo với phông tùy chỉnh vào tệp Word .docx bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Mã từng bước để thêm watermark văn bản chéo với phông tùy chỉnh vào
    tệp Word .docx bằng Aspose.Words for .NET.
  headline: Tạo Watermark Văn bản Chéo với Phông Tùy chỉnh trong Tài liệu Word bằng
    Aspose.Words for .NET
  type: TechArticle
- description: Mã từng bước để thêm watermark văn bản chéo với phông tùy chỉnh vào
    tệp Word .docx bằng Aspose.Words for .NET.
  name: Tạo Watermark Văn bản Chéo với Phông Tùy chỉnh trong Tài liệu Word bằng Aspose.Words
    for .NET
  steps:
  - name: Tạo một thể hiện tài liệu Word mới rỗng có tên `document`.
    text: Tạo một thể hiện tài liệu Word mới rỗng có tên `document`.
  - name: Cấu hình `watermarkSettings` với phông Arial 48‑pt màu xám, bố cục chéo,
      và hiển thị không trong suốt.
    text: Cấu hình `watermarkSettings` với phông Arial 48‑pt màu xám, bố cục chéo,
      và hiển thị không trong suốt.
  - name: Áp dụng watermark văn bản "Private" vào `document` bằng cách sử dụng các
      thiết lập đã định nghĩa trước.
    text: Áp dụng watermark văn bản "Private" vào `document` bằng cách sử dụng các
      thiết lập đã định nghĩa trước.
  - name: Xác định đường dẫn tệp nơi tài liệu đã được gắn watermark sẽ được lưu.
    text: Xác định đường dẫn tệp nơi tài liệu đã được gắn watermark sẽ được lưu.
  - name: Lưu `document` đã chỉnh sửa vào đường dẫn đã chỉ định dưới dạng tệp .docx.
    text: Lưu `document` đã chỉnh sửa vào đường dẫn đã chỉ định dưới dạng tệp .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` xác định liệu watermark có được hiển thị với độ trong
      suốt một phần hay không; đặt thành `false` làm watermark hoàn toàn không trong
      suốt, trong khi `true` áp dụng hiệu ứng bán trong suốt mặc định.'
    question: Cờ **IsSemitrasparent** kiểm soát gì trong `TextWatermarkOptions`?
  - answer: Có—đặt thuộc tính `Layout` thành `WatermarkLayout.Horizontal` (hoặc một
      giá trị enum khác) trước khi gọi `document.Watermark.SetText`.
    question: Tôi có thể thay đổi hướng của watermark thành ngang thay vì chéo không?
  - answer: Word sẽ chuyển sang phông mặc định cho watermark, vì vậy văn bản vẫn hiển
      thị nhưng có thể trông khác so với kiểu mong muốn.
    question: Điều gì sẽ xảy ra nếu `FontFamily` được chỉ định (ví dụ, "Arial") không
      được cài đặt trên máy đích?
  - answer: Tải tệp hiện có bằng `Document document = new Document("Existing.docx");`
      sau đó cấu hình `TextWatermarkOptions` và gọi `document.Watermark.SetText` như
      đã minh họa.
    question: Có thể thêm watermark vào tệp `.docx` hiện có thay vì tạo tệp mới không?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Thêm Watermark Văn bản Chéo với Phông Tùy chỉnh
og_description: Học cách nhúng watermark văn bản nghiêng với phông chữ của bạn vào tệp Word chỉ trong vài phút.
og_image_alt: Hướng dẫn cách thêm watermark văn bản chéo với phông tùy chỉnh vào tài liệu Word bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Watermark Văn bản Chéo với Phông Tùy chỉnh trong Tài liệu Word bằng Aspose.Words
Hướng dẫn này sẽ đưa bạn qua các bước tạo một tài liệu Word mới, cấu hình watermark văn bản chéo với các thiết lập phông chữ bạn chọn, áp dụng nó qua API Document.Watermark.SetText, và lưu kết quả dưới dạng tệp .docx. Khi hoàn thành, bạn sẽ có một tài liệu được gắn watermark chuyên nghiệp, thể hiện thương hiệu hoặc quyền sở hữu của bạn. Mã nguồn từng bước đã sẵn sàng để sao chép vào bất kỳ dự án .NET nào.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Cờ **IsSemitrasparent** kiểm soát gì trong `TextWatermarkOptions`?**  
A: `IsSemitrasparent` xác định liệu watermark có được hiển thị với độ trong suốt một phần hay không; đặt thành `false` làm watermark hoàn toàn không trong suốt, trong khi `true` áp dụng hiệu ứng bán trong suốt mặc định.

**Q: Tôi có thể thay đổi hướng của watermark thành ngang thay vì chéo không?**  
A: Có—đặt thuộc tính `Layout` thành `WatermarkLayout.Horizontal` (hoặc một giá trị enum khác) trước khi gọi `document.Watermark.SetText`.

**Q: Điều gì sẽ xảy ra nếu `FontFamily` được chỉ định (ví dụ, "Arial") không được cài đặt trên máy đích?**  
A: Word sẽ chuyển sang phông mặc định cho watermark, vì vậy văn bản vẫn hiển thị nhưng có thể trông khác so với kiểu mong muốn.

**Q: Có thể thêm watermark vào tệp `.docx` hiện có thay vì tạo tệp mới không?**  
A: Tải tệp hiện có bằng `Document document = new Document("Existing.docx");` sau đó cấu hình `TextWatermarkOptions` và gọi `document.Watermark.SetText` như đã minh họa.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}