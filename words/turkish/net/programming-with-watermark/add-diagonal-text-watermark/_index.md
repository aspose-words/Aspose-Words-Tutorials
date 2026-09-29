---
title: Aspose.Words for .NET kullanarak bir Word belgesinde Özel Yazı Tipiyle Diyagonal Metin Filigranı Oluşturun
weight: 210
limit:
description: Aspose.Words for .NET kullanarak bir Word .docx dosyasına özel yazı tipiyle diyagonal metin filigranı eklemek için adım adım kod.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET kullanarak bir Word .docx dosyasına özel yazı
    tipiyle diyagonal metin filigranı eklemek için adım adım kod.
  headline: Aspose.Words for .NET kullanarak bir Word belgesinde Özel Yazı Tipiyle
    Diyagonal Metin Filigranı Oluşturun
  type: TechArticle
- description: Aspose.Words for .NET kullanarak bir Word .docx dosyasına özel yazı
    tipiyle diyagonal metin filigranı eklemek için adım adım kod.
  name: Aspose.Words for .NET kullanarak bir Word belgesinde Özel Yazı Tipiyle Diyagonal
    Metin Filigranı Oluşturun
  steps:
  - name: Yeni boş bir Word belge örneği `document` adıyla oluşturun.
    text: Yeni boş bir Word belge örneği `document` adıyla oluşturun.
  - name: '`watermarkSettings`''i Arial 48 pt gri yazı tipi, diyagonal düzen ve opak
      render ile yapılandırın.'
    text: '`watermarkSettings`''i Arial 48 pt gri yazı tipi, diyagonal düzen ve opak
      render ile yapılandırın.'
  - name: Önceden tanımlanan ayarları kullanarak "Private" metin filigranını `document`'e
      uygulayın.
    text: Önceden tanımlanan ayarları kullanarak "Private" metin filigranını `document`'e
      uygulayın.
  - name: Filigranlı belgenin kaydedileceği dosya yolunu tanımlayın.
    text: Filigranlı belgenin kaydedileceği dosya yolunu tanımlayın.
  - name: Değiştirilen `document`'i belirtilen yola .docx dosyası olarak kaydedin.
    text: Değiştirilen `document`'i belirtilen yola .docx dosyası olarak kaydedin.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent`, filigranın kısmi saydamlıkla render edilip edilmediğini
      belirler; `false` olarak ayarlandığında filigran tamamen opak olur, `true` ise
      varsayılan yarı saydam etkiyi uygular.'
    question: '`TextWatermarkOptions` içinde **IsSemitrasparent** bayrağının neyi
      kontrol ettiğini öğrenin.'
  - answer: Evet—`document.Watermark.SetText` çağırmadan önce `Layout` özelliğini
      `WatermarkLayout.Horizontal` (veya başka bir enum değeri) olarak ayarlayın.
    question: Filigran yönünü diyagonal yerine yatay olarak değiştirebilir miyim?
  - answer: Word, filigran için varsayılan yazı tipine geri döner, böylece metin hâlâ
      görünür ancak istenen stilden farklı görünebilir.
    question: Belirtilen `FontFamily` (ör. "Arial") hedef makinede yüklü değilse ne
      olur?
  - answer: Mevcut dosyayı `Document document = new Document("Existing.docx");` ile
      yükleyin, ardından `TextWatermarkOptions`'ı yapılandırın ve gösterildiği gibi
      `document.Watermark.SetText`'i çağırın.
    question: Yeni bir dosya oluşturmak yerine mevcut bir `.docx` dosyasına filigran
      eklemek mümkün mü?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Özel Yazı Tipiyle Diyagonal Metin Filigranı Ekle
og_description: Kendi yazı tipinizle eğik bir metin filigranını dakikalar içinde bir Word dosyasına yerleştirmeyi öğrenin.
og_image_alt: Aspose.Words for .NET kullanarak bir Word belgesine özel yazı tipiyle diyagonal metin filigranı eklemeyi gösteren rehber.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak bir Word belgesinde Özel Yazı Tipiyle Diyagonal Metin Filigranı Oluşturun
Bu öğretici, yeni bir Word belgesi oluşturmayı, seçtiğiniz yazı tipi ayarlarıyla diyagonal bir metin filigranı yapılandırmayı, bunu Document.Watermark.SetText API'si aracılığıyla uygulamayı ve sonucu .docx dosyası olarak kaydetmeyi adım adım gösterir. Sonunda, markanızı veya sahipliğinizi sergileyen profesyonel bir filigranlı belgeye sahip olacaksınız. Adım adım kod, herhangi bir .NET projesine kopyalanmaya hazırdır.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: `TextWatermarkOptions` içinde **IsSemitrasparent** bayrağının neyi kontrol ettiğini öğrenin.**  
A: `IsSemitrasparent`, filigranın kısmi saydamlıkla render edilip edilmediğini belirler; `false` olarak ayarlandığında filigran tamamen opak olur, `true` ise varsayılan yarı saydam etkiyi uygular.

**Q: Filigran yönünü diyagonal yerine yatay olarak değiştirebilir miyim?**  
A: Evet—`document.Watermark.SetText` çağırmadan önce `Layout` özelliğini `WatermarkLayout.Horizontal` (veya başka bir enum değeri) olarak ayarlayın.

**Q: Belirtilen `FontFamily` (ör. "Arial") hedef makinede yüklü değilse ne olur?**  
A: Word, filigran için varsayılan yazı tipine geri döner, böylece metin hâlâ görünür ancak istenen stilden farklı görünebilir.

**Q: Yeni bir dosya oluşturmak yerine mevcut bir `.docx` dosyasına filigran eklemek mümkün mü?**  
A: Mevcut dosyayı `Document document = new Document("Existing.docx");` ile yükleyin, ardından `TextWatermarkOptions`'ı yapılandırın ve gösterildiği gibi `document.Watermark.SetText`'i çağırın.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}