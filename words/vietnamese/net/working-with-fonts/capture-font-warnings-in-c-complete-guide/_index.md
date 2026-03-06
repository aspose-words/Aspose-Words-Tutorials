---
category: general
date: 2026-03-06
description: Ghi lại cảnh báo phông chữ khi tải tài liệu Word bằng C#. Học cách phát
  hiện phông chữ thiếu, kiểm tra phông chữ trong tài liệu và xử lý phông chữ thiếu
  một cách hiệu quả.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: vi
og_description: Ghi lại cảnh báo phông chữ khi tải tài liệu Word trong C#. Hướng dẫn
  này chỉ cách phát hiện phông chữ thiếu, kiểm tra phông chữ trong tài liệu và xử
  lý phông chữ thiếu.
og_title: Ghi lại Cảnh báo Font trong C# – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Font Management
title: Bắt cảnh báo phông chữ trong C# – Hướng dẫn đầy đủ
url: /vi/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Phông chữ trong C# – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **ghi lại cảnh báo phông chữ** khi xử lý tài liệu Word chưa? Ghi lại cảnh báo phông chữ là cần thiết để **phát hiện phông chữ thiếu** và đảm bảo kết quả cuối cùng hiển thị chính xác như bạn mong muốn.  

Trong tutorial này chúng ta sẽ đi qua một ví dụ thực tế, từ đầu tới cuối, tải một tệp `.docx`, giám sát quá trình tải và báo cáo bất kỳ sự thay thế phông chữ nào. Khi kết thúc, bạn sẽ biết cách **load word document** một cách an toàn, **check document fonts**, và **handle missing fonts** mà không gặp lỗi runtime bất ngờ.

## Những gì bạn sẽ học

- Cách gắn một bộ thu thập cảnh báo vào `Document` của Aspose.Words.  
- Các loại cảnh báo nào cho biết phông chữ bị thiếu hoặc đã được thay thế.  
- Cách ghi log hoặc phản hồi các cảnh báo này trong một ứng dụng cấp sản xuất.  
- Mẹo cấu hình nguồn phông chữ tùy chỉnh nếu bạn cần **handle missing fonts** một cách linh hoạt.

> **Prerequisite:** Bạn đã có giấy phép hợp lệ cho Aspose.Words for .NET (hoặc đang dùng bản dùng thử miễn phí) và môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code). Không cần thư viện nào khác.

---

## Ghi lại Cảnh báo Phông chữ – Từng Bước

Dưới đây là toàn bộ mã có thể chạy được. Mỗi phần được tách ra thành một bước riêng để bạn có thể sao chép‑dán, thử nghiệm và mở rộng logic.

![Capture font warnings diagram](image.png "Diagram showing warning collection"){: alt="capture font warnings diagram"}

### Bước 1: Load Word Document

Đầu tiên, chúng ta cần **load word document** có thể chứa các phông chữ chưa được cài đặt trên máy hiện tại. Hàm khởi tạo `Document` thực hiện phần lớn công việc, nhưng chúng ta sẽ tách lời gọi này ra để bạn có thể thay thế bằng stream hoặc mảng byte sau này nếu cần.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Why this matters:** Loading a document without a warning handler means any font substitution is silently ignored. By setting `WarningCallback` *before* the load we guarantee we’ll see every `FontSubstitution` warning that occurs.

### Bước 2: Gắn Bộ Thu Thập Cảnh Báo

Lớp `WarningInfoCollector` là một triển khai sẵn có của `IWarningCallback`. Nó chỉ đơn giản lưu mỗi cảnh báo vào một danh sách để chúng ta có thể kiểm tra sau.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Pro tip:** Nếu bạn cần **handle missing fonts** một cách quyết liệt hơn (ví dụ: dừng quá trình tải hoặc thay thế bằng một phông chữ fallback cụ thể), bạn có thể thay `Console.WriteLine` bằng logic tùy chỉnh — ném ngoại lệ, ghi vào file, hoặc thậm chí thêm nguồn phông chữ tùy chỉnh.

### Bước 3: Xác Minh Kết Quả

