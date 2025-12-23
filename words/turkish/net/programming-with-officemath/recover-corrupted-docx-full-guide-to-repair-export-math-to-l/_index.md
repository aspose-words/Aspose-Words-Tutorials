---
category: general
date: 2025-12-23
description: Bozuk docx dosyalarını nasıl kurtaracağınızı, kurtarma modunu nasıl kullanacağınızı,
  denklemleri LaTeX'e nasıl dışa aktaracağınızı ve C#'ta benzersiz resim adları nasıl
  oluşturacağınızı öğrenin. Açıklamalı adım adım kod.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: tr
og_description: Bozuk docx dosyalarını kurtarın, kurtarma modunu kullanın, denklemleri
  LaTeX'e dışa aktarın ve C#'ta Aspose.Words ile benzersiz resim adları oluşturun.
og_title: Bozuk docx dosyasını kurtar – Tam C# Öğreticisi
tags:
- Aspose.Words
- C#
- Document Recovery
title: bozuk docx dosyasını kurtar – Onarım, Matematiği LaTeX'e Dışa Aktarma ve Benzersiz
  Görsel İsimleri Oluşturma Tam Kılavuzu
url: /tr/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# bozuk docx dosyasını kurtar – Onarım, Matematik'i LaTeX'e Dışa Aktarma ve Benzersiz Görsel İsimleri Oluşturma Tam Kılavuzu

Hiç **.docx** dosyasını açmaya çalıştınız mı ve bozuk olduğu için yüklenmiyorsa? Yalnız değilsiniz. Gerçek dünyadaki birçok projede, bozuk bir Word dosyası tüm iş akışını durdurabilir, ancak iyi haber şu ki **recover corrupted docx** dosyalarını programlı olarak kurtarabilirsiniz.  

Bu öğreticide **recover corrupted docx** adımlarını ayrıntılı olarak gösterecek, **how to use recovery mode** nasıl kullanılacağını anlatacak, **export equations to LaTeX** işlemini gösterecek ve son olarak Markdown olarak kaydederken **generate unique image names** nasıl yapılacağını göstereceğiz. Sonunda, tüm bu görevleri sorunsuz bir şekilde yerine getiren tek bir çalıştırılabilir C# programına sahip olacaksınız.

## Prerequisites

- .NET 6 veya üzeri (kod .NET Framework .6+ ile de çalışır).  
- Aspose.Words for .NET (ücretsiz deneme veya lisanslı sürüm). NuGet üzerinden kurun:

```bash
dotnet add package Aspose.Words
```

- C# ve dosya I/O konusunda temel bilgi.  
- Test etmek için bozuk bir `corrupt.docx` dosyası (geçerli bir dosyayı keserek bozulma simüle edebilirsiniz).

> **Pro tip:** Başlamadan önce orijinal dosyanın bir yedeğini alın—kurtarma yalnızca kaynağı üzerine yazarsanız yıkıcı olur.

## Step 1 – Recover the corrupted DOCX using Recovery Mode

İlk olarak Aspose.Words’a gelen dosyanın potansiyel olarak hasarlı olduğunu söylememiz gerekir. İşte **how to use recovery mode** burada devreye girer.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Neden önemli:**  
`RecoveryMode.Recover` etkinleştirildiğinde, Aspose.Words okunamayan bölümleri atlayarak iç belge ağacını yeniden oluşturmaya çalışır ve mümkün olduğunca çok içeriği korur. Bu özellik olmadan `Document` yapıcı bir istisna fırlatır ve dosyayı kurtarma şansını kaybedersiniz.

> **Dosya tamir edilemezse ne olur?**  
> Kütüphane yine de bir `Document` nesnesi döndürür, ancak bazı düğümler eksik olabilir. Kaç öğenin hayatta kaldığını görmek için `doc.GetChildNodes(NodeType.Any, true).Count` kontrol edebilirsiniz.

## Step 2 – Export Office Math equations to LaTeX when saving as Markdown

Birçok teknik belgede Office Math ile yazılmış denklemler bulunur. Bu denklemlere LaTeX ihtiyacınız varsa—örneğin bilimsel bir blogda yayınlamak için—Aspose.Words’tan dönüşümü talep edebilirsiniz.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Nasıl çalışır:**  
`OfficeMathExportMode.LaTeX` kaydediciyi her `OfficeMath` düğümünü LaTeX temsiliyle `$…$` (satır içi) veya `$$…$$` (görünüm) biçiminde değiştirmeye yönlendirir. Oluşan Markdown dosyası doğrudan Hugo veya Jekyll gibi statik site jeneratörlerine beslenebilir.

