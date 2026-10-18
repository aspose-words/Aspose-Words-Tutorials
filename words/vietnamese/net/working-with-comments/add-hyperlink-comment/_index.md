---
title: Thêm Hyperlink Comment và Xuất dưới dạng PDF Annotation bằng Aspose.Words for .NET
weight: 110
limit:
description: Học cách thêm một hyperlink comment trong tệp Word và xuất nó dưới dạng PDF annotation bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Học cách thêm một hyperlink comment trong tệp Word và xuất nó dưới
    dạng PDF annotation bằng Aspose.Words for .NET.
  headline: Thêm Hyperlink Comment và Xuất dưới dạng PDF Annotation bằng Aspose.Words
    for .NET
  type: TechArticle
- description: Học cách thêm một hyperlink comment trong tệp Word và xuất nó dưới
    dạng PDF annotation bằng Aspose.Words for .NET.
  name: Thêm Hyperlink Comment và Xuất dưới dạng PDF Annotation bằng Aspose.Words
    for .NET
  steps:
  - name: Tạo một đối tượng Document trống mới và một DocumentBuilder để làm việc
      với nó.
    text: Tạo một đối tượng Document trống mới và một DocumentBuilder để làm việc
      với nó.
  - name: Viết một dòng văn bản hiển thị sẽ chứa bình luận sắp tới.
    text: Viết một dòng văn bản hiển thị sẽ chứa bình luận sắp tới.
  - name: Tạo một Comment do Jane Doe viết và gắn nó vào đoạn văn đầu tiên của tài
      liệu.
    text: Tạo một Comment do Jane Doe viết và gắn nó vào đoạn văn đầu tiên của tài
      liệu.
  - name: Bên trong comment, thêm một đoạn văn và chèn một siêu liên kết màu xanh,
      gạch chân tới trang web Aspose.Words Library.
    text: Bên trong comment, thêm một đoạn văn và chèn một siêu liên kết màu xanh,
      gạch chân tới trang web Aspose.Words Library.
  - name: Cấu hình tài liệu để hiển thị comment dưới dạng chú thích PDF và làm mới
      bố cục.
    text: Cấu hình tài liệu để hiển thị comment dưới dạng chú thích PDF và làm mới
      bố cục.
  - name: Tạo một thư mục "Output" trong thư mục hiện tại để lưu PDF đã tạo.
    text: Tạo một thư mục "Output" trong thư mục hiện tại để lưu PDF đã tạo.
  - name: Lưu tài liệu đã chuẩn bị dưới dạng tệp PDF bằng cách sử dụng PdfSaveOptions.
    text: Lưu tài liệu đã chuẩn bị dưới dạng tệp PDF bằng cách sử dụng PdfSaveOptions.
  - name: Kiểm tra xem tệp PDF có tồn tại và chứa dữ liệu hay không, sau đó in kết
      quả ra console.
    text: Kiểm tra xem tệp PDF có tồn tại và chứa dữ liệu hay không, sau đó in kết
      quả ra console.
  type: HowTo
- questions:
  - answer: Tham số thứ ba của `InsertHyperlink` xác định liệu liên kết có được coi
      là một field hay không; đặt nó thành `false` sẽ chèn một siêu liên kết thuần
      túy hoạt động trong PDF annotation mà không cần mã field.
    question: Tham số thứ ba (`false`) trong `InsertHyperlink` kiểm soát gì?
  - answer: Đặt `myDocument.LayoutOptions.CommentDisplayMode` thành `CommentDisplayMode.ShowInBalloons`
      trước khi gọi `Save`; PDF sau đó sẽ chứa comment dưới dạng comment Word thông
      thường thay vì annotation.
    question: Làm sao để comment hiển thị dưới dạng bóng trong tài liệu Word thay
      vì PDF annotation?
  - answer: Có — mỗi `Comment` bạn gắn vào một đoạn văn có thể chứa lời gọi `InsertHyperlink`
      riêng, và tất cả các siêu liên kết sẽ được giữ lại dưới dạng các PDF annotation
      riêng biệt khi tài liệu được lưu.
    question: Nếu tôi thêm hơn một comment, mỗi siêu liên kết có hoạt động trong PDF
      đã xuất không?
  - answer: Mở PDF đã tạo, tìm chú thích comment (thường hiển thị dưới dạng biểu tượng
      ghi chú), nhấp vào để hiển thị văn bản comment, sau đó nhấp vào liên kết màu
      xanh gạch chân; nó sẽ mở URL mục tiêu trong trình duyệt web.
    question: Làm sao tôi kiểm tra rằng siêu liên kết trong comment thực sự hoạt động
      sau khi PDF được tạo?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Chèn Hyperlink Comment & Xuất ra PDF
og_description: Học cách nhúng một liên kết có thể nhấp vào trong một comment Word và chuyển nó thành PDF annotation.
og_image_alt: Hướng dẫn cách thêm một comment có siêu liên kết có thể nhấp vào vào tài liệu Word và xuất nó dưới dạng PDF annotation bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Hyperlink Comment và Xuất dưới dạng PDF Annotation bằng Aspose.Words
Trong hướng dẫn này, bạn sẽ thấy cách tạo tài liệu Word, chèn một comment chứa siêu liên kết có thể nhấp tới một trang web bên ngoài, cấu hình comment đó để hiển thị dưới dạng chú thích PDF, xuất tài liệu ra PDF và xác minh tệp PDF kết quả. Mã từng bước cho phép bạn thêm các comment phong phú, có liên kết và giữ chúng lại khi chuyển đổi sang PDF, giúp dễ dàng chia sẻ ghi chú tương tác với người đọc.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Tham số thứ ba (`false`) trong `InsertHyperlink` kiểm soát gì?**  
A: Tham số thứ ba của `InsertHyperlink` xác định liệu liên kết có được coi là một field hay không; đặt nó thành `false` sẽ chèn một siêu liên kết thuần túy hoạt động trong PDF annotation mà không cần mã field.

**Q: Làm sao để comment hiển thị dưới dạng bóng trong tài liệu Word thay vì PDF annotation?**  
A: Đặt `myDocument.LayoutOptions.CommentDisplayMode` thành `CommentDisplayMode.ShowInBalloons` trước khi gọi `Save`; PDF sau đó sẽ chứa comment dưới dạng comment Word thông thường thay vì annotation.

**Q: Nếu tôi thêm hơn một comment, mỗi siêu liên kết có hoạt động trong PDF đã xuất không?**  
A: Có — mỗi `Comment` bạn gắn vào một đoạn văn có thể chứa lời gọi `InsertHyperlink` riêng, và tất cả các siêu liên kết sẽ được giữ lại dưới dạng các PDF annotation riêng biệt khi tài liệu được lưu.

**Q: Làm sao tôi kiểm tra rằng siêu liên kết trong comment thực sự hoạt động sau khi PDF được tạo?**  
A: Mở PDF đã tạo, tìm chú thích comment (thường hiển thị dưới dạng biểu tượng ghi chú), nhấp vào để hiển thị văn bản comment, sau đó nhấp vào liên kết màu xanh gạch chân; nó sẽ mở URL mục tiêu trong trình duyệt web.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}