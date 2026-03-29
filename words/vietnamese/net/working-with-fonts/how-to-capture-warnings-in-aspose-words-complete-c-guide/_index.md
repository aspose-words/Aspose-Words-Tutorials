---
category: general
date: 2026-03-28
description: Cách bắt các cảnh báo khi tải DOCX bằng Aspose.Words và nhận thông báo
  cảnh báo về phông chữ thiếu. Học cách xử lý phông chữ thiếu một cách hiệu quả.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: vi
og_description: Cách bắt các cảnh báo khi tải DOCX bằng Aspose.Words, lấy thông báo
  cảnh báo và xử lý phông chữ thiếu với các ví dụ mã thực tế.
og_title: Cách bắt cảnh báo trong Aspose.Words – Hướng dẫn C# đầy đủ
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách bắt các cảnh báo trong Aspose.Words – Hướng dẫn C# đầy đủ
url: /vi/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Thu Thập Cảnh Báo trong Aspose.Words – Hướng Dẫn Đầy Đủ C#

Bạn đã bao giờ tự hỏi **cách thu thập các cảnh báo** xuất hiện khi tải một tài liệu Word bằng Aspose.Words chưa? Có thể bạn đang thấy các thay đổi phông chữ lạ và muốn biết chính xác nguyên nhân. Nói ngắn gọn, bạn có thể gắn vào hệ thống cảnh báo của thư viện, **lấy các thông điệp cảnh báo**, và thậm chí **xử lý các phông chữ thiếu** trước khi chúng làm hỏng bố cục của bạn.  

Trong hướng dẫn này, chúng ta sẽ đi qua một kịch bản thực tế: tải một tệp DOCX, thu thập mọi cảnh báo mà engine phát sinh, và in ra chi tiết về bất kỳ việc thay thế phông chữ nào xảy ra. Khi kết thúc, bạn sẽ có một mẫu mã sẵn sàng chạy, hiểu “tại sao” đằng sau mỗi bước, và biết cách mở rộng phương pháp này cho các dự án của mình.

## Những Điều Bạn Sẽ Học

- Cách cấu hình `LoadOptions` để tự động thu thập các cảnh báo.  
- Cách **lấy các thông điệp cảnh báo** từ `WarningInfoCollection`.  
- Cách xác định và phản hồi **phông chữ thiếu** thông qua cờ `WarningType.FontSubstitution`.  
- Một số mẹo để khắc phục các trường hợp đặc biệt, chẳng hạn như tài liệu có phông chữ nhúng hoặc thư mục phông chữ tùy chỉnh.  

Không cần tham chiếu bên ngoài – mọi thứ bạn cần đều có ở đây.

---

## Điều Kiện Tiên Quyết

- .NET 6.0 trở lên (mã cũng hoạt động trên .NET Framework 4.7+).  
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Một tệp DOCX mẫu (`input.docx`) mà có thể thiếu một số phông chữ hoặc sử dụng các phông chữ không được cài đặt trên máy của bạn.  

Đó là tất cả. Nếu bạn đã quen với C# và Visual Studio, bạn có thể sao chép‑dán mã và chạy ngay lập tức.

---

## Bước 1: Chuẩn Bị Load Options và Callback Cảnh Báo

Điều đầu tiên Aspose.Words thực hiện khi bạn gọi `new Document(path, loadOptions)` là phân tích tệp. Trong quá trình phân tích, nó có thể gặp phông chữ thiếu, tính năng không hỗ trợ, hoặc markup đã lỗi thời. Để bắt những sự kiện này, bạn cần một đối tượng **callback cảnh báo**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Tại sao điều này quan trọng:** Nếu không có callback, Aspose.Words sẽ im lặng ghi cảnh báo vào console (hoặc bỏ qua chúng), khiến bạn không biết được các việc thay thế phông chữ có thể ảnh hưởng đến bố cục. Bằng cách cung cấp một `WarningInfoCollection` riêng, bạn sẽ có toàn bộ tầm nhìn.

> **Mẹo chuyên nghiệp:** Nếu bạn chỉ quan tâm đến các cảnh báo liên quan đến phông chữ, bạn có thể lọc sau – nhưng việc thu thập *tất cả* cảnh báo sẽ tạo một lưới an toàn cho các vấn đề trong tương lai.

---

## Bước 2: Tải Tài Liệu Với Các Tuỳ Chọn Đã Cấu Hình

Bây giờ callback đã sẵn sàng, hãy tải tệp. Hàm khởi tạo `Document` sẽ tự động gọi callback cho bất kỳ vấn đề nào nó phát hiện.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Điều gì đang diễn ra phía sau?** Aspose.Words phân tích Open XML, giải quyết các style, và cố gắng ánh xạ mỗi tham chiếu phông chữ tới một phông chữ đã được cài đặt trên hệ thống. Nếu không tìm thấy khớp, nó sẽ tạo một mục `WarningInfo` loại `FontSubstitution`.

---

## Bước 3: Lấy Và Kiểm Tra Các Cảnh Báo Đã Thu Thập

Sau khi việc tải hoàn tất, `warningCollector` của bạn hiện chứa mọi cảnh báo đã xảy ra. Hãy lấy chúng ra và tập trung vào các thông điệp thay thế phông chữ.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Kết quả mẫu** (console của bạn có thể hiển thị tương tự):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Nếu bạn muốn *tất cả* các cảnh báo, chỉ cần bỏ qua câu lệnh `if` hoặc ghi `warning.Type` cho mỗi mục.

---

## Bước 4: Xử Lý Phông Chữ Thiếu – Ngoài Việc Ghi Log