> **Köşe durumu:** Orijinal belgede karmaşık denklem nesneleri (ör. matrisler) varsa, LaTeX dönüşümü çok satırlı çıktı üretebilir. Oluşan `.md` dosyasını inceleyerek biçimlendirme beklentilerinizi karşıladığından emin olun.

## Step 3 – Save the document as PDF while controlling floating shape tags

Bazen aynı belgenin bir PDF sürümüne ihtiyacınız olur, ancak yüzen şekillerin (resimler, metin kutuları) erişilebilirlik için nasıl etiketlendiği de önemlidir. `ExportFloatingShapesAsInlineTag` bayrağı bu kontrolü sağlar.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Bu bayrağı neden değiştirirsiniz?**  
- `true` → Yüzen şekiller `<Figure>` etiketine dönüşür, bu da birçok ekran okuyucunun bunları başlıklı ayrı görseller olarak algılamasını sağlar.  
- `false` → Şekiller genel `<Div>` etiketine sarılır, bu da yardımcı teknolojiler tarafından göz ardı edilebilir. Erişilebilirlik gereksinimlerinize göre seçim yapın.

## Step 4 – Export to Markdown with custom image handling (generate unique image names)

Word belgesini Markdown’a kaydettiğinizde, gömülü tüm görseller diske yazılır. Varsayılan olarak orijinal dosya adı kullanılır; bu da aynı klasörde birden çok belge işlediğinizde çakışmalara yol açabilir. Kaydetme sürecine müdahale edip **generate unique image names** otomatik olarak yapalım.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Arka planda neler oluyor?**  
`ResourceSavingCallback` kaydetme işlemi sırasında her dış kaynak (görseller, SVG’ler vb.) için tetiklenir. Tam bir yol döndürerek dosyanın nereye ve hangi adla kaydedileceğini belirlersiniz. GUID, **generate unique image names** sağlamak için manuel bir işlem gerektirmez.

> **İpucu:** Belirli bir adlandırma şeması (ör. görsel alt metnine dayalı) isterseniz, `Guid.NewGuid()` yerine `resourceInfo.Name`’in bir hash’ini kullanın.

## Full Working Example

Her şeyi bir araya getirdiğimizde, konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program aşağıdadır:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Expected Output

Programı çalıştırdığınızda aşağıdaki gibi konsol mesajları almanız gerekir:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Üç dosya bulacaksınız:

| File | Purpose |
|------|---------|
| `out.md` | Her Office Math denkleminin LaTeX (`$…$` veya `$$…$$`) olarak göründüğü Markdown. |
| `out.pdf` | Yüzen şekiller `<Figure>` etiketiyle işaretlenmiş PDF sürümü, daha iyi erişilebilirlik için. |
| `out2.md` + `md_images\*` | Markdown ve benzersiz‑adlı (GUID‑tabanlı) görsel dosyalarının bulunduğu klasör. |

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if the corrupted file has no recoverable content?** | Aspose.Words hâlâ bir `Document` nesnesi döndürür, ancak boş olabilir. Devam etmeden önce `doc.GetChildNodes(NodeType.Paragraph, true).Count` kontrol edin. |
| **Can I change the LaTeX delimiter?** | Evet—`markdownMathOptions.MathDelimiter = "$$"` ayarlayarak görüntü‑stili sınırlayıcıları zorlayabilirsiniz. |
| **Do I need to dispose of the `Document` object?** | `Document` sınıfı `IDisposable` uygular. Birçok dosya işliyorsanız yerel kaynakları hızlıca serbest bırakmak için `using` bloğu içinde kullanın. |
| **How do I keep the original image filenames?** | Geri arama içinde `Path.Combine(imageFolder, resourceInfo.Name)` döndürün. Ancak ad çakışması riskini unutmayın. |
| **Is the GUID approach safe for version‑controlled repos?** | GUID’ler çalıştırmalar arasında sabittir, ancak insan‑okunabilir değildir. Tekrarlanabilir isimler isterseniz, orijinal ismi bir proje‑geneli tuzla hash’leyin. |

## Conclusion

**recover corrupted docx** dosyalarını nasıl kurtaracağınızı, **how to use recovery mode** nasıl kullanılacağını ve **export equations to LaTeX** ile **generate unique image names** nasıl yapılacağını gösterdik.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}