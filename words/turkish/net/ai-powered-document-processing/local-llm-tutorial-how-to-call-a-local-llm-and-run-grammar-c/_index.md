---
category: general
date: 2026-06-24
description: Yerel LLM öğreticisi, yerel bir LLM'yi nasıl çağıracağınızı, bir Word
  belgesini nasıl yükleyeceğinizi ve C#'ta AI dilbilgisi denetimi kullanarak nasıl
  dilbilgisi kontrolü yapacağınızı gösterir.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: tr
og_description: Yerel LLM öğreticisi, adım adım bir yerel LLM'yi nasıl çağıracağınızı,
  bir Word belgesini nasıl yükleyeceğinizi ve C#'ta bir AI dilbilgisi kontrolü nasıl
  çalıştıracağınızı açıklar.
og_title: Yerel LLM Eğitimi – Yerel LLM'yi Çağır ve Dilbilgisi Kontrolü Yap
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
title: Yerel LLM Eğitimi – Yerel bir LLM'yi Çağırma ve Dilbilgisi Kontrolü Çalıştırma
url: /tr/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yerel LLM Öğreticisi – Yerel LLM'yi Çağır ve Dilbilgisi Kontrolü Yap

Hiç bir Word dosyasını buluta göndermeden **dilbilgisi kontrolü** yapmayı düşündünüz mü? Bu **yerel llm öğreticisi**nde kendiniz barındırdığınız büyük dil modelini bağlayacak, bir `.docx` dosyasını yükleyecek ve yapay zekanın metni düzenlemesine izin vereceğiz. API anahtarı yok, dış trafiği yok—sadece kendi makineniz işi yapıyor.

Her kod satırını adım adım inceleyecek, her parçanın neden önemli olduğunu açıklayacak ve yaygın tuzaklarla (eksik dosyalar ya da erişilemeyen uç nokta gibi) nasıl başa çıkılacağını göstereceğiz. Sonunda, yerel olarak barındırılan bir model kullanarak **ai grammar check** yapan çalıştırılabilir bir C# konsol uygulamanız olacak.

> **Ne elde edeceksiniz:** tam, çalıştırılabilir bir program, her adımın net açıklaması ve çözümü daha büyük belgeler veya farklı LLM sağlayıcıları için ölçeklendirme ipuçları.

