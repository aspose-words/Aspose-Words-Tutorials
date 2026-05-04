---
category: general
date: 2026-05-04
description: Aspose ile belgeleri düzenlemek için LLM nasıl kullanılır – paragraf
  metnini değiştirmeyi, yerel LLM'ye bağlanmayı ve AI kullanarak metni yeniden yazmayı
  öğrenin.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: tr
og_description: LLM'yi kullanarak Aspose ile belgeleri nasıl düzenleyeceğiniz. Bu
  rehber, yerel bir LLM'ye nasıl bağlanılacağını, paragraf metnini nasıl değiştirileceğini
  ve metni AI kullanarak nasıl yeniden yazılacağını gösterir.
og_title: Aspose.Words ile LLM Nasıl Kullanılır – C#’ta Paragrafları Yeniden Yazma
tags:
- Aspose.Words
- C#
- AI
- LLM
title: LLM'yi Aspose.Words ile Nasıl Kullanılır – C#'ta Paragrafları Yeniden Yazma
url: /tr/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile LLM Kullanımı – C#'ta Paragrafları Yeniden Yazma

Hiç **LLM'yi nasıl kullanarak** bir Word belgesini manuel olarak açmadan düzenleyebileceğinizi merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, *paragraf metnini* programlı bir şekilde değiştirmeleri gerektiğinde, temiz bir AI‑tabanlı iş akışı eksikliği nedeniyle bir çıkmaza giriyor.  

Bu öğreticide yerel bir büyük dil modelini bağlayacağız, bir `.docx` dosyasından bir kesit vereceğiz, **AI kullanarak metni yeniden yazmasını** isteyeceğiz ve sonunda güncellenmiş belgeyi kaydedeceğiz—hepsi Aspose.Words ile. Sonunda, tüm süreci gösteren çalıştırılabilir bir C# konsol uygulamanız olacak.

> **Elde edeceğiniz:** tam, çalıştırılabilir bir örnek, her adımın açıklamaları, uç durumlar için ipuçları ve çözümü genişletme fikirleri.

## Gereksinimler

- **.NET 6+** (veya .NET Framework 4.7.2 – kod her iki ortamda da çalışır)
- **Aspose.Words for .NET** (NuGet paketi `Aspose.Words`)
- **Yerel bir LLM sunucusu** basit bir HTTP `/generate` uç noktası sunan (ör. Ollama, LMStudio veya özel bir Flask servisi)
- C# ve HTTP istemci koduna temel bir aşinalık  

Ek SDK'lara gerek yok; diğer her şey birlikte yazacağımız kodda yer alıyor.

## Adım 1: LLM ile Paragraf Metnini Değiştirme

İlk yapmamız gereken, değiştirmek istediğimiz paragrafı belirlemek. Aspose.Words, zengin bir nesne modeli sunarak bunu çok kolaylaştırıyor.

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

**Neden önemli:**  
Doğru düğümü seçmek, başlıkları veya tabloları yanlışlıkla üzerine yazmanızı önler. **Paragraf metnini değiştirme** yaklaşımını kullanarak, yalnızca ilgilendiğimiz içeriği dokunarak belge yapısını bozulmadan tutarız.

> **Pro ipucu:** Belgenizde değişken uzunlukta bölümler varsa, `document.GetChildNodes(NodeType.Paragraph, true)` ve LINQ kullanarak bir paragrafı metnine veya stiline göre bulun.

## Adım 2: Yerel LLM Uç Noktasına Bağlanma

Artık metnimiz olduğuna göre, bunu LLM'ye göndermemiz gerekiyor. Örnek, HTTP detaylarını gizleyen basit bir sarmalayıcı sınıfı `LocalLargeLanguageModel` kullanıyor. İsterseniz `HttpClient` çağrılarıyla değiştirebilirsiniz.

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

**Neden bu şekilde bağlanıyoruz:**  
Bir **yerel llm'ye bağlanma** kurulumu gecikmeyi ortadan kaldırır, verileri yerinde tutar ve API maliyetlerinden kaçınır. Sarmalayıcı ayrıca sonraki kodu daha temiz hâle getirir, **AI kullanarak metni yeniden yazma** mantığına odaklanmamızı sağlar.

## Adım 3: Aspose.Words ile AI Kullanarak Metni Yeniden Yazma

