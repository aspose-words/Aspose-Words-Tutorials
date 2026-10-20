---
title: Đặt Nhãn Dữ liệu Đồng nhất trong Biểu đồ Cột bằng Aspose.Words for .NET
weight: 110
limit:
description: Học cách tạo biểu đồ cột Word và áp dụng kích thước phông chữ và màu sắc nhãn dữ liệu đồng nhất cho tất cả các chuỗi bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Học cách tạo biểu đồ cột Word và áp dụng kích thước phông chữ và màu
    sắc nhãn dữ liệu đồng nhất cho tất cả các chuỗi bằng Aspose.Words for .NET.
  headline: Đặt Nhãn Dữ liệu Đồng nhất trong Biểu đồ Cột bằng Aspose.Words for .NET
  type: TechArticle
- description: Học cách tạo biểu đồ cột Word và áp dụng kích thước phông chữ và màu
    sắc nhãn dữ liệu đồng nhất cho tất cả các chuỗi bằng Aspose.Words for .NET.
  name: Đặt Nhãn Dữ liệu Đồng nhất trong Biểu đồ Cột bằng Aspose.Words for .NET
  steps:
  - name: Tạo một tài liệu Word mới trống và một DocumentBuilder để chỉnh sửa nó.
    text: Tạo một tài liệu Word mới trống và một DocumentBuilder để chỉnh sửa nó.
  - name: Chèn một biểu đồ cột kích thước 500×300 vào tài liệu và lấy đối tượng Chart
      của nó.
    text: Chèn một biểu đồ cột kích thước 500×300 vào tài liệu và lấy đối tượng Chart
      của nó.
  - name: Xóa chuỗi mẫu mặc định mà Aspose.Words thêm vào biểu đồ mới.
    text: Xóa chuỗi mẫu mặc định mà Aspose.Words thêm vào biểu đồ mới.
  - name: Xác định nhãn danh mục và thêm hai chuỗi dữ liệu (Item Alpha và Item Beta)
      cùng giá trị của chúng vào biểu đồ.
    text: Xác định nhãn danh mục và thêm hai chuỗi dữ liệu (Item Alpha và Item Beta)
      cùng giá trị của chúng vào biểu đồ.
  - name: Đặt kích thước phông chữ và màu sắc cơ bản sẽ được áp dụng cho tất cả các
      nhãn dữ liệu.
    text: Đặt kích thước phông chữ và màu sắc cơ bản sẽ được áp dụng cho tất cả các
      nhãn dữ liệu.
  - name: Bật nhãn dữ liệu cho mỗi chuỗi, hiển thị giá trị số và áp dụng kích thước
      phông chữ và màu sắc đã định trước.
    text: Bật nhãn dữ liệu cho mỗi chuỗi, hiển thị giá trị số và áp dụng kích thước
      phông chữ và màu sắc đã định trước.
  - name: Lưu tài liệu dưới dạng tệp .docx.
    text: Lưu tài liệu dưới dạng tệp .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` tạo một biểu đồ với chuỗi mẫu mặc định; việc xóa nó loại
      bỏ phần giữ chỗ đó để biểu đồ chỉ hiển thị các chuỗi bạn thêm (`Item Alpha`
      và `Item Beta`).'
    question: Tại sao tôi cần gọi `chart.Series.Clear()` trước khi thêm chuỗi của
      mình?
  - answer: Thay thế `Color.White` bằng bất kỳ giá trị `System.Drawing.Color` nào,
      ví dụ `Color.Black` hoặc `Color.FromArgb(255, 30, 144, 255)`; màu mới sẽ được
      áp dụng qua `series.DataLabels.Font.Color` trong vòng lặp.
    question: Làm thế nào để thay đổi màu nhãn dữ liệu thành màu khác ngoài trắng?
  - answer: Các nhãn dữ liệu sẽ bị ẩn, vì vậy các thiết lập phông chữ bạn áp dụng
      sẽ không hiển thị; bạn phải giữ `HasDataLabels` ở trạng thái `true` để các nhãn
      (và kiểu dáng của chúng) xuất hiện.
    question: Điều gì sẽ xảy ra nếu tôi đặt `series.HasDataLabels = false` sau khi
      đã cấu hình kích thước phông chữ và màu?
  - answer: Có — mỗi `ChartSeries` có đối tượng `DataLabels` riêng, vì vậy bất kỳ
      chuỗi nào được thêm sau vòng lặp ban đầu cũng phải có `HasDataLabels`, `ShowValue`
      và các thuộc tính phông chữ được thiết lập, có thể bằng cách lặp lại hoặc bằng
      cách tách kiểu dáng ra thành một phương thức trợ giúp.
    question: Tôi có cần lặp lại qua các chuỗi nữa nếu sau này tôi thêm một chuỗi
      khác trong mã không?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Áp dụng Nhãn Dữ liệu Đồng nhất cho Biểu đồ Word
og_description: Nhanh chóng đặt cùng một kích thước phông chữ và màu cho mọi nhãn biểu đồ bằng Aspose.Words for .NET.
og_image_alt: Hướng dẫn hiển thị tài liệu Word có biểu đồ cột, trong đó tất cả các nhãn dữ liệu chia sẻ cùng một kích thước phông chữ và màu, được tạo bằng Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Đặt Nhãn Dữ liệu Đồng nhất trong Biểu đồ Cột bằng Aspose.Words
Hướng dẫn này cho thấy cách tạo tài liệu Word, chèn biểu đồ cột và thêm chuỗi dữ liệu tùy chỉnh bằng Aspose.Words for .NET. Sau đó nó trình bày cách định nghĩa kích thước phông chữ và màu sắc mặc định cho nhãn dữ liệu sao cho mỗi chuỗi trong biểu đồ hiển thị nhãn giống nhau. Bằng cách áp dụng một kiểu duy nhất, bạn đảm bảo giao diện trực quan nhất quán trên toàn bộ biểu đồ.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Tại sao tôi cần gọi `chart.Series.Clear()` trước khi thêm chuỗi của mình?**  
A: `InsertChart` tạo một biểu đồ với chuỗi mẫu mặc định; việc xóa nó loại bỏ phần giữ chỗ đó để biểu đồ chỉ hiển thị các chuỗi bạn thêm (`Item Alpha` và `Item Beta`).

**Q: Làm thế nào để thay đổi màu nhãn dữ liệu thành màu khác ngoài trắng?**  
A: Thay thế `Color.White` bằng bất kỳ giá trị `System.Drawing.Color` nào, ví dụ `Color.Black` hoặc `Color.FromArgb(255, 30, 144, 255)`; màu mới sẽ được áp dụng qua `series.DataLabels.Font.Color` trong vòng lặp.

**Q: Điều gì sẽ xảy ra nếu tôi đặt `series.HasDataLabels = false` sau khi đã cấu hình kích thước phông chữ và màu?**  
A: Các nhãn dữ liệu sẽ bị ẩn, vì vậy các thiết lập phông chữ bạn áp dụng sẽ không hiển thị; bạn phải giữ `HasDataLabels` ở trạng thái `true` để các nhãn (và kiểu dáng của chúng) xuất hiện.

**Q: Tôi có cần lặp lại qua các chuỗi nữa nếu sau này tôi thêm một chuỗi khác trong mã không?**  
A: Có — mỗi `ChartSeries` có đối tượng `DataLabels` riêng, vì vậy bất kỳ chuỗi nào được thêm sau vòng lặp ban đầu cũng phải có `HasDataLabels`, `ShowValue` và các thuộc tính phông chữ được thiết lập, có thể bằng cách lặp lại hoặc bằng cách tách kiểu dáng ra thành một phương thức trợ giúp.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}