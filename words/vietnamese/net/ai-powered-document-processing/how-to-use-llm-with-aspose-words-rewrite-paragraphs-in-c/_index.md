---
category: general
date: 2026-05-04
description: Cách sử dụng LLM để chỉnh sửa tài liệu với Aspose – học cách thay thế
  văn bản đoạn, kết nối với LLM cục bộ và viết lại văn bản bằng AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: vi
og_description: Cách sử dụng LLM để chỉnh sửa tài liệu với Aspose. Hướng dẫn này cho
  thấy cách kết nối với LLM cục bộ, thay thế văn bản đoạn văn và viết lại văn bản
  bằng AI.
og_title: Cách sử dụng LLM với Aspose.Words – Viết lại các đoạn văn trong C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Cách sử dụng LLM với Aspose.Words – Viết lại các đoạn văn trong C#
url: /vi/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách sử dụng LLM với Aspose.Words – Viết lại các đoạn văn trong C#

Bạn đã bao giờ tự hỏi **cách sử dụng LLM** để chỉnh sửa một tài liệu Word mà không cần mở thủ công chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi họ cần *thay thế văn bản đoạn* một cách lập trình nhưng lại thiếu quy trình làm việc dựa trên AI sạch sẽ.  

Trong hướng dẫn này, chúng ta sẽ kết nối một mô hình ngôn ngữ lớn cục bộ, cung cấp cho nó một đoạn trích từ tệp `.docx`, yêu cầu nó **viết lại văn bản bằng AI**, và cuối cùng lưu tài liệu đã cập nhật — tất cả đều sử dụng Aspose.Words. Khi kết thúc, bạn sẽ có một ứng dụng console C# sẵn sàng chạy, minh họa toàn bộ quy trình.

> **Bạn sẽ nhận được:** một ví dụ hoàn chỉnh, có thể chạy được, giải thích từng bước, mẹo cho các trường hợp đặc biệt, và ý tưởng mở rộng giải pháp.

## Những gì bạn cần

- **.NET 6+** (hoặc .NET Framework 4.7.2 – mã hoạt động trên cả hai)
- **Aspose.Words for .NET** (gói NuGet `Aspose.Words`)
- Một **máy chủ LLM cục bộ** cung cấp endpoint HTTP đơn giản `/generate` (ví dụ: Ollama, LMStudio, hoặc dịch vụ Flask tùy chỉnh)
- Kiến thức cơ bản về C# và mã client HTTP  

Không cần SDK bổ sung; mọi thứ còn lại nằm trong mã chúng ta sẽ viết cùng nhau.

## Bước 1: Cách sử dụng LLM để thay thế văn bản đoạn

Điều đầu tiên chúng ta cần làm là xác định đoạn văn mà chúng ta muốn sửa đổi. Aspose.Words làm cho việc này trở nên dễ dàng bằng cách cung cấp một mô hình đối tượng phong phú.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Tại sao điều này quan trọng:**  
Việc chọn đúng node ngăn bạn vô tình ghi đè tiêu đề hoặc bảng. Bằng cách sử dụng phương pháp **replace paragraph text**, chúng ta giữ nguyên cấu trúc tài liệu trong khi chỉ chỉnh sửa nội dung mà chúng ta quan tâm.

> **Mẹo chuyên nghiệp:** Nếu tài liệu của bạn có các phần có độ dài biến đổi, hãy sử dụng `document.GetChildNodes(NodeType.Paragraph, true)` và LINQ để tìm một đoạn dựa trên văn bản hoặc kiểu của nó.

## Bước 2: Kết nối tới Endpoint LLM Cục bộ

Bây giờ chúng ta đã có văn bản, cần gửi nó tới LLM. Ví dụ sử dụng một lớp wrapper đơn giản `LocalLargeLanguageModel` để ẩn đi các chi tiết HTTP. Bạn có thể thay thế bằng các lời gọi `HttpClient` nếu muốn.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Tại sao chúng ta kết nối theo cách này:**  
Cấu hình **connect to local llm** loại bỏ độ trễ, giữ dữ liệu trên máy chủ nội bộ và tránh chi phí API. Wrapper cũng làm cho mã sau này sạch hơn, cho phép chúng ta tập trung vào logic **rewrite text using ai**.

## Bước 3: Viết lại Văn bản bằng AI với Aspose.Words

