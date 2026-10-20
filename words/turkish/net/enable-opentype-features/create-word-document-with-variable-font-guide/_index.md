---
category: general
date: 2026-03-19
description: Aspose.Words ve değişken bir yazı tipi kullanarak Word belgesi oluşturun.
  C#'ta yazı tipi kalınlığını nasıl değiştireceğinizi, yazı tipi genişliğini nasıl
  ayarlayacağınızı ve yazı tipi varyasyonunu nasıl tanımlayacağınızı öğrenin.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: tr
og_description: Aspose.Words kullanarak değişken bir yazı tipiyle Word belgesi oluşturun.
  Bu öğreticide, yazı tipini nasıl yükleyeceğinizi, yazı tipi kalınlığını nasıl değiştireceğinizi,
  yazı tipi genişliğini nasıl ayarlayacağınızı ve yazı tipi varyasyonunu nasıl tanımlayacağınızı
  gösterir.
og_title: Değişken Yazı Tipiyle Word Belgesi Oluşturma – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Variable Font
title: Değişken Yazı Tipiyle Word Belgesi Oluşturma – Rehber
url: /tr/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Değişken Yazı Tipi ile Word Belgesi Oluşturma – Kılavuz

Modern bir değişken yazı tipi kullanan bir **word document** oluşturmanız gerektiğinde, nereden başlayacağınızı bilemediğiniz oldu mu? Tek başınıza değilsiniz. Dinamik raporlar ya da marka‑tutarlı broşürler gibi birçok projede, **change font weight** özelliğini anlık olarak kullanabilmek gerçek bir oyun‑değiştirici.  

Bu öğreticide, süreci baştan sona ele alacağız: Aspose.Words’e bir değişken yazı tipi yüklemek, ağırlığını ve genişliğini ayarlamak ve sonunda tasarladığınız gibi görünen bir DOCX dosyası kaydetmek. Belirsiz referanslar yok, sadece C# projenize hemen ekleyebileceğiniz somut kodlar.

## Neler Öğreneceksiniz

- `FontSettings` kullanarak Aspose.Words’e **load variable font** dosyalarını nasıl yüklersiniz.
- `wght` (ağırlık) ve `wdth` (genişlik) gibi **define font variation** eksenlerinin sözdizimi.
- Tek bir `Run` üzerinde **set font width** ve **change font weight** nasıl yapılır.
- Yaygın sorunların (eksik glifler, hatalı klasör yolları vb.) giderilmesi için ipuçları.
- Anında kopyalayıp çalıştırabileceğiniz eksiksiz bir örnek.

> **Prerequisites**: .NET 6+ (veya .NET Framework 4.6+), NuGet üzerinden kurulu Aspose.Words for .NET ve yerel bir *Fonts* klasörüne yerleştirilmiş *RobotoFlex.ttf* gibi bir değişken‑yazı‑tipi dosyası.

---

## Step 1 – Load the Variable Font into Aspose.Words

İlk olarak, Aspose.Words’e özel yazı tiplerimizin nerede olduğunu söylememiz gerekiyor. Bu işi `FontSettings` sınıfı yapıyor.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Why this matters**: Klasör kaydedilmezse, Aspose.Words sistem yazı tiplerine geri döner ve daha sonra uygulamaya çalıştığınız OpenType varyasyon verilerini görmezden gelir. Belirli bir dizine işaret ederek *RobotoFlex* (veya başka bir değişken yazı tipi) kod her çalıştığında bulunur.

> **Pro tip**: `SetFontsFolder` metodunun ikinci parametresini `true` yaparsanız Aspose alt‑klasörleri de arar. Bu, yazı tiplerini stil ya da ağırlığa göre düzenlediğinizde işe yarar.

---

## Step 2 – Create a New Document and Add Sample Text

Yazı tipi motoru nerede arayacağını bildiğine göre, boş bir `Document` oluşturup bir `Run` içeren bir paragraf ekliyoruz.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**What’s happening**: `Run`, tek tip biçimlendirmeye sahip kesintisiz bir metin parçasını temsil eder. Önce onu oluşturmak, biçimlendirme mantığını izole eder—daha sonra farklı varyasyon eksenlerini ayrı ayrı `Run`’lara uygulamak istediğinizde mükemmeldir.

---

## Step 3 – Define the Desired Variation Axes (Weight & Width)

Değişken yazı tipleri, çalışma zamanında ayarlayabileceğiniz *eksler* sunar. En yaygın iki eksen `wght` (yazı tipi ağırlığı) ve `wdth` (yazı tipi genişliği) dir. Aspose.Words bunu `OpenTypeFontVariation` koleksiyonu ile modeller.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Why these numbers**: OpenType spesifikasyonunda, `wght` minimumdan maksimuma (genellikle 100–900) kadar bir aralıkta olur. **700** değeri kalın bir görünüme karşılık gelir. `wdth` de benzer çalışır; **100** varsayılan (normal) genişliktir, 100’ün altındaki değerler glifleri sıkıştırır.

