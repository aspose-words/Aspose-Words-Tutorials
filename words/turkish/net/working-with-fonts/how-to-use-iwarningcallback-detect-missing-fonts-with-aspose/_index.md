---
category: general
date: 2026-06-24
description: Aspose.Words belgelerinde eksik yazı tiplerini tespit etmek için IWarningCallback
  nasıl kullanılır. Tam, çalıştırılabilir bir örnek ve en iyi uygulamaları öğrenin.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: tr
og_description: Aspose.Words'ta eksik yazı tiplerini tespit etmek için IWarningCallback
  nasıl kullanılır? Tam ve üretim ortamına hazır bir çözüm için adım adım kılavuzu
  izleyin.
og_title: IWarningCallback Nasıl Kullanılır – Eksik Yazı Tiplerini Tespit Et
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: IWarningCallback Nasıl Kullanılır – Aspose.Words ile Eksik Yazı Tiplerini Tespit
  Etme
url: /tr/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile IWarningCallback Nasıl Kullanılır – Eksik Yazı Tiplerini Algılayın

**IWarningCallback** kullanımı, Aspose.Words ile çalışırken bir DOCX dosyasındaki **eksik yazı tiplerini algılamak** için çok önemlidir. Bu rehberde, IWarningCallback’i kullanarak yazı tipi ikame uyarılarını yakalamanın tam bir kopyala‑yapıştır örneğini, neden önemli olduğunu ve uyarıları yakaladıktan sonra ne yapmanız gerektiğini adım adım göstereceğiz.

Eğer bir belgeyi açtığınızda özel bir yazı tipi yüklü olmadığı için metnin bozulduğunu gördüyseniz, bu hayal kırıklığını bilir ve anlıyorsunuzdur. Bu öğreticinin sonunda, bu sorunları programatik olarak ortaya çıkaran, kaydeden ya da otomatik olarak bir yedek yazı tipi uygulayan güvenilir bir yönteme sahip olacaksınız.

## Öğrenecekleriniz

- **IWarningCallback**’in amacı ve ne zaman kullanılacağı.  
- **eksik yazı tiplerini algıla** olaylarını izole eden özel bir uyarı toplayıcısının nasıl uygulanacağı.  
- Toplayıcıyı **LoadOptions** içine nasıl bağlayacağınız, böylece her belge yüklemesi izlenir.  
- Çıktıyı doğrulama ve kenar durumlarını (birden fazla eksik yazı tipi, sessiz uyarılar vb.) ele alma.  

### Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.6+ üzerinde de çalışır).  
- NuGet üzerinden Aspose.Words for .NET kurulumu (`Install-Package Aspose.Words`).  
- Makinede bulunmayan bir yazı tipine referans veren bir DOCX dosyası (ör. `DocumentWithMissingFont.docx`).  

Ek bir kütüphane gerekmez—her şey Aspose.Words içinde yer alır.

---

## Aspose.Words’te Eksik Yazı Tiplerini Algılamak İçin IWarningCallback Nasıl Kullanılır

Aşağıda **tam, çalıştırılabilir program** yer alıyor. Yeni bir konsol projesine kopyalayın, dosya yolunu ayarlayın ve çalıştırın. Her eksik‑yazı‑tipi uyarısı için konsolda bir çıktı göreceksiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Beklenen Çıktı

`DocumentWithMissingFont.docx` dosyası, yüklü olmayan *“MyFancyFont”* adlı bir yazı tipine referans veriyorsa, aşağıdaki gibi bir çıktı alırsınız:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

**[Missing Font]** ile başlayan her satır, **IWarningCallback** uygulamamız tarafından üretilir ve **eksik yazı tiplerini algılayabildiğimizi** kanıtlar.

---

## Adım 1: IWarningCallback Arayüzünü Uygulayın

Neden özel bir sınıfa ihtiyacımız var? Aspose.Words, dosya formatı sorunları, kullanımdan kalkmış özellikler ve bizim için en önemlisi yazı tipi ikamesi gibi çeşitli nedenlerle **uyarılar** üretir. `IWarningCallback`’i uygulayarak, her uyarıyı gerçekleştiği anda yakalayan bir kanca elde ederiz. `WarningType.FontSubstitution` kontrolü, bir yazı tipinin eksik olduğu özel senaryoyu izole eder.

**İpucu:** Tanı amaçlı **tüm** uyarıları yakalamak isterseniz, `if` kontrolünü kaldırıp `info.Type` değerini her seferinde kaydedebilirsiniz.

