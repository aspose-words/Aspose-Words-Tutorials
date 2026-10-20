---
category: general
date: 2026-03-19
description: Tạo tài liệu Word bằng Aspose.Words và phông chữ biến thể. Tìm hiểu cách
  thay đổi độ đậm của phông chữ, thiết lập độ rộng phông chữ và định nghĩa biến thể
  phông chữ trong C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: vi
og_description: Tạo tài liệu Word với phông chữ biến thể bằng Aspose.Words. Hướng
  dẫn này chỉ cho bạn cách tải phông chữ, thay đổi độ đậm, đặt độ rộng phông và xác
  định biến thể phông chữ.
og_title: Tạo tài liệu Word với phông chữ biến đổi – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Variable Font
title: Tạo tài liệu Word với phông chữ biến đổi – Hướng dẫn
url: /vi/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word với Variable Font – Hướng dẫn

Bạn đã bao giờ cần **tạo tài liệu word** sử dụng một variable font hiện đại, nhưng không chắc bắt đầu từ đâu chưa? Bạn không đơn độc. Trong nhiều dự án—hãy nghĩ đến các báo cáo động hoặc brochure đồng nhất thương hiệu—khả năng **thay đổi độ đậm của font** ngay lập tức thực sự là một yếu tố thay đổi cuộc chơi.  

Trong tutorial này chúng ta sẽ đi qua toàn bộ quy trình: từ việc tải một variable font vào Aspose.Words, đến việc thiết lập độ đậm và độ rộng, và cuối cùng lưu thành DOCX trông chính xác như thiết kế của bạn. Không có những tham chiếu mơ hồ, chỉ có mã cụ thể mà bạn có thể sao chép vào dự án C# ngay lập tức.

## Những gì bạn sẽ học

- Cách **tải file variable font** vào Aspose.Words bằng `FontSettings`.
- Cú pháp để **định nghĩa các trục biến thể font** như `wght` (weight) và `wdth` (width).
- Các cách **đặt độ rộng font** và **thay đổi độ đậm font** trên một `Run` duy nhất.
- Mẹo khắc phục các vấn đề thường gặp (glyph thiếu, đường dẫn thư mục sai, v.v.).
- Một ví dụ hoàn chỉnh, có thể chạy ngay mà bạn có thể sao chép‑dán và thử nghiệm.

> **Yêu cầu trước**: .NET 6+ (hoặc .NET Framework 4.6+), Aspose.Words for .NET được cài đặt qua NuGet, và một file variable‑font như *RobotoFlex.ttf* được đặt trong thư mục *Fonts* cục bộ.

---

## Bước 1 – Tải Variable Font vào Aspose.Words

Đầu tiên, chúng ta phải cho Aspose.Words biết nơi tìm các font tùy chỉnh của mình. Lớp `FontSettings` thực hiện phần việc nặng.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Tại sao điều này quan trọng**: Nếu không đăng ký thư mục, Aspose.Words sẽ quay lại sử dụng các font hệ thống và sẽ bỏ qua bất kỳ dữ liệu biến thể OpenType nào bạn cố gắng áp dụng sau này. Bằng cách chỉ định một thư mục cụ thể, bạn đảm bảo rằng *RobotoFlex* (hoặc bất kỳ variable font nào khác) luôn được tìm thấy mỗi khi mã chạy.

> **Mẹo chuyên nghiệp**: Đặt tham số thứ hai của `SetFontsFolder` thành `true` nếu bạn muốn Aspose tìm kiếm cả các thư mục con. Điều này hữu ích khi bạn sắp xếp font theo kiểu hoặc độ đậm.

---

## Bước 2 – Tạo Document mới và Thêm Văn bản mẫu

