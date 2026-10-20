---
title: Ẩn viền vùng vẽ trong biểu đồ cột bằng Aspose.Words for .NET
weight: 410
limit:
description: Học cách ẩn viền vùng vẽ của biểu đồ trong khi giữ các đường trục hiển thị trên biểu đồ cột Word bằng Aspose.Words for .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Học cách ẩn viền vùng vẽ của biểu đồ trong khi giữ các đường trục hiển
    thị trên biểu đồ cột Word bằng Aspose.Words for .NET.
  headline: Ẩn viền vùng vẽ trong biểu đồ cột bằng Aspose.Words for .NET
  type: TechArticle
- description: Học cách ẩn viền vùng vẽ của biểu đồ trong khi giữ các đường trục hiển
    thị trên biểu đồ cột Word bằng Aspose.Words for .NET.
  name: Ẩn viền vùng vẽ trong biểu đồ cột bằng Aspose.Words for .NET
  steps:
  - name: Tạo một tài liệu Word trống mới và một DocumentBuilder để chỉnh sửa nó.
    text: Tạo một tài liệu Word trống mới và một DocumentBuilder để chỉnh sửa nó.
  - name: Chèn một biểu đồ cột kích thước 432×252 vào tài liệu và lấy đối tượng Chart
      của nó.
    text: Chèn một biểu đồ cột kích thước 432×252 vào tài liệu và lấy đối tượng Chart
      của nó.
  - name: Xóa mọi series hiện có, định nghĩa ba nhãn danh mục, và thêm một series
      với các giá trị mẫu vào biểu đồ.
    text: Xóa mọi series hiện có, định nghĩa ba nhãn danh mục, và thêm một series
      với các giá trị mẫu vào biểu đồ.
  - name: Đặt trọng lượng stroke của vùng vẽ thành zero, loại bỏ viền của nó trong
      khi giữ các đường trục vẫn hiển thị.
    text: Đặt trọng lượng stroke của vùng vẽ thành zero, loại bỏ viền của nó trong
      khi giữ các đường trục vẫn hiển thị.
  - name: Lưu tài liệu đã chỉnh sửa thành tệp .docx.
    text: Lưu tài liệu đã chỉnh sửa thành tệp .docx.
  type: HowTo
- questions:
  - answer: '`Thuộc tính `Stroke` thuộc về định dạng tổng thể của đối tượng `Chart`,
      nó vẽ viền hình chữ nhật quanh vùng vẽ; các đường trục là các đối tượng `Axis`
      riêng biệt và không bị ảnh hưởng bởi cài đặt `Stroke` của biểu đồ.'
    question: Tại sao việc đặt `columnChart.Format.Stroke.Weight = 0` lại loại bỏ
      viền vùng vẽ nhưng vẫn giữ các đường trục hiển thị?
  - answer: Không, thuộc tính `Stroke` điều khiển toàn bộ viền vùng vẽ như một hình
      chữ nhật duy nhất, vì vậy không thể ẩn các viền một phần qua Aspose.Words; bạn
      cần phủ lên các hình dạng tùy chỉnh hoặc chỉnh sửa biểu đồ thủ công.
    question: 'Tôi có thể ẩn chỉ một phía của viền vùng vẽ (ví dụ: phía trái) trong
      khi giữ ba phía còn lại không?'
  - answer: Có, thuộc tính `Stroke` độc lập với `ChartType`, vì vậy việc đặt `Weight`
      thành 0 sẽ loại bỏ viền vùng vẽ cho Line, Pie hoặc bất kỳ loại biểu đồ nào khác
      được hỗ trợ.
    question: Nếu tôi thay đổi loại biểu đồ thành Line hoặc Pie, `columnChart.Format.Stroke.Weight
      = 0` vẫn sẽ ẩn viền vùng vẽ chứ?
  - answer: Không cần làm mới thêm; việc xóa series và thêm series mới sẽ cập nhật
      biểu đồ nội bộ, và `wordDoc.Save(...)` sẽ ghi trạng thái hiện tại vào tệp .docx.
    question: Sau khi gọi `columnChart.Series.Clear()`, tôi có cần làm mới biểu đồ
      trước khi lưu tài liệu không?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Ẩn viền vùng vẽ trong biểu đồ cột Word
og_description: Xóa viền vùng vẽ trong khi giữ các đường trục hiển thị trên biểu đồ cột Word bằng Aspose.Words for .NET.
og_image_alt: Hướng dẫn hiển thị tài liệu Word có biểu đồ cột, trong đó viền vùng vẽ bị ẩn nhưng các đường trục vẫn hiển thị, sử dụng Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ẩn viền vùng vẽ trong biểu đồ cột bằng Aspose.Words
Trong hướng dẫn này, bạn sẽ học cách tạo tài liệu Word, chèn biểu đồ cột, điền dữ liệu mẫu, và sau đó ẩn viền vùng vẽ của biểu đồ trong khi giữ các đường trục hiển thị. Mã lệnh từng bước minh họa mỗi thao tác và kết thúc bằng việc lưu tài liệu, để bạn có thể xem kết quả ngay lập tức.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Tại sao việc đặt `columnChart.Format.Stroke.Weight = 0` lại loại bỏ viền vùng vẽ nhưng vẫn giữ các đường trục hiển thị?**  
A: `Thuộc tính `Stroke` thuộc về định dạng tổng thể của đối tượng `Chart`, nó vẽ viền hình chữ nhật quanh vùng vẽ; các đường trục là các đối tượng `Axis` riêng biệt và không bị ảnh hưởng bởi cài đặt `Stroke` của biểu đồ.

**Q: Tôi có thể ẩn chỉ một phía của viền vùng vẽ (ví dụ: phía trái) trong khi giữ ba phía còn lại không?**  
A: Không, thuộc tính `Stroke` điều khiển toàn bộ viền vùng vẽ như một hình chữ nhật duy nhất, vì vậy không thể ẩn các viền một phần qua Aspose.Words; bạn cần phủ lên các hình dạng tùy chỉnh hoặc chỉnh sửa biểu đồ thủ công.

**Q: Nếu tôi thay đổi loại biểu đồ thành Line hoặc Pie, `columnChart.Format.Stroke.Weight = 0` vẫn sẽ ẩn viền vùng vẽ chứ?**  
A: Có, thuộc tính `Stroke` độc lập với `ChartType`, vì vậy việc đặt `Weight` thành 0 sẽ loại bỏ viền vùng vẽ cho Line, Pie hoặc bất kỳ loại biểu đồ nào khác được hỗ trợ.

**Q: Sau khi gọi `columnChart.Series.Clear()`, tôi có cần làm mới biểu đồ trước khi lưu tài liệu không?**  
A: Không cần làm mới thêm; việc xóa series và thêm series mới sẽ cập nhật biểu đồ nội bộ, và `wordDoc.Save(...)` sẽ ghi trạng thái hiện tại vào tệp .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}