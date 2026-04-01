---
category: general
date: 2026-04-01
description: Kích hoạt cảnh báo phông chữ khi tải tài liệu Word bằng Aspose.Words.
  Tìm hiểu cách bắt các sự kiện thay thế phông chữ bằng C# LoadOptions và Cài đặt
  Phông chữ.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: vi
og_description: Kích hoạt cảnh báo phông chữ khi tải tài liệu Word bằng Aspose.Words.
  Hướng dẫn này cho bạn thấy cách bắt các sự kiện thay thế phông chữ trong C#.
og_title: Bật Cảnh Báo Phông Chữ trong Aspose.Words – Hướng Dẫn C# Đầy Đủ
tags:
- Aspose.Words
- C#
- Font Management
title: Bật Cảnh Báo Phông Chữ trong Aspose.Words – Hướng Dẫn C# Đầy Đủ
url: /vi/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kích hoạt Cảnh báo Phông chữ trong Aspose.Words – Hướng dẫn đầy đủ C#

Bạn có bao giờ tự hỏi tại sao một tài liệu Word đột nhiên trông khác đi sau khi bạn tải nó bằng chương trình không? **Enable Font Warnings** và bạn sẽ ngay lập tức biết khi Aspose.Words thay thế phông chữ thiếu bằng một phông chữ dự phòng. Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ thực hành không chỉ bắt các sự thay thế mà còn giải thích *tại sao* chúng xảy ra.

Chúng tôi sẽ bao phủ mọi thứ bạn cần để bắt đầu: gói NuGet cần thiết, cấu hình `LoadOptions` chính xác, và một đầu ra console gọn gàng cho biết phông chữ nào đã được thay thế. Khi kết thúc, bạn sẽ có một mẫu vững chắc, có thể tái sử dụng cho **C# document processing** hoạt động với bất kỳ phiên bản nào của Aspose.Words.

## Những gì bạn sẽ học

- Cách tạo một thể hiện `LoadOptions` theo dõi thay đổi phông chữ.  
- Mục đích của sự kiện `SubstitutionWarning` và cách gắn nó.  
- Một mẫu mã hoàn chỉnh, có thể chạy được, in ra các cảnh báo rõ ràng trên console.  
- Mẹo xử lý các trường hợp đặc biệt như tài liệu chỉ chứa các phông chữ tiêu chuẩn.  

Không cần kinh nghiệm trước với Aspose.Words—chỉ cần quen thuộc cơ bản với C# và .NET.

---

![Sơ đồ cảnh báo phông chữ](placeholder-image.png "Sơ đồ cảnh báo phông chữ")

*Alt text: sơ đồ cảnh báo phông chữ hiển thị luồng sự kiện khi một phông chữ thiếu được thay thế.*

## Bước 1: Thiết lập LoadOptions và Kích hoạt Cảnh báo Phông chữ

Điều đầu tiên bạn cần là một đối tượng `LoadOptions`. Bộ chứa này cho Aspose.Words biết cách xử lý tệp bạn sắp tải. Bằng cách gán một thể hiện `FontSettings` mới, bạn mở ra cánh cửa cho các sự kiện liên quan đến phông chữ.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Tại sao điều này quan trọng:**  
Nếu bạn bỏ qua việc gán `FontSettings`, Aspose.Words vẫn sẽ thay thế các phông chữ thiếu, nhưng bạn sẽ không nhận được bất kỳ thông báo nào. Cơ chế cảnh báo nằm trong `FontSettings`, vì vậy việc khởi tạo nó là *cực kỳ quan trọng* cho mục tiêu của chúng ta.

> **Mẹo chuyên nghiệp:** Bạn cũng có thể chỉ định `FontSettings` tới một thư mục phông chữ tùy chỉnh bằng cách sử dụng `SetFontsFolder`. Điều này giảm số lượng cảnh báo bạn sẽ thấy, vì Aspose.Words thực sự có thể tìm thấy các kiểu chữ thiếu.

## Bước 2: Đăng ký Sự kiện SubstitutionWarning (thay thế phông chữ)

Bây giờ đối tượng `FontSettings` đã tồn tại, chúng ta gắn vào sự kiện `SubstitutionWarning` của nó. Sự kiện này được kích hoạt **mỗi khi** Aspose.Words thay thế một phông chữ yêu cầu bằng một phông chữ khác.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Tại sao điều này quan trọng:**  
Nếu không có trình lắng nghe này, bạn sẽ không có khả năng quan sát quá trình thay thế. Dòng console cung cấp cho bạn một dấu vết kiểm tra nhanh, đặc biệt hữu ích trong các bản dựng tự động hoặc khi tạo PDF cho các ngành công nghiệp có yêu cầu tuân thủ cao.