---

## Adım 2: Callback’i LoadOptions’a Bağlayın

`LoadOptions`, Aspose.Words’e gelen belgeyi nasıl işleyeceğini söyleyen kapıdır. `WarningCallback` özelliğini toplayıcı örneğimizle ayarladığınızda, callback tüm yükleme işlemi boyunca aktif olur. Aynı `LoadOptions` nesnesini birden fazla belge için yeniden kullanabilirsiniz; bu, toplu işleme hatlarında oldukça kullanışlıdır.

**Sık sorulan soru:** *LoadOptions belirtmeden bir belge yüklerseniz ne olur?*  
Cevap: Aspose.Words hâlâ dahili olarak uyarılar üretir, ancak bir callback tanımlı olmadığından bu uyarılar sessizce yok sayılır ve **eksik yazı tiplerini algılamak** şansını kaybedersiniz.

---

## Adım 3: Bir Belgeyi Yükleyin ve Eksik Yazı Tipi Uyarılarını Yakalayın

Dosya yolunu ve `LoadOptions`’ı alan `Document` yapıcısı, işi halleder. Dosya ayrıştırılırken, eksik bir yazı tipi `FontWarningCollector.Warning` metodumuzu tetikler. Konsol çıktısı, mekanizmanın çalıştığını kanıtlar.

**Kenar durumu:** Tek bir belge birden fazla eksik yazı tipine referans verebilir. Callback, her eksik yazı tipi için bir kez çalışır; bu yüzden birden fazla satır görürsünüz—tam kapsamlı bir rapor oluşturmak için idealdir.

---

## Neden IWarningCallback Kullanmalı, Manuel Yazı Tipi Kontrolleri Yerine?

Belge yüklendikten sonra `Run.Font` özelliklerini manuel olarak tarayabilirsiniz, ancak bu, belgenin tamamen yüklenebilmesini gerektirir—yazı tipi hiç yoksa yükleme başarısız olur. Uyarı sistemi, herhangi bir ikame gerçekleşmeden **önce** çalışır ve neyin eksik olduğuna dair gerçek bir tablo sunar.

Ayrıca, callback **yükleme boru hattının bir parçası** olarak çalıştığından, erken çıkış yapabilir, anlık olarak yazı tiplerini değiştirebilir veya belge ağacına ekstra bir geçiş yapmadan ayrıntılı tanı bilgileri kaydedebilirsiniz.

---

## Birden Fazla Eksik Yazı Tipini Zarifçe Ele Alma

Çok sayıda eksik yazı tipi bekliyorsanız, bunları bir koleksiyonda biriktirmeyi düşünün:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Yükleme tamamlandıktan sonra `MissingFonts` koleksiyonunu döngüyle gezebilir ve örneğin tasarım ekibi için bir CSV dosyasına yazabilirsiniz.

---

## Bonus: Uyarıları Bir Dosyaya Kaydetme

Konsol çıktısı demo amaçlı iyidir, ancak üretim kodunda genellikle kalıcı bir depoya loglanır. `Console.WriteLine` çağrısını aşağıdaki gibi bir şeyle değiştirin:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Artık daha sonra incelenebilecek bir denetim izi oluşturmuş olursunuz; bu da uyumluluk gereksinimlerini karşılar.

---

## Sonuç

**IWarningCallback**’i **eksik yazı tiplerini algılamak** için nasıl kullanacağınızı, callback’i uygulamaktan `LoadOptions` içine bağlamaya ve ortaya çıkan uyarıları yönetmeye kadar ele aldık. Bu yaklaşım, yazı tipiyle ilgili sorunlara gerçek zamanlı içgörü sağlar; böylece belge render edilmeden önce loglayabilir, değiştirebilir veya kullanıcıları uyarabilirsiniz.

İleride keşfedebileceğiniz adımlar:

- **Yedek yazı tipleri:** ikame gerçekleştiğinde programatik olarak varsayılan bir yazı tipi atayın.  
- **Toplu işleme:** bir klasördeki belgeler üzerinde döngü kurun, aynı `AggregatingFontCollector` nesnesini yeniden kullanın.  
- **Kullanıcı geri bildirimi:** konsol yerine bir UI’da eksik‑yazı‑tipi uyarılarını gösterin.

Kendi projenizde deneyin—artık gizemli bozuk metinler yok, sadece net ve eyleme dönüştürülebilir tanılar. İyi kodlamalar!


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}