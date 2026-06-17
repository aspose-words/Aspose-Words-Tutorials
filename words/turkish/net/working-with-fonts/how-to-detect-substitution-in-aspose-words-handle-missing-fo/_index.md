---
category: general
date: 2026-04-24
description: C# kullanarak Aspose.Words'ta eksik yazı tiplerinin yerine geçişini nasıl
  tespit edebileceğinizi gösterir. Bu kılavuz, FontSettings uyarılarıyla eksik yazı
  tiplerini güvenilir bir şekilde nasıl ele alacağınızı anlatır.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: tr
og_description: C# ile Aspose.Words’ta eksik yazı tiplerinin yerine geçişini nasıl
  tespit edebileceğinizi öğrenin. FontSettings uyarılarını kullanarak eksik yazı tiplerini
  nasıl yöneteceğinizi keşfedin.
og_title: Aspose.Words'te Değiştirmeyi Nasıl Tespit Edersiniz – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Aspose.Words'ta Değiştirmeyi Nasıl Algılayabilirsiniz – Eksik Yazı Tiplerini
  Ele Alın
url: /tr/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Değiştirmeyi Algılamak – Eksik Yazı Tiplerini Yönetme

Sunucunuzda yüklü olmayan bir yazı tipi kullanmaya çalışan bir belgeyle karşılaştığınızda **değiştirmeyi nasıl algılayacağınızı** hiç merak ettiniz mi? Bu, özellikle otomatik bir pipeline'da PDF veya Word dosyaları oluştururken yaygın bir sorun. İyi haber şu ki Aspose.Words bu durumu tespit etmeniz için yerleşik bir kanca sunar ve ayrıca **eksik yazı tiplerini** sorunsuz bir şekilde **yönetebilirsiniz**.

Bu öğreticide, `FontSettings.Warning` olayı aracılığıyla **değiştirmeyi nasıl algılayacağınızı** gösteren gerçek bir örnek üzerinden ilerleyeceğiz ve **eksik yazı tiplerini** iş akışınızı bozmadan nasıl yöneteceğinizi açıklayacağız. Sonuna geldiğinizde, çalıştırmaya hazır bir kod parçacığına, her satırın neden önemli olduğuna dair net bir anlayışa ve tipik tuzaklardan kaçınmak için birkaç ipucuya sahip olacaksınız.

## Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework'te de çalışır)
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`) – 23.11 veya daha yeni sürüm
- Yüklü olmayan bir yazı tipine referans veren örnek bir belge (ör. `MissingFont.docx`)
- Visual Studio, VS Code veya tercih ettiğiniz herhangi bir C# IDE

NuGet paketini eklemenin ötesinde ekstra bir yapılandırma gerekmez.

---

## FontSettings ile Değiştirmeyi Algılamak

**Değiştirmeyi nasıl algılayacağınız**ın temeli `FontSettings.Warning` olayında yatar. Aspose.Words istenen bir yazı tipini bulamadığında `WarningType.FontSubstitution` uyarısı oluşturur. Bu olaya abone olarak, gerçek zamanlı bir bildirim alırsınız; bildirim orijinal yazı tipi adı ve yedek olarak kullanılan yazı tipini içerir.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Neden bu çalışır:**  
- `LoadOptions.FontSettings`, Aspose.Words'e az önce oluşturduğunuz `FontSettings` nesnesini kullanmasını söyler.  
- `Warning` olayına abone olmak, eksik yazı tipleriyle sınırlı kalmayıp *tüm* yazı tipiyle ilgili sorunları tek bir yerde izlemenizi sağlar.  
- `WarningType.FontSubstitution` filtresi, yalnızca ilgilendiğiniz tam senaryoya yanıt vermenizi garantiler – **değiştirmeyi nasıl algılayacağınız**ın özü.

### Beklenen Çıktı

Yukarıdaki kodu, var olmayan bir yazı tipine referans veren bir belgeyle çalıştırdığınızda aşağıdakine benzer bir çıktı verir:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Belge yalnızca yüklü yazı tiplerini kullanıyorsa, konsol sessiz kalır – **değiştirmeyi nasıl algılayacağınız**ın yanlış alarm vermeden başarılı olduğunun net bir göstergesidir.

---

## Eksik Yazı Tiplerini Sorunsuz Bir Şekilde Yönetmek

Değiştirmeyi tespit etmek sadece mücadelenin yarısıdır; ayrıca son çıktının istediğiniz gibi görünmesi için **eksik yazı tiplerini** yönetmek üzere bir stratejiye ihtiyacınız var. Aşağıda karıştırıp eşleştirebileceğiniz üç pratik yaklaşım bulabilirsiniz.

### 1. Yedek Yazı Tipi Klasörü Sağlamak

Aspose.Words, ek dizinlerde yazı tiplerini arayabilir. En yaygın yazı tiplerini içeren bir klasöre yönlendirerek, değiştirme ihtimalini tamamen azaltırsınız.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Neden:** Orijinal yazı tipi eksik olduğunda, Aspose.Words artık bilinen bir alternatif setine sahiptir; bu genellikle daha öngörülebilir bir görsel sonuç verir.

### 2. Eksik Yazı Tiplerini Programlı Olarak Değiştirmek

Tam kontrol istiyorsanız, tespit sonrası eksik yazı tipini belirli bir yazı tipiyle değiştirebilirsiniz.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Neden:** Bu, motorun hangi yazı tiplerini deneyeceğini tam olarak belirtir ve kurumsal marka kimliği ya da erişilebilirlik standartlarını uygulamanıza olanak tanır.

### 3. Günlüğe Kaydet ve İptal Et (Değiştirme Kabul Edilemezse)

Bazen eksik bir yazı tipi, belgenin kullanım senaryonuz için geçersiz olduğu anlamına gelir (ör. yasal formlar). Bu durumda, bir değiştirme gerçekleştiği anda bir istisna fırlatabilirsiniz.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Neden:** Hemen başarısız olmak, hizalanmamış tablolar veya bozuk imzalar gibi sonraki hataları önler.

---

## Tam Çalışan Örnek – Tüm Adımlar Birleştirildi

Aşağıda, **değiştirmeyi nasıl algılayacağınızı** *ve* **eksik yazı tiplerini** yönetmenin çeşitli yollarını gösteren tek bir, kopyala‑yapıştır hazır program bulunmaktadır. İhtiyacınız olmayan bölümleri yorum satırı haline getirmekten çekinmeyin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Ne beklenir:**  
- `MissingFont.docx` makinede bulunmayan bir yazı tipine referans veriyorsa, konsol değiştirme uyarısını yazdırır.  
- Kaydedilen `Processed.docx`, yapılandırdığınız yedek yazı tipini (veya kütüphanenin varsayılanını) kullanır.  
- Değiştirme üzerine kasıtlı olarak iptal etmediğiniz sürece işlenmemiş bir istisna ortaya çıkmaz.

---

## Yaygın Sorular ve Kenar Durumları

| Soru | Cevap |
|----------|--------|
| *Belge birçok eksik yazı tipi içerirse ne olur?* | Uyarı olayı **her** değiştirme için tetiklenir, bu yüzden birden fazla satır görürsünüz. Bunları bir özet raporu için bir listeye toplayabilirsiniz. |
| *PDF dönüşümüyle çalışır mı?* | Kesinlikle. `doc.Save("out.pdf")` çağrısı yapıldığında aynı `FontSettings` uygulanır. Değiştirme uyarısı hâlâ tetiklenir ve PDF'nin görsel bütünlüğünü doğrulamanızı sağlar. |
| *Belge zaten yüklendikten sonra değiştirmeyi tespit edebilir miyim?* | Doğrudan mümkün değil. Uyarı **yükleme** veya **kaydetme** sırasında oluşturulur. Yükleme sonrası analiz gerekiyorsa, uyarıları yükleme aşamasında bir koleksiyona yakalayabilirsiniz. |
| *DOCX içinde gömülü özel yazı tipleri ne olur?* | Gömülü yazı tipleri mevcut kabul edilir, bu yüzden değiştirme gerçekleşmez. Gömülü yazı tipi bozuksa, Aspose.Words yine bir uyarı oluşturur; bunu aynı şekilde yakalayabilirsiniz. |
| *Performans etkisi var mı?* | Minimum. Uyarı kontrolü hafiftir; asıl maliyet belgenin kendisinin yüklenmesidir. Bir yazı tipi klasörü eklemek arama süresini biraz artırabilir, ancak sadece ilk yüklemede. |

---

## Profesyonel İpuçları ve Kaçınılması Gereken Tuzaklar

- **İpucu:** Çok sayıda yazı tipi içeren bir klasöre işaret ederken her zaman `recursive: true` ayarlayın; aksi takdirde alt klasörler göz ardı edilir.  
- **Dikkat edin:** Linux'ta büyük/küçük harf duyarlılığı. Yazı tipi adları Windows'ta büyük/küçük harfe duyarsızdır ancak Linux'ta değildir; bu yüzden tam adı kullanın ya da her iki varyantı da ekleyin.  
- **Unutmayın:** Eğer konteyner tabanlı bir ortamda çalışıyorsanız, yazı tipi klasörünün imajın bir parçası olduğundan ya da çalışma zamanında bağlandığından emin olun.  
- **İpucu:** Uyarıları `List<string>` içinde saklayın; böylece son kullanıcıya bir özet sunabilir veya bir izleme sistemine kaydedebilirsiniz.  

## Sonuç

Aspose.Words'ta eksik yazı tiplerinin **değiştirmeyi nasıl algılayacağınızı** ele aldık, **eksik yazı tiplerini** yönetmenin çeşitli yollarını gösterdik ve herhangi bir .NET projesine ekleyebileceğiniz tam, çalıştırılabilir bir örnek sunduk. `FontSettings.Warning` olayına bağlanarak yazı tipi sorunlarını gerçek zamanlı görebilir ve yedek klasörler ya da açık değiştirme kurallarıyla çıktınızın tam istediğiniz gibi görünmesini sağlayabilirsiniz.

Bir sonraki adıma hazır mısınız? Çözümü, oluşturulan PDF'ye yedek yazı tipini otomatik olarak gömmek için genişletmeyi ya da uyarı işleyicisini büyük ölçekli belge pipeline'ları için merkezi bir günlük hizmetine bağlamayı deneyin. Bugün tartıştığımız desenler—olay‑tabanlı algılama, sorunsuz yedekleme ve açık hata yönetimi—diğer birçok Aspose API'sine de uygulanabilir; böylece artık tüm platformlarda yazı tipiyle ilgili zorlukları çözmeye hazırsınız.

Yazı tipi yönetimi, PDF dönüşümü veya Aspose.Words ipuçları hakkında daha fazla sorunuz mu var? Aşağıya bir yorum bırakın, iyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}