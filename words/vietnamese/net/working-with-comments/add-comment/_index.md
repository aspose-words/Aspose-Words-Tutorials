---
title: Chèn một Comment vào Đoạn Văn Cụ Thể trong Tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Hướng dẫn chi tiết từng bước để thêm bình luận của tác giả vào một đoạn văn được chọn trong tài liệu Word và lưu nó dưới dạng DOCX bằng Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Hướng dẫn chi tiết từng bước để thêm bình luận của tác giả vào một
    đoạn văn được chọn trong tài liệu Word và lưu nó dưới dạng DOCX bằng Aspose.Words
    for .NET.
  headline: Chèn một Comment vào Đoạn Văn Cụ Thể trong Tài liệu Word bằng Aspose.Words
    for .NET
  type: TechArticle
- description: Hướng dẫn chi tiết từng bước để thêm bình luận của tác giả vào một
    đoạn văn được chọn trong tài liệu Word và lưu nó dưới dạng DOCX bằng Aspose.Words
    for .NET.
  name: Chèn một Comment vào Đoạn Văn Cụ Thể trong Tài liệu Word bằng Aspose.Words
    for .NET
  steps:
  - name: Khởi tạo một Document mới và một DocumentBuilder để bắt đầu xây dựng tệp
      Word.
    text: Khởi tạo một Document mới và một DocumentBuilder để bắt đầu xây dựng tệp
      Word.
  - name: Sử dụng DocumentBuilder.Writeln để thêm ba đoạn văn bản riêng biệt vào tài
      liệu.
    text: Sử dụng DocumentBuilder.Writeln để thêm ba đoạn văn bản riêng biệt vào tài
      liệu.
  - name: Lấy đoạn văn thứ hai một cách an toàn, nếu tài liệu có ít hơn hai đoạn thì
      sẽ quay lại đoạn đầu tiên.
    text: Lấy đoạn văn thứ hai một cách an toàn, nếu tài liệu có ít hơn hai đoạn thì
      sẽ quay lại đoạn đầu tiên.
  - name: Tạo một Comment với thông tin tác giả, đặt nội dung của nó, và gắn vào đoạn
      văn đã chọn.
    text: Tạo một Comment với thông tin tác giả, đặt nội dung của nó, và gắn vào đoạn
      văn đã chọn.
  - name: Lưu tài liệu đã chỉnh sửa dưới dạng tệp DOCX có tên 'sample.docx' trong
      thư mục hiện tại.
    text: Lưu tài liệu đã chỉnh sửa dưới dạng tệp DOCX có tên 'sample.docx' trong
      thư mục hiện tại.
  type: HowTo
- questions:
  - answer: Khối `if` sẽ quay lại đoạn đầu tiên (`paraList[0]`) khi `paraList.Count`
      ít hơn 2, vì vậy bình luận sẽ được gắn vào đoạn duy nhất đó thay vì đoạn thứ
      hai không tồn tại.
    question: Mã sẽ làm gì nếu tài liệu chỉ chứa một đoạn văn?
  - answer: Chúng được truyền vào hàm khởi tạo `Comment` như là đối số thứ hai và
      thứ ba – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – trong đó
      "Jordan" là tên tác giả và "JH" là chữ viết tắt.
    question: Tên tác giả và chữ viết tắt của bình luận được đặt như thế nào trong
      ví dụ này?
  - answer: Trong đoạn mã này, bình luận được liên kết với toàn bộ `Paragraph` thông
      qua `AppendChild`, nhưng để bình luận một phạm vi văn bản, bạn cần tạo một `CommentRangeStart`
      và `CommentRangeEnd` quanh các node `Run` mong muốn và sau đó chèn node `Comment`
      giữa chúng.
    question: Tôi có thể gắn bình luận vào một đoạn văn bản cụ thể thay vì toàn bộ
      đoạn không?
  - answer: '`AppendChild` thêm node `Comment` vào bộ sưu tập con của đoạn, và Aspose.Words
      tự động tạo các dấu bắt đầu/kết thúc bình luận cần thiết khi tài liệu được lưu.'
    question: Tôi có cần chèn thủ công các dấu hiệu bình luận không, hay `AppendChild`
      tự động xử lý việc này?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Chèn một bình luận vào đoạn văn Word
og_description: Thêm bình luận của tác giả vào một đoạn văn cụ thể và xuất tệp dưới dạng DOCX với Aspose.Words.
og_image_alt: Hướng dẫn cách thêm bình luận vào một đoạn văn trong tài liệu Word bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn một Comment vào Đoạn Văn Cụ Thể trong Tài liệu Word bằng Aspose.Words
Với Aspose.Words for .NET, bạn có thể thêm bình luận vào các tệp Word một cách lập trình. Hướng dẫn này hướng qua việc tạo một tài liệu mới, chèn ba đoạn văn, xác định đoạn thứ hai, và gắn một bình luận bao gồm thông tin tác giả và ngày tháng. Cuối cùng, tài liệu được lưu dưới dạng tệp DOCX giữ lại bình luận.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: Mã sẽ làm gì nếu tài liệu chỉ chứa một đoạn văn?**  
A: Khối `if` sẽ quay lại đoạn đầu tiên (`paraList[0]`) khi `paraList.Count` ít hơn 2, vì vậy bình luận sẽ được gắn vào đoạn duy nhất đó thay vì đoạn thứ hai không tồn tại.

**Q: Tên tác giả và chữ viết tắt của bình luận được đặt như thế nào trong ví dụ này?**  
A: Chúng được truyền vào hàm khởi tạo `Comment` như là đối số thứ hai và thứ ba – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – trong đó "Jordan" là tên tác giả và "JH" là chữ viết tắt.

**Q: Tôi có thể gắn bình luận vào một đoạn văn bản cụ thể thay vì toàn bộ đoạn không?**  
A: Trong đoạn mã này, bình luận được liên kết với toàn bộ `Paragraph` thông qua `AppendChild`, nhưng để bình luận một phạm vi văn bản, bạn cần tạo một `CommentRangeStart` và `CommentRangeEnd` quanh các node `Run` mong muốn và sau đó chèn node `Comment` giữa chúng.

**Q: Tôi có cần chèn thủ công các dấu hiệu bình luận không, hay `AppendChild` tự động xử lý việc này?**  
A: `AppendChild` thêm node `Comment` vào bộ sưu tập con của đoạn, và Aspose.Words tự động tạo các dấu bắt đầu/kết thúc bình luận cần thiết khi tài liệu được lưu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}