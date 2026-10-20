---
category: general
date: 2026-06-27
description: Đăng ký callback cảnh báo trong Aspose.Words để bắt các thay thế phông
  chữ và các vấn đề tải. Tìm hiểu cách sử dụng LoadOptions từng bước với Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: vi
og_description: Đăng ký callback cảnh báo trong Aspose.Words để giám sát việc thay
  thế phông chữ và các cảnh báo tải khác. Tham khảo toàn bộ hướng dẫn này để triển
  khai một cách mạnh mẽ.
og_title: Đăng ký Callback Cảnh báo trong Aspose.Words – Hướng dẫn toàn diện
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Đăng ký Callback Cảnh báo trong Aspose.Words – Hướng dẫn Lập trình Toàn diện
url: /vi/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đăng ký Callback Cảnh báo trong Aspose.Words – Hướng dẫn Lập trình Toàn diện

Bạn đã bao giờ tự hỏi làm thế nào để **đăng ký callback cảnh báo trong Aspose.Words** để có thể xem chính xác những phông chữ nào bị thay thế khi tài liệu được tải không? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi việc thay thế phông chữ âm thầm làm hỏng bố cục của file PDF hoặc Word được tạo.

Trong tutorial này, chúng ta sẽ đi qua một giải pháp thực hành không chỉ đăng ký callback cảnh báo trong Aspose.Words mà còn giải thích *tại sao* bạn nên làm như vậy, cách callback hoạt động bên trong, và những trường hợp đặc biệt bạn có thể gặp phải. Khi kết thúc, bạn sẽ có thể ghi lại mọi lần thay thế phông chữ, bắt các cảnh báo tải khác, và giữ cho pipeline xử lý tài liệu của bạn trong suốt.

## Những gì bạn sẽ học

- Cài đặt **LoadOptions** để kiểm soát hành vi tải tài liệu.  
- Đăng ký một **warning callback** sẽ được kích hoạt cho việc thay thế phông chữ và các loại cảnh báo khác.  
- Tải một DOCX với các tùy chọn đã cấu hình và giải thích đầu ra của callback.  
- Những bẫy thường gặp (phông chữ thiếu, thư mục phông chữ tùy chỉnh, và cân nhắc hiệu năng).  

