---
title: Tạo Bảng Văn Bản Với Văn Bản Xoay trong Word bằng Aspose.Words cho .NET
weight: 110
limit:
description: Học cách xây dựng bảng Word với độ rộng cột cố định, văn bản xoay, chiều cao hàng chính xác và các ô đã được điền nội dung bằng Aspose.Words cho .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Học cách xây dựng bảng Word với độ rộng cột cố định, văn bản xoay,
    chiều cao hàng chính xác và các ô đã được điền nội dung bằng Aspose.Words cho
    .NET.
  headline: Tạo Bảng Văn Bản Với Văn Bản Xoay trong Word bằng Aspose.Words cho .NET
  type: TechArticle
- description: Học cách xây dựng bảng Word với độ rộng cột cố định, văn bản xoay,
    chiều cao hàng chính xác và các ô đã được điền nội dung bằng Aspose.Words cho
    .NET.
  name: Tạo Bảng Văn Bản Với Văn Bản Xoay trong Word bằng Aspose.Words cho .NET
  steps:
  - name: Khởi tạo một đối tượng Document mới và một DocumentBuilder sẽ được dùng
      để xây dựng bảng.
    text: Khởi tạo một đối tượng Document mới và một DocumentBuilder sẽ được dùng
      để xây dựng bảng.
  - name: Bắt đầu một bảng mới, chèn ô đầu tiên và cố định độ rộng cột để chúng không
      tự điều chỉnh.
    text: Bắt đầu một bảng mới, chèn ô đầu tiên và cố định độ rộng cột để chúng không
      tự điều chỉnh.
  - name: Căn giữa nội dung theo chiều dọc trong ô hiện tại và ghi văn bản cho ô đầu
      tiên của hàng đầu tiên.
    text: Căn giữa nội dung theo chiều dọc trong ô hiện tại và ghi văn bản cho ô đầu
      tiên của hàng đầu tiên.
  - name: Chèn ô thứ hai của hàng đầu tiên và ghi văn bản cho ô này.
    text: Chèn ô thứ hai của hàng đầu tiên và ghi văn bản cho ô này.
  - name: Kết thúc hàng đầu tiên, hoàn thiện bố cục của nó.
    text: Kết thúc hàng đầu tiên, hoàn thiện bố cục của nó.
  - name: Bắt đầu ô đầu tiên của hàng thứ hai, đặt chiều cao hàng chính xác 100 điểm,
      xoay văn bản lên trên và ghi nội dung cho ô.
    text: Bắt đầu ô đầu tiên của hàng thứ hai, đặt chiều cao hàng chính xác 100 điểm,
      xoay văn bản lên trên và ghi nội dung cho ô.
  - name: Chèn ô thứ hai của hàng thứ hai, xoay văn bản xuống dưới và ghi nội dung
      cho ô.
    text: Chèn ô thứ hai của hàng thứ hai, xoay văn bản xuống dưới và ghi nội dung
      cho ô.
  - name: Kết thúc hàng thứ hai, hoàn thành dòng thứ hai của bảng.
    text: Kết thúc hàng thứ hai, hoàn thành dòng thứ hai của bảng.
  - name: Kết thúc việc xây dựng bảng, khép lại cấu trúc bảng.
    text: Kết thúc việc xây dựng bảng, khép lại cấu trúc bảng.
  - name: Lưu tài liệu đã hoàn thành thành tệp .docx.
    text: Lưu tài liệu đã hoàn thành thành tệp .docx.
  type: HowTo
- questions:
  - answer: Sau khi cố định độ rộng cột, gán độ rộng cho mỗi ô bằng cách sử dụng `builder.CellFormat.Width
      = <valueInPoints>;` trước khi chèn ô tiếp theo; bảng sẽ giữ các độ rộng chính
      xác đó.
    question: Làm thế nào tôi có thể đặt độ rộng cột cụ thể sau khi gọi `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` là cài đặt ở mức ô, vì vậy bạn
      cần đặt lại nó cho các ô trong hàng thứ hai (ví dụ, `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) trước khi ghi nội dung của chúng.'
    question: Tại sao căn dọc chỉ ảnh hưởng đến hàng đầu tiên mà không ảnh hưởng đến
      hàng thứ hai?
  - answer: Có — đặt `builder.RowFormat.Height` và `builder.RowFormat.HeightRule =
      HeightRule.Exactly` trước mỗi lần gọi `builder.EndRow();`; hàng tiếp theo có
      thể có giá trị chiều cao khác.
    question: Tôi có thể đặt chiều cao chính xác khác nhau cho mỗi hàng không, và
      nếu có thì làm thế nào?
  - answer: Đặt lại hướng bằng cách gán `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      trước khi ghi vào ô tiếp theo.
    question: Làm thế nào để khôi phục lại hướng văn bản mặc định sau khi đã sử dụng
      `TextOrientation.Upward` hoặc `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Tạo Bảng Văn Bản Xoay trong Word với Aspose.Words
og_description: Mã từng bước để xây dựng bảng có độ rộng cố định với văn bản xoay dọc và chiều cao hàng chính xác.
og_image_alt: Ảnh chụp màn hình hiển thị tài liệu Word có bảng với độ rộng cột cố định, văn bản xoay trong các ô và chiều cao hàng được xác định, được tạo bằng Aspose.Words cho .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Bảng Văn Bản Với Văn Bản Xoay trong Word bằng Aspose.Words cho .NET
Hướng dẫn này chỉ ra cách tạo tài liệu Word và thêm một bảng có các cột có độ rộng cố định, các hàng có chiều cao chính xác, và văn bản trong ô được xoay theo chiều dọc. Bạn sẽ học cách đặt căn dọc, áp dụng hướng văn bản, điền nội dung vào từng ô, và cuối cùng lưu tài liệu — tất cả đều sử dụng Aspose.Words cho .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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

**Q: Làm thế nào tôi có thể đặt độ rộng cột cụ thể sau khi gọi `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Sau khi cố định độ rộng cột, gán độ rộng cho mỗi ô bằng cách sử dụng `builder.CellFormat.Width = <valueInPoints>;` trước khi chèn ô tiếp theo; bảng sẽ giữ các độ rộng chính xác đó.

**Q: Tại sao căn dọc chỉ ảnh hưởng đến hàng đầu tiên mà không ảnh hưởng đến hàng thứ hai?**  
A: `builder.CellFormat.VerticalAlignment` là cài đặt ở mức ô, vì vậy bạn cần đặt lại nó cho các ô trong hàng thứ hai (ví dụ, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) trước khi ghi nội dung của chúng.

**Q: Tôi có thể đặt chiều cao chính xác khác nhau cho mỗi hàng không, và nếu có thì làm thế nào?**  
A: Có — đặt `builder.RowFormat.Height` và `builder.RowFormat.HeightRule = HeightRule.Exactly` trước mỗi lần gọi `builder.EndRow();`; hàng tiếp theo có thể có giá trị chiều cao khác.

**Q: Làm thế nào để khôi phục lại hướng văn bản mặc định sau khi đã sử dụng `TextOrientation.Upward` hoặc `Downward`?**  
A: Đặt lại hướng bằng cách gán `builder.CellFormat.Orientation = TextOrientation.Horizontal;` trước khi ghi vào ô tiếp theo.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}