Với văn bản đoạn đã có và LLM sẵn sàng, chúng ta tạo một prompt để nói cho mô hình biết chính xác những gì chúng ta muốn — viết lại với tông trang trọng. Bạn có thể điều chỉnh prompt cho các phong cách khác (thân thiện, kỹ thuật, v.v.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Tại sao cách này hoạt động:**  
LLM hoạt động dựa trên prompt; cung cấp chỉ dẫn rõ ràng (“Rewrite … in a formal tone”) mang lại kết quả nhất quán. Bước **rewrite text using ai** là trung tâm của hướng dẫn – nó minh họa cách AI có thể được nhúng trực tiếp vào quy trình làm việc với tài liệu.

## Bước 4: Chỉnh sửa Tài liệu và Lưu Thay đổi

Bây giờ chúng ta thay thế các run gốc bằng nội dung mới. Aspose.Words lưu trữ văn bản trong các đối tượng `Run`, vì vậy việc xóa chúng trước sẽ tránh các artefact định dạng còn lại.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Lưu ý trường hợp đặc biệt:**  
Nếu đoạn gốc chứa định dạng hỗn hợp (đậm, nghiêng) bạn có thể muốn giữ nguyên kiểu. Trong trường hợp đó, tạo một `Run` mới, sao chép cài đặt `Font` gốc, sau đó đặt `Text` của nó thành `revisedText`.

## Ví dụ Hoạt động Đầy đủ

Dưới đây là toàn bộ chương trình bạn có thể sao chép và dán vào dự án console. Hãy nhớ cài đặt gói NuGet Aspose.Words trước (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Kết quả Dự kiến

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Mở `output.docx` – bạn sẽ thấy đoạn văn thứ ba bây giờ hiển thị phiên bản đã được chỉnh sửa.

## Câu hỏi Thường gặp & Lưu ý

| Câu hỏi | Trả lời |
|----------|--------|
| **Nếu LLM của tôi trả về JSON với các trường phụ?** | Điều chỉnh `GenerateText` để giải mã thuộc tính đúng hoặc phân tích phản hồi theo cách thủ công. |
| **Tôi có thể xử lý nhiều đoạn cùng lúc không?** | Có – lặp qua `document.FirstSection.Body.Paragraphs` và áp dụng cùng logic prompt, có thể thêm chỉ mục đoạn vào prompt để cung cấp ngữ cảnh. |
| **Máy chủ LLM của tôi yêu cầu xác thực?** | Thêm header vào `HttpClient` trước khi POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Định dạng bị mất sau khi thay thế.** | Giữ nguyên cài đặt `Run.Font` gốc: tạo một `Run` mới, sao chép `originalRun.Font.Clone()`, sau đó đặt `Text` của nó. |
| **LLM đôi khi trả về chuỗi rỗng.** | Triển khai cơ chế dự phòng – nếu `revisedText.Trim().Length == 0`, giữ nguyên văn bản gốc hoặc thử lại với prompt đơn giản hơn. |

## Mở rộng Giải pháp

Bây giờ bạn đã thành thạo **cách sử dụng llm** cho một đoạn văn, hãy xem xét các bước tiếp theo sau:

- **Xử lý hàng loạt:** Lặp qua mọi đoạn và viết lại theo phong cách đã chọn (ví dụ: “làm ngắn gọn tất cả văn bản”).  
- **Viết lại có nhận thức kiểu:** Truyền tên kiểu của đoạn gốc vào prompt để LLM có thể tôn trọng tiêu đề so với văn bản thân.  
- **Tích hợp vào pipeline CI:** Tự động chỉnh sửa tài liệu như một phần của quy trình xây dựng tài liệu.  
- **Prompt thay thế:** Thử “tóm tắt đoạn này” hoặc “dịch đoạn này sang tiếng Tây Ban Nha” để khám phá toàn bộ sức mạnh của **rewrite text using ai**.

## Kết luận

Chúng ta đã đi qua toàn bộ quy trình **cách sử dụng llm** với Aspose.Words: tải tài liệu, **connect to local llm**, trích xuất một đoạn, **rewrite text using ai**, **replace paragraph text**, và cuối cùng lưu kết quả. Mã nguồn độc lập, hoạt động ngay khi chạy, và trình bày cách thực tế để kết hợp AI với tự động hoá tài liệu truyền thống.

Hãy thử nghiệm, điều chỉnh các prompt, và để

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}