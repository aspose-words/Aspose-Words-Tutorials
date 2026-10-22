---
title: Chèn Biểu Đồ Cột Tùy Chỉnh vào Tài Liệu Word bằng Aspose.Words for .NET
weight: 310
limit:
description: Tạo một tệp Word, chèn biểu đồ cột, thay thế dữ liệu của nó bằng một mảng tùy chỉnh, thêm tiêu đề và lưu—tất cả đều bằng Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tạo một tệp Word, chèn biểu đồ cột, thay thế dữ liệu của nó bằng một
    mảng tùy chỉnh, thêm tiêu đề và lưu—tất cả đều bằng Aspose.Words for .NET.
  headline: Chèn Biểu Đồ Cột Tùy Chỉnh vào Tài Liệu Word bằng Aspose.Words for .NET
  type: TechArticle
- description: Tạo một tệp Word, chèn biểu đồ cột, thay thế dữ liệu của nó bằng một
    mảng tùy chỉnh, thêm tiêu đề và lưu—tất cả đều bằng Aspose.Words for .NET.
  name: Chèn Biểu Đồ Cột Tùy Chỉnh vào Tài Liệu Word bằng Aspose.Words for .NET
  steps:
  - name: Tạo một Document mới và một DocumentBuilder gắn vào nó.
    text: Tạo một Document mới và một DocumentBuilder gắn vào nó.
  - name: Chèn một biểu đồ cột có kích thước 432x252 điểm vào tài liệu và lấy đối
      tượng Chart của nó.
    text: Chèn một biểu đồ cột có kích thước 432x252 điểm vào tài liệu và lấy đối
      tượng Chart của nó.
  - name: Xóa các series mẫu được tạo tự động khỏi biểu đồ.
    text: Xóa các series mẫu được tạo tự động khỏi biểu đồ.
  - name: Xác định nhãn danh mục trục X và các mục chú giải cho mỗi series.
    text: Xác định nhãn danh mục trục X và các mục chú giải cho mỗi series.
  - name: Tạo một mảng hai chiều, trong đó mỗi hàng chứa các giá trị cho một series.
    text: Tạo một mảng hai chiều, trong đó mỗi hàng chứa các giá trị cho một series.
  - name: Lặp qua từng series, trích xuất các giá trị hàng tương ứng từ ma trận, và
      thêm series vào biểu đồ cùng với mục chú giải và nhãn trục X tương ứng.
    text: Lặp qua từng series, trích xuất các giá trị hàng tương ứng từ ma trận, và
      thêm series vào biểu đồ cùng với mục chú giải và nhãn trục X tương ứng.
  - name: Đặt văn bản tiêu đề biểu đồ thành 'Half‑Yearly Revenue' và hiển thị nó.
    text: Đặt văn bản tiêu đề biểu đồ thành 'Half‑Yearly Revenue' và hiển thị nó.
  - name: Lưu tài liệu chứa biểu đồ tùy chỉnh thành tệp .docx.
    text: Lưu tài liệu chứa biểu đồ tùy chỉnh thành tệp .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` yêu cầu độ dài mảng giá trị phải bằng số nhãn trục
      X, và bạn phải thêm đúng một series cho mỗi mục chú giải; nếu không khớp sẽ
      ném ra `ArgumentException` khi chạy.'
    question: Nếu các hàng hoặc cột trong `dataMatrix` không khớp với độ dài của `legendEntries`
      hoặc `xLabels` thì sao?
  - answer: Có—thay `ChartType.Column` trong `docBuilder.InsertChart` bằng bất kỳ
      `ChartType` nào khác (ví dụ, `ChartType.Line`) và các lời gọi `Series.Add` tiếp
      theo sẽ điền dữ liệu cho biểu đồ mới theo cùng cách.
    question: Tôi có thể sử dụng loại biểu đồ khác, chẳng hạn biểu đồ đường, với cùng
      logic điền dữ liệu không?
  - answer: Điều chỉnh các thuộc tính `Width` và `Height` của `Shape` trả về bởi `InsertChart`
      (ví dụ, `chartContainer.Width = 500; chartContainer.Height = 300;`).
    question: Làm sao để thay đổi kích thước của biểu đồ sau khi đã chèn?
  - answer: Đặt `chartObj.Series[i].HasDataLabel = true;` cho mỗi series sau khi thêm,
      hoặc lặp qua `chartObj.Series` và bật `HasDataLabel` để hiển thị các giá trị
      trên biểu đồ.
    question: Có cách nhanh để hiển thị nhãn dữ liệu trên mỗi cột của biểu đồ không?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Thêm Biểu Đồ Cột Tùy Chỉnh vào Tài Liệu Word
og_description: Thay đổi dữ liệu mặc định của biểu đồ bằng mảng của bạn và đặt tiêu đề trong vài giây.
og_image_alt: Ảnh chụp màn hình hiển thị tài liệu Word với biểu đồ cột tùy chỉnh được tạo bằng Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Biểu Đồ Cột Tùy Chỉnh vào Tài Liệu Word bằng Aspose.Words
Hướng dẫn này sẽ dẫn bạn qua quá trình tạo tài liệu Word, chèn biểu đồ cột, xóa dữ liệu mặc định, và điền biểu đồ bằng các giá trị tùy chỉnh từ một mảng hai chiều—gán mỗi hàng cho một series và mỗi cột cho một danh mục. Bạn cũng sẽ thấy cách thêm tiêu đề biểu đồ trước khi lưu tệp. Thực hiện các bước để tạo một biểu đồ hoàn toàn tùy chỉnh trực tiếp trong tệp Word của bạn.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Nếu các hàng hoặc cột trong `dataMatrix` không khớp với độ dài của `legendEntries` hoặc `xLabels` thì sao?**  
A: `Chart.Series.Add` yêu cầu độ dài mảng giá trị phải bằng số nhãn trục X, và bạn phải thêm đúng một series cho mỗi mục chú giải; nếu không khớp sẽ ném ra `ArgumentException` khi chạy.

**Q: Tôi có thể sử dụng loại biểu đồ khác, chẳng hạn biểu đồ đường, với cùng logic điền dữ liệu không?**  
A: Có—thay `ChartType.Column` trong `docBuilder.InsertChart` bằng bất kỳ `ChartType` nào khác (ví dụ, `ChartType.Line`) và các lời gọi `Series.Add` tiếp theo sẽ điền dữ liệu cho biểu đồ mới theo cùng cách.

**Q: Làm sao để thay đổi kích thước của biểu đồ sau khi đã chèn?**  
A: Điều chỉnh các thuộc tính `Width` và `Height` của `Shape` trả về bởi `InsertChart` (ví dụ, `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Có cách nhanh để hiển thị nhãn dữ liệu trên mỗi cột của biểu đồ không?**  
A: Đặt `chartObj.Series[i].HasDataLabel = true;` cho mỗi series sau khi thêm, hoặc lặp qua `chartObj.Series` và bật `HasDataLabel` để hiển thị các giá trị trên biểu đồ.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}