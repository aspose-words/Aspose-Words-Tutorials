---
category: general
date: 2026-06-24
description: Bài hướng dẫn LLM cục bộ cho bạn cách gọi một LLM cục bộ, tải tài liệu
  Word và chạy kiểm tra ngữ pháp bằng AI trong C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: vi
og_description: Hướng dẫn LLM cục bộ giải thích từng bước cách gọi LLM cục bộ, tải
  tài liệu Word và chạy kiểm tra ngữ pháp AI bằng C#.
og_title: Hướng dẫn LLM cục bộ – Gọi LLM cục bộ và chạy kiểm tra ngữ pháp
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Hướng dẫn LLM cục bộ – Cách gọi LLM cục bộ và thực hiện kiểm tra ngữ pháp
url: /vi/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hướng dẫn LLM cục bộ – Gọi LLM cục bộ và thực hiện kiểm tra ngữ pháp

Bạn đã bao giờ tự hỏi làm thế nào để **kiểm tra ngữ pháp** trên một tệp Word mà không gửi bất cứ thứ gì lên đám mây? Trong **hướng dẫn llm cục bộ** này, chúng ta sẽ kết nối một mô hình ngôn ngữ lớn tự‑host, tải một tệp `.docx`, và để AI dọn dẹp văn bản. Không cần API keys, không có lưu lượng bên ngoài—chỉ máy của bạn thực hiện công việc nặng.

Chúng tôi sẽ đi qua từng dòng mã, giải thích tại sao mỗi phần lại quan trọng, và thậm chí chỉ cho bạn cách xử lý các bẫy thường gặp (như tệp tin bị thiếu hoặc endpoint không thể truy cập). Khi kết thúc, bạn sẽ có một ứng dụng console C# sẵn sàng chạy, thực hiện **ai grammar check** bằng mô hình được lưu trữ cục bộ.

> **Bạn sẽ nhận được:** một chương trình hoàn chỉnh, có thể chạy được, giải thích rõ ràng từng bước, và các mẹo để mở rộng giải pháp cho tài liệu lớn hơn hoặc các nhà cung cấp LLM khác.

