---
title: Chèn Ngắt Trang trong Tài liệu Word bằng Aspose.Words for .NET
weight: 110
limit:
description: Học cách thêm ngắt trang vào tệp Word bằng Aspose.Words for .NET sử dụng Document và DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Ngắt Trang trong Tài liệu Word bằng Aspose.Words
Trong hướng dẫn tương tác này, bạn sẽ học cách thêm ngắt trang vào tài liệu Word một cách lập trình bằng Aspose.Words for .NET. Bằng cách tạo một đối tượng Document và sử dụng DocumentBuilder, bạn có thể kiểm soát vị trí bắt đầu các trang mới, điều này rất quan trọng cho việc định dạng báo cáo, hoá đơn hoặc bất kỳ tài liệu đa phần nào. Hãy làm theo ví dụ từng bước để xem mã thực thi và xem trước tệp kết quả.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Tôi có thể dùng InsertBreak để thêm ngắt dòng hoặc ngắt phần thay vì ngắt trang không?**
A: Đúng, InsertBreak chấp nhận bất kỳ giá trị enum BreakType nào, chẳng hạn như BreakType.LineBreak hoặc BreakType.SectionBreakContinuous, để chèn ngắt tương ứng.

**Q: Tôi có cần gọi InsertBreak trước hay sau khi viết văn bản cho trang mới không?**
A: InsertBreak nên được gọi sau nội dung bạn muốn trên trang hiện tại; lệnh Writeln tiếp theo sẽ bắt đầu trên trang mới được tạo bởi ngắt.

**Q: Điều gì sẽ xảy ra nếu đường dẫn dataDir không kết thúc bằng dấu phân tách thư mục?**
A: Nếu dataDir thiếu dấu gạch chéo cuối cùng, tên tệp sẽ được nối trực tiếp (ví dụ: "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), có thể gây ra đường dẫn không hợp lệ; hãy đảm bảo đường dẫn kết thúc bằng "\\" hoặc sử dụng Path.Combine.

**Q: Tôi có thể tái sử dụng cùng một thể hiện DocumentBuilder để chèn nhiều ngắt trong toàn bộ tài liệu không?**
A: Đúng, cùng một DocumentBuilder có thể được sử dụng liên tục; mỗi lần gọi InsertBreak sẽ chèn một ngắt tại vị trí con trỏ hiện tại của builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}