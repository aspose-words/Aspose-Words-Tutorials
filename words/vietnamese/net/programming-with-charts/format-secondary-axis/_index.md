---
title: Định dạng Trục X Phụ và Đặt Đơn vị Hiển thị thành Hàng nghìn trong Biểu đồ Đường Word bằng Aspose.Words cho .NET
weight: 710
limit:
description: Tạo một biểu đồ đường Word, thêm trục X phụ, đặt đơn vị hiển thị của nó thành hàng nghìn, và áp dụng định dạng số tùy chỉnh với Aspose.Words cho .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tạo một biểu đồ đường Word, thêm trục X phụ, đặt đơn vị hiển thị của
    nó thành hàng nghìn, và áp dụng định dạng số tùy chỉnh với Aspose.Words cho .NET.
  headline: Định dạng Trục X Phụ và Đặt Đơn vị Hiển thị thành Hàng nghìn trong Biểu
    đồ Đường Word bằng Aspose.Words cho .NET
  type: TechArticle
- description: Tạo một biểu đồ đường Word, thêm trục X phụ, đặt đơn vị hiển thị của
    nó thành hàng nghìn, và áp dụng định dạng số tùy chỉnh với Aspose.Words cho .NET.
  name: Định dạng Trục X Phụ và Đặt Đơn vị Hiển thị thành Hàng nghìn trong Biểu đồ
    Đường Word bằng Aspose.Words cho .NET
  steps:
  - name: Tạo một Document mới và một DocumentBuilder để bắt đầu xây dựng tệp Word.
    text: Tạo một Document mới và một DocumentBuilder để bắt đầu xây dựng tệp Word.
  - name: Chèn một biểu đồ đường có kích thước 500×300 vào tài liệu và lấy đối tượng
      Chart.
    text: Chèn một biểu đồ đường có kích thước 500×300 vào tài liệu và lấy đối tượng
      Chart.
  - name: Xóa series demo mặc định mà Aspose.Words tự động thêm.
    text: Xóa series demo mặc định mà Aspose.Words tự động thêm.
  - name: Xác định một mảng các nhãn danh mục sẽ được sử dụng cho trục X.
    text: Xác định một mảng các nhãn danh mục sẽ được sử dụng cho trục X.
  - name: Thêm series dữ liệu chính có tên "Main Data" bằng cách sử dụng các nhãn
      và giá trị.
    text: Thêm series dữ liệu chính có tên "Main Data" bằng cách sử dụng các nhãn
      và giá trị.
  - name: Tạo một nhóm series phụ loại Line và gán nó cho nhóm trục phụ.
    text: Tạo một nhóm series phụ loại Line và gán nó cho nhóm trục phụ.
  - name: Đặt đơn vị hiển thị của trục X phụ thành hàng nghìn để các giá trị hiển
      thị dưới dạng K.
    text: Đặt đơn vị hiển thị của trục X phụ thành hàng nghìn để các giá trị hiển
      thị dưới dạng K.
  - name: Áp dụng định dạng số tùy chỉnh "#,##0.0" cho các nhãn tick của trục X phụ.
    text: Áp dụng định dạng số tùy chỉnh "#,##0.0" cho các nhãn tick của trục X phụ.
  - name: Tùy chọn, thêm một series dữ liệu phụ trợ vào nhóm phụ.
    text: Tùy chọn, thêm một series dữ liệu phụ trợ vào nhóm phụ.
  - name: Lưu tài liệu thành tệp .docx.
    text: Lưu tài liệu thành tệp .docx.
  type: HowTo
