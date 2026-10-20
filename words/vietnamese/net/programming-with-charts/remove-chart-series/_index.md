---
title: Xóa một Chart Series khỏi Word Document bằng Aspose.Words for .NET
weight: 510
limit:
description: Tìm hiểu cách xóa một series dữ liệu cụ thể khỏi biểu đồ cột trong Word document bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tìm hiểu cách xóa một series dữ liệu cụ thể khỏi biểu đồ cột trong
    Word document bằng Aspose.Words for .NET.
  headline: Xóa một Chart Series khỏi Word Document bằng Aspose.Words for .NET
  type: TechArticle
- description: Tìm hiểu cách xóa một series dữ liệu cụ thể khỏi biểu đồ cột trong
    Word document bằng Aspose.Words for .NET.
  name: Xóa một Chart Series khỏi Word Document bằng Aspose.Words for .NET
  steps:
  - name: Tạo một Word Document mới và một DocumentBuilder liên kết với nó.
    text: Tạo một Word Document mới và một DocumentBuilder liên kết với nó.
  - name: Chèn một biểu đồ cột có kích thước 432×252 điểm và lấy đối tượng Chart để
      thao tác tiếp theo.
    text: Chèn một biểu đồ cột có kích thước 432×252 điểm và lấy đối tượng Chart để
      thao tác tiếp theo.
  - name: Xác định chỉ mục bắt đầu từ 0 của series cần xóa (series thứ hai).
    text: Xác định chỉ mục bắt đầu từ 0 của series cần xóa (series thứ hai).
  - name: Nếu chỉ mục hợp lệ, gọi RemoveAt trên bộ sưu tập Series của chart để xóa
      series đó.
    text: Nếu chỉ mục hợp lệ, gọi RemoveAt trên bộ sưu tập Series của chart để xóa
      series đó.
  - name: Lưu tài liệu đã cập nhật thành file .docx.
    text: Lưu tài liệu đã cập nhật thành file .docx.
  type: HowTo
- questions:
  - answer: Kiểm tra `if` (`targetSeriesIdx < columnChart.Series.Count`) sẽ thất bại,
      vì vậy `RemoveAt` không bao giờ được gọi và biểu đồ vẫn không thay đổi.
    question: Điều gì sẽ xảy ra nếu tôi truyền một chỉ mục bằng số lượng series trong
      biểu đồ?
  - answer: Có, sau khi thực hiện `columnChart.Series.RemoveAt`, chú giải được tạo
      lại để phản ánh các series còn lại, vì vậy mục đã xóa sẽ biến mất khỏi chú giải.
    question: Việc xóa một series có tự động cập nhật chú giải (legend) của biểu đồ
      không?
  - answer: Đoạn mã hoạt động cho bất kỳ loại biểu đồ nào hỗ trợ bộ sưu tập `Series`;
      chỉ cần thay đổi `ChartType.Column` thành loại mong muốn khi chèn biểu đồ.
    question: Tôi có thể dùng cùng đoạn mã để xóa một series khỏi biểu đồ đường hoặc
      biểu đồ tròn không?
  - answer: Biểu đồ không có series vẫn là một `Shape` hợp lệ và sẽ được lưu, nhưng
      nó sẽ hiển thị trống trong tài liệu kết quả.
    question: Nếu tôi xóa series duy nhất trong một biểu đồ, biểu đồ có vẫn được lưu
      đúng không?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Xóa một Chart Series trong Word Document
og_description: Hướng dẫn từng bước để loại bỏ một series dữ liệu khỏi biểu đồ Word bằng Aspose.Words for .NET.
og_image_alt: Hướng dẫn cách xóa một series dữ liệu cụ thể khỏi biểu đồ cột trong Word document bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Xóa một Chart Series khỏi Word Document bằng Aspose.Words
Hướng dẫn này chỉ cách tạo một Word document, thêm một biểu đồ cột bằng DocumentBuilder, và sau đó xóa một series dữ liệu cụ thể khỏi biểu đồ đó bằng phương thức ChartSeriesCollection.RemoveAt. Khi hoàn thành, bạn sẽ có một tài liệu đã lưu với series không mong muốn đã bị xóa, cho phép bạn kiểm soát chính xác nội dung biểu đồ trực tiếp từ mã .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Điều gì sẽ xảy ra nếu tôi truyền một chỉ mục bằng số lượng series trong biểu đồ?**  
A: Kiểm tra `if` (`targetSeriesIdx < columnChart.Series.Count`) sẽ thất bại, vì vậy `RemoveAt` không bao giờ được gọi và biểu đồ vẫn không thay đổi.

**Q: Việc xóa một series có tự động cập nhật chú giải (legend) của biểu đồ không?**  
A: Có, sau khi thực hiện `columnChart.Series.RemoveAt`, chú giải được tạo lại để phản ánh các series còn lại, vì vậy mục đã xóa sẽ biến mất khỏi chú giải.

**Q: Tôi có thể dùng cùng đoạn mã để xóa một series khỏi biểu đồ đường hoặc biểu đồ tròn không?**  
A: Đoạn mã hoạt động cho bất kỳ loại biểu đồ nào hỗ trợ bộ sưu tập `Series`; chỉ cần thay đổi `ChartType.Column` thành loại mong muốn khi chèn biểu đồ.

**Q: Nếu tôi xóa series duy nhất trong một biểu đồ, biểu đồ có vẫn được lưu đúng không?**  
A: Biểu đồ không có series vẫn là một `Shape` hợp lệ và sẽ được lưu, nhưng nó sẽ hiển thị trống trong tài liệu kết quả.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}