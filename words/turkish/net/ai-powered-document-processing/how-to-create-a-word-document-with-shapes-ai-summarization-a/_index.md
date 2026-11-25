---
category: general
date: 2026-11-25
description: Word belgesi oluşturmayı, dikdörtgen şekli eklemeyi, belgeyi AI ile özetlemeyi,
  metni AI kullanarak çevirmeyi ve Aspose.Words ile belgeyi DOCX olarak kaydetmeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: tr
lastmod: 2026-11-25
og_description: Bir Word belgesi oluşturun, dikdörtgen şekli ekleyin, belgeyi AI ile
  özetleyin, metni AI kullanarak çevirin ve belgeyi DOCX olarak kaydedin—hepsi tek
  bir C# öğreticisinde.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: C# ile şekiller, AI özeti ve çeviri içeren bir Word belgesi oluşturun
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: C#'ta şekiller, AI özetleme ve çeviri içeren bir Word belgesi nasıl oluşturulur
url: /tr/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile şekiller, AI özetleme ve çeviri içeren bir Word belgesi nasıl oluşturulur

Programlı olarak **Word belgesi oluşturmanız** gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Aspose.Words for .NET kullanarak **rectangle shape eklemeyi**, bir AI hizmeti çağırarak **belgeyi AI ile özetlemeyi**, bir paragrafı **AI kullanarak metni çevirmeyi**, ve son olarak **belgeyi DOCX olarak kaydetmeyi** öğreneceksiniz.

Birçok geliştirici belge otomasyonu ve modern AI özelliklerini birleştirmekte zorlanıyor. Bu öğreticinin sonunda, görsel bir şekil, AI tarafından oluşturulan özet ve çok dilli içerik içeren tam biçimlendirilmiş bir *.docx* dosyası üreten tek bir, bağımsız C# projesine sahip olacaksınız.

## Önkoşullar

