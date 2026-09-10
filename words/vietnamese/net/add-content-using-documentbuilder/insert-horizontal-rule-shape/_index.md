---
title: Chèn Hình Dạng Quy Tắc Ngang trong Tài Liệu Word bằng Aspose.Words for .NET
weight: 110
limit:
description: Hướng dẫn chi tiết từng bước để chèn một hình dạng quy tắc ngang vào tài liệu Word với Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Hình Dạng Quy Tắc Ngang trong Tài Liệu Word bằng Aspose.Words
Tìm hiểu cách sử dụng Aspose.Words for .NET để chèn một hình dạng quy tắc ngang vào tài liệu Word. Hướng dẫn này sẽ chỉ cho bạn cách tạo một tài liệu mới, thêm một dòng văn bản, đặt hình dạng quy tắc ngang bằng DocumentBuilder, và lưu tệp. Quy tắc ngang cung cấp một ranh giới trực quan đơn giản cho nội dung của bạn.

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

**Q: Tôi có thể thay đổi giao diện (màu sắc, độ dày) của quy tắc ngang được chèn bằng DocumentBuilder.InsertHorizontalRule() không?**
A: InsertHorizontalRule tạo một hình dạng đường ngang tích hợp sẵn với định dạng mặc định; để sửa đổi giao diện của nó, bạn phải lấy đối tượng Shape đã chèn (builder.CurrentParagraph.LastChild) và điều chỉnh các thuộc tính LineFormat.

**Q: Điều gì sẽ xảy ra nếu tôi gọi InsertHorizontalRule() sau một đoạn văn đã kết thúc bằng ngắt dòng?**
A: Phương thức này chèn quy tắc như một đoạn riêng, vì vậy bất kỳ ngắt dòng nào trước đó chỉ tạo một đoạn trống trước quy tắc; quy tắc vẫn sẽ hiển thị trên một dòng riêng.

**Q: Có thể chèn hơn một quy tắc ngang trong cùng một tài liệu bằng DocumentBuilder không?**
A: Có, mỗi lần gọi builder.InsertHorizontalRule() sẽ thêm một hình dạng quy tắc ngang mới tại vị trí con trỏ hiện tại, cho phép có nhiều quy tắc trong toàn bộ tài liệu.

**Q: InsertHorizontalRule() có hoạt động khi lưu tài liệu sang các định dạng khác ngoài DOCX, chẳng hạn như PDF không?**
A: Quy tắc ngang được lưu dưới dạng shape trong mô hình tài liệu, vì vậy khi bạn lưu sang PDF, XPS hoặc các định dạng hỗ trợ khác, quy tắc sẽ được hiển thị đúng trong đầu ra.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}