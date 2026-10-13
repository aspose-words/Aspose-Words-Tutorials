---
title: Định dạng trục Y phụ thành Tiền tệ trong biểu đồ Word bằng Aspose.Words for .NET
weight: 710
limit:
description: Học cách thêm và định dạng trục Y phụ dưới dạng tiền tệ trong biểu đồ đường Word bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Học cách thêm và định dạng trục Y phụ dưới dạng tiền tệ trong biểu
    đồ đường Word bằng Aspose.Words for .NET.
  headline: Định dạng trục Y phụ thành Tiền tệ trong biểu đồ Word bằng Aspose.Words
    for .NET
  type: TechArticle
- description: Học cách thêm và định dạng trục Y phụ dưới dạng tiền tệ trong biểu
    đồ đường Word bằng Aspose.Words for .NET.
  name: Định dạng trục Y phụ thành Tiền tệ trong biểu đồ Word bằng Aspose.Words for
    .NET
  steps:
  - name: Tạo một tài liệu Word trống mới và một DocumentBuilder để chỉnh sửa nó.
    text: Tạo một tài liệu Word trống mới và một DocumentBuilder để chỉnh sửa nó.
  - name: Chèn một biểu đồ đường có kích thước 450×250 điểm vào tài liệu và lấy đối
      tượng Chart của nó.
    text: Chèn một biểu đồ đường có kích thước 450×250 điểm vào tài liệu và lấy đối
      tượng Chart của nó.
  - name: Xóa chuỗi placeholder mặc định mà Aspose thêm vào biểu đồ mới.
    text: Xóa chuỗi placeholder mặc định mà Aspose thêm vào biểu đồ mới.
  - name: Xác định các nhãn quý và thêm một chuỗi dữ liệu chính với các giá trị mẫu
      vào biểu đồ.
    text: Xác định các nhãn quý và thêm một chuỗi dữ liệu chính với các giá trị mẫu
      vào biểu đồ.
  - name: Tạo một nhóm chuỗi phụ loại Line và gán nó cho nhóm trục phụ.
    text: Tạo một nhóm chuỗi phụ loại Line và gán nó cho nhóm trục phụ.
  - name: Ẩn trục X phụ để chỉ trục Y phụ hiển thị.
    text: Ẩn trục X phụ để chỉ trục Y phụ hiển thị.
  - name: Hiển thị tiêu đề trục Y phụ và đặt văn bản của nó thành "Sales (USD)".
    text: Hiển thị tiêu đề trục Y phụ và đặt văn bản của nó thành "Sales (USD)".
  - name: Đặt định dạng số của trục Y phụ thành mẫu tiền tệ với hai chữ số thập phân
      và tách nó khỏi định dạng nguồn.
    text: Đặt định dạng số của trục Y phụ thành mẫu tiền tệ với hai chữ số thập phân
      và tách nó khỏi định dạng nguồn.
  - name: Thêm một chuỗi phụ trợ vào nhóm phụ, cung cấp dữ liệu sẽ được vẽ trên trục
      Y phụ.
    text: Thêm một chuỗi phụ trợ vào nhóm phụ, cung cấp dữ liệu sẽ được vẽ trên trục
      Y phụ.
  - name: Lưu tài liệu đã hoàn thiện vào tệp có tên ProfitChart.docx trong thư mục
      hiện tại.
    text: Lưu tài liệu đã hoàn thiện vào tệp có tên ProfitChart.docx trong thư mục
      hiện tại.
  type: HowTo
