---
category: general
date: 2026-04-28
description: C#'tan yerel LLM'ye bağlan ve büyük dil modeline Word belgesini yüklemesi
  için komut ver, yerel LLM'yi çağır ve metni otomatik olarak yeniden yaz. Adım adım
  kod dahil.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: tr
og_description: C#'tan yerel LLM'ye bağlanın ve büyük dil modelini nasıl yönlendireceğinizi
  görün, Word belgesini yükleyin, yerel LLM'yi çağırın ve metni dakikalar içinde otomatik
  olarak yeniden yazın.
og_title: C#'de Yerel LLM'ye Bağlan – Tam Programlama Rehberi
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: C#'ta Yerel LLM'ye Bağlan – Tam Programlama Rehberi
url: /tr/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Yerel LLM'ye Bağlan – Tam Programlama Rehberi

Hiç .NET uygulamasından **yerel llm'ye bağlan**manız ve bunun bir Word dosyasıyla nasıl konuşacağını merak ettiniz mi? Yalnız değilsiniz. Bu rehberde tüm süreci adım adım inceleyeceğiz—yerel llm'ye bağlan, **büyük dil modelini yönlendir**, bir Word belgesi yükle, **yerel llm'yi çağır**, ve sonunda **metni otomatik olarak yeniden yaz**. Sonunda, dış API anahtarları olmadan herhangi bir paragrafı resmi bir üsluba dönüştüren çalıştırılabilir bir örnek elde edeceksiniz.

## Bu Öğreticide Neler Kapsanıyor

İlk olarak gerekli NuGet paketlerini kuracağız, ardından basit bir yerel LLM uç noktasını (örneğin Ollama 11434 portunda) çalıştıracağız. Daha sonra Aspose.Words kullanarak bir `.docx` dosyasını yükleyecek, bir paragrafı LLM'ye gönderecek, yeniden yazılmış bir sürüm alacak ve aynı belgeye geri yazacağız. Ayrıca yaygın tuzakları—null paragraflar, async disposal ve kodlama sorunları—nasıl ele alacağınızı göreceksiniz; böylece kod sadece bir demo değil, üretimde de çalışır.

### Önkoşullar

- .NET 6.0 SDK veya daha yeni bir sürüm (isteğe bağlı olarak .NET 8 de kullanabilirsiniz)
- Visual Studio 2022 veya C# uzantılı VS Code
- **Aspose.Words for .NET** (ücretsiz deneme yeterli)
- `/api/generate` sözleşmesini destekleyen yerel bir LLM (ör. Ollama, LMStudio)
- C#'ta async/await konusunda temel bilgi

> **Pro tip:** Eğer henüz Ollama'yı kurmadıysanız, `ollama serve` komutunu çalıştırın ve `ollama pull llama3` ile bir model indirin. Varsayılan HTTP uç noktası `http://localhost:11434/api/generate` olacaktır.

---

## Adım 1: Gerekli Paketleri Kurun

İlk olarak, projenize Aspose.Words ve Aspose.Words.AI NuGet paketlerini ekleyin.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Bu kütüphaneler bize **Word belgesini yükleme** yeteneği ve **yerel llm'yi çağırma** için HTTP isteklerini elle oluşturmak zorunda kalmadan ince bir sarmalayıcı sağlar.

---

## Adım 2: Yerel LLM Uç Noktasına Bağlan

Yerel olarak barındırılan bir modele bağlanmak, `LocalLargeLanguageModel` sınıfını örneklemek kadar basittir. Yapıcı, oluşturma uç noktasının tam URL'sini bekler.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Neden uç noktayı bir sınıf içinde sarmalıyoruz? `LocalLargeLanguageModel`, JSON serileştirmesini, yeniden denemeleri ve akış yanıtlarını sizin için yönetir—böylece `HttpClient` ile uğraşmak yerine istem (prompt) mantığına odaklanabilirsiniz.

---

## Adım 3: Kaynak Word Belgesini Yükle

Sonra belgeyi belleğe alıyoruz. Aspose.Words neredeyse tüm Word formatlarını destekler, bu yüzden `Document`, Office yüklü olmadan `input.docx` dosyasını ayrıştıracaktır.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Eğer bir akış (ör. ASP.NET üzerinden yüklenen bir dosya) ile çalışmanız gerekiyorsa, dosya yolunu bir `MemoryStream` ile değiştirin ve `Document` yapıcısına geçirin.

---

## Adım 4: Mevcut Paragraf Metnini Çıkar

`DocumentBuilder` kullanarak belge içinde gezineceğiz. Bu örnekte **ilk paragrafı** yeniden yazıyoruz, ancak birden çok paragrafı işlemek için `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` üzerinde dönebilirsiniz.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

`?.` operatörü, belge boş olduğunda `NullReferenceException` oluşmasını önler. Bu, yeni başlayanların sıkça karşılaştığı **kenar durum**lardan biridir.

---

## Adım 5: LLM'yi Paragrafı Yeniden Yazması İçin İstemi Gönder

