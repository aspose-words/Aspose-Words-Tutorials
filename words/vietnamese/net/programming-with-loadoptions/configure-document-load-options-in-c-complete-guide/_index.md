---
category: general
date: 2026-06-05
description: Cấu hình các tùy chọn tải tài liệu trong C# để xử lý cảnh báo thay thế
  phông chữ và tùy chỉnh hành vi tải bằng callback cảnh báo.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: vi
og_description: Cấu hình các tùy chọn tải tài liệu trong C# để quản lý cảnh báo thay
  thế phông chữ và tinh chỉnh quá trình tải tài liệu bằng callback cảnh báo.
og_title: Cấu hình các tùy chọn tải tài liệu trong C# – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Cấu hình các tùy chọn tải tài liệu trong C# – Hướng dẫn đầy đủ
url: /vi/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cấu hình tùy chọn tải tài liệu trong C# – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **cấu hình tùy chọn tải tài liệu** trong C# vì hành vi tải mặc định không đáp ứng được yêu cầu? Có thể bạn đang gặp các trường hợp thay thế phông chữ không mong muốn hoặc muốn ghi lại mọi cảnh báo xuất hiện trong quá trình nhập tệp. Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp thực tế, từ đầu tới cuối, không chỉ thiết lập các tùy chọn mà còn minh họa **callback cảnh báo** cho các cảnh báo thay thế phông chữ.

Chúng ta sẽ bao phủ mọi thứ từ đoạn mã ngắn tạo callback cho đến lúc bạn thực sự mở tài liệu với các cài đặt tùy chỉnh. Khi kết thúc, bạn sẽ có một mẫu có thể tái sử dụng trong bất kỳ dự án Aspose.Words nào, dù bạn đang xử lý hoá đơn, hợp đồng pháp lý hay báo cáo đơn giản.

## Những gì bạn sẽ học

- Cách **cấu hình tùy chọn tải tài liệu** bằng `LoadOptions`.
- Cách triển khai **callback cảnh báo** để bắt các cảnh báo `FontSubstitution`.
- Tại sao việc xử lý sớm **cảnh báo thay thế phông chữ** có thể giúp bạn tránh những bất ngờ về bố cục.
- Xử lý các trường hợp biên cho phông chữ thiếu và cách dự phòng một cách nhẹ nhàng.
- Một mẫu mã hoàn chỉnh, có thể sao chép‑dán và chạy ngay hôm nay.

### Yêu cầu trước

- .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.6+).
- Aspose.Words for .NET đã được cài đặt (`dotnet add package Aspose.Words`).
- Kiến thức cơ bản về cú pháp C#.

Nếu bạn đã có những thứ trên, hãy cùng bắt đầu.

## Cấu hình tùy chọn tải tài liệu – Các bước chi tiết

Dưới đây là quy trình đầy đủ được chia thành bốn bước rõ ràng. Mỗi bước được giải thích, sau đó là một khối mã ngắn gọn mà bạn có thể dán thẳng vào Visual Studio.

### Bước 1: Triển khai Callback Cảnh báo cho Thay thế Phông chữ

Đầu tiên—callback cảnh báo là gì? Trong Aspose.Words, nó là một delegate được gọi mỗi khi thư viện gặp phải điều gì đó đáng chú ý, như một phông chữ bị thiếu. Bằng cách bắt `WarningType.FontSubstitution` chúng ta có thể ghi lại chính xác phông chữ mà engine đã thay thế.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Tại sao điều này quan trọng:** Nếu không có callback, thư viện sẽ âm thầm thay thế các phông chữ thiếu, dẫn đến văn bản bị rối trong PDF hoặc DOCX cuối cùng. Khi hiển thị cảnh báo, bạn sẽ có được cái nhìn rõ ràng và có thể quyết định nhúng phông chữ thiếu, chuyển sang dự phòng, hoặc thông báo cho người dùng.

> **Mẹo chuyên nghiệp:** Nếu bạn muốn bắt *tất cả* cảnh báo, hãy bỏ qua câu lệnh `if`. Chỉ cần ghi `warningInfo.Description` cho mọi sự kiện.

### Bước 2: Thiết lập LoadOptions với Callback