- questions:
  - answer: Biểu đồ sẽ giữ lại chuỗi placeholder mặc định mà Aspose.Words chèn vào,
      vì vậy "Main Series" tùy chỉnh của bạn sẽ xuất hiện cùng với các điểm dữ liệu
      không mong muốn.
    question: Điều gì sẽ xảy ra nếu tôi bỏ qua lệnh `lineChart.Series.Clear()`?
  - answer: Đặt `secondarySeriesGroup.AxisX.Hidden = false;` (hoặc đơn giản là bỏ
      qua dòng đặt nó thành `true`).
    question: Làm sao tôi có thể hiển thị trục X phụ thay vì ẩn nó?
  - answer: Đúng – thay đổi chuỗi định dạng, ví dụ `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` cho euro hoặc điều chỉnh mẫu cho phù hợp với địa phương
      của bạn.
    question: Tôi có thể sử dụng ký hiệu tiền tệ hoặc định dạng khác cho trục Y phụ
      không?
  - answer: Khi `IsLinkedToSource` là true, trục sẽ kế thừa định dạng số từ nguồn
      dữ liệu gốc, ghi đè bất kỳ `FormatCode` tùy chỉnh nào; đặt nó thành false buộc
      biểu đồ sử dụng định dạng bạn chỉ định.
    question: Tại sao tôi cần đặt `IsLinkedToSource = false` khi áp dụng định dạng
      số tùy chỉnh?
  - answer: Đúng, gán `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (hoặc
      `Right` cho mặc định) để điều khiển trục được vẽ ở phía nào.
    question: Có thể di chuyển trục Y phụ sang phía bên trái của biểu đồ không?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Định dạng trục phụ của Chart thành Tiền tệ
og_description: Học cách thêm trục Y phụ vào biểu đồ đường Word và định dạng nó dưới dạng tiền tệ với hai chữ số thập phân.
og_image_alt: Ảnh chụp màn hình hiển thị biểu đồ đường Word với trục Y phụ được định dạng dưới dạng tiền tệ bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng trục Y phụ thành Tiền tệ trong biểu đồ Word bằng Aspose.Words
Trong hướng dẫn này, bạn sẽ thấy cách tạo tài liệu Word, chèn biểu đồ đường, thêm trục Y phụ, định dạng trục đó dưới dạng tiền tệ với hai chữ số thập phân, và liên kết một chuỗi dữ liệu phụ với nó bằng cách sử dụng Aspose.Words for .NET. Định dạng trục phụ dưới dạng tiền tệ giúp bạn trình bày rõ ràng dữ liệu tài chính cùng với chuỗi chính. Hãy làm theo mã từng bước để xem biểu đồ được hiển thị trực tiếp trong tài liệu được tạo.

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

**Q: Điều gì sẽ xảy ra nếu tôi bỏ qua lệnh `lineChart.Series.Clear()`?**  
A: Biểu đồ sẽ giữ lại chuỗi placeholder mặc định mà Aspose.Words chèn vào, vì vậy "Main Series" tùy chỉnh của bạn sẽ xuất hiện cùng với các điểm dữ liệu không mong muốn.

**Q: Làm sao tôi có thể hiển thị trục X phụ thay vì ẩn nó?**  
A: Đặt `secondarySeriesGroup.AxisX.Hidden = false;` (hoặc đơn giản là bỏ qua dòng đặt nó thành `true`).

**Q: Tôi có thể sử dụng ký hiệu tiền tệ hoặc định dạng khác cho trục Y phụ không?**  
A: Đúng – thay đổi chuỗi định dạng, ví dụ `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` cho euro hoặc điều chỉnh mẫu cho phù hợp với địa phương của bạn.

**Q: Tại sao tôi cần đặt `IsLinkedToSource = false` khi áp dụng định dạng số tùy chỉnh?**  
A: Khi `IsLinkedToSource` là true, trục sẽ kế thừa định dạng số từ nguồn dữ liệu gốc, ghi đè bất kỳ `FormatCode` tùy chỉnh nào; đặt nó thành false buộc biểu đồ sử dụng định dạng bạn chỉ định.

**Q: Có thể di chuyển trục Y phụ sang phía bên trái của biểu đồ không?**  
A: Đúng, gán `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (hoặc `Right` cho mặc định) để điều khiển trục được vẽ ở phía nào.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}