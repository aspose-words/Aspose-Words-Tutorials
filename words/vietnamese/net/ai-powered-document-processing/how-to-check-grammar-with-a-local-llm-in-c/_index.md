---
category: general
date: 2026-03-19
description: Học cách kiểm tra ngữ pháp trong Word bằng LLM cục bộ, đăng ký mô hình
  và lưu tài liệu đã chỉnh sửa — tất cả trong một hướng dẫn C# duy nhất.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: vi
og_description: Cách kiểm tra ngữ pháp trong Word bằng LLM cục bộ, đăng ký mô hình
  và lưu tài liệu đã chỉnh sửa — hướng dẫn từng bước.
og_title: Cách kiểm tra ngữ pháp bằng LLM cục bộ trong C#
tags:
- Aspose.Words
- AI
- C#
title: Cách kiểm tra ngữ pháp bằng LLM cục bộ trong C#
url: /vi/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách kiểm tra ngữ pháp với LLM cục bộ trong C#

Bạn đã bao giờ tự hỏi **cách kiểm tra ngữ pháp** trong một tài liệu Word mà không gửi văn bản của mình lên đám mây chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển muốn sự riêng tư của một mô hình tự lưu trữ đồng thời vẫn nhận được các đề xuất được hỗ trợ bởi AI. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn cách đăng ký một LLM tùy chỉnh, cấu hình Aspose.Words để sử dụng nó, và cuối cùng **cách lưu các tệp đã chỉnh sửa** — tất cả bằng C# thuần.

Chúng tôi cũng sẽ đề cập đến chi tiết **cài đặt llm cục bộ**, cho bạn thấy **cách đăng ký endpoint llm**, và trình bày các bước chính xác để **kiểm tra ngữ pháp trong tài liệu word**. Khi kết thúc, bạn sẽ có một mẫu có thể chạy được mà bạn có thể đưa vào bất kỳ dự án .NET nào.

## Yêu cầu trước

- .NET 6+ SDK (mã hoạt động trên .NET Core và .NET Framework)
- Visual Studio 2022 hoặc VS Code với các extension C#
- Aspose.Words cho .NET (v24.12 hoặc mới hơn) – bạn có thể tải từ NuGet
- Một LLM chạy cục bộ hỗ trợ API tương thích OpenAI (ví dụ: Ollama trên cổng 11434)

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng Ollama, lệnh `ollama serve` sẽ tự động khởi động endpoint `http://localhost:11434/api/generate`.

## Bước 1 – Cách đăng ký llm: Thêm mô hình tùy chỉnh vào Aspose.Words

Điều đầu tiên chúng ta cần làm là thông báo cho Aspose.Words về **llm cục bộ** của chúng ta. Điều này được thực hiện một lần duy nhất khi khởi động ứng dụng.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**Tại sao điều này quan trọng:** Bằng cách đăng ký mô hình, bạn cung cấp cho Aspose.Words một tên định danh (`"local-llm"`). Sau này, khi chúng ta gọi `CheckGrammar`, thư viện sẽ biết chính xác endpoint nào cần truy cập. Bỏ qua bước này sẽ khiến thư viện quay lại sử dụng dịch vụ đám mây tích hợp sẵn, làm mất mục đích của một LLM riêng tư.

## Bước 2 – Tải tài liệu Word bạn muốn phân tích

Bây giờ chúng ta đưa tệp vào bộ nhớ. Bạn có thể chỉ tới bất kỳ tệp `.docx`, `.doc`, hoặc thậm chí `.rtf` nào.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Điều đang xảy ra:** `Document` là mô hình đối tượng cốt lõi của Aspose.Words. Nó phân tích tệp và xây dựng một cây các nút (đoạn văn, bảng, hình ảnh, v.v.). Điều này cho phép engine AI nhắm mục tiêu các đoạn văn bản cụ thể để phân tích ngữ pháp.

## Bước 3 – Cấu hình tùy chọn kiểm tra ngữ pháp (cài đặt llm cục bộ)