![yerel llm öğretici diyagramı](https://example.com/local-llm-tutorial-diagram.png "Yerel llm öğreticisinin akışını gösteren diyagram")

## Önkoşullar

Başlamadan önce şunlara sahip olduğunuzdan emin olun:

- .NET 6.0 SDK veya daha yeni bir sürüm (Microsoft sitesinden indirebilirsiniz)
- OpenAI‑uyumlu bir uç nokta sunan yerel bir LLM sunucusu (ör. Ollama, LM Studio veya özel bir FastAPI sarmalayıcısı)
- `AiGrammar` NuGet paketi (veya `LocalLargeLanguageModel`, `Document` ve `AiModelType` sınıflarını sağlayan kütüphane)
- Daha sonra referans göstereceğiniz bir klasöre yerleştirilmiş örnek Word belgesi (`input.docx`)

Hepsi bu—ekstra bulut kimlik bilgilerine gerek yok.

## Adım 1: Yerel LLM Öğreticisi – Uç Noktayı Ayarlama

İlk olarak, isteklerini nereye göndereceğini bilen bir **call local llm** nesnesine ihtiyacımız var. Bunu, konuşmaya başlamadan önce çevirdiğiniz telefon numarası gibi düşünün.

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

**Neden önemli:**  
Çoğu LLM SDK'sı, OpenAI API sözleşmesini izleyen bir HTTP uç noktası bekler. `Endpoint`i `http://localhost:8000/v1` olarak ayarlayarak kütüphaneye **call local llm** yapmasını, OpenAI sunucularına bağlanmasını engelliyoruz. Sahte API anahtarı sadece bir yer tutucudur—bazı istemciler null değeri kabul etmez, bu yüzden zararsız bir şey veriyoruz.

> **İpucu:** LLM'i bir ters proxy arkasında çalıştırıyorsanız, `Endpoint`i proxy URL'sine ayarlayın ve TLS sonlandırmasını proxy'nin yapmasına izin verin. Bu, konsol uygulamanızı basit ve güvenli tutar.

## Adım 2: Dilbilgisi Kontrolü İçin Word Belgesini Yükleme

Model artık erişilebilir olduğuna göre, **load word document** içeriğini belleğe almamız gerekiyor. `Document` sınıfı `.docx` ayrıştırmasını bizim için soyutlar.

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

**Neden önemli:**  
İkili bir `.docx` dosyasını doğrudan bir LLM'e vermek onu şaşırtır. `Document` yardımcı sınıfı, paragraf sonlarını koruyarak ham metni çıkarır; bu da **ai grammar check** için temiz bir girdi sağlar. Varlık kontrolü, aksi takdirde uygulamayı çökerten bir `FileNotFoundException` oluşmasını önler.

## Adım 3: LLM Kullanarak Dilbilgisi Kontrolü Çalıştırma

İşte öğreticinin kalbi: yerel modeli metni düzeltmesi için soruyoruz. `CheckGrammar` yöntemi HTTP ayrıntılarını gizler ve bir sonuç nesnesi döndürür.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Neden önemli:**  
`AiModelType.Gpt4` sadece uzaktaki hizmete hangi istem şablonunun kullanılacağını söyleyen bir etikettir. Daha küçük bir modeliniz varsa (ör. `Llama2`), ona göre değiştirin. Kütüphane belge metnini serileştirir, `http://localhost:8000/v1/completions` adresine gönderir ve düzeltilmiş çıktıyı ayrıştırır.

> **Köşe durumu:** LLM zaman aşımına uğrarsa, `CheckGrammar` bir `TimeoutException` fırlatır. Büyük belgeler veya yoğun bir sunucu bekliyorsanız, çağrıyı bir `try/catch` bloğuna sarın.

## Adım 4: Düzeltlenmiş Metni Çıktı Olarak Verme

Son olarak, temizlenmiş sürümü ekrana basıyoruz. Gerçek bir uygulamada yeni bir `.docx` dosyasına geri yazabilirsiniz, ancak bu öğreticide bir konsol dökümü yeterli.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Beklenen çıktı** (orijinal dosyada birkaç kasıtlı hata olduğunu varsayarsak):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

LLM hiçbir hata bulamazsa, çıktı girişle aynı olur; bu hâlâ faydalı bir sinyaldir.

## Tam Çalışan Örnek

Her şeyi bir araya getirerek, yeni bir konsol projesine kopyalayıp yapıştırabileceğiniz tam program aşağıdadır:

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

### Nasıl Çalıştırılır

1. Proje klasöründe bir terminal açın.  
2. `dotnet run` komutunu çalıştırın.  
3. Konsolun düzeltilmiş metni yazdırmasını izleyin.

Bu, **local llm tutorial**ın 100 satırın altında tamamı.

## Sık Sorulan Sorular (SSS)

### Farklı bir LLM markası kullanabilir miyim?

Kesinlikle. Sunucu OpenAI v1 API şemasına uyduğu sürece sadece `Endpoint`i değiştirin ve ilgili `AiModelType` enum değerini (ör. `AiModelType.Llama2`) seçin. Kodun geri kalanı aynı kalır.

### Belgem çok büyük (10 MB+) ise ne yapmalıyım?

Büyük yükler birçok sunucunun varsayılan istek boyutunu aşabilir. Belgeyi bölümlere ayırıp her bölüm için `CheckGrammar` çağırın, ardından sonuçları birleştirin. Bu aynı zamanda zaman aşımı riskini de azaltır.

### Düzeltlenmiş çıktıyı bir `.docx` dosyasına nasıl kaydederim?

`Document` sınıfı genellikle bir `Save(string path, string content)` metodu sağlar. `result.CorrectedText` aldıktan sonra şu şekilde çağırın:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Tam imza için kütüphanenin belgelerine bakın.

### Sahte API anahtarı bir güvenlik riski mi?

Hayır. Anahtar, kend‑hosted uç noktalar tarafından göz ardı edilir, ancak bazı SDK'lar null olmayan bir dize zorunluluğu getirir. `"dummy"` gibi bir yer tutucu, SDK'yı gizli bir şey açığa çıkarmadan tatmin eder.

## Sonraki Adımlar ve İlgili Konular

- **Yerel LLM'nizi alan‑spesifik dilbilgisi için ince ayar yapın** (ör. hukuki veya tıbbi yazım).  
- **Bir toplu iş çalıştırın** ve bir klasördeki tüm Word dosyalarını işleyin—yayınlama hatları için harika.  
- **Akış yanıtlarını keşfedin** eğer kullanıcı yazarken gerçek‑zamanlı öneriler istiyorsanız.  
- **Yazım denetimi kütüphaneleri** ile birleştirerek çift katmanlı kalite kontrolü oluşturun.

Bu fikirlerin her biri, bu **local llm tutorial**da ele alınan temel kavramlar üzerine inşa edilmiştir; bu yüzden **call local llm**, **load word document**, **run grammar check** ve **handle results** kalıpları boyunca aynı desenleri göreceksiniz.

---

*Kodlamanın tadını çıkarın! Bir sorunla karşılaşırsanız, aşağıya yorum bırakın, birlikte çözüm bulalım.*


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Load Encrypted In Word Document](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}