Thu thập cảnh báo là hữu ích, nhưng thường bạn cần **xử lý phông chữ thiếu** một cách lập trình. Dưới đây là hai chiến lược phổ biến:

### 4.1 Thay Thế Phông Chữ Thiếu Bằng Một Phông Chữ Dự Phòng Cụ Thể

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Bây giờ bất kỳ phông chữ nào thiếu sẽ được thay thế bằng *Calibri* thay vì fallback mặc định của thư viện.

### 4.2 Nhúng Phông Chữ Thay Thế Một Cách Động

Nếu bạn có một tệp phông chữ tùy chỉnh (ví dụ, `MyFallback.ttf`) bạn có thể đăng ký nó tại thời gian chạy:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Cách tiếp cận này hữu ích khi bạn phân phối một phông chữ công ty cụ thể cùng với ứng dụng của mình.

> **Trường hợp đặc biệt:** Các tài liệu đã nhúng sẵn phông chữ cần thiết sẽ bỏ qua các quy tắc thay thế hệ thống. Trong trường hợp đó, bộ sưu tập cảnh báo sẽ rỗng cho phông chữ đó, và đó chính là điều bạn muốn.

---

## Bước 5: Ví Dụ Hoàn Chỉnh (Sẵn Sàng Sao Chép‑Dán)

Dưới đây là một chương trình tự chứa thể hiện mọi thứ từ đầu đến cuối. Chỉ cần thay `YOUR_DIRECTORY/input.docx` bằng đường dẫn tới tệp thử nghiệm của bạn.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Bạn sẽ nhận được gì**

- Console in ra mọi cảnh báo thay thế phông chữ, kèm biểu tượng cảnh báo để dễ nhìn.  
- Tệp DOCX đầu ra (`output.docx`) sẽ sử dụng *Calibri* ở mọi vị trí mà phông chữ bị thiếu được phát hiện.  
- Không có ngoại lệ chưa được xử lý – hệ thống cảnh báo sẽ xử lý một cách êm ái bất kỳ phông chữ không xác định nào.

---

## Câu Hỏi Thường Gặp & Trả Lời

**H: Điều này có hoạt động với PDF được tạo từ Word không?**  
Đ: Có. Aspose.Words coi PDF là một định dạng xuất ra khác. Việc thu thập cảnh báo diễn ra trong giai đoạn *load*, vì vậy nó không phụ thuộc vào quá trình xuất cuối cùng.

**H: Nếu tôi muốn thu thập cảnh báo cho **tất cả** các thao tác tài liệu (lưu, chuyển đổi, v.v.) thì sao?**  
Đ: Bạn có thể tái sử dụng cùng một `WarningInfoCollection` bằng cách gán nó cho `Document.WarningCallback` sau khi tài liệu được khởi tạo. Mọi thao tác tiếp theo sẽ đẩy các mục mới vào cùng một bộ sưu tập.

**H: Callback cảnh báo có ảnh hưởng tới hiệu năng không?**  
Đ: Rất ít. Bộ sưu tập chỉ đơn giản lưu trữ các đối tượng; trừ khi bạn xử lý hàng ngàn cảnh báo trong một vòng lặp chặt chẽ, bạn sẽ không cảm nhận được sự chậm lại.

**H: Làm sao để loại bỏ các cảnh báo mà tôi không quan tâm?**  
Đ: Triển khai một lớp tùy chỉnh kế thừa `IWarningCallback` và lọc bên trong phương thức `Warning`. `WarningInfoCollection` tích hợp chỉ lưu, không lọc.

---

## Mẹo Chuyên Nghiệp & Những Cạm Bẫy

- **Mẹo:** Luôn kiểm tra `Warning.Description` – nó chứa tên phông chữ chính xác đã bị thiếu. Điều này giúp bạn quyết định có nên đóng gói phông chữ cùng ứng dụng hay không.  
- **Cảnh giác với phông chữ nhúng:** Nếu DOCX nguồn đã nhúng phông chữ cần thiết, Aspose.Words sẽ không phát sinh cảnh báo thay thế, ngay cả khi phông chữ không được cài đặt trên máy local.  
- **An toàn đa luồng:** `WarningInfoCollection` không phải là thread‑safe. Nếu bạn tải nhiều tài liệu đồng thời, hãy cung cấp cho mỗi luồng một bộ sưu tập riêng.  
- **Kiểm tra phiên bản:** API cảnh báo đã ổn định từ Aspose.Words 20.8. Đảm bảo bạn đang dùng phiên bản mới để tránh bỏ sót các loại cảnh báo mới hơn.

---

## Kết Luận

Chúng ta đã bao quát **cách thu thập cảnh báo** từ Aspose.Words, trình bày cách **lấy các thông điệp cảnh báo**, và chỉ ra các cách thực tiễn để **xử lý phông chữ thiếu** thông qua phông chữ dự phòng hoặc thư mục phông chữ tùy chỉnh. Ví dụ đầy đủ đã sẵn sàng để đưa vào bất kỳ dự án .NET nào, và các khái niệm này có thể mở rộng cho các pipeline tự động lớn hơn.

Tiếp theo, bạn có thể khám phá:

- Sử dụng `Document.WarningCallback` để thu thập cảnh báo trong quá trình **lưu** tài liệu.  
- Ghi log các cảnh báo vào file hoặc hệ thống telemetry để giám sát trong môi trường production.  
- Mở rộng callback để tự động thay thế phông chữ thiếu bằng các kiểu chữ mang thương hiệu.

Hãy thoải mái thử nghiệm—đổi phông chữ dự phòng, thêm nhiều tài liệu vào batch, hoặc tích hợp bộ thu thập cảnh báo vào pipeline CI để phát hiện các regression liên quan đến phông chữ. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng như mong đợi!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}