- .NET 6.0 SDK veya daha yeni bir sürüm yüklü  
- Visual Studio 2022 (veya herhangi bir C# IDE)  
- Aspose.Words for .NET lisansı (veya ücretsiz bir değerlendirme anahtarı)  
- AI özetleme ve çeviri çağrıları için internet erişimi  

Ek bir NuGet paketi `Aspose.Words` ve `Aspose.Words.AI` dışında gerekli değildir.

## Adım 1: Projeyi kurun ve gerekli paketleri ekleyin

Yeni bir konsol projesi oluşturun ve Aspose.Words kütüphanelerini ekleyin.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** Değerlendirme modunu kullanmayı planlıyorsanız, `Main` içinde erken bir aşamada `Aspose.Words.License.SetLicense("Aspose.Words.lic");` çağırarak filigranları önleyin.

## Adım 2: Belgeyi başlatın – **create word document** işleminin çekirdeği

İlk uygulanabilir kod satırı yeni bir **Word document** nesnesi oluşturur. Bu nesne sonraki tüm işlemler için bir tuval görevi görür.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder`, düşük seviyeli düğüm ağaçlarını manuel olarak yönetmeden metin, şekil ve denetim eklemeyi basitleştirir.

## Adım 3: Belgeye **Add rectangle shape** ekleyin

Bir rectangle shape, görsel bir yer tutucu, etiket arka planı veya basit bir grafik olarak kullanılabilir. İlk olarak bir `GroupShape` oluşturur, ardından içine bir `Rectangle` ekleriz.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Bu rectangle 100 puan genişliğinde ve 50 puan yüksekliğindedir. `GroupShape` içinde bulunduğu için, daha sonra daha fazla öğe (ör. metin kutuları) ekleyebilir ve yerleşim çakışmalarını düşünmek zorunda kalmazsınız.

## Adım 4: Düz metin StructuredDocumentTag (SDT) ekleyin

StructuredDocumentTag nesneleri, daha sonra veri kaynaklarına bağlanabilecek içerik denetimleri için faydalıdır.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true` bayrağı, etiketi **repeating** bir denetim olarak işaretler; bu şablonlar için kullanışlıdır.

## Adım 5: ActiveX CommandButton denetimi ekleyin (isteğe bağlı UI)

Oluşturulan belge ActiveX destekleyen bir ortamda kullanılacaksa, bir düğme gömebilirsiniz.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Bu adım isteğe bağlıdır; hedef kitleniz belgenin Windows ortamında hiç etkileşime girmeyecekse kaldırabilirsiniz.

## Adım 6: **Summarize document with AI**

Aspose.Words.AI, büyük dil modeli hizmetleri etrafında kullanışlı bir sarmalayıcı sağlar. Burada OpenAI arka ucu ile `DocumentSummarizer.Summarize` metodunu çağırıyoruz.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Metod, mevcut düğüm ağacını analiz eder, en ilgili cümleleri çıkarır ve öz bir paragraf döndürür. Bu, **summarize document with AI** işlevselliğinin çekirdeğidir.

## Adım 7: **Translate text using AI**

Sonra örnek bir dizeyi İngilizceden Fransızcaya nasıl çevireceğimizi gösteriyoruz. `Translator.Translate` metodu dahili olarak bir Google AI modelini çağırır.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

`Language.French` ifadesini, desteklenen herhangi bir dil enum değeriyle değiştirebilir, böylece anlık çok dilli belge üretimi sağlayabilirsiniz.

## Adım 8: **Save document as DOCX**

Son olarak, düzenlenmiş belgeyi diske kaydedin. `.docx` uzantısını belirttiğinizde `Save` metodu otomatik olarak bir *.docx* dosyası yazar.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

`Result.docx` dosyası artık şunları içeriyor:

- Bir grup şekil içinde rectangle shape  
- Düz metin içerik denetimi (SDT)  
- Bir ActiveX CommandButton (Adım 5'i tuttuysanız)  
- AI tarafından oluşturulan özet paragrafı  
- “Hello world” ifadesinin Fransızca çevirisi  

Dosyayı Microsoft Word'de açarak her bir öğeyi doğrulayabilirsiniz.

## Tam kaynak kodu

Aşağıda tam, çalıştırmaya hazır program bulunmaktadır. `Program.cs` içine kopyalayın ve `dotnet run` komutunu çalıştırın.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Beklenen çıktı

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

`Result.docx` dosyasını açtığınızda, üst kısımda rectangle shape, SDT yer tutucu, düğme, özet paragraf ve düz metin olarak eklenmiş Fransızca çeviriyi göreceksiniz.

## Sonuç

Artık sıfırdan **Word belgesi oluşturmayı**, **rectangle shape eklemeyi**, **belgeyi AI ile özetlemeyi**, **AI kullanarak metni çevirmeyi** ve **belgeyi DOCX olarak kaydetmeyi**—hepsi birkaç özlü C# satırıyla biliyorsunuz. Bu desen ölçeklenebilir: sabit kodlanmış dizeleri dinamik verilerle değiştirebilir, daha fazla şekil veya grafik ekleyebilir ve `SummarizerOptions` ya da `Translator` parametrelerini ayarlayarak AI sağlayıcısını değiştirebilirsiniz.

### Sıradaki adımlar?

- **add rectangle shape** varyasyonlarını keşfedin: dolgu rengini, çizgi stilini değiştirin veya şeklin içine metin ekleyin.  
- Daha büyük belgelerde **summarize document with AI** kullanarak otomatik yönetici özetleri oluşturun.  
- **translate text using AI**'yi genişleterek tüm paragrafları veya tabloları toplu işleyin ve çok dilli raporlar üretin.  
- Aspose.Words grafik API'lerini birleştirerek AI‑tarafından oluşturulan içgörülerle birlikte veri görselleştirmeleri ekleyin.  

Denemekten çekinmeyin ve sonuçlarınızı yorumlarda ya da GitHub'da paylaşın. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Boş bir Word belgesi oluşturma ve rectangle shape ekleme](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Aspose.Words for .NET kullanarak Word belgesine Grup Şekli ekleme](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET kullanarak Word belgesine Metin Filigranı ekleme](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}