**Tiền đề:** Visual Studio 2022 (hoặc bất kỳ IDE C# nào), runtime .NET 6+, và giấy phép Aspose.Words hợp lệ (bản dùng thử miễn phí đủ cho việc thử nghiệm). Không cần thêm gói NuGet nào ngoài `Aspose.Words`.

---

![Sơ đồ minh họa luồng đăng ký callback cảnh báo trong Aspose.Words và xử lý cảnh báo thay thế phông chữ](register-warning-callback-aspose-words.png "sơ đồ đăng ký callback cảnh báo aspose.words")

## Bước 1: Tạo LoadOptions – Điểm vào cho việc Xử lý Cảnh báo  

Trước khi callback có thể được kích hoạt, bạn cần một thể hiện của **LoadOptions**. Hãy nghĩ nó như bảng điều khiển bạn đưa cho Aspose.Words khi nói “tải file này, nhưng hãy cho tôi biết nếu có gì bất thường”.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Tại sao điều này quan trọng:** `LoadOptions` cho phép bạn tinh chỉnh mọi thứ từ mật khẩu mã hoá đến thư mục phông chữ. Bằng cách gắn một warning callback vào đối tượng này, bạn biến một quy trình im lặng thành một quy trình có thể quan sát được.

## Bước 2: Đăng ký Warning Callback – Ghi lại các Thay thế Phông chữ  

Bây giờ là phần trọng tâm: **warning callback**. Chúng ta sẽ đăng ký một phương thức ẩn danh (lambda) mà Aspose.Words sẽ gọi cho mỗi cảnh báo tải. Trong callback, chúng ta lọc `WarningType.FontSubstitution` và in ra một thông báo thân thiện.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Mẹo chuyên nghiệp:** Nếu bạn cũng muốn ghi lại các hình ảnh thiếu hoặc tính năng không được hỗ trợ, hãy thêm các nhánh `if` kiểm tra `args.WarningType`. Điều này biến việc **đăng ký callback cảnh báo trong Aspose.Words** của bạn thành một giải pháp “một cửa” cho mọi chẩn đoán khi tải.

## Bước 3: Tải Tài liệu bằng LoadOptions Đã Cấu hình  

Sau khi đã gắn callback, bước tiếp theo chỉ là tải tài liệu. Truyền thể hiện `loadOptions` vào hàm khởi tạo `Document`. Mỗi khi Aspose.Words gặp một phông chữ không tìm thấy, callback của bạn sẽ được kích hoạt và ghi vào console.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Chạy chương trình, và bạn sẽ thấy đầu ra tương tự như:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Đó là cốt lõi của **đăng ký callback cảnh báo aspose.words** — một mẫu ba bước bạn có thể tái sử dụng trong bất kỳ dự án nào.

## Bước 4: Mở Rộng Callback cho Các Kịch bản Thực tế  

### 4.1 Ghi Log vào File Thay vì Console  

Trong môi trường production, bạn hiếm khi muốn console spam. Thay `Console.WriteLine` bằng một logger (ví dụ: `Serilog`, `NLog`) hoặc ghi vào file văn bản:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Cung cấp Thư mục Phông chữ Tùy chỉnh  

Nếu môi trường của bạn sử dụng phông chữ công ty, hãy cho Aspose.Words biết nơi tìm kiếm trước khi nó rơi vào việc thay thế:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Bây giờ callback có thể được kích hoạt *ít* hơn, vì engine sẽ tìm thấy đúng phông chữ.

### 4.3 Xử lý Các Cảnh báo Không phải Phông chữ  

Bạn có thể mở rộng phạm vi để bắt mọi cảnh báo tải:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Bước 5: Kiểm tra Implemention – Những gì Mong đợi  

### 5.1 Xác minh với Tài liệu Có Phông chữ Thiếu  

Tạo một DOCX nhỏ tham chiếu một phông chữ không được cài trên máy của bạn (ví dụ: “Comic Sans MS” trên server Linux). Chạy loader; bạn sẽ thấy thông báo thay thế.

### 5.2 Đánh giá Overhead  

Callback thêm overhead không đáng kể — khoảng vài microseconds cho mỗi cảnh báo. Nếu bạn tải hàng ngàn tài liệu, có thể gom log lại hoặc tắt callback cho các lần chạy không quan trọng.

### 5.3 Các Trường hợp Đặc biệt  

- **Nhiều lần Thay thế cho cùng một Phông chữ:** Aspose.Words có thể kích hoạt callback nhiều lần nếu cùng một phông chữ thiếu xuất hiện trên các trang khác nhau. Hãy loại bỏ trùng lặp trong logger nếu cần.  
- **Tài liệu Mã hoá:** Nếu DOCX được bảo vệ bằng mật khẩu, bạn cũng phải đặt `loadOptions.Password`. Callback vẫn sẽ được kích hoạt sau khi giải mã.  
- **Async Loading:** API là đồng bộ, nhưng bạn có thể bọc lời gọi tải trong `Task.Run` để chạy nền; callback vẫn an toàn với đa luồng.

## Những Bẫy Thường Gặp & Cách Tránh  

| Bẫy | Tại sao Xảy ra | Cách khắc phục |
|-----|----------------|----------------|
| **Không có đầu ra nào** | Callback chưa được gán *hoặc* `WarningCallback` bị ghi đè sau. | Đảm bảo gán callback **một lần** trước khi tải, và không gán lại `loadOptions` sau khi đã gán. |
| **Lỗi cast không hợp lệ** | Cố gắng cast một cảnh báo không phải `FontSubstitutionWarningInfo`. | Luôn kiểm tra `args.WarningType` trước khi cast. |
| **Giảm hiệu năng** | Ghi log đồng bộ vào nguồn I/O chậm. | Sử dụng framework ghi log bất đồng bộ hoặc buffer ghi. |
| **Phông chữ tùy chỉnh không được tìm** | Thư mục phông chữ chưa được thêm vào `FontSettings`. | Thêm `SetFontsFolder` như trong Bước 4.2. |

## Ví dụ Hoàn chỉnh – Sao chép & Chạy  

Dưới đây là một chương trình tự chứa bạn có thể sao chép vào dự án Console App mới. Nó minh họa toàn bộ luồng từ đầu đến cuối.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Đầu ra console mong đợi** (giả sử có phông chữ thiếu):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Chạy chương trình, và bạn sẽ thấy chính xác những phông chữ nào Aspose.Words đã thay thế, cung cấp cho bạn khả năng quan sát toàn diện quá trình tải.

---

## Kết luận  

Chúng ta vừa tìm hiểu **cách đăng ký warning callback trong Aspose.Words**, tại sao đây là thực hành tốt cho bất kỳ workflow xử lý tài liệu nào, và cách mở rộng mẫu này để ghi log, sử dụng phông chữ tùy chỉnh, và xử lý các cảnh báo rộng hơn. Chỉ với ba dòng code, bạn biến một thao tác tải “hộp đen” thành một bước có thể audit và debug — không còn những thay đổi bố cục bí ẩn nữa.

Tiếp theo bạn có thể thử kết hợp callback này với **Aspose.Words SaveOptions** để ghi log cảnh báo cả khi tải *và* lưu, hoặc gắn callback vào một Web API xử lý upload thời gian thực. Bạn cũng có thể khám phá các từ khóa phụ mà chúng tôi đã giới thiệu — như *loadoptions font substitution warning* — để tối ưu hiệu năng hoặc tích hợp với bảng điều khiển giám sát.

Có câu hỏi hay tình huống khó khăn? Hãy để lại bình luận, chúng ta cùng nhau giải quyết. Chúc bạn lập trình vui vẻ, và mong rằng các PDF của bạn luôn hiển thị đúng phông chữ!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ cùng giải thích chi tiết từng bước, giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Aspose Words Java Callback Tùy chỉnh Lưu](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Tùy chỉnh Lưu](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Tùy chỉnh Lưu](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}