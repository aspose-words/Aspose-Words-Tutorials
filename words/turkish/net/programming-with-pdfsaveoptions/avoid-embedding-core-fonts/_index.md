---
title: Çekirdek Yazı Tiplerini Yerleştirmeyerek PDF Dosya Boyutunu Azaltın
linktitle: Çekirdek Yazı Tiplerini Yerleştirmeyerek PDF Dosya Boyutunu Azaltın
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak çekirdek yazı tiplerini gömmeyerek PDF dosya boyutunu nasıl küçülteceğinizi öğrenin. PDF'lerinizi optimize etmek için adım adım kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Çekirdek Yazı Tiplerini Yerleştirmeyerek PDF Dosya Boyutunu Azaltın

## giriiş

Hiç kafanızı kaşıyarak PDF dosyalarınızın neden bu kadar büyük olduğunu merak ettiğiniz oldu mu? Eh, yalnız değilsiniz. Yaygın bir suçlu, Arial ve Times New Roman gibi temel yazı tiplerini yerleştirmektir. Neyse ki, .NET için Aspose.Words bu sorunu ele almak için akıllıca bir yola sahip. Bu eğitimde, bu temel yazı tiplerini yerleştirmekten kaçınarak PDF dosyanızın boyutunu nasıl küçülteceğinizi göstereceğim. Hemen başlayalım!

## Ön koşullar

Bu heyecan verici yolculuğa çıkmadan önce, ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım. İşte hızlı bir kontrol listesi:

-  Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olduğundan emin olun. Eğer henüz yüklü değilse, indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio gibi bir geliştirme ortamına ihtiyacınız olacak.
- Word Belgesi: Bu eğitimde bir Word belgesi (örneğin, "Rendering.docx") kullanacağız.
- Temel C# Bilgisi: C# hakkında temel bir anlayışa sahip olmak konuyu takip etmenize yardımcı olacaktır.

Tamam, artık her şey tamam olduğuna göre, asıl meseleye gelelim!

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktaralım. Bu adım, ihtiyacımız olan tüm Aspose.Words işlevlerine erişimimizi sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Belge Dizininizi Başlatın

Belgemizi düzenlemeye başlamadan önce, belgelerimizin depolandığı dizini belirtmemiz gerekir. Bu, dosyalara erişim için önemlidir.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` Word belgenizin bulunduğu gerçek yol ile.

## Adım 2: Word Belgesini Yükleyin

Sonra, PDF'ye dönüştürmek istediğimiz Word belgesini yüklememiz gerekiyor. Bu örnekte, "Rendering.docx" adlı bir belge kullanıyoruz.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Bu kod satırı, belgeyi belleğe yükleyerek daha ileri işlemlere hazır hale getirir.

## Adım 3: PDF Kaydetme Seçeneklerini Yapılandırın

Şimdi sihirli kısım geliyor! Temel yazı tiplerini gömmekten kaçınmak için PDF kaydetme seçeneklerini yapılandıracağız. Bu, PDF dosya boyutunu küçültmeye yardımcı olan temel adımdır.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 Ayar`UseCoreFonts` ile`true` Arial ve Times New Roman gibi temel yazı tiplerinin PDF'e gömülmemesini sağlayarak dosya boyutunu önemli ölçüde azaltır.

## Adım 4: Belgeyi PDF olarak kaydedin

Son olarak, yapılandırılmış kaydetme seçeneklerini kullanarak Word belgesini PDF olarak kaydediyoruz. Bu adım, çekirdek yazı tiplerini gömmeden PDF dosyasını oluşturur.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

Ve işte oldu! PDF dosyanız artık belirtilen dizine o hantal çekirdek yazı tipleri olmadan kaydedildi.

## Çözüm

PDF dosya boyutunu küçültmek Aspose.Words for .NET ile çocuk oyuncağı olabilir. Çekirdek yazı tiplerinin gömülmesinden kaçınarak, dosya boyutunu önemli ölçüde küçültebilir ve belgelerinizi paylaşmayı ve depolamayı kolaylaştırabilirsiniz. Umarım bu eğitim faydalı olmuştur ve size süreç hakkında net bir anlayış sağlamıştır. Unutmayın, küçük ayarlamalar büyük fark yaratabilir!

## SSS

### PDF'lere çekirdek yazı tiplerini yerleştirmekten neden kaçınmalıyım?
Çekirdek yazı tiplerinin gömülmesinden kaçınılması dosya boyutunu küçültür, paylaşımı ve depolamayı kolaylaştırır.

### Gömülü çekirdek yazı tipleri olmadan PDF'yi hala doğru şekilde görüntüleyebilir miyim?
Evet, Arial ve Times New Roman gibi temel yazı tipleri genellikle çoğu sistemde mevcuttur.

### Özel yazı tiplerini eklemem gerekirse ne olur?
 Özelleştirebilirsiniz`PdfSaveOptions`gerektiğinde belirli yazı tiplerini yerleştirmek için.

### Aspose.Words for .NET'i kullanmak ücretsiz mi?
 Aspose.Words for .NET lisans gerektirir. Ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?
 Ayrıntılı dokümanları bulabilirsiniz[Burada](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
