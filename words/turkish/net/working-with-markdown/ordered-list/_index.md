---
title: Sıralı Liste
linktitle: Sıralı Liste
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET'i kullanarak Word belgelerinde sıralı listelerin nasıl oluşturulacağını adım adım kılavuzumuzla öğrenin. Belge oluşturmayı otomatikleştirmek için mükemmeldir.
weight: 10
url: /tr/net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sıralı Liste

## giriiş

Yani, programatik olarak muhteşem Word belgeleri oluşturmak için Aspose.Words for .NET'e dalmaya karar verdiniz. Harika bir seçim! Bugün, Word belgesinde sıralı bir liste oluşturmayı açıklayacağız. Adım adım ilerleyeceğiz, bu nedenle ister kodlama konusunda yeni başlayan biri olun ister deneyimli bir profesyonel, bu kılavuzu çok faydalı bulacaksınız. Başlayalım!

## Ön koşullar

Koda dalmadan önce ihtiyacınız olacak birkaç şey var:

1. Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olduğundan emin olun. Yüklü değilse, indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
3. Temel C# Bilgisi: Kolayca takip edebilmek için C# temellerine hakim olmalısınız.

## Ad Alanlarını İçe Aktar

Projenizde Aspose.Words kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Bu, çalışmaya başlamadan önce araç kutunuzu ayarlamaya benzer.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Kodu küçük parçalara bölelim ve her bir parçayı açıklayalım. Hazır mısınız? Hadi başlayalım!

## Adım 1: Belgeyi Başlatın

İlk önce, yeni bir belge oluşturmanız gerekir. Bunu bilgisayarınızda boş bir Word belgesi açmak gibi düşünün.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Burada yeni bir belge ve bir DocumentBuilder nesnesi başlatıyoruz. DocumentBuilder kaleminiz gibidir ve belgeye içerik yazmanıza olanak tanır.

## Adım 2: Numaralandırılmış Liste Formatını Uygula

Şimdi, varsayılan numaralandırılmış liste biçimini uygulayalım. Bu, Word belgenizi numaralandırılmış madde işaretleri kullanacak şekilde ayarlamak gibidir.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Bu kod satırı listenizin numaralandırmasını ayarlar. Kolay, değil mi?

## Adım 3: Liste Öğeleri Ekleyin

Şimdi listemize birkaç madde ekleyelim. Bir alışveriş listesi yazdığınızı düşünün.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Bu satırlarla listenize ilk iki maddeyi ekliyorsunuz.

## Adım 4: Listeyi girintili hale getirin

Bir öğenin altına alt öğeler eklemek isterseniz ne olur? Hadi yapalım!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

 The`ListIndent` yöntem listeyi girintiler ve bir alt liste oluşturur. Şimdi, iç içe geçmiş yapılacaklar listesi gibi, hiyerarşik bir liste oluşturuyorsunuz.

## Çözüm

Word belgesinde programatik olarak sıralı bir liste oluşturmak ilk başta göz korkutucu görünebilir, ancak Aspose.Words for .NET ile bu çok kolaydır. Bu basit adımları izleyerek, belgelerinize kolayca liste ekleyebilir ve yönetebilirsiniz. İster raporlar üretiyor, ister yapılandırılmış belgeler oluşturuyor veya sadece iş akışlarınızı otomatikleştiriyor olun, Aspose.Words for .NET sizin için her şeyi yapar. Öyleyse neden bekliyorsunuz? Kodlamaya başlayın ve büyünün ortaya çıkışını görün!

## SSS

### Listenin numaralandırma stilini özelleştirebilir miyim?  
 Evet, numaralandırma stilini kullanarak özelleştirebilirsiniz.`ListFormat`özellikleri. Roma rakamları, harfler vb. gibi farklı numaralandırma stilleri ayarlayabilirsiniz.

### Daha fazla girinti düzeyi nasıl eklerim?  
 Kullanabilirsiniz`ListIndent` alt listelerin daha derin seviyelerini oluşturmak için yöntemi birden çok kez kullanın. Her çağrı`ListIndent` bir düzey girinti ekler.

### Madde işaretli ve numaralı listeleri bir arada kullanabilir miyim?  
 Kesinlikle! Aynı belge içinde farklı liste biçimlerini kullanarak uygulayabilirsiniz.`ListFormat` mülk.

### Önceki bir listeden numaralandırmaya devam etmek mümkün müdür?  
Evet, aynı liste biçimini kullanarak numaralandırmaya devam edebilirsiniz. Aspose.Words, farklı paragraflar arasında liste numaralandırmasını kontrol etmenizi sağlar.

### Liste formatını nasıl kaldırabilirim?  
 Liste biçimini şu şekilde çağırarak kaldırabilirsiniz:`ListFormat.RemoveNumbers()`Bu, liste öğelerini tekrar normal paragraflara dönüştürecektir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