- questions:
  - answer: Không – các cài đặt `AxisX` thuộc về `ChartSeriesGroup`, vì vậy bạn có
      thể đặt `secondaryGroup.AxisX.DisplayUnit.Unit` và `secondaryGroup.AxisX.NumberFormat.FormatCode`
      trước hoặc sau khi thêm series; cấu hình sẽ áp dụng cho trục của nhóm dù thế
      nào.
    question: Tôi có phải thêm series phụ trước khi đặt đơn vị hiển thị và định dạng
      số cho trục X phụ không?
  - answer: Có – gán bất kỳ giá trị `AxisBuiltInUnit` nào, ví dụ `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` để hiển thị giá trị trục dưới dạng triệu thay vì
      hàng nghìn.
    question: Tôi có thể sử dụng một đơn vị tích hợp khác, chẳng hạn như triệu, cho
      trục X phụ không?
  - answer: Không – mã định dạng chỉ được áp dụng cho trục bạn chỉnh sửa (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      vì vậy trục X chính giữ nguyên định dạng mặc định.
    question: Định dạng tùy chỉnh "#,##0.0" có ảnh hưởng đến nhãn trục X chính không?
  - answer: Biểu đồ sẽ chứa series demo mặc định cùng với các series bạn thêm, có
      thể dẫn đến các đường thừa và danh mục không khớp; việc xóa bộ sưu tập đảm bảo
      chỉ có dữ liệu bạn muốn hiển thị.
    question: Điều gì sẽ xảy ra nếu tôi quên xóa series demo bằng `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Định dạng Trục X Phụ và Đặt Đơn vị thành Hàng nghìn
og_description: Thêm trục X phụ vào biểu đồ đường Word và định dạng các nhãn của nó dưới dạng hàng nghìn với mẫu tùy chỉnh.
og_image_alt: Hướng dẫn cách thêm trục X phụ vào biểu đồ đường Word và định dạng các nhãn để hiển thị đơn vị hàng nghìn bằng Aspose.Words cho .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng Trục X Phụ và Đặt Đơn vị Hiển thị thành Hàng nghìn trong Biểu đồ Đường Word bằng Aspose.Words cho .NET
Hướng dẫn này sẽ đưa bạn qua quá trình tạo một tài liệu Word chứa biểu đồ đường, thêm trục X phụ, và cấu hình trục đó để hiển thị giá trị dưới dạng hàng nghìn. Bạn cũng sẽ học cách áp dụng định dạng số tùy chỉnh cho nhãn trục phụ, cho phép bạn kiểm soát chính xác cách dữ liệu được trình bày. Thực hiện các bước để cải thiện khả năng đọc của các biểu đồ đa trục trong báo cáo Word của bạn.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Tôi có phải thêm series phụ trước khi đặt đơn vị hiển thị và định dạng số cho trục X phụ không?**  
A: Không – các cài đặt `AxisX` thuộc về `ChartSeriesGroup`, vì vậy bạn có thể đặt `secondaryGroup.AxisX.DisplayUnit.Unit` và `secondaryGroup.AxisX.NumberFormat.FormatCode` trước hoặc sau khi thêm series; cấu hình sẽ áp dụng cho trục của nhóm dù thế nào.

**Q: Tôi có thể sử dụng một đơn vị tích hợp khác, chẳng hạn như triệu, cho trục X phụ không?**  
A: Có – gán bất kỳ giá trị `AxisBuiltInUnit` nào, ví dụ `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` để hiển thị giá trị trục dưới dạng triệu thay vì hàng nghìn.

**Q: Định dạng tùy chỉnh "#,##0.0" có ảnh hưởng đến nhãn trục X chính không?**  
A: Không – mã định dạng chỉ được áp dụng cho trục bạn chỉnh sửa (`secondaryGroup.AxisX.NumberFormat.FormatCode`), vì vậy trục X chính giữ nguyên định dạng mặc định.

**Q: Điều gì sẽ xảy ra nếu tôi quên xóa series demo bằng `lineChart.Series.Clear();`?**  
A: Biểu đồ sẽ chứa series demo mặc định cùng với các series bạn thêm, có thể dẫn đến các đường thừa và danh mục không khớp; việc xóa bộ sưu tập đảm bảo chỉ có dữ liệu bạn muốn hiển thị.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}