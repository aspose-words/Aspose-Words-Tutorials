---
title: Chèn trường TC vào tài liệu Word bằng Aspose.Words for .NET
weight: 110
limit:
description: Tìm hiểu cách chèn một trường TC với văn bản tùy chỉnh vào tài liệu Word bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn trường TC vào tài liệu Word bằng Aspose.Words
Hướng dẫn này cho thấy cách sử dụng Aspose.Words for .NET để chèn một trường TC (Table of Contents) vào tài liệu Word mới tạo. Bằng cách sử dụng DocumentBuilder, bạn có thể thêm một trường TC với văn bản mục tùy chỉnh, hữu ích cho việc xây dựng chỉ mục có thể tìm kiếm cho mục lục. Ví dụ cũng minh họa cách lưu tài liệu vào đĩa.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Dấu chuyển "\f t" trong mã trường TC có nghĩa là gì?**
A: Dấu chuyển "\f t" yêu cầu Word coi mục này là một mục bảng, khiến nó xuất hiện trong mục lục được tạo bằng dấu chuyển \f.

**Q: Làm thế nào để thay đổi văn bản hiển thị trong trường TC?**
A: Thay thế "Entry Text" trong lời gọi InsertField bằng bất kỳ chuỗi nào bạn muốn, ví dụ: builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Tôi có thể chèn nhiều trường TC trong cùng một tài liệu không?**
A: Có; chỉ cần gọi builder.InsertField với các văn bản mục khác nhau tại các vị trí mong muốn trước khi lưu tài liệu.

**Q: Mã này có hoạt động với các định dạng khác ngoài .docx, chẳng hạn .pdf không?**
A: Tài liệu được lưu dưới dạng .docx trong ví dụ, nhưng Aspose.Words có thể lưu sang các định dạng khác (ví dụ: .pdf) bằng cách thay đổi phần mở rộng tệp trong doc.Save và đảm bảo định dạng đầu ra tương ứng được hỗ trợ.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}