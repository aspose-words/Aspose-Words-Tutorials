---
title: Chèn HTML căn chỉnh vào tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Học cách chèn HTML thô với căn chỉnh trái, giữa hoặc phải vào tài liệu Word bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn HTML căn chỉnh vào tài liệu Word bằng Aspose.Words
Bài hướng dẫn tương tác này cho thấy cách nhúng HTML thô vào tài liệu Word đồng thời kiểm soát căn chỉnh của nó—trái, giữa hoặc phải—bằng cách sử dụng Aspose.Words for .NET. Nhờ tận dụng Document và DocumentBuilder, bạn có thể chèn một chuỗi HTML và áp dụng căn chỉnh đoạn mong muốn chỉ trong vài dòng mã. Ví dụ này rất phù hợp khi bạn cần giữ nguyên định dạng HTML và đặt nội dung một cách chính xác trong tài liệu của mình.

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

**Q: Điều gì sẽ xảy ra nếu chuỗi HTML truyền vào DocumentBuilder.InsertHtml chứa các thẻ mà Aspose.Words không hỗ trợ, chẳng hạn như <script> hoặc <iframe>?**
A: Các thẻ không được hỗ trợ sẽ bị bỏ qua; Aspose.Words chỉ phân tích một phần con của HTML mà nó có thể hiển thị, vì vậy <script>, <iframe> và các phần tử tương tự sẽ bị loại bỏ trong khi phần còn lại của nội dung được chèn.

**Q: Các kiểu CSS nội tuyến (ví dụ: <span style=\"color:red;\">) có được giữ lại khi sử dụng InsertHtml không?**
A: Có, InsertHtml tôn trọng nhiều thuộc tính CSS nội tuyến như color, font‑size và background, chuyển chúng thành định dạng Word tương ứng.

**Q: InsertHtml có tự động tạo một đoạn mới cho các phần tử cấp khối như <div> hoặc <h1> không?**
A: Các phần tử cấp khối được ánh xạ thành các đoạn trong Word, vì vậy mỗi <div>, <p>, <h1>, v.v., sẽ trở thành một đoạn riêng trong tài liệu.

**Q: Làm thế nào để chèn HTML vào một vị trí cụ thể trong tài liệu hiện có thay vì ở đầu?**
A: Di chuyển con trỏ DocumentBuilder đến nút mong muốn (ví dụ: builder.MoveToDocumentEnd() hoặc builder.MoveToParagraph(index)) trước khi gọi InsertHtml; HTML sẽ được chèn tại vị trí con trỏ hiện tại.

**Q: Nếu tài liệu đã chứa văn bản, việc gọi InsertHtml có ghi đè nội dung hiện có không?**
A: Không, InsertHtml chèn HTML đã phân tích vào vị trí hiện tại của builder mà không xóa các nút hiện có, trừ khi bạn tự ý di chuyển con trỏ vào hoặc xóa các nút đó trước đó.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}