Chạy chương trình từ console. Nếu `input.docx` của bạn sử dụng phông chữ chưa được cài, bạn sẽ thấy các dòng như:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Nếu không có đầu ra nào xuất hiện, tài liệu hoặc chỉ dùng những phông chữ đã có **hoặc** Aspose.Words đã tìm thấy một phông chữ phù hợp trong bộ sưu tập fallback tích hợp. Dù sao, bạn đã **checked document fonts** thành công.

---

## Phát hiện Phông chữ Thiếu mà Không Cần Giấy Phép (Dùng Bản Dùng Thử)

Ngay cả khi bạn đang dùng bản dùng thử 30 ngày, cơ chế cảnh báo vẫn hoạt động giống hệt. Điểm khác duy nhất là bản dùng thử sẽ thêm watermark vào đầu ra, **không** ảnh hưởng tới việc thu thập cảnh báo. Vì vậy bạn có thể an toàn **detect missing fonts** trước khi quyết định mua giấy phép đầy đủ.

---

## Xử lý Phông chữ Thiếu – Các Tùy chọn Nâng cao

Đôi khi bạn muốn cung cấp các tệp phông chữ riêng (ví dụ: phông chữ thương hiệu công ty) để việc thay thế không bao giờ xảy ra. Aspose.Words cho phép bạn đăng ký các thư mục phông chữ tùy chỉnh:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Đặt đoạn mã trên **trước** khi tải tài liệu nếu bạn muốn loader cân nhắc các phông chữ này trong giai đoạn phân tích ban đầu. Đây là cách đáng tin cậy nhất để **handle missing fonts** mà không phụ thuộc vào phông chữ hệ thống mặc định.

---

## Những Sai Lầm Thường Gặp & Cách Tránh

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Warning collector attached after loading** | Tài liệu đã được phân tích, vì vậy không có cảnh báo nào được ghi lại. | Gắn `WarningCallback` **before** gọi `new Document(path)`. |
| **Only generic warnings appear** | Bạn đã lọc sai `WarningType`. | Sử dụng `WarningType.FontSubstitution` để tập trung vào vấn đề phông chữ. |
| **No output despite missing fonts** | Aspose.Words đã tìm thấy fallback tích hợp (ví dụ: Arial). | Tắt fallback tích hợp bằng `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Performance hit when scanning large docs** | Thu thập mọi cảnh báo có thể tốn tài nguyên. | Giới hạn thu thập chỉ ở `FontSubstitution`, hoặc xử lý cảnh báo theo lô. |

---

## Ví dụ Hoàn chỉnh (Sẵn sàng Sao chép‑Dán)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Expected console output** (giả sử có hai phông chữ bị thiếu):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Nếu console chỉ hiển thị “Document loaded successfully” mà không có gì khác, bạn đã **checked document fonts** và không phát hiện phông chữ nào thiếu.

---

## Kết luận

Chúng tôi đã chỉ cho bạn cách **capture font warnings** trong C# bằng Aspose.Words, một phương pháp đáng tin cậy để **detect missing fonts**, **load word document** an toàn, **check document fonts**, và **handle missing fonts** thông qua nguồn phông chữ tùy chỉnh.  

Với mẫu này, bạn có thể tích hợp kiểm tra phông chữ vào bất kỳ quy trình tự động nào — dù bạn đang tạo PDF, chuyển đổi sang HTML, hay chỉ đơn giản lưu trữ các tệp Word.

### Tiếp theo là gì?

- Khám phá API **FontSettings.SubstitutionSettings** để định nghĩa các quy tắc fallback riêng.  
- Kết hợp việc thu thập cảnh báo với framework ghi log (Serilog, NLog) để giám sát trong môi trường production.  
- Áp dụng cùng một cách tiếp cận để ghi lại các loại cảnh báo khác, như độ phân giải ảnh hoặc tính năng không được hỗ trợ.

Có câu hỏi nào thêm về việc xử lý phông chữ hoặc Aspose.Words nói chung? Hãy để lại bình luận hoặc tham gia diễn đàn cộng đồng Aspose. Chúc bạn lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng phông chữ mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}