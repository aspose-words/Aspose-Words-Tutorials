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

Hiç **LLM'yi nasıl arayacağım**'i bir .NET gösterdiğin, veri buluta göndermeden çağırmayı düşünmedin mi? Yalnız değildin. Birçok geliştirici, özellikle hassas metinlerle çalışıyor, bilgilerini ve kayıtlarını yerinde tutmak istiyor. Bu öğreticide gerçek bir senaryoyu adım adım ince parçalar: kendi içinde barındırdığınız bir LLM uç alanlarını kullanarak bir Word belgesini yeniden yazın, tüm içeriği kaydeder, saklanır ve sonunda **docx nasıl kaydedilir**'i diske okur.

Ayrıca **use local LLM**'i nasıl dağıtacağını, Aspose.Words `Document`'tan **remove all content**'i nasıl kaldıracağınızı tam kod örnekleriyle anlatacak ve Word'ün programatik olarak düzenlemesinin inceliklerini açıklayacağız. Sonunda Aspose.Words7+ ve herhangi bir OpenAI‑uyumlu yerel model ile çalışan bir kopyala‑yapıştır çözümünüz olacak.

## Önkoşullar – Başlamadan Önce İhtiyacınız Olanlar

- **.NET 6+** (veya klasik tercih .NET Framework 4.7.2)
- **Aspose.Words for .NET** NuGet paketi (`Aspose.Words` ve `Aspose.Words.AI`)
- **local LLM**'nizin OpenAI‑uyumlu `/v1` uç dağıtması (ör.`http://localhost:8000/v1` üzerindeki bir GPT‑Neo sunucusu) yayınlaması
- Bir klasörde bulunan örnek `input.docx'ı kontrol edin
- Visual Studio, Rider veya sevdiğiniz herhangi bir editör – ekran görüntülerinde VS Code kullanacağım

> **Pro ipucu:** Henüz bir yerel modeliniz yoksa, ücretsiz Docker görüntüsü GPT‑Neo2.7B'yi inceleyin – bir dakikadan kısa sürede çalışır ve burada Sonuçta aynı API sözleşmesini izler.

## Adım 1 – Yerel LLM Uç Noktasını Yapılandırma (LLM Nasıl Aranır)

C#'tan **nasıl çağrılacağını** yapmak istediğinizde ilk yapmak istediğiniz, kendi içinde barındırdığınız hizmet işaretlerini gösteren bir nesne oluşturmaktır. Aspose.Words.AI, HTTP çağrılarını soyutlayan bir `LocalLargeLanguageModel` yardımcı sınıfı sunar.

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

> **Neden önemli:** Uç noktayı kişisel olarak yapılandırarak istekleri yüklerini, kimlik kesintiyi ve gecikmeyi tam kontrol altında tutarsınız. Bu, **llm nasıl çağırılır**'i dış hizmetlere bağımlı olmadan yapılma temelidir.

## Adım 2 – Kaynak Word Belgesini Yükleyin (Word Nasıl Düzenlenir)

Şimdi orijinal `.docx`ın bir kısmı Aspose `Document` nesnesine yüklüyoruz. Bu, klasik “**sözcük nasıl düzenlenir**” adımıdır: dosya alındıktan sonra boyutu sorgulanabilir, ortaya çıkabilir veya tamamen yenisiyle değiştirebilirsiniz.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Dosya bulunamazsa `FileNotFoundException` kullanırsınız; bu yüzden yolun doğru olduğundan emin olun. Yüklemelerle çalışıyorsanız `Stream` üzerinden yükleyebilirsiniz.

## Adım 3 – Yerel LLM'yi Kullanarak Gözden Geçirilmiş Metin Oluşturun (LLM Nasıl Aranır)

Şimdi sihirli bir kısmını gerçekleştiriyoruz: LLM'den tüm metnin resmi bir üslupla yeniden yazmasını istiyoruz. İstem, kısa bir talimat ile `document.GetText()` ile alınan ve metnin birleştirilmesiyle oluşturulur.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Edge case:** Kaynak belge çok büyükse (10k token üzeri) modelin bağlama limitine takılabilirsin. Bu durumda metin paragraflara bölüp onu bir parçayı `GenerateText` ile çağırın.

## Adım 4 – Mevcut Tüm İçeriği Kaldır (Tüm İçeriği Kaldır)

Yeni metni eklemeden önce belgelememizin temizlenmesi gerekiyor. Aspose, bölümler, paragraflar, tablolar—her şeyi silen `RemoveAllChildren()` yöntemini sunar. Bu, bir Word dosyasından **tüm içeriği kaldır**'i kaldırmanın kanonik olarak dağıtılmasıdır.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **Ya yalnızca gövdeyi silip başlıkları tutmak isteseydiniz?** `document.Sections.Clear()` kullanın ve ardından ihtiyacınız olan parçaları yeniden oluşturun.

## Adım 5 – Gözden Geçirilmiş Metni Ekleme (Word Nasıl Düzenlenir)

Temiz bir sayfa ile LLM tarafından üretilen metni geri yazabiliriz. `DocumentBuilder`, paragraflar, tablolar, görseller vb. miktarını sağlayan bir sarmalayıcıdır. Burada tüm dizeyi tek bir paragraf olarak yazıyoruz.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Daha zengin biçimlendirme (kalın, başlıklar) istiyorsanız, LLM'nin çıkışındaki markdown işaretlerini ayrıştırıp `builder.Font`un yapısına göre buna göre uygulayabilirsiniz.

## Adım 6 – Güncellenen Belgeyi Kaydedin (Docx Nasıl Kaydedilir)

Son olarak bozulan yeni bir dosyaya kalıcı hâle getiriyoruz. Bu, programatik düzenlemelerden sonra **docx'in nasıl kaydedileceğini**'i göstermektedir.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

`Kaydet' yöntemi dosya uzantısından formatı otomatik algılamalar; tek bir satır değişikliğiyle PDF, HTML veya ODT olarak da düzenlenebilir.

