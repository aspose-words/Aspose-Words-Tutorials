---
title: Yazı Tipi Satır Aralığını Al
linktitle: Yazı Tipi Satır Aralığını Al
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım eğitimle Aspose.Words for .NET kullanarak yazı tipi satır aralığını nasıl elde edeceğinizi öğrenin. Geliştiriciler için mükemmel.
weight: 10
url: /tr/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Satır Aralığını Al

## giriiş

Aspose.Words for .NET, Word belgelerini programatik olarak oluşturmanıza, düzenlemenize ve dönüştürmenize olanak tanıyan güçlü bir kütüphanedir. Gerçekleştirmeniz gereken yaygın görevlerden biri, bir belgedeki belirli bir yazı tipinin satır aralığını almaktır. Bu eğitimde, Aspose.Words for .NET kullanarak yazı tipi satır aralığını kolayca elde edebilmenizi sağlayarak sizi adım adım süreçte yönlendireceğiz. 

## Ön koşullar

Koda dalmadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

1.  Aspose.Words for .NET Kütüphanesi: En son sürümü buradan indirin ve kurun[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi bir IDE'nin kurulu olduğundan emin olun.
3. Temel C# Bilgisi: Bu eğitimde C# programlama hakkında temel bir anlayışa sahip olduğunuzu varsayıyoruz.

## Ad Alanlarını İçe Aktar

Öncelikle, C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu ad alanları, Aspose.Words işlevlerine erişmenizi sağlayacaktır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Yazı tipi satır aralığını ayarlama sürecini basit ve yönetilebilir adımlara bölelim.

## Adım 1: Yeni Bir Belge Oluşturun

İlk adım, Aspose.Words for .NET kullanarak yeni bir Word belgesi örneği oluşturmaktır.

```csharp
Document doc = new Document();
```

## Adım 2: DocumentBuilder'ı Başlatın

Daha sonra, başlatmamız gerekiyor`DocumentBuilder` nesne. Bu nesne, belge içeriğini oluşturmamıza ve düzenlememize yardımcı olacaktır.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: Yazı Tipi Özelliklerini Ayarlayın

Şimdi, eklemek istediğimiz metin için font özelliklerini ayarlıyoruz. Bu örnek için "Calibri" fontunu kullanacağız.

```csharp
builder.Font.Name = "Calibri";
```

## Adım 4: Belgeye Metin Yazın

 Kullanımı`DocumentBuilder` nesne, belgeye biraz metin yazın. Bu metin, önceki adımda ayarladığımız yazı tipi özelliklerini kullanacaktır.

```csharp
builder.Writeln("Sample Text");
```

## Adım 5: Font Nesnesini Alın

Satır aralığını elde etmek için, az önce eklediğimiz metnin font nesnesine erişmemiz gerekir. Bu, belge yapısı boyunca ilk paragraf çalışmasına giderek yapılabilir.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Adım 6: Satır Aralığını Alın

Son olarak font nesnesinden satır aralığını alıp konsola yazdırıyoruz.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak yazı tipi satır aralığını almak, bunu bu basit adımlara böldüğünüzde basittir. Yeni bir belge oluşturuyor veya mevcut bir belgeyle çalışıyor olun, Aspose.Words yazı tipi özelliklerini etkili bir şekilde yönetmeniz için gereken tüm araçları sağlar.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin C# kullanarak Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan güçlü bir kütüphanedir.

### Aspose.Words for .NET'i diğer .NET dillerinde kullanabilir miyim?
Evet, Aspose.Words for .NET'i VB.NET ve F# dahil olmak üzere herhangi bir .NET diliyle kullanabilirsiniz.

### Aspose.Words for .NET'i nasıl indirebilirim?
 Aspose.Words for .NET'in en son sürümünü şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/net/).

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şu adresten alabilirsiniz:[Burada](https://releases.aspose.com/).

### Aspose.Words for .NET'in belgelerini nerede bulabilirim?
 Aspose.Words for .NET'e ilişkin belgeler mevcuttur[Burada](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
