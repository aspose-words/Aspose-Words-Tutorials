---
category: general
date: 2026-09-11
description: API anahtarını okuyarak, OpenAI'yi çağırarak ve bir Word belgesinin özlü
  bir özetini oluşturarak C#'ta metni özetlemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: tr
lastmod: 2026-09-11
og_description: C#'ta metni nasıl özetlersiniz? Bu öğreticide API anahtarını nasıl
  okur, OpenAI'yi nasıl çağırır ve bir Word belgesinin özetini nasıl oluşturursunuz
  gösterilmektedir.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: OpenAI ile C#'ta Metni Özetleme – Adım Adım Rehber
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: OpenAI kullanarak C#'de metni özetleme
url: /tr/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile OpenAI Kullanarak Metni Özetleme

Eğer bir .docx dosyasında **metni özetleme** ihtiyacınız varsa, bu rehber size eksiksiz, çalıştırmaya hazır bir çözüm gösterir. Ortam değişkeninizden API anahtarını nasıl okuyacağınızı, C#'tan OpenAI (veya Google) nasıl çağıracağınızı ve bir Word belgesinin özlü bir özetini nasıl oluşturacağınızı öğreneceksiniz.

Bir Word belgesini özetlemek, rapor oluşturma, e‑posta özetleri veya bilgi tabanı çıkarımı gibi durumlar için yaygın bir gereksinimdir. Bu öğreticinin sonunda, sağladığınız herhangi bir `.docx` dosyasının beş cümlelik özetini yazdıran bir komut satırı programına sahip olacaksınız.

## Önkoşullar

- .NET 6.0 SDK veya daha yeni bir sürüm (indir: [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- `OPENAI_API_KEY` adlı bir ortam değişkeninde saklanan geçerli bir OpenAI API anahtarı (**read api key** örneğini göreceksiniz)
- `.docx` dosyalarını okumak için `DocumentFormat.OpenXml` NuGet paketi
- `OpenAI` NuGet paketi (ya da Google sağlayıcısını tercih ediyorsanız `Google.AI`)

## Adım 1: Projeyi oluşturun ve bağımlılıkları kurun

Yeni bir konsol projesi oluşturun ve gerekli paketleri ekleyin:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **İpucu:** Daha sonra daha fazla bağımlılık ekleyecekseniz, ilgili paketleri bir `<ItemGroup>` altında gruplayarak `csproj` dosyanızı düzenli tutun.

## Adım 2: API anahtarını güvenli bir şekilde okuyun

Sırları kod içinde sabitlemek güvensizdir. Bu öğretici, ortam değişkenlerinden **read api key** almanın doğru yolunu gösterir.

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Adım 3: Özetlemek istediğiniz Word belgesini yükleyin

Aşağıdaki kod, OpenXML yapısından düz metin çıkararak **how to summarize word document** içeriğini gösterir.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Adım 4: Yeniden kullanılabilir bir özetleyici sınıfı oluşturun

Bu sınıf, **how to call openai** (veya Google) işlemini kapsüller ve **how to create summary** mantığını uygular. Tek bir enum değeriyle sağlayıcıları değiştirebilmenizi sağlar.

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### Bu yapının önemi

- **Sorumlulukların ayrılması:** Belgeyi yükleme, API anahtarını okuma ve AI hizmetini çağırma kendi metodlarına ayrılmıştır. Bu, kodun test edilmesini ve genişletilmesini kolaylaştırır.
- **Sağlayıcı esnekliği:** Bir enum kullanarak OpenAI ve Google arasında kodu dokunmadan geçiş yapabilirsiniz; bu doğrudan **how to call openai** ve **how to create summary** sorularına yeniden kullanılabilir bir yanıt verir.
- **Hata yönetimi:** Eksik API anahtarları net bir istisna fırlatır, sessiz hataları önler.

## Adım 5: Her şeyi `Program.cs` içinde birleştirin

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### Beklenen çıktı

Örnek bir belgeyle programı çalıştırdığınızda:

```bash
dotnet run -- "sample/input.docx"
```

şu çıktıyı alabilirsiniz:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Adım 6: Yaygın varyasyonlar ve kenar durumları

| Durum | Önerilen ayarlama |
|-----------|------------------------|
| **Büyük belgeler** ( > 10 KB ) | Metni parçalara bölün, her parçayı özetleyin ve ardından sonuçları birleştirin. |
| **İngilizce dışı içerik** | İpucu dilini istemde belirtin, ör. “Summarize the following French text …”. |
| **Google sağlayıcısı** | `SummarizeWithOpenAIAsync` çağrısını uygun Google API istemcisiyle değiştirin; aynı enum arayüzünü koruyun. |
| **Özel özet uzunluğu** | `SummarizeAsync` çağrısında `maxSentences` argümanını değiştirin. |
| **API anahtarı eksik** | `GetOpenAIApiKey` metodu zaten net bir istisna fırlatır; daha dost bir mesaj isterseniz `Main` içinde yakalayın. |

## Üretim kullanımı için ipuçları

1. **API anahtarını önbellekle** – her çağrıda ortamdan okumak ihmal edilebilir bir yük ekler, ancak özetleyiciyi aynı işlem içinde çok kez çağırıyorsanız statik readonly bir alanda saklayabilirsiniz.
2. **İstekleri oranla sınırlayın** – OpenAI istek limitleri uygular; `429 Too Many Requests` alırsanız üssel geri çekilme (exponential back‑off) uygulayın.
3. **Girdiyi temizle** – Dış bir AI hizmetine metin göndermeden önce kişisel tanımlayıcı bilgileri kaldırın.
4. **Çıkarma mantığını birim testiyle doğrula** – `WordprocessingDocument` nesnesini taklit ederek `ExtractTextFromDocx` metodunun farklı belge yapılarıyla çalıştığını test edin.

## Sonuç

Artık C#'ta **how to summarize text** işlemini, API anahtarını güvenli bir şekilde okuyarak, OpenAI'yi çağırarak ve bir Word belgesinin özlü özetini oluşturarak biliyorsunuz. Aynı desen, **how to call openai** işlemini diğer sağlayıcılarla, farklı içerik tipleri için **how to create summary** mantığını ve ortamdan **read api key** değerlerini güvenli bir şekilde almanızı sağlar. Daha uzun belgeler, farklı sağlayıcılar veya özel istemler deneyerek özetlemeyi kendi alanınıza göre özelleştirin.

---


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [how to create pdf from Word – Complete C# Guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word Document - How to Remove Content](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}