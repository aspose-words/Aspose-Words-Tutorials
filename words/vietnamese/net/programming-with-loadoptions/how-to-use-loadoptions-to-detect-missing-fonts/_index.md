---
category: general
date: 2026-06-08
description: Tìm hiểu cách sử dụng LoadOptions trong Aspose.Words để phát hiện phông
  chữ thiếu khi nhập tài liệu. Hướng dẫn từng bước kèm mã nguồn, giải thích và các
  thực tiễn tốt nhất.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: vi
og_description: Cách sử dụng LoadOptions trong Aspose.Words và phát hiện phông chữ
  thiếu khi tải tài liệu. Hướng dẫn đầy đủ kèm mã nguồn và các mẹo thực tế.
og_title: Cách sử dụng LoadOptions để phát hiện phông chữ thiếu
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Cách sử dụng LoadOptions để phát hiện phông chữ thiếu
url: /vi/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Sử Dụng LoadOptions Để Phát Hiện Phông Chữ Thiếu

Bạn đã bao giờ tự hỏi **cách sử dụng LoadOptions** khi tải một tài liệu Word bằng Aspose.Words chưa? Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn chính xác **cách sử dụng LoadOptions** để **phát hiện phông chữ thiếu** và xử lý chúng một cách khéo léo. Dù bạn đang xây dựng dịch vụ chuyển đổi tài liệu hay một công cụ báo cáo, phông chữ thiếu có thể gây ra những bất ngờ về bố cục, vì vậy việc phát hiện sớm là điều cần thiết.

Chúng tôi sẽ hướng dẫn từng bước—từ việc gắn một callback cảnh báo đến việc giải thích kết quả—để bạn có thể hoàn thành với một ví dụ C# hoạt động đầy đủ, có thể đưa vào bất kỳ dự án .NET nào. Không cần tài liệu bên ngoài, chỉ một giải pháp tự chứa. Khi kết thúc, bạn sẽ hiểu tại sao hệ thống cảnh báo tồn tại, cách kích hoạt nó và cần làm gì khi callback được kích hoạt.

## Yêu Cầu Trước

- **Aspose.Words for .NET** (bất kỳ phiên bản mới nào; API chúng tôi sử dụng đã ổn định từ năm 2022).
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code với tiện ích mở rộng C#).
- Một tệp Word mẫu (`input.docx`) mà tham chiếu tới một phông chữ bạn *không* có cài đặt trên máy.

Đó là tất cả—không cần gói NuGet bổ sung nào ngoài Aspose.Words.

## Cách Sử Dụng LoadOptions Với Aspose.Words

Lớp **LoadOptions** là cổng vào để tùy chỉnh cách một tài liệu được đọc. Bằng cách gắn một callback cảnh báo vào nó, bạn có thể **phát hiện phông chữ thiếu** ngay khi Aspose.Words phân tích tệp. Hãy cùng phân tích.

### Bước 1: Tạo Trình Xử Lý Cảnh Báo

Aspose.Words sử dụng giao diện `IWarningCallback` để thông báo cho bạn về các vấn đề không quan trọng, chẳng hạn như việc thay thế phông chữ. Triển khai giao diện này và quyết định hành động khi một cảnh báo xuất hiện.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Tại sao điều này quan trọng:**  
Nếu không có callback, Aspose.Words sẽ im lặng thay thế các phông chữ thiếu bằng một phông chữ mặc định (thường là Arial). Bằng cách bắt cảnh báo `FontSubstitution`, bạn có thể ghi lại vấn đề, thông báo cho người dùng, hoặc thậm chí thay thế phông chữ thiếu bằng một phông chữ dự phòng tùy chỉnh.

### Bước 2: Gắn Trình Xử Lý Vào LoadOptions

