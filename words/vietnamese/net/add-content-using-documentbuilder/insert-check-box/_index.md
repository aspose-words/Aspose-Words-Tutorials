---
title: Thêm Trường Biểu Mẫu Hộp Kiểm vào Tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Tìm hiểu cách thêm một trường biểu mẫu hộp kiểm vào tài liệu Word mới một cách lập trình bằng Aspose.Words for .NET và lưu tệp.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Trường Biểu Mẫu Hộp Kiểm vào Tài liệu Word bằng Aspose.Words
Hướng dẫn này chỉ cách tạo một tài liệu Word mới và sử dụng DocumentBuilder của Aspose.Words for .NET để chèn một trường biểu mẫu hộp kiểm. Bằng cách làm theo các bước, bạn sẽ thấy mã chính xác cần thiết để thêm yếu tố tương tác và sau đó lưu tài liệu vào tệp. Đây là cách nhanh chóng để tạo các tệp Word có biểu mẫu đơn giản một cách lập trình.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Tham số thứ tư (0) trong InsertCheckBox đại diện cho gì?**
A: Nó xác định kích thước hiển thị của hộp kiểm tính bằng điểm; giá trị 0 cho Aspose.Words biết sử dụng kích thước mặc định.

**Q: Tôi có thể chèn nhiều hơn một hộp kiểm với cùng một tên không?**
A: Không – mỗi tên trường biểu mẫu phải là duy nhất; cố gắng chèn một hộp kiểm khác có tên "CheckBox" sẽ gây ra ArgumentException.

**Q: Làm thế nào để thêm một hộp kiểm vào tài liệu hiện có thay vì tạo mới?**
A: Đầu tiên tải tài liệu (ví dụ, `Document doc = new Document("Existing.docx");`) rồi tạo một DocumentBuilder cho tài liệu đó và gọi `InsertCheckBox` tại vị trí con trỏ mong muốn.

**Q: Làm sao tôi có thể đọc trạng thái của hộp kiểm đã chèn sau khi tài liệu được lưu?**
A: Lấy trường biểu mẫu bằng `doc.Range.FormFields["CheckBox"]` và kiểm tra thuộc tính `Checked` của nó để xem nó có được chọn hay không.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}