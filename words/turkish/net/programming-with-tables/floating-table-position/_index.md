---
title: Yüzen Tablo Pozisyonu
linktitle: Yüzen Tablo Pozisyonu
second_title: Aspose.Words Belge İşleme API'si
description: Ayrıntılı, adım adım kılavuzumuzla Aspose.Words for .NET'i kullanarak Word belgelerindeki tabloların kayan konumlarını nasıl kontrol edeceğinizi öğrenin.
weight: 10
url: /tr/net/programming-with-tables/floating-table-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yüzen Tablo Pozisyonu

## giriiş

Aspose.Words for .NET kullanarak Word belgelerindeki tablo konumlarını düzenleme dünyasına dalmaya hazır mısınız? Emniyet kemerlerinizi bağlayın çünkü bugün tabloların yüzen konumunu kolayca nasıl kontrol edeceğinizi keşfedeceğiz. Sizi kısa sürede bir tablo konumlandırma sihirbazına dönüştürelim!

## Ön koşullar

Bu heyecanlı yolculuğa çıkmadan önce ihtiyacımız olan her şeye sahip olduğumuzdan emin olalım:

1. Aspose.Words for .NET Library: En son sürüme sahip olduğunuzdan emin olun. Eğer sahip değilseniz,[buradan indirin](https://releases.aspose.com/words/net/).
2. .NET Framework: Geliştirme ortamınızın .NET ile kurulduğundan emin olun.
3. Geliştirme Ortamı: Visual Studio veya tercih ettiğiniz herhangi bir IDE.
4. Word Belgesi: İçinde tablo bulunan bir Word belgesi hazır bulundurun.

## Ad Alanlarını İçe Aktar

Başlamak için, .NET projenize gerekli ad alanlarını içe aktarmanız gerekir. İşte C# dosyanızın en üstüne eklemeniz gereken kod parçası:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım Adım Kılavuz

Şimdi süreci basit ve anlaşılır adımlara bölelim.

## Adım 1: Belgeyi Yükleyin

İlk önce, Word belgenizi yüklemeniz gerekir. Tablonuz burada bulunur.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Word belgenizin bir tuval olduğunu ve masanızın da üzerinde bir sanat eseri olduğunu düşünün. Amacımız bu sanatı tuval üzerinde tam olarak istediğimiz yere yerleştirmektir.

## Adım 2: Tabloya Erişim

Sonra, belge içindeki tabloya erişmemiz gerekiyor. Genellikle, belgenin gövdesindeki ilk tabloyla çalışacaksınız.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Bu adımı, fiziksel bir belgede çalışmak istediğiniz tabloyu bulmak olarak düşünün. Herhangi bir değişiklik yapmak için tam olarak nerede olduğunu bilmeniz gerekir.

## Adım 3: Yatay Pozisyonu Ayarlayın

Şimdi tablonun yatay konumunu ayarlayalım. Bu, tablonun belgenin sol kenarından ne kadar uzağa yerleştirileceğini belirler.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

 Bunu, tabloyu belgeniz boyunca yatay olarak hareket ettirmek olarak görselleştirin.`AbsoluteHorizontalDistance` sol kenardan tam uzaklıktır.

## Adım 4: Dikey Hizalamayı Ayarlayın

Ayrıca tablonun dikey hizalamasını da ayarlamamız gerekiyor. Bu, tabloyu çevresindeki metin içinde dikey olarak ortalayacaktır.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Duvara bir resim astığınızı düşünün. Estetik bir görünüm için dikey olarak ortalandığından emin olmak istersiniz. Bu adım bunu başarır.

## Adım 5: Değiştirilen Belgeyi Kaydedin

Son olarak tabloyu konumlandırdıktan sonra değiştirdiğiniz belgeyi kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

Bu, düzenlenen belgenizde 'Kaydet'e basmak gibidir. Tüm değişiklikleriniz artık korunur.

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir Word belgesindeki tabloların yüzen konumunu nasıl kontrol edeceğinizi öğrendiniz. Bu becerilerle, tablolarınızın belgelerinizin okunabilirliğini ve estetiğini artıracak şekilde mükemmel bir şekilde konumlandırılmasını sağlayabilirsiniz. Aspose.Words for .NET'in geniş yeteneklerini denemeye ve keşfetmeye devam edin.

## SSS

### Tablonun sayfanın üstünden dikey uzaklığını ayarlayabilir miyim?

 Evet, kullanabilirsiniz`AbsoluteVerticalDistance` Tablonun sayfanın üst kenarından dikey uzaklığını ayarlama özelliği.

### Tabloyu belgenin sağına nasıl hizalarım?

 Tabloyu sağa hizalamak için,`HorizontalAlignment` tablonun özelliği`HorizontalAlignment.Right`.

### Aynı belgede birden fazla tabloyu farklı şekilde konumlandırmak mümkün müdür?

 Kesinlikle! Birden fazla tablo için konumlara tek tek erişebilir ve ayarlayabilirsiniz.`Tables` Belgedeki koleksiyon.

### Yatay hizalama için bağıl konumlandırmayı kullanabilir miyim?

Evet, Aspose.Words, aşağıdaki gibi özellikleri kullanarak hem yatay hem de dikey hizalamalar için göreceli konumlandırmayı destekler:`RelativeHorizontalAlignment`.

### Aspose.Words bir belgenin farklı bölümlerinde kayan tabloları destekliyor mu?

Evet, belgenizdeki belirli bir bölüme ve o bölüme ait tablolara erişerek yüzen tabloları farklı bölümlere yerleştirebilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
