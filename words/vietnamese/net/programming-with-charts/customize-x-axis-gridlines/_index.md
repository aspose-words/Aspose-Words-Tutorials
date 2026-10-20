---
title: Tùy chỉnh các đường lưới trục X trong biểu đồ cột bằng Aspose.Words for .NET
weight: 610
limit:
description: Học cách thêm và tùy chỉnh màu cho các đường lưới chính của trục X trong biểu đồ cột Word bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Học cách thêm và tùy chỉnh màu cho các đường lưới chính của trục X
    trong biểu đồ cột Word bằng Aspose.Words for .NET.
  headline: Tùy chỉnh các đường lưới trục X trong biểu đồ cột bằng Aspose.Words for
    .NET
  type: TechArticle
- description: Học cách thêm và tùy chỉnh màu cho các đường lưới chính của trục X
    trong biểu đồ cột Word bằng Aspose.Words for .NET.
  name: Tùy chỉnh các đường lưới trục X trong biểu đồ cột bằng Aspose.Words for .NET
  steps:
  - name: Tạo một tài liệu Word mới và một DocumentBuilder để chỉnh sửa nó.
    text: Tạo một tài liệu Word mới và một DocumentBuilder để chỉnh sửa nó.
  - name: Chèn một biểu đồ cột kích thước 432×252 vào tài liệu và lấy đối tượng Chart
      của nó.
    text: Chèn một biểu đồ cột kích thước 432×252 vào tài liệu và lấy đối tượng Chart
      của nó.
  - name: Xóa series mặc định và thêm một series tùy chỉnh với ba nhóm và các giá
      trị.
    text: Xóa series mặc định và thêm một series tùy chỉnh với ba nhóm và các giá
      trị.
  - name: Lấy tham chiếu tới trục ngang (X) chính của biểu đồ.
    text: Lấy tham chiếu tới trục ngang (X) chính của biểu đồ.
  - name: Bật hiển thị các đường lưới chính trên trục X chính.
    text: Bật hiển thị các đường lưới chính trên trục X chính.
  - name: Đặt màu của các đường lưới thành màu xanh da trời và độ dày của chúng là
      2 điểm.
    text: Đặt màu của các đường lưới thành màu xanh da trời và độ dày của chúng là
      2 điểm.
  - name: Lưu tài liệu dưới dạng tệp .docx.
    text: Lưu tài liệu dưới dạng tệp .docx.
  type: HowTo
- questions:
  - answer: 'Đặt thuộc tính trục tương tự thành false: `horizontalAxis.HasMajorGridlines
      = false;` sẽ chuyển đổi trạng thái hiển thị của các đường lưới chính trục X.'
    question: Làm sao tôi có thể ẩn lại các đường lưới chính sau khi đã bật chúng?
  - answer: Không, các cài đặt `Format.Stroke` chỉ áp dụng cho trục bạn chỉnh sửa;
      để tạo kiểu cho các đường lưới trục Y, bạn phải điều chỉnh `chart.AxisY.Format.Stroke`
      riêng biệt.
    question: Việc thay đổi `horizontalAxis.Format.Stroke.Color` có ảnh hưởng đến
      các đường lưới trục Y không?
  - answer: Sử dụng `horizontalAxis.Format.Stroke.Weight` và gán một giá trị kiểu
      double (ví dụ, `0.5`) để làm các đường lưới mỏng hơn.
    question: Thuộc tính nào kiểm soát độ dày của các đường lưới chính trục X?
  - answer: Có, đặt `horizontalAxis.Format.Stroke.DashStyle` thành một giá trị enum
      `DashStyle` như `DashStyle.Dash` hoặc `DashStyle.Dot`.
    question: Tôi có thể thay đổi mẫu gạch ngang của các đường lưới chính trục X không?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Tạo kiểu cho các đường lưới trục X trong biểu đồ cột Word
og_description: Bật và tùy chỉnh màu cho các đường lưới trục X chính của biểu đồ Word bằng Aspose.Words for .NET.
og_image_alt: Hướng dẫn hiển thị tài liệu Word có biểu đồ cột, trong đó các đường lưới chính của trục X chính được làm nổi bật bằng màu tùy chỉnh bằng Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tùy chỉnh các đường lưới trục X trong biểu đồ cột bằng Aspose.Words
Trong hướng dẫn này, bạn sẽ học cách tạo tài liệu Word, chèn biểu đồ cột, thay thế dữ liệu mặc định của nó, và sau đó bật các đường lưới chính trên trục X chính. Bạn cũng sẽ thấy cách thay đổi màu đường của các đường lưới để phù hợp với thiết kế của mình. Hãy làm theo mã từng bước để kiểm soát chính xác việc hiển thị và tạo kiểu cho các đường lưới trục X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: Làm sao tôi có thể ẩn lại các đường lưới chính sau khi đã bật chúng?**  
A: Đặt thuộc tính trục tương tự thành false: `horizontalAxis.HasMajorGridlines = false;` sẽ chuyển đổi trạng thái hiển thị của các đường lưới chính trục X.

**Q: Việc thay đổi `horizontalAxis.Format.Stroke.Color` có ảnh hưởng đến các đường lưới trục Y không?**  
A: Không, các cài đặt `Format.Stroke` chỉ áp dụng cho trục bạn chỉnh sửa; để tạo kiểu cho các đường lưới trục Y, bạn phải điều chỉnh `chart.AxisY.Format.Stroke` riêng biệt.

**Q: Thuộc tính nào kiểm soát độ dày của các đường lưới chính trục X?**  
A: Sử dụng `horizontalAxis.Format.Stroke.Weight` và gán một giá trị kiểu double (ví dụ, `0.5`) để làm các đường lưới mỏng hơn.

**Q: Tôi có thể thay đổi mẫu gạch ngang của các đường lưới chính trục X không?**  
A: Có, đặt `horizontalAxis.Format.Stroke.DashStyle` thành một giá trị enum `DashStyle` như `DashStyle.Dash` hoặc `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}