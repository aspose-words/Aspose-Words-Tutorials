---
title: Scale Wmf Fonts To Metafile Boyutuyla PDF Boyutunu Küçültün
linktitle: Scale Wmf Fonts To Metafile Boyutuyla PDF Boyutunu Küçültün
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET ile PDF'e dönüştürürken ölçek wmf yazı tiplerini meta dosyası boyutuna küçültme kılavuzu.
weight: 10
url: /tr/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Scale Wmf Fonts To Metafile Boyutuyla PDF Boyutunu Küçültün

## giriiş

PDF dosyalarıyla çalışırken, özellikle WMF (Windows Meta Dosyası) grafikleri içeren Word belgelerinden oluşturulan dosyalarda, boyut yönetimi belge işlemenin önemli bir yönü haline gelebilir. PDF boyutunu kontrol etmenin bir yolu, WMF yazı tiplerinin belge içinde nasıl işlendiğini ayarlamaktır. Bu eğitimde, .NET için Aspose.Words kullanarak WMF yazı tiplerini meta dosya boyutuna ölçekleyerek PDF boyutunu nasıl küçülteceğimizi inceleyeceğiz.

## Ön koşullar

Adımlara dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Değilse, şunları yapabilirsiniz:[buradan indirin](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Bu eğitimde, C# kodu yazıp çalıştırabileceğiniz bir .NET geliştirme ortamınız (örneğin Visual Studio) olduğunu varsayıyoruz.
3. .NET Programlamanın Temel Anlayışı: Temel .NET programlama kavramlarına ve C# sözdizimine aşinalık faydalı olacaktır.
4. WMF Grafikli Word Belgesi: WMF grafikleri içeren bir Word belgesine ihtiyacınız olacak. Kendi belgenizi kullanabilir veya test için bir tane oluşturabilirsiniz.

## Ad Alanlarını İçe Aktar

Öncelikle C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu, Aspose.Words ile çalışmak için gereken sınıflara ve yöntemlere erişmenizi sağlayacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Word Belgesini Yükleyin

 Başlamak için, WMF grafiklerini içeren Word belgesini yükleyin. Bu, şu şekilde yapılır:`Document` Aspose.Words'den sınıf.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Belgeyi yükle
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Burada,`dataDir` belge dizin yolunuz için bir yer tutucudur. Bir örneğini oluşturuyoruz`Document` Word dosyasına giden yolu geçirerek sınıf. Bu, belgeyi belleğe yükler ve daha fazla işleme hazır hale getirir.

## Adım 2: Meta Dosyası Oluşturma Seçeneklerini Yapılandırın

 Sonra, meta dosyası oluşturma seçeneklerini yapılandırmanız gerekir. Özellikle,`ScaleWmfFontsToMetafileSize`mülk`false`. Bu, WMF yazı tiplerinin meta dosyası boyutuyla eşleşecek şekilde ölçeklenip ölçeklenmeyeceğini kontrol eder.

```csharp
// MetafileRenderingOptions'ın yeni bir örneğini oluşturun
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 The`MetafileRenderingOptions` sınıf, meta dosyalarının (WMF gibi) nasıl işleneceğine ilişkin seçenekler sağlar. Ayarlayarak`ScaleWmfFontsToMetafileSize` ile`false`, Aspose.Words'e meta dosya boyutuna göre yazı tiplerini ölçeklememesi talimatını veriyorsunuz; bu, genel PDF boyutunu azaltmaya yardımcı olabilir.

## Adım 3: PDF Kaydetme Seçeneklerini Ayarlayın

Şimdi, PDF kaydetme seçeneklerini az önce ayarladığınız meta dosya oluşturma seçeneklerini kullanacak şekilde yapılandırın. Bu, Aspose.Words'e belgeyi PDF olarak kaydederken meta dosyaları nasıl işleyeceğini söyler.

```csharp
// PdfSaveOptions'ın yeni bir örneğini oluşturun
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 The`PdfSaveOptions` sınıf, belgeyi PDF olarak kaydetmek için çeşitli ayarları belirtmenize olanak tanır. Önceden yapılandırılmış ayarları atayarak`MetafileRenderingOptions` için`MetafileRenderingOptions` mülkiyeti`PdfSaveOptions`, belgenin istediğiniz meta dosyası oluşturma ayarlarına göre kaydedilmesini sağlarsınız.

## Adım 4: Belgeyi PDF olarak kaydedin

Son olarak, yapılandırılmış kaydetme seçeneklerini kullanarak Word belgesini PDF olarak kaydedin. Bu, meta dosya oluşturma seçenekleri de dahil olmak üzere tüm ayarları çıktı PDF'sine uygulayacaktır.


```csharp
// Belgeyi PDF olarak kaydedin
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 Bu adımda,`Save` yöntemi`Document` sınıf, belgeyi bir PDF dosyasına aktarmak için kullanılır. PDF'nin kaydedileceği yol,`PdfSaveOptions` meta dosyası oluşturma ayarlarını da içerir.

## Çözüm

WMF yazı tiplerini meta dosya boyutuna ölçekleyerek, Word belgelerinden oluşturulan PDF dosyalarınızın boyutunu önemli ölçüde azaltabilirsiniz. Bu teknik, görsel içeriğin kalitesinden ödün vermeden belge depolama ve dağıtımını optimize etmeye yardımcı olur. Yukarıda belirtilen adımları izlemek, PDF dosyalarınızın daha yönetilebilir ve boyut olarak daha verimli olmasını sağlar.

## SSS

### WMF nedir ve PDF boyutu için neden önemlidir?

WMF (Windows Meta Dosyası), Microsoft Windows'da kullanılan bir grafik biçimidir. Hem vektör hem de bitmap verileri içerebilir. Vektör verileri ölçeklenebilir ve işlenebilir olduğundan, gereksiz yere büyük PDF dosyalarından kaçınmak için bunları düzgün bir şekilde işlemek önemlidir.

### WMF yazı tiplerinin meta dosya boyutuna ölçeklenmesi PDF'yi nasıl etkiler?

WMF yazı tiplerini meta dosyası boyutuna ölçeklemek, dosya boyutunu artırabilecek yüksek çözünürlüklü yazı tipi oluşturma işlemlerinden kaçınarak genel PDF boyutunu azaltmaya yardımcı olabilir.

### Aspose.Words ile diğer meta dosyası formatlarını kullanabilir miyim?

Evet, Aspose.Words, WMF'nin yanı sıra EMF (Gelişmiş Meta Dosyası) da dahil olmak üzere çeşitli meta dosyası biçimlerini destekler.

### Bu teknik her türlü Word belgesine uygulanabilir mi?

Evet, bu teknik WMF grafikleri içeren herhangi bir Word belgesine uygulanabilir ve oluşturulan PDF'in boyutunun optimize edilmesine yardımcı olur.

### Aspose.Words hakkında daha fazla bilgiyi nerede bulabilirim?

 Aspose hakkında daha fazla bilgi edinmek için Words'ü ziyaret edebilirsiniz.[Aspose.Words Belgeleri](https://reference.aspose.com/words/net/) İndirmeler, denemeler ve destek için şu adresi ziyaret edin:[Aspose.Words İndirme Sayfası](https://releases.aspose.com/words/net/), [Aspose.Words'ü satın al](https://purchase.aspose.com/buy), [Ücretsiz Deneme](https://releases.aspose.com/), [Geçici Lisans](https://purchase.aspose.com/temporary-license/) , Ve[Destek](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