> **Edge case**: Bazı değişken yazı tipleri belirli bir ekseni desteklemez. Desteklenmeyen bir etiket verirseniz Aspose sessizce yok sayar. Yazı tipinin spesifikasyonunu (genellikle `.ttf` ya da `.otf` dosyasının meta verilerinde) mutlaka kontrol edin.

---

## Step 4 – Apply the Variation to the Run Using the Font Name

Şimdi varyasyon verilerini gerçek metne bağlayacağız. `FontInfo` sınıfı, yazı tipi ailesi adını ve eksen koleksiyonunu tutar.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explanation**: `FontInfo` ayarlanarak, normal `Font.Name` özelliğini atlayıp motoru tam nitelikli bir yazı tipi yapılandırmasıyla besleriz. Bu, Aspose.Words’e özel eksenlerle bir değişken yazı tipi kullanmasını söylemenin tek yoludur.

> **Common mistake**: Yazı tipi dosyasındaki tam aile adını (`RobotoFlex` bu örnekte) eşleştirmeyi unutmak. Küçük bir yazım hatası Aspose’un varsayılan bir yazı tipine geri dönmesine ve varyasyonunuzun kaybolmasına neden olur.

---

## Step 5 – Save the Document and Verify the Result

Son olarak belgeyi diske yazdırıyoruz. Oluşturulan DOCX, değişken‑yazı‑tipi talimatlarını içerir; Microsoft Word (2016+) bu talimatları doğru şekilde render eder.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Dosyayı Word’de açın, metni seçin ve **Font** iletişim kutusuna bakın. *Roboto Flex* listelenmiş olmalı ve metin, `wght = 700` ayarımız sayesinde çevresindeki içerikten daha kalın görünecektir.

> **Verification tip**: Metin değişmemiş gibi görünüyorsa, yazı tipi dosyasının gerçekten `wght` eksenini desteklediğini kontrol edin. Bazı “değişken” yazı tipleri sadece `ital` (italik) ya da `opsz` (optik boyut) sunar.

---

## Optional: Add More Variation – Changing Width Dynamically

Başka bir paragraf için **set font width** değerini farklı bir şekilde ayarlamak isterseniz, adım 3‑4’ü yeni bir `OpenTypeFontVariation` koleksiyonu ile tekrarlayın.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Şimdi iki `Run`’unuz var—biri kalın, diğeri biraz daha geniş—ve aynı belgede **change font weight** ve **set font width** işlemlerini göstermiş olduk.

---

## Full Working Example

Aşağıdaki kod parçacığını yeni bir console uygulamasına (`Program.cs`) kopyalayıp çalıştırın. `Fonts` klasörünün içinde `RobotoFlex.ttf` (veya tercih ettiğiniz başka bir değişken yazı tipi) bulunduğundan emin olun.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Expected output**: `VariableFont.docx` adlı bir dosya oluşur; “Variable‑weight text” ifadesi `wght = 700` ekseni sayesinde kalın görünür, genişlik ise varsayılan kalır.

---

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| *What if the font isn’t found?* | Verify the folder path, ensure the file name matches, and that the process has read permissions. You can also call `fontSettings.GetFonts()` to list detected fonts. |
| *Can I combine multiple runs with different variations?* | Absolutely. Each `Run` can carry its own `FontInfo`. Just repeat steps 3‑4 for each run. |
| *Do older versions of Word support variable fonts?* | Word 2016 (Build 16.0.8001) introduced basic support. If you target older versions, the document will fall back to the nearest static instance of the font. |
| *Is there a limit to how many axes I can set?* | You can set any number the font defines. Common tags are `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Supplying an unsupported tag simply has no effect. |
| *How do I debug missing glyphs?* | Use `FontSettings.GetFontSources()` to inspect loaded fonts, and `FontInfo.HasGlyph(char)` to test individual characters. |

---

## Conclusion

Birkaç adımda **how to create word document** dosyalarının değişken yazı tiplerinin gücünden yararlanarak **change font weight**, **set font width**, **load variable font** dosyalarını ve **define font variation** eksenlerini Aspose.Words for .NET ile nasıl kullanacağınızı gösterdik.  

Temel fikir basit: yazı tipi klasörünü kaydedin, istediğiniz eksenleri tanımlayın, bir `Run`’a ekleyin ve kaydedin. Bundan sonra aynı tekniği bütün bölümler, tablolar ya da hatta marka‑özel raporlar üretmek için genişletebilirsiniz.

**Next steps**: `RobotoFlex` yerine başka bir değişken yazı tipi deneyin, `ital` (italik) ekseniyle oynayın ya da aynı belgeyi Aspose.PDF ile PDF olarak üretin. Aynı desen geçerli—yükle, tanımla, uygula, kaydet.

Happy coding, and enjoy the flexibility that variable fonts bring to your Word automation projects!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}