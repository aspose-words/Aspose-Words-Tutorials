---
category: general
date: 2026-04-24
description: Cách phát hiện việc thay thế phông chữ bị thiếu trong Aspose.Words bằng
  C#. Hướng dẫn này chỉ cho bạn cách xử lý phông chữ thiếu một cách đáng tin cậy bằng
  các cảnh báo FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: vi
og_description: Cách phát hiện việc thay thế phông chữ bị thiếu trong Aspose.Words
  bằng C#. Tìm hiểu cách xử lý phông chữ thiếu bằng cảnh báo FontSettings.
og_title: Cách phát hiện thay thế trong Aspose.Words – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Cách phát hiện thay thế trong Aspose.Words – Xử lý phông chữ thiếu
url: /vi/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách phát hiện thay thế trong Aspose.Words – Xử lý phông chữ thiếu

Bạn đã bao giờ tự hỏi **cách phát hiện thay thế** khi một tài liệu cố gắng sử dụng một phông chữ không được cài đặt trên máy chủ của bạn chưa? Đây là một vấn đề phổ biến, đặc biệt khi bạn tạo PDF hoặc tệp Word trong một quy trình tự động. Tin tốt là Aspose.Words cung cấp cho bạn một hook tích hợp để phát hiện chính xác tình huống đó, và bạn cũng có thể **xử lý phông chữ thiếu** một cách khéo léo.

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ thực tế cho thấy **cách phát hiện thay thế** thông qua sự kiện `FontSettings.Warning`, và chúng tôi sẽ giải thích cách **xử lý phông chữ thiếu** mà không làm gián đoạn luồng xử lý của bạn. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy, hiểu rõ lý do mỗi dòng quan trọng, và một vài mẹo để tránh các bẫy thường gặp.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Framework)
- Aspose.Words cho .NET (gói NuGet `Aspose.Words`) – phiên bản 23.11 hoặc mới hơn
- Một tài liệu mẫu tham chiếu tới một phông chữ bạn chưa cài đặt (ví dụ, `MissingFont.docx`)
- Visual Studio, VS Code, hoặc bất kỳ IDE C# nào bạn thích  

Không cần cấu hình bổ sung nào ngoài việc thêm gói NuGet.

---

## Cách phát hiện thay thế với FontSettings

Cốt lõi của **cách phát hiện thay thế** nằm trong sự kiện `FontSettings.Warning`. Khi Aspose.Words không thể tìm thấy phông chữ được yêu cầu, nó sẽ phát ra cảnh báo `WarningType.FontSubstitution`. Bằng cách đăng ký sự kiện này, bạn sẽ nhận được thông báo thời gian thực, bao gồm tên phông chữ gốc và phông chữ được sử dụng làm dự phòng.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Tại sao cách này hoạt động:**  
- `LoadOptions.FontSettings` cho Aspose.Words biết sử dụng đối tượng `FontSettings` mà bạn vừa tạo.  
- Đăng ký vào `Warning` cung cấp cho bạn một nơi duy nhất để giám sát *tất cả* các vấn đề liên quan đến phông chữ, không chỉ phông chữ thiếu.  
- Bộ lọc `WarningType.FontSubstitution` đảm bảo bạn chỉ phản hồi với kịch bản chính xác mà bạn quan tâm – bản chất của **cách phát hiện thay thế**.

### Kết quả mong đợi

Chạy đoạn mã trên với một tài liệu tham chiếu tới một phông chữ không tồn tại sẽ in ra một thứ gì đó như sau:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Nếu tài liệu chỉ sử dụng các phông chữ đã được cài đặt, console sẽ không in gì – một tín hiệu rõ ràng rằng **cách phát hiện thay thế** đã thành công mà không có cảnh báo sai.

---

## Xử lý phông chữ thiếu một cách khéo léo

Phát hiện một sự thay thế chỉ là một nửa cuộc chiến; bạn cũng cần một chiến lược để **xử lý phông chữ thiếu** để đầu ra cuối cùng hiển thị như mong muốn. Dưới đây là ba cách tiếp cận thực tế mà bạn có thể kết hợp.

### 1. Cung cấp thư mục phông chữ dự phòng

Aspose.Words có thể tìm kiếm các thư mục bổ sung cho phông chữ. Bằng cách chỉ định một thư mục chứa các phông chữ phổ biến mà bạn mong đợi, bạn giảm thiểu khả năng xảy ra thay thế hoàn toàn.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Tại sao:** Khi phông chữ gốc bị thiếu, Aspose.Words bây giờ có một tập hợp các lựa chọn thay thế đã biết, thường mang lại kết quả hình ảnh dự đoán được hơn.

### 2. Thay thế phông chữ thiếu bằng mã

Nếu bạn muốn kiểm soát hoàn toàn, bạn có thể thay thế phông chữ thiếu bằng một phông chữ cụ thể sau khi phát hiện.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Tại sao:** Điều này cho engine biết chính xác phông chữ nào sẽ được thử, cho phép bạn thực thi thương hiệu công ty hoặc tiêu chuẩn truy cập.

### 3. Ghi log và hủy (Khi việc thay thế không chấp nhận được)

