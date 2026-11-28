---
category: general
date: 2026-06-02
description: C#'ta değişken ağırlıklı fontu nasıl kullanacağınızı öğrenin ve dinamik
  tipografi için font genişletme kodunu değiştirirken font ağırlığını programlı olarak
  ayarlayın.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: tr
og_description: C#'ta değişken ağırlıklı yazı tipini kullanarak yazı tipi ağırlığını
  programlı olarak ayarlayın ve yazı tipi genişletme kodunu değiştirin, belgelerinizde
  dinamik tipografi sağlayın.
og_title: C#'de Değişken Ağırlıklı Yazı Tipi Kullanımı – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: C#'ta Değişken Ağırlıklı Yazı Tipi Kullanımı – Tam Programlama Rehberi
url: /tr/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'de Değişken Ağırlıklı Yazı Tipi Kullanımı – Tam Programlama Kılavuzu

Hiç .NET projesinde **değişken ağırlıklı yazı tipi** kullanmanız gerekti ama ağırlık ve stretch'in kullanıcı girdisine nasıl yanıt vereceğinden emin olmadınız mı? Yalnız değilsiniz. Birçok UI veya raporlama senaryosunda metnin uyum sağlamasını istersiniz—belki üzerine gelindiğinde kalınlaşan hafif bir başlık ya da vurgulamak için genişliği artan bir paragraf. İyi haber şu ki, Aspose.Words ile **yazı tipi ağırlığını programmatically (programatik olarak) ayarlayabilir** ve hatta **yazı tipi stretch kodunu** anında değiştirebilirsiniz.

Bu öğreticide, değişken ağırlıklı bir yazı tipini nasıl yükleyeceğinizi, özel bir ağırlık uygulayacağınızı ve stretch ayarını nasıl ince ayar yapacağınızı adım adım gösteren bir örnek üzerinden ilerleyeceğiz—hepsi kopyalayıp yapıştırabileceğiniz net C# kodlarıyla. Sonunda, bu etkiyi gösteren bir PDF üreten çalıştırılabilir bir konsol uygulamanız olacak.

---

## İhtiyacınız Olanlar

- **Aspose.Words for .NET** (v23.12 veya daha yeni). Kütüphane, değişken ağırlıklı yazı tipleri için tam destekle birlikte gelir.
- En az bir değişken ağırlıklı yazı tipi dosyası içeren bir klasör, ör. *RobotoFlex‑Variable.ttf*. Google Fonts'tan indirebilirsiniz.
- .NET 6 SDK (veya herhangi bir yeni .NET sürümü) ve tercih ettiğiniz bir IDE.
- Temel C# bilgisi—fantezi bir şey değil, sadece birkaç satır kod.

Hepsi bu. Aspose.Words dışındaki ekstra NuGet paketlerine gerek yok ve gizli yapılandırma dosyaları da yok.

