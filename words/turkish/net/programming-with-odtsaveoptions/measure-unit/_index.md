---
title: Ölçü Birimi
linktitle: Ölçü Birimi
second_title: Aspose.Words Belge İşleme API'si
description: ODT dönüştürme sırasında belge biçimlendirmesini korumak için Aspose.Words for .NET'te ölçüm birimi özelliğinin nasıl yapılandırılacağını öğrenin.
weight: 10
url: /tr/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ölçü Birimi

## giriiş

Word belgelerinizi farklı biçimlere dönüştürmeniz gerekti ancak düzeniniz için belirli bir ölçü birimine mi ihtiyacınız oldu? İster inç, ister santimetre veya puanla uğraşıyor olun, belgenizin dönüştürme işlemi sırasında bütünlüğünü koruması çok önemlidir. Bu eğitimde, .NET için Aspose.Words'de ölçü birimi özelliğinin nasıl yapılandırılacağını ele alacağız. Bu güçlü özellik, belgenizin biçimlendirmesinin ODT (Açık Belge Metni) biçimine dönüştürürken tam olarak ihtiyaç duyduğunuz şekilde korunmasını sağlar.

## Ön koşullar

Koda dalmadan önce, başlamak için ihtiyacınız olacak birkaç şey var:

1. Aspose.Words for .NET: Aspose.Words for .NET'in en son sürümünün yüklü olduğundan emin olun. Eğer henüz yüklü değilse, şuradan indirebilirsiniz:[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: C# kodunuzu yazmak ve çalıştırmak için Visual Studio benzeri bir IDE.
3. Temel C# Bilgisi: C# temellerini anlamak, eğitimi takip etmenize yardımcı olacaktır.
4. Word Belgesi: Dönüştürme işleminde kullanabileceğiniz örnek bir Word belgesi hazır bulundurun.

## Ad Alanlarını İçe Aktar

Kodlamaya başlamadan önce, gerekli ad alanlarının içe aktarıldığından emin olalım. Kod dosyanızın en üstüne şu using yönergelerini ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Belge Dizininizi Ayarlayın

Öncelikle belge dizininize giden yolu tanımlamanız gerekir. Word belgenizin bulunduğu ve dönüştürülen dosyanın kaydedileceği yer burasıdır.

```csharp
// Belgelerinizin dizinine giden yol
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENTS DIRECTORY"` dizininize giden gerçek yol ile. Bu, kodunuzun Word belgenizi nerede bulacağını bilmesini sağlar.

## Adım 2: Word Belgesini Yükleyin

 Sonra, dönüştürmek istediğiniz Word belgesini yüklemeniz gerekir. Bu, şu şekilde yapılır:`Document` Aspose.Words'den sınıf.

```csharp
// Word belgesini yükleyin
Document doc = new Document(dataDir + "Document.docx");
```

"Belge.docx" adlı Word belgenizin belirtilen dizinde bulunduğundan emin olun.

## Adım 3: Ölçüm Birimini Yapılandırın

 Şimdi, ODT dönüşümü için ölçüm birimini yapılandıralım. Sihir burada gerçekleşir. Şunu ayarlayacağız:`OdtSaveOptions` ölçü birimi olarak inç kullanmak.

```csharp
// "Ölçüm birimi" özelliği ile yedekleme seçeneklerinin yapılandırılması
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 Bu örnekte, ölçüm birimini inç olarak ayarlıyoruz. Ayrıca, aşağıdaki gibi diğer birimleri de seçebilirsiniz:`OdtSaveMeasureUnit.Centimeters` veya`OdtSaveMeasureUnit.Points` İhtiyaçlarınıza bağlı olarak.

## Adım 4: Belgeyi ODT'ye Dönüştürün

 Son olarak, yapılandırılmış olan Word belgesini ODT biçimine dönüştüreceğiz.`OdtSaveOptions`.

```csharp
// Belgeyi ODT'ye dönüştür
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Bu kod satırı, dönüştürülen belgeyi yeni ölçüm birimi uygulanarak belirtilen dizine kaydeder.

## Çözüm

İşte bu kadar! Bu adımları izleyerek, Aspose.Words for .NET'te ölçüm birimi özelliğini kolayca yapılandırabilir ve dönüştürme sırasında belgenizin düzeninin korunmasını sağlayabilirsiniz. İster inç, ister santimetre veya nokta ile çalışıyor olun, bu eğitim belgenizin biçimlendirmesini kolayca nasıl kontrol edeceğinizi göstermiştir.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, Word belgeleriyle programatik olarak çalışmak için güçlü bir kütüphanedir. Geliştiricilerin Microsoft Word gerektirmeden Word belgeleri oluşturmasına, değiştirmesine, dönüştürmesine ve işlemesine olanak tanır.

### İnç dışında başka ölçü birimleri kullanabilir miyim?
 Evet, Aspose.Words for .NET santimetre ve puan gibi diğer ölçüm birimlerini destekler. İstediğiniz birimi kullanarak belirtebilirsiniz`OdtSaveMeasureUnit` sayım.

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?
 Evet, Aspose.Words for .NET'in ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/).

### Aspose.Words for .NET için dokümanları nerede bulabilirim?
 Aspose.Words for .NET için kapsamlı belgelere şu adresten erişebilirsiniz:[bu bağlantı](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET desteğini nasıl alabilirim?
 Destek için Aspose.Words forumunu ziyaret edebilirsiniz.[bu bağlantı](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
