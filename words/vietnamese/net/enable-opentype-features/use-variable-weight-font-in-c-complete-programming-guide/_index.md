---
category: general
date: 2026-06-02
description: Học cách sử dụng phông chữ trọng lượng biến trong C# và thiết lập trọng
  lượng phông chữ bằng lập trình, đồng thời thay đổi mã kéo dài phông chữ cho kiểu
  chữ động.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: vi
og_description: Sử dụng phông chữ trọng lượng biến trong C# để thiết lập trọng lượng
  phông chữ một cách lập trình và thay đổi mã độ dãn phông chữ, cho phép kiểu chữ
  động trong tài liệu của bạn.
og_title: Sử dụng phông chữ trọng lượng biến trong C# – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Sử dụng phông chữ trọng lượng biến trong C# – Hướng dẫn lập trình toàn diện
url: /vi/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Phông chữ Trọng lượng Biến trong C# – Hướng dẫn Lập trình Toàn diện

Bạn đã bao giờ cần **sử dụng phông chữ trọng lượng biến** trong dự án .NET nhưng không chắc làm sao để trọng lượng và độ kéo dài phản hồi theo đầu vào của người dùng? Bạn không phải là người duy nhất. Trong nhiều trường hợp UI hoặc báo cáo, bạn muốn văn bản thích ứng — có thể là tiêu đề nhẹ nhàng trở nên đậm khi rê chuột, hoặc một đoạn văn mở rộng chiều rộng để nhấn mạnh. Tin tốt là với Aspose.Words bạn có thể **đặt trọng lượng phông chữ bằng mã** và thậm chí **thay đổi mã độ kéo dài phông chữ** một cách linh hoạt.

Trong hướng dẫn này, chúng ta sẽ thực hành một ví dụ cụ thể cho thấy cách tải phông chữ trọng lượng biến, áp dụng trọng lượng tùy chỉnh và điều chỉnh cài đặt độ kéo dài — tất cả bằng mã C# rõ ràng mà bạn có thể sao chép và dán. Khi hoàn thành, bạn sẽ có một ứng dụng console chạy được và tạo ra PDF minh họa hiệu ứng.

---

## Những gì bạn cần

- **Aspose.Words for .NET** (v23.12 trở lên). Thư viện này hỗ trợ đầy đủ phông chữ trọng lượng biến.
- Một thư mục chứa ít nhất một tệp phông chữ trọng lượng biến, ví dụ: *RobotoFlex‑Variable.ttf*. Bạn có thể tải về từ Google Fonts.
- .NET 6 SDK (hoặc bất kỳ phiên bản .NET mới nào) và một IDE mà bạn thích.
- Kiến thức cơ bản về C# — không cần gì phức tạp, chỉ vài dòng mã.

Đó là tất cả. Không cần gói NuGet bổ sung nào ngoài Aspose.Words, và không có tệp cấu hình lạ.

---

