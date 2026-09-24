---
title: Chèn hình dạng đường kẻ ngang trong tài liệu Word bằng Aspose.Words for .NET
weight: 110
limit:
description: Học cách thêm một hình dạng đường kẻ ngang vào tài liệu Word với Aspose.Words for .NET bằng cách sử dụng DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn hình dạng đường kẻ ngang trong tài liệu Word bằng Aspose.Words
Trong hướng dẫn này, bạn sẽ học cách chèn một hình dạng đường kẻ ngang vào tài liệu Word một cách lập trình bằng Aspose.Words for .NET. Sử dụng các lớp Document và DocumentBuilder, chúng ta tạo một tài liệu mới, thêm một đoạn văn bản, và sau đó đặt một hình dạng đường ngang tại vị trí mong muốn. Đường kẻ ngang cung cấp một ranh giới trực quan có thể hữu ích cho việc ngắt phần hoặc nhấn mạnh trực quan.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: `builder.InsertHorizontalRule()` đặt dòng ở vị trí chính xác nào trong tài liệu?**  
A: `InsertHorizontalRule` chèn một hình dạng đường kẻ ngang tại vị trí con trỏ hiện tại của `DocumentBuilder`; nếu bạn muốn nó trên một dòng riêng, hãy gọi `builder.Writeln()` trước khi chèn.

**Q: Tôi có thể thay đổi độ dày, màu sắc hoặc chiều rộng của đường kẻ ngang đã chèn không?**  
A: `InsertHorizontalRule` thêm một đường kẻ có kiểu mặc định và không cung cấp các tùy chọn định dạng; để tùy chỉnh các thuộc tính đó, bạn cần chèn một `Shape` một cách thủ công (ví dụ, `builder.InsertShape(ShapeType.HorizontalLine)`) và sau đó đặt các thuộc tính `LineFormat` của nó.

**Q: Có thể thêm hơn một đường kẻ ngang trong cùng một tài liệu không?**  
A: Có—chỉ cần gọi `builder.InsertHorizontalRule()` mỗi khi bạn cần một đường kẻ mới; mỗi lần gọi sẽ tạo một hình dạng riêng tại vị trí hiện tại của builder.

**Q: Đường kẻ ngang có hiển thị khi tệp .docx đã lưu được mở trong Microsoft Word không?**  
A: Chắc chắn; đường kẻ được lưu dưới dạng một hình dạng trong tệp .docx, vì vậy Word hiển thị nó chính xác như trong tài liệu được tạo.

**Q: Điều gì sẽ xảy ra nếu thư mục `dataDir` không tồn tại trước khi gọi `doc.Save(...)`?**  
A: `doc.Save` sẽ ném ra một `DirectoryNotFoundException`; hãy đảm bảo thư mục đích tồn tại hoặc tạo nó bằng mã trước khi lưu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}