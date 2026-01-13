---
category: general
date: 2026-01-13
description: Yerel bir LLM uç noktasını kullanarak C#'tan LLM'yi nasıl çağıracağınızı,
  Word dosyalarını nasıl düzenleyeceğinizi, tüm içeriği nasıl kaldıracağınızı ve docx'i
  nasıl kaydedeceğinizi tek bir öğreticide öğrenin.
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: tr
og_description: Yerel bir model kullanarak C#'tan LLM'yi nasıl çağırılır, Word belgelerini
  düzenleme, tüm içeriği kaldırma ve docx'i verimli bir şekilde kaydetme.
og_title: C#'de LLM Nasıl Çağrılır – Adım Adım Öğretici
tags:
- Aspose.Words
- C#
- LLM Integration
title: C#'de LLM Nasıl Çağrılır – Yerel Model ile Tam Rehber
url: /tr/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta LLM Nasıl Çağrılır – Yerel Model ile Tam Kılavuz

Hiç **how to call LLM**'i bir .NET uygulamasından, verileri buluta göndermeden çağırmayı düşündünüz mü? Yalnız değilsiniz. Birçok geliştirici, özellikle hassas metinlerle çalışırken, istemlerini ve belgelerini yerinde tutmak istiyor. Bu öğreticide gerçek bir senaryoyu adım adım inceleyeceğiz: kendi barındırdığınız bir LLM uç noktasını kullanarak bir Word belgesini yeniden yazmak, tüm içeriği kaldırmak, dosyayı düzenlemek ve sonunda **how to save docx**'i diske kaydetmek.  

Ayrıca **use local LLM**'i nasıl kullanacağınızı gösterecek, Aspose.Words `Document`'tan **remove all content**'i nasıl kaldıracağınızı tam kod örnekleriyle anlatacak ve Word dosyalarını programatik olarak düzenlemenin inceliklerini açıklayacağız. Sonunda, Aspose.Words 7+ ve herhangi bir OpenAI‑uyumlu yerel model ile çalışan bir kopyala‑yapıştır çözümünüz olacak.

## Prerequisites – What You Need Before You Start

- **.NET 6+** (veya klasik tercih ediyorsanız .NET Framework 4.7.2)
- **Aspose.Words for .NET** NuGet paketi (`Aspose.Words` ve `Aspose.Words.AI`)
- **local LLM**'inizin OpenAI‑uyumlu `/v1` uç noktasını (ör. `http://localhost:8000/v1` üzerindeki bir GPT‑Neo sunucusu) yayınlaması
- Kontrol ettiğiniz bir klasörde bulunan örnek `input.docx`
- Visual Studio, Rider veya sevdiğiniz herhangi bir editör – ekran görüntülerinde VS Code kullanacağım

> **Pro tip:** Henüz bir yerel modeliniz yoksa, ücretsiz Docker görüntüsü GPT‑Neo 2.7B'yi inceleyin – bir dakikadan kısa sürede çalışır ve burada kullandığımız aynı API sözleşmesini izler.

## Step 1 – Configure the Local LLM Endpoint (How to Call LLM)

C#'tan **how to call llm** yapmak istediğinizde ilk yapmanız gereken, kendi barındırdığınız servise işaret eden bir istemci nesnesi oluşturmaktır. Aspose.Words.AI, HTTP çağrılarını soyutlayan bir `LocalLargeLanguageModel` yardımcı sınıfı sunar.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **Why this matters:** Uç noktayı kendiniz yapılandırarak istek yüklerini, kimlik doğrulamayı ve gecikmeyi tam kontrol altında tutarsınız. Bu, **how to call llm**'i dış hizmetlere bağımlı olmadan yapmanın temelidir.

## Step 2 – Load the Source Word Document (How to Edit Word)

Şimdi orijinal `.docx` dosyasını bir Aspose `Document` nesnesine yüklüyoruz. Bu, klasik “**how to edit word**” adımıdır: dosya belleğe alındıktan sonra içeriğini sorgulayabilir, değiştirebilir veya tamamen yenisiyle değiştirebilirsiniz.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Dosya bulunamazsa `FileNotFoundException` alırsınız; bu yüzden yolun doğru olduğundan emin olun. Yüklemelerle çalışıyorsanız `Stream` üzerinden de yükleyebilirsiniz.

## Step 3 – Generate Revised Text Using the Local LLM (How to Call LLM)

Şimdi sihirli kısmı gerçekleştiriyoruz: LLM'den tüm metni resmi bir üslupla yeniden yazmasını istiyoruz. İstem, kısa bir talimat ile `document.GetText()` ile alınan ham metnin birleştirilmesiyle oluşturulur.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Edge case:** Kaynak belge çok büyükse (10 k token üzeri) modelin bağlam limitine takılabilirsiniz. Bu durumda metni paragraflara bölüp her bir parçayı `GenerateText` ile çağırın.

## Step 4 – Remove All Existing Content (Remove All Content)

Yeni metni eklemeden önce belgeyi temizlememiz gerekiyor. Aspose, bölümler, paragraflar, tablolar—her şeyi silen `RemoveAllChildren()` metodunu sunar. Bu, bir Word dosyasından **remove all content**'i kaldırmanın kanonik yoludur.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **What if you only wanted to delete the body but keep headers?** `document.Sections.Clear()` kullanın ve ardından ihtiyacınız olan bölümleri yeniden oluşturun.

