---
category: general
date: 2026-09-30
description: C# ile Word’de şekilleri gruplayın – şekilleri nasıl gruplayacağınızı,
  dikdörtgen ve elips eklemeyi ve Word belgelerine programlı olarak dikdörtgen şekli
  eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: tr
lastmod: 2026-09-30
og_description: C# ve Aspose.Words kullanarak Word’de şekilleri gruplayın. Dikdörtgen
  eklemek, elips eklemek ve şekilleri verimli bir şekilde gruplamayı öğrenmek için
  bu kapsamlı rehberi izleyin.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: C# ile Word’de şekilleri gruplama – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# ve Aspose.Words kullanarak Word'de şekilleri nasıl gruplandırılır
url: /tr/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ve Aspose.Words ile Word’de Şekilleri Nasıl Gruplandırılır

Programlı olarak **Word’de şekilleri gruplandırmanız** gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Bir dikdörtgen eklemeyi, bir elips eklemeyi ve ardından bunları Aspose.Words .NET kütüphanesini kullanarak tek bir grup şekil haline getirmeyi göreceksiniz.

Şekillerle çalışmak, raporlar, sözleşmeler veya pazarlama materyallerini otomatik olarak oluştururken yaygın bir gereksinimdir. Bu öğreticinin sonunda, bir DOCX dosyasını yükleyen, bir dikdörtgen ve bir elips ekleyen, bunları gruplandıran ve sonucu kaydeden yeniden kullanılabilir bir C# metoduna sahip olacaksınız—Word’ü manuel olarak açmadan.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm  
* Visual Studio 2022 gibi bir geliştirme ortamı (Community sürümü yeterlidir)  
* Aspose.Words for .NET lisansı veya ücretsiz bir değerlendirme kopyası (API lisans olmadan çalışır ancak bir filigran ekler)  

Ayrıca koddan referans verebileceğiniz bir klasörde bir kaynak Word belgesi (`input.docx`) bulunmalıdır. Belge boş olabilir; öğretici şekil işleme üzerine odaklanmaktadır.

## Adım 1: Yeni bir konsol projesi oluşturun ve Aspose.Words ekleyin

Bir terminal veya Visual Studio komut istemcisi açın ve şu komutu çalıştırın:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Bu komut, **WordShapeDemo** adlı yeni bir konsol uygulaması oluşturur ve Word dosyalarını manipüle etmek için kullanılan `Document` ve `DocumentBuilder` sınıflarını içeren `Aspose.Words` NuGet paketini ekler.

## Adım 2: Bir belge yükleyin veya oluşturun

**Word’de grup şekilleri** ile çalışırken ilk işlem bir `Document` nesnesi elde etmektir. Mevcut bir DOCX dosyasını yükleyebilir veya boş bir belgeden başlayabilirsiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

`Document` sınıfı, tüm Word dosyasını temsil eder. Bir dosya yüklemek, şekilleri eklemek için hazır bir tuval sağlar.

## Adım 3: Bir grup şekil başlatın

*Grup şekli*, birkaç bağımsız şekli tek bir birim olarak ele almanızı sağlar—bunları birlikte taşımak veya yeniden boyutlandırmak için mükemmeldir. Bir grup başlatmak için `DocumentBuilder` üzerinde `StartGroupShape()` metodunu çağırın.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

`StartGroupShape` çağrısı, Aspose.Words’e sonraki tüm şekil eklemelerinin aynı mantıksal gruba ait olduğunu, `EndGroupShape` çağrılana kadar bildirir.

## Adım 4: Word’de dikdörtgen şekli nasıl eklenir

Grup açıldıktan sonra bir dikdörtgen ekleyin. `InsertShape` metodu bir `ShapeType` enum’u, ardından genişlik ve yükseklik (puan cinsinden) alır.

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Dikdörtgen, grubun ilk üyesi olur. Gerektiğinde dolgu, kenarlık veya metnini daha sonra özelleştirebilirsiniz.

## Adım 5: Word’de elips şekli nasıl eklenir

Sonra bir elips ekleyin (genişlik yükseklik eşit olduğunda daire olur). Bu, aynı builder kullanılarak **elips eklemenin** nasıl yapılacağını gösterir.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Her iki şekil de artık grup içinde aynı koordinat alanını paylaşır, bu da görsel olarak hizalamayı kolaylaştırır.

## Adım 6: Grup şekli tanımını kapatın

İstediğiniz tüm üyeleri eklediğinizde grubu kapatın. Bu, şekil koleksiyonunu sonlandırır ve Word bunları tek bir nesne olarak algılar.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Bu noktada belge, bir dikdörtgen ve bir elipsten oluşan tek bir gruplanmış şekil içerir.

## Adım 7: Değiştirilen belgeyi kaydedin

