---
category: general
date: 2026-11-15
description: Google ile C#’ta metin çevirme nasıl yapılır öğrenin. Bu öğreticide bir
  Google Translate örneği, birden fazla dili işleme ve en iyi uygulamalar gösterilmektedir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: tr
lastmod: 2026-11-15
og_description: 'C#''ta Google kullanarak metin çevirme: tam bir Google Translate
  örneğiyle. Birden fazla dili güvenli bir şekilde çevirmek için bu öğreticiyi takip
  edin.'
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Google Translate API ile C#'ta Metin Çevirme – Hızlı Öğretici
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
title: C# ile Google Translate API kullanarak metni nasıl çevirirsiniz – adım adım
  rehber
url: /tr/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Google Translate API kullanarak metin nasıl çevrilir – adım adım rehber

Bir .NET uygulamasında **metni nasıl çevireceğinizi** öğrenmeniz gerekiyorsa, Google Cloud Translation API güvenilir, dil bağımsız bir çözüm sunar. Bu öğreticide, basit bir dizeyi çeviren bir **Google Translate örneği** görecek, **birden çok dili çevir** genişletecek ve API anahtarları ve hata yönetimi için en iyi uygulamaları izleyeceksiniz.

Hazır‑çalıştır C# konsol programı, **Google ile metin çevirme** konusunda net bir anlayış ve kodu daha büyük projelere uyarlama konusunda güven kazanacaksınız.

## Bu öğreticide neler ele alınır

* Google Cloud projesi oluşturma ve bir API anahtarı edinme.  
* `Google.Cloud.Translation.V2` NuGet paketini kurma.  
* Resmi SDK'yı kullanarak **metni nasıl çevirileceği** konusunda temiz, yeniden kullanılabilir kod yazma.  
* Çözümü tek bir çağrıda **birden çok dili çevirecek** şekilde genişletme.  
* Üretim‑düzeyi uygulamalar için yaygın tuzaklar ve ipuçları.

### Önkoşullar

* .NET 6.0 SDK veya daha yeni bir sürüm (kod .NET Core ve .NET Framework ile derlenir).  
* **Cloud Translation API** etkinleştirilmiş bir Google Cloud hesabı.  
* C# ve konsol uygulamaları konusunda temel bilgi.  

---

## Adım 1: Google Cloud Translation istemci kütüphanesini kurun

Resmi istemci kütüphanesi HTTP çağrılarını soyutlar ve kimlik doğrulamayı sizin için yönetir.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Komutu çalıştırmak, projenize `Google.Cloud.Translation.V2` paketini ekler ve bu rehber boyunca kullanılan `TranslationClient` sınıfına erişim sağlar.

> **Bu adımın önemi** – SDK'yı kullanmak, manuel istek oluşturmayı önler, hataları azaltır ve Google'ın en son API sürümüyle uyumlu olmanızı sağlar.

## Adım 2: Yeniden kullanılabilir bir çeviri yardımcı sınıfı oluşturun

Çeviri mantığını statik bir sınıfta kapsüllemek, kodun yeniden kullanılabilir olmasını sağlar ve API‑anahtarı yönetimini izole eder.

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

> **Neden bir sözlük döndürüyoruz** – **Birden çok dili çevirmek** istediğinizde, sonuçları dil koduna göre düzenlemek sonraki işlemleri basitleştirir.

## Adım 3: Yardımcı sınıfı kullanan konsol uygulamasını oluşturun

Aşağıda, tek bir metin çevirisini ve toplu çeviriyi gösteren tam bir `Program.cs` bulunmaktadır.

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

**Beklenen konsol çıktısı**

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

> **Neden try/catch blokları?** – Ağ hataları, kota sınırları veya geçersiz bir API anahtarı istisna oluşturur. Bunları nazikçe ele almak kullanıcı deneyimini iyileştirir ve uygulamanızın kararlılığını korur.

## Adım 4: API anahtarınızı güvence altına alın

Yukarıda gösterildiği gibi API anahtarını kod içinde sabit tutmak hızlı bir demo için kabul edilebilir, ancak üretim ortamı için uygun değildir. Bu uygulamaları izleyin:

* Anahtarı bir ortam değişkeninde (`GOOGLE_API_KEY`) saklayın ve çalışma zamanında okuyun:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Google Cloud üzerinde (App Engine, Cloud Run vb.) çalışırken API anahtarı yerine **Google Application Default Credentials** kullanın.
* Anahtarı Google Cloud konsolunda Translation API ile sınırlayın ve kullanımını belirli IP adreslerine veya yönlendirenlere (referrer) kısıtlayın.

## Adım 5: Çözümü gerçek‑dünya senaryoları için genişletin

### Dil algılamayı yönetme

Kaynak dili bilmeniz gerekiyorsa, yanıt nesnesi `DetectedSourceLanguage` içerir:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Büyük belgeleri çevirmek

API, istekte en fazla 30 KB destekler. Daha büyük metinler için içeriği parçalara bölün, her parçayı çevirin ve ardından sonuçları birleştirin. Cümle sınırlarını koruyarak garip ifadelerden kaçının.

### Hız sınırlaması ve kotalar

Google, dakikada istek sınırları uygular. Kota sınırlarına saygı göstermek ve `429 Too Many Requests` hatalarından kaçınmak için üssel geri çekilme (exponential back‑off) ile bir yeniden deneme politikası uygulayın.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Yaygın sorular ve uç durumlar

**S: Bir bütün HTML sayfasını çevirebilir miyim?**  
C: Evet. `TranslateText` çağırırken `Format` parametresini (`"text"` veya `"html"`) kullanın. SDK, bunu `TranslateTextRequest` kabul eden `TranslateText` aşırı yüklemesi aracılığıyla sunar.

**S: Bir dil desteklenmiyorsa ne olur?**  
C: API bir hata döndürür. İstek yapmadan önce dil kodlarını `client.ListSupportedLanguages()` tarafından döndürülen listeye karşı doğrulayın.

**S: API karakter başına ücret alıyor mu?**  
C: Google, çevrilen karakter başına faturalandırır. Fiyatlandırma sayfasını kullanarak maliyeti tahmin edin ve sık kullanılan çevirileri önbelleğe almayı düşünün.

---

## Sonuç

Artık resmi Google Translate API'yi kullanarak C# içinde **metni nasıl çevirileceğini** biliyorsunuz. Öğreticide bir **Google translate örneği** ele alındı, **birden çok dili çevirme** gösterildi ve API‑anahtarı güvenliği ve hata yönetimi gibi üretim‑hazır uygulamalar vurgulandı. `Translator` yardımcı sınıfını yeniden kullanarak çeviriyi herhangi bir .NET servisine, masaüstü uygulamasına veya mikroservise entegre edebilirsiniz.

**Sonraki adımlar**

- **Google Translate öğreticisini** sözlükler ve özel modeller gibi gelişmiş özellikler için keşfedin.  
- Bu kodu ASP.NET Core ile birleştirerek çok dilli bir web API oluşturun.  
- CSV dosyalarının toplu çevirisiyle yerelleştirme hatlarını otomatikleştirmeyi deneyin.

Kodlamaktan keyif alın ve küresel erişilebilir uygulamalar geliştirmenin tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [C# ile Google AI kullanarak çevrilmiş Word belgesini kaydetme](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}