---
category: general
date: 2026-08-04
description: Aspose.Words kullanarak C#'ta dipnot ayırıcıyı değiştirin – dipnot ayırıcıyı
  nasıl düzenleyeceğinizi ve Word belgelerinde sonnot ayırıcıyı nasıl değiştireceğinizi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: tr
lastmod: 2026-08-04
og_description: Aspose.Words ile C#'ta dipnot ayırıcıyı değiştirin. Bu rehber, dipnot
  ayırıcıyı nasıl düzenleyeceğinizi, sonnot ayırıcıyı nasıl özelleştireceğinizi ve
  güncellenmiş belgeyi nasıl kaydedeceğinizi gösterir.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: C#'de dipnot ayırıcıyı değiştir – tam Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Aspose.Words kullanarak C#'de dipnot ayırıcıyı değiştir
url: /tr/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak Aspose.Words ile dipnot ayırıcıyı değiştirin

Bir Word belgesinde **dipnot ayırıcıyı değiştirmek** istiyorsanız, bu öğretici Aspose.Words for .NET ile tam adımları size gösterir. Varsayılan çizgiyi bir sembolle değiştirmek ya da sonnot ayırıcılarına farklı bir stil uygulamak isteyin, aşağıdaki kod tam süreci kapsar.

Ayrıca **dipnot ayırıcıyı düzenleme** ve ilgili **sonnot ayırıcıyı değiştirme** işlemini de öğreneceksiniz; böylece aynı belge hem dipnotlar hem de sonnotlar için tutarlı bir stil elde edebilir. Harici araçlara gerek yok—sadece birkaç satır C#.

## Ne elde edeceksiniz

Bu kılavuzun sonunda şunları yapabilecek durumdasınız:

* Dipnot ve sonnot içeren mevcut bir *.docx* dosyasını yükleyin.  
* Dipnotlar, dipnot devamları ve sonnotlar için ayırıcı düğümlerine erişin.  
* Ayırıcı karakterini (örneğin, varsayılan çizgiyi bir yıldız işaretiyle değiştirin) değiştirin.  
* Diğer içerikleri kaybetmeden değiştirilmiş belgeyi kaydedin.  

Bu öğretici, C# hakkında temel bir anlayışa sahip olduğunuzu ve **Aspose.Words** NuGet paketini (sürüm 24.9 veya daha yeni) kurduğunuzu varsayar.  

---

## Gereksinimler

| Gereksinim | Sebep |
|-------------|--------|
| .NET 6.0+ veya .NET Framework 4.7.2+ | Aspose.Words için gerekli çalışma zamanı |
| Aspose.Words for .NET kütüphanesi | `Document` ve `FootnoteOptions` API'lerini sağlar |
| En az bir dipnot veya sonnot içeren bir giriş Word dosyası (`input.docx`) | Ayırıcı değişimini gösterir |

Projeye Aspose.Words eklemek için aşağıdaki CLI komutunu kullanabilirsiniz:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Adım 1: Dipnotları içeren belgeyi yükleyin

İlk işlem, kaynak dosyayı bir `Document` nesnesine okumaktır. Bu nesne, tüm Word dosyasını bellekte temsil eder ve tüm düğümlere erişim sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Neden önemli:** Belgeyi yüklemek, herhangi bir manipülasyonun giriş noktasıdır. Dosya bulunamazsa, Aspose.Words bir `FileNotFoundException` fırlatır; bu nedenle devam etmeden önce yolun doğru olduğundan emin olun.

---

## Adım 2: Dipnot ve sonnot ayırıcı düğümlerine erişin

`Document.FootnoteOptions` üç ayırıcı düğümünü ortaya çıkarır:

* `Separator` – İlk sayfadaki dipnot koleksiyonundan sonra görünen çizgi.  
* `ContinuationSeparator` – Dipnotlar bir sonraki sayfaya devam ettiğinde kullanılan çizgi.  
* `EndnoteSeparator` – Ana metni sonnot listesine ayıran çizgi.

Bu düğümleri genel `Node` nesneleri olarak alır, ardından metni değiştirmek için `Run` tipine dönüştürürsünüz.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Neden önemli:** Bu düğümler, görsel ayırıcı karakterinin bulunduğu tek yerdir. Başka bir düğümü (ör. normal bir paragraf) değiştirmek dipnot biçimlendirmesini etkilemez.

---

## Adım 3: Dipnot ayırıcı karakterini değiştirin

En yaygın gereksinim, varsayılan çizgiyi bir yıldız (`*`) gibi bir sembolle değiştirmektir. Ayırıcı bir `Run` olarak depolandığı için `Text` özelliğini güvenle değiştirebilirsiniz.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Neden önemli:** `Run.Text`'i doğrudan düzenlemek, diğer dipnot içeriğini etkilemeden son belge içinde görsel temsili günceller. Aynı desen, Unicode semboller dahil herhangi bir dizeyi uygulamak için kullanılabilir.