Şimdi gerçekten **büyük dil modeline istem gönderiyoruz**. İstem düz İngilizcedir; sarmalayıcı bunu JSON olarak yerel uç noktaya gönderir.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

İsteği bu şekilde ifade etmemizin nedeni nedir? LLM'ler net, tek‑görevli talimatlara en iyi yanıt verir. İki nokta üstünden sonra bir yeni satır eklemek, talimatı içerikten ayırır ve modelin istemi geri tekrarlama olasılığını azaltır.

**Beklenen çıktı** – `originalParagraph` `"Hey, what's up?"` ise, LLM şu şekilde dönebilir:

> “İyi günler, size nasıl yardımcı olabilirim?”

Sonucu, ekrana yazdırarak doğrulayabilirsiniz:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Adım 6: Yeniden Yazılmış Metni Belgeye Geri Yerleştir

Yeni metni elde ettiğimizde, eski paragrafı değiştiririz. `DocumentBuilder.Writeln` yeni bir satır yazar ve imleci ileri hareket ettirir; ekleme için mükemmeldir. Aynı paragrafı *tamamen* değiştirmek isterseniz, yazmadan önce `docBuilder.CurrentParagraph.RemoveAllChildren()` kullanabilirsiniz.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Her iki yaklaşım da gösterildi, böylece iş akışınıza uyanı seçebilirsiniz.

---

## Adım 7: Güncellenmiş Belgeyi Kaydet

Son olarak, değişiklikleri yeni bir dosyaya kaydediyoruz. Aspose.Words dosya uzantısına göre formatı otomatik seçer.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

`output.docx` dosyasını Word'de açın, paragrafın artık resmi bir üslupla okunduğunu göreceksiniz.

---

## Tam Çalışan Örnek

Aşağıda **tam, bağımsız program** yer alıyor. Bir konsol projesine kopyalayıp yapıştırın, NuGet paketlerini geri yükleyin ve çalıştırın—çalışan bir yerel LLM dışında ekstra yapılandırma gerekmez.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Çalıştırdığınızda Ne Beklemelisiniz

1. Konsol, orijinal ve yeniden yazılmış paragrafları yazdırır.  
2. `output.docx`, `input.docx`'nin yanında görünür.  
3. Dosyayı açtığınızda yeni resmi paragrafın orijinalin ardından (veya alternatif koda geçerseniz değiştirilmiş olarak) eklendiğini görürsünüz.

---

## Yaygın Kenar Durumlarını Ele Alma

| Situation | Solution |
|-----------|----------|
| **Boş veya sadece boşluk içeren paragraf** | İstem göndermeden önce `string.IsNullOrWhiteSpace` kontrol edin (Adım 3'e bakın). |
| **LLM bir hata döndürür veya boş string verir** | `PromptAsync`'i bir `try/catch` bloğuna alın ve orijinal metne geri dönün. |
| **Birden fazla paragrafın yeniden yazılması gerekiyor** | `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` üzerinde döngü kurun ve aynı istem mantığını uygulayın. |
| **Büyük belgeler gecikmeye neden olur** | Paragrafları toplu hâle getirip tek bir istekle gönderin (istek başına 4 KB'ye kadar). |
| **ASCII olmayan karakterler bozulur** | LLM uç noktasının UTF‑8 kullandığından emin olun (çoğu modern model bunu yapar). |

---

## Sonraki Adımlar ve İlgili Konular

- **Büyük dil modeline** daha zengin talimatlarla (ör. stil rehberleri, uzunluk sınırları) istem gönderin.  
- Belge otomasyonunu bir hizmet olarak sunmak için bir web API'de **yerel llm'yi çağır**.  
- Yüksek verim senaryoları için paralel akışlarda **Word belgesini yükle** özelliğini keşfedin.  
- Bu yaklaşımı toplu e‑posta üretimi veya rapor standartlaştırması için **metni otomatik olarak yeniden yaz** ile birleştirin.  

Daha derine inmek isterseniz, Aspose'un **belge birleştirme** dokümantasyonuna ve özel örnekleme parametreleri için Ollama API referansına göz atın.

---

## Sonuç

C#'ta **yerel llm'ye bağlan**, **büyük dil modeline istem gönder**, **Word belgesini yükle**, **yerel llm'yi çağır** ve **metni otomatik olarak yeniden yaz** nasıl yapılacağını az önce gösterdik—hepsi tek bir çalıştırılabilir konsol uygulamasında. Bu desen ölçeklenebilir: istemi değiştirin, paragraflar üzerinde döngü kurun veya mantığı bir ASP.NET uç noktası üzerinden dışa aktarın. Ana çıkarım, yerel AI modellerinin klasik belge işleme kütüphaneleriyle sıkı bir şekilde bütünleştirilebileceği ve güvenilir on‑prem ortamınızdan çıkmadan güçlü otomasyon sağlayabileceğidir.

İş parçacığı (threading) hakkında sorularınız varsa,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}