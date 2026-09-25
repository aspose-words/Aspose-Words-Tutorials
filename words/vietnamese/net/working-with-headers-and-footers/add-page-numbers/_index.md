---
title: Thêm số trang vào chân trang của tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Thêm số trang tự động cập nhật vào chân trang chính của tài liệu Word bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Thêm số trang tự động cập nhật vào chân trang chính của tài liệu Word
    bằng Aspose.Words for .NET.
  headline: Thêm số trang vào chân trang của tài liệu Word bằng Aspose.Words for .NET
  type: TechArticle
- description: Thêm số trang tự động cập nhật vào chân trang chính của tài liệu Word
    bằng Aspose.Words for .NET.
  name: Thêm số trang vào chân trang của tài liệu Word bằng Aspose.Words for .NET
  steps:
  - name: Tạo một đối tượng Document mới và một DocumentBuilder gắn với nó.
    text: Tạo một đối tượng Document mới và một DocumentBuilder gắn với nó.
  - name: Di chuyển con trỏ của builder tới chân trang chính của phần đầu tiên.
    text: Di chuyển con trỏ của builder tới chân trang chính của phần đầu tiên.
  - name: Đặt căn chỉnh đoạn văn thành trung tâm để văn bản chân trang được căn giữa.
    text: Đặt căn chỉnh đoạn văn thành trung tâm để văn bản chân trang được căn giữa.
  - name: Ghi nhãn "Page " và chèn một trường PAGE hiển thị số trang hiện tại.
    text: Ghi nhãn "Page " và chèn một trường PAGE hiển thị số trang hiện tại.
  - name: Ghi " of " và chèn một trường NUMPAGES hiển thị tổng số trang.
    text: Ghi " of " và chèn một trường NUMPAGES hiển thị tổng số trang.
  - name: Lưu tài liệu dưới dạng tệp .docx.
    text: Lưu tài liệu dưới dạng tệp .docx.
  type: HowTo
- questions:
  - answer: Không. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` chỉ di chuyển
      builder tới chân trang chính của *phần đầu tiên*, vì vậy các trường chỉ được
      chèn ở đó.
    question: Nếu tài liệu có hơn một phần, đoạn mã này có thêm số trang vào chân
      trang của mọi phần không?
  - answer: Đặt `builder.ParagraphFormat.Alignment` thành một giá trị `ParagraphAlignment`
      khác (ví dụ, `ParagraphAlignment.Right`) trước khi ghi các trường.
    question: Làm thế nào để thay đổi căn chỉnh của đoạn văn số trang trong chân trang?
  - answer: '`InsertField` nhận mã trường và một kết quả trường tùy chọn; truyền `null`
      cho Aspose.Words để Word tính kết quả tại thời gian chạy.'
    question: Tham số `null` trong `InsertField("PAGE", null)` đại diện cho gì?
  - answer: Đúng—thay `HeaderFooterType.FooterPrimary` bằng `HeaderFooterType.HeaderPrimary`
      (hoặc một loại header khác) trước khi chèn các trường.
    question: Tôi có thể đặt các trường "Page X of Y" tương tự trong header thay vì
      footer không?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Chèn số trang tự động trong chân trang Word
og_description: Mã từng bước để thêm số trang động vào chân trang Word bằng Aspose.Words for .NET.
og_image_alt: Hướng dẫn cách thêm số trang tự động vào chân trang tài liệu Word bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm số trang vào chân trang của tài liệu Word bằng Aspose.Words
Hướng dẫn này cho thấy cách sử dụng Aspose.Words Document và DocumentBuilder để chèn số trang tự động cập nhật vào chân trang chính của tài liệu Word. Bằng cách thêm số trang bằng chương trình, bạn đảm bảo việc phân trang nhất quán trên toàn bộ tệp mà không cần chỉnh sửa thủ công. Mã ví dụ đã sẵn sàng để chạy trong môi trường .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Nếu tài liệu có hơn một phần, đoạn mã này có thêm số trang vào chân trang của mọi phần không?**  
A: Không. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` chỉ di chuyển builder tới chân trang chính của *phần đầu tiên*, vì vậy các trường chỉ được chèn ở đó.

**Q: Làm thế nào để thay đổi căn chỉnh của đoạn văn số trang trong chân trang?**  
A: Đặt `builder.ParagraphFormat.Alignment` thành một giá trị `ParagraphAlignment` khác (ví dụ, `ParagraphAlignment.Right`) trước khi ghi các trường.

**Q: Tham số `null` trong `InsertField("PAGE", null)` đại diện cho gì?**  
A: `InsertField` nhận mã trường và một kết quả trường tùy chọn; truyền `null` cho Aspose.Words để Word tính kết quả tại thời gian chạy.

**Q: Tôi có thể đặt các trường "Page X of Y" tương tự trong header thay vì footer không?**  
A: Đúng—thay `HeaderFooterType.FooterPrimary` bằng `HeaderFooterType.HeaderPrimary` (hoặc một loại header khác) trước khi chèn các trường.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}