---

## Adım 4: Sonnot ayırıcıyı değiştirin (isteğe bağlı)

Ayrıca **sonnot ayırıcıyı değiştirmek** istiyorsanız, süreç dipnot değişimiyle aynıdır. `endnoteSeparator` metnini istediğiniz karakterle değiştirin.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Neden önemli:** Sonnotlar genellikle dipnotlardan farklı biçimlendirilir. Ayrı bir ayırıcı sağlamak, belge tasarım yönergelerinizle görsel tutarlılığı korumanıza olanak tanır.

---

## Adım 5: Değiştirilmiş belgeyi kaydedin

Tüm değişikliklerden sonra, `Document.Save` kullanarak değişiklikleri kalıcı hâle getirin. Orijinal dosyanın üzerine yazabilir veya yeni bir konuma kaydedebilirsiniz.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Neden önemli:** `Save`, bellek içi temsili diske yazar ve diğer tüm öğeleri (stilller, görseller, tablolar) değişmeden korur.

---

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek, tüm iş akışını gösteren bağımsız bir konsol uygulaması aşağıdadır:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Beklenen sonuç:** *ModifiedSeparators.docx* dosyasını Microsoft Word'de açın. İlk dipnot sayfasının altındaki dipnot ayırıcı çizgisi artık tek bir yıldız (`*`) olacaktır. Belge sonnot içeriyorsa, ana metni sonnot listesinden ayıran çizgi bir tire (`-`) olarak görünecektir. Diğer tüm içerik (metin, görseller, tablolar) dokunulmamış kalır.

---

## Yaygın sorular & kenar‑durum yönetimi

| Soru | Cevap |
|----------|--------|
| **Belge hiç dipnot içermiyorsa ne olur?** | `FootnoteOptions.Separator` hâlâ bir `Run` düğümü döndürür, ancak metni boş olabilir. Kod, düğüm tipini güvenli bir şekilde kontrol ederek değiştirmeye çalışır. |
| **Çok karakterli bir dize (ör. "***") kullanabilir miyim?** | Evet. `Run.Text` özelliği Unicode karakterler dahil herhangi bir dizeyi kabul eder. |
| **Ayırıcıyı değiştirmek mevcut dipnot numaralandırmasını etkiler mi?** | Hayır. Ayırıcı, numaralandırma şemasından bağımsızdır. |
| **`Document` nesnesini dispose etmem gerekiyor mu?** | `Document`, `Node` aracılığıyla dolaylı olarak `IDisposable` uygular. Kısa ömürlü bir konsol uygulamasında opsiyoneldir, ancak uzun‑çalışan servislerde bir `using` bloğu içinde sarmalamanız önerilir. |
| **.NET Core ile .NET Framework arasında nasıl çalışır?** | API, çalışma zamanları arasında aynıdır; yalnızca hedef framework sürümü önemlidir (Aspose.Words paketi tarafından desteklenmelidir). |

**İpucu:** Farklı bölümler için farklı ayırıcılar uygulamanız gerekiyorsa, `doc.GetChildNodes(NodeType.Footnote, true)` üzerinden döngü yaparak her dipnotun `Separator` özelliğini ayrı ayrı ayarlayabilirsiniz. Bu daha gelişmiş bir yaklaşımdır ancak karmaşık belgeler için faydalıdır.

---

## Sonuç

Artık Aspose.Words for C# kullanarak bir Word dosyasında **dipnot ayırıcıyı değiştirme** ve **sonnot ayırıcıyı değiştirme** konularını biliyorsunuz. Kılavuz, belgeyi yüklemeyi, ilgili ayırıcı düğümlerine erişmeyi, metinlerini değiştirmeyi ve sonucu kaydetmeyi tek bir bağımsız programda ele aldı.

Bundan sonra **dipnot ayırıcı stilini düzenleme**, dipnot numaralandırmasını özelleştirme veya sayfa düzenine dayalı koşullu biçimlendirme gibi ilgili konuları keşfedebilirsiniz. Aynı desen (bir düğüm al, `Run` tipine dönüştür, `Text`i değiştir) birçok Word‑işleme senaryosunda işe yarar.

İyi kodlamalar, farklı semboller denemekten veya ayırıcıları gerçekten benzersiz bir belge düzeni için görsellere dönüştürmekten çekinmeyin!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Dipnot ve Sonnot ile Kelime İşleme](/words/english/net/working-with-footnote-and-endnote/)
- [Word Belgesinde Paragraf Stili Ayırıcıyı Al](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Word'de Belge Stili Ayırıcı Ekle](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}