---
category: general
date: 2026-03-08
description: Cài đặt phông chữ tùy chỉnh cho phép bạn thiết lập cài đặt phông chữ,
  tải tài liệu Word một cách an toàn và xử lý các phông chữ thiếu với Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: vi
og_description: Cài đặt phông chữ tùy chỉnh cho phép bạn thiết lập các tùy chọn phông
  chữ, tải tài liệu Word một cách an toàn và xử lý các phông chữ thiếu với Aspose.Words.
og_title: Cài đặt phông chữ tùy chỉnh trong C# – Tải Word và Xử lý phông chữ thiếu
tags:
- Aspose.Words
- C#
- Font Management
title: Cài đặt phông chữ tùy chỉnh trong C# – Tải Word và Xử lý phông chữ thiếu
url: /vi/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

sure no extra spaces.

Now produce final answer with all content.

Let's write translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cài đặt phông chữ tùy chỉnh trong C# – Tải Word & Xử lý phông chữ thiếu

Bạn đã bao giờ tự hỏi cách **cài đặt phông chữ tùy chỉnh** hoạt động khi một tệp Word tham chiếu đến các phông chữ mà bạn không cài đặt không? Đó là một vấn đề phổ biến—tài liệu của bạn trông ổn trên một máy, rồi đột nhiên mọi đoạn văn đều chuyển sang phông chữ dự phòng trên máy khác.  

Tin tốt? Với Aspose.Words, bạn có thể **đặt cài đặt phông chữ**, **tải nội dung tài liệu Word** và **xử lý các phông chữ thiếu** trong một quy trình gọn gàng. Dưới đây bạn sẽ tìm thấy một ví dụ hoàn chỉnh, sẵn sàng chạy, cho thấy chính xác cách thực hiện, cùng với “lý do” cho mỗi bước.

## Những gì bạn sẽ học

Trong hướng dẫn này chúng ta sẽ đề cập tới:

* Tạo một đối tượng `LoadOptions` và gắn một thể hiện `FontSettings`.  
* Đăng ký một callback cảnh báo để bạn có thể xem những phông chữ nào đã được thay thế.  
* Tải một tệp DOCX có thể thiếu phông chữ, và in chi tiết thay thế ra console.  

Khi kết thúc, bạn sẽ có thể phát hành ứng dụng C# của mình một cách tự tin, biết rằng mọi trường hợp phông chữ thiếu đều được ghi lại và có thể xử lý sau.

> **Yêu cầu trước:** Aspose.Words for .NET (v23.12 hoặc mới hơn) được cài đặt qua NuGet, và có kiến thức cơ bản về ứng dụng console C#.

---

## Cài đặt phông chữ tùy chỉnh – Cấu hình LoadOptions

Điều đầu tiên bạn cần là một đối tượng `LoadOptions`. Nó cho Aspose.Words biết cách xử lý tệp đến. Bằng cách gán một thể hiện `FontSettings` mới, chúng ta cung cấp cho thư viện một nơi để tìm kiếm các phông chữ tùy chỉnh.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Tại sao điều này quan trọng:**  
Nếu bạn bỏ qua `FontSettings`, Aspose.Words sẽ quay lại bộ sưu tập phông chữ mặc định của hệ thống. Điều đó có nghĩa là bất kỳ phông chữ nào thiếu sẽ bị thay thế một cách im lặng, và bạn sẽ không biết phông chữ nào đã được hoán đổi. Bằng cách tạo một container `FontSettings` rõ ràng, bạn có toàn quyền kiểm soát quá trình tra cứu.

---

## Đặt cài đặt phông chữ trên LoadOptions

Bây giờ chúng ta đã có một đối tượng `FontSettings`, bạn có thể tự hỏi nên trỏ nó tới đâu. Thông thường bạn sẽ thêm một thư mục chứa các phông chữ mà bạn phân phối cùng ứng dụng:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Nếu bạn không có thư mục riêng, bạn có thể bỏ qua khối này—Aspose.Words vẫn sẽ báo cáo các phông chữ thiếu qua callback cảnh báo.*

**Mẹo chuyên nghiệp:** Sử dụng cờ `recursive: true` nếu các phông chữ của bạn rải rác trong các thư mục con. Điều này giúp bạn không phải thêm từng đường dẫn một cách thủ công.

---

## Tải tài liệu Word với cài đặt phông chữ tùy chỉnh