![local llm tutorial diagram](https://example.com/local-llm-tutorial-diagram.png "Diagram illustrating the flow of the local llm tutorial")

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn bạn có:

- .NET 6.0 SDK hoặc phiên bản mới hơn (bạn có thể tải từ trang của Microsoft)
- Một server LLM đang chạy cục bộ, cung cấp endpoint tương thích OpenAI (ví dụ: Ollama, LM Studio, hoặc một wrapper FastAPI tùy chỉnh)
- Gói NuGet `AiGrammar` (hoặc bất kỳ thư viện nào cung cấp các lớp `LocalLargeLanguageModel`, `Document`, và `AiModelType`)
- Một tài liệu Word mẫu (`input.docx`) đặt trong thư mục bạn sẽ tham chiếu sau

Chỉ vậy—không cần bất kỳ thông tin xác thực đám mây nào.

## Bước 1: Hướng dẫn LLM cục bộ – Cấu hình Endpoint

Điều đầu tiên chúng ta cần là một đối tượng **call local llm** biết nơi gửi yêu cầu. Hãy nghĩ nó như số điện thoại bạn quay trước khi có thể nói chuyện.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Tại sao điều này quan trọng:**  
Hầu hết các SDK LLM mong đợi một endpoint HTTP tuân theo hợp đồng API của OpenAI. Bằng cách chỉ `Endpoint` tới `http://localhost:8000/v1` chúng ta nói cho thư viện **call local llm** thay vì kết nối tới máy chủ của OpenAI. API key giả chỉ là một placeholder—một số client không chấp nhận giá trị null, vì vậy chúng ta cung cấp một giá trị vô hại.

> **Mẹo chuyên nghiệp:** Nếu bạn chạy LLM phía sau một reverse proxy, đặt `Endpoint` thành URL của proxy và để proxy xử lý việc chấm dứt TLS. Điều này giữ cho ứng dụng console của bạn đơn giản và an toàn.

## Bước 2: Tải tài liệu Word để kiểm tra ngữ pháp

Bây giờ mô hình đã có thể truy cập, chúng ta cần **load word document** nội dung vào bộ nhớ. Lớp `Document` trừu tượng hoá việc phân tích `.docx` cho chúng ta.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Tại sao điều này quan trọng:**  
Việc đưa thẳng một tệp nhị phân `.docx` vào LLM sẽ làm nó bối rối. Trợ giúp `Document` trích xuất văn bản thô đồng thời giữ nguyên các ngắt đoạn, cung cấp cho **ai grammar check** một đầu vào sạch sẽ. Kiểm tra tồn tại ngăn ngừa `FileNotFoundException` gây crash cho ứng dụng.

## Bước 3: Thực hiện kiểm tra ngữ pháp bằng LLM

Đây là phần cốt lõi của hướng dẫn: chúng ta yêu cầu mô hình cục bộ đọc lại văn bản. Phương thức `CheckGrammar` ẩn đi việc giao tiếp HTTP và trả về một đối tượng kết quả.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Tại sao điều này quan trọng:**  
`AiModelType.Gpt4` chỉ là một nhãn cho biết dịch vụ từ xa nên dùng mẫu prompt nào. Nếu bạn có mô hình nhỏ hơn (ví dụ `Llama2`), hãy thay thế cho phù hợp. Thư viện sẽ tuần tự hoá văn bản tài liệu, gửi tới `http://localhost:8000/v1/completions`, và phân tích đầu ra đã được chỉnh sửa.

> **Trường hợp biên:** Nếu LLM hết thời gian chờ, `CheckGrammar` sẽ ném ra `TimeoutException`. Hãy bao bọc lời gọi trong khối `try/catch` nếu bạn dự kiến tài liệu lớn hoặc server bận.

## Bước 4: Xuất văn bản đã chỉnh sửa

Cuối cùng, chúng ta hiển thị phiên bản đã được dọn dẹp. Trong một ứng dụng thực tế, bạn có thể ghi lại vào một tệp `.docx` mới, nhưng cho hướng dẫn này, việc in ra console là đủ.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Kết quả mong đợi** (giả sử tệp gốc chứa một vài lỗi cố ý):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Nếu LLM không tìm thấy lỗi nào, đầu ra sẽ giống hệt đầu vào, điều này vẫn là một tín hiệu hữu ích.

## Ví dụ Hoạt động Đầy đủ

Kết hợp mọi thứ lại, đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một dự án console mới:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Cách chạy

1. Mở terminal trong thư mục dự án.  
2. Chạy `dotnet run`.  
3. Quan sát console in ra văn bản đã chỉnh sửa.

Đó là toàn bộ **local llm tutorial** trong chưa tới 100 dòng mã.

## Câu hỏi thường gặp (FAQ)

### Tôi có thể dùng một thương hiệu LLM khác không?

Tuyệt đối. Miễn là server tuân theo schema API OpenAI v1, chỉ cần thay đổi `Endpoint` và chọn giá trị enum `AiModelType` tương ứng (ví dụ `AiModelType.Llama2`). Phần còn lại của mã vẫn giống nhau.

### Nếu tài liệu của tôi rất lớn (10 MB+) thì sao?

Payload lớn có thể vượt quá kích thước yêu cầu mặc định của nhiều server. Chia tài liệu thành các phần và gọi `CheckGrammar` cho mỗi phần, sau đó nối các kết quả lại. Điều này cũng giảm khả năng timeout.

### Làm sao để ghi lại đầu ra đã chỉnh sửa vào tệp `.docx`?

Lớp `Document` thường cung cấp phương thức `Save(string path, string content)`. Sau khi bạn có `result.CorrectedText`, gọi:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Kiểm tra tài liệu của thư viện để biết chữ ký chính xác.

### API key giả có phải là rủi ro bảo mật không?

Không. Khóa này bị các endpoint tự‑host bỏ qua, nhưng một số SDK yêu cầu một chuỗi không null. Sử dụng placeholder như `"dummy"` đáp ứng SDK mà không lộ bất kỳ bí mật nào.

## Các bước tiếp theo và Chủ đề liên quan

- **Fine‑tune your local LLM** cho ngữ pháp đặc thù theo lĩnh vực (ví dụ: viết pháp lý hoặc y tế).  
- **Run a batch job** xử lý toàn bộ thư mục các tệp Word—rất hữu ích cho quy trình xuất bản.  
- Khám phá **streaming responses** nếu bạn muốn gợi ý thời gian thực khi người dùng gõ.  
- Kết hợp với **spell‑checking libraries** để có lớp kiểm soát chất lượng đôi.

Mỗi ý tưởng này dựa trên các khái niệm cốt lõi trong **local llm tutorial**, vì vậy bạn sẽ thấy các mẫu lặp lại—**call local llm**, **load word document**, **run grammar check**, và **handle results**—trong toàn bộ nội dung.

---

*Chúc lập trình vui vẻ! Nếu gặp khó khăn, hãy để lại bình luận bên dưới và chúng tôi sẽ cùng bạn khắc phục.*

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Load Encrypted In Word Document](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}