Bây giờ chúng ta đã có callback, chúng ta cần **cấu hình tùy chọn tải tài liệu** để thực sự sử dụng nó. `LoadOptions` là một container nhẹ giúp Aspose.Words biết cách hành xử trong quá trình gọi constructor `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Tại sao điều này quan trọng:** Khi gán `WarningCallback`, mọi cảnh báo phát sinh trong giai đoạn tải sẽ được chuyển qua delegate của chúng ta. Bạn cũng có thể điều chỉnh các thuộc tính khác của `LoadOptions` ở đây—như `LoadFormat` nếu bạn biết chính xác loại tệp, hoặc `Password` cho các tài liệu được mã hoá.

### Bước 3: Tải Tài liệu bằng Các Tùy chọn Đã Cấu hình

Với callback đã được kết nối, bước cuối cùng là **tải tài liệu** thực sự. Constructor `Document` nhận một đường dẫn tệp và `LoadOptions` mà chúng ta vừa chuẩn bị.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Nếu tệp nguồn tham chiếu một phông chữ không được cài đặt trên máy, bạn sẽ thấy một dòng như:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

trong console. Phản hồi ngay lập tức này cho phép bạn quyết định có nên đưa phông chữ thiếu kèm theo ứng dụng hay thay thế nó một cách lập trình.

### Bước 4: Tùy chọn – Xác minh Phông chữ Đã Tải (Xử lý Trường hợp Biên)

Đôi khi bạn muốn *kiểm tra trước* tài liệu trước khi tải đầy đủ, đặc biệt trong các kịch bản xử lý hàng loạt. Aspose.Words cung cấp lớp `FontSettings` có thể liệt kê các phông chữ cần thiết.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Khi nào nên dùng:** Nếu bạn duy trì một kho phông chữ riêng (ví dụ: phông chữ thương hiệu công ty), việc chỉ định `FontSettings` tới thư mục đó sẽ giúp engine tìm đúng kiểu chữ mà không phải dựa vào các phông chữ chung.

## Ví dụ Hoạt động Đầy đủ

Dưới đây là toàn bộ chương trình—chỉ cần sao chép, dán và chạy. Nó minh họa mọi thứ từ việc tạo callback đến việc tải tài liệu cuối cùng.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Kết quả mong đợi**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Nếu không có phông chữ nào bị thiếu, callback sẽ im lặng—không có gì cần lo lắng.

## Các Câu hỏi Thường gặp & Trường hợp Biên

### Nếu callback cảnh báo ném ra ngoại lệ thì sao?

Callback chạy trên cùng một luồng tải tài liệu. Ném ngoại lệ bên trong delegate sẽ làm dừng quá trình tải và truyền ngoại lệ lên. Hãy bọc logic của bạn trong `try/catch` nếu cần độ bền cao.

### Tôi có thể ẩn *tất cả* cảnh báo thay vì xử lý chúng không?

Có—đặt `loadOptions.WarningCallback = null;` hoặc cung cấp một callback không làm gì. Tuy nhiên, bạn sẽ mất khả năng nhìn thấy các vấn đề tiềm ẩn.

### Điều này có hoạt động với các tệp DOCX được mã hoá không?

Hoàn toàn có. Chỉ cần thêm `Password = "yourPassword"` vào `LoadOptions` trước khi tạo `Document`. Callback cảnh báo vẫn sẽ được kích hoạt cho các vấn đề phông chữ.

### Điều này khác gì so với việc sử dụng `DocumentBuilder`?

`DocumentBuilder` dùng để *tạo* hoặc *sửa* tài liệu sau khi đã tải. **Cấu hình tùy chọn tải tài liệu** ảnh hưởng đến giai đoạn *phân tích* ban đầu, nơi quyết định thay thế phông chữ được thực hiện.

## Tổng quan Trực quan

![Sơ đồ hiển thị luồng cấu hình tùy chọn tải tài liệu](https://example.com/images/load-options-flow.png "Sơ đồ hiển thị luồng cấu hình tùy chọn tải tài liệu")

*Hình ảnh minh họa luồng: callback → LoadOptions → constructor Document → xử lý cảnh báo.*

## Kết luận

Bây giờ bạn đã biết cách **cấu hình tùy chọn tải tài liệu** trong C# để bắt các cảnh báo thay thế phông chữ, chèn thư mục phông chữ tùy chỉnh và giữ toàn quyền kiểm soát quá trình tải. Mẫu này mang lại cho bạn sự tự tin rằng mọi phông chữ thiếu sẽ được báo cáo, giúp duy trì độ chính xác của tài liệu trên bất kỳ môi trường nào.

Bước tiếp theo? Hãy thử thay thế việc ghi log console bằng một hệ thống telemetry mạnh mẽ hơn, hoặc kết hợp cách tiếp cận này với `DocumentBuilder` để tự động thay thế phông chữ thiếu bằng phông chữ mặc định của công ty. Bạn cũng có thể khám phá các giá trị `WarningType` khác như `DocumentStructure` để có cái nhìn sâu hơn.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng như mong muốn!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Làm chủ Aspose.Words Markdown Load Options trong Python để Nâng cao Xử lý Tài liệu](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Tối ưu hoá Tải Tài liệu với Các Tùy chọn HTML, RTF và TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Sử dụng Document Options và Settings trong Aspose.Words cho Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}