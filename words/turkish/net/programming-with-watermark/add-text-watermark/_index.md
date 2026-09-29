---
title: Aspose.Words for .NET kullanarak Word Belgelerine Kırmızı Çapraz Metin Filigranı Ekleyin
weight: 110
limit:
description: Aspose.Words for .NET kullanarak toplu olarak oluşturulan her Word dosyasına otomatik olarak kırmızı çapraz metin filigranı uygulayın.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET kullanarak toplu olarak oluşturulan her Word
    dosyasına otomatik olarak kırmızı çapraz metin filigranı uygulayın.
  headline: Aspose.Words for .NET kullanarak Word Belgelerine Kırmızı Çapraz Metin
    Filigranı Ekleyin
  type: TechArticle
- description: Aspose.Words for .NET kullanarak toplu olarak oluşturulan her Word
    dosyasına otomatik olarak kırmızı çapraz metin filigranı uygulayın.
  name: Aspose.Words for .NET kullanarak Word Belgelerine Kırmızı Çapraz Metin Filigranı
    Ekleyin
  steps:
  - name: '"GeneratedReports" klasörünü oluşturun; çıktı dosyaları bu klasöre kaydedilecektir.'
    text: '"GeneratedReports" klasörünü oluşturun; çıktı dosyaları bu klasöre kaydedilecektir.'
  - name: Üç ayrı belge oluşturacak bir döngü başlatın.
    text: Üç ayrı belge oluşturacak bir döngü başlatın.
  - name: Yeni boş bir Word belge nesnesi oluşturun.
    text: Yeni boş bir Word belge nesnesi oluşturun.
  - name: Belgeye bir başlık satırı ve açıklama eklemek için DocumentBuilder'ı kullanın.
    text: Belgeye bir başlık satırı ve açıklama eklemek için DocumentBuilder'ı kullanın.
  - name: Filigranın görünümünü, yazı tipi, boyut, renk ve çapraz düzen dahil olmak
      üzere tanımlayın.
    text: Filigranın görünümünü, yazı tipi, boyut, renk ve çapraz düzen dahil olmak
      üzere tanımlayın.
  - name: Belgeye "PROTECTED" metniyle yapılandırılmış kırmızı çapraz filigranı uygulayın.
    text: Belgeye "PROTECTED" metniyle yapılandırılmış kırmızı çapraz filigranı uygulayın.
  - name: Filigranlı belgeyi benzersiz bir dosya adıyla "GeneratedReports" klasörüne
      kaydedin.
    text: Filigranlı belgeyi benzersiz bir dosya adıyla "GeneratedReports" klasörüne
      kaydedin.
  - name: Mevcut belge işlendikten sonra döngüyü kapatın.
    text: Mevcut belge işlendikten sonra döngüyü kapatın.
  type: HowTo
- questions:
  - answer: IsSemitrasparent, filigranın kısmi saydamlıkla render edilip edilmediğini
      belirler; **true** olarak ayarlandığında metin yarı saydam olur ve alttaki içerik
      daha okunabilir hâle gelir.
    question: '**IsSemitrasparent** seçeneği neyi kontrol eder ve **true** olarak
      ayarlandığında ne etkisi olur?'
  - answer: Evet—**document.Watermark.SetText**'i çağırmadan önce **TextWatermarkOptions**
      içinde **Layout** özelliğini **WatermarkLayout.Horizontal** olarak ayarlayın.
    question: Filigran yönünü çapraz yerine yatay olarak değiştirebilir miyim?
  - answer: Parça yeni bir **Document** örneği oluşturur, ancak herhangi bir mevcut
      dosyayı (ör. `new Document("Existing.docx")`) açıp ardından aynı filigranı uygulamak
      için **document.Watermark.SetText**'i çağırabilirsiniz.
    question: Bu kod mevcut bir Word dosyasına filigran ekleyecek mi, yoksa yalnızca
      yeni oluşturulan belgelere mi?
  - answer: '**TextWatermarkOptions**''ın **Color** özelliğine **Color.FromArgb(red,
      green, blue)** ile özel bir renk atayın; örneğin mor için `Color = Color.FromArgb(128,
      0, 128)`.'
    question: Önceden tanımlı **Color.Red** yerine filigran için özel bir RGB rengi
      nasıl kullanabilirim?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Word Belgelerine Kırmızı Çapraz Metin Filigranı Ekleyin
og_description: Aspose.Words ile toplu bir grup Word belgesine kırmızı çapraz filigranı otomatik olarak nasıl uygulayacağınızı görün.
og_image_alt: Aspose.Words for .NET kullanarak Word belgelerine kırmızı çapraz metin filigranı eklemenin gösterildiği rehber
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word Belgelerine Kırmızı Çapraz Metin Filigranı Ekleyin
Bu öğretici, toplu rapor oluşturma sırasında oluşturulan her Word belgesine otomatik olarak kırmızı çapraz metin filigranı yerleştirmenin nasıl yapılacağını gösterir. Aspose.Words for .NET'in Document ve DocumentBuilder sınıfları kullanılarak, dosyalar üretildiği anda programlı olarak filigran uygulanır; böylece her belge aynı marka ya da gizlilik uyarısını manuel çaba harcamadan taşır.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: **IsSemitrasparent** seçeneği neyi kontrol eder ve **true** olarak ayarlandığında ne etkisi olur?**  
A: IsSemitrasparent, filigranın kısmi saydamlıkla render edilip edilmediğini belirler; **true** olarak ayarlandığında metin yarı saydam olur ve alttaki içerik daha okunabilir hâle gelir.

**Q: Filigran yönünü çapraz yerine yatay olarak değiştirebilir miyim?**  
A: Evet—**document.Watermark.SetText**'i çağırmadan önce **TextWatermarkOptions** içinde **Layout** özelliğini **WatermarkLayout.Horizontal** olarak ayarlayın.

**Q: Bu kod mevcut bir Word dosyasına filigran ekleyecek mi, yoksa yalnızca yeni oluşturulan belgelere mi?**  
A: Parça yeni bir **Document** örneği oluşturur, ancak herhangi bir mevcut dosyayı (ör. `new Document("Existing.docx")`) açıp ardından aynı filigranı uygulamak için **document.Watermark.SetText**'i çağırabilirsiniz.

**Q: Önceden tanımlı **Color.Red** yerine filigran için özel bir RGB rengi nasıl kullanabilirim?**  
A: **TextWatermarkOptions**'ın **Color** özelliğine **Color.FromArgb(red, green, blue)** ile özel bir renk atayın; örneğin mor için `Color = Color.FromArgb(128, 0, 128)`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}