Bây giờ chúng ta tạo một thể hiện `LoadOptions` và chỉ định nó sử dụng `FontWarningHandler` của chúng ta. Đây là lúc **cách sử dụng LoadOptions** thực sự tỏa sáng.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Tại sao điều này quan trọng:**  
`LoadOptions` là một điểm duy nhất cho nhiều cài đặt khi nhập (mã hoá, mật khẩu, v.v.). Bằng cách đặt `WarningCallback`, bạn kích hoạt một cơ chế nhẹ, dựa trên sự kiện, hoạt động cho bất kỳ tài liệu nào bạn tải với các tùy chọn này.

### Bước 3: Tải Tài Liệu Sử Dụng Các Tùy Chọn Đã Cấu Hình

Cuối cùng, chúng ta truyền `LoadOptions` vào hàm khởi tạo `Document`. Nếu tệp nguồn tham chiếu tới một phông chữ chưa được cài đặt, Aspose.Words sẽ kích hoạt cảnh báo và trình xử lý của bạn sẽ in ra một thông báo.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Bạn sẽ thấy:**  
Giả sử `input.docx` sử dụng một phông chữ có tên *“MyCustomFont”* mà không có trên máy, đầu ra console sẽ trông như sau:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Nếu mọi phông chữ đều có, callback sẽ im lặng—không có đầu ra, không ảnh hưởng tới hiệu năng.

## Phát Hiện Phông Chữ Thiếu Bằng Callback Cảnh Báo (Từ Khóa Phụ Trong Hành Động)

Cụm từ **detect missing fonts** xuất hiện tự nhiên trong tiêu đề ở trên, củng cố từ khóa phụ. Hãy khám phá một vài biến thể mà bạn có thể gặp trong các dự án thực tế.

### Nhiều Tài Liệu Trong Vòng Lặp

Thường bạn sẽ xử lý một loạt tệp. Cùng một thể hiện `LoadOptions` có thể được tái sử dụng, nhưng hãy nhớ rằng `WarningCallback` tồn tại qua các lần tải. Nếu bạn cần cách ly từng tài liệu, hãy tạo một `LoadOptions` mới cho mỗi vòng lặp.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Logic Thay Thế Phông Chữ Tùy Chỉnh

Thay vì chỉ ghi log, bạn có thể muốn thay thế một phông chữ thiếu cụ thể bằng một lựa chọn được công ty phê duyệt. Mở rộng trình xử lý:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Bây giờ bạn không chỉ **phát hiện phông chữ thiếu**, mà còn quyết định cách thay thế chúng.

### Tắt Các Cảnh Báo Không Muốn

Nếu bạn chỉ quan tâm đến các vấn đề về phông chữ và muốn loại bỏ mọi cảnh báo khác, hãy lọc theo `WarningType` như minh họa. Ngược lại, để ghi lại *tất cả* cảnh báo, hãy bỏ kiểm tra `if` và xuất `info.WarningType` cùng với `info.Description`.

## Ví Dụ Đầy Đủ, Có Thể Chạy

Kết hợp tất cả lại, đây là một chương trình hoàn chỉnh mà bạn có thể biên dịch và chạy. Thay thế `"YOUR_DIRECTORY/input.docx"` bằng đường dẫn tới tệp thử nghiệm của bạn.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Đầu ra console dự kiến (khi một phông chữ bị thiếu):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Nếu không có phông chữ nào bị thiếu, bạn sẽ chỉ thấy:

```
Document loaded successfully.
```

## Những Sai Lầm Thường Gặp & Mẹo Chuyên Nghiệp

- **Sai lầm:** Quên thiết lập `WarningCallback`. API vẫn sẽ thay thế phông chữ, nhưng bạn sẽ không bao giờ biết điều đó đã xảy ra.  
  **Mẹo chuyên nghiệp:** Luôn gắn một trình xử lý khi bạn cần độ chính xác về phông chữ; chi phí gần như không đáng kể.
- **Pitfall:**

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoàn chỉnh, kèm theo giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}