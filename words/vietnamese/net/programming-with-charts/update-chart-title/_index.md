---
title: Cập nhật tiêu đề biểu đồ và bật/tắt hiển thị legend trong Word bằng Aspose.Words for .NET
weight: 810
limit:
description: Học cách thay đổi tiêu đề biểu đồ và kiểm soát hiển thị legend trong tài liệu Word bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Học cách thay đổi tiêu đề biểu đồ và kiểm soát hiển thị legend trong
    tài liệu Word bằng Aspose.Words for .NET.
  headline: Cập nhật tiêu đề biểu đồ và bật/tắt hiển thị legend trong Word bằng Aspose.Words
    for .NET
  type: TechArticle
- description: Học cách thay đổi tiêu đề biểu đồ và kiểm soát hiển thị legend trong
    tài liệu Word bằng Aspose.Words for .NET.
  name: Cập nhật tiêu đề biểu đồ và bật/tắt hiển thị legend trong Word bằng Aspose.Words
    for .NET
  steps:
  - name: Xác định tiêu đề biểu đồ do người dùng cung cấp và việc có hiển thị chú
      giải hay không.
    text: Xác định tiêu đề biểu đồ do người dùng cung cấp và việc có hiển thị chú
      giải hay không.
  - name: Tạo một tài liệu Word mới và một DocumentBuilder để thêm nội dung.
    text: Tạo một tài liệu Word mới và một DocumentBuilder để thêm nội dung.
  - name: Chèn một biểu đồ cột kích thước 432 × 252 pt vào tài liệu và xác minh shape
      thực sự chứa một chart.
    text: Chèn một biểu đồ cột kích thước 432 × 252 pt vào tài liệu và xác minh shape
      thực sự chứa một chart.
  - name: Lấy đối tượng chart, đặt văn bản tiêu đề của nó thành giá trị do người dùng
      cung cấp, và đảm bảo tiêu đề được hiển thị.
    text: Lấy đối tượng chart, đặt văn bản tiêu đề của nó thành giá trị do người dùng
      cung cấp, và đảm bảo tiêu đề được hiển thị.
  - name: 'Cấu hình legend: hiển thị ở phía bên phải nếu yêu cầu, nếu không thì ẩn,
      và cho phép nó overlay lên vùng vẽ.'
    text: 'Cấu hình legend: hiển thị ở phía bên phải nếu yêu cầu, nếu không thì ẩn,
      và cho phép nó overlay lên vùng vẽ.'
  - name: Lưu tài liệu đã chỉnh sửa vào đĩa với tên CustomChart.docx.
    text: Lưu tài liệu đã chỉnh sửa vào đĩa với tên CustomChart.docx.
  type: HowTo
- questions:
  - answer: Khi `displayLegend` là `true`, mã sẽ đặt `chartLegend.Position` thành
      `LegendPosition.Right`, làm cho legend hiển thị ở phía bên phải của vùng vẽ;
      thuộc tính `Overlay` vẫn là `true`, vì vậy legend có thể overlay lên biểu đồ
      để tiết kiệm không gian.
    question: Việc đặt `displayLegend` thành `true` thay đổi gì trong biểu đồ được
      tạo?
  - answer: Đặt `chartTitle.Show = false` (hoặc đơn giản không đặt `Show` thành `true`)
      sau khi gán `chartTitle.Text`; tiêu đề sẽ không được hiển thị trong tài liệu
      Word.
    question: Làm sao để ẩn tiêu đề biểu đồ nếu người dùng không cung cấp?
  - answer: Có—`InsertChart` trả về một `Shape` mà nên chứa một chart, nhưng việc
      xác minh `HasChart` đảm bảo shape thực sự chứa một đối tượng `Chart`; nếu không,
      mã sẽ ném ra `InvalidOperationException`.
    question: Có cần kiểm tra `chartContainer.HasChart` sau khi gọi `InsertChart`
      không?
  - answer: 'Chắc chắn; gán bất kỳ giá trị nào từ enum `LegendPosition` (ví dụ: `LegendPosition.Top`,
      `LegendPosition.Bottom`, `LegendPosition.Left`) cho `chartLegend.Position` để
      di chuyển legend theo nhu cầu.'
    question: Tôi có thể đặt legend ở vị trí khác ngoài phía bên phải không?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Thay đổi tiêu đề biểu đồ & legend trong Word
og_description: Học cách đặt tiêu đề biểu đồ tùy chỉnh và kiểm soát hiển thị legend trong tài liệu Word bằng Aspose.Words for .NET.
og_image_alt: Hướng dẫn hiển thị mã cập nhật tiêu đề biểu đồ và bật/tắt legend trong tài liệu Word bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cập nhật tiêu đề biểu đồ và bật/tắt hiển thị legend trong Word bằng Aspose.Words
Hướng dẫn này chỉ cách chỉnh sửa biểu đồ trong tài liệu Word một cách lập trình bằng Aspose.Words for .NET. Bạn sẽ học cách chèn biểu đồ cột, thay thế tiêu đề của nó bằng văn bản do người dùng cung cấp, và kiểm soát việc hiển thị và overlay của legend dựa trên tùy chọn của người dùng. Những bước này cho phép bạn tùy chỉnh cách trình bày biểu đồ một cách động mà không cần chỉnh sửa thủ công.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Việc đặt `displayLegend` thành `true` thay đổi gì trong biểu đồ được tạo?**  
A: Khi `displayLegend` là `true`, mã sẽ đặt `chartLegend.Position` thành `LegendPosition.Right`, làm cho legend hiển thị ở phía bên phải của vùng vẽ; thuộc tính `Overlay` vẫn là `true`, vì vậy legend có thể overlay lên biểu đồ để tiết kiệm không gian.

**Q: Làm sao để ẩn tiêu đề biểu đồ nếu người dùng không cung cấp?**  
A: Đặt `chartTitle.Show = false` (hoặc đơn giản không đặt `Show` thành `true`) sau khi gán `chartTitle.Text`; tiêu đề sẽ không được hiển thị trong tài liệu Word.

**Q: Có cần kiểm tra `chartContainer.HasChart` sau khi gọi `InsertChart` không?**  
A: Có—`InsertChart` trả về một `Shape` mà nên chứa một chart, nhưng việc xác minh `HasChart` đảm bảo shape thực sự chứa một đối tượng `Chart`; nếu không, mã sẽ ném ra `InvalidOperationException`.

**Q: Tôi có thể đặt legend ở vị trí khác ngoài phía bên phải không?**  
A: Chắc chắn; gán bất kỳ giá trị nào từ enum `LegendPosition` (ví dụ: `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) cho `chartLegend.Position` để di chuyển legend theo nhu cầu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}