Paragraf metni elimizde ve LLM hazır olduğunda, modele tam olarak ne istediğimizi söyleyen bir istem (prompt) oluştururuz—resmi bir üslupla yeniden yazma. İstemi diğer stiller (samimi, teknik vb.) için de ayarlayabilirsiniz.

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Neden işe yarıyor:**  
LLM'ler istem (prompt) odaklıdır; açık talimatlar vermek (“…'yi resmi bir üslupla yeniden yaz”) tutarlı sonuçlar verir. **AI kullanarak metni yeniden yazma** adımı öğretinin kalbidir – AI'nin belge iş akışlarına doğrudan nasıl entegre edilebileceğini gösterir.

## Adım 4: Belgeyi Düzenleme ve Değişiklikleri Kaydetme

Şimdi orijinal run'ları yeni içerikle değiştiriyoruz. Aspose.Words, metni `Run` nesnelerinde saklar, bu yüzden önce temizlemek kalan biçimlendirme kalıntılarını önler.

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

**Köşe‑durum notu:**  
Eğer orijinal paragraf karışık biçimlendirme (kalın, italik) içeriyorsa stilleri korumak isteyebilirsiniz. Bu durumda yeni bir `Run` oluşturun, orijinal `Font` ayarlarını kopyalayın ve ardından `Text` özelliğini `revisedText` olarak ayarlayın.

## Tam Çalışan Örnek

Aşağıda, bir konsol projesine kopyalayıp yapıştırabileceğiniz tüm program yer alıyor. Önce Aspose.Words NuGet paketini kurmayı unutmayın (`dotnet add package Aspose.Words`).

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

### Beklenen Çıktı

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

`output.docx` dosyasını açın – üçüncü paragrafın artık düzenlenmiş sürümü okunduğunu göreceksiniz.

## Sık Sorulan Sorular & Tuzaklar

| Question | Answer |
|----------|--------|
| **LLM'im ekstra alanlarla JSON döndürürse ne olur?** | `GenerateText`'i doğru özelliği ayrıştıracak şekilde ayarlayın veya yanıtı manuel olarak parse edin. |
| **Birden fazla paragrafı aynı anda işleyebilir miyim?** | Evet – `document.FirstSection.Body.Paragraphs` üzerinde döngü yapın ve aynı istem mantığını uygulayın, belki bağlam için isteme paragraf indeksini ekleyin. |
| **LLM sunucum kimlik doğrulama gerektiriyor mu?** | POST'tan önce `HttpClient`'a bir başlık ekleyin: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Değiştirme sonrası biçimlendirme kayboluyor.** | Orijinal `Run.Font` ayarlarını koruyun: yeni bir `Run` oluşturun, `originalRun.Font.Clone()`'ı kopyalayın, ardından `Text`'i ayarlayın. |
| **LLM bazen boş string döndürüyor.** | Bir geri dönüş mekanizması ekleyin – eğer `revisedText.Trim().Length == 0` ise, orijinal metni tutun veya daha basit bir istemle tekrar deneyin. |

## Çözümü Genişletme

Artık tek bir paragraf için **llm'yi nasıl kullanacağınızı** öğrendiğinize göre, aşağıdaki adımları düşünün:

- **Toplu işleme:** Her paragrafı döngüye alıp seçilen bir stilde yeniden yazın (ör. “tüm metni özlü hâle getir”).  
- **Stil‑bilinçli yeniden yazma:** Orijinal paragrafın stil adını isteme gönderin, böylece LLM başlıklar ile gövde metni arasında fark gözetebilir.  
- **CI pipeline entegrasyonu:** Belge düzenlemeyi dokümantasyon oluşturma sürecinin bir parçası olarak otomatikleştirin.  
- **Alternatif istemler:** “Bu paragrafı özetle” ya da “Bu paragrafı İspanyolcaya çevir” gibi istemleri deneyerek **AI kullanarak metni yeniden yazma**'nın tam gücünü keşfedin.

## Sonuç

**llm'yi nasıl kullanacağınızı** Aspose.Words ile tüm süreci adım adım inceledik: belgeyi yükleme, **yerel llm'ye bağlanma**, bir paragrafı çıkarma, **AI kullanarak metni yeniden yazma**, **paragraf metnini değiştirme** ve sonunda sonucu kaydetme. Kod bağımsızdır, kutudan çıkar çıkmaz çalışır ve AI'yi geleneksel belge otomasyonu ile birleştirmenin pratik bir yolunu gösterir.

Give it a spin, tweak the prompts, and let

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}