Với các tùy chọn đã chuẩn bị, việc tải tài liệu trở nên cực kỳ đơn giản. Hàm khởi tạo `Document` nhận đường dẫn tệp và `LoadOptions` mà chúng ta vừa tạo.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Điều gì đang diễn ra phía sau?**  
Aspose.Words phân tích DOCX, kiểm tra mọi tham chiếu `<w:font>`, và tham khảo `FontSettings` mà bạn cung cấp. Nếu không tìm thấy phông chữ, nó sẽ kích hoạt một cảnh báo loại `FontSubstitution`. Trình xử lý tùy chỉnh của chúng ta (được hiển thị ở phần tiếp theo) sẽ bắt các cảnh báo này.

---

## Xử lý phông chữ thiếu với Callback cảnh báo

Giao diện `IWarningCallback` cho phép bạn phản hồi bất kỳ vấn đề nào phát sinh trong quá trình tải. Việc triển khai nó rất đơn giản:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Khi tài liệu được tải, mỗi phông chữ thiếu sẽ tạo ra một dòng như sau:

```
Font substituted: Arial -> Liberation Sans
```

**Tại sao bạn nên ghi lại điều này:**  
Trong môi trường production, bạn có thể chuyển các thông điệp này tới tệp hoặc hệ thống telemetry, giúp dễ dàng phát hiện những phông chữ cần đóng gói hoặc cấp phép.

---

## Ví dụ hoạt động đầy đủ

Dưới đây là một chương trình console tự chứa, kết nối mọi thứ lại với nhau. Sao chép‑dán nó vào một dự án console .NET Core mới và nhấn **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Kết quả mong đợi** (giả sử `input.docx` sử dụng một phông chữ mà bạn không có):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Nếu tất cả các phông chữ đều có, bạn sẽ chỉ thấy dòng xác nhận cuối cùng.

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| **Nếu tôi cần nhúng các phông chữ thiếu vào PDF thì sao?** | Sau khi tải, gọi `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` và sau đó bật nhúng bằng `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Tôi có thể tắt các cảnh báo thay vì ghi chúng không?** | Có—đặt `loadOptions.WarningCallback = null;` hoặc triển khai callback để bỏ qua các cảnh báo không liên quan tới phông chữ. |
| **Điều này có hoạt động với các tệp `.doc` và `.rtf` không?** | Hoàn toàn có. Đối tượng `LoadOptions` giống nhau áp dụng cho bất kỳ định dạng nào được Aspose.Words hỗ trợ. |
| **Callback có an toàn với đa luồng không?** | Callback chạy trên cùng một luồng tải tài liệu, vì vậy bạn có thể ghi an toàn vào console. Đối với các kịch bản đa luồng, hãy sử dụng collection đồng thời hoặc framework logging. |

---

## Mẹo chuyên nghiệp & Những cạm bẫy

* **Mẹo chuyên nghiệp:** Nếu bạn phân phối một phông chữ không được cài đặt trên máy đích, hãy thêm nó vào thư mục bạn truyền cho `SetFontsFolder`. Điều này đảm bảo việc hiển thị luôn xác định.  
* **Cẩn thận với giấy phép:** Một số phông chữ yêu cầu giấy phép thương mại để nhúng. Luôn kiểm tra EULA của phông chữ trước khi đóng gói.  
* **Lưu ý về hiệu năng:** Tải một thư viện phông chữ lớn có thể làm chậm quá trình phân tích tài liệu. Giữ thư mục gọn nhẹ—chỉ bao gồm những phông chữ thực sự cần thiết.  
* **Trường hợp đặc biệt:** Khi một tài liệu tham chiếu một phông chữ bằng *tên PostScript* thay vì tên họ, Aspose.Words vẫn sẽ giải quyết được miễn là tệp phông chữ có trong đường dẫn tìm kiếm.

---

## Kết luận

Bạn giờ đã có một mẫu hoàn chỉnh, sẵn sàng cho môi trường production để sử dụng **cài đặt phông chữ tùy chỉnh** trong C#. Bằng cách cấu hình `LoadOptions`, đăng ký callback cảnh báo, và tùy chọn chỉ tới một thư mục phông chữ riêng, bạn có thể **đặt cài đặt phông chữ**, **tải nội dung tài liệu Word** một cách đáng tin cậy.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}