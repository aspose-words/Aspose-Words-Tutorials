---
title: Word Belgesinde Karşılaştırma Granülaritesi
linktitle: Word Belgesinde Karşılaştırma Granülaritesi
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET'in Word belgelerinde Granularity'yi karşılaştırma özelliğini öğrenin; bu özellik, belgelerin karakter karakter karşılaştırılmasını ve yapılan değişikliklerin raporlanmasını sağlar.
weight: 10
url: /tr/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde Karşılaştırma Granülaritesi

Aşağıda, Aspose.Words for .NET'in Word belgesinde Karşılaştırma Granülaritesi özelliğini kullanan C# kaynak kodunu açıklayan adım adım bir kılavuz bulunmaktadır.

## Adım 1: Giriş

Aspose.Words for .NET'in Granularity'yi Karşılaştırma özelliği, belgeleri karakter düzeyinde karşılaştırmanıza olanak tanır. Bu, her karakterin karşılaştırılacağı ve değişikliklerin buna göre raporlanacağı anlamına gelir.

## Adım 2: Ortamı kurma

Başlamadan önce, Aspose.Words for .NET ile çalışacak şekilde geliştirme ortamınızı ayarlamanız gerekir. Aspose.Words kütüphanesinin yüklü olduğundan ve kodu gömmek için uygun bir C# projeniz olduğundan emin olun.

## Adım 3: Gerekli Montajları Ekleyin

Aspose.Words for .NET'in Karşılaştırma Granülaritesi özelliğini kullanmak için projenize gerekli derlemeleri eklemeniz gerekir. Projenizde Aspose.Words'e uygun referanslara sahip olduğunuzdan emin olun.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Adım 4: Belgelerin Oluşturulması

Bu adımda, DocumentBuilder sınıfını kullanarak iki belge oluşturacağız. Bu belgeler karşılaştırma için kullanılacak.

```csharp
// A belgesini oluştur.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// B belgesini oluştur.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Adım 5: Karşılaştırma Seçeneklerini Yapılandırma

Bu adımda, karşılaştırma ayrıntı düzeyini belirtmek için karşılaştırma seçeneklerini yapılandıracağız. Burada karakter düzeyinde ayrıntı düzeyini kullanacağız.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Adım 6: Belge Karşılaştırması

Şimdi Document sınıfının Compare metodunu kullanarak belgeleri karşılaştıralım. Değişiklikler A belgesine kaydedilecektir.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 The`Compare`yöntem, belge A'yı belge B ile karşılaştırır ve değişiklikleri belge A'ya kaydeder. Referans için yazarın adını ve karşılaştırma tarihini belirtebilirsiniz.

## Çözüm

Bu makalede, Aspose.Words for .NET'in Karşılaştırma Granülaritesi özelliğini inceledik. Bu özellik, belgeleri karakter düzeyinde karşılaştırmanıza ve değişiklikleri raporlamanıza olanak tanır. Bu bilgiyi projelerinizde ayrıntılı belge karşılaştırmaları yapmak için kullanabilirsiniz.

### .NET için Aspose.Words'ü kullanarak Karşılaştırma Granülaritesi için örnek kaynak kodu

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Çözüm

Bu eğitimde, Aspose.Words for .NET'in Comparison Granularity özelliğini inceledik. Bu özellik, belgeleri karşılaştırırken ayrıntı düzeyini belirtmenize olanak tanır. Farklı ayrıntı düzeyleri seçerek, özel gereksinimlerinize bağlı olarak karakter, kelime veya blok düzeyinde ayrıntılı karşılaştırmalar yapabilirsiniz. Aspose.Words for .NET, farklı ayrıntı düzeylerine sahip belgelerdeki farklılıkları belirlemeyi kolaylaştıran esnek ve güçlü bir belge karşılaştırma yeteneği sunar.

### SSS

#### S: Aspose.Words for .NET'te Karşılaştırma Granülaritesinin kullanılma amacı nedir?

A: Aspose.Words for .NET'teki Karşılaştırma Granülaritesi, belgeleri karşılaştırırken ayrıntı düzeyini belirtmenize olanak tanır. Bu özellik sayesinde belgeleri karakter düzeyi, kelime düzeyi veya hatta blok düzeyi gibi farklı düzeylerde karşılaştırabilirsiniz. Her bir granülarite düzeyi, karşılaştırma sonuçlarında farklı bir ayrıntı düzeyi sağlar.

#### S: Aspose.Words for .NET'te Karşılaştırma Granülaritesini nasıl kullanırım?

A: Aspose.Words for .NET'te Karşılaştırma Granülaritesini kullanmak için şu adımları izleyin:
1. Geliştirme ortamınızı Aspose.Words kütüphanesi ile kurun.
2. Gerekli derlemeleri Aspose.Words'e başvurarak projenize ekleyin.
3.  Karşılaştırmak istediğiniz belgeleri kullanarak oluşturun`DocumentBuilder` sınıf.
4.  Karşılaştırma seçeneklerini bir karşılaştırma oluşturarak yapılandırın`CompareOptions` nesne ve ayarlama`Granularity` mülkü istenilen düzeye (örneğin,`Granularity.CharLevel` (karakter düzeyinde karşılaştırma için).
5.  Kullanın`Compare`bir belge üzerindeki yöntem, diğer belgeyi geçirerek ve`CompareOptions` nesneyi parametre olarak kullanır. Bu yöntem, belgeleri belirtilen ayrıntı düzeyine göre karşılaştırır ve değişiklikleri ilk belgeye kaydeder.

#### S: Aspose.Words for .NET'te Karşılaştırma Ayrıntılılığının hangi düzeyleri mevcuttur?

A: Aspose.Words for .NET üç düzeyde Karşılaştırma Ayrıntılılığı sağlar:
- `Granularity.CharLevel`: Belgeleri karakter düzeyinde karşılaştırır.
- `Granularity.WordLevel`: Belgeleri kelime düzeyinde karşılaştırır.
- `Granularity.BlockLevel`: Belgeleri blok düzeyinde karşılaştırır.

#### S: Karakter düzeyinde ayrıntılandırma ile karşılaştırma sonuçlarını nasıl yorumlayabilirim?

A: Karakter düzeyinde ayrıntılandırma ile karşılaştırılan belgelerdeki her karakter farklılıklar açısından analiz edilir. Karşılaştırma sonuçları, eklemeler, silmeler ve değişiklikler dahil olmak üzere bireysel karakter düzeyindeki değişiklikleri gösterecektir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