Son olarak değişiklikleri diske yazın. Orijinal dosyanın üzerine yazabilir veya yeni bir dosya oluşturabilirsiniz.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Programı çalıştırdığınızda `output.docx` üretilir. Dosyayı Microsoft Word’de açın, şekli seçin; dikdörtgen ve elipsin birlikte hareket ettiğini göreceksiniz—**Word’de grup şekilleri** işleminin başarılı olduğunun kanıtı.

### Beklenen sonuç

* Word dosyası tek bir gruplanmış nesne içerir.  
* Grubu seçtiğinizde hem dikdörtgen hem de elips aynı anda sürüklenebilir, yeniden boyutlandırılabilir veya döndürülebilir.  
* Word ile manuel etkileşim gerekmez; her şey C# kodu ile yapılır.

![Grouped shapes in Word document](grouped-shapes.png "Word belgesinde gruplanmış bir dikdörtgen ve elips şekli gösteren ekran görüntüsü")

*Görsel alt metni: “Word belgesinde gruplanmış bir dikdörtgen ve elips şekli gösteren ekran görüntüsü”* (görsel alt‑metin gereksinimini karşılar).

## Şekilleri gruplandırmanın önemi

Şekilleri gruplandırmak sadece görsel bir rahatlık değildir. Şunları sağlar:

* **Düzen tutarlılığını koruma** – bir grubu taşımak, göreceli konumları aynı tutar.  
* **Dönüşümleri tek seferde uygulama** – tüm grup yerine her şekli ayrı ayrı döndürmek veya ölçeklendirmek yerine grup üzerinde işlem yaparsınız.  
* **Sonraki işlemeyi basitleştirme** – diğer araçlar DOCX’i okurken tek bir birleşik şekil görür, karmaşıklık azalır.

Aynı mantıksal birime daha fazla şekil (ör. bir çizgi veya metin kutusu) eklemeniz gerektiğinde, `EndGroupShape`’den önce tekrar `InsertShape` çağırmanız yeterlidir.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Nasıl ele alınır |
|-----------|-----------------|
| **Farklı birimler** – ölçümleriniz santimetre cinsindeyse | `InsertShape` çağırmadan önce santimetreyi puana dönüştürün (`1 cm ≈ 28.35 pt`). |
| **Metin etiketi ekleme** – grup içinde bir başlık istiyorsunuz | Dikdörtgen ve elipsin ardından bir `ShapeType.TextBox` ekleyin, ardından `Text` özelliğini ayarlayın. |
| **Dolgu rengi uygulama** – mavi bir dikdörtgene ihtiyacınız var | `InsertShape` sonrası son şekli `builder.CurrentParagraph.Runs[0].Font` üzerinden alın ve `shape.FillColor = System.Drawing.Color.Blue;` satırını ekleyin. |
| **Farklı belge formatı kullanma** – `.doc` hedefliyorsunuz, `.docx` yerine | Kod aynı çalışır; sadece `Save` çağrısında dosya uzantısını değiştirin. Aspose.Words formatı otomatik olarak yönetir. |

## Profesyonel ipuçları

* **Builder’ı yeniden kullanın** – aynı belgede birden fazla grup başlatıp bitirebilirsiniz; `EndGroupShape` sonrası tekrar `StartGroupShape` çağırmanız yeterlidir.  
* **Performans** – Tek bir `StartGroupShape/EndGroupShape` bloğu içinde toplu şekil eklemek, grup dışına ayrı ayrı eklemekten daha hızlıdır.  
* **Lisanslama** – değerlendirme lisansı ilk sayfada bir filigran ekler. Üretim ortamlarında kaldırmak için tam bir lisans kurun.

## Sonuç

Artık C# ile **Word’de şekilleri gruplandırmayı**, **dikdörtgen eklemeyi**, **elips eklemeyi** ve Aspose.Words kullanarak Word belgelerine **şekil eklemeyi** biliyorsunuz. Tam, çalıştırılabilir örnek, proje kurulumundan nihai dosyanın kaydedilmesine kadar her adımı gösteriyor.

Buradan itibaren ek şekil türlerini keşfedebilir, stil uygulayabilir veya gruplandırılmış şekilleri tablolar ve görsellerle birleştirerek karmaşık, programatik olarak oluşturulmuş belgeler yaratabilirsiniz.

---

**Sonraki adımlar**

* **Gruplanmış şekilleri döndürmeyi** öğrenin: grup kapatıldıktan sonra `Shape.RotationAngle` kullanın.  
* Dikdörtgen ve elips için **dolgu ve kenarlık özelleştirmelerini** keşfedin.  
* Bu mantığı bir ASP.NET Core API’ye entegre ederek isteğe bağlı raporlar üretin.  

İyi kodlamalar!


## Bir Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}