> **Câu hỏi thường gặp:** *Nếu tôi muốn tắt các cảnh báo thì sao?*  
> Bạn có thể đơn giản gỡ bỏ trình xử lý hoặc đặt `FontSettings.SubstitutionWarning += null;`. Tuy nhiên, giữ lại các cảnh báo thường là cách an toàn nhất vì các sự thay thế im lặng có thể gây ra lỗi bố cục.

## Bước 3: Tải Tài liệu của Bạn với Các Tùy chọn Được Cấu hình (xử lý tài liệu C#)

Với hệ thống cảnh báo đã sẵn sàng, việc tải tài liệu trở nên đơn giản. Truyền thể hiện `LoadOptions` vào hàm khởi tạo `Document`, và Aspose.Words sẽ thực hiện phần còn lại.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Tại sao điều này quan trọng:**  
Đối tượng `LoadOptions` là cầu nối giữa tệp thô và cơ sở hạ tầng cảnh báo. Nếu bạn bỏ qua nó, tài liệu sẽ được tải một cách im lặng, và bất kỳ phông chữ nào thiếu sẽ được thay thế mà không để lại dấu vết.

> **Trường hợp đặc biệt:** Một số tài liệu nhúng chính xác các tệp phông chữ mà chúng cần. Trong trường hợp đó, không có cảnh báo nào xuất hiện vì Aspose.Words tìm thấy phông chữ được nhúng. Mã trên vẫn hoạt động; bạn sẽ chỉ thấy đầu ra console trống.

## Bước 4: Xác minh Đầu ra và Các Bẫy Thường gặp

Chạy chương trình từ command‑prompt hoặc trình gỡ lỗi của IDE. Nếu tài liệu nguồn chứa một phông chữ không được cài đặt trên máy (hoặc không có trong thư mục phông chữ tùy chỉnh), bạn sẽ thấy các dòng như:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Nếu không có gì được in, hoặc:

1. Tất cả các phông chữ đã được tìm thấy, **hoặc**  
2. Trình xử lý `SubstitutionWarning` không được gắn đúng (kiểm tra lại Bước 2).

### Tại sao lại xảy ra Thay thế Phông chữ?

- **Phông chữ hệ thống thiếu:** Hệ điều hành không có kiểu chữ yêu cầu.  
- **Định dạng phông chữ không được hỗ trợ:** Aspose.Words có thể đọc TrueType và OpenType, nhưng không phải mọi định dạng độc quyền.  
- **Hạn chế giấy phép:** Một số phông chữ thương mại chặn việc nhúng, buộc phải dùng phông chữ dự phòng.

Hiểu được *lý do* giúp bạn quyết định có nên cung cấp các phông chữ thiếu cùng với ứng dụng của mình hay điều chỉnh kiểu dáng của tài liệu.

## Thêm: Kiểm soát Phông chữ Dự phòng

Nếu bạn muốn mọi phông chữ thiếu đều thay thế bằng một họ cụ thể (ví dụ, “Calibri”), bạn có thể đặt quy tắc thay thế toàn cục:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Bây giờ console vẫn sẽ cảnh báo bạn, nhưng kết quả hiển thị sẽ nhất quán cho tất cả các phông chữ thiếu.

---

## Tóm tắt

- **Kích hoạt Cảnh báo Phông chữ** bằng cách tạo một `LoadOptions` với một `FontSettings` mới.  
- Gắn sự kiện `SubstitutionWarning` để nhận cảnh báo thời gian thực mỗi khi một phông chữ bị thay thế.  
- Tải tài liệu của bạn bằng các tùy chọn đã cấu hình, và tùy chọn lưu thành PDF để xem hiệu ứng trực quan.  
- Chẩn đoán lý do xảy ra thay thế và, nếu cần, buộc một phông chữ dự phòng cụ thể.

Bạn vừa thêm một lớp bảo vệ vào quy trình làm việc **Aspose.Words** của mình, ngăn ngừa các thay đổi bố cục im lặng. Tiếp theo, bạn có thể khám phá **cài đặt phông chữ** như `DefaultFontName` hoặc tìm hiểu các tùy chọn **kết xuất tài liệu** để tinh chỉnh đầu ra PDF.

---

### Những gì nên thử tiếp theo?

- **Khám phá các tính năng khác của FontSettings**: `SetFontsFolder`, `LoadFontSources`, và `DefaultFontName`.  
- **Kết hợp cảnh báo với các framework ghi log** (Serilog, NLog) để có chẩn đoán cấp độ sản xuất.  
- **Thử nghiệm với các định dạng tài liệu khác nhau** (`.doc`, `.rtf`, `.html`) để xem cách mỗi định dạng xử lý phông chữ thiếu.  

Có câu hỏi hoặc tình huống lạ? Để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}