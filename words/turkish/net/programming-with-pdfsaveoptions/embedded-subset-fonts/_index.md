---
title: Alt Küme Yazı Tiplerini PDF Belgesine Göm
linktitle: Alt Küme Yazı Tiplerini PDF Belgesine Göm
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak yalnızca gerekli font alt kümelerini gömerek PDF dosya boyutunu azaltın. PDF'lerinizi verimli bir şekilde optimize etmek için adım adım kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alt Küme Yazı Tiplerini PDF Belgesine Göm

## giriiş

Bazı PDF dosyalarının benzer içerikler içerseler bile diğerlerinden çok daha büyük olduğunu fark ettiniz mi? Suçlu genellikle yazı tiplerindedir. Bir PDF'e yazı tiplerini yerleştirmek, her cihazda aynı görünmesini sağlar, ancak dosya boyutunu da şişirebilir. Neyse ki, .NET için Aspose.Words yalnızca gerekli yazı tipi alt kümelerini yerleştirmek için kullanışlı bir özellik sunarak PDF'lerinizi yalın ve verimli tutar. Bu eğitim sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET: İndirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- .NET Ortamı: Çalışan bir .NET geliştirme ortamınız olduğundan emin olun.
- Temel C# Bilgisi: C# programlamaya aşina olmanız, takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET'i kullanmak için projenize gerekli ad alanlarını içe aktarmanız gerekir. Bunları C# dosyanızın en üstüne ekleyin:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Belgeyi Yükleyin

 Öncelikle PDF'e dönüştürmek istediğimiz Word belgesini yüklememiz gerekiyor. Bu, şu şekilde yapılır:`Document` Aspose.Words tarafından sağlanan sınıf.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Bu kod parçacığı şu konumda bulunan belgeyi yükler:`dataDir` . Değiştirdiğinizden emin olun`"YOUR DOCUMENT DIRECTORY"` belgenizin gerçek yolunu belirtin.

## Adım 2: PDF Kaydetme Seçeneklerini Yapılandırın

 Daha sonra, şunu yapılandırıyoruz:`PdfSaveOptions` yalnızca gerekli yazı tipi alt kümelerinin gömülmesini sağlamak için. Ayarlayarak`EmbedFullFonts` ile`false`, Aspose.Words'e yalnızca belgede kullanılan glifleri yerleştirmesini söylüyoruz.

```csharp
// Çıktı PDF'i belgedeki yazı tiplerinin alt kümelerini içerecektir.
// PDF yazı tiplerine yalnızca belgede kullanılan glifler dahil edilir.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Bu küçük ama önemli adım PDF dosya boyutunu önemli ölçüde azaltmaya yardımcı olur.

## Adım 3: Belgeyi PDF olarak kaydedin

 Son olarak, belgeyi PDF olarak kaydediyoruz`Save` yöntem, yapılandırılmış olanı uygulayarak`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 Bu kod, şu isimde bir PDF dosyası üretecektir:`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` belirtilen dizinde, yalnızca gerekli yazı tipi alt kümeleri gömülü olarak.

## Çözüm

İşte karşınızda! Bu basit adımları izleyerek, Aspose.Words for .NET kullanarak yalnızca gerekli font alt kümelerini gömerek PDF dosyalarınızın boyutunu etkili bir şekilde azaltabilirsiniz. Bu yalnızca depolama alanından tasarruf sağlamakla kalmaz, aynı zamanda özellikle kapsamlı fontlara sahip belgeler için daha hızlı yükleme süreleri ve daha iyi performans sağlar.

## SSS

### Neden bir PDF'e yalnızca yazı tipi alt kümelerini yerleştirmeliyim?
Yalnızca gerekli yazı tipi alt kümelerini yerleştirmek, belgenin görünümünden ve okunabilirliğinden ödün vermeden PDF dosya boyutunu önemli ölçüde azaltabilir.

### Gerekirse tam yazı tiplerini yerleştirmeye geri dönebilir miyim?
 Evet, yapabilirsiniz. Basitçe şunu ayarlayın:`EmbedFullFonts`mülk`true` içinde`PdfSaveOptions`.

### Aspose.Words for .NET diğer PDF optimizasyon özelliklerini destekliyor mu?
Kesinlikle! Aspose.Words for .NET, görüntü sıkıştırma ve kullanılmayan nesneleri kaldırma gibi PDF'leri optimize etmek için bir dizi seçenek sunar.

### Aspose.Words for .NET kullanılarak hangi yazı tipleri alt kümeye gömülebilir?
Aspose.Words for .NET, belgede kullanılan tüm TrueType yazı tipleri için alt küme yerleştirmeyi destekler.

### PDF dosyamda hangi yazı tiplerinin gömülü olduğunu nasıl doğrulayabilirim?
PDF'yi Adobe Acrobat Reader'da açabilir ve gömülü fontları görmek için Fontlar sekmesi altındaki özellikleri kontrol edebilirsiniz.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