Bây giờ công cụ font đã biết nơi tìm, chúng ta tạo một `Document` trống và chèn một đoạn văn với một `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Điều gì đang xảy ra**: `Run` đại diện cho một đoạn văn bản liên tục có cùng định dạng. Bằng cách tạo nó trước, chúng ta giữ logic định dạng riêng biệt—hoàn hảo để sau này áp dụng các trục biến thể khác nhau cho các run riêng biệt nếu cần.

---

## Bước 3 – Định nghĩa các Trục Biến Thể Mong Muốn (Weight & Width)

Variable fonts cung cấp các *trục* mà bạn có thể điều chỉnh tại thời gian chạy. Hai trục phổ biến nhất là `wght` (độ đậm) và `wdth` (độ rộng). Aspose.Words mô hình hoá điều này bằng bộ sưu tập `OpenTypeFontVariation`.  

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Tại sao lại dùng các số này**: Trong đặc tả OpenType, `wght` có phạm vi từ mức tối thiểu đến tối đa của font (thường là 100–900). Giá trị **700** tương đương với kiểu chữ đậm. `wdth` hoạt động tương tự; **100** là độ rộng mặc định (bình thường), trong khi các giá trị dưới 100 sẽ làm các glyph lại lại.

> **Trường hợp đặc biệt**: Một số variable font không hỗ trợ một trục nào đó. Nếu bạn cung cấp một thẻ không được hỗ trợ, Aspose sẽ bỏ qua nó một cách im lặng. Luôn kiểm tra lại thông số kỹ thuật của font (thường nằm trong metadata của file `.ttf` hoặc `.otf`).

---

## Bước 4 – Áp dụng Biến Thể cho Run bằng Tên Font

Bây giờ chúng ta gắn dữ liệu biến thể vào văn bản thực tế. Lớp `FontInfo` chứa tên họ font và bộ sưu tập các trục.  

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Giải thích**: Bằng cách thiết lập `FontInfo`, chúng ta bỏ qua thuộc tính `Font.Name` thông thường và cung cấp cho engine một cấu hình font đầy đủ. Đây là cách duy nhất để thông báo cho Aspose.Words sử dụng một variable font với các trục tùy chỉnh.

> **Sai lầm thường gặp**: Quên khớp chính xác tên họ font bên trong file font (`RobotoFlex` trong ví dụ này). Một lỗi chính tả sẽ khiến Aspose quay lại font mặc định, và biến thể của bạn sẽ bị mất.

---

## Bước 5 – Lưu Document và Kiểm tra Kết quả

Cuối cùng, ghi document ra đĩa. DOCX được tạo sẽ chứa các chỉ thị variable‑font, mà Microsoft Word (2016+) có thể render đúng.  

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Mở file kết quả trong Word, chọn đoạn văn bản và xem hộp thoại **Font**. Bạn sẽ thấy *Roboto Flex* được liệt kê, và văn bản sẽ xuất hiện đậm hơn nội dung xung quanh—đúng như thiết lập `wght = 700` của chúng ta yêu cầu.

> **Mẹo kiểm tra**: Nếu văn bản không thay đổi, hãy kiểm tra lại xem file font có thực sự hỗ trợ trục `wght` không. Một số “variable” font chỉ mở ra `ital` (italic) hoặc `opsz` (optical size).

---

## Tùy chọn: Thêm Biến Thể – Thay Đổi Độ Rộng Động

Nếu bạn muốn *đặt độ rộng font* khác cho một đoạn văn khác, chỉ cần lặp lại các bước 3‑4 với một bộ `OpenTypeFontVariation` mới.  

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Bây giờ bạn có hai run—một đậm, một hơi rộng hơn—để minh họa cả **thay đổi độ đậm font** và **đặt độ rộng font** trong cùng một tài liệu.

---

## Ví dụ Hoàn chỉnh

Sao chép đoạn mã dưới đây vào một ứng dụng console mới (`Program.cs`) và chạy. Đảm bảo thư mục `Fonts` chứa `RobotoFlex.ttf` (hoặc bất kỳ variable font nào bạn muốn).  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Kết quả mong đợi**: Một file `VariableFont.docx` trong đó cụm từ “Variable‑weight text” xuất hiện đậm, nhờ trục `wght = 700`, trong khi vẫn giữ độ rộng mặc định.

---

## Câu hỏi Thường gặp & Trường hợp Đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Nếu font không được tìm thấy thì sao?* | Kiểm tra lại đường dẫn thư mục, đảm bảo tên file khớp, và tiến trình có quyền đọc. Bạn cũng có thể gọi `fontSettings.GetFonts()` để liệt kê các font đã phát hiện. |
| *Có thể kết hợp nhiều run với các biến thể khác nhau không?* | Chắc chắn. Mỗi `Run` có thể mang `FontInfo` riêng. Chỉ cần lặp lại các bước 3‑4 cho mỗi run. |
| *Các phiên bản Word cũ có hỗ trợ variable fonts không?* | Word 2016 (Build 16.0.8001) đã giới thiệu hỗ trợ cơ bản. Nếu bạn nhắm tới các phiên bản cũ hơn, tài liệu sẽ fallback về phiên bản tĩnh gần nhất của font. |
| *Có giới hạn số trục tôi có thể đặt không?* | Bạn có thể đặt bất kỳ số trục nào mà font định nghĩa. Các thẻ phổ biến là `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Cung cấp thẻ không được hỗ trợ sẽ không có hiệu lực. |
| *Làm sao debug khi glyph bị thiếu?* | Dùng `FontSettings.GetFontSources()` để kiểm tra các font đã tải, và `FontInfo.HasGlyph(char)` để kiểm tra từng ký tự. |

---

## Kết luận

Trong vài bước ngắn gọn, chúng ta đã chỉ ra **cách tạo tài liệu word** tận dụng sức mạnh của variable fonts, cho phép bạn **thay đổi độ đậm font**, **đặt độ rộng font**, **tải file variable font**, và **định nghĩa các trục biến thể font**—tất cả đều với Aspose.Words for .NET.  

Ý tưởng cốt lõi rất đơn giản: đăng ký thư mục font, mô tả các trục mong muốn, gắn chúng vào một `Run`, và lưu lại. Từ đây bạn có thể mở rộng kỹ thuật này cho toàn bộ phần, bảng, hoặc thậm chí tự động tạo các báo cáo thương hiệu.  

**Bước tiếp theo**: thử thay `RobotoFlex` bằng một variable font khác, khám phá trục `ital` (italic), hoặc tạo phiên bản PDF của cùng một tài liệu bằng Aspose.PDF. Mô hình tương tự vẫn áp dụng—tải, định nghĩa, áp dụng, lưu.

Chúc bạn lập trình vui vẻ và tận hưởng sự linh hoạt mà variable fonts mang lại cho các dự án tự động hoá Word của mình!  

<img src="variable-font-demo.png" alt="Ví dụ tạo tài liệu word với variable font">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}