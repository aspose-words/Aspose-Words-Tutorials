---
title: Chèn mã vạch DataMatrix vào tài liệu Word bằng Aspose.Words for .NET
weight: 210
limit:
description: Thêm mã vạch DataMatrix vào tài liệu Word một cách lập trình với Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Thêm mã vạch DataMatrix vào tài liệu Word một cách lập trình với Aspose.Words
    for .NET.
  headline: Chèn mã vạch DataMatrix vào tài liệu Word bằng Aspose.Words for .NET
  type: TechArticle
- description: Thêm mã vạch DataMatrix vào tài liệu Word một cách lập trình với Aspose.Words
    for .NET.
  name: Chèn mã vạch DataMatrix vào tài liệu Word bằng Aspose.Words for .NET
  steps:
  - name: Tạo một tài liệu Word trống mới và một DocumentBuilder để chỉnh sửa nó.
    text: Tạo một tài liệu Word trống mới và một DocumentBuilder để chỉnh sửa nó.
  - name: Chèn một trường DISPLAYBARCODE tại vị trí con trỏ hiện tại, điều này sẽ
      thêm một placeholder trường vào tài liệu.
    text: Chèn một trường DISPLAYBARCODE tại vị trí con trỏ hiện tại, điều này sẽ
      thêm một placeholder trường vào tài liệu.
  - name: Đặt BarcodeType của trường thành DataMatrix và cung cấp chuỗi dữ liệu để
      mã hoá.
    text: Đặt BarcodeType của trường thành DataMatrix và cung cấp chuỗi dữ liệu để
      mã hoá.
  - name: Tùy chọn, định nghĩa màu nền và màu chữ của mã vạch.
    text: Tùy chọn, định nghĩa màu nền và màu chữ của mã vạch.
  - name: Gọi UpdateFields trên tài liệu để tạo hình ảnh mã vạch bên trong trường.
    text: Gọi UpdateFields trên tài liệu để tạo hình ảnh mã vạch bên trong trường.
  - name: Lưu tài liệu thành tệp .docx.
    text: Lưu tài liệu thành tệp .docx.
  type: HowTo
- questions:
  - answer: Trường sẽ được chèn, nhưng `document.UpdateFields()` sẽ để mã vạch trống
      và Aspose.Words sẽ ném ra một `FieldException` chỉ ra loại mã vạch không hợp
      lệ.
    question: Điều gì sẽ xảy ra nếu tôi gán một giá trị không được hỗ trợ cho `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` tạo hình ảnh mã vạch, vì vậy bạn có thể chèn nhiều đối
      tượng `FieldDisplayBarcode` và gọi `document.UpdateFields()` một lần duy nhất
      ở cuối để tạo chúng tất cả.'
    question: Tôi có cần gọi `document.UpdateFields()` sau mỗi lần chèn mã vạch không,
      hay có thể cập nhật một lần sau khi đã thêm tất cả các trường?
  - answer: Cả hai thuộc tính đều yêu cầu một chuỗi RGB thập lục phân có tiền tố `0x`
      (ví dụ, \"0xFF0000\" cho màu đỏ); bất kỳ định dạng nào khác sẽ bị bỏ qua và
      màu mặc định sẽ được sử dụng.
    question: Chuỗi màu cho `BackgroundColor` và `ForegroundColor` nên ở định dạng
      nào?
  - answer: Có — chỉ cần đặt `displayBarcodeField.BarcodeValue` thành một chuỗi mới
      và gọi lại `document.UpdateFields()` để làm mới hình ảnh đã tạo.
    question: Tôi có thể thay đổi nội dung mã vạch sau khi trường đã được chèn không?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Chèn mã vạch DataMatrix bằng Aspose.Words
og_description: Tìm hiểu cách thêm mã vạch DataMatrix vào tệp Word chỉ trong vài dòng mã .NET.
og_image_alt: Hướng dẫn cách chèn và tạo mã vạch DataMatrix trong tài liệu Word bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn mã vạch DataMatrix vào tài liệu Word bằng Aspose.Words
Với Aspose.Words for .NET, bạn có thể thêm mã vạch DataMatrix vào tài liệu Word một cách lập trình. Hướng dẫn này cho thấy cách tạo một tài liệu mới, chèn trường DISPLAYBARCODE, đặt loại của nó thành DataMatrix, và tạo hình ảnh mã vạch bằng các lớp Document và DocumentBuilder. Thực hiện các bước để tạo mã vạch có thể in trực tiếp trong tệp .docx của bạn.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Điều gì sẽ xảy ra nếu tôi gán một giá trị không được hỗ trợ cho `displayBarcodeField.BarcodeType`?**  
A: Trường sẽ được chèn, nhưng `document.UpdateFields()` sẽ để mã vạch trống và Aspose.Words sẽ ném ra một `FieldException` chỉ ra loại mã vạch không hợp lệ.

**Q: Tôi có cần gọi `document.UpdateFields()` sau mỗi lần chèn mã vạch không, hay có thể cập nhật một lần sau khi đã thêm tất cả các trường?**  
A: `UpdateFields()` tạo hình ảnh mã vạch, vì vậy bạn có thể chèn nhiều đối tượng `FieldDisplayBarcode` và gọi `document.UpdateFields()` một lần duy nhất ở cuối để tạo chúng tất cả.

**Q: Chuỗi màu cho `BackgroundColor` và `ForegroundColor` nên ở định dạng nào?**  
A: Cả hai thuộc tính đều yêu cầu một chuỗi RGB thập lục phân có tiền tố `0x` (ví dụ, \"0xFF0000\" cho màu đỏ); bất kỳ định dạng nào khác sẽ bị bỏ qua và màu mặc định sẽ được sử dụng.

**Q: Tôi có thể thay đổi nội dung mã vạch sau khi trường đã được chèn không?**  
A: Có — chỉ cần đặt `displayBarcodeField.BarcodeValue` thành một chuỗi mới và gọi lại `document.UpdateFields()` để làm mới hình ảnh đã tạo.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}