Ở đây chúng ta liên kết mô hình đã đăng ký trước đó với hoạt động kiểm tra ngữ pháp.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**Tại sao chúng tôi cung cấp các tùy chọn này:** Các LLM khác nhau có hành vi khác nhau. Bằng cách cung cấp `Model`, Aspose.Words cho phép bạn chuyển đổi giữa mô hình cục bộ và mô hình dựa trên đám mây mà không cần thay đổi bất kỳ mã nào khác. Tính linh hoạt này là cần thiết khi **cài đặt llm cục bộ** trong môi trường tuân thủ hoặc ngoại tuyến.

## Bước 4 – Chạy kiểm tra ngữ pháp dựa trên AI (kiểm tra ngữ pháp trong word)

Khi mọi thứ đã được kết nối, việc kiểm tra ngữ pháp thực tế chỉ cần một dòng lệnh.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**Bên trong:** Aspose.Words trích xuất mỗi câu, gửi tới endpoint LLM, nhận payload JSON với các đề xuất chỉnh sửa, và sau đó áp dụng các chỉnh sửa đó trở lại cây tài liệu. Quá trình này chạy đồng bộ ở đây để đơn giản; bạn cũng có thể gọi phiên bản async `CheckGrammarAsync` nếu muốn I/O không chặn.

## Bước 5 – Cách lưu tài liệu đã chỉnh sửa

Sau khi AI thực hiện xong, bạn sẽ muốn lưu lại các thay đổi.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**Điều mong đợi:** Mở `checked.docx` trong Word và bạn sẽ thấy các lỗi ngữ pháp được đánh dấu (hoặc tự động chỉnh sửa, tùy thuộc vào `AiGrammarCheckOptions` của bạn). Nếu bạn bật theo dõi, bạn cũng sẽ thấy các dấu sửa đổi.

## Ví dụ Hoạt động Đầy đủ

Kết hợp mọi thứ lại, đây là một ứng dụng console sẵn sàng chạy:

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**Kết quả mong đợi trong console:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

Mở `checked.docx` và bạn sẽ thấy các cải thiện ngữ pháp được áp dụng tự động.

## Các Câu hỏi Thường gặp & Trường hợp Cạnh

| Câu hỏi | Câu trả lời |
|----------|--------|
| *Nếu LLM của tôi yêu cầu khóa API thì sao?* | Gửi khóa tới `apiKey` trong `RegisterModel`. Mã này hoạt động cho cả dịch vụ có khóa và không có khóa. |
| *Tôi có thể sử dụng định dạng tệp khác không?* | Chắc chắn. `Document.Save` chấp nhận `.pdf`, `.html`, `.txt`, v.v. Chỉ cần thay đổi phần mở rộng. |
| *Nếu LLM trả về lỗi thì sao?* | Bao quanh `CheckGrammar` bằng try/catch; kiểm tra `AiException` để biết chi tiết. Thường là timeout—cân nhắc tăng `grammarOptions.Timeout`. |
| *Hoạt động này có an toàn với đa luồng không?* | Bước đăng ký là toàn cục và nên thực hiện một lần khi khởi động. Các lần gọi `CheckGrammar` sau đó có thể chạy song song miễn là mỗi lần sử dụng một instance `Document` riêng. |

## Các Bước Tiếp Theo

Bây giờ bạn đã biết **cách kiểm tra ngữ pháp** bằng **llm cục bộ**, bạn có thể khám phá:

- **Xử lý hàng loạt**: Lặp qua một thư mục các tài liệu và chạy cùng một pipeline.
- **Prompt tùy chỉnh**: Điều chỉnh payload yêu cầu bằng cách đặt `grammarOptions.PromptTemplate` cho các kiểm tra theo phong cách cụ thể.
- **Tích hợp với ASP.NET Core**: Cung cấp một endpoint API nhận các tệp `.docx` tải lên, chạy kiểm tra ngữ pháp và trả về tệp đã chỉnh sửa.

Các phần mở rộng này cho phép bạn xây dựng một nền tảng “ngữ pháp‑dư‑dịch‑vụ” đầy đủ tính năng mà không cần rời khỏi cơ sở của mình.

---

*Chúc lập trình vui vẻ! Nếu gặp bất kỳ khó khăn nào, hãy để lại bình luận bên dưới — tôi sẵn sàng giúp bạn tinh chỉnh cấu hình.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}