### Beklenen Sonuç

`output.docx` açıldığında, orijinal içeriğin tamamen cilalı, resmi bir üslupla yeniden yazıldığını gör. Kaynak belgeden kalan tablo, başlık veya alt bilgi kalmamış; sadece LLM'in aldığı yeni metin bulunur.

---

![Output.docx'in Word'de açılmış ekran görüntüsü, yeniden yazılmış resmi metni gösteriyor - llm nasıl çağrılır](/images/output-docx.png "llm örneği nasıl çağrılır")

*Resim alt metni:* **yeniden yazılmış Word belgesini gösteren llm örneğinin nasıl çağrılacağı**

## Yaygın Sorular ve Sorun Giderme

### 1. “Ya Yüksek Lisansım hata verirse?”

`GenerateText` yöntemi, 2xx olmayan yanıtlar için bir `HttpRequestException` fırlatır. Çağrıyı bir `try/catch` `ın alınmasına ve `ex.Message``ı incelemeye alın. Çoğu zaman sorun eksik bir API anahtarının başlığı ya da modelin token limitini aşmaktır.

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

### 2. “Her şeyi silmek yerine belgenin belirli bölümlerini düzenleyebilir miyim?”

kesinlikle. `document.GetChildNodes(NodeType.Paragraph, true)` ile paragrafları döngüye aktarma sadece ihtiyacı olanın `Paragraph.Text` özelliği onaylanmıştır. Bu yöntem, **sözcüğün nasıl düzenleneceğini**'i daha ince bir şekilde tamamlamayı sağlar ve bütünlüğü korur.

### 3. “Orijinal biçimlendirmeyi korumanın bir yolu var mı?”

Stilleri korumak istiyorsanız, LLM çıkışını düz metin olarak alıp paragraf için `builder.Font.StyleIdentifier`ı planlamanıza göre programlar. Alternatif olarak LLM HTML üretebilirsa `DocumentBuilder.InsertHtml()` kullanabilirsiniz.

### 4. “Büyük belgeleri nasıl işleyebilirim?”

Belgeyi bölümlere (`belge.Bölümler`) ayırıp onu birini ayrı ayrı işleyin. Bu yalnızca token limitlerinizi aştığınızı belirterek, aynı zamanda bellek kullanımından da tasarruf etmenizi sağlar.

## Performans İpuçları

- **Birden fazla çağrıda `LocalLargeLanguageModel` örneğini yeniden kullanın;** alttaki `HttpClient` bağlantıyı canlı tutacaktır.

- Aynı komut istemini tekrar tekrar çalıştırmayı bekliyorsanız, **düzenlenmiş metni önbelleğe alın**—LLM çağrıları yerel donanımda bile maliyetli olabilir.

- Çok çekirdekli bir CPU'nuz ve iş parçacığı güvenli bir LLM istemciniz varsa, bölüm işlemeyi `Parallel.ForEach` ile **paralelleştirin**.

## Sonraki Adımlar – İş Akışını Genişletme

Artık **llm nasıl aranır**, **yerel llm kullanılır**, **tüm içeriği kaldır**, **kelime nasıl düzenlenir** ve **docx nasıl kaydedilir** konularını bildiğinize göre aşağıdaki konuları keşfedebilirsiniz:

- **Toplu işleme**: Bir klasördeki tüm `.docx` dosyaları üzerinde aynı yeniden yazma mantığını döngüyle çalıştırılır.
- **Özel istemler**: İstemi özetler, madde listeleri veya çeviriler seçilip seçilebilir.
- **ASP.NET Core ile entegrasyon**: Bir dosyayı yükleme kabul eden, LLM'i çalıştıran ve silinen belgeyi dönen bir HTTP uç noktası birleştirir.
- **Gelişmiş stillendirme**: LLM'den gelen markdown'ı Word'ün içeriğine `DocumentBuilder` ile eşleyin.

Bu yaygınların her biri, burada ele alınan temel desen üzerine kurulur; bu kod sayesinde minimum çabayla uyum sağlayabilirsiniz.

---

## Çözüm

Bu rehberde **how to call llm**'i bir .NET projesinden kendi barındırdığınız uç nokta üzerinden nasıl yapılacağını, **use local llm**'i nasıl saklandığını, bir Word dosyasından **remove all content**'i nasıl sileceğinizi, **how to edit word**'i programatik olarak nasıl gerçekleştireceğinizi ve **nasıl docx kaydedeceğinizi**'i nasıl tamamlayacağınızı gösterdi. Tam, çalıştırılabilir örnek herhangi bir .NET projesine eklenmeye hazır ve her adımın “neden”ini işlemlerini notlar sayesinde kodu yapılandırma özelleştirebilir, genişletebilir veya hata ayıklayabilirsiniz.

Deneylerin, farklı istemlerle oynama ve yerel LLM'nizin belge otomasyon hatlarını nasıl güçlendirebileceği. Sorun yaşarsanız, sorun giderici bölümü sizi doğru yöne yönlendirecektir. İyileşmeler ve yerel LLM'lerin gücünün tadını çıkarmak!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}