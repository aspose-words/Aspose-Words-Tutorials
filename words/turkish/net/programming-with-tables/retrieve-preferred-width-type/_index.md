---
title: Tercih Edilen Genişlik Türünü Al
linktitle: Tercih Edilen Genişlik Türünü Al
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET'i kullanarak Word belgelerindeki tablo hücrelerinin tercih edilen genişlik türünü nasıl alacağınızı adım adım kılavuzumuzla öğrenin.
weight: 10
url: /tr/net/programming-with-tables/retrieve-preferred-width-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tercih Edilen Genişlik Türünü Al

## giriiş

Aspose.Words for .NET kullanarak Word belgelerinizdeki tablo hücrelerinin tercih edilen genişlik türünü nasıl alacağınızı hiç merak ettiniz mi? Doğru yerdesiniz! Bu eğitimde, süreci adım adım açıklayarak çocuk oyuncağı haline getireceğiz. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuzu yararlı ve ilgi çekici bulacaksınız. O halde, Word belgelerinde tablo hücresi genişliklerini yönetmenin sırlarını keşfedelim.

## Ön koşullar

Başlamadan önce ihtiyacınız olacak birkaç şey var:

1.  Aspose.Words for .NET: En son sürümün yüklü olduğundan emin olun. Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi bir IDE'ye ihtiyacınız olacak.
3. Temel C# Bilgisi: C# temellerini anlamak, konuyu takip etmenize yardımcı olacaktır.
4.  Örnek Belge: Üzerinde çalışabileceğiniz tabloların bulunduğu hazır bir Word belgesi bulundurun. Herhangi bir belgeyi kullanabilirsiniz, ancak biz buna`Tables.docx` Bu eğitimde.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu adım, Aspose.Words özelliklerini kullanmak için ortamımızı ayarladığı için önemlidir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım 1: Belge Dizininizi Ayarlayın

Belgemizi düzenlemeden önce, bulunduğu dizini belirtmemiz gerekir. Bu basit ama önemli bir adımdır.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` belge dizininize giden gerçek yol ile. Bu, programımıza çalışmak istediğimiz dosyanın nerede bulunacağını söyler.

## Adım 2: Belgeyi Yükleyin

Sonra, Word belgesini uygulamamıza yükleriz. Bu, içeriğiyle programatik olarak etkileşime girmemizi sağlar.

```csharp
Document doc = new Document(dataDir + "Tables.docx");
```

 Bu kod satırı şunu açar:`Tables.docx` belirtilen dizinden belge. Şimdi, belgemiz daha ileri işlemler için hazır.

## Adım 3: Tabloya Erişim

Artık belgemiz yüklendiğine göre, çalışmak istediğimiz tabloya erişmemiz gerekiyor. Basitleştirmek için, belgedeki ilk tabloyu hedefleyeceğiz.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Bu satır belgeden ilk tabloyu alır. Belgeniz birden fazla tablo içeriyorsa, farklı bir tablo seçmek için dizini ayarlayabilirsiniz.

## Adım 4: Tablo için Otomatik Sığdırmayı Etkinleştirin

Tablonun sütunlarını otomatik olarak ayarlamasını sağlamak için AutoFit özelliğini etkinleştirmemiz gerekiyor.

```csharp
table.AllowAutoFit = true;
```

 Ayar`AllowAutoFit` ile`true` Tablo sütunlarının içeriklerine göre yeniden boyutlandırılmasını sağlayarak tablomuza dinamik bir hava kazandırır.

## Adım 5: İlk Hücrenin Tercih Edilen Genişlik Türünü Alın

Şimdi dersimizin en önemli noktasına geliyoruz: Tablodaki ilk hücrenin tercih edilen genişlik türünü almak.

```csharp
Cell firstCell = table.FirstRow.FirstCell;
PreferredWidthType type = firstCell.CellFormat.PreferredWidth.Type;
double value = firstCell.CellFormat.PreferredWidth.Value;
```

 Bu kod satırları tablonun ilk satırındaki ilk hücreye erişir ve tercih edilen genişlik türünü ve değerini alır.`PreferredWidthType` olabilir`Auto`, `Percent` , veya`Point`Genişliğin nasıl belirlendiğini gösteren

## Adım 6: Sonuçları Göster

Son olarak aldığımız bilgileri konsola gösterelim.

```csharp
Console.WriteLine("Preferred Width Type: " + type);
Console.WriteLine("Preferred Width Value: " + value);
```

Bu satırlar tercih edilen genişlik türünü ve değerini konsola yazdıracak ve kod yürütmenizin sonuçlarını görmenizi sağlayacaktır.

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak Word belgelerindeki tablo hücrelerinin tercih edilen genişlik türünü almak, yönetilebilir adımlara bölündüğünde basittir. Bu kılavuzu izleyerek Word belgelerinizdeki tablo özelliklerini kolayca düzenleyebilir ve belge yönetimi görevlerinizi çok daha verimli hale getirebilirsiniz.

## SSS

### Bir tablodaki tüm hücreler için tercih edilen genişlik türünü alabilir miyim?

Evet, tablodaki her hücrede dolaşıp her birinin tercih edilen genişlik türlerini ayrı ayrı alabilirsiniz.

###  Olası değerler nelerdir?`PreferredWidthType`?

`PreferredWidthType` olabilir`Auto`, `Percent` , veya`Point`.

### Tercih edilen genişlik türünü programlı olarak ayarlamak mümkün müdür?

 Kesinlikle! Tercih edilen genişlik türünü ve değerini kullanarak ayarlayabilirsiniz.`PreferredWidth` mülkiyeti`CellFormat` sınıf.

### Word dışındaki belgelerdeki tablolar için bu yöntemi kullanabilir miyim?

Bu eğitim özellikle Word belgelerini kapsar. Diğer belge türleri için uygun Aspose kütüphanesini kullanmanız gerekir.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?

 Evet, Aspose.Words for .NET lisanslı bir üründür. Ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/) veya geçici bir lisans[Burada](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