Đôi khi một phông chữ thiếu có nghĩa là tài liệu không hợp lệ cho trường hợp sử dụng của bạn (ví dụ, các mẫu pháp lý). Trong trường hợp đó, bạn có thể ném một ngoại lệ ngay khi xảy ra sự thay thế.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Tại sao:** Sự thất bại ngay lập tức ngăn ngừa các lỗi ở các bước tiếp theo, như bảng lệch vị trí hoặc chữ ký bị hỏng.

---

## Ví dụ hoạt động đầy đủ – Tất cả các bước kết hợp

Dưới đây là một chương trình duy nhất, sẵn sàng sao chép‑dán, minh họa **cách phát hiện thay thế** *và* một số cách **xử lý phông chữ thiếu**. Bạn có thể bình luận các phần mà không cần.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Điều sẽ xảy ra:**  
- Nếu `MissingFont.docx` tham chiếu tới một phông chữ không có trên máy, console sẽ in cảnh báo thay thế.  
- Tệp `Processed.docx` đã lưu sẽ sử dụng phông chữ dự phòng mà bạn cấu hình (hoặc mặc định của thư viện).  
- Không có ngoại lệ chưa được xử lý xuất hiện trừ khi bạn cố ý hủy khi có sự thay thế.

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| *Nếu tài liệu chứa nhiều phông chữ thiếu thì sao?* | Sự kiện cảnh báo sẽ được kích hoạt cho **mỗi** lần thay thế, vì vậy bạn sẽ thấy nhiều dòng. Bạn có thể tổng hợp chúng thành một danh sách để tạo báo cáo tóm tắt. |
| *Điều này có hoạt động với chuyển đổi PDF không?* | Chắc chắn. Các `FontSettings` tương tự được tôn trọng khi bạn gọi `doc.Save("out.pdf")`. Cảnh báo thay thế vẫn được kích hoạt, cho phép bạn xác minh độ chính xác hình ảnh của PDF. |
| *Tôi có thể phát hiện thay thế sau khi tài liệu đã được tải không?* | Không trực tiếp. Cảnh báo được đưa ra **trong quá trình** tải hoặc lưu. Nếu bạn cần phân tích sau khi tải, hãy ghi lại các cảnh báo vào một bộ sưu tập trong giai đoạn tải. |
| *Còn các phông chữ tùy chỉnh được nhúng trong DOCX thì sao?* | Các phông chữ được nhúng được coi là có sẵn, vì vậy không có sự thay thế nào xảy ra. Nếu phông chữ nhúng bị hỏng, Aspose.Words vẫn phát ra cảnh báo, bạn có thể bắt nó theo cùng cách. |
| *Có ảnh hưởng tới hiệu năng không?* | Tối thiểu. Kiểm tra cảnh báo nhẹ, chi phí thực sự là việc tải tài liệu. Thêm thư mục phông chữ có thể làm tăng thời gian tìm kiếm hơi lâu, nhưng chỉ trong lần tải đầu tiên. |

---

## Mẹo chuyên nghiệp & Những sai lầm cần tránh

- **Mẹo chuyên nghiệp:** Luôn đặt `recursive: true` khi chỉ định một thư mục có nhiều phông chữ; nếu không, các thư mục con sẽ bị bỏ qua.  
- **Cẩn thận:** Độ nhạy chữ hoa/chữ thường trên Linux. Tên phông chữ không phân biệt hoa thường trên Windows nhưng trên Linux thì có, vì vậy hãy sử dụng tên chính xác hoặc thêm cả hai biến thể.  
- **Nhớ:** Nếu bạn chạy trong môi trường container, hãy chắc chắn rằng thư mục phông chữ là một phần của image hoặc được gắn tại thời gian chạy.  
- **Mẹo:** Lưu các cảnh báo vào một `List<string>` nếu bạn cần trình bày bản tóm tắt cho người dùng cuối hoặc ghi chúng vào hệ thống giám sát.

---

## Kết luận

Chúng tôi đã trình bày **cách phát hiện thay thế** các phông chữ thiếu trong Aspose.Words, cho bạn thấy một số cách **xử lý phông chữ thiếu**, và cung cấp một ví dụ hoàn chỉnh, có thể chạy được mà bạn có thể đưa vào bất kỳ dự án .NET nào. Bằng cách sử dụng sự kiện `FontSettings.Warning`, bạn có được khả năng quan sát thời gian thực các vấn đề về phông chữ, và với các thư mục dự phòng hoặc quy tắc thay thế rõ ràng, bạn giữ cho đầu ra luôn hiển thị đúng như mong muốn.

Sẵn sàng cho bước tiếp theo? Hãy thử mở rộng giải pháp để tự động nhúng phông chữ dự phòng vào PDF được tạo, hoặc kết nối trình xử lý cảnh báo vào dịch vụ ghi log trung tâm cho các pipeline tài liệu quy mô lớn. Các mẫu chúng tôi đã thảo luận hôm nay—phát hiện dựa trên sự kiện, dự phòng khéo léo, và xử lý lỗi rõ ràng—có thể áp dụng cho nhiều API Aspose khác, vì vậy bạn đã sẵn sàng giải quyết các thách thức liên quan đến phông chữ trên toàn bộ.

Có thêm câu hỏi nào về xử lý phông chữ, chuyển đổi PDF, hoặc các thủ thuật Aspose.Words không? Hãy để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}