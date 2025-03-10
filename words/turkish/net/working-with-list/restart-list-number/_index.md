---
title: Yeniden Başlatma Listesi Numarası
linktitle: Yeniden Başlatma Listesi Numarası
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerindeki liste numaralarını nasıl yeniden başlatacağınızı öğrenin. Bu ayrıntılı, 2000 kelimelik kılavuz, kurulumdan gelişmiş özelleştirmeye kadar bilmeniz gereken her şeyi kapsar.
weight: 10
url: /tr/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yeniden Başlatma Listesi Numarası

## giriiş

Aspose.Words for .NET kullanarak Word belgelerinizde liste düzenleme sanatında ustalaşmak mı istiyorsunuz? Doğru yerdesiniz! Bu eğitimde, belge otomasyon becerilerinizi bir üst seviyeye taşıyacak şık bir özellik olan liste numaralarını yeniden başlatmaya derinlemesine dalacağız. Emniyet kemerlerinizi bağlayın ve başlayalım!

## Ön koşullar

Koda geçmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olması gerekir. Henüz yüklemediyseniz,[buradan indirin](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi uygun bir geliştirme ortamına sahip olduğunuzdan emin olun.
3. Temel C# Bilgisi: C# hakkında temel bir anlayışa sahip olmak, eğitimi takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bunlar Aspose.Words özelliklerine erişim için çok önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Şimdi, süreci takip etmesi kolay adımlara bölelim. Bir liste oluşturmaktan numaralandırmayı yeniden başlatmaya kadar her şeyi ele alacağız.

## Adım 1: Belgenizi ve Oluşturucunuzu Ayarlayın

Listeleri düzenlemeye başlamadan önce bir belgeye ve bir DocumentBuilder'a ihtiyacınız var. DocumentBuilder, belgenize içerik eklemek için başvuracağınız araçtır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: İlk Listenizi Oluşturun ve Özelleştirin

Sonra, bir şablona dayalı bir liste oluşturacağız ve görünümünü özelleştireceğiz. Bu örnekte, parantezli Arap sayı biçimini kullanıyoruz.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Burada yazı rengini kırmızı olarak ayarladık ve metni sağa hizaladık.

## Adım 3: İlk Listenize Öğeler Ekleyin

 Listeniz hazır olduğunda, bazı öğeler eklemenin zamanı geldi. DocumentBuilder'ın`ListFormat.List` özellik, liste biçiminin metne uygulanmasına yardımcı olur.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Adım 4: Liste Numaralandırmasını Yeniden Başlatın

Listeyi yeniden kullanmak ve numaralandırmasını yeniden başlatmak için orijinal listenin bir kopyasını oluşturmanız gerekir. Bu, yeni listeyi bağımsız olarak değiştirmenize olanak tanır.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Bu örnekte yeni liste 10 numaradan başlıyor.

## Adım 5: Yeni Listeye Öğeler Ekleyin

Daha önce olduğu gibi, yeni listenize öğeler ekleyin. Bu, listenin belirtilen sayıdan yeniden başladığını gösterir.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Adım 6: Belgenizi Kaydedin

Son olarak belgenizi belirttiğiniz dizine kaydedin.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Çözüm

Aspose.Words for .NET kullanarak Word belgelerindeki liste numaralarını yeniden başlatmak basit ve inanılmaz derecede kullanışlıdır. İster raporlar üretiyor olun, ister yapılandırılmış belgeler oluşturuyor olun veya sadece listeleriniz üzerinde daha iyi bir kontrole ihtiyacınız olsun, bu teknik sizin için idealdir.

## SSS

### NumberArabicParenthesis dışında başka liste şablonları kullanabilir miyim?

Kesinlikle! Aspose.Words, madde işaretleri, harfler, Roma rakamları ve daha fazlası gibi çeşitli liste şablonları sunar. İhtiyaçlarınıza en uygun olanı seçebilirsiniz.

### Liste düzeyini nasıl değiştirebilirim?

 Liste düzeyini, şunu değiştirerek değiştirebilirsiniz:`ListLevels` mülk. Örneğin,`list1.ListLevels[1]` listenin ikinci seviyesini ifade eder.

### Numaralandırmayı herhangi bir sayıdan yeniden başlatabilir miyim?

 Evet, başlangıç numarasını herhangi bir tam sayı değerine ayarlayabilirsiniz.`StartAt` liste düzeyinin özelliği.

### Farklı liste seviyeleri için farklı biçimlendirme kullanmak mümkün müdür?

Gerçekten de! Her liste düzeyinin yazı tipi, hizalama ve numaralandırma stili gibi kendi biçimlendirme ayarları olabilir.

### Yeniden başlamak yerine önceki bir listeden numaralandırmaya devam etmek istersem ne olur?

Numaralandırmaya devam etmek istiyorsanız, listenin bir kopyasını oluşturmanıza gerek yok. Sadece orijinal listeye öğeler eklemeye devam edin.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
