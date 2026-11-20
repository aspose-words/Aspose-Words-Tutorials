---
category: general
date: 2026-11-15
description: Học cách dịch văn bản bằng Google trong C#. Bài hướng dẫn này trình bày
  một ví dụ về Google Translate, xử lý nhiều ngôn ngữ và các thực tiễn tốt nhất.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: vi
lastmod: 2026-11-15
og_description: Cách dịch văn bản bằng Google trong C# sử dụng một ví dụ đầy đủ về
  Google Translate. Hãy làm theo hướng dẫn này để dịch nhiều ngôn ngữ một cách an
  toàn.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Cách dịch văn bản bằng Google Translate API trong C# – hướng dẫn nhanh
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Cách dịch văn bản bằng Google Translate API trong C# – hướng dẫn từng bước
url: /vi/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách dịch văn bản bằng Google Translate API trong C# – hướng dẫn từng bước

Nếu bạn cần **how to translate text** trong một ứng dụng .NET, Google Cloud Translation API cung cấp một giải pháp đáng tin cậy, không phụ thuộc vào ngôn ngữ. Trong hướng dẫn này, bạn sẽ thấy một **Google Translate example** dịch một chuỗi đơn giản, mở rộng để **translate multiple languages**, và tuân theo các thực hành tốt nhất cho khóa API và xử lý lỗi.

Bạn sẽ có một chương trình console C# sẵn sàng chạy, hiểu rõ về **translate text with Google**, và tự tin điều chỉnh mã cho các dự án lớn hơn.

## Những gì hướng dẫn này bao gồm

* Thiết lập dự án Google Cloud và lấy khóa API.  
* Cài đặt gói NuGet `Google.Cloud.Translation.V2`.  
* Viết mã sạch, có thể tái sử dụng mà **how to translate text** bằng SDK chính thức.  
* Mở rộng giải pháp để **translate multiple languages** trong một lần gọi.  
* Các lỗi thường gặp và mẹo cho triển khai mức độ sản xuất.  

### Yêu cầu trước

* .NET 6.0 SDK hoặc mới hơn (mã biên dịch với .NET Core và .NET Framework).  
* Tài khoản Google Cloud có **Cloud Translation API** được bật.  
* Kiến thức cơ bản về C# và các ứng dụng console.  

---

## Bước 1: Cài đặt thư viện khách hàng Google Cloud Translation

Thư viện khách hàng chính thức trừu tượng hoá các cuộc gọi HTTP và xử lý xác thực cho bạn.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Chạy lệnh này sẽ thêm gói `Google.Cloud.Translation.V2` vào dự án của bạn, cung cấp quyền truy cập vào lớp `TranslationClient` được sử dụng xuyên suốt trong hướng dẫn này.

> **Tại sao bước này quan trọng** – Sử dụng SDK tránh việc tự xây dựng yêu cầu, giảm lỗi, và đảm bảo bạn đồng bộ với phiên bản API mới nhất của Google.

## Bước 2: Tạo một helper dịch có thể tái sử dụng

Đóng gói logic dịch trong một lớp tĩnh giúp mã có thể tái sử dụng và tách riêng việc xử lý khóa API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Tại sao chúng tôi trả về một dictionary** – Khi bạn cần **translate multiple languages**, việc tổ chức kết quả theo mã ngôn ngữ giúp xử lý downstream trở nên đơn giản.

## Bước 3: Xây dựng ứng dụng console sử dụng helper

Dưới đây là file `Program.cs` hoàn chỉnh minh họa cả dịch một đoạn văn bản và dịch hàng loạt.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Kết quả console dự kiến**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Tại sao cần các khối try/catch?** – Lỗi mạng, giới hạn quota, hoặc khóa API không hợp lệ sẽ gây ra ngoại lệ. Xử lý chúng một cách nhẹ nhàng cải thiện trải nghiệm người dùng và giữ cho ứng dụng của bạn ổn định.

## Bước 4: Bảo mật khóa API của bạn

Việc hard‑code khóa API, như trên, chấp nhận được cho bản demo nhanh nhưng không phù hợp cho môi trường production. Hãy tuân theo các thực hành sau:

* Lưu khóa trong biến môi trường (`GOOGLE_API_KEY`) và đọc nó khi chạy:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Sử dụng **Google Application Default Credentials** thay vì khóa API khi chạy trên Google Cloud (App Engine, Cloud Run, v.v.).
* Hạn chế khóa chỉ cho Translation API trong console Google Cloud và giới hạn việc sử dụng cho các địa chỉ IP hoặc referrer cụ thể.

## Bước 5: Mở rộng giải pháp cho các kịch bản thực tế

### Xử lý phát hiện ngôn ngữ

Nếu bạn cần biết ngôn ngữ nguồn, đối tượng phản hồi chứa `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Dịch tài liệu lớn

API hỗ trợ tối đa 30 KB cho mỗi yêu cầu. Đối với văn bản lớn hơn, chia nội dung thành các đoạn, dịch từng đoạn, sau đó nối các kết quả lại với nhau. Giữ nguyên ranh giới câu để tránh cách diễn đạt lạ lùng.

### Giới hạn tốc độ và quota

Google áp dụng giới hạn số yêu cầu mỗi phút. Triển khai chính sách retry với exponential back‑off để tuân thủ giới hạn quota và tránh lỗi `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Các câu hỏi thường gặp và trường hợp đặc biệt

**Q: Tôi có thể dịch toàn bộ trang HTML không?**  
A: Có. Sử dụng tham số `Format` (`"text"` hoặc `"html"`) khi gọi `TranslateText`. SDK cung cấp điều này qua overload `TranslateText` nhận một `TranslateTextRequest`.

**Q: Nếu một ngôn ngữ không được hỗ trợ thì sao?**  
A: API sẽ trả về lỗi. Kiểm tra mã ngôn ngữ dựa trên danh sách trả về bởi `client.ListSupportedLanguages()` trước khi gửi yêu cầu.

**Q: API có tính phí theo ký tự không?**  
A: Google tính phí theo ký tự đã dịch. Ước tính chi phí bằng trang giá và cân nhắc cache các bản dịch thường xuyên.

---

## Kết luận

Bây giờ bạn đã biết **how to translate text** trong C# bằng Google Translate API chính thức. Hướng dẫn đã bao gồm một **Google translate example**, minh họa **translate multiple languages**, và nêu bật các thực hành sẵn sàng cho production như bảo mật khóa API và xử lý lỗi. Bằng cách tái sử dụng helper `Translator`, bạn có thể tích hợp dịch vào bất kỳ dịch vụ .NET, ứng dụng desktop, hoặc microservice nào.

**Các bước tiếp theo**

* Khám phá **Google Translate tutorial** để tìm hiểu các tính năng nâng cao như glossaries và custom models.  
* Kết hợp mã này với ASP.NET Core để tạo một web API đa ngôn ngữ.  
* Thử nghiệm dịch hàng loạt các file CSV để tự động hoá quy trình localization.

Chúc lập trình vui vẻ, và tận hưởng việc xây dựng các ứng dụng có thể tiếp cận toàn cầu!

## Bạn Nên Học Gì Tiếp Theo?

Những hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách lưu tài liệu Word đã dịch trong C# với Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}