![Değişken ağırlıklı yazı tipi örneği](https://example.com/variable-weight-sample.png "Değişken ağırlıklı yazı tipi gösterimi")

*Alt metin: oluşturulan bir PDF belgesinde değişken ağırlıklı yazı tipinin kullanıldığını gösteren ekran görüntüsü.*

## Adım 1: FontSettings'i Ayarlayın ve Yazı Tipi Klasörünüzü Belirtin  

İlk olarak—Aspose.Words'in değişken ağırlıklı yazı tiplerinizin nerede olduğunu bilmesi gerekir. Bunu bir `FontSettings` nesnesi oluşturarak ve bir `FolderFontSource` ekleyerek yaparsınız. `true` bayrağı, motorun alt klasörleri de aramasını sağlar; bu, birden fazla yazı tipi ailesini aynı anda tutuyorsanız kullanışlıdır.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Neden önemli:** Klasörü kaydetmeden, Aspose.Words sistem yazı tiplerine geri döner ve özel yazı tipi dosyanızda gömülü değişken ağırlık verilerini görmez. Bu adım, sonrasında gelen her şeyin temeli.

## Adım 2: FontSettings'i Belgeye Bağlayın  

Şimdi yeni bir `Document` (veya mevcut bir belgeyi) oluşturup, az önce hazırladığımız `FontSettings`'i kullanmasını söylüyoruz. Bu bağlama, daha sonra ekleyeceğimiz her `Run` için değişken‑ağırlıklı verilerin kullanılabilir olmasını sağlar.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Eğer zaten bir şablonunuz varsa—örneğin yer tutucular içeren bir Word dosyası—`new Document()` ifadesini `new Document("Template.docx")` ile değiştirebilirsiniz. Aynı `FontSettings` uygulanacaktır.

## Adım 3: Değişken‑Ağırlıklı Yazı Tipini Kullanacak Bir Run Metni Ekleyin  

**Run**, Aspose.Words'te metin biçimlendirmesinin en küçük birimidir. Bir tane oluşturacağız, yeni bir paragraf içine ekleyeceğiz ve daha sonra yazı tipi özelliklerini değiştireceğiz.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Bu noktada metin, varsayılan yazı tipi (genellikle Times New Roman) ile görüntülenecek. Gerçek sihir, değişken‑ağırlıklı aileyi atadığımızda gerçekleşir.

## Adım 4: Değişken‑Ağırlıklı Yazı Tipi Ailesini Seçin  

İşte **değişken ağırlıklı yazı tipini** gerçekten kullandığımız yer. `Font.Name` özelliğini, değişken yazı tipi dosyasında tanımlı tam aile adıyla ayarlayın. Roboto Flex için ad `"Roboto Flex"`'tir.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Aile adından emin değilseniz, `.ttf` dosyasını bir yazı tipi görüntüleyicide açın veya mevcut aileleri listelemek için `fontSettings.GetFonts()` metodunu kullanın.

## Adım 5: Yazı Tipi Ağırlığını ve Stretch'i Programatik Olarak Ayarlayın  

Şimdi öğreticinin özü: **yazı tipi ağırlığını programatik olarak ayarlıyoruz** ve **yazı tipi stretch kodunu değiştiriyoruz**. Her iki özellik de OpenType spesifikasyonuna karşılık gelen tam sayı değerlerini kabul eder.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Değişken yazı tipinin desteklediği herhangi bir değeri seçin.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Varsayılan 100 (Normal).

> **Pro ipucu:** Her değişken yazı tipi tam aralığı sunmaz. Desteklenmeyen bir değer ayarlarsanız, motor en yakın mevcut ağırlık veya stretch değerine yuvarlar.

## Adım 6: Belgeyi Kaydedin ve Sonucu Doğrulayın  

Son olarak, belgeyi PDF (veya DOCX) olarak kaydedin ve etkisini görmek için açın. PDF, görsel doğrulama için harika bir formattır çünkü renderlama platformlar arasında tutarlıdır.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

*VariableWeightDemo.pdf* dosyasını açtığınızda, “Variable‑weight text demo” ifadesinin Roboto Flex'in hafif, hafifçe genişletilmiş bir versiyonunda renderlandığını görmelisiniz. `FontWeight`'i `700` ve `FontStretch`'i `80` olarak değiştirip yeniden çalıştırın—metnin kalınlaştığını ve daha sıkıştığını izleyin.

## Yaygın Sorular & Kenar Durumları  

### Yazı tipi hiç görünmüyorsa ne olur?

- **Missing FontSettings**: `doc.FontSettings = fontSettings;` ifadesinin **herhangi bir metin eklenmeden önce** çalıştırıldığını iki kez kontrol edin.
- **Incorrect family name**: Tüm bulunan aileleri listelemek için `fontSettings.GetFonts()` kullanın; tam dizeyi kopyalayın.
- **Unsupported weight/stretch**: Bazı değişken yazı tipleri sadece 100‑900 ağırlık aralığının bir alt kümesini destekler. Güvenli bir geri dönüş olarak `run.Font.FontWeight = 400;` kullanın.

### Belge kaydedildikten sonra ağırlığı değiştirebilir miyim?

Evet. `Run` nesnesi değiştirilebilir, bu yüzden son `Save` işleminden önce istediğiniz zaman `FontWeight` veya `FontStretch` değerlerini ayarlayabilirsiniz. Ağırlıkları dinamik olarak (ör. kullanıcı etkileşimine göre) değiştirmek isterseniz, her durum için ayrı run'lar oluşturmayı düşünün.

### Bu DOCX çıktısı ile çalışır mı?

Kesinlikle. Değişken‑ağırlıklı meta veri, temel OpenXML içinde saklanır ve modern Word sürümleri bunu yorumlayabilir. Ancak, eski Word sürümleri stretch ayarını görmezden gelebilir.

## Tam Çalışan Örnek  

Aşağıda, anında derleyip çalıştırabileceğiniz tam bir konsol programı bulunmaktadır. Gerekli tüm `using` yönergeleri, hata yönetimi ve yorumlar içerir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Beklenen çıktı:** Konsol, kaydetme yolunu yazdırır ve oluşturulan PDF, metni hafif, genişletilmiş bir stilde gösterir—tam olarak yapılandırdığımız gibi.

## Özet  

Aspose.Words ile C#'de **değişken ağırlıklı yazı tipini nasıl kullanacağınızı**, **yazı tipi ağırlığını programatik olarak nasıl ayarlayacağınızı** ve glifleri genişletmek veya sıkıştırmak için gereken tam **yazı tipi stretch kodunu değiştirmeyi** ele aldık. Adımlar basittir: `FontSettings`'i yapılandırın, bir `Document`'e ekleyin, bir `Run` oluşturun, değişken‑ağırlıklı aileyi seçin ve son olarak `FontWeight` ve `FontStretch` değerlerini ayarlayın.

## Sıradaki Adımlar  

- **Dinamik UI entegrasyonu**: Aynı mantığı bir WinForms veya WPF uygulamasına bağlayarak kullanıcıların kaydırıcılarla ağırlık/stretch seçmesine izin verin.
- **Birden fazla run**: Aynı paragrafta farklı ağırlıklara sahip birkaç run'ı birleştirerek zengin tipografik hiyerarşiler oluşturun.
- **Gelişmiş eksenler**: Bazı değişken yazı tipleri ek eksenler (ör. eğim, optik boyut) sunar. Daha ince kontrol için `run.Font.FontStyle` kullanın veya `FontVariationSettings`'i keşfedin.
- **Performans ipuçları**: Çok sayıda belge işlerken `FontSettings` örneğini önbelleğe alarak klasör taramalarını tekrarlamaktan kaçının.

Denemekten çekinmeyin—*Roboto Flex* yerine *Inter Variable* ya da başka bir OpenType değişken yazı tipini kullanın ve belgelerinizin yeni bir görsel esneklik seviyesine kavuşmasını izleyin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Hedef Makineden Yazı Tipi Kullan](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Hedef Makineden Yazı Tipi Kullan](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Hedef Makineden Yazı Tipi Kullan](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}