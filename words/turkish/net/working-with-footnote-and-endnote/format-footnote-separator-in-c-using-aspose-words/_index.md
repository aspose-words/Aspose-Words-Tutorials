---
category: general
date: 2026-08-10
description: Aspose.Words ile C#'ta dipnot ayırıcıyı biçimlendirerek dipnot ve sonnot
  satırlarını özelleştirin. C# dipnot biçimlendirmesini dakikalar içinde öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: tr
lastmod: 2026-08-10
og_description: Aspose.Words kullanarak C#'de dipnot ayırıcıyı biçimlendirin. Dipnot
  ve sonnot ayırıcılarını hızlı ve güvenilir bir şekilde biçimlendirmek için bu öğreticiyi
  izleyin.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: C#'ta dipnot ayırıcı biçimlendirme – eksiksiz Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: C#'de Aspose.Words kullanarak dipnot ayırıcıyı biçimlendir
url: /tr/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words kullanarak dipnot ayırıcı biçimlendirme

Bir Word belgesinde **dipnot ayırıcıyı biçimlendirmek** istiyorsanız, bu kılavuz Aspose.Words for .NET ile nasıl yapılacağını gösterir. Hizalanma ve ayırıcı paragrafın rengini değiştiren tam, çalıştırılabilir bir örnek göreceksiniz ve aynı tekniği sonnot ayırıcılarına nasıl uygulayacağınızı öğreneceksiniz.

Bu öğretici, kaynak dosyanın yüklenmesinden değiştirilmiş belgenin kaydedilmesine kadar her adımı kapsar—kodları kendi projenize ek araştırma yapmadan kopyalayıp yapıştırabilirsiniz.

## Gereksinimler

* .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır)
* Geçerli bir Aspose.Words for .NET lisansı (ücretsiz deneme değerlendirme için çalışır)
* En az bir dipnot veya sonnot içeren bir Word dosyası (ör. `Footnotes.docx`)
* Visual Studio 2022 veya tercih ettiğiniz herhangi bir C# IDE

Bu öğelere sahip olmak, ortam kurulumundan ziyade **C# dipnot biçimlendirme** mantığına odaklanmanızı sağlar.

## Adım 1: Dipnot ve sonnot içeren belgeyi yükleyin

İlk işlem, kaynak dosyanıza işaret eden bir `Document` nesnesi oluşturmaktır. Aspose.Words, tüm DOCX paketini belleğe okur ve dipnot ve sonnot düğümlerine tam erişim sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Neden önemli*: Belgeyi yüklemek, herhangi bir manipülasyonun ön koşuludur. Dosya yolu yanlışsa, Aspose.Words bir `FileNotFoundException` fırlatır, bu yüzden ilerlemeden önce yolu doğrulayın.

## Adım 2: Ayırıcı ve devam‑ayırıcı düğümlerini alın

Dipnot ve sonnot ayırıcıları, `Footnotes` ve `Endnotes` koleksiyonları içinde özel düğümler olarak depolanır. Her koleksiyon, bir `Node` referansı döndüren `Separator` ve `ContinuationSeparator` özelliklerini sunar.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Neden önemli*: `Separator` düğümü, ana metni dipnot bloğundan görsel olarak ayıran satırı temsil eder. Bir referans elde ederek, paragraf biçimini, yazı tipini değiştirebilir veya düğümü tamamen değiştirebilirsiniz.

## Adım 3: Dipnot ayırıcısının görsel stilini değiştirin

Çoğu Word belgesinde ayırıcı, bir tire veya yıldız işareti içeren tek bir paragraftır. Aşağıdaki kod, ayırıcıların `Paragraph` olup olmadığını kontrol eder ve eğer öyleyse ortalar ve metin rengini griye değiştirir.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Devam ayırıcıyı stilize etme (isteğe bağlı)

Bir dipnot birden fazla sayfaya yayıldığında devam ayırıcı ortaya çıkar. Bunu da benzer şekilde stilize edebilirsiniz:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Neden önemli*: Ayırıcıyı hizalamak okunabilirliği artırır ve rengi değiştirmek onu normal paragraf metninden ayırır. `ParagraphAlignment.Center` ifadesini, belgenizin tasarım yönergelerine uygun olarak `Left` veya `Right` ile değiştirebilirsiniz.

## Adım 4: Değiştirilmiş belgeyi kaydedin

İstenen stili uyguladıktan sonra belgeyi diske geri yazın. Orijinal dosyanın üzerine yazabilir veya yeni bir sürüm oluşturabilirsiniz.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

`Footnotes_Styled.docx` dosyasını Microsoft Word'de açtığınızda, dipnot ayırıcı kodda belirtildiği gibi ortalanmış ve gri olarak görünür.

## İleri düzey varyasyonlar

### Sonnot ayırıcıyı biçimlendirme

Belgeniz aynı zamanda sonnotlar da içeriyorsa, aynı mantığı `Endnotes` koleksiyonuna uygulayabilirsiniz:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Ayırıcı için özel bir dize kullanma

Bazen ayırıcıyı bir dizi yıldız (`***`) olarak istiyorsunuzdur. Mevcut run'ları yeni bir run ile değiştirin:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Ayırıcı düğümü olmayan belgeleri işleme

Nadir bir uç durum, ayırıcı düğümünü içermeyen bir belgedir (ör. yazar silmişse). Bu senaryoda `document.Footnotes.Separator` `null` döner. Buna karşı önlem alın:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Yaygın tuzaklar ve nasıl önlenir

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Ayırıcı bir `Paragraph` değil** | Bazı Word şablonları ayırıcı olarak bir `Table` veya `Shape` kullanır. | `is Paragraph` ile düğüm tipini kontrol edin, ardından dönüştürün. |
| **`Runs` koleksiyonu boş** | Ayırıcı boş bir paragraf olabilir. | `Runs[0]`'a erişmeden önce `Runs.Count > 0` olduğunu doğrulayın. |
| **Lisans uygulanmadı** | Lisans olmadan, Aspose.Words bir filigran ekler ve API kullanımını sınırlayabilir. | Programınızın başında `License license = new License(); license.SetLicense("Aspose.Words.lic");` çağrısını yapın. |
| **Salt okunur bir klasöre kaydetme** | `Save` metodu bir `UnauthorizedAccessException` fırlatır. | Hedef dizinin yazma izni olduğundan emin olun. |

Bu sorunları erken ele almak, çalışma zamanı istisnalarını önler ve sorunsuz bir **dipnot ayırıcıyı değiştirme** deneyimi sağlar.

## Tam, çalıştırılabilir örnek

Aşağıda, yukarıda tartışılan her adımı gösteren bağımsız bir konsol uygulaması bulunmaktadır. Kodu yeni bir .NET konsol projesine kopyalayın, dosya yollarını değiştirin ve çalıştırın.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Beklenen sonuç**  

`Footnotes_Styled.docx` dosyasını açtığınızda:

* Dipnot ayırıcı satırı ana metnin altında ortalanmış olur.
* Rengi açık gri olarak görünür, görsel olarak ayırt edilebilir.
* Belge sonnotlar içeriyorsa, onların ayırıcıları da ortalanmış ve gri (veya slayt

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Dipnot ve Sonnot ile Kelime İşleme](/words/english/net/working-with-footnote-and-endnote/)
- [Dipnot ve Sonnot Konumunu Ayarlama](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Dipnot ve Sonnot ile Çalışma](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}