![Sử dụng phông chữ trọng lượng biến](https://example.com/variable-weight-sample.png "Trình diễn sử dụng phông chữ trọng lượng biến")

*Alt text: ảnh chụp màn hình cho thấy việc sử dụng phông chữ trọng lượng biến trong tài liệu PDF được tạo ra.*

---

## Bước 1: Thiết lập FontSettings và chỉ tới Thư mục Phông chữ của bạn  

Điều quan trọng đầu tiên — Aspose.Words cần biết nơi lưu trữ các phông chữ trọng lượng biến của bạn. Bạn thực hiện điều này bằng cách tạo một đối tượng `FontSettings` và gắn một `FolderFontSource`. Tham số `true` cho biết engine sẽ tìm kiếm cả các thư mục con, rất hữu ích nếu bạn lưu nhiều họ phông chữ trong cùng một thư mục.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Tại sao điều này quan trọng:** Nếu không đăng ký thư mục, Aspose.Words sẽ quay lại sử dụng phông chữ hệ thống và sẽ bỏ qua dữ liệu trọng lượng biến được nhúng trong tệp phông chữ tùy chỉnh của bạn. Bước này là nền tảng cho mọi thứ tiếp theo.

---

## Bước 2: Gắn FontSettings vào Document  

Bây giờ chúng ta tạo một `Document` mới (hoặc tải một tài liệu hiện có) và chỉ định nó sử dụng `FontSettings` vừa chuẩn bị. Việc ràng buộc này sẽ làm cho dữ liệu trọng lượng biến sẵn sàng cho mọi `Run` mà chúng ta thêm sau này.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Nếu bạn đã có một mẫu — chẳng hạn một tệp Word có các placeholder — bạn có thể thay `new Document()` bằng `new Document("Template.docx")`. `FontSettings` sẽ được áp dụng tương tự.

---

## Bước 3: Thêm một Run Văn bản sẽ Sử dụng Phông chữ Trọng lượng Biến  

Một **Run** là đơn vị định dạng văn bản nhỏ nhất trong Aspose.Words. Chúng ta sẽ tạo một Run, chèn nó vào một đoạn mới, và sau đó sẽ thay đổi các thuộc tính phông chữ của nó.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Lúc này, văn bản sẽ hiển thị bằng phông chữ mặc định (thường là Times New Roman). Phép màu sẽ xuất hiện khi chúng ta gán họ phông chữ trọng lượng biến.

---

## Bước 4: Chọn Họ Phông chữ Trọng lượng Biến  

Đây là nơi chúng ta **thực sự sử dụng phông chữ trọng lượng biến**. Đặt `Font.Name` thành tên họ chính xác được định nghĩa trong tệp phông chữ biến. Đối với Roboto Flex, tên là `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Nếu bạn không chắc tên họ, hãy mở tệp `.ttf` bằng một trình xem phông chữ hoặc dùng phương thức `fontSettings.GetFonts()` để liệt kê các họ có sẵn.

---

## Bước 5: Đặt Trọng lượng và Độ Kéo dài Phông chữ bằng Mã  

Bây giờ là phần cốt lõi của hướng dẫn: chúng ta **đặt trọng lượng phông chữ bằng mã** và **thay đổi mã độ kéo dài phông chữ**. Cả hai thuộc tính đều nhận giá trị nguyên tương ứng với chuẩn OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Chọn bất kỳ giá trị nào mà phông chữ biến hỗ trợ.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Mặc định là 100 (Normal).

> **Mẹo chuyên nghiệp:** Không phải mọi phông chữ biến đều cung cấp toàn bộ dải. Nếu bạn đặt một giá trị không được hỗ trợ, engine sẽ tự động điều chỉnh tới trọng lượng hoặc độ kéo dài gần nhất có sẵn.

---

## Bước 6: Lưu Document và Kiểm tra Kết quả  

Cuối cùng, ghi tài liệu ra PDF (hoặc DOCX) và mở nó để xem hiệu ứng. PDF là định dạng tuyệt vời để kiểm tra hình ảnh vì việc hiển thị nhất quán trên mọi nền tảng.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Khi bạn mở *VariableWeightDemo.pdf*, bạn sẽ thấy cụm từ “Variable‑weight text demo” được hiển thị bằng một phiên bản nhẹ, hơi mở rộng của Roboto Flex. Thay `FontWeight` thành `700` và `FontStretch` thành `80`, rồi chạy lại — bạn sẽ quan sát văn bản trở nên đậm và gọn hơn.

---

## Câu hỏi Thường gặp & Trường hợp Cạnh  

### Phông chữ không hiển thị gì cả?  

- **Thiếu FontSettings**: Kiểm tra lại rằng `doc.FontSettings = fontSettings;` được thực thi **trước** khi thêm bất kỳ văn bản nào.
- **Tên họ không đúng**: Dùng `fontSettings.GetFonts()` để liệt kê tất cả các họ đã được phát hiện; sao chép chính xác chuỗi.
- **Trọng lượng/độ kéo dài không được hỗ trợ**: Một số phông chữ biến chỉ hỗ trợ một phần của dải 100‑900. Dùng `run.Font.FontWeight = 400;` như một giá trị dự phòng an toàn.

### Có thể thay đổi trọng lượng sau khi tài liệu đã được lưu không?  

Có. Đối tượng `Run` có thể thay đổi, vì vậy bạn có thể điều chỉnh `FontWeight` hoặc `FontStretch` bất kỳ lúc nào trước khi gọi `Save`. Nếu bạn cần chuyển đổi trọng lượng một cách động (ví dụ dựa trên tương tác người dùng), hãy cân nhắc tạo các Run riêng biệt cho mỗi trạng thái.

### Điều này có hoạt động với đầu ra DOCX không?  

Hoàn toàn có. Siêu dữ liệu trọng lượng biến được lưu trong OpenXML nền tảng, và các phiên bản Word hiện đại có thể giải thích nó. Tuy nhiên, các phiên bản Word cũ hơn có thể bỏ qua cài đặt độ kéo dài.

---

## Ví dụ Hoàn chỉnh  

Dưới đây là một chương trình console đầy đủ mà bạn có thể biên dịch và chạy ngay. Nó bao gồm tất cả các `using` cần thiết, xử lý lỗi và chú thích.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Kết quả mong đợi:** Console sẽ in ra đường dẫn lưu, và PDF được tạo sẽ hiển thị văn bản ở kiểu nhẹ, mở rộng — chính xác như chúng ta đã cấu hình.

---

## Tổng kết  

Chúng ta đã tìm hiểu cách **sử dụng phông chữ trọng lượng biến** trong C# với Aspose.Words, minh họa cách **đặt trọng lượng phông chữ bằng mã**, và chỉ ra **cách thay đổi mã độ kéo dài phông chữ** để mở rộng hoặc thu hẹp glyphs. Các bước rất đơn giản: cấu hình `FontSettings`, gắn chúng vào `Document`, tạo một `Run`, chọn họ phông chữ trọng lượng biến, và cuối cùng điều chỉnh `FontWeight` và `FontStretch`.

---

## Tiếp theo là gì?  

- **Tích hợp UI động**: Áp dụng logic tương tự trong ứng dụng WinForms hoặc WPF để cho phép người dùng chọn trọng lượng/độ kéo dài qua thanh trượt.
- **Nhiều Run**: Kết hợp nhiều Run với các trọng lượng khác nhau trong cùng một đoạn để tạo ra hệ thống kiểu chữ phong phú.
- **Các trục nâng cao**: Một số phông chữ biến cung cấp các trục bổ sung (ví dụ: slant, optical size). Sử dụng `run.Font.FontStyle` hoặc khám phá `FontVariationSettings` để kiểm soát chi tiết hơn.
- **Mẹo hiệu năng**: Lưu trữ đối tượng `FontSettings` khi xử lý nhiều tài liệu để tránh quét thư mục lặp lại.

Hãy thoải mái thử nghiệm — thay *Roboto Flex* bằng *Inter Variable* hoặc bất kỳ phông chữ OpenType biến nào khác, và xem tài liệu của bạn trở nên linh hoạt hơn về mặt hình ảnh. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây liên quan chặt chẽ đến các kỹ thuật đã trình bày trong bài viết này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}