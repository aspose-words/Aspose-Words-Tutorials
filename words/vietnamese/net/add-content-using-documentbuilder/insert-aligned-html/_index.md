---
title: Chèn HTML căn chỉnh vào tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Tìm hiểu cách chèn HTML với căn chỉnh cụ thể vào tài liệu Word bằng Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn HTML căn chỉnh vào tài liệu Word bằng Aspose.Words
Hướng dẫn này trình bày cách sử dụng DocumentBuilder của Aspose.Words for .NET để nhúng mã HTML vào tài liệu Word và kiểm soát việc căn chỉnh của nó. Bạn sẽ thấy cách chèn HTML, thiết lập căn chỉnh đoạn văn (trái, giữa hoặc phải), và sau đó lưu tài liệu kết quả. Ví dụ này phù hợp cho các nhà phát triển cần giữ nguyên định dạng kiểu web khi tạo tệp Word một cách tự động.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Liệu InsertHtml có thể được sử dụng để thêm HTML vào tài liệu Word hiện có thay vì tạo tài liệu mới không?**
A: Có. Tạo một Document từ tệp hiện có, đặt con trỏ DocumentBuilder ở vị trí bạn muốn chèn HTML (ví dụ, bằng cách sử dụng builder.MoveToDocumentEnd()), sau đó gọi builder.InsertHtml với mã của bạn.

**Q: Các thuộc tính HTML nào được InsertHtml tôn trọng để căn chỉnh?**
A: InsertHtml tôn trọng thuộc tính "align" trên các phần tử cấp khối như <p>, <div> và các thẻ tiêu đề, áp dụng căn chỉnh đoạn văn tương ứng trong tài liệu Word kết quả.

**Q: Điều gì sẽ xảy ra nếu chuỗi HTML chứa các thẻ hoặc CSS không được hỗ trợ?**
A: Các thẻ không được hỗ trợ sẽ bị bỏ qua và nội dung bên trong của chúng sẽ được chèn dưới dạng văn bản thuần; các kiểu CSS nội tuyến mà Aspose.Words không nhận diện cũng bị bỏ qua, vì vậy chỉ phần phụ thuộc HTML được hỗ trợ sẽ được hiển thị.

**Q: Tôi có cần đóng DocumentBuilder trước khi lưu tài liệu không?**
A: Không cần đóng một cách rõ ràng; sau khi chèn HTML, bạn có thể trực tiếp gọi doc.Save với tên tệp và định dạng mong muốn, và các tài nguyên của builder sẽ được giải phóng tự động.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}