## Step 5 – Insert the Revised Text (How to Edit Word)

Temiz bir sayfa ile LLM tarafından üretilen metni geri yazabiliriz. `DocumentBuilder`, paragraflar, tablolar, görseller vb. eklemenizi sağlayan dostça bir sarmalayıcıdır. Burada tüm dizeyi tek bir paragraf olarak yazıyoruz.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Daha zengin biçimlendirme (kalın, başlıklar) istiyorsanız, LLM çıktısındaki markdown işaretlerini ayrıştırıp `builder.Font` ayarlarını buna göre uygulayabilirsiniz.

## Step 6 – Save the Updated Document (How to Save Docx)

Son olarak değişiklikleri yeni bir dosyaya kalıcı hâle getiriyoruz. Bu, programatik düzenlemelerden sonra **how to save docx**'i göstermektedir.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

`Save` metodu dosya uzantısından formatı otomatik algılar; tek bir satır değişikliğiyle PDF, HTML veya ODT olarak da dışa aktarabilirsiniz.

### Expected Result

`output.docx` dosyasını açtığınızda, orijinal içeriğin tamamen cilalı, resmi bir üslupla yeniden yazıldığını görmelisiniz. Kaynak belgeden kalan tablo, başlık veya alt bilgi kalmamış; sadece LLM'in ürettiği yeni metin bulunur.

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "how to call llm example")

*Image alt text:* **how to call llm example showing rewritten Word document**

## Common Questions & Troubleshooting

### 1. “What if my LLM returns an error?”

`GenerateText` metodu, 2xx olmayan yanıtlar için bir `HttpRequestException` fırlatır. Çağrıyı bir `try/catch` bloğuna alın ve `ex.Message`'ı inceleyin. Çoğu zaman sorun eksik bir API anahtarı başlığı ya da modelin token limitini aşmaktır.

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. “Can I edit specific parts of the document instead of wiping everything?”

Kesinlikle. `document.GetChildNodes(NodeType.Paragraph, true)` ile paragrafları döngüye alıp sadece ihtiyacınız olan yerlerde `Paragraph.Text` özelliğini değiştirin. Bu yöntem, **how to edit word**'i daha ince bir seviyede yapmanızı sağlar ve stilleri korur.

### 3. “Is there a way to keep the original formatting?”

Stilleri korumak istiyorsanız, LLM çıktısını düz metin olarak alıp her paragraf için `builder.Font.StyleIdentifier`'ı şablonunuza göre uygulayın. Alternatif olarak, LLM HTML üretebiliyorsa `DocumentBuilder.InsertHtml()` kullanabilirsiniz.

### 4. “How do I handle large documents?”

Belgeyi bölümlere (`document.Sections`) ayırıp her birini ayrı ayrı işleyin. Bu sadece token limitlerini aşmanızı engellemekle kalmaz, aynı zamanda bellek kullanımını da azaltır.

## Performance Tips

- **Reuse the `LocalLargeLanguageModel` instance** across multiple calls; the underlying `HttpClient` will keep the connection alive.
- **Cache the revised text** if you expect to run the same prompt repeatedly—LLM calls can be costly even on local hardware.
- **Parallelize** section processing with `Parallel.ForEach` when you have a multi‑core CPU and a thread‑safe LLM client.

## Next Steps – Extending the Workflow

Artık **how to call llm**, **use local llm**, **remove all content**, **how to edit word** ve **how to save docx** konularını bildiğinize göre aşağıdaki konuları keşfedebilirsiniz:

- **Batch processing**: Bir klasördeki tüm `.docx` dosyaları üzerinde aynı yeniden yazma mantığını döngüyle çalıştırın.
- **Custom prompts**: İstemi özetler, madde listeleri veya çeviriler üretmek üzere özelleştirin.
- **Integration with ASP.NET Core**: Bir dosya yükleme kabul eden, LLM'i çalıştıran ve düzenlenmiş belgeyi dönen bir HTTP uç noktası oluşturun.
- **Advanced styling**: LLM'den gelen markdown'ı Word stillerine `DocumentBuilder` ile eşleyin.

Bu uzantıların her biri, burada ele aldığımız temel desen üzerine kuruludur; bu sayede kodu minimum çabayla adapte edebilirsiniz.

---

## Conclusion

Bu rehberde **how to call llm**'i bir .NET projesinden kendi barındırdığınız uç nokta üzerinden nasıl yapacağınızı, **use local llm**'i nasıl kullanacağınızı, bir Word dosyasından **remove all content**'i nasıl sileceğinizi, **how to edit word**'i programatik olarak nasıl gerçekleştireceğinizi ve **how to save docx**'i nasıl tamamlayacağınızı gösterdik. Tam, çalıştırılabilir örnek herhangi bir .NET projesine eklenmeye hazır ve her adımın “neden”ini açıklayan notlar sayesinde kodu rahatça özelleştirebilir, genişletebilir veya hata ayıklayabilirsiniz.

Deneyin, farklı istemlerle oynayın ve yerel LLM'inizin belge otomasyon hatlarını nasıl güçlendirebileceğini keşfedin. Sorun yaşarsanız, sorun giderme bölümü sizi doğru yöne yönlendirecektir. İyi kodlamalar ve yerel LLM'lerin gücünün tadını çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}