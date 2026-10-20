---
title: Aspose.Words for .NET kullanarak bir Word belgesinin altbilgisine sayfa numaraları ekleyin
weight: 210
limit:
description: Aspose.Words for .NET kullanarak bir Word belgesinin birincil altbilgisine otomatik olarak güncellenen sayfa numaraları ekleyin.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aspose.Words for .NET kullanarak bir Word belgesinin birincil altbilgisine
    otomatik olarak güncellenen sayfa numaraları ekleyin.
  headline: Aspose.Words for .NET kullanarak bir Word belgesinin altbilgisine sayfa
    numaraları ekleyin
  type: TechArticle
- description: Aspose.Words for .NET kullanarak bir Word belgesinin birincil altbilgisine
    otomatik olarak güncellenen sayfa numaraları ekleyin.
  name: Aspose.Words for .NET kullanarak bir Word belgesinin altbilgisine sayfa numaraları
    ekleyin
  steps:
  - name: Yeni bir Document nesnesi ve ona bağlı bir DocumentBuilder oluşturun.
    text: Yeni bir Document nesnesi ve ona bağlı bir DocumentBuilder oluşturun.
  - name: Builder'ın imlecini ilk bölümün birincil altbilgisine taşıyın.
    text: Builder'ın imlecini ilk bölümün birincil altbilgisine taşıyın.
  - name: Paragraf hizalamasını ortala olarak ayarlayın, böylece altbilgi metni ortalanır.
    text: Paragraf hizalamasını ortala olarak ayarlayın, böylece altbilgi metni ortalanır.
  - name: '"Page " etiketini yazın ve mevcut sayfa numarasını gösteren bir PAGE alanı
      ekleyin.'
    text: '"Page " etiketini yazın ve mevcut sayfa numarasını gösteren bir PAGE alanı
      ekleyin.'
  - name: '" of " yazın ve toplam sayfa sayısını gösteren bir NUMPAGES alanı ekleyin.'
    text: '" of " yazın ve toplam sayfa sayısını gösteren bir NUMPAGES alanı ekleyin.'
  - name: Belgeyi bir .docx dosyasına kaydedin.
    text: Belgeyi bir .docx dosyasına kaydedin.
  type: HowTo
- questions:
  - answer: Hayır. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` builder'ı
      yalnızca *ilk* bölümün birincil altbilgisine taşır, bu yüzden alanlar sadece
      oraya eklenir.
    question: Belge birden fazla bölüme sahipse, bu kod her bölümün altbilgisine sayfa
      numarası ekleyecek mi?
  - answer: Alanları yazmadan önce `builder.ParagraphFormat.Alignment` değerini başka
      bir `ParagraphAlignment` değerine (ör. `ParagraphAlignment.Right`) ayarlayın.
    question: Altbilgideki sayfa numarası paragrafının hizalamasını nasıl değiştirebilirim?
  - answer: '`InsertField` alan kodunu ve isteğe bağlı bir alan sonucunu alır; `null`
      geçmek, Aspose.Words''a sonucu çalışma zamanında Word''un hesaplamasını söyler.'
    question: '`InsertField("PAGE", null)` içindeki `null` argümanı neyi temsil eder?'
  - answer: Evet—alanları eklemeden önce `HeaderFooterType.FooterPrimary` yerine `HeaderFooterType.HeaderPrimary`
      (veya başka bir üstbilgi türü) ile değiştirin.
    question: Aynı "Page X of Y" alanlarını altbilgi yerine üstbilgiye yerleştirebilir
      miyim?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Word altbilgisine otomatik sayfa numaraları ekleyin
og_description: Aspose.Words for .NET ile bir Word altbilgisine canlı sayfa numaraları eklemek için adım adım kod.
og_image_alt: Aspose.Words for .NET kullanarak bir Word belgesinin altbilgisine otomatik sayfa numaraları eklemeyi gösteren kılavuz
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak bir Word belgesinin altbilgisine sayfa numaraları ekleyin
Bu öğreticide Aspose.Words Document ve DocumentBuilder kullanarak bir Word belgesinin birincil altbilgisine otomatik olarak güncellenen sayfa numaraları nasıl eklenir gösterilmektedir. Sayfa numaralarını programlı olarak ekleyerek, dosyanın tamamında manuel düzenleme yapmadan tutarlı sayfalama sağlarsınız. Örnek kod .NET ortamında çalıştırılmaya hazırdır.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Belge birden fazla bölüme sahipse, bu kod her bölümün altbilgisine sayfa numarası ekleyecek mi?**  
A: Hayır. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` builder'ı yalnızca *ilk* bölümün birincil altbilgisine taşır, bu yüzden alanlar sadece oraya eklenir.

**Q: Altbilgideki sayfa numarası paragrafının hizalamasını nasıl değiştirebilirim?**  
A: Alanları yazmadan önce `builder.ParagraphFormat.Alignment` değerini başka bir `ParagraphAlignment` değerine (ör. `ParagraphAlignment.Right`) ayarlayın.

**Q: `InsertField("PAGE", null)` içindeki `null` argümanı neyi temsil eder?**  
A: `InsertField` alan kodunu ve isteğe bağlı bir alan sonucunu alır; `null` geçmek, Aspose.Words'a sonucu çalışma zamanında Word'un hesaplamasını söyler.

**Q: Aynı "Page X of Y" alanlarını altbilgi yerine üstbilgiye yerleştirebilir miyim?**  
A: Evet—alanları eklemeden önce `HeaderFooterType.FooterPrimary` yerine `HeaderFooterType.HeaderPrimary` (veya başka bir üstbilgi türü) ile değiştirin.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}