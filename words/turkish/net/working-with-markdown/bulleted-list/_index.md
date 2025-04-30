---
"description": "Bu adım adım kılavuzla Aspose.Words for .NET'i kullanarak Word belgelerinde madde işaretli listelerin nasıl oluşturulacağını ve özelleştirileceğini öğrenin."
"linktitle": "Madde işaretli liste"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Madde işaretli liste"
"url": "/tr/net/working-with-markdown/bulleted-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Madde işaretli liste

## giriiş

Aspose.Words for .NET dünyasına dalmaya hazır mısınız? Bugün, Word belgelerinizde madde işaretli liste oluşturmayı ele alacağız. İster fikirleri düzenliyor, ister öğeleri listeliyor veya belgenize biraz yapı ekliyor olun, madde işaretli listeler oldukça kullanışlıdır. Hadi başlayalım!

## Ön koşullar

Kodlama eğlencesine başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Henüz yüklü değilse, [buradan indirin](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio benzeri AC# geliştirme ortamı.
3. Temel C# Bilgisi: C# programlamaya dair temel bir anlayışa sahip olmak, konuyu takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktaralım. Bu, kodumuzun sorunsuz çalışması için ortamı hazırlamak gibidir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Şimdi süreci kolay ve yönetilebilir adımlara bölelim.

## Adım 1: Yeni Bir Belge Oluşturun

Tamam, yeni bir belge oluşturarak başlayalım. Tüm sihir burada gerçekleşecek.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Adım 2: Madde İşaretli Liste Biçimini Uygula

Sonra, madde işaretli liste biçimini uygulayacağız. Bu, belgeye madde işaretli bir liste başlatmak üzere olduğumuzu söyler.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Adım 3: Madde İşaretli Listeyi Özelleştirin

Burada, madde işaretli listeyi kendi zevkimize göre özelleştireceğiz. Bu örnek için, madde işareti olarak tire (-) kullanacağız.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Adım 4: Liste Öğeleri Ekleyin

Şimdi, madde işaretli listemize birkaç madde ekleyelim. Burada yaratıcı olabilir ve ihtiyacınız olan içeriği ekleyebilirsiniz.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Adım 5: Alt Öğeler Ekleyin

İşleri daha ilginç hale getirmek için "Öğe 2"nin altına bazı alt öğeler ekleyelim. Bu, alt noktaları düzenlemeye yardımcı olur.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Ana liste düzeyine dön
```

## Çözüm

İşte karşınızda! Aspose.Words for .NET kullanarak bir Word belgesinde madde işaretli bir liste oluşturdunuz. Bu basit bir işlemdir ancak belgelerinizi düzenlemek için inanılmaz derecede güçlüdür. İster basit listeler, ister karmaşık iç içe geçmiş listeler oluşturun, Aspose.Words sizin için her şeyi yapar.

İhtiyaçlarınıza uygun farklı liste stilleri ve formatlarını denemekten çekinmeyin. İyi kodlamalar!

## SSS

### Listede farklı madde işaretleri kullanabilir miyim?
   Evet, madde işareti sembollerini değiştirerek özelleştirebilirsiniz. `NumberFormat` mülk.

### Daha fazla girinti düzeyi nasıl eklerim?
   Kullanın `ListIndent` daha fazla seviye ekleme yöntemi ve `ListOutdent` daha yüksek bir seviyeye geri dönmek.

### Madde işaretli ve numaralı listeleri karıştırmak mümkün müdür?
   Kesinlikle! Madde işareti ve sayı biçimleri arasında geçiş yapabilirsiniz. `ApplyNumberDefault` Ve `ApplyBulletDefault` Yöntemler.

### Liste öğelerindeki metinleri biçimlendirebilir miyim?
   Evet, liste öğelerindeki metne farklı stiller, yazı tipleri ve biçimlendirme uygulayabilirsiniz. `Font` mülkiyeti `DocumentBuilder`.

### Çok sütunlu madde işaretli liste nasıl oluşturabilirim?
   Her hücresi ayrı madde işaretli liste içeren çok sütunlu listeler oluşturmak için tablo biçimlendirmesini kullanabilirsiniz.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}