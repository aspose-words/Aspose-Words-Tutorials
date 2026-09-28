---
category: general
date: 2026-02-13
description: Yüzen şekilleri koruyarak docx'i pdf olarak kaydedin. Word'ü pdf'ye nasıl
  dönüştüreceğinizi, şekilleri nasıl dışa aktaracağınızı ve C#'ta kenar durumlarını
  nasıl ele alacağınızı öğrenin.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: tr
og_description: Yüzen şekilleri koruyarak docx'i pdf olarak kaydedin. Bu rehber, Word'ü
  pdf'ye nasıl dönüştüreceğinizi, şekilleri nasıl dışa aktaracağınızı ve yaygın sorunları
  nasıl ele alacağınızı gösterir.
og_title: Shape Export ile docx'i PDF olarak kaydet – Tam Kılavuz
tags:
- Aspose.Words
- C#
- PDF conversion
title: Şekil Dışa Aktarma ile docx'i pdf olarak kaydet – Tam Kılavuz
url: /tr/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx'i pdf olarak kaydet – Full‑stack Öğretici (C#)

Hiç **docx'i pdf olarak kaydetmek** ve o yüzen diyagramların tam olarak aynı görünmesini sağlamak istediniz mi? Yalnız değilsiniz. Birçok geliştirici, Word’teki şekillerin dönüşüm sonrası kaybolması veya bozulmasıyla karşılaşıyor. İyi haber? Birkaç C# satırıyla kütüphaneye her şekli blok‑seviyesinde bir öğe olarak ele almasını söyleyebilir ve sonuç olarak PDF'nin sadık bir kopyasını elde edebilirsiniz.

Bu rehberde tüm süreci adım adım inceleyeceğiz: bir `.docx` dosyasını yüklemek, şekillerin doğru dışa aktarılmasını sağlayacak **convert word to pdf** seçeneklerini yapılandırmak ve sonunda PDF'yi diske yazmak. Sonuna geldiğinizde **how to export shapes** konusunu öğrenecek, farklı dışa aktarma modlarının artı‑eksilerini anlayacak ve herhangi bir .NET projesine ekleyebileceğiniz çalıştırılabilir bir kod örneğine sahip olacaksınız.

> **What you’ll get:** tam bir, çalıştırılabilir örnek, her ayarın *neden* önemli olduğuna dair açıklamalar, uç durumlar için ipuçları ve çözümü genişletme fikirleri (ör. görüntü işleme, özel yazı tipleri veya parola korumalı PDF'ler).

---

## Prerequisites

- .NET 6+ (veya .NET Framework 4.7+). Kullandığımız API her iki platformda da çalışır.
- Aspose.Words for .NET (ücretsiz deneme veya lisanslı sürüm). NuGet üzerinden kurun: `Install-Package Aspose.Words`.
- Yüzen şekiller (metin kutuları, otomatik‑şekiller, SmartArt vb.) içeren bir Word belgesi (`input.docx`).
- Visual Studio 2022 veya tercih ettiğiniz herhangi bir IDE.

Başka üçüncü‑taraf kütüphane gerekmez.

---

## Step‑by‑Step Implementation

Aşağıdaki her adımda kısa bir kod parçacığı, sade bir açıklama ve **how to export shapes** konusundaki doğru ayar notunu göreceksiniz.

### ## Step 1 – Load the source document (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Why this matters:* `Document` sınıfı, Word dosyasının tamamını bellek içinde temsil eder. Bu adımı atlayarsanız dönüştürülecek bir şey olmaz ve sonraki PDF seçenekleri üzerinde çalışacak bir nesne kalmaz.

### ## Step 2 – Configure PDF save options (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Explanation**

- `PdfSaveOptions` Aspose.Words'a Word yapısını PDF'ye nasıl çevireceğini söyleyen bir “ayar çantası”dır.
- **ExportFloatingShapesAsInlineTag** özelliğinin üç olası değeri vardır:
  1. **Inline** – şekiller satır içi öğeler haline gelir (genellikle çevredeki metne sıkışır).
  2. **Block** – her şekil kendi bloğunda yer alır; bu, orijinal görünümü korumanın en güvenli yoludur.
  3. **Auto** – kütüphane otomatik karar verir (her zaman en iyi seçeneği seçmeyebilir).

**Block** seçmek, *need to export shapes* olduğunda ve şekillerin orijinal belgede göründüğü gibi tam olarak dışa aktarılması gerektiğinde önerilen yaklaşımdır. Bu, sadece `doc.Save("out.pdf")` çağrısı yapıldığında birçok kullanıcının karşılaştığı “şekil kayboluyor” sorununu önler.

### ## Step 3 – Save the document as PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*What you’ll see:* Bu satır çalıştırıldıktan sonra `FloatingShapes.pdf` `C:\MyFolder` içinde bulunur. Açın ve her metin kutusu, açıklama ve SmartArt'ın kaynak `.docx` dosyasındaki konumda olduğunu görmelisiniz.

---

## Full Working Example

Aşağıda **tam program** yer alıyor; bir konsol uygulaması olarak derleyip çalıştırabilirsiniz. Gerekli tüm `using` ifadeleri ve açıklayıcı yorumlar eklenmiştir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Expected output**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Oluşturulan PDF'yi açın ve tüm şekillerin orijinal konumlarını koruduğunu doğrulayın. Eğer bir şekil hâlâ yanlış konumda görünüyorsa, Word'de gerçekten *yüzen* bir şekil (satır içi resim değil) olduğundan emin olun.

---

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **Can I export shapes as inline instead of block?** | Evet – `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline` olarak ayarlayın. Bu, basit düzenler için faydalı olabilir, ancak daha sıkı metin akışı ve olası çakışmalarla karşılaşabilirsiniz. |
| **What if my document contains images inside shapes?** | Aynı seçenek çalışır; Aspose.Words şekli içindeki görüntüyü birlikte rasterleştirir. En yüksek doğruluk için, daha iyi sıkıştırma istiyorsanız `PdfSaveOptions.JpegQuality` ayarını da etkinleştirin. |
| **Does this work with password‑protected DOCX files?** | Belgeyi, şifreyi sağlayan bir `LoadOptions` nesnesiyle yükleyin, ardından normal şekilde devam edin. |
| **Can I convert multiple DOCX files in a batch?** | Üç adımlı mantığı bir dosya listesi üzerinde `foreach` döngüsüyle sarın. Performans için `PdfSaveOptions` örneğini yeniden kullanmayı unutmayın. |
| **Is the PDF compatible with older readers (Acrobat 7)?** | Varsayılan olarak Aspose.Words PDF 1.7 dosyaları üretir. Eski okuyucular için arşiv‑düzeyi PDF oluşturmak isterseniz `pdfOptions.Compliance = PdfCompliance.PdfA1b` ayarını kullanın. |

---

## Pro Tips & Common Pitfalls

- **Pro tip:** Dönüştürme sonrası hafif dikey kaymalar fark ederseniz, `pdfOptions.UsePdfDocumentStructure = true` ayarını deneyin. Bu, PDF motorunun Word yerleşim hiyerarşisini korumasını sağlar.
- **Watch out for:** Yüzen şekillerle birlikte tablo sabitlemeleri içeren belgeler. Bazı durumlarda blok dışa aktarımı bir tabloyu yeni bir sayfaya itebilir; bunu `pdfOptions.PageSetup` ayarlarını kaydetmeden önce düzenleyerek azaltabilirsiniz.
- **Performance note:** Çok sayıda dosya işliyorsanız aynı `PdfSaveOptions` örneğini yeniden kullanmak, GC baskısını azaltır ve toplu dönüşümlerde hızı artırır.

---

## Visual Reference

Below is a schematic screenshot (placeholder) showing the before/after of a document with a floating text box.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*The image illustrates how the shape stays exactly where it was in the original Word file after conversion.*  
*Görsel, dönüşüm sonrasında şeklin orijinal Word dosyasındaki tam konumunda kaldığını gösterir.*

---

## Wrap‑Up

**docx'i pdf olarak kaydet** while keeping every floating shape intact konusunu ele aldık, önemli **convert word to pdf** ayarlarını inceledik ve en sık sorulan “**how to export shapes**” sorularına yanıt verdik. Tam kod örneği herhangi bir C# projesine eklenmeye hazır ve isteğe bağlı ayarlar, toplu işleme veya PDF/A uyumluluğu gibi gerçek dünya senaryoları için esneklik sağlıyor.

### Next Steps

- Farklı uyumluluk seviyeleri (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) ile **convert word document pdf** deneyin ve düzenleyici gereksinimlerinizi karşılayın.
- Parola korumalı dosyalar için **how to convert docx pdf** üzerine deney yapın – `LoadOptions` içinde şifre ekleyin ve `PdfSaveOptions` içinde `EncryptionDetails` ayarlayın.
- Aynı `Document` nesnesini kullanarak diğer çıktı formatlarını (ör. XPS, HTML) keşfedin; tek değişiklik `Save` metodunun format argümanı olacaktır.

Daha fazla sorunuz mu var? Yorum bırakın, iyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}