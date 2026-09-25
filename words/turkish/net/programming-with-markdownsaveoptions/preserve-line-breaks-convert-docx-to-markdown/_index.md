---
category: general
date: 2026-02-13
description: "DOCX'i markdown'a dönüştürürken satır sonlarını koruyun.  \nWord'ü markdown
  olarak kaydetmeyi, boş paragrafları dışa aktarmayı ve biçimlendirmeyi bozulmadan
  tutmayı öğrenin."
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: tr
og_description: "DOCX'i markdown'a dönüştürürken satır sonlarını koruyun.  \nBu kılavuz,
  Word'ü markdown olarak kaydetmeyi ve boş paragrafları doğru şekilde dışa aktarmayı
  gösterir."
og_title: 'Satır Sonlarını Koru: DOCX''i Markdown''a Dönüştür'
tags:
- Aspose.Words
- C#
- Markdown
title: 'Satır Sonlarını Koru: DOCX''i Markdown''a Dönüştür'
url: /tr/net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

.

We'll translate.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Satır Sonlarını Koru: DOCX'i Markdown'a Dönüştürme

Bir DOCX dosyasını Markdown'a dönüştürürken **satır sonlarını koruma** ihtiyacı hiç duydunuz mu? Bu yaygın bir sorun—güzel Word belgeniz tek bir metin duvarına dönüşüyor ve o kasıtlı boş satırlar kayboluyor. İyi haber? Birkaç basit ayarla her satır sonunu, hatta boş paragrafları bile tutabilirsiniz.

Bu öğreticide **Word'ü Markdown olarak kaydetme** sürecini baştan sona ele alacağız; kaynak belgeyi yüklemekten doğru dışa aktarma modunu yapılandırmaya kadar her şeyi kapsayacağız. Sonunda *boş paragrafları nasıl dışa aktaracağınızı*, *karmaşık düzenlerde satır sonlarını nasıl koruyacağınızı* öğrenecek ve eksiksiz, kopyala‑yapıştır‑hazır bir kod örneğine sahip olacaksınız. Eksik parça yok, “belgelere bakın” gibi çıkmazlar da yok.

## Öğrenecekleriniz

- Satır sonlarını korumanın okunabilirlik ve sonraki araçlar için neden önemli olduğu.  
- Aspose.Words for .NET kullanarak **DOCX'i markdown'a dönüştürme** yöntemi.  
- Boş paragraf işleme kontrolünü sağlayan `MarkdownSaveOptions` ayarları.  
- Tablolar, listeler ve kod blokları gibi kenar durumlarıyla başa çıkma ipuçları.  
- Bugün herhangi bir C# projesine ekleyebileceğiniz tam, çalıştırılabilir bir örnek.

### Önkoşullar

- .NET 6+ (veya .NET Framework 4.7.2+) yüklü.  
- **Aspose.Words for .NET** lisansı (bu demo için ücretsiz deneme sürümü yeterli).  
- C# ve Markdown kavramına temel aşinalık.  

Bu koşulları karşıladığınızda, hemen başlayalım.

![Satır sonlarını koruma diyagramı](preserve-line-breaks.png "Boş paragrafların Markdown'da satır sonlarına nasıl dönüştüğünü gösteren diyagram")

## Satır Sonlarını Koru – Neden Önemli

Bir Word belgesinde kasıtlı boş satırlar—bölümler arasındaki görsel ayırıcılar gibi—dönüştürme sırasında genellikle silinir. Markdown, tasarım gereği tek bir satır sonunu aynı paragrafın devamı olarak kabul eder; bu yüzden boş bir satırın açıkça temsil edilmesi gerekir. **Satır sonlarını korumazsanız**, çıktınız sıkışık görünebilir ve sonraki ayrıştırıcılar (statik site üreticileri gibi) bölümleri istemeden birleştirebilir.

Bu boşlukları tutmak sadece estetikle ilgili değil; aynı zamanda dipnot yerleştirme, özel stil uygulama ya da SEO‑dostu başlık çıkarımı gibi paragraf sınırlarına dayanan araçlar için de faydalıdır. Kısacası, doğru bir dönüşüm yazarın niyetine saygı gösterir.

## Aspose.Words ile DOCX'i Markdown'a Dönüştürme

Aspose.Words, dönüşüm sürecinde ince ayar yapmanızı sağlar. Ana sınıf `MarkdownSaveOptions` olup, boş paragrafların nasıl dışa aktarılacağını belirlemenize imkan tanır. Aşağıda `EmptyParagraphExportMode` özelliğini `EmptyLine` olarak ayarlayacağız; bu mod, boş bir Word paragrafını boş bir Markdown satırına çevirir.

### Adım‑Adım Uygulama

### 1️⃣ Kaynak Belgeyi Yükle

Öncelikle kütüphaneyi `.docx` dosyanıza yönlendirin. `Document` yapıcısı tüm ağır işi yapar—stil, resim ve düzen bilgilerini ayrıştırır.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **Neden önemli:** Belgeyi erken yüklemek, iç yapısına erişmenizi sağlar; böylece keşfettiklerinize göre (örneğin dosyanın gerçekten boş paragraf içerip içermediğini tespit ederek) ayarları ince ayar yapabilirsiniz.

### 2️⃣ Markdown Kaydetme Seçeneklerini Yapılandır

İşte **“boş paragrafları nasıl dışa aktarırız?”** sorusunun cevabı. `EmptyParagraphExportMode` enum’ı üç seçenek sunar:

| Mod | Markdown'da Sonuç |
|------|--------------------|
| `EmptyLine` | Boş bir satır ekler (`\n\n`). |
| `PreserveLineBreaks` | Her satır sonunu sert bir kırılma haline getirir (`  \n`). |
| `None` | Boş paragrafı tamamen atar. |

Çoğu senaryoda görsel bir boşluk istiyorsanız, `EmptyLine` yeterli olur.

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **Pro ipucu:** Manuel satır sonlarını da (Word'de Shift + Enter) tutmak istiyorsanız, `PreserveLineBreaks = true` olarak ayarlayın. Böylece hem boş paragraflar hem de yumuşak kırılmalar dönüşümde korunur.

### 3️⃣ Belgeyi Markdown Olarak Kaydet

Şimdi çıktıyı dosyaya yazalım. İstediğiniz herhangi bir klasörü seçebilirsiniz; sadece uzantının `.md` olduğundan emin olun.

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

Bu, tüm işlem hattıdır. Programı çalıştırın, `.md` dosyasını açın ve orijinal Word dosyasındaki boş satırların tam olarak aynı yerde olduğunu göreceksiniz.

### Tam Çalışan Örnek

Hepsini bir araya getirdiğimizde, anında derlenebilen bağımsız bir konsol uygulaması elde ediyoruz:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**Beklenen çıktı:** `WithEmptyParas.md` dosyasını herhangi bir editörde açın. `input.docx` dosyasındaki her boş satırın Markdown dosyasında da boş bir satır olarak göründüğünü, tasarladığınız görsel ayrımı koruduğunu fark edeceksiniz.

## Word'ü Markdown Olarak Kaydet – İleri Senaryolar

### Tablolar ve Listelerle Çalışma

Word'deki tablolar otomatik olarak Markdown tablolarına dönüşür, ancak boş satırlar sorun yaratabilir. Bir tablo satırı yalnızca boş bir hücre içeriyorsa, Aspose.Words bunu boş bir paragraf olarak değerlendirir. `EmptyParagraphExportMode` hâlâ geçerli olduğundan, tablo **dışında** bir boş satır elde edersiniz—tablonun içinde değil. Tablo içinde görsel bir boşluk bırakmak isterseniz, hücreye kırılmayan boşluk (`&nbsp;`) ekleyin.

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### Kod Blokları ve Ön‑Biçimlendirilmiş Metin

DOCX içinde ön‑biçimlendirilmiş kod varsa, Aspose.Words bunu üç backtick (` ``` `) içinde sarar. Kod bloğu içindeki boş satırlar, `EmptyParagraphExportMode` ne olursa olsun otomatik olarak korunur. Ancak eksik boş satırlar fark ederseniz, orijinal Word paragraf stilinin “No Spacing” (Boşluk Yok) olarak ayarlandığından emin olun. Böylece kütüphane her satırı ayrı bir paragraf olarak ele alır.

### `PreserveLineBreaks` Ne Zaman Kullanılır?

Bazen tam bir boş paragraf yerine sert bir satır kırılması (`  `) gerekir. Örneğin şiir ya da adres blokları genellikle tek satır kırılmalarına dayanır. Seçeneği şu şekilde değiştirin:

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

Artık Word'deki her `Shift+Enter` Markdown'da `  \n` haline gelir, gerçek boş paragraflar ise (eğer `EmptyLine` da etkinleştirilmemişse) kaybolur.

## Boş Paragrafları Doğru Şekilde Dışa Aktarmak

Kısa cevap: `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine` ayarlayın. Uzun cevap ise bunun *neden* işe yaradığını anlamaktır.

- **EmptyParagraphExportMode** serileştiriciye hiçbir metin içermeyen bir paragrafla ne yapılacağını söyler.  
- **EmptyLine** çift yeni satır ekler; Markdown bunu paragraf ayırıcı olarak yorumlar.  
- Diğer modlar paragrafı daraltır (`None`) veya satır sonlarını sert kırılma olarak işler (`PreserveLineBreaks`).

Bu ayarı unutursanız, varsayılan davranış `None` olur ve tüm boş satırlar kaybolur—tam da çözmek istediğimiz sorun.

## Karmaşık Belgelerde Satır Sonlarını Korumak

Karmaşık belgeler genellikle başlıklar, görseller ve dipnotları karıştırır. Satır sonlarını kaybetmemek için aşağıdaki kontrol listesini izleyin:

| Kontrol Listesi Öğesi | Neden Önemli |
|------------------------|--------------|
| **Boş paragrafları doğrula** | Dönüştürmeden önce `doc.GetChildNodes(NodeType.Paragraph, true)` ile boşları sayın. |
| **Şiir için `PreserveLineBreaks` etkinleştir** | Tek satır kırılmalarının korunmasını garantiler. |
| **Görsel alt yazılarını kontrol et** | Alt yazılar ayrı paragraflardır; aynı dışa aktarma moduna ihtiyaç duyarlar. |
| **Dönüşüm sonrası diff çalıştır** | Orijinal metni (`doc.GetText()`) Markdown çıktısıyla karşılaştırın. |
| **Markdown görüntüleyicide test et** | Bazı render'lar birden çok boş satırı farklı yorumlayabilir; görsel sonucu doğrulayın. |

### Örnek Doğrulama Kodu

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

Kaydetme adımından önce bu kodu çalıştırmak, beklediğiniz satır sayısını gerçekten elde edip etmediğinize dair size güven verir.

## Yaygın Tuzaklar & Pro İpuçları

- **Tuzak:** 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}