---
category: general
date: 2026-10-26
description: C#'ta boş bir Word belgesi oluşturun ve bir grup şekil eklemeyi öğrenin,
  ardından gruba bir dikdörtgen şekli ekleyin. Bu rehber, birden fazla şekli gruplamayı
  adım adım ele alır.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: tr
lastmod: 2026-10-26
og_description: C# ile boş bir Word belgesi oluşturun ve grubun nasıl ekleneceğini
  görün, ardından dikdörtgen şekli ekleyin. Birden fazla şekli gruplamayı tam bir
  kod örneğiyle ustalaşın.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Boş Word belgesi oluşturun ve birden fazla şekli gruplayın – C# öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Boş bir Word belgesi oluşturma ve birden fazla şekli gruplama
url: /tr/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word belgesi oluşturma ve birden fazla şekli gruplama

Programlı olarak **boş Word belgesi oluşturmanız** gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını gösterir. Bir grup şekli nasıl ekleyeceğinizi ve ardından o gruba **dikdörtgen eklemeyi** göreceksiniz; boş bir belgeden gruplanmış bir çizime kadar tam iş akışını kapsar.

Word dosyalarıyla çalışmak genellikle birkaç çizimi bir araya getirmeyi gerektirir—birden çok şekilden oluşan bir diyagramı düşünün. Bu rehberin sonunda **birden fazla şekli gruplamayı**, bir **dikdörtgen şekli eklemeyi** ve **grup eklemenin nasıl yapılacağını** ve **dikdörtgen eklemenin nasıl yapılacağını** temiz, yeniden kullanılabilir bir şekilde anlayabileceksiniz.

## Gereksinimler

* .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır)
* **Aspose.Words for .NET** NuGet paketi (`Install-Package Aspose.Words`)
* C# ve Visual Studio IDE'sine temel bir anlayış (herhangi bir IDE çalışır)

> **Pro ipucu:** Aspose.Words tamamen çevrim dışı çalışır; paket yüklendikten sonra internet bağlantısına ihtiyacınız yok.

## Adım 1: Boş bir Word belgesi oluşturma

İlk işlem, boş bir `Document` nesnesi örneklemektir. Bu nesne, daha sonra şekillerle zenginleştireceğiniz **boş Word belgesini** temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Neden önemli?*: Bölüm veya paragraf içermeyen bir `Document` hâlâ geçerli bir .docx dosyasıdır. Temiz bir sayfadan başlamak, daha sonra ekleyeceğiniz şekillerin gizli biçimlendirmelerden etkilenmemesini garanti eder.

## Adım 2: Grup şekli ekleme (grup ekleme nasıl yapılır)

Bir **grup şekli**, diğer çizim nesnelerini tutabilen bir kapsayıcı gibi davranır. Aspose.Words'ta bunu `InsertGroupShape` ile oluşturursunuz.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Neden grup kullanmalı?* Gruplama, birkaç şekli tek bir birim olarak taşımanıza, döndürmenize veya yeniden boyutlandırmanıza olanak tanır. Bu, öğelerin hizalı kalması gereken diyagramlar için esastır.

## Adım 3: Dikdörtgen şekli ekleme (dikdörtgen şekli ekleme)

Şimdi belgeye bir dikdörtgen ekleyin. `InsertShape` yöntemi, daha sonra gruba ekleyebileceğiniz bir `Shape` nesnesi döndürür.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Neden dikdörtgen?* Dikdörtgenler, akış şemaları, UI mock‑up​ları ve yer tutucu grafikler için en yaygın yapı taşlarıdır. Boyutlar nokta cinsinden ifade edilir (1 pt ≈ 1/72 inç).

## Adım 4: Dikdörtgeni gruba ekleme (dikdörtgen ekleme nasıl yapılır)

`InsertShape` ile oluşturulan bir şekil doğrudan belge gövdesinde bulunur. Bunu grubun bir parçası haline getirmek için `GroupShape` üzerinde `AppendChild` metodunu çağırın.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Arka planda ne olur?* `AppendChild`, dikdörtgen düğümünü belgenin ana hikâyesinden grubun iç koleksiyonuna taşır ve boyutunu ve konumunu grup kökenine göre korur.

## Adım 5: Belgeyi kaydetme

Son olarak, dosyayı diske yazın. Oluşan `.docx` dosyasını Microsoft Word'de açarak gruplanmış dikdörtgeni görebilirsiniz.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Köşe durumu:** Aynı gruba daha fazla şekil (ör. daireler, çizgiler) eklemeyi planlıyorsanız, kaydetmeden önce her yeni şekil için **Adım 3** ve **Adım 4**'ü tekrarlayın. Grup, tüm alt öğeleri kapsayacak şekilde sınır kutusunu otomatik olarak ayarlar.

## Birden fazla şekli gruplama – örneği genişletme

Aşağıda, aynı gruba ikinci bir şekil (bir elips) ekleyen ve tek bir belgede **birden fazla şekli gruplamayı** gösteren hızlı bir kod parçacığı bulunmaktadır.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

`GroupedShapeExample.docx` dosyasını açtığınızda, Word'de grubu seçtiğinizde dikdörtgen ve elipsin birlikte hareket ettiğini göreceksiniz.

## Yaygın sorular ve sorun giderme

| Soru | Cevap |
|----------|--------|
| **Aspose.Words için bir lisansa ihtiyacım var mı?** | Ücretsiz değerlendirme lisans olmadan çalışır, ancak bir filigran ekler. Üretim ortamında filigranı kaldırmak ve tam performansı açmak için bir lisans uygulamalısınız. |
| **Şekilleri tam olarak konumlandırabilir miyim?** | Evet. Bir şekil ekledikten sonra `Shape.Left`, `Shape.Top`, `Shape.Width` ve `Shape.Height` özelliklerini ayarlayabilirsiniz. |
| **Kaydetme sonrası dikdörtgen kaybolursa ne olur?** | `group.AppendChild(rectangle)` metodunu dikdörtgeni ekledikten *sonra* çağırdığınızdan emin olun. Şekli önce belge gövdesine eklemek, ardından gruba taşımak gerekir. |
| **Farklı bölümler arasında şekilleri gruplamak mümkün mü?** | Hayır. Bir gruptaki tüm şekiller aynı hikâyeye (bölüme) ait olmalıdır. Gerekirse bölüm başına ayrı gruplar oluşturun. |

## Özet

Artık Aspose.Words for .NET kullanarak **boş Word belgesi oluşturma**, **grup ekleme**, **dikdörtgen ekleme** ve **birden fazla şekli gruplama** konularını biliyorsunuz. Yukarıdaki tam, çalıştırılabilir örnek bir konsol uygulamasına kopyalanıp hemen çalıştırılabilir.

## Sonraki adımlar

* **insert rectangle shape** boyutları ve renkleriyle deney yapın (`rectangle.FillColor = Color.LightBlue;`).  
* Diğer şekil türlerini keşfedin (`ShapeType.Polygon`, `ShapeType.Line`) ve diyagramlarınızı zenginleştirin.  
* Son `.docx` dosyasını PDF'ye dönüştürmeyi öğrenin (`doc.Save("output.pdf");`) dağıtım için.  
* **how to add rectangle**'ı zaten metin içeren mevcut belgelere eklemeyi araştırın—grubu istediğiniz yere konumlandırmak için `DocumentBuilder.MoveTo` kullanın.

Kodu kendi raporlama veya diyagram‑oluşturma ihtiyaçlarınıza göre uyarlamaktan çekinmeyin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [C#'ta boş Word belgesi oluşturma ve şekilleri gruplama](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Word'de şekilleri gruplama ve Word belgesine şekil ekleme](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Aspose.Words ile Word'de dikdörtgen şekli oluşturma ve şekilleri gruplama](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}