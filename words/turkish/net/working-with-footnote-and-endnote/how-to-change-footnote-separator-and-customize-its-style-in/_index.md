---
category: general
date: 2026-10-13
description: Aspose.Words kullanarak bir Word belgesindeki dipnot ayırıcıyı nasıl
  değiştireceğiniz. Word belgesinde programlı olarak yazı tipi rengini değiştirmeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: tr
lastmod: 2026-10-13
og_description: Aspose.Words ile bir Word belgesindeki dipnot ayırıcıyı nasıl değiştirirsiniz.
  Bu öğreticide C# kullanarak Word belgesindeki yazı tipi rengini nasıl değiştireceğinizi
  gösteriyoruz.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Word belgesinde dipnot ayırıcıyı nasıl değiştirirsiniz – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Word belgesinde dipnot ayırıcıyı nasıl değiştirir ve stilini özelleştirirsiniz
url: /tr/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesinde dipnot ayırıcıyı nasıl değiştirir ve stilini özelleştirirsiniz

Eğer bir Word belgesinde **dipnot ayırıcıyı nasıl değiştirir** öğrenmek istiyorsanız, bu kılavuz size eksiksiz, hemen çalıştırılabilir bir çözüm sunar. Aspose.Words for .NET kullanarak, dipnot ve sonnot ayırıcıları gibi **Word belgesinde yazı tipi rengini değiştirme** öğelerini de değiştirebilir, son dosyanın marka kimliğinize veya stil rehberinize uymasını sağlayabilirsiniz.

Belge yazarları sık sık sorar: *Neden varsayılan dipnot ayırıcısı sade görünür ve nasıl daha belirgin hâle getirebilirim?* Cevap, ayırıcı paragraf nesnelerine doğrudan erişmek, yazı tipi özelliklerini ayarlamak ve sonucu kaydetmektir. Bu öğretici, .docx dosyasını yüklemekten stilize edilmiş çıktıyı kalıcı hâle getirmeye kadar her adımı size gösterir.

Şunları öğreneceksiniz:

* Zaten dipnot ve sonnot içeren bir Word dosyasını yükleme.  
* Dipnot ve sonnot ayırıcı paragrafını bulma.  
* Her ayırıcıyı (dipnotlar için kırmızı, sonnotlar için mavi) yazı tipi rengini değiştirme.  
* Değiştirilmiş belgeyi mevcut içeriği kaybetmeden kaydetme.

Aspose.Words kütüphanesi ve bir .NET geliştirme ortamı dışındaki hiçbir harici araca ihtiyaç yoktur.

## Prerequisites

* .NET 6.0 SDK veya daha yeni bir sürüm (kod .NET Framework 4.7+ ile de çalışır).  
* Visual Studio 2022, Rider veya tercih ettiğiniz herhangi bir C# editörü.  
* Aspose.Words for .NET NuGet paketi (`Aspose.Words`).  
* En az bir dipnot ve bir sonnot içeren örnek bir Word dosyası (`Footnotes.docx`).

> **Pro tip:** Eğer bir örnek dosyanız yoksa, yeni bir Word belgesi oluşturun, bir dipnot (`References → Insert Footnote`) ve bir sonnot (`References → Insert Endnote`) ekleyin. Dosyayı `Footnotes.docx` olarak, koddan referans verebileceğiniz bir klasöre kaydedin.

## How to change footnote separator with Aspose.Words

Görevin özü, Aspose.Words'ün *separator* düğümleri olarak ortaya koyduğu özel paragrafları almaktır. Bu düğümler `Paragraph` tipindedir ve diğer paragraflar gibi biçimlendirilebilir.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Why each line matters

* **Belgeyi yükleme** (`new Document`) Aspose.Words'ün manipüle edebileceği bellek içi bir temsil oluşturur.  
* **`GetChild` ile `ParagraphNodeType.FootnoteSeparator`** Word'ün dipnotları ana metinden ayırmak için kullandığı gizli paragrafı döndürür. Aynı yöntem sonnot ayırıcı için de çalışır.  
* **`Font.Color` değiştirme** satırın görünümünü doğrudan etkiler çünkü Word ayırıcıyı tek bir “‑” karakteri içeren bir paragraf olarak işler. Rengi `Color.Red` (veya herhangi bir `System.Drawing.Color`) olarak ayarlamak görsel stili günceller.  
* **Kaydetme** değişiklikleri .docx dosyasına yazar; bu dosya herhangi bir Word işlemcisiyle açılabilir.

### Expected output

`FootnoteSeparatorsStyled.docx` dosyasını Microsoft Word'de açtığınızda:

* Dipnot ayırıcı çizgisi **kırmızı** görünecek.  
* Sonnot ayırıcı çizgisi **mavi** görünecek.  

Tüm orijinal dipnot ve sonnot içeriği dokunulmamış kalır.

## Change font color in Word document using C#

Yukarıda gösterilen işlem, daha geniş bir yeteneğin özel bir örneğidir: **Word belgesinde yazı tipi rengini değiştirme** programatik olarak. Bir `Paragraph`, `Run` veya metin içeren herhangi bir `Node` elde ettiğinizde, `Font.Color` özelliğini ayarlayabilirsiniz.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Bu kod parçacığı her paragrafı dolaşır, `Heading 1` stilini kullanıp kullanmadığını kontrol eder ve yazı tipi rengini ayarlar.  
* Koşulu dipnotlar, tablolar veya başka bir düğüm türüne hedefleyecek şekilde uyarlayabilirsiniz.

## Step‑by‑step breakdown

### 1. Install Aspose.Words

Proje klasörünüzde bir terminal açın ve şu komutu çalıştırın:

```bash
dotnet add package Aspose.Words
```

Paket, daha önce gösterilen kod için gerekli tüm derlemeleri içerir.

### 2. Prepare the input file

`Footnotes.docx` dosyasını bilinen bir dizine (ör. `C:\Docs`) yerleştirin. Dosyanın en az bir dipnot ve bir sonnot içerdiğinden emin olun; böylece ayırıcı düğümleri bulunur.

### 3. Write the C# program

Yeni bir konsol projesi oluşturun (`dotnet new console -n FootnoteStyler`) ve oluşturulan `Program.cs` dosyasını **dipnot ayırıcıyı nasıl değiştirir** bölümündeki tam kod bloğuyla değiştirin. Dosya yollarını ortamınıza göre ayarlamayı unutmayın.

### 4. Run and verify

Programı çalıştırın:

```bash
dotnet run
```

Çalışma tamamlandıktan sonra `FootnoteSeparatorsStyled.docx` dosyasını açın. Açıklanan gibi kırmızı ve mavi ayırıcı çizgilerini görmelisiniz.

### 5. Extend the solution

* **Farklı renkler:** `Color.FromArgb(255, 128, 0)` gibi herhangi bir `System.Drawing.Color` değeri kullanın (ör. turuncu).  
* **Özel çizgi stili:** Rengi değiştirmek yerine `ParagraphFormat` özelliklerini (ör. `LineSpacing`, `Shading`) ya da ayırıcı karakterini değiştirebilirsiniz.  
* **Birden çok belge:** Mantığı giriş ve çıkış yollarını parametre olarak alan bir metoda sarın, ardından toplu işleme için döngü içinde çağırın.

## Common pitfalls and how to avoid them

| Belirti | Neden | Çözüm |
|---------|-------|-----|
| `GetChild` `null` döner | Kaynak belgede dipnot/sonnot ayırıcı yok (ör. dipnot yok). | En az bir dipnot veya sonnot ekleyin, ya da `Font` erişmeden önce `null` kontrolü yapın. |
| Renk değişikliği görünmez | Bazı Word sürümlerinde ayırıcı bir karakter yerine çizgi olarak işlenir. | Görünür bir karakter zorlamak için `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` ve `ParagraphFormat.LineSpacing = 1` ayarlayın. |
| Çalışma zamanı `FileNotFoundException` | Yanlış dosya yolu. | Mutlak yollar kullanın veya `Path.Combine` ile `Environment.CurrentDirectory` kullanın. |

## Full, runnable example

Aşağıda bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Hata yönetimi ve her adımı açıklayan yorumlar içerir.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Bu programı çalıştırdığınızda, dipnot ayırıcı çizgisi kırmızı, sonnot ayırıcı çizgisi mavi olacak bir Word dosyası üretilir; böylece **dipnot ayırıcıyı nasıl değiştirir** gereksinimi karşılanırken **Word belgesinde yazı tipi rengini değiştirme** de gösterilmiş olur.

## Conclusion

Artık Aspose.Words for .NET kullanarak bir Word belgesinde **dipnot ayırıcıyı nasıl değiştirir** ve **Word belgesinde yazı tipi rengini değiştirme** işlemlerini programatik olarak yapabildiğinizi biliyorsunuz. Yaklaşım şu şekildedir:

1. Belgeyi yükleyin.  
2. Gizli ayırıcı paragraflarını alın.  
3. `Font.Color` özelliklerini ayarlayın.  
4. Değiştirilmiş dosyayı kaydedin.

Buradan itibaren daha gelişmiş stil seçeneklerini keşfedebilirsiniz—çizgi kalınlığını ayarlama, farklı yazı tipleri uygulama veya işlemi birçok dosya üzerinde otomatikleştirme. Bu teknikleri ustalıkla kullanmak, C# kodundan doğrudan Word belgesi görünümünü ince ayarlarla kontrol etmenizi sağlar.

---


## What Should You Learn Next?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Word Belgesinde Paragraf Stil Ayırıcıyı Al](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Aspose.Words Kullanarak Başlık ve Altbilgi ile Word Belgesi Oluştur](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET ile Word Belgesinin Altbilgisine